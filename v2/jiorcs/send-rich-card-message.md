# RCS Messaging Api

## Sending Message Wirh RichCard

Your agent can revoke messages that it has sent but that the RBM platform hasn't delivered to the user. If the RBM platform successfully revokes a message, the platform deletes the message from the user's message queue and doesn't deliver the message.

#### API Endpoint

```
{domain}/api/{version}/
```

Sending Message

```
{endpoint}rcs/message/send
```

#### MANDATORY PARAMETERS

| Name    | Descriptions                                  |
| ------- | --------------------------------------------- |
| to      | Receiver mobile number with country code      |
| id      | Message Id for the request                    |
| fileUrl | Remote url of the media file you want to send |

#### Example Request

```
curl -X POST \
  '{endpoint}jiorcs/message/send?access_token=d9e1cac3812186b353c50229a36e589d' \
  -H 'cache-control: no-cache' \
  -H 'content-type: application/json' \
  -H 'postman-token: 6243f354-d2f7-b84d-0420-d54ade3716ba' \
  -d '{
    "content": {
        "RCSMessage": {
        "msgId": "045b08de-c965-469a-babf-9334281d5ab3",
        "richcardMessage": {
            "message": {
                "generalPurposeCard": {
                    "content": {
                        "media": {
                            "height": "SHORT_HEIGHT",
                            "mediaContentType": "image/png",
                            "mediaFileSize": 10,
                            "mediaUrl": "https://www.domin-name.com/ResponsiveSlides.js/images/ban-5.jpg",
                            "thumbnailFileSize": 0
                        },
                        "title": "Subscription"
                    },
                    "layout": {
                        "cardOrientation": "HORIZONTAL",
                        "cardWidth": "MEDIUM_WIDTH",
                        "imageAlignment": "LEFT"
                    }
                }
            }
        }
    },
    "messageContact": {
        "userContact": "+918919525224"
    }
    }

}'

```

#### Example Response

```json
{
  "code": 404,
  "status": "ERROR",
  "data": {
    "error": {
      "code": 404,
      "message": "Requested entity was not found.",
      "status": "NOT_FOUND"
    }
  }
}
```
