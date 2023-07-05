### Authentication Category

#### PARAMETERS

| name                      | optional | value                                       |
| ------------------------- | -------- | ------------------------------------------- |
| category                  | No       | `authentication`                            |
| header.type               | No       | `text`                                      |
| body_params               | No       | your verification code only one ex: 1287     |
| body                      | No       | Use defined content                         |
| security                  | No       | true, false                                 |
| codeExpire                | No       | min 1 and max 90 minutes (Code expiry time) |
| choices.type              | No       | value is `otp`                              |
| choices.type.otp.otp_type | No       | value is `copy_code` and `one_tap`          |
| choices.type.otp.otp_code | No       | value button text ex: copy your code        |

### Example Request

```
curl -X POST \
  '{endpoint}whatsapp/templates' \
  -H 'authorization: Bearer 5b02112fb7xxxxxxxxx' \
  -H 'content-type: application/json' \
  -d '{
    "type": "mediatemplate",
    "name": "template_name",
    "category": "authentication",
    "meta_approval": true,
    "language": "en",
    "number": "918736xxxxxx",
    "payload": {
        "type": "mediatemplate",
        "payload": {
            "name": "authentication_template",
            "language": "en",
            "body_params": [
                "123**"
            ],
            "header": {
                "type": "text"
            },
            "body": {
                "type": "text",
                "payload": {
                    "text": "@{{#var#}} is your verification code."
                }
            },
            "security": "true",
            "codeExpire": 5,
            "choices": {
                "type": "otp",
                "otp": {
                    "otp_type": "copy_code",
                    "otp_code": "Copy your Code"
                }
            }
        }
    }
}'
```

### Example Response

```
{
    "status": "OK",
    "code": 200,
    "message": "Template created successfully.",
    "data": []
}
```
