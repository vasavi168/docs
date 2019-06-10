## Edit Sender-ids

Edit sender-ids using post method under your account

#### POST

```
{domain}/rest/v1/sender/edit/{id}
```

#### PARAMETERS

| Name     | optional | Descriptions |
|----------|-------|----------|
| name |No | Edit the sender-id |
| entity_name |No | Edit the entity_name|
| message |No | edit the message|
| document |yes | choose a optin file that matches the sender_id |


#### Example Request

```
curl -X POST \
  {domain}/rest/v1/sender/edit/93af9991-f1cc-4b36-abd5-xxxxxx \
  -H 'Authorization: Bearer 5b02112fb7xxxxxxxxx' \
  -H 'access_token: 5b02112fb7xxxxxxxxxxx' \
  -H 'content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' \
  -F name=xxxxx \
  -F entity_name=test \
  -F message=testing \
  -F document=@/xxxx/xxx/xxx/xxx/xxx/xxx/xxx/xxxx/xxxx.png
```

```
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "{domain}/rest/v1/sender/edit/93af9991-f1cc-4b36-abd5-xxxxxx",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"name\"\r\n\r\nvidyas\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"entity_name\"\r\n\r\ntest\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"message\"\r\n\r\ntesting\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"document\"; filename=\"python.png\"\r\nContent-Type: image/png\r\n\r\n\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--",
  CURLOPT_HTTPHEADER => array(
    "Authorization: Bearer 5b02112fb7xxxxxxxxxxxxxxxxxxxxxxx",
    "access_token: 5b02112fb7xxxxxxxxxxxxxxxxxxxxxxx",
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
    "message": "Sender updated successfully",
    "id": 1
}
```
