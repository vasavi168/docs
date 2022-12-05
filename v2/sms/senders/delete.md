## Delete Sender-id

Delete sender-id using delete method under your account

#### API Endpoint

```
{domain}/api/{version}/
```

#### DELETE

```
{endpoint}sms/senders/{id}
```

Replace the {id} with the actual id of the sender that you would like to delete.

#### Example Request

```
curl -X DELETE \
  {endpoint}sms/senders/ff467e28-7170-4a72-952e-c999cxxxxxx \
  -H 'Authorization: Bearer 5b02112fb7xxxxxxxxxxxxxxx' \
```

#### Example Response

```json
{
    "status": "OK",
    "code": 200,
    "message": "Deleted Successfully",
    "data": []
}
```
