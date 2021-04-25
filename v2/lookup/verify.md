## Verify HLR of mobile numbers

Verify HLR of mubile numbers using post method under your account

#### API Endpoint

```
{domain}/api/{version}/
```

#### POST

```
{domain}/api/v2/lookup/verify
```

#### PARAMETERS

| Name   | optional | Descriptions                                                                    |
| ------ | -------- | ------------------------------------------------------------------------------- |
| number | No       | Enter the mobile number with country code (multile numbers are seperated by , ) |

#### Example Request

```

curl -X POST \
  {domain}/api/v2/lookup/verify \
  -H 'Authorization: Bearer 5b02112fb7xxxxxxxxxxxxxxxx' \
  -H 'access_token: 5b02112fb7xxxxxxxxxxxxxxxxxxxxxxxx' \
  -F number=9194928xxxxx,9180743xxxxx \
```

```

<?php
$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => '{domain}/api/v2/lookup/verify',
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => '',
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => true,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => 'POST',
  CURLOPT_POSTFIELDS => array('number' => '919492839930'),
  CURLOPT_HTTPHEADER => array(
    'Authorization: Bearer 7160f04c05870ee8881xxxxxxxxxxxxx',
    'access_token: 7160f04c05870ee8881xxxxxxxxxxxxx'
  ),
));


$response = curl_exec($curl);

curl_close($curl);
echo $response;

```

#### Example Response

```json
{
  "status": 200,
  "message": "Verified Successfully",
  "results": [
    {
      "phone": "919492xxxxx",
      "mcc_mnc": "40xxx",
      "imsi": "404738104xxxxxx",
      "serving_msc": "919xxx",
      "status": "SUCCESS",
      "original_network": {
        "network_prefix": "94928",
        "country_prefix": "91",
        "network_name": "BSNL",
        "country_name": "India",
        "state_name": "Andhra Pradesh"
      },
      "ported": false,
      "ported_network": {
        "ported_network_prefix": null,
        "ported_country_prefix": null,
        "ported_network_name": null,
        "ported_country_name": null,
        "ported_state_name": null
      },
      "roaming": false,
      "roaming_network": {
        "roaming_network_prefix": null,
        "roaming_country_prefix": null,
        "roaming_network_name": null,
        "roaming_country_name": null,
        "roaming_state_name": null
      }
    }
  ]
}
```
