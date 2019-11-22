---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - javascript

toc_footers:
  - <a href='https://latamex.com'>Visit Latamex</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Latamex Checkout API Documentation! Here you will find all the information and examples needed to perform your integration with our checkout product.

# Authentication

> Payload Example:

```javascript 
{
  "email": "example@email.com",
  "password": "yourPasswordHere"
}
```

> Response Example:

```javascript
{
  "data": {
      "role": "consumer",
      "_id": 53,
      "email": "example@email.com",
      "name": "Consumer Name",
      "accounts": [],
      "webhooks": []
  },
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6ImJpbmFuY2VAYmluYW5jZS5jb20iLCJuYW1lIjoiQmluYW5jZSIsImlhdCI6MTU2ODAzNjk5MCwiZXhwIjoxNTY4MDQwNTkwfQ.bVRsaN4nbH5-GPNb1466r9lEOYICjRYhqmNbkz4bvSw"
}

```
### HTTP Request
`POST /api/auth/login`

For the API to be accessed, a valid session token needs to be provided.

The session token is retrieved upon send of a set of credentials to the login endpoint.
Access to the endpoints provided on this document, will be granted according to the RBA
described below.
 
A short-lived token is retrieved by the login endpoint and expires after 1 hour.
 
Role Based Authentication Details
Based on the Latamex user role, a different set of permission policies and scope will be
granted to each user login into the system.
 
In terms of third-party integrations, the role given is Consumer, which has the
ability to get tickets by Id or account Id.

### Payload

key | Type | Description
--------- | ------- | -----------
email | integer | <strong>required</strong> - Email provided by Latamex
password | string | <strong>required</strong> - Password provided by Latamex


# Get Asset Quote

> Response Example:

```javascript
{
  "quote": 559695.6857328482,
  "fromAssetMinAmount": 0.001,
  "toAssetMinAmount": 559.6956857328482,
  "dailyLimit": 250000,
  "fee": 1.5,
  "minFee": 300
}
```
><strong>Note:</strong> The "fee" field is expressed as percentage. In this example it would be 1.5%.

### HTTP Request
`GET /api/quotes`

### Query Params

key | Type | Description
--------- | ------- | -----------
fromAsset | string | <strong>required</strong> -  The asset to return the quote about
toAsset | string | <strong>required</strong> -  The asset used to represent the quote
type | string | <strong>Sell, Buy</strong> - Default: <strong>Sell</strong> (Sell for deposit / Buy for withdraw)

### Current Supported Assets for Sell type (Deposit)

key | Value 
--------- | -------
fromAsset | BTC, BNB, ETH, LTC
toAsset | ARS, BRL
type | Sell

### Current Supported Assets for Sell type (Withdraw)

key | Value 
--------- | -------
fromAsset | ARS, BRL
toAsset | BTC, BNB, ETH, LTC
type | Buy

# Initialize Checkout Flow

> Response Headers:

```javascript
{
    "set-cookie": checkout.session={{latamex.checkout.cookie}}
    "status": 303,
    "location": {{latamex.checkout.url}}
}
```

> Example
> Form Data Content

```javascript
{
    "version": 1,
    "type": "Deposit",
    "consumer": "Consumer Name",
    "destinationWalletAddress": "1CSprwPi9KtGToVcAC3i5DF4DuF66zNoGy",
    "destinationAsset": "BTC",
    "originAsset": "ARS",
    "checkoutAmount": 1500,
    "consumerUserEmail": "example@mail.com",
    "consumerUserId": "60176823-206c-49b7-8288-bdb3fed628c6",
    "countryCode": "AR",
    "quote": 530945.15,
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
    "originAsset": "ARS",
    "checkoutAmount": 0.001,
    "consumerUserEmail": "example@mail.com",
    "consumerUserId": "60176823-206c-49b7-8288-bdb3fed628c6",
    "countryCode": "AR",
    "quote": 530945.15,
    "callbackUrl": "https://www.your-domain.com/es/user/wallet/withdraw/BTC"
}
```

><strong>Note:</strong> As the response of the POST is a 303, XHR requests won’t work. The request must be performed sending the form data by posting the data using a form and a form action.

### HTTP Request
`POST /api/checkout/new`

### Form Data

key | Type | Description
--------- | ------- | -----------
version | integer | <strong>required</strong> - The checkout flow version
type | string | <strong>required</strong> - The type of checkout. (<strong>Deposit</strong> or <strong>Withdraw</strong>)
consumer | string | <strong>required</strong> - The consumer identifier that is initializing the checkout
consumerUserEmail | string | <strong>required</strong> - The user email
consumerUserId | string | <strong>required</strong> - UUID that identifies the user
countryCode | string | <strong>required</strong> - One of: <strong>AR</strong>, <strong>BR</strong>
transactionRef | string | <strong>required</strong> - Unique Key to identify transaction between both systems. Only used with <strong>type = Withdraw</strong>
destinationWalletAddress | string | <strong>required</strong> - The wallet that will receive the funds. Only used with type = Deposit
destinationWalletAddressTag | string | <strong>optional</strong> - Extra data of wallet that will receive the funds. Only used with type = Deposit
destinationAsset | string | <strong>required</strong> - The asset to be sent
originAsset | string | <strong>required</strong> - The asset that we will receive during checkout
checkoutAmount | real | <strong>required</strong> - The total amount on originAsset to be sent
quote | real | <strong>required</strong> - The quote at the moment of starting the checkout flow
callbackUrl | string | <strong>required</strong> - If present, we will send the user back to this url once the flow is finished

