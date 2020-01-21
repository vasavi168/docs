# Whatsapp For Business API


#### HTTP Methods
  
  It will support only `POST` requests.


## Sending Text Message

```
{endpoint}whatsapp/message/send
```

####  MANDATORY PARAMETERS

| Name     | Descriptions |
|----------|--------------|
| from | Whatsapp Number |
| to | Destination mobile number with country code|
| text | Message text you want to send |


#### Example Request With Text Messgae

```
curl -X POST \
  '{endpoint}whatsapp/message/send' \
  -H 'authorization: Bearer d9e1cac3812186b353c50229a36e589d' \
  -d 'from=91886713XXXX&to=91788788XXXX&text=checking%20sms%20for%20whatspp'
```

#### Example Response

```json
{
    "status": "OK",
    "message": "Message Queued successfully"
}
```

## Template Message

```
{endpoint}whatsapp/message/send
```

####  MANDATORY PARAMETERS

| Name     | Descriptions |
|----------|--------------|
| from | Whatsapp Number |
| to | Destination mobile number with country code|
| type | Type of the message : template |
| name | Name of the template |

#### OPTIONAL PARAMETERS

| Name     | Descriptions |
|----------|--------------|
| variables[] | value of the variables used in template  |


```
Example of the template looks as follows :

{{1}} code: {{2}}. Valid for {{3}} minutes.

```
Here {{1}}, {{2}}, {{3}} are replacement variables which is different for each message. Same needs to be for `variables[]` parameter.

####  Example Request With Template

```
curl -X POST \
  {endpoint}whatsapp/message/send' \
  -H 'authorization: Bearer d9e1cac3812186b353c50229a36e589d' \
  -H 'content-type: application/x-www-form-urlencoded' \
  -d 'type=template&name=otp_message&from=918867XXXX&to=918867XXXXX&variables%5B%5D=Company&variables%5B%5D=123467&variables%5B%5D=30'

  ```
#### Example Response

```json
{
    "status": "OK",
    "message": "Message Queued successfully"
}
```