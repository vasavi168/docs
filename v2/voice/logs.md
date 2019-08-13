# Call Logs Report

This Voice API supports the following:

#### GET

```
{domain}/api/{{version}}/voice/calls
```

####  MANDATORY PARAMETERS

| Name     | Descriptions |
|----------|--------------|
| access_token | Access token of your account |


####  Filters

| Name     | Descriptions |
|----------|--------------|
| datetime[end_at] |  daterange for filtering the call logs | Ex: Aug 12, 2019 - Aug 12, 2019 |

#### Example Request

```
curl -X GET \
  "{domain}/api/{{version}}/voice/calls?access_token=209eccd40ee3a2e14af7fe45b21xxx&datetime[end_at]=Aug 12, 2019 - Aug 12, 2019"
```

#### Example Response

```json
{
    "status": "OK",
    "data": [
        {
            "id": "c839b4c4-8c0d-11e9-bb88-6c2b59c79f5a",
            "call_from": "917989532456",
            "call_to": "918068287601",
            "service": "IN",
            "bridge": "918068287601",
            "status": "RECEIVED",
            "duration": "00:00:12",
            "billing": "00:00:12",
            "pulsing": "30",
            "charges": "0.0150",
            "start_at": "2019-06-11 05:57:24",
            "end_at": "2019-06-11 05:57:36",
            "hangup_by": "caller",
            "dtmf": null,
            "location": "IN",
            "region": "AP",
            "provider": "RJ",
            "notes": "Hi laxman final fix",
            "audio": null,
            "audio_length": null,
            "storage": null,
            "name": "Laxman ka",
            "serial": 1
        }
    ]
}
```

# Recordings Report

#### GET

```
{domain}/api/{{version}}/voice/recordings
```

####  MANDATORY PARAMETERS

| Name     | Descriptions |
|----------|--------------|
| access_token | Access token of your account |


####  Filters

| Name     | Descriptions |
|----------|--------------|
| datetime[r.created_at] |  daterange for filtering the recordings | Ex: Aug 07, 2019 - Aug 13, 2019 |

#### Example Request

```
curl -X GET \
  "{domain}/api/{{version}}/voice/recordings?access_token=209eccd40ee3a2e14af7fe45b21xxx&datetime[r.created_at]: Jun 07, 2019 - Aug 13, 2019"
```

#### Example Response

```json
{
    "status": "OK",
    "data": [
        {
            "id": "c136768e-8c0e-11e9-b795-6c2b59c79f5a",
            "user_id": "13016",
            "agent_id": "0",
            "call_id": null,
            "service": "C",
            "call_from": "918553001122",
            "call_to": "918068287601",
            "name": null,
            "audio": "https://s30m.s3.ap-southeast-1.amazonaws.com/rc/190624/c-9180682876012-11061911.mp3?X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAITXHQTJADVE4ZNPA%2F20190813%2Fap-southeast-1%2Fs3%2Faws4_request&X-Amz-Date=20190813T112154Z&X-Amz-SignedHeaders=host&X-Amz-Expires=3600&X-Amz-Signature=2c5a05b7b7dcf9e6d288a0828a4acc69d357da008d28dac7f424d940792d8a6f",
            "storage": "s3",
            "duration": "00:01:33",
            "options": null,
            "notes": null,
            "created_at": "2019-06-11 06:04:21",
            "agent": null,
            "serial": 1,
            "created": "Jun 11, 2019 06:04 AM"
        }
    ]
}
```