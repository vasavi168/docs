## Create Templates

Create templates using post method under your account

#### POST

```
{domain}/rest/v1/template/create
```

#### PARAMETERS

| Name     | Optional | Descriptions |
|----------|-----|-----|
| sender | No | Enter the approved sender-id under your account |
| name | Yes | Input the name of the template that you would like to refer with|
| body | No | Input the body of the sms(template)|


#### Example Request

```
curl -X POST \
  {domain}/rest/v1/template/create \
  -H 'Authorization: Bearer 81fe2ebd35xxxxxxx' \
  -H 'access_token: 81fe2ebd35xxxxxxxxx' \
  -H 'content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' \
  -F sender=TXTsms \
  -F name=test1 \
  -F 'body=testing sms 1'
```

```
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "{domain}/rest/v1/template/create",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"sender\"\r\n\r\nmobtxt\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"name\"\r\n\r\ntest1\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"body\"\r\n\r\ntesting sms 1\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--",
  CURLOPT_HTTPHEADER => array(
    "Authorization: Bearer 81fe2ebd35xxxxxxxxxxx",
    "access_token: 81fe2ebd35xxxxxxxxxxxxx",
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
    "message": "Template saved successfully"
}
```
