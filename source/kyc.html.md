---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - javascript

toc_footers:
  - <a href='https://settlenetwork.com'>Visit Settle Network</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the xRamp Kyc API Documentation! Here you will find all the information and examples needed to perform your integration with our kyc product.

# CheckCode (PRIVATE)

> Payload Example:

```javascript
{
  "phoneNumber": 1155446677,
  "phoneCountryCode": "54",
  "code": "AR"
}
```

> Response Example:

```javascript
{
  "data": {
      "xxxxx": "xxxxx"
  }
}
```

### HTTP Request

`POST /api/kyc/check-code`

Check a code to phone number.

### Payload

| key              | Type   | Description                        |
| ---------------- | ------ | ---------------------------------- |
| phoneNumber      | string | The user's phone number            |
| phoneCountryCode | string | The user's country code            |
| code             | string | The code received in phone message |

# Info

> Response Example:

```javascript
{
    "data": {
        "idType": "DNI",
        "processMethod": "automatic",
        "status": "Accepted",
        "verifiedFlows": [
            "LivenessCheck"
        ],
        "fullyProcessed": true,
        "flagged": false,
        "history": [],
        "_id": 1001,
        "email": "johndoe@gmail.com",
        "internalNotes": [],
        "images": [],
        "files": [],
        "webhooks": [],
        "identityChecks": [],
        "createdTimestamp": "2020-03-02T20:14:05.116Z",
        "lastUpdateTimeStamp": "2020-03-02T20:17:01.260Z",
        "typeLevel": 2,
        "typeName": "LivenessCheck",
        "born": "1982-03-01",
        "country": "AR",
        "nationalId": "33445566",
        "consumer": "latamex",
        "gender": "M",
        "lastname": "Doe",
        "name": "John",
        "city": "caba",
        "number": "25",
        "province": "Ciudad Autónoma de Buenos Aires",
        "street": "25 de mayo",
        "zip": "1244",
        "isOS": false,
        "isPEP": false,
        "occupation": "Director",
        "isDataCompleted": true
    }
}
```

### HTTP Request

`GET /api/kyc/info`

Return the user information.

### Query Params

| key   | Type   | Description    |
| ----- | ------ | -------------- |
| email | string | The user email |

# Info basic

> Payload Example:

```javascript
{
  "name": "John",
  "lastname": "Doe",
  "born": "11/11/2020",
  "gender": "m",
  "nationalId": "2343435454",
   "street": "Rivadavia",
   "number": "125",
   "floor": "1",
   "unit": "a",
   "province": "Buenos Aires",
   "city": "Ciudad autonoma de Buenos Aires",
   "zip" : "1218",
   "occupation": "Director",
   "isPEP": false,
   "isOS": false
}
```

> Response Example

```javascript
{
    "data": {
        "idType": "DNI",
        "processMethod": "automatic",
        "status": "Incomplete",
        "verifiedFlows": [],
        "fullyProcessed": false,
        "flagged": false,
        "history": [],
        "_id": 1002,
        "email": "operator@settlenetwork.com",
        "internalNotes": [],
        "images": [],
        "files": [],
        "webhooks": [],
        "identityChecks": [],
        "createdTimestamp": "2020-03-03T15:22:17.873Z",
        "lastUpdateTimeStamp": "2020-03-03T15:24:44.167Z",
        "born": "11/11/2020",
        "city": "Ciudad autonoma de Buenos Aires",
        "floor": "1",
        "gender": "m",
        "isOS": false,
        "isPEP": false,
        "lastname": "Doe",
        "name": "John",
        "nationalId": "2343435454",
        "number": "125",
        "occupation": "Director",
        "province": "Buenos Aires",
        "street": "Rivadavia",
        "unit": "a",
        "zip": "1218"
    }
}
```

### HTTP Request

`POST /api/kyc/info/basic`

Upload the user information.

### Payload

