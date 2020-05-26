# Get Cash-In Tickets (Deposit)

> Response Example (Pending Ticket)

```javascript
{
 "data": [
   {
     "depositId": 1234,
     "method": "bank-transfer",
     "countryCode": "BR",
     "transactionRef": "ee463315-8522-4b77-92ff-cb5705313731",
     "status": "Pending",
     "createdTimestamp": "2020-04-17 10:30:00.000Z",
     "lastUpdateTimeStamp": "2020-04-24 10:30:00.000Z",
     "destinationWalletAddress": "1FfmbHfnpaZjKFvyi1okTjJJus4455paPH",
     "destinationAsset": "BTC",
     "originAsset": "BRL",
     "checkoutAmount": 100,
     "consumerUserId": "bae42210-d136-4832-afad-ebfbace4eb3a",
     "callbackUrl": "https://www.your-domain.com/es/user/wallet/deposit/BTC"
   },
   ...
 ],
 "total": 10
}
```

> Response Example (Accepted Ticket)

```javascript
{
  "data": [
    {
      "depositId": 1234,
      "method": "bank-transfer",
      "countryCode": "BR",
      "transactionRef": "ee463315-8522-4b77-92ff-cb5705313731",
      "status": "Accepted",
      "createdTimestamp": "2020-04-17 10:30:00.000Z",
      "lastUpdateTimeStamp": "2020-04-24 10:30:00.000Z",
      "destinationWalletAddress": "1FfmbHfnpaZjKFvyi1okTjJJus4455paPH",
      "destinationAsset": "BTC",
      "originAsset": "BRL",
      "checkoutAmount": 99,
      "consumerUserId": "bae42210-d136-4832-afad-ebfbace4eb3a",
      "paidQuote": 37721.12,
      "callbackUrl": "https://www.your-domain.com/es/user/wallet/deposit/BTC",
      "fee": 1,
      "providerWithdrawId": "60d354c910874531b9268d476bb01d42",
      "providerWithdrawMsg": "Success",
      "paidAmount": 0.00262452,
      "txId": "fdf6e560dc317cc92f94bf6be639f86f503ddae224354d0a3cca1ba5ce14ac8e"
    },
    ...
  ],
  "total": 10
}
```

### HTTP Request

`GET /api/account/{id}/deposits`

<aside class="notice">
  Note: {id} could be the “user id” (see consumerUserId in response) as well as “all” as wildcard to retrieve all the tickets from all users.
</aside>
 
Examples:

Retrieve tickets for a specific user:

`GET /api/account/bae42210-d136-4832-afad-ebfbace4eb3a/deposits`

Retrieve all tickets for all users:

`GET /api/account/all/deposits`

### Query Params

| key     | Type    | Description                                                                               |
| ------- | ------- | ----------------------------------------------------------------------------------------- |
| status  | string  | A filter to be applied to the query. One of: <strong>Accepted, Rejected, Pending</strong> |
| limit   | integer | The amount of items per page. (default = 1000)                                            |
| offset  | integer | From where to start.                                                                      |
| orderBy | string  | The property to be used for sorting (with a - as a prefix for desc order)                 |

### Headers (see Authentication section)

| key           | Type   | Description                                                                |
| ------------- | ------ | -------------------------------------------------------------------------- |
| Authorization | string | <strong>required</strong> - Example: Token eyJhbGciOiJIUzI1NiIsInR5cCI6Ikp |
