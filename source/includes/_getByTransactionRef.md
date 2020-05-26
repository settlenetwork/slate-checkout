# Get ticket by transactionRef

### HTTP Request

`GET /api/transaction/{transactionRef}`

Example:

`GET /api/transaction/ee463315-8522-4b77-92ff-cb5705313731`

### Query Params

| key  | Type   | Description                                                                        |
| ---- | ------ | ---------------------------------------------------------------------------------- |
| type | string | The type to use for the lookup. One of: "Desposit", "Withdraw". Default: "Deposit" |

> Response Example

```javascript
{
 "data": {
    "depositId": 1234,
    "method": "bank-transfer",
    "countryCode": "BR",
    "transactionRef": "ee463315-8522-4b77-92ff-cb5705313731",
    "status": "Accepted",
    "createdTimestamp": "2020-04-17 10:30:00.000Z",
    "lastUpdateTimeStamp": "2020-04-24 20:31:37.228Z",
    "destinationWalletAddress": "1FfmbHfnpaZjKFvyi1okTjJJus4455paPH",
    "destinationAsset": "BTC",
    "originAsset": "BRL",
    "checkoutAmount": 99,
    "feeAmount": 1,
    "consumerUserId": "bae42210-d136-4832-afad-ebfbace4eb3a",
    "paidQuote": 37721.12,
    "callbackUrl": "https://www.your-domain.com/es/user/wallet/deposit/BTC",
    "providerWithdrawId": "60d354c910874531b9268d476bb01d42",
    "providerWithdrawMsg": "Success",
    "paidAmount": 0.00262452,
    "txId": "fdf6e560dc317cc92f94bf6be639f86f503ddae224354d0a3cca1ba5ce14ac8e"
  }
}
```
