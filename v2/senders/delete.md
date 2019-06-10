## Delete Sender-id

Delete sender-id using post method under your account

#### POST

```
{domain}/rest/v1/sender/delete/{id}
```
Replace the {id} with the actual id of the sender that you would like to delete.

#### Example Request

```
curl -X GET \
  {domain}/rest/v1/sender/delete/b7e42a8e-b6df-4a5e-ac42-xxxxxxxxxxxx \
  -H 'Authorization: Bearer 5b02112fb7xxxxxxxxxxxxxxx' \
  -H 'access_token: 5b02112fb745380e489xxxxxxxxxxxxxxx'
```

```
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "{domain}/rest/v1/sender/delete/b7e42a8e-b6df-4a5e-ac42-xxxxxxxxxxxx",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "GET",
  CURLOPT_HTTPHEADER => array(
    "Authorization: Bearer 5b02112fb7xxxxxxxx",
    "access_token: 5b02112fb745380e489xxxxxxxxxxxxxxx"
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
    "message": "Sender deleted successfully",
    "id": 1
}
```