| key        | Type   | Description               |
| ---------- | ------ | ------------------------- |
| name       | string | The first name to be load |
| lastname   | string | The last name to be load  |
| born       | string | The birthday to be load   |
| gender     | string | The gender to be load     |
| nationalId | string | The nationalId to be load |
| street     | string | The street to be load     |
| number     | string | The number to be load     |
| floor      | string | The floor to be load      |
| unit       | string | The unit to be load       |
| province   | string | The province to be load   |
| city       | string | The city to be load       |
| zip        | string | The zip to be load        |
| country    | string | The country to be load    |
| occupation | string | The occupation to be load |
| isPEP      | string | The isPEP to be load      |
| isOS       | string | The isOS to be load       |

# Send code

> Payload Example:

```javascript
{
    "data": {
        "message": "code sent to mail"
    }
}
```

> Response Example

```javascript
{
    "xxxxx": "xxxxx"
}
```

### HTTP Request

`Post /api/kyc/send-code`

Send a code to phone number.

### Payload

| key              | Type   | Description             |
| ---------------- | ------ | ----------------------- |
| phoneNumber      | string | The user's phone number |
| phoneCountryCode | string | The user's country code |

# KYC

> Payload Example:

```javascript
{
  "status": "Accepted",
  "internalNote": "Approved",
  "fullyProcessed": true,
  "flagged": false
}
```

> Response Example

```javascript
{
    "data": {
        "idType": "DNI",
        "processMethod": "automatic",
        "status": "Accepted",
        "verifiedFlows": [
            "LivenessCheck"
        ],
        "fullyProcessed": true,
        "flagged": false,
        "history": [],
        "_id": 1003,
        "email": "johndoe@settlenetwork.com",
        "internalNotes": [
            {
                "_id": "5e5ee869b63a6c92045b2638",
                "note": "Test",
                "createdTimestamp": "1583278185293"
            }
        ],
        "images": [],
        "files": [],
        "webhooks": [],
        "identityChecks": [],
        "createdTimestamp": "2020-03-03T20:55:23.100Z",
        "lastUpdateTimeStamp": "2020-03-04T14:09:33.135Z",
        "typeLevel": 2,
        "typeName": "LivenessCheck",
        "born": "1986-02-02",
        "country": "AR",
        "nationalId": "33445566",
        "consumer": "latamex",
        "gender": "M",
        "lastname": "Doe",
        "name": "John",
        "city": "caba",
        "number": "25",
        "province": "Ciudad Autónoma de Buenos Aires",
        "street": "25 de mayo",
        "zip": "1251",
        "isOS": false,
        "isPEP": false,
        "occupation": "Director",
        "isDataCompleted": true
    }
}
```

### HTTP Request

`Patch /api/kyc/{id}`

Upload the user information with admin permissions.

### Query Params

| key | Type   | Description                            |
| --- | ------ | -------------------------------------- |
| id  | string | <strong>required</strong> - The kyc id |

### Payload

| key            | Type    | Description                    |
| -------------- | ------- | ------------------------------ |
| status         | string  | The status to be load          |
| internalNote   | string  | The internal note to be load   |
| fullyProcessed | boolean | The fully processed to be load |
| flagged        | boolean | The flagged be load            |

# KYCS

> Response Example

```javascript
{
    "data": [
        {
            "idType": "DNI",
            "processMethod": "automatic",
            "status": "Incomplete",
            "verifiedFlows": [],
            "fullyProcessed": false,
            "flagged": false,
            "history": [],
            "_id": 1004,
            "email": "elvis@settlenetwork.com",
            "files": [],
            "createdTimestamp": "2020-03-03T21:10:26.656Z",
            "lastUpdateTimeStamp": "2020-03-03T21:28:21.290Z",
            "phoneCountryCode": "54",
            "phoneNumber": "1166789045"
        },
        {
            "idType": "DNI",
            "processMethod": "automatic",
            "status": "Accepted",
            "verifiedFlows": [
                "LivenessCheck"
            ],
            "fullyProcessed": true,
            "flagged": false,
            "history": [],
            "_id": 1003,
            "email": "johndoe@settlenetwork.com",
            "files": [],
            "createdTimestamp": "2020-03-03T20:55:23.100Z",
            "lastUpdateTimeStamp": "2020-03-03T21:00:18.389Z",
            "typeLevel": 2,
            "typeName": "LivenessCheck",
            "born": "1982-02-02",
            "country": "AR",
            "nationalId": "33445566",
            "consumer": "latamex",
            "gender": "M",
            "lastname": "Doe",
            "name": "John",
            "city": "caba",
            "number": "25",
            "province": "Ciudad Autónoma de Buenos Aires",
            "street": "25 de mayo",
            "zip": "1251",
            "isOS": false,
            "isPEP": false,
            "occupation": "Programador",
            "isDataCompleted": true
        }
    ],
    "total": 2
}
```

