# Get Transactions

> Response Example

```javascript
{
  "data": [
    {
       "_id": 2986,
        "type": "Deposit",
        "amount": 20000,
        "originAsset": "BRL",
        "consumer": "consumer_name"
        "consumerUserEmail": 20,
        "consumerUserId": "1ss4d1ed-987b-3f34-1a0e-11223f32ce17",
        "countryCode": "BR",
        "transactionRef": "9dder3ef-222b-3d92-2a0e-123453f4c329"
        "target": "balance"
    },
    ...
  ],
  "total": 2896
}
```

### HTTP Request

`GET /api/account/{id}/transactions`

<aside class="notice">
  Note: {id} could be the “user id” (see consumerUserId in response) as well as “all” as wildcard to retrieve all the transactions from all users.
</aside>
 
Examples:

Retrieve tickets for a specific user:

`GET /api/account/bae42210-d136-4832-afad-ebfbace4eb3a/transactions`

Retrieve all tickets for all users:

`GET /api/account/all/transactions`

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
