n# Messaging

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

### Templates

   Now you can send message using template id of the predefined template created in your account.

   Example template as follows:

   ```
    Dear {{1}}, Thanks for registering with us. Your details as follows {{2}}, {{3}}.
    ```


    While sending sms we need to pass the variables in the api url then content will be replaced automatically in the template as below.

    Ex: variables=laxman,laxman46XXXXXX@gmail.com,891952XXXX

    ```
    Dear laxman, Thanks for regisitering with us. Your details as follows laxman46XXXX@gmail.com, 891952XXXX.
    ```


## Send SMS

#### POST/GET

```
{endpoint}sms/template?template_id=123445566&sender=TXTSMS&to=91901xxxxxx&service=T&variables=name,12345,Bangalore
```

You can send sms using `POST` or `GET` methods, GET method requires data should be url_encoded.


####  MANDATORY PARAMETERS

| Name     | Descriptions |
|----------|--------------|
| to | Phone number to send with country prefix. (multiple numbers can be separated by comma.) |
| template_id | Id of the template |
| sender | The registered and approved Sender-id |
| service | Determines whether the SMS to be sent is Transactional, Promotional or other. |
| variables | Varible values for replacing in template content (separated by comma) Ex:name,891919XXX


####  OPTIONAL PARAMETERS


| Name     | Descriptions |
|----------|--------------|
| dlr_url | The Url for which the SMS response to be sent after sending the SMS can be specified using this parameter. [read more](/docs/{{version}}/sms-push-dlr)|
| time |  Schedule time (in format i.e,yyyy-mm-dd hh:mm:ss) at which the SMS has to be sent. |
| type | The SMS to be sent is Unicode, Normal or Auto detect. (value "U", "N" or "A") |
| flash | This parameter can be used to send flash sms via API ( Values 1 or 0.) |
| custom | Any customised parameters can be passed  using this parameter |
| custom1 | Any customised parameter |
| port | Port number to which SMS has to be sent |

#### Example Request

```
curl -X GET \
  "{endpoint}sms/template?access_token=209eccd40ee3a2e14af7fe45b21xxx&template_id=123dsaf4xxxxxxx&sender=TXTSMS&to=91901xxxxxx&service=T&varibales=laxman,laxmanxxxxx@gmail.com,8919XXXXX"
```

#### Example Response

```json
{
  "status": 200,
  "message": "1 numbers accepted for delivery.",
  "data": [
    {
      "id": "b34e35ad-fe34-4a8b-977c-b21cd76cd7d6:1",
      "mobile": "91901xxxxxx",
      "status": "AWAITING-DLR",
      "units": 1,
      "length": 7,
      "charges": 1,
      "customid": "",
      "customid1": "",
      "iso_code": null,
      "submitted_at": "2020-07-09 16:27:35"
    }
  ]
}
```
