## Edit Templates

Edit template using post method under your account

#### POST

```
{domain}/rest/v1/template/edit/{id}
```

Replace the {id} with the actual id of the template that you would like to Edit.

#### PARAMETERS

| Name   | Optinal | Descriptions                                   |
| ------ | ------- | ---------------------------------------------- |
| sender | No      | Edit the approved sender-id under your account |
| body   | No      | Edit the body of the sms(template)             |

#### Example Request

```
curl -X POST \
 {domain}/rest/v1/template/edit/b10a9c3c-33bd-42f4-9e68-31c2216e5bcf \
  -H 'Authorization: Bearer 81fe2ebd35xxxxxxxxxx' \
  -H 'Content-Type: application/x-www-form-urlencoded'
  -H 'content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' \
  -F sender=txtme \
  -F body=testing-2

```

#### Example Response

```json
{
  "status": "OK",
  "message": "Template updated successfully"
}
```
