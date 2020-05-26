# Get Cash-Out Tickets (Withdraw)

> Response Example (Pending Ticket)

```javascript
{
 "data": [
   {
     "cashoutId": 1234,
     "method": "bank-transfer",
     "countryCode": "BR",
     "transactionRef": "ee463315-8522-4b77-92ff-cb5705121223",
     "status": "Pending",
     "createdTimestamp": "2020-04-17 10:30:00.000Z",
     "lastUpdateTimeStamp": "2020-04-24 10:30:00.000Z",
     "destinationAsset": "BRL",
     "originAsset": "BTC",
     "checkoutAmount": 0.0999,
     "feeAmount": 0.0001,
     "consumerUserId": "bae42210-d136-4832-afad-ebfbace4eb3a",
     "callbackUrl": "https://www.your-domain.com/es/user/wallet/withdraw/BTC"
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
      "cashoutId": 1234,
      "method": "bank-transfer",
      "countryCode": "BR",
      "transactionRef": "ee463315-8522-4b77-92ff-cb570590876",
      "status": "Accepted",
      "createdTimestamp": "2020-04-17 10:30:00.000Z",
      "lastUpdateTimeStamp": "2020-04-24 10:30:00.000Z",
      "destinationAsset": "BRL",
      "originAsset": "BTC",
      "checkoutAmount": 0.0999,
     "feeAmount": 0.0001,
      "consumerUserId": "bae42210-d136-4832-afad-ebfbace4eb3a",
      "paidQuote": 37721.12,
      "callbackUrl": "https://www.your-domain.com/es/user/wallet/withdraw/BTC",
      "fee": 1,
      "providerWithdrawId": "657",
      "providerWithdrawMsg": "Success",
      "paidAmount": 3768.34
    },
    ...
  ],
  "total": 10
}
```

### HTTP Request

`GET /api/account/{id}/cashouts`

<aside class="notice">
  Note: {id} could be the “user id” (see consumerUserId in response) as well as “all” as wildcard to retrieve all the tickets from all users.
</aside>
 
Examples:

Retrieve tickets for a specific user:

`GET /api/account/bae42210-d136-4832-afad-ebfbace4eb3a/cashouts`

Retrieve all tickets for all users:

`GET /api/account/all/cashouts`

### Query Params

| key     | Type    | Description                                                                               |
| ------- | ------- | ----------------------------------------------------------------------------------------- |
| status  | string  | A filter to be applied to the query. One of: <strong>Accepted, Rejected, Pending</strong> |
| limit   | integer | The amount of items per page. (default = 100)                                             |
| offset  | integer | From where to start.                                                                      |
| orderBy | string  | The property to be used for sorting (with a - as a prefix for desc order)                 |

### Headers (see Authentication section)

| key           | Type   | Description                                                                |
| ------------- | ------ | -------------------------------------------------------------------------- |
| Authorization | string | <strong>required</strong> - Example: Token eyJhbGciOiJIUzI1NiIsInR5cCI6Ikp |
