# Step 5 Payment Methods

> Payload Example:

```javascript
const residenceCountry = "AR";
const selectedOrderType = "pay-in";

const url = `${server}/api/v2/payment-methods?countryCode=${residenceCountry}&orderType=${selectedOrderType}`;
axiosLoggedIn.get(url).then(function (result) {
  console.log(result.data);
});
```

> Response Example:

```javascript
{
  "paymentMethods": {
    "pay-in": {
      "AR": {
        "bank-transfer": [
          {
            "name": "bank",
            "limits": {
              "daily": {
                "min": 1800,
                "max": 40000
              },
              "monthly": {
                "max": 138000
              },
              "annual": {
                "max": 240000
              }
            }
          }
        ]
      }
    }
  }
}
```

`[GET] /api/v2/payment-methods?countryCode={residenceCountry}&orderType={selectedOrderType}`

### Query Params

| key         | Type   | Description                                             |
| ----------- | ------ | ------------------------------------------------------- |
| countryCode | string | <strong>optional</strong> - Country to filter results   |
| orderType   | string | <strong>optional</strong> - OrderType to filter results |

### Result

Returns the payment methods for a given country / orderType.
this structure is the next one:

`{ paymentMethods: { [orderType]: { [country]: { [paymentMethod]:[ providerMethodList ] } } } }`

The structure of each providerMethod is:

`{ name: “bank”, limits: { daily: { min: 100, max: 1000 }, ... }, ... }`

The most important data in this providerMethod is the name field and within the limits attribute the daily, which indicates the minimum and maximum values for said transaction. With this data, the minimum and maximum amount that the user can load must be validated.
