## Create Sender-ids

Create sender-ids using post method under your account

#### POST

```
{domain}/rest/v1/sender/create
```

#### PARAMETERS

| Name        | optional | Descriptions                                   |
| ----------- | -------- | ---------------------------------------------- |
| name        | No       | Enter the sender-id that you want to create    |
| entity_name | No       | Input the entity name                          |
| message     | No       | Input the message related to the sender-id     |
| document    | Yes      | choose a optin file that matches the sender_id |

#### Example Request

```
curl -X POST \
  {domain}/rest/v1/sender/create \
  -H 'Authorization: Bearer 5b02112fb7xxxxxxxxxxxxxxxx' \
  -H 'access_token: 5b02112fb7xxxxxxxxxxxxxxxxxxxxxxxx' \
  -H 'content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' \
  -F name=xxxxxx \
  -F entity_name=xxxxx \
  -F message=xxxxxx
```

```

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "{domain}/rest/v1/sender/create",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"name\"\r\n\r\nvishal\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"entity_name\"\r\n\r\ntest\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"message\"\r\n\r\ntesting\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--",
  CURLOPT_HTTPHEADER => array(
    "Authorization: Bearer 5b02112fb7xxxxxxxxxxxxxx",
    "access_token: 5b02112fb7453xxxxxxxxxxxxxxxx",
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
  "message": "Sender saved successfully",
  "id": "b7e42a8e-b6df-4a5e-ac42-xxxxxxxxxxx"
}
```
