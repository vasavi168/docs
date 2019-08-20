## User Registration Api

Registration api will support only `POST` method.

#### POST

```
{domain}/api/{version}/register
```

####  MANDATORY PARAMETERS

| Name     | Descriptions |
|----------|--------------|
| name | Name of the user |
| email | EmailId of the user |
| password | Password must contain uppercase, lowercase characters and numbers. Lenght should be min 6, max 20 characters.|


####  OPTIONAL PARAMETERS


| Name     | Descriptions |
|----------|--------------|
| mobile | Mobile number with coutry code | 

#### Example Request

```
curl -X POST \
  {domain}/api/{version}/register \
  -H 'cache-control: no-cache' \
  -H 'content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' \
  -F name=Lakshman \
  -F email=youremailid@mail.com \
  -F mobile=918867135684 \
  -F password=Qwe@12334
```

Kindly replace the name, email, mobile, password accroding to your details.
  
#### Example Response

```json
{
    "status": "OK",
    "message": "User registered successfully"
}
```
