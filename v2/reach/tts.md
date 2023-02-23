# CREATE OUTBOUND CALL USING TEXT

Using Text2Speech API we can trigger a call using text as input and that text will be played as voice message once recipient answers the call.

#### API Endpoint

```
{domain}/api/{version}/
```

#### POST

```
{endpoint}outgoing/tts
```

#### MANDATORY PARAMETERS

| Name   | Descriptions                                                |
| ------ | ----------------------------------------------------------- |
| bridge | Bridge number for call initiation                           |
| to     | Phone number with country code to which call has to connect |
| text  | Message text you want to send which will be played as speech once call is answered|

#### OPTIONAL PARAMETERS

| Name       | Descriptions                                                                  |
| ---------- | ----------------------------------------------------------------------------- |
| options       | Extra options for TTS API                                                          |
| language   | The language in which the text needs to be play after picking the call  |
| break | definition of the break that you can add in the text to Play  |
| identifier  | Identifier for the break characters in message text to play  |
| time  | Break duration  |

## Example Request Using Audio File ID

```
curl -X POST '{endpoint}outgoing/tts' \
    -H 'authorization: Bearer 46fd72850fXXXXXX' \
  -H 'cache-control: no-cache' \
  -H 'content-type: application/json' \
  -d '{
    "bridge": "9172007XXX",
    "to": 918867XXXXXX,
    "text": "Hi## This is the text to speech using ##outgoing api",
    "options": {
        "language": "en-US",
        "break": {
            "identifier": "##",
            "time": 1
        }
    }
}'
```
#### Example Response

```json
{
    "status": "OK",
    "message": "Calls queued successfully",
    "data": [
        {
            "id": "52ecf5da-259b-4e0f-a2eb-XXXXXX",
            "channel": "outgoing",
            "caller_id": "917200XXXXXX",
            "mobile": "918867XXXXXX",
            "flow_id": "5784",
            "credits": "0.0005",
            "created_at": "2023-01-23T12:13:25.666366Z",
            "foreign_id": null,
            "status": "queued"
        }
    ]
}
```
