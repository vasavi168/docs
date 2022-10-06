## Edit Sender-ids

Edit sender-ids using post method under your account

#### API Endpoint

```
{domain}/api/{version}/
```

#### PUT

```
{endpoint}sms/sender/edit/{id}
```

#### PARAMETERS

| Name         | optional | Descriptions                                                  |
| ------------ | -------- | ------------------------------------------------------------- |
| country_code | No       | For which country this sender belongs to. 2 letters           |
| entity_id    | Mixed    | Input the entity id (required for india)                      |
| entity_name  | Mixed    | Company name whom this sender belongs to (required for india) |
| service      | no       | Input the Service like (T, P, MKT, A2P)                       |

#### Example Request

```
curl -X PUT \
  {endpoint}sms/sender/edit/93af9991-f1cc-4b36-abd5-xxxxxx \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer 5b02112fb7xxxxxxxxx' \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  -d entity_name=xxxxx \
  -d entity_id=xxxxx \
  -d country_code=IN
```

#### Example Response

```json
{
  "status": "OK",
  "code": 200,
  "message": "Sender updated successfully"
}
```
