# Step 3 Order Types

> Payload Example:

```javascript
axiosLoggedIn.get(`${server}/api/v2/order-types`).then(function (result) {
  console.log(result.data);
});
```

> Response Example:

```javascript
{
  "orderTypes": [
      {
          "orderType": "pay-in",
          "description": "Deposit to fiat balance"
      },
      {
          "orderType": "pay-out",
          "description": "Withdraw from fiat balance"
      }
  ]
}
```

### Http Request

The user must interactively select an OrderType within this list.

`[GET] /api/v2/order-types`
