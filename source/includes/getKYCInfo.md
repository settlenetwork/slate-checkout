# Get KYC Information

> Response Example

```javascript
{
    "data": {
        "_id": 90862,
        "name": "John",
        "lastname": "Doe",
        "born": "1967-10-24 00:00:00.000Z",
        "gender": "M"
        "nationalId": "23100299900",
        "phoneNumber": "11991234567",
        "street": "Rua Ana Castro Duarte do Pateo",
        "number": "1796",
        "zip": "13487-166",
        "province": "São Paulo",
        "city": "Limeira",
        "occupation": "Advogado",
        "occupationCategory": "self-employed",
        "isPEP": false,
        "isOS": false
    }
}
```

### HTTP Request

`GET /api/kyc/{id}`

### Headers (see Authentication section)

| key           | Type   | Description                                                                |
| ------------- | ------ | -------------------------------------------------------------------------- |
| Authorization | string | <strong>required</strong> - Example: Token eyJhbGciOiJIUzI1NiIsInR5cCI6Ikp |
