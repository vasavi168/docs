## Create Sender-ids

Create sender-ids using post method under your account

#### API Endpoint

```
{domain}/api/{version}/
```

#### POST

```
{endpoint}sms/sender/create
```

#### PARAMETERS

| Name        | optional | Descriptions                                   |
| ----------- | -------- | ---------------------------------------------- |
| name        | No       | Enter the sender-id that you want to create    |
| entity_name | No       | Input the entity name                          |
| message     | No       | Input the message related to the sender-id     |
| document    | Yes      | choose a optin file that matches the sender_id |

#### Example Request

```
curl -X POST \
  {endpoint}sms/sender/create \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer 5b02112fb7xxxxxxxxxxxxxxxx' \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  -d name=xxxxxx \
  -d entity_name=xxxxx \
  -d message=xxxxxx
```

#### Example Response

```json
{
  "status": "OK",
  "message": "Sender saved successfully",
  "id": "b7e42a8e-b6df-4a5e-ac42-xxxxxxxxxxx"
}
```
