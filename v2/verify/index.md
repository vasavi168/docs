# Verify Api

Verify API enables you to verify a mobile phone number with two-factor authentication.

This is useful for:

- Protecting against spam, by preventing spammers from creating multiple accounts
- Monitoring suspicious activity, by forcing an account user to verify ownership of a number
- Ensuring that you can reach your users at any time because you have their correct phone number

Create a new Verify object through the API to start the verification process of a recipient. We will take care of creating a token and making sure that the message gets delivered to the user's handset.

## Verify Request

#### API Endpoint

```
{domain}/api/{version}/
```

#### POST

```
{endpoint}verify
```

#### MANDATORY PARAMETERS

| Name | Type | Description                                  |
| ---- | ---- | -------------------------------------------- |
| to   | int  | The telephone number that you want to verify |

#### OPTIONAL PARAMETERS

| Name        | Type   | Description                                                                                                                                     |
| ----------- | ------ | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| from        | string | Sender Id from which message should get delivered. default: VERIFY                                                                              |
| reference   | string | A client reference                                                                                                                              |
| template    | string | The template of the message body. Needs to contain {token} for the verification code to be included. default: {token} is your verification code |
| timeout     | int    | The verification code expiry time in seconds. Default: 120                                                                                      |
| length      | string | The number of characters in the verification code. Must be between 4 and 10. Default: 6                                                         |
| ip_address  | string | The IP address used by your user when they entered the verification code.                                                                       |
| entity_id   | string | Entityid registered in DLT portal (for indian routes)                                                                                           |
| template_id | string | Templateid registered in DLT portal (for indian routes)                                                                                         |

#### Example Request

```curl
curl -X POST \
  '{endpoint}verify?to=919019955xxx' \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer 38e896f55670311982434e929xxx' \
```

#### Example Response

```json
{
  "id": "fb5e1214-7c9f-4f54-b18f-78dc7a901dec",
  "status": "sent",
  "to": "919019955xxx",
  "reference": null,
  "created_at": "2019-01-31 14:41:48",
  "expire_at": "2019-01-31 14:43:48"
}
```
