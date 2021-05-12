# Whatsapp For Business API

## Channel Info

```
{
    "channels": {
        "channel" : {
            "name": "whatsapp",
            "from": "919019120120",
            "recipient": {
                "group_id": "{segment_id}",  // String or array
                "to": ["918919525224", "918867135684"]
            }
        },
        "recipient": {
            "group_id": "{segment_id}",  // String or array
            "to": ["91XXXXXX", "91XXXXXX"]
        }

     }
}
```

#### PARAMETERS

| Name      | Description                                                 | type                | Required                       |
| --------- | ----------------------------------------------------------- | ------------------- | ------------------------------ |
| channel   | This block contains information realted messaging channel   | N/A                 | Yes                            |
| name      | Name of Messaging Channel. Ex: `whatsapp`                   | `string`            | Yes                            |
| from      | Sender or From Number                                       | `number`            | Yes                            |
| recipient | This block contains contacts information related to channel | N/A                 | Yes                            |
| group_id  | Segment id which contain list of phone numbers              | `string` or `array` | Yes if `to` param not present  |
| to        | Receiver mobile numbers : `text`                            | `array`             | Yes, if `group_id` not present |

`Note` : The `recipient` block inside channel is related to particular communication channel and it is optional. The outside `recipient` channel contain common recipients for every channel.

#### HTTP Methods

It will support only `POST` requests.

#### API Endpoint

```
{domain}/api/{version}/
```

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
    "channels": {
        "channel" : {
            "name": "whatsapp",
            "from": "919019120120",
            "recipient": {
                "group_id": "{segment_id}",
                "to": ["918919525224", "918867135684"]
            }
        },
        "recipient": {
            "group_id": "{segment_id}",
            "to": ["91XXXXXX", "91XXXXXX"]
        }

     },
    "payload" : {
       "text_payload": {
            "text": "This is a simple text message from whatsapp channel"
        }
    }
}'
```

#### PARAMETERS

| Name    | Description                                 | Limits              | Required |
| ------- | ------------------------------------------- | ------------------- | -------- |
| payload | Messaage Payload section                    | N/A                 | Yes      |
| to      | Destination mobile number with country code | NA                  | Yes      |
| text    | Message Content you want to send            | Max 4096 Characters | Yes      |

#### Example Response

```json
{
  "status": "OK",
  "message": "Message Queued successfully"
}
```

## Sending Template Message

#### API Endpoint

```
{domain}/api/{version}/
```

Template message is the way of sending dynamic content using variables.

```
Example of the template looks as follows :

Otp For verifying your account is @{{1}} code: @{{2}}. Valid for @{{3}} minutes.

