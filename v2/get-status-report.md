# PULL STATUS SUMMARY
    
This api will give status wise summary report for the given daterange

#### GET
```
{endpoint}sms/report
```

####  ACCEPTED PARAMETERS

| Name     | Descriptions |
|----------|--------------|
| daterange | Date Range : (in format i.e,yyyy-mm-dd|yyyy-mm-dd) Ex: 2019-06-02|2019-06-10 |

you can pass any of the above params to get the report.

#### Example Request

```curl
curl -X GET \
  '{endpoint}sms/report?daterange=2019-06-19|2019-06-22&access_token=209eccd40e45b21xxxx'
```

#### Example Response

```json
{
    "status": 200,
    "message": "OK",
    "data": {
        "2019-07-02": {
            "date": "2019-07-02",
            "status": {
                "TIMEOUT-DLR": 572,
                "DELIVRD": 150781,
                "UNDELIV": 1450
            }
        },
        "2019-07-01": {
            "date": "2019-07-01",
            "status": {
                "BARRED": 6,
                "BLACKLST": 10,
                "EXPIRED": 3040,
                "FAILED": 15,
                "INVALID-SUB": 54,
                "MOB-OFF": 9,
                "NET-ERR": 5,
                "REJ-MULTIPART": 416
            }
        }
    }
}
```