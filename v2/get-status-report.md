# PULL STATUS SUMMARY
    
This api will give status wise summary report for the given daterange

#### GET
```
{endpoint}sms/report
```

####  ACCEPTED PARAMETERS

| Name     | Descriptions |
|----------|--------------|
| datetime[created_at] | Date Range : (in format i.e,Mon dd, yyyy - Mon dd, yyyy) Ex: Jun 26, 2019 - Jun 28, 2019|

you can pass any of the above params to get the report.

#### Example Request

```curl
curl -X GET \
  '{endpoint}sms/report?datetime[created_at]=Jun 26, 2019 - Jun 28, 2019&access_token=209eccd40e45b21xxxx'
```

#### Example Response

```json
{
    "status": 200,
    "message": "OK",
    "data": [
        {
            "status": "DELIVRD",
            "total": "56"
        },
        {
            "status": "OPTOUT-REJ",
            "total": "1"
        },
        {
            "status": "SNDR-BLOCK",
            "total": "2"
        }
    ]
}
```