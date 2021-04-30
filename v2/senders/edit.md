## Edit Sender-ids

Edit sender-ids using post method under your account

#### API Endpoint

```
{domain}/api/{version}/
```

#### POST

```
{endpoint}sms/sender/edit/{id}
```

#### PARAMETERS

| Name        | optional | Descriptions                                   |
| ----------- | -------- | ---------------------------------------------- |
| name        | No       | Edit the sender-id                             |
| entity_name | No       | Edit the entity_name                           |
| message     | No       | edit the message                               |
| document    | yes      | choose a optin file that matches the sender_id |

#### Example Request

```
curl -X POST \
  {endpoint}sms/sender/edit/93af9991-f1cc-4b36-abd5-xxxxxx \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer 5b02112fb7xxxxxxxxx' \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  -d name=xxxxx \
  -d entity_name=test \
  -d message=testing \
  -d document=@/xxxx/xxx/xxx/xxx/xxx/xxx/xxx/xxxx/xxxx.png
```

#### Example Response

```json
{
  "status": "OK",
  "message": "Sender updated successfully",
  "id": 1
}
```
