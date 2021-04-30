## Create Templates

Create templates using post method under your account

#### API Endpoint

```
{domain}/api/{version}/
```

#### POST

```
{endpoint}sms/template/create
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
  {endpoint}sms/template/create \
    -H 'Accept: application/json' \
    -H 'Authorization: Bearer 5b02112fb7xxxxxxxxx'
    -H 'Content-Type: application/x-www-form-urlencoded' \
    -d sender=TXTsms \
    -d name=test1 \
    -d 'body=testing sms 1'
```

#### Example Response

```json
{
  "status": "OK",
  "message": "Template saved successfully"
}
```
