# Initialize Checkout Flow

> Example
> Form Data Content

```javascript
{
    "version": 1,
    "type": "Deposit",
    "consumer": "Consumer Name",
    "transactionRef": "ee463315-8522-4b77-92ff-cb5705313731",
    "destinationWalletAddress": "1CSprwPi9KtGToVcAC3i5DF4DuF66zNoGy",
    "destinationAsset": "BTC",
    "originAsset": "BRL",
    "checkoutAmount": 99,
    "feeAmount": 1,
    "consumerUserEmail": "example@mail.com",
    "consumerUserId": "60176823-206c-49b7-8288-bdb3fed628c6",
    "countryCode": "BR",
    "quote": 37679.15,
    "callbackUrl": "https://www.your-domain.com/es/user/wallet/deposit/BTC"
}
```

```javascript
{
    "version": 1,
    "type": "Withdraw",
    "consumer": "Consumer Name",
    "transactionRef": "ee463315-8522-4b77-92ff-cb5705313731",
    "destinationAsset": "BTC",
    "originAsset": "BRL",
    "checkoutAmount": 0.0999,
    "feeAmount": 0.0001,
    "consumerUserEmail": "example@mail.com",
    "consumerUserId": "60176823-206c-49b7-8288-bdb3fed628c6",
    "countryCode": "BR",
    "quote": 37207.16,
    "callbackUrl": "https://www.your-domain.com/es/user/wallet/withdraw/BTC"
}
```

> <strong>Note:</strong> As the response of the POST is a 303, XHR requests won’t work. The request must be performed sending the form data by posting it using a form and a form action.

> <strong>Note:</strong> All fields sent to this endpoint must be previously encrypted. Encryption method and instructions are provided on a separate document.

> Response Headers:

```javascript
{
    "set-cookie": checkout.session={{latamex.checkout.cookie}}
    "status": 303,
    "location": {{latamex.checkout.url}}
}
```

### HTTP Request

`POST /api/checkout/new`

### Form Data

| key                         | Type    | Description                                                                                                  |
| --------------------------- | ------- | ------------------------------------------------------------------------------------------------------------ |
| version                     | integer | <strong>required</strong> - The checkout flow version                                                        |
| type                        | string  | <strong>required</strong> - The type of checkout. (<strong>Deposit</strong> or <strong>Withdraw</strong>)    |
| consumer                    | string  | <strong>required</strong> - The consumer identifier that is initializing the checkout                        |
| consumerUserEmail           | string  | <strong>required</strong> - The user email                                                                   |
| consumerUserId              | string  | <strong>required</strong> - UUID that identifies the user                                                    |
| countryCode                 | string  | <strong>required</strong> - One of: <strong>AR</strong>, <strong>BR</strong>                                 |
| transactionRef              | string  | <strong>required</strong> - Unique Key to identify transaction between both systems.                         |
| destinationWalletAddress    | string  | <strong>required</strong> - The wallet that will receive the funds. Only used with type = Deposit            |
| destinationWalletAddressTag | string  | <strong>optional</strong> - Extra data of wallet that will receive the funds. Only used with type = Deposit  |
| originWalletAddress         | string  | <strong>optional</strong> - The wallet that will send the funds. Only used with type = Withdraw              |
| originWalletAddressTag      | string  | <strong>optional</strong> - Extra data of wallet that will receive the funds. Only used with type = Withdraw |
| destinationAsset            | string  | <strong>required</strong> - The asset to be sent                                                             |
| originAsset                 | string  | <strong>required</strong> - The asset that we will receive during checkout                                   |
| checkoutAmount              | real    | <strong>required</strong> - The total amount on originAsset to be sent                                       |
| feeAmount                   | real    | <strong>required</strong> - The total fee on originAsset                                                     |
| quote                       | real    | <strong>required</strong> - The quote at the moment of starting the checkout flow                            |
| callbackUrl                 | string  | <strong>required</strong> - The url where we will redirect the user once the flow is completed               |