# Get Deposit Tickets

> Response Example (Pending Ticket)

```javascript
{
 "data": [
   {
     "depositId": 1234,
     "method": "bank-transfer",
     "countryCode": "AR",
     "status": "Pending",
     "createdTimestamp": "Thu Aug 29 2019 18:56:48 GMT-0300 (Argentina Standard Time)",
     "lastUpdateTimeStamp": "Thu Aug 30 2019 18:56:48 GMT-0300 (Argentina Standard Time)",
     "destinationWalletAddress": "1FfmbHfnpaZjKFvyi1okTjJJus4455paPH",
     "destinationAsset": "BTC",
     "originAsset": "ARS",
     "checkoutAmount": 600,
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
      "countryCode": "AR",
      "status": "Accepted",
      "createdTimestamp": "Thu Aug 29 2019 18:56:48 GMT-0300 (Argentina Standard Time)",
      "lastUpdateTimeStamp": "Thu Aug 30 2019 18:56:48 GMT-0300 (Argentina Standard Time)",
      "destinationWalletAddress": "1FfmbHfnpaZjKFvyi1okTjJJus4455paPH",
      "destinationAsset": "NEO",
      "originAsset": "ARS",
      "checkoutAmount": 600,
      "consumerUserId": "bae42210-d136-4832-afad-ebfbace4eb3a",
      "paidQuote": 600,
      "callbackUrl": "https://www.your-domain.com/es/user/wallet/deposit/BTC",
      "fee": 10,
      "providerWithdrawId": "60d354c910874531b9268d476bb01d42",
      "providerWithdrawMsg": "Success",
      "paidAmount": 1,
      "txId": "fdf6e560dc317cc92f94bf6be639f86f503ddae224354d0a3cca1ba5ce14ac8e"
    },
    ...
  ],
  "total": 10
}
```

### HTTP Request
`GET /api/account/{id}/deposits`

FYI: {id} could be the “user id” (see consumerUserId in response) as well as “all” as wildcard to retrieve all the tickets from all users.
 
Examples: 
    Retrieve tickets for a specific user:
`GET /api/account/bae42210-d136-4832-afad-ebfbace4eb3a/deposits`
    Retrieve all tickets for all users: 
`GET /api/account/all/deposits`

### Query Params
key | Type | Description
--------- | ------- | -----------
status | string | A filter to be applied to the query. One of: <strong>Accepted, Rejected, Pending</strong>
limit | integer | The amount of items per page. (default = 1000)
offset | integer | From where to start.
orderBy | string | The property to be used for sorting (with a - as a prefix for desc order)

### Headers (see Authentication section)
key | Type | Description
--------- | ------- | -----------
Authorization | string | <strong>required</strong> - Example: Token eyJhbGciOiJIUzI1NiIsInR5cCI6Ikp



# Get Withdraw Status

> Response Example (Pending Ticket)

```javascript
{
     "status": "Checkout_Pending"
}
```

> Response Example (Rejected Ticket)

```javascript
{
      "status": "Checkout_Rejected",
      "countryCode": "Limit_Rejected",
}
```

### HTTP Request
`GET /api/withdraw/status?ref={refValue}`

<strong>NOTE: {refValue}</strong> must be the <strong>“transactionRef”</strong> sent during the Withdraw creation.
Example: `GET /api/withdraw/status?ref=ee463315-8522-4b77-92ff-cb5705313731`

### Headers (see Authentication section)
key | Type | Description
--------- | ------- | -----------
Authorization | string | <strong>required</strong> - Example: Token eyJhbGciOiJIUzI1NiIsInR5cCI6Ikp

### Result Data
key | Type | Description
--------- | ------- | -----------
status | string | One of: <strong>Checkout_Pending:</strong> First state when the Withdraw is created / <strong>Checkout_Rejected:</strong> An error occurred during the identity verification or limit validation / <strong>New:</strong> the identity verification and limit validation were executed successfully / <strong>Accepted:</strong> Entire Withdraw flow was completed / <strong>Rejected:</strong> After verification and validation flow, has an error.
reason | string | The reason in case status is <strong>Checkout_Rejected</strong> or <strong>Rejected</strong>, one of: <strong>Limit_Rejected:</strong> Limit enforcement rejected / <strong>KYC_Rejected:</strong> KYC (Know Your Customer) Rejected / <strong>Manual_Rejected:</strong> An operator or manager Rejected this Withdraw manually / <strong>Error {CustomValueLabel}:</strong> Custom Label Error


# Link Withdraw with BlockChain TxId 

> Request Example

```javascript
{
     "transactionRef": "ee463315-8522-4b77-92ff-cb5705313731",
     "txId": "0x72bcca6aa071e5b439e56684d9552433edc846b0a340701e192b2493f52b9d3e"
}
```

### HTTP Request
`POST /api/withdraw/link`

### Payload

key | Type | Description
--------- | ------- | -----------
transactionRef | string | <strong>required</strong> - Unique Key to identify transaction between both systems
txId | string | <strong>required</strong> - Transaction Id on BlockChain

### Headers (see Authentication section)
key | Type | Description
--------- | ------- | -----------
Authorization | string | <strong>required</strong> - Example: Token eyJhbGciOiJIUzI1NiIsInR5cCI6Ikp
