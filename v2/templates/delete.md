## Delete Template

Delete template using post method under your account

#### GET

```
{domain}/rest/v1/template/delete/{id}
```

Replace the {id} with the actual id of the template that you would like to delete.

#### Example Request

```
curl -X GET \
 {domain}/rest/v1/template/delete/b10a9c3c-33bd-42f4-9e68-31c2216e5bcf \
  -H 'Authorization: Bearer 81fe2ebd35xxxxxxxxxxxxxx'
```

#### Example Response

```json
{
  "status": "OK",
  "message": "Template deleted successfully"
}
```
