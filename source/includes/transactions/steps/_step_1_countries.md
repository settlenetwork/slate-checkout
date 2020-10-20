# Step 1 Countries

> Payload Example:

```javascript
axiosLoggedIn.get(`${server}/api/v2/countries`).then(function (result) {
  console.log(result.data);
});
```

> Response Example:

```javascript
{
    "countries": [
        "BR",
        "MX",
        "AR"
    ]
}
```

### Http Request

`GET /api/v2/countries`
