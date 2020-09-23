# Authentication

> Payload Example:

```javascript
const axios = require("axios");

const axiosLoggedIn = axios.create({
  headers: {
    "x-api-key": "e90770ad-bc53-464b-8dcb-8b216c6171f8",
  },
});
```

### Api Key

To consume these resources, it’s used as an authentication mechanism, API-KEY method.
This api-key is provided by Settle by a partner. There can be more than one.
