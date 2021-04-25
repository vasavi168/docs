## Create Templates

Create templates using post method under your account

#### POST

```
{domain}/rest/v1/template/create
```

#### PARAMETERS

| Name   | Optional | Descriptions                                                     |
| ------ | -------- | ---------------------------------------------------------------- |
| sender | No       | Enter the approved sender-id under your account                  |
| name   | Yes      | Input the name of the template that you would like to refer with |
| body   | No       | Input the body of the sms(template)                              |

#### Example Request

```
curl -X POST \
  {domain}/rest/v1/template/create \
  -H 'Authorization: Bearer 81fe2ebd35xxxxxxx' \
  -H 'content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' \
  -F sender=TXTsms \
  -F name=test1 \
  -F 'body=testing sms 1'
```

#### Example Response

```json
{
  "status": "OK",
  "message": "Template saved successfully"
}
```
