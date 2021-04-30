## Edit Templates

Edit template using post method under your account

#### API Endpoint

```
{domain}/api/{version}/
```

#### POST

```
{endpoint}sms/template/edit/{id}
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
 {endpoint}sms/template/edit/b10a9c3c-33bd-42f4-9e68-31c2216e5bcf \
    -H 'Accept: application/json' \
    -H 'Authorization: Bearer 5b02112fb7xxxxxxxxx'
    -H 'Content-Type: application/x-www-form-urlencoded'
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
