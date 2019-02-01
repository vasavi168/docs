# Verify Token

{appp} Verify a sent verification token. Can only be done once for each token.

  - Send the verification code that your user supplied, with the corresponding `id` from the Verify request.
  - Check the `status` of the response to determine if the code the user supplied matches the one sent by {app}.

#### GET
```
{endpoint}check/{id}/{token}
```

#### MANDATORY PARAMETERS

| Name     | Type | Description |
|----------|------|----------|
| id | string | The Verify request to check. This is the `id` you received in the response to the Verify request.|
| token | int | The verification code entered by your user.|

#### Example Request

```curl
curl -X GET \
  '{endpoint}verify/check/41379328-d3a7-4fcd-be90-d5237f911d76/742385' \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer 38e896f55670311982434e929559xxxx' \
```

#### Example Response

```json
{
    "id": "41379328-d3a7-4fcd-be90-d5237f911d76",
    "status": "success"
}
```