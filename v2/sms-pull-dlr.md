# PULL DLR STATUS

#### GET
```
{endpoint}sms/status?id=469ea920-ccd1-4a39-b728-c0b6f15f6aa6:1&token=209eccd40ee3a2e14af7fe45b2xxxx
```

You can send sms using `POST` or `GET` methods, GET method requires data should be url_encoded.

####  ACCEPTED PARAMETERS

| Name     | Descriptions |
|----------|--------------|
| id | Message Id we have given in response|
| mobile | Mobile number with country code|
| cid | Your custom id|

you can pass any of the above params to get the dlr response

#### Example Request

```curl
curl -X GET \
  '{{base_url}}status?id=469ea920-ccd1-xxxx&access_token=209eccd40e45b21xxxx'
```

#### Example Response

```json
{
    "status": 200,
    "message": "OK",
    "data": [
        {
            "id": "469ea920-ccd1-4a39-b728-c0b6f15f6aa6:1",
            "mobile": "9189212693xx",
            "status": "DELIVRD",
            "units": 1,
            "length": 7,
            "charges": 1,
            "custom": "",
            "custom1": "",
            "location": "",
            "provider": "",
            "submitted_at": "2018-07-06 09:57:42",
            "delivered_at": "2018-07-06 21:57:42"
        }
    ]
}
```