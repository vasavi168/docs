# Create Sound File

This Voice API supports the following:

#### HTTP Methods
  
  It will support only POST requests.

## Call Initiation

#### POST

```
{{endpoint}voice/sound/create
```

####  MANDATORY PARAMETERS

| Name     | Descriptions |
|----------|--------------|
| audio | sound file that you want to upload |


####  OPTIONAL PARAMETERS

| Name     | Descriptions |
|----------|--------------|
| name |  name of the sound file for your response |

#### Example Request

```
curl -X POST \
  "{endpoint}voice/sound/create?access_token=209eccd40ee3a2e14af7fe45b21xxx&name=myAudioFile&audio=<<youraudiofileHere>>"
```

#### Example Response

```json
{
    "status": "OK",
    "message": "Sound uploaded successfully",
    "data": {
        "id": "5d2c9c40-8f00-48f3-902e-d4c1f2a7b0a4"
    }
}
```

- The `id` parameter in response can be used for outgoing campaign purpose as a audio source.