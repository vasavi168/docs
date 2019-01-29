# Messaging

The SMS API supports the following:

#### HTTP Methods 

`POST` - When you send a POST request with the end user's phone number to the messaging subresource, We sends the SMS message you specify.

`GET` - You can retrieve the results of the message you sent using the GET method. You do this by sending a GET request containing the reference id for the message you sent. We return a response message in the form of a *__JSON__* object in the entity body.

### Services

Types of services and their values are listed below:

* T - Transactional Messaging.
* P - Promotional Messaging.
* S - Transcrub Messaging.
* G - Global Messaging

Country code is mandatory to be included in the `to` paramenter for global messaging and optional for indian numbers. If country code not found, default `91` will get appended to mobile number.

Before you start sending transactional SMS through this API, please test whether your content is matching a template which has been pre approved. Otherwise, the SMS will end up being rejected.

## Send SMS

#### POST/GET

```
{endpoint}sms/send?message=Welcome&sender=TXTSMS&to=91901xxxxxx&service=T
```

You can send sms using `POST` or `GET` methods, GET method requires data should be url_encoded.


####  MANDATORY PARAMETERS

| Name     | Descriptions |
|----------|--------------|
| to | Phone number to send with country prefix. (multiple numbers can be separated by comma.) |
| message | The content of the SMS |
| sender | The registered and approved Sender-id |
| service | Determines whether the SMS to be sent is Transactional, Promotional or other. |


####  OPTIONAL PARAMETERS


| Name     | Descriptions |
|----------|--------------|
| dlr_url | The Url for which the SMS response to be sent after sending the SMS can be specified using this parameter. |
| time |  Schedule time (in format i.e,yyyy-mm-dd hh:mm:ss) at which the SMS has to be sent. |
| type | The SMS to be sent is Unicode, Normal or Auto detect. (value "U", "N" or "A") |
| flash | This parameter can be used to send flash sms via API ( Values 1 or 0.) |
| custom | Any customised parameters can be passed  using this parameter |
| custom1 | Any customised parameter |
| port | Port number to which SMS has to be sent |

#### Example Request

```
curl -X GET \
  "{domain}/api/{{version}}/sms/send?access_token=209eccd40ee3a2e14af7fe45b21xxx&message=Welcome&sender=TXTSMS&to=91901xxxxxx&service=T"
```

#### Example Response

```json
{
  "status": 200,
  "message": "1 numbers accepted for delivery.",
  "data": [
    {
      "id": "b34e35ad-fe34-4a8b-977c-b21cd76cd7d6:1",
      "mobile": "918921269xxx",
      "status": "AWAITING-DLR",
      "units": 1,
      "length": 7,
      "charges": 1,
      "customid": "",
      "customid1": "",
      "iso_code": null,
      "submitted_at": "2018-07-09 16:27:35"
    }
  ]
}
```