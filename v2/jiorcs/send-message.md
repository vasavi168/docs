# JioRCS Messaging Api


## Capabilities Check

```
{endpoint}jiorcs/capabilities
```
#### HTTP Methods
  
  It will support only `GET` Method

####  MANDATORY PARAMETERS

| Name     | Descriptions |
|----------|--------------|
| mobile | Mobile number of the user you want to send rcs message |

#### Example Request With Text Messgae

```
curl -X GET \
  'http://portal.mobtexting.co/api/v2/jiorcs/capabilities?access_token=d9e1cac3812186b353cxxxxxx&mobile=8919525224'
```

#### Example Response For Success

```json
{
    "code": 200,
    "status": "OK",
    "data": {
        "capabilities": [
        "chat",
        "fileTransfer",
        "geolocationPush",
        "chatBotCommunication"
      ]
    }
}
```

#### Example Response For Failure

```json
{
    "code": 404,
    "status": "failed",
    "message": null,
    "data": {
        "error": {
            "code": 404,
             "reason": {
                "text": "The user contact or chat ID cannot be found or the given user's device is not RCS capabile."
            },
            "status": "NOT_FOUND"
        }
    }
}
```


## Sending Text Message

```
{endpoint}rcs/message/send
```

####  MANDATORY PARAMETERS

| Name     | Descriptions |
|----------|--------------|
| userContact | Receiver mobile number with country code|
| textMessage | Message text you want to send |

####  OPTIONAL PARAMETERS

| Name     | Descriptions |
|----------|--------------|
| custom | CustomId for reference|


####  Example Request

```
curl -X POST \
  'http://portal.mobtexting.co/api/v2/jiorcs/message/send?access_token=d9e1cac38121XXXXXX' \
  -H 'content-type: application/json' \
  -d '  {
    "content": {
      "RCSMessage": {
        "textMessage": "RCS Message from MOBtexting Platform with Image Now",
        "trafficType": "subscription",
        "msgId": "1233333333333333"
      },
      "messageContact": {
        "userContact": "+918919525224"
      }
    },
    "custom": "123456789"
  }'
  ```
#### Example Response For Success

```json
{
    "code": 202,
    "status": "OK",
    "data": {
        "RCSMessage": {
            "msgId": "6a3c94c9d7404733bfcda590b03ba386",
            "status": "pending",
            "timestamp": "2020-07-01T10:47:26.701Z"
        }
    }
}
```

#### Example Response For Failure

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

## Sending Message With Suggested Replies

```
{endpoint}rcs/message/send
```

####  MANDATORY PARAMETERS

| Name     | Descriptions |
|----------|--------------|
| userContact | Receiver mobile number with country code|


####  Example Request

```
curl -X POST \
  'http://portal.mobtexting.co/api/v2/jiorcs/message/send?access_token=d9e1cac3812186b353c50229a36e589d' \
  -H 'cache-control: no-cache' \
  -H 'content-type: application/json' \
  -H 'postman-token: 1f3191e9-d939-162f-750a-3541ddecd374' \
  -d '{
    "content": {
        "RCSMessage": {
          "textMessage": "Please tell whether ur particiapating or not?",
      "msgId": "MzJmajlmamVzZGZ8bmk5MHNlbmRmZTAz",
      "suggestedResponse": {
        "response": {
          "reply": {
            "displayText": "Yes",
            "postback": {
              "data": "set_by_chatbot_reply_yes"
            }
          }
        }
      },
      "timestamp": "2017-09-26T01:33:20.315Z"
      },
      "messageContact": {
        "userContact": "+918919525224"
      },
      "event": "response"
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