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
  -H 'Authorization: Bearer 81fe2ebd35xxxxxxxxxxxxxx' \
  -H 'access_token: 81fe2ebd35xxxxxxxxxxxxxxxxx'
```

```
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "{domain}/rest/v1/template/delete/b10a9c3c-33bd-42f4-9e68-31c2216e5bcf",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 30,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "GET",
  CURLOPT_HTTPHEADER => array(
    "Authorization: Bearer 81fe2ebd35xxxxxxxxxxxxxx",
    "access_token: 81fe2ebd35xxxxxxxxx"
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
  "message": "Template deleted successfully"
}
```
