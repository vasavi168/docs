# Check Account Balance

#### GET
```
/account/balance
```

You can get the account balance of each service using this api.

#### Example Request

```curl
  curl -X GET \
  {endpoint}account/balance \
  -H 'Authorization: Bearer 209eccd40ee3a2e14af7fe45b21xxx'
```

#### Example Response

```json
{
    "status": 200,
    "message": "OK",
    "data": [
        {
            "service": "P",
            "name": "Promotional SMS",
            "postpaid": 0,
            "credits": 69,
            "charges": 1
        },
        {
            "service": "T",
            "name": "Transactional SMS",
            "postpaid": 0,
            "credits": 109,
            "charges": 1
        }
    ]
}
```