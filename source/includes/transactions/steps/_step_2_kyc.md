# Step 2.a KYC Created

> Payload Example:

```javascript
const kycId = 1031;
axiosLoggedIn.get(`${server}/api/v2/kyc/${kycId}`).then(function (result) {
  console.log(result.data);
});
```

> Response Example:

```javascript
{
    "kyc": {
        "kycId": "1031",
        "status": "Accepted",
        "partnerUserId": "112233",
        "txRef": "john-smith",
        "born": "16/09/1983",
        "gender": "M",
        "nationality": "AR",
        "nationalIdType": "national-id",
        "nationalIdNumber": "11222333",
        "taxIdNumber": "20112223331",
        "phoneNumber": "91133388899",
        "email": "john@mail.com",
        "name": "John",
        "lastname": "Smith",
        "residenceCountry": "AR",
        "street": "Av Park",
        "number": "4462",
        "zip": "CBR0110",
        "province": "CABA",
        "city": "CABA",
        "occupation": "Developer",
        "occupationCategory": "self-employed",
        "isPEP": false,
        "isOS": false,
        "imageIdFront": "https://KYC_SERVER/api/kyc/images/1031_Declarative_id-front_1597247222153",
        "imageIdBack": "https://KYC_SERVER/api/kyc/images/1031_Declarative_id-back_1597247222216",
        "imageSelfie": "https://KYC_SERVER/api/kyc/images/1031_Declarative_selfie_1597247222171"
    }
}
```

In case of having already registered in our system the user's KYC, you can obtain with this endpoint the data that we have saved in our system referring to this user, mainly the `residenceCountry` field with which we verify if said user has a country supported by the list obtained in `step 1)`. If there is no such country, this user will not be able to operate transactions.

`[GET] /api/v2/kyc/{kycId}`

# Step 2.b KYC Not Created

> Payload Example:

```javascript
const payload = {
  partnerUserId: "112233",
  txRef: "john-smith",

  born: "16/09/1983",
  gender: "M",
  nationality: "AR",
  nationalIdType: "national-id",
  nationalIdNumber: "11222333",
  taxIdNumber: "20112223331",

  phoneNumber: "91133388899",
  email: "john@mail.com",
  name: "John",
  lastname: "Smith",

  residenceCountry: "AR",
  street: "Av Park",
  number: "4462",
  zip: "CBR0110",
  province: "CABA",
  city: "CABA",

  occupation: "Developer",
  occupationCategory: "self-employed",
  isPEP: false,
  isOS: false,

  imageIdFront: "https://PARTNER_SERVER/id-front_1597247222153.jpg",
  imageIdBack: "https://PARTNER_SERVER/id-back_1597247222216.jpg",
  imageSelfie: "https://PARTNER_SERVER/selfie_1597247222171.jpg",
};

axiosLoggedIn.post(`${server}/api/v2/kyc`, payload).then(function (result) {
  console.log(result.data);
});
```

> Response Example:

```javascript
{
  "kycId": "1031",
  "status": "Accepted"
}
```

In case you have not created a KYC for said user in our system, you must create it taking into account the same limitation of `step 2.a` which refers to the existence of the `residenceCountry` field in the list of available countries

`[POST] /api/v2/kyc/{kycId}`

### Payload

| key                | Type    | Description                                                                                                                                                 |
| ------------------ | ------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| partnerUserId      | string  | <strong>required</strong> - UUID that identifies the user                                                                                                   |
| txRef              | string  | <strong>required</strong> - Unique Key to identify transaction between both systems                                                                         |
| born               | string  | <strong>required</strong> - The user's date of birth                                                                                                        |
| gender             | string  | <strong>required</strong> - The user's gender. One of: `F`, `M`                                                                                             |
| nationality        | string  | <strong>required</strong> - nationality of ID                                                                                                               |
| nationalIdType     | string  | <strong>required</strong> - The category of the user’s national type. One of: passport, national-id, driving-licence                                        |
| nationalIdNumber   | string  | <strong>required</strong> - The user's ID from national type selected                                                                                       |
| taxIdNumber        | string  | <strong>required</strong> - `CUIT` for `AR`, `CPF` for `BR`, `RFC` for `MX`                                                                                 |
| phoneNumber        | string  | <strong>required</strong> - The user's phone number                                                                                                         |
| email              | string  | <strong>required</strong> - The user email                                                                                                                  |
| name               | string  | <strong>required</strong> - The user's name                                                                                                                 |
| lastname           | string  | <strong>required_except_MX</strong> - The user's lastname                                                                                                   |
| fatherLastname     | string  | <strong>required_only_MX</strong> - Used only for mexican users                                                                                             |
| motherLastname     | string  | <strong>required_only_MX</strong> - Used only for mexican users                                                                                             |
| residenceCountry   | string  | <strong>required</strong> - country where user resides                                                                                                      |
| street             | string  | <strong>required</strong> - The user's address street                                                                                                       |
| number             | string  | <strong>required</strong> - The user's address street number                                                                                                |
| floor              | string  | <strong>optional</strong> - The user's building floor                                                                                                       |
| unit               | string  | <strong>optional</strong> - The user's building unit                                                                                                        |
| zip                | string  | <strong>required</strong> - The user's address zip code                                                                                                     |
| province           | string  | <strong>required</strong> - The province where the user leaves                                                                                              |
| city               | string  | <strong>required</strong> - The city where the user leaves                                                                                                  |
| colony             | string  | <strong>optional</strong> - The colony where the user leaves                                                                                                |
| occupation         | string  | <strong>required</strong> - What the user does for a leaving                                                                                                |
| occupationCategory | string  | <strong>required</strong> - The category of the user's job. One of: `employee`, `self-employed`, `civil-servant`, `ONG`, `entrepreneur`, `student`, `other` |
| isPEP              | boolean | <strong>required</strong> - Whether the user is a Political Exposed Person or not                                                                           |
| isOS               | boolean | <strong>required</strong> - Whether the user is an Obligated Subject or not                                                                                 |
| imageIdFront       | string  | <strong>required</strong> - url with hosted national ID front                                                                                               |
| imageIdBack        | string  | <strong>required</strong> - url with hosted national ID back                                                                                                |
| imageSelfie        | string  | <strong>required</strong> - url with selfie of user holding national ID front                                                                               |
| imageAddressProof  | string  | <strong>required_if</strong> - residenceCountry != nationality                                                                                              |
