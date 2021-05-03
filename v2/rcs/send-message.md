# RCS Messaging Api

## Channel Info

```
{
    "channels": {
        "channel" : {
            "name": "rcs"
        },
        "recipient": {
            "group_id": "{segment_id}",  // String or array
            "to": ["91XXXXXX", "91XXXXXX"]
        }

     }
}
```

#### PARAMETERS

| Name      | Description                                                 | type     | Required |
| --------- | ----------------------------------------------------------- | -------- | -------- |
| channel   | This block contains information realted messaging channel   | N/A      | Yes      |
| name      | Name of Messaging Channel. Ex: `rcs`                        | `string` | Yes      |
| recipient | This block contains contacts information related to channel | N/A      | Yes      |
| to        | Receiver mobile numbers : `text`                            | `array`  | Yes      |

#### API Endpoint

```
{domain}/api/{version}/
```

## Capabilities Check

```
{endpoint}rcs/capabilities
```

#### HTTP Methods

It will support only `POST` Method

#### MANDATORY PARAMETERS

| Name | Descriptions                                           |
| ---- | ------------------------------------------------------ |
| to   | Mobile number of the user you want to send rcs message |
| id   | Request Id                                             |

#### Example Request

```
curl -X POST '{endpoint}rcs/capabilities' \
    -H 'Authorization: Bearer 38e896f55670311982434e929559bxxxx' \
    -H 'Content-Type: application/x-www-form-urlencoded' \
    -d 'to=917026267xxx' \
    -d 'id=123456-89992-XXXXX'
``` 

#### Example Response For Success

```json
{
  "code": 200,
  "status": "OK",
  "data": {
    "features": [
      "RICHCARD_STANDALONE",
      "ACTION_CREATE_CALENDAR_EVENT",
      "ACTION_DIAL",
      "ACTION_OPEN_URL",
      "ACTION_SHARE_LOCATION",
      "ACTION_VIEW_LOCATION",
      "RICHCARD_CAROUSEL"
    ]
  }
}
```

#### Example Response For Failure

```json
{
  "status": "ERROR",
  "message": "An error occured. pleae try again"
}
```

#### API Endpoint

```
{domain}/api/{version}/
```

## Sending Text Message

```
{endpoint}rcs/message/send
```

#### MANDATORY PARAMETERS

| Name | Descriptions                             |
| ---- | ---------------------------------------- |
| to   | Receiver mobile number with country code |
| id   | Message Id for the request               |
| text | Message text you want to send            |

#### Example Request

```
curl --request POST \
  --url {endpoint}rcs/message/send \
  -H 'Authorization: Bearer d9e1cac3812186b353c50229a36e589d' \
  -H 'Content-Type: application/json' \
  -d '{
    "channels": {
        "channel" : {
            "name": "rcs"
        },
        "recipient": {
            "to": ["9189195XXXX"]
        }
    },
    "payload" : {
        "text_payload": {
            "text": "Hello From Google RCS"
        }
        "id": '1234a-1223jnkf-xxxx'
    }

}'

```

#### Example Response For Success

```json
{
  "status": "OK",
  "message": "Message Queued successfully"
}
```

#### Example Response For Failure

```json
{
  "status": "ERROR",
  "message": "An error occured. pleae try again"
}
```

#### API Endpoint

```
{domain}/api/{version}/
```

## Sending Media Message

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
curl --request POST \
  --url {endpoint}rcs/message/send \
  -H 'Authorization: Bearer d9e1cac3812186b353c50229a36e589d' \
  -H 'Content-Type: application/json' \
  -d '{
    "channels": {
        "channel" : {
            "name": "rcs"
        },
        "recipient": {
            "to": ["9189195XXXX"]
        }
    },
    "payload" : {
        "media_payload": {
            "url": "http://yourdomain.com/images/richcard.png",
            "forceRefresh": "false"
        },
        "id": '1234a-1223jnkf-xxxx'
    }

}'

