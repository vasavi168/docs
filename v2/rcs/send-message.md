# RCS Messaging Api


## Capabilities Check

```
{endpoint}rcs/capabilities
```
#### HTTP Methods
  
  It will support only `GET` Method

####  MANDATORY PARAMETERS

| Name     | Descriptions |
|----------|--------------|
| to | Mobile number of the user you want to send rcs message |
| id | Request Id |

#### Example Request With Text Messgae

```
curl -X GET \
  'http://portal.mobtexting.co/api/v2/rcs/capabilities?access_token=d9e1cac3812186b353c5022xxxxxxxxd&to=9640024149&id=1233444xxxxxxxx
```

#### Example Response For Success

```json
{
    "code": "200",
    "status": "OK",
    "data": {
        "features": {
            "RICHCARD_STANDALONE",
            "ACTION_CREATE_CALENDAR_EVENT",
            "ACTION_DIAL",
            "ACTION_OPEN_URL",
            "ACTION_SHARE_LOCATION",
            "ACTION_VIEW_LOCATION",
            "RICHCARD_CAROUSEL"
        }
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
            "message": "The specified phone number cannot be reached by RBM at this time.",
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
| to | Receiver mobile number with country code|
| id | Message Id for the request |
| text | Message text you want to send |


####  Example Request

```
curl -X POST \
  '{endpoint}rcs/message/send' \
  -H 'authorization: Bearer d9e1cac3812186b353c50229a36e589d' \
  -H 'content-type: application/json' \
  -d '{ 
        "content":{
          "contentMessage": {
              "text": "Hello, world!"
            }
        },
        "to": "918919525224",
        "id": "12900926r221223xxxxxx"
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

## Sending Media Message

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
        "content":{
          "contentMessage": {
              'contentInfo': {
                'fileUrl': 'http://yourdomain.com/images/richcard.png',
                'forceRefresh': false
              }
            }
        },
        "to": "918919525224",
        "id": "12900926r221223xxxxxx"
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

## Sending Message With Suggested Replies

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
        'contentMessage': {
          'text': 'Hello, world!',
          'suggestions': [
            {
              reply: {
                'text': 'Suggestion #1',
                'postbackData': 'Yes, Agreed',
              },
            },
            {
              reply: {
                'text': 'Suggestion #2',
                'postbackData': 'No',
              },
            }
          ]
        },
        "to": "918919525224",
        "id": "12900926r221223xxxxxx"
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