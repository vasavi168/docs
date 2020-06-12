# RCS Messaging Api


## Sending Message Wirh RichCard

Your agent can revoke messages that it has sent but that the RBM platform hasn't delivered to the user. If the RBM platform successfully revokes a message, the platform deletes the message from the user's message queue and doesn't deliver the message.


```
{endpoint}rcs/message/send
```

####  MANDATORY PARAMETERS

| Name     | Descriptions |
|----------|--------------|
| to | Receiver mobile number with country code|
| id | Message Id for the request |
| fileUrl | Remote url of the media file you want to send |


####  Example Request

```
curl -X POST \
  '{endpoint}rcs/message/send' \
  -H 'authorization: Bearer d9e1cac3812186b353c50229a36e589d' \
  -H 'content-type: application/json' \
  -d '{
        "content" : {
          "contentMessage": {
            "richCard": {
              "standaloneCard": {
                "thumbnailImageAlignment": "RIGHT",
                "cardOrientation": "VERTICAL",
                "cardContent": {
                  "title": "Hello, User! Welcome to RCS Platform of MOBtexting",
                  "description": "RBM is awesome!",
                  "media": {
                    "height": "TALL",
                    "contentInfo":{
                      "fileUrl": "https://www.mobtexting.com/assets/images/sms-home.png",
                      "forceRefresh": false
                    }
                  },
                  "suggestions": [
                    {
                      "reply": {
                        "text": "Yes Recommended",
                        "postbackData": "suggestion_1"
                      }
                    },
                    {
                      "reply": {
                        "text": "No Not matched",
                        "postbackData": "suggestion_1"
                      }
                    }
                  ]
                }
              }
            }
          }
        },
        "to": "918919525224",
        "id": "laxmn123345890"
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