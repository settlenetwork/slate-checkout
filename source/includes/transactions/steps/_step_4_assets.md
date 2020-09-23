# Step 4 Assets

> Payload Example:

```javascript
const residenceCountry = "AR";
const selectedOrderType = "pay-in";

const url = `${server}/api/v2/assets?countryCode=${residenceCountry}&orderType=${selectedOrderType}`;
axiosLoggedIn.get(url).then(function (result) {
  console.log(result.data);
});
```

> Response Example:

```javascript
{
  "assets": {
      "pay-in": {
          "AR": [
              "ARS"
          ]
      }
  }
}
```

Once the OrderType has been selected, the assets supported by the countryCode and orderType filters must be obtained.

`[GET] /api/v2/assets?countryCode={residenceCountry}&orderType={selectedOrderType}`

### Query Params

| key         | Type   | Description                                             |
| ----------- | ------ | ------------------------------------------------------- |
| countryCode | string | <strong>optional</strong> - Country to filter results   |
| orderType   | string | <strong>optional</strong> - OrderType to filter results |
