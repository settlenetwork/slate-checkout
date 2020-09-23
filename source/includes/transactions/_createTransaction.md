# Create Transaction

> Response Example:

```javascript
const payload = {
  txRef: "pay-in-00001",
  orderType: "pay-in",
  kycId: 1031,
  amount: 12000,
  asset: "ARS",
  paymentMethod: "bank-transfer",
  providerMethod: "bank",
  accountHolder: "0011111222212212",
};

axiosLoggedIn
  .post(`${server}/api/v2/transactions`, payload)
  .then(function (result) {
    console.log(result.data);
  });
```

> Response Example:

```javascript
{
    "id": 17,
    "status": "Pending",
    "amount": 12000,
    "feeAmount": 240,
    "netAmount": 11760,
    "instructions": [
        {
            "title": "Información muy importante sobre tu pago",
            "content": "En caso de no cumplir con todas estas indicaciones, tu pago no podrá ser identificado correctamente, pudiendo demorar, dificultar o extraviar tu transacción",
            "children": [
                {
                    "title": "Cuenta a tu nombre",
                    "content": "La transferencia debe realizarse únicamente desde una cuenta bancaria a tu nombre."
                },
                {
                    "title": "Incluir Nº de Referencia",
                    "content": "Deberás incluir el número de referencia (provisto en la siguiente pantalla) en el campo de concepto/referencia al momento de realizar la transferencia."
                },
                {
                    "title": "Importe Exacto",
                    "content": "El importe a enviar debe ser el importe exacto por el cual creaste la orden."
                }
            ]
        },
        {
            "title": "Datos para la transferencia",
            "content": "Por favor realiza una transferencia bancaria desde una cuenta a tu nombre, Carlos, Iglesias, por el importe exacto e incluye el número de referencia, si tu banco te permite esta opción, para que podamos identificar mejor tu pago. Si tu banco no te permite incluir el número de referencia, puedes ignorarlo.",
            "children": [
                {
                    "title": "Banco",
                    "content": "Banco Industrial"
                },
                {
                    "title": "Beneficiario",
                    "content": "Settle ARG S.A.S."
                },
                {
                    "title": "CBU",
                    "content": "3220001805006761180013"
                },
                {
                    "title": "Alias",
                    "content": "BIND.AR.PESOS"
                },
                {
                    "title": "CUIT",
                    "content": "1122333"
                },
                {
                    "title": "Nº Referencia",
                    "content": 17
                },
                {
                    "title": "Total"
                }
            ]
        }
    ]
}
```

### HTTP Request

`POST /api/v2/transaction`

### Payload

| key             | Type   | Description                                                                                                      |
| --------------- | ------ | ---------------------------------------------------------------------------------------------------------------- |
| txRef           | string | <strong>required</strong> - Unique Key to identify transaction between both systems                              |
| orderType       | string | <strong>required</strong> - The type of the transaction. One of pay-in, pay-out                                  |
| kycId           | string | <strong>required</strong> - Settle Kyc Id that identifies the user                                               |
| amount          | string | <strong>required</strong> - The total amount to transact                                                         |
| asset           | string | <strong>required</strong> - The asset that the user is going to use to pay. One of: `ARS`, `BRL`, `MXN`          |
| paymentMethod   | string | <strong>required</strong> - Payment Method selected                                                              |
| paymentProvider | string | <strong>required</strong> - Provider Method selected                                                             |
| accountHolder   | string | <strong>required_if</strong> - type = `pay-out` / paymentMethod = `bank-transfer` - Address to FIAT destination. |