```

Here @{{1}}, @{{2}}, @{{3}} are replacement variables which is different for each message. Same needs to be for `params` or `body_params` parameters.

```
{endpoint}whatsapp/message/send
```

#### Example Request With Template

```
curl -X POST \
  '{endpoint}whatsapp/message/send' \
  -H 'authorization: Bearer d9e1cac3812186b353c5022xxxxx' \
  -H 'content-type: application/json' \
  -d '{
    "channels": {
        "channel" : {
            "name": "whatsapp",
            "from": "919019120120",
            "recipient": {
                "group_id": "{segment_id}",
                "to": ["918919525224", "918867135684"]
            }
        },
        "recipient": {
            "group_id": "{segment_id}",
            "to": ["91XXXXXX", "91XXXXXX"]
        }

     },
    "payload" : {
       "text_payload": {
            "text": "This is a simple text message from whatsapp channel"
        },
        "template_payload" : {
            "name": "otp",
            "language": "en",
            "params": ["name", "223344", "MOBtexting", "10"],
            "header_params": ["Replacement Text"],
            "body_params": ["name", "223344", "MOBtexting", "10"]
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

| Name          | Description                                                                                                                                                                                         | Limits                                                                     | Required |
| ------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------- | -------- |
| language      | Language to send the template in. Default `en`                                                                                                                                                      | N/A                                                                        | No       |
| params        | Parameters to replace the variables in the template                                                                                                                                                 | can only be used for template messages with only a body                    | No       |
| header_params | Parameters to replace the variables in the template                                                                                                                                                 | Up to 60 characters for all parameters and predefined template header text | No       |
| body_params   | Parameters to replace the variables in the template                                                                                                                                                 | Up to 1024 characters for all parameters and predefined template text      | No       |
| ttl           | Time to live of the template message. If the receiver has not opened the template message before the time to live expires, the message will be deleted. Default 30 Days. Need to specify in Seconds | Can be more than 1 day i.e 86400 sec                                       | No       |

## Send Image Message

#### API Endpoint

```
{domain}/api/{version}/
```

We can send Images as attachment in whatsapp using below API. The maximum image size is limited to 64 MB.

```
{endpoint}whatsapp/message/send
```

#### Example Request With Image Messgae

```
curl -X POST \
  '{endpoint}whatsapp/message/send' \
  -H 'authorization: Bearer d9e1cac3812186b353c5022xxxxx' \
  -H 'content-type: application/json' \
  -d '{
    "channels": {
        "channel" : {
            "name": "whatsapp",
            "from": "919019120120",
            "recipient": {
                "group_id": "{segment_id}",
                "to": ["918919525224", "918867135684"]
            }
        },
        "recipient": {
            "group_id": "{segment_id}",
            "to": ["91XXXXXX", "91XXXXXX"]
        }

     },
    "payload" : {
        "image_payload": {
            "url": "https://domin-name.com/your_image_path.png",
            "caption": "some caption for image"
        }
    }
}'
```

#### PARAMETERS

| Name    | Description                                              | Limits | Required |
| ------- | -------------------------------------------------------- | ------ | -------- |
| url     | Public url of the image file. Either HTTP or HTTPS link. | 64 MB  | Yes      |
| caption | some text for image caption                              | N/A    | No       |

#### Example Response

```json
{
  "status": "OK",
  "message": "Message Queued successfully"
}
```

## Send Document Message

#### API Endpoint

```
{domain}/api/{version}/
```

We can send Document which is having valid MIME-type as attachment in whatsapp using below API. The maximum document size is limited to 64 MB. So anything not image, audio or video will be transmitted as document message.

```
{endpoint}whatsapp/message/send
```

#### Example Request With Document Messgae

```
curl -X POST \
  '{endpoint}whatsapp/message/send' \
  -H 'authorization: Bearer d9e1cac3812186b353c5022xxxxx' \
  -H 'content-type: application/json' \
  -d '{
    "channels": {
        "channel" : {
            "name": "whatsapp",
            "from": "919019120120",
            "recipient": {
                "group_id": "{segment_id}",
                "to": ["918919525224", "918867135684"]
            }
        },
        "recipient": {
            "group_id": "{segment_id}",
            "to": ["91XXXXXX", "91XXXXXX"]
        }

     },
    "payload" : {
      "type": "document",
        "document_payload": {
            "url": "https://domin-name.com/docs/uploads/voice.pdf",
            "caption": "some caption for document"
        }
    }
}'
```

#### PARAMETERS

| Name    | Description                                                 | Limits             | Required |
| ------- | ----------------------------------------------------------- | ------------------ | -------- |
| type    | Message tpe. value : `document`                             | Max File size 64MB | Yes      |
| url     | Public url of the document file. Either HTTP or HTTPS link. | N/A                | Yes      |
| caption | some text for document caption                              | N/A                | No       |

#### Example Response

```json
{
  "status": "OK",
  "message": "Message Queued successfully"
}
```

## Send Audio Message

#### API Endpoint

```
{domain}/api/{version}/
```

We can send Audio clips as attachment in whatsapp using below API. The maximum audio file size is limited to max 64 MB.

```
{endpoint}whatsapp/message/send
```

#### Example Request With Audio Messgae

```
curl -X POST \
  '{endpoint}whatsapp/message/send' \
  -H 'authorization: Bearer d9e1cac3812186b353c5022xxxxx' \
  -H 'content-type: application/json' \
  -d '{
    "channels": {
        "channel" : {
            "name": "whatsapp",
            "from": "919019120120",
            "recipient": {
                "group_id": "{segment_id}",
                "to": ["918919525224", "918867135684"]
            }
        },
        "recipient": {
            "group_id": "{segment_id}",
            "to": ["91XXXXXX", "91XXXXXX"]
        }

     },
    "payload" : {
        "audio_payload": {
            "url": "https://domin-name.com/audio_file.mp3",
            "caption": "some caption for audio file"
        }
    }
}'
```

#### PARAMETERS

| Name    | Description                                              | Limits    | Required |
| ------- | -------------------------------------------------------- | --------- | -------- |
| url     | Public url of the audio file. Either HTTP or HTTPS link. | Upto 64MB | Yes      |
| caption | some text for audio caption                              | N/A       | No       |

#### Example Response

```json
{
  "status": "OK",
  "message": "Message Queued successfully"
}
```

## Send Video Message

#### API Endpoint

```
{domain}/api/{version}/
```

We can send Video clips as attachment in whatsapp using below API. The maximum audio file size is limited to 64 MB.

```
{endpoint}whatsapp/message/send
```

#### Example Request With Video Messgae

```
curl -X POST \
  '{endpoint}whatsapp/message/send' \
  -H 'authorization: Bearer d9e1cac3812186b353c5022xxxxx' \
  -H 'content-type: application/json' \
  -d '{
    "channels": {
        "channel" : {
            "name": "whatsapp",
            "from": "919019120120",
            "recipient": {
                "group_id": "{segment_id}",
                "to": ["918919525224", "918867135684"]
            }
        },
        "recipient": {
            "group_id": "{segment_id}",
            "to": ["91XXXXXX", "91XXXXXX"]
        }

     },
    "payload" : {
        "video_payload": {
            "url": "https://domin-name.com/uploads/2021/demo_video.mp4",
            "caption": "some caption for video file"
        }
    }
}'
```

#### PARAMETERS

| Name    | Description                                              | Limits    | Required |
| ------- | -------------------------------------------------------- | --------- | -------- |
| url     | Public url of the video file. Either HTTP or HTTPS link. | Max 64 MB | Yes      |
| caption | some text for video caption                              | N/A       | No       |

#### Example Response

```json
{
  "status": "OK",
  "message": "Message Queued successfully"
}
```

## Send Message With Suggestions

#### API Endpoint

```
{domain}/api/{version}/
```

We can send Video clips as attachment in whatsapp using below API. The maximum audio file size is limited to 64 MB.

```
{endpoint}whatsapp/message/send
```

#### Example Request With Suggestions Messgae

```
curl -X POST \
  '{endpoint}whatsapp/message/send' \
  -H 'authorization: Bearer d9e1cac3812186b353c5022xxxxx' \
  -H 'content-type: application/json' \
  -d '{
    "channels": {
        "channel" : {
            "name": "whatsapp",
            "from": "919019120120",
            "recipient": {
                "group_id": "{segment_id}",
                "to": ["918919525224", "918867135684"]
            }
        },
        "recipient": {
            "group_id": "{segment_id}",
            "to": ["91XXXXXX", "91XXXXXX"]
        }

     },
    "payload" : {
        "text": "Sample text message",
        "suggestions_payload": {
            buttons": [
              {
                  "type": "url",
                  "payload": "https://example.com",
                  "caption": "Click Here"
              },
              {
                  "type": "text",
                  "payload": "__unsubscribe",
                  "caption": "Unsubscribe"
              }
          ]
        }
    }
}'
```

#### PARAMETERS

| Name    | Description                                                | Limits | Required |
| ------- | ---------------------------------------------------------- | ------ | -------- |
| buttons | this block contains actions for suggestions of the message | N/A    | Yes      |

#### Example Response

```json
{
  "status": "OK",
  "message": "Message Queued successfully"
}
```

## Send Vcard / Contacts Message

#### API Endpoint

```
{domain}/api/{version}/
```

We can send location in whatsapp using below API. The maximum audio file size is limited to 64 MB.

```
{endpoint}whatsapp/message/send
```

#### Example Request With Vcard Messgae

```
curl -X POST \
  '{endpoint}whatsapp/message/send' \
  -H 'authorization: Bearer d9e1cac3812186b353c5022xxxxx' \
  -H 'content-type: application/json' \
  -d '{
    "channels": {
        "channel" : {
            "name": "whatsapp",
            "from": "919019120120",
            "recipient": {
                "group_id": "{segment_id}",
                "to": ["918919525224", "918867135684"]
            }
        },
        "recipient": {
            "group_id": "{segment_id}",
            "to": ["91XXXXXX", "91XXXXXX"]
        }

     },
    "payload" : {
        "contacts_payload" : {
            "options" : [
                {
                    "addresses": [
                        {
                            "city": "Bangalore",
                            "country": "India",
                            "country_code": "in",
                            "state": "KA",
                            "type": "Office",
                            "zip": "560078"
                        }
                    ],
                    "birthday": "1993-08-18",
                    "emails": [
                        {
                            "email": "hello@domin-name.com",
                            "type": "WORK"
                        }
                    ],
                    "name": {
                        "first_name": "Laxman",
                        "formatted_name": "Laxman Ka",
                        "last_name": "Ka"
                    },
                    "phones": [
                        {
                            "phone": "919019120120",
                            "type": "HOME"
                        }
                    ],
                    "urls": [
                        {
                             "url": "https://www.domin-name.com",
                             "type": "WORK"
                        }
                    ]
                }
            ]
        }
    }
}'
```

#### PARAMETERS

| Name    | Description                    | Limits | Required |
| ------- | ------------------------------ | ------ | -------- |
| phone   | Mobile numbers saved in mobile | N/A    | Yes      |
| name    | Person name                    | N/A    | No       |
| address | Address details of the contact | N/A    | No       |

#### Example Response

```json
{
  "status": "OK",
  "message": "Message Queued successfully"
}
```

## Send Location Message

#### API Endpoint

```
{domain}/api/{version}/
```

We can send location in whatsapp using below API. The maximum audio file size is limited to 64 MB.

```
{endpoint}whatsapp/message/send
```

#### Example Request With Location Messgae

```
curl -X POST \
  '{endpoint}whatsapp/message/send' \
  -H 'authorization: Bearer d9e1cac3812186b353c5022xxxxx' \
  -H 'content-type: application/json' \
  -d '{
    "channels": {
        "channel" : {
            "name": "whatsapp",
            "from": "919019120120",
            "recipient": {
                "group_id": "{segment_id}",
                "to": ["918919525224", "918867135684"]
            }
        },
        "recipient": {
            "group_id": "{segment_id}",
            "to": ["91XXXXXX", "91XXXXXX"]
        }

     },
    "payload" : {
        "location_payload" : {
            "longitude": 12.912985,
            "latitude": 77.599505,
            "name": "MOBtexting Pvt Ltd",
            "address": "JP Nagar, Mini forest"
        }
    }
}'
```

#### PARAMETERS

| Name      | Description                           | Limits | Required |
| --------- | ------------------------------------- | ------ | -------- |
| longitude | Longitude of the location coordinates | N/A    | Yes      |
| latitude  | Latitude of the location coordinates  | N/A    | No       |
| name      | Address name                          | N/A    | No       |
| address   | Textual representation of location    | N/A    | No       |

#### Example Response

```json
{
  "status": "OK",
  "message": "Message Queued successfully"
}
```

## Send Carousel Message

#### API Endpoint

```
{domain}/api/{version}/
```

We can send Carousel in whatsapp using below API. The maximum audio file size is limited to 64 MB.

```
{endpoint}whatsapp/message/send
```

#### Example Request With Carousel Messgae

```
curl -X POST \
  '{endpoint}whatsapp/message/send' \
  -H 'authorization: Bearer d9e1cac3812186b353c5022xxxxx' \
  -H 'content-type: application/json' \
  -d '{
    "channels": {
        "channel" : {
            "name": "whatsapp",
            "from": "919019120120",
            "recipient": {
                "group_id": "{segment_id}",
                "to": ["918919525224", "918867135684"]
            }
        },
        "recipient": {
            "group_id": "{segment_id}",
            "to": ["91XXXXXX", "91XXXXXX"]
        }

     },
    "payload" : {
        "carousel_payload" : {
            --Coming Soon ----
        }
    }
}'
```

## Send Card Message

#### API Endpoint

```
{domain}/api/{version}/
```

We can send Carousel in whatsapp using below API. The maximum audio file size is limited to 64 MB.

```
{endpoint}whatsapp/message/send
```

#### Example Request With Card Messgae

```
curl -X POST \
  '{endpoint}whatsapp/message/send' \
  -H 'authorization: Bearer d9e1cac3812186b353c5022xxxxx' \
  -H 'content-type: application/json' \
  -d '{
    "channels": {
        "channel" : {
            "name": "whatsapp",
            "from": "919019120120",
            "recipient": {
                "group_id": "{segment_id}",
                "to": ["918919525224", "918867135684"]
            }
        },
        "recipient": {
            "group_id": "{segment_id}",
            "to": ["91XXXXXX", "91XXXXXX"]
        }

     },
    "payload" : {
        "card_payload" : {
            --Coming Soon ----
        }
    }
}'
```

#### PARAMETERS

| Name | Description | Limits | Required |
| ---- | ----------- | ------ | -------- |


#### Example Response

```json
{
  "status": "OK",
  "message": "Message Queued successfully"
}
```
