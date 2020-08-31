# Create Transaction

> Response Example:

```javascript
{
  "transaction": {
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
  "kyc": {
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

`POST /api/transaction`

### Payload

| key                | Type    | Description                                                                                                                                                                                                                                                          |
| ------------------ | ------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| name               | string  | <strong>required</strong> - The user's name                                                                                                                                                                                                                          |
| lastname           | string  | <strong>required</strong> - The users's lastname                                                                                                                                                                                                                     |
| fatherLastname     | string  | <strong>optional</strong> - Used only for mexican users                                                                                                                                                                                                              |
| motherLastname     | string  | <strong>optional</strong> - Used only for mexican users                                                                                                                                                                                                              |
| born               | string  | <strong>required</strong> - The user's date of birth                                                                                                                                                                                                                 |
| gender             | string  | <strong>required</strong> - The user's gender. One of: <strong>F</strong>, <strong>M</strong>                                                                                                                                                                        |
| nationalId         | string  | <strong>required</strong> - The user's national ID                                                                                                                                                                                                                   |
| phoneNumber        | string  | <strong>required</strong> - The user's phone number                                                                                                                                                                                                                  |
| street             | string  | <strong>required</strong> - The user's address street                                                                                                                                                                                                                |
| number             | string  | <strong>required</strong> - The user's address street number                                                                                                                                                                                                         |
| floor              | string  | <strong>optional</strong> - The user's building floor                                                                                                                                                                                                                |
| unit               | string  | <strong>optional</strong> - The user's building unit                                                                                                                                                                                                                 |
| zip                | string  | <strong>required</strong> - The user's address zip code                                                                                                                                                                                                              |
| province           | string  | <strong>required</strong> - The province where the user leaves                                                                                                                                                                                                       |
| city               | string  | <strong>required</strong> - The city where the user leaves                                                                                                                                                                                                           |
| colony             | string  | <strong>optional</strong> - The colony where the user leaves                                                                                                                                                                                                         |
| occupation         | string  | <strong>required</strong> - What the user does for a leaving                                                                                                                                                                                                         |
| occupationCategory | string  | <strong>required</strong> - The category of the user's job. One of: <strong>employee</strong>, <strong>self-employed</strong>, <strong>civil-servant</strong>, <strong>ONG</strong>, <strong>entrepreneur</strong>, <strong>student</strong>, <strong>other</strong> |
| type               | string  | <strong>required</strong> - The type of the transaction. One of <strong>Deposit</strong>, <strong>Withdraw</strong>                                                                                                                                                  |
| isPEP              | boolean | <strong>required</strong> - Whether the user is a Political Exposed Person or not                                                                                                                                                                                    |
| isOs               | boolean | <strong>required</strong> - Whethet the user is an Obligated Subject or not                                                                                                                                                                                          |
| amount             | real    | <strong>required</strong> - The total amount to transact                                                                                                                                                                                                             |
| consumer           | string  | <strong>required</strong> - The consumer identifier that is creating the transaction                                                                                                                                                                                 |
| consumerUserEmail  | string  | <strong>required</strong> - The user email                                                                                                                                                                                                                           |
| consumerUserId     | string  | <strong>required</strong> - UUID that identifies the user                                                                                                                                                                                                            |
| countryCode        | string  | <strong>required</strong> - One of: <strong>AR</strong>, <strong>BR</strong>, <strong>MX</strong>                                                                                                                                                                    |
| transactionRef     | string  | <strong>required</strong> - Unique Key to identify transaction between both systems.                                                                                                                                                                                 |
| target             | string  | <strong>optional</strong> - Where the payment is going to land. One of: <strong>balance</strong>, <strong>wallet</strong>. Default: <strong>balance</                                                                                                                |
| originAsset        | string  | <strong>required</strong> - The asset that the user is going to use to pay. One of: <strong>ARS</strong>, <strong>BRL</strong>, <strong>MXN</strong>                                                                                                                 |
