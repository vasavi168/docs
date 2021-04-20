# Whatsapp For Business API


#### HTTP Methods
  
  It will support only `POST` requests.


## Sending Text Message

```
{endpoint}whatsapp/message/send
```

#### Example Request With Text Messgae

```
curl -X POST \
  '{endpoint}whatsapp/message/send' \
  -H 'authorization: Bearer d9e1cac3812186b353c5022xxxxx' \
  -H 'content-type: application/json' \
  -d '{
    "from": "919019120120",
    "to": "918867135684",
    "payload" : {
      "type": "text",
      "text": "This is text message"
    }
}'
```

#### PARAMETERS

| Name     | Description | Limits | Required   |
|----------|--------------| ---- | -----------|
| from | Whatsapp Number | N/A | Yes |
| to | Destination mobile number with country code| NA | Yes |
| type| Message tpe. value : `text` | Max 4096 Characters | Yes |

#### Example Response

```json
{
    "status": "OK",
    "message": "Message Queued successfully"
}
```

## Sending Template Message

Template message is the way of sending dynamic content using variables.

```
Example of the template looks as follows :

Otp For verifying your account is {{1}} code: {{2}}. Valid for {{3}} minutes.

```
Here {{1}}, {{2}}, {{3}} are replacement variables which is different for each message. Same needs to be for `params` or `body_params` parameters.

```
{endpoint}whatsapp/message/send
```

####  Example Request With Template

```
curl -X POST \
  '{endpoint}whatsapp/message/send' \
  -H 'authorization: Bearer d9e1cac3812186b353c5022xxxxx' \
  -H 'content-type: application/json' \
  -d '{
    "from": "919019120120",
    "to": "918867135684",
    "payload" : {
      "type": "template",
        "template": {
          "name": "otp",
          "language": "en",
          "params": 
              [
                "MOBtexting",
                  "223344", 
                  "30",
              ],
          "ttl": 86400
        }
    }
    
}'
```
#### Example Response

```json
{
    "status": "OK",
    "message": "Message Queued successfully"
}
```

#### PARAMETERS

| Name     | Description | Limits | Required   |
|----------|--------------| ---- | -----------|
| from | Whatsapp Number | N/A | Yes |
| to | Destination mobile number with country code| NA | Yes |
| type| Type of message, value : `template` | Max 4096 Characters | Yes |
| language | Language to send the template in. Default `en`| N/A | No |
| params| Parameters to replace the variables in the template | can only be used for template messages with only a body| No |
| header_params| Parameters to replace the variables in the template | Up to 60 characters for all parameters and predefined template header text| No |
| body_params| Parameters to replace the variables in the template | Up to 1024 characters for all parameters and predefined template text| No |
| ttl | Time to live of the template message. If the receiver has not opened the template message before the time to live expires, the message will be deleted. Default 30 Days. Need to specify in Seconds| Can be more than 1 day i.e 86400 sec | No


## Send Image Message

We can send Images as attachment in  whatsapp using below API. The maximum image size is limited to 5 MB.

```
{endpoint}whatsapp/message/media
```

#### Example Request With Image Messgae

```
curl -X POST \
  '{endpoint}whatsapp/message/media' \
  -H 'authorization: Bearer d9e1cac3812186b353c5022xxxxx' \
  -H 'content-type: application/json' \
  -d '{
    "from": "919019120120",
    "to": "918867135684",
    "payload" : {
      "type": "image",
        "image": {
            "url": "https://mobtexting.com/uploadpath/myfolder/voice.png",
            "caption": "some caption for image"
        }
    }    
}'
```

#### PARAMETERS

| Name     | Description | Limits | Required   |
|----------|--------------| ---- | -----------|
| from | Whatsapp Number | N/A | Yes |
| to | Destination mobile number with country code| NA | Yes |
| type| Message tpe. value : `image` | Max File size 5MB | Yes |
| url | Public url of the image file. Either HTTP or HTTPS link. | N/A | Yes |
| caption | some text for image caption | N/A | No |

#### Example Response

```json
{
    "status": "OK",
    "message": "Message Queued successfully"
}
```

## Send Document Message

We can send Document which is having valid MIME-type as attachment in whatsapp using below API. The maximum document size is limited to 100 MB. So anything not image, audio or video will be transmitted as document message.

```
{endpoint}whatsapp/message/media
```

#### Example Request With Image Messgae

```
curl -X POST \
  '{endpoint}whatsapp/message/media' \
  -H 'authorization: Bearer d9e1cac3812186b353c5022xxxxx' \
  -H 'content-type: application/json' \
  -d '{
    "from": "919019120120",
    "to": "918867135684",
    "payload" : {
      "type": "document",
        "document": {
            "url": "https://mobtexting.com/docs/uploads/voice.pdf",
            "caption": "some caption for image"
        }
    }    
}'
```

#### PARAMETERS

| Name     | Description | Limits | Required   |
|----------|--------------| ---- | -----------|
| from | Whatsapp Number | N/A | Yes |
| to | Destination mobile number with country code| NA | Yes |
| type| Message tpe. value : `document` | Max File size 100MB | Yes |
| url | Public url of the document file. Either HTTP or HTTPS link. | N/A | Yes |
| caption | some text for document caption | N/A | No |

#### Example Response

```json
{
    "status": "OK",
    "message": "Message Queued successfully"
}
```
