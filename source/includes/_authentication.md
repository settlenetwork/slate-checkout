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
Based on the xRamp user role, a different set of permission policies and scope will be
granted to each user login into the system.

In terms of third-party integrations, the role given is Consumer, which has the
ability to get tickets by Id or account Id.

### Payload

| key      | Type    | Description                                            |
| -------- | ------- | ------------------------------------------------------ |
| email    | integer | <strong>required</strong> - Email provided by xRamp    |
| password | string  | <strong>required</strong> - Password provided by xRamp |
