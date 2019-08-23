# OUTBOUND CALL Status

This Voice API supports the following:

#### HTTP Methods
  
  It will support `GET` request.

```
{domain}/api/{{version}}/outgoing/callstatus?access_token=209eccd40ee3a2e14af7fe45b21xxx
```

####  MANDATORY PARAMETERS

| Name     | Descriptions |
|----------|--------------|
| id | ID of the call which initiated through api |


####  OPTIONAL PARAMETERS

| Name     | Descriptions |
|----------|--------------|
| mobile |  mobile number  |

#### Example Request

```
curl -X GET \
  "{domain}/api/{{version}}/outgoing/callstatus?access_token=209eccd40ee3a2e14af7fe45b21xxx&id=047d8cfc-77d1-4f6c-bfb5-e81f1a1343a7:1"
```


#### Example Response

```json
{
    "status": 200,
    "message": "OK",
    "data": [
        {
            "id": "047d8cfc-77d1-4f6c-bfb5-e81f1a1343a7:1",
            "mobile": "918919525224",
            "caller_id": "918068287602",
            "duration": "00:00:19",
            "pulsing": "30",
            "status": "ANSWER",
            "charges": "0.1500",
            "dtmf": null,
            "location": "IN",
            "provider": "RJ",
            "start_at": "2019-07-16 18:13:44",
            "end_at": "2019-07-16 18:14:03"
        }
    ]
}
```