### HTTP Request

`Get /api/kycs`

Return all kycs.

# Comment (PRIVATE)

> Payload Example:

```javascript
{
  "internalNote": "approved"
}
```

> Response Example

```javascript
{
    "xxxxx": "xxxxx"
}
```

### HTTP Request

`Patch /api/kyc/{id}/comment`

Add comment in kyc.

### Query Params

| key | Type   | Description                            |
| --- | ------ | -------------------------------------- |
| id  | string | <strong>required</strong> - The kyc id |

### Payload

| key          | Type   | Description                  |
| ------------ | ------ | ---------------------------- |
| internalNote | string | The internal note to be load |

# Status

> Response Example

```javascript
{
    "status": "Accepted"
}
```

### HTTP Request

`Get /api/kyc/status`

Verify status.

### Query Params

| key   | Type   | Description    |
| ----- | ------ | -------------- |
| email | string | The user email |

# Images

> Response Example

```javascript
{
    "data": "xxxxxxx"
}
```

### HTTP Request

`Get /api/kyc/images/{file}`

Retrieve images.

### Query Params

| key  | Type   | Description                                   |
| ---- | ------ | --------------------------------------------- |
| file | string | <strong>required</strong> - The received file |

# Images

> Payload Example:

```javascript
{
    "maxBytes": 1000 * 1000 * 8,
    "output": "stream"
}
```

> Response Example

```javascript
{
    "xxxxx": "xxxxx"
}
```

### HTTP Request

`Post /api/kyc/images`

Retrieve images.

### Payload

| key      | Type   | Description   |
| -------- | ------ | ------------- |
| maxBytes | number | The max bytes |
| output   | string | The stream    |

# Reset (PRIVATE)

> Payload Example:

```javascript
{
  "internalNote": "Test"
}
```

> Response Example

```javascript
{
    "data": "xxxxxx"
}
```

### HTTP Request

`Patch /api/kyc/{id}/reset`

Reset kyc data.

### Query Params

| key | Type   | Description                            |
| --- | ------ | -------------------------------------- |
| id  | string | <strong>required</strong> - The kyc id |

### Payload

| key          | Type   | Description                                   |
| ------------ | ------ | --------------------------------------------- |
| internalNote | string | <strong>required</strong> - The internal note |

# Verify national ID

> Response Example

```javascript
{
    "exist": false
}
```

### HTTP Request

`Get /api/verifyNationalId`

Verify national id.

### Query Params

| key         | Type   | Description                                   |
| ----------- | ------ | --------------------------------------------- |
| id          | string | <strong>required</strong> - The kyc id        |
| dob         | string | <strong>required</strong> - The date of birth |
| countryCode | string | <strong>required</strong> - The country code  |

# File attachment

> Payload Example:

```javascript
{
  "uri": "uri",
  "filename": "filename",
  "description": "description",
  "type": "type"
}
```

> Response Example

```javascript
{
    "xxxxx": "xxxxx"
}
```

### HTTP Request

`Patch /api/kyc/{id}/file`

Add File Attachment.

### Query Params

| key | Type   | Description                            |
| --- | ------ | -------------------------------------- |
| id  | string | <strong>required</strong> - The kyc id |

### Payload

| key         | Type   | Description                                    |
| ----------- | ------ | ---------------------------------------------- |
| uri         | string | <strong>required</strong> - The uri to be load |
| filename    | string | The file name to be load                       |
| description | string | The description to be load                     |
| type        | string | The type file                                  |
