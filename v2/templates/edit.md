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
  -H 'access_token: 81fe2ebd35xxxxxxxxxxxxx' \
  -H 'content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' \
  -F sender=txtme \
  -F body=testing-2

```

```
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "{domain}/rest/v1/template/edit/b10a9c3c-33bd-42f4-9e68-31c2216e5bcf",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"sender\"\r\n\r\nmobtxt\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"name\"\r\n\r\nsame\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"body\"\r\n\r\ntesting-2\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--",
  CURLOPT_HTTPHEADER => array(
    "Authorization: Bearer 81fe2ebd35xxxxxxxxxxxxxxxxxxxxx",
    "Content-Type: application/x-www-form-urlencoded",
    "access_token: 81fe2ebd35xxxxxxxxxxxxxxxxxxx",
    "content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW"
  ),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
}
```

#### Example Response

```json
{
  "status": "OK",
  "message": "Template updated successfully"
}
```
