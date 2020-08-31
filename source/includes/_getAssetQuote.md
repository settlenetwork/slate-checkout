# Get Asset Quote

> Response Example:

```javascript
{
  "quote": 37679.15,
  "fromAssetMinAmount": 0.001,
  "toAssetMinAmount": 20,
  "dailyLimit": 10000,
  "fee": 1,
  "minFee": 0
}
```

> <strong>Note:</strong> The "fee" field is expressed as percentage. In this example it would be 1%.

### HTTP Request

`GET /api/quotes`

### Query Params

| key       | Type   | Description                                                                                       |
| --------- | ------ | ------------------------------------------------------------------------------------------------- |
| fromAsset | string | <strong>required</strong> - The asset to return the quote about                                   |
| toAsset   | string | <strong>required</strong> - The asset used to represent the quote                                 |
| type      | string | <strong>Sell, Buy</strong> - Default: <strong>Sell</strong> (Sell for deposit / Buy for withdraw) |

### Current Supported Assets for Sell type (Deposit/Cash-In)

| key       | Value              |
| --------- | ------------------ |
| fromAsset | BTC, BNB, ETH, LTC |
| toAsset   | ARS, BRL, MXN      |
| type      | Sell               |

### Current Supported Assets for Buy type (Withdraw/Cash-Out)

| key       | Value              |
| --------- | ------------------ |
| fromAsset | BTC, BNB, ETH, LTC |
| toAsset   | ARS, BRL, MXN      |
| type      | Buy                |
