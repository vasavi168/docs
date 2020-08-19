# Whatsapp For Business API


#### HTTP Methods
  
  It will support only `POST` requests.


## Sending Media Message

```
{endpoint}whatsapp/media
```

####  MANDATORY PARAMETERS

| Name     | Descriptions |
|----------|--------------|
| from | Whatsapp Number |
| to | Destination mobile number with country code|
| text | Message text you want to send |
| file | Attachment you want to send | 


#### Example Request With Text Messgae

```
curl -X POST \
  '{endpoint}whatsapp/media' \
  -H 'authorization: Bearer d9e1cac3812186b353c50229a36e589d' \
  -H 'content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' \
  -F file=@mob-logo.png \
  -F from=91901xxxxxx \
  -F to=918867xxxxxx
```

#### Example Response

```json
{
    "status": "OK",
    "message": "Message Queued successfully"
}
```