```

Note : `forceRefresh` to true forces RBM to fetch new content from the specified URL, even if the URL content is cached

#### Example Response

```json
{
  "status": "OK",
  "message": "Message Queued successfully"
}
```

#### API Endpoint

```
{domain}/api/{version}/
```

## Sending Message With Suggestions

```
{endpoint}rcs/message/send
```

#### MANDATORY PARAMETERS

| Name | Descriptions                                  |
| ---- | --------------------------------------------- |
| to   | Receiver mobile number with country code      |
| id   | Message Id for the request                    |
| url  | Remote url of the media file you want to send |

#### Example Request

```
curl --request POST \
  --url {endpoint}rcs/message/send \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer 38e896f55670311982434e929559bxxxx' \
  -H 'Content-Type: application/json' \
  -d '{
    "channels": {
        "channel" : {
            "name": "rcs",
            "from": "9190191XXXXX",
            "recipient": {
                "contact_id": "9d702140-b9b5-4827-b485-XXXX",
                "to": ["91891952XXXX", "91886713XXXX"]
            }
        },
        "recipient": {
            "to": ["9189195XXXX"]
        }
    },
    "payload" : {
        "suggestions_payload": {
            "text": "This is the main message",
            'replies': [{
                "reply": {
                  "text": "Suggestion #1",
                  "postbackData": "Yes, I Am In"
                }
              },
              {
                "reply": {
                  "text": "Suggestion #2",
                  "postbackData": "No, Not interested"
                }
              }
            ]
        },
        "id": '1234a-1223jnkf-xxxx'
    }
}
```

#### Example Response

```json
{
  "status": "OK",
  "message": "Message Queued successfully"
}
```

#### API Endpoint

```
{domain}/api/{version}/
```

## Sending Message With Actions

```
{endpoint}rcs/message/send
```

#### MANDATORY PARAMETERS

| Name | Descriptions                             |
| ---- | ---------------------------------------- |
| to   | Receiver mobile number with country code |
| id   | Message Id for the request               |

#### Example Request with Dial Number action

```
curl --request POST \
  --url {endpoint}rcs/message/send \
  -H 'Authorization: Bearer d9e1cac3812186b353c50229a36e589d' \
  -H 'Content-Type: application/json' \
  -d '{
    "channels": {
        "channel" : {
            "name": "rcs"
        },
        "recipient": {
            "to": ["9189195XXXX"]
        }
    },
    "payload" : {
        "actions_payload": {
            "text": "This is the main message",
            'action': {
              'text': 'Call',              
              'dialAction': {
                'phoneNumber': '+918919525XXXX'
              },
              'postbackData': 'postback_data_1234',
              'fallbackUrl': 'https://www.google.com/contact/'s
            }
          },
          "id": '1234a-1223jnkf-xxxx'
    }
}
```

#### Example Response

```json
{
  "status": "OK",
  "message": "Message Queued successfully"
}
```

#### API Endpoint

```
{domain}/api/{version}/
```

#### Example Request with Share Location action

```
curl --request POST \
  --url {endpoint}rcs/message/send \
  -H 'Authorization: Bearer d9e1cac3812186b353c50229a36e589d' \
  -H 'Content-Type: application/json' \
  -d '{
    "channels": {
        "channel" : {
            "name": "rcs"
        },
        "recipient": {
            "to": ["9189195XXXX"]
        }
    },
    "payload" : {
      "text": "some text messae here",
      "id": '1234a-1223jnkf-xxxx',
      "actions_payload": [{
            'action': {
              'text': 'Share Your Location',              
              'shareLocationAction': {
                  'latLong': {
                    'latitude': "37.4220188',
                    'longitude': "-122.0844786'
                  },
                  'label': 'Googleplex'
                },
              'fallbackUrl': 'https://www.google.com/maps/@37.4220188,-122.0844786,15z'
            }
          }]
    }
}
```

#### Example Response

```json
{
  "status": "OK",
  "message": "Message Queued successfully"
}
```

#### API Endpoint

```
{domain}/api/{version}/
```

#### Example Request with Calendar Event action

```
curl --request POST \
  --url {endpoint}rcs/message/send \
  -H 'Authorization: Bearer d9e1cac3812186b353c50229a36e589d' \
  -H 'Content-Type: application/json' \
  -d '{
    "channels": {
        "channel" : {
            "name": "rcs"
        },
        "recipient": {
            "to": ["9189195XXXX"]
        }
    },
    "payload" : {
        "actions_payload": {
            'action': {
              'text': 'Save to calendar',              
              'createCalendarEventAction': {
                  'startTime': '2021-06-30T19:00:00Z',
                  'endTime': '2021-06-30T20:00:00Z',
                  'title': 'My calendar event',
                  'description': 'Description of the calendar event'
              },
              'postbackData': 'postback_data_1234',
              'fallbackUrl': 'https://www.google.com/calendar',
            }
          },
          "id": '1234a-1223jnkf-xxxx'
    }
}
```

#### Example Response

```json
{
  "status": "OK",
  "message": "Message Queued successfully"
}
```

#### API Endpoint

```
{domain}/api/{version}/
```

## Sending Rich Card Message

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
curl --request POST \
  --url {endpoint}rcs/message/send \
  -H 'Authorization: Bearer d9e1cac3812186b353c50229a36e589d' \
  -H 'Accept: application/json' \
  -d '{
    "channels": {
        "channel" : {
            "name": "rcs"
        },
        "recipient": {
            "to": ["9189195XXXX"]
        }
    },
    "payload" : {
        "id": '1234a-1223jnkf-xxxx',
        "richCard_payload": {
            '
            ': {
            'thumbnailImageAlignment': 'RIGHT',
            'cardOrientation': 'VERTICAL',
            'cardContent': {
                'title': 'Hello, world!',
                'description': 'RBM is awesome!',
                'media_payload': {
                    'height': 'TALL',
                    'fileUrl': 'http://www.yourdomain.com/document.gif',
                    'forceRefresh': 'false'
                },
                'suggestions_payload': {
                    'replies' : [
                      {
                        'reply': {
                          'text': 'Suggestion #1',
                          'postbackData': 'suggestion_1'
                        }
                      },
                      {
                        'reply': {
                          'text': 'Suggestion #2',
                          'postbackData': 'suggestion_2'
                        }
                      }
                    ]
                }
            }
          }
        }
    }

}'

```

Note : `forceRefresh` to true forces RBM to fetch new content from the specified URL, even if the URL content is cached

#### Example Response

```json
{
  "status": "OK",
  "message": "Message Queued successfully"
}
```
