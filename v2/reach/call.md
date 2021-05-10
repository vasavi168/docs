# CREATE OUTBOUND CALL

#### API Endpoint

```
{domain}/api/{version}/
```

#### POST

```
{endpoint}outgoing/send
```

#### MANDATORY PARAMETERS

| Name   | Descriptions                                                |
| ------ | ----------------------------------------------------------- |
| bridge | Bridge number for call initiation                           |
| to     | Phone number with country code to which call has to connect |
| ivr_id | Id of the IVR flow created in your voice account `OR`       |
| audio  | Audio file id incase ivr is not provided                    |

#### OPTIONAL PARAMETERS

| Name       | Descriptions                                                                  |
| ---------- | ----------------------------------------------------------------------------- |
| name       | name of the campaign                                                          |
| interval   | Retry interval time Expected Values : 5, 15, 30, 45, 60 (Minutes) : Default 0 |
| webhook_id | Id of the webhook created in webhook section [View Webhooks Page](/webhooks)  |

## Example Request Using Audio File ID

```
curl -X POST '{endpoint}outgoing/send' \
    -H 'Accept: application/json' \
    -H 'Authorization: Bearer 38e896f55670311982434e929559bxxxx' \
    -H 'Content-Type: application/x-www-form-urlencoded' \
    -d 'bridge=91806828XXXX' \
    -d 'to=918867135XXXX' \
    -d 'audio=39888925-718e-43bb-a8b1-d4a3XXXXX' \
    -d 'name=obd_api_call'
```

- Here `39888925-718e-43bb-a8b1-d4a3XXXXX` is the sound file id uploaded in Reach > Sounds Section.

## Example Request Using IVR Flow ID

```
curl -X POST '{endpoint}outgoing/send' \
    -H 'Accept: application/json' \
    -H 'Authorization: Bearer 38e896f55670311982434e929559bxxxx' \
    -H 'Content-Type: application/x-www-form-urlencoded' \
    -d 'bridge=91806828XXXX' \
    -d 'to=918867135XXXX' \
    -d 'ivr_id=23' \
    -d 'name=obd_api_call'
```

- Here `ivr_id` `23` is the ivr flow id created in Engage > Studio Section

## Example Request Using Custom Audio File Location

```
curl -X POST '{endpoint}outgoing/send' \
    -H 'Accept: application/json' \
    -H 'Authorization: Bearer 38e896f55670311982434e929559bxxxx' \
    -H 'Content-Type: application/x-www-form-urlencoded' \
    -d 'bridge=91806828XXXX' \
    -d 'to=918867135XXXX' \
    -d 'audio==http://youraudiofilelocation.mp3' \
    -d 'name=obd_api_call'
```

- Here `audio` parameter accepts publicly accessable audio file location and must start with either `http` or `https`.

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
