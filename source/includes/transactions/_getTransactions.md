# Get Transactions

> Payload Example:

```javascript
const kycId = 1031;
axiosLoggedIn
  .get(`${server}/api/v2/account/${kycId}/transactions`)
  .then(function (result) {
    console.log(result.data);
  });
```

> Response Example

```javascript
{
  "total": 7,
  "list": [
    {
      "id": 17,
      "orderType": "pay-in",
      "status": "Pending",
      "amount": 12000,
      "feeAmount": 240,
      "netAmount": 11760
    },
    {
      "id": 16,
      "orderType": "pay-out",
      "status": "Pending",
      "amount": 12000,
      "feeAmount": 240,
      "netAmount": 11760
    },
    {
      "id": 15,
      "orderType": "pay-in",
      "status": "Pending",
      "amount": 12000,
      "feeAmount": 240,
      "netAmount": 11760
    },
    {
      "id": 14,
      "orderType": "pay-in",
      "status": "Accepted",
      "amount": 12000,
      "feeAmount": 240,
      "netAmount": 11760
    },
    {
      "id": 13,
      "orderType": "pay-in",
      "status": "Accepted",
      "amount": 12000,
      "feeAmount": 240,
      "netAmount": 11760
    },
    {
      "id": 12,
      "orderType": "pay-out",
      "status": "Accepted",
      "amount": 7000,
      "feeAmount": 140,
      "netAmount": 6860
    },
    {
      "id": 11,
      "orderType": "pay-out",
      "status": "Accepted",
      "amount": 7000,
      "feeAmount": 140,
      "netAmount": 6860
    }
  ]
}
```

### HTTP Request

`GET /api/v2/account/{kycId | all}/transactions`

<aside class="notice">
  Note: {kycId} could be the “kyc user id” as well as “all” as wildcard to retrieve all the transactions from all users.
</aside>
 
Examples:

Retrieve tickets for a specific user:

`GET /api/account/1031/transactions`

Retrieve all tickets for all users:

`GET /api/account/all/transactions`

### Query Params

| key       | Type    | Description                                                                    |
| --------- | ------- | ------------------------------------------------------------------------------ |
| status    | string  | A filter to be applied to the query. One of: `Accepted`, `Rejected`, `Pending` |
| limit     | integer | The amount of items per page. (default = 10)                                   |
| offset    | integer | From where to start.                                                           |
| orderBy   | string  | The property to be used for sorting (with a - as a prefix for desc order)      |
| startDate | string  | Filter by startDate `MM/DD/YYYY`                                               |
| endDate   | string  | Filter by endDate `MM/DD/YYYY`                                                 |
| orderType | string  | A filter to be applied to the query. One of: `pay-in`, `pay-out`               |
