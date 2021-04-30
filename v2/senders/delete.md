## Delete Sender-id

Delete sender-id using post method under your account

#### DELETE

```
{domain}/rest/v1/sender/delete/{id}
```

Replace the {id} with the actual id of the sender that you would like to delete.

#### Example Request

```
curl -X DELETE \
  {domain}/rest/v1/sender/delete/b7e42a8e-b6df-4a5e-ac42-xxxxxxxxxxxx \
  -H 'Authorization: Bearer 5b02112fb7xxxxxxxxxxxxxxx' \
```

#### Example Response

```json
{
  "status": "OK",
  "message": "Sender deleted successfully",
  "id": 1
}
```
