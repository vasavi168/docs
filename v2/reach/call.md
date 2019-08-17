# CREATE OUTBOUND CALL

This Voice API supports the following:

#### HTTP Methods
  
  It will support both GET and POST requests.

## Call Initiation

#### POST/GET

```
{domain}/api/{{version}}/voice/outgoing/send?access_token=209eccd40ee3a2e14af7fe45b21xxx
```

####  MANDATORY PARAMETERS

| Name     | Descriptions |
|----------|--------------|
| bridge | Bridge number for call initiation |
| to | Phone number with country code  to which call has to connect |
| ivr_id | Id of the IVR flow created in your voice account  `OR` |
| audio | Audio file id incase ivr is not provided |


####  OPTIONAL PARAMETERS

| Name     | Descriptions |
|----------|--------------|
| name |  name of the campaign |
| interval | Retry interval time  Expected Values : 5, 15, 30, 45, 60 (Minutes) : Default 0|

#### Example Request

With Audio File ID :
```
curl -X GET \
  "{domain}/api/{{version}}/outgoing/send?access_token=209eccd40ee3a2e14af7fe45b21xxx&name=api obd&to=8919525224&bridge=91123456789&audio=39888925-718e-43bb-a8b1-d4a37722e37"
```
- Here `39888925-718e-43bb-a8b1-d4a37722e37`  is the sound file id uploaded to your voice account.

With Ivr Flow ID :

```
curl -X GET \
  "{domain}/api/{{version}}/outgoing/send?access_token=209eccd40ee3a2e14af7fe45b21xxx&name=api obd&to=8919525224&bridge=91123456789&ivr_id=23"
```
- Here `23` is the ivr flow id created in voice account
#### Example Response

```json
{
    "status": 200,
    "message": "1 numbers accepted for delivery.",
    "data": [
        {
            "id": "70fa87e0-9df9-4327-bc80-a561c48703d8:1",
            "mobile": "918919525224",
            "charges": "0.5000",
            "customid": "",
            "customid1": "",
            "iso_code": null,
            "submitted_at": "2019-08-16 15:09:51"
        }
    ]
}
```