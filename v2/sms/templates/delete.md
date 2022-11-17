## Delete Template

Delete template using delete method under your account

#### API Endpoint

```
{domain}/api/{version}/
```

#### DELETE

```
{endpoint}sms/templates/{id}
```

Replace the {id} with the actual id of the template that you would like to delete.

#### Example Request

```
curl -X DELETE \
  {endpoint}sms/templates/b23769e6-019f-48f4-aae9-ec00a5xxxxxx \
    -H 'Accept: application/json' \
    -H 'Authorization: Bearer 5b02112fb7xxxxxxxxx'
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
