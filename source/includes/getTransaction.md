# Get Transaction

> Response Example

```javascript
{
  "data": {
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
}
```

### HTTP Request

`GET /api/transaction/{id}`

### Headers (see Authentication section)

| key           | Type   | Description                                                                |
| ------------- | ------ | -------------------------------------------------------------------------- |
| Authorization | string | <strong>required</strong> - Example: Token eyJhbGciOiJIUzI1NiIsInR5cCI6Ikp |
