## View Account Usage Report

It will display account usage report

#### API Endpoint

```
{domain}/api/{{version}}/
```

#### GET

```
{domain}/rest/v1/account/activity
```

#### PARAMETERS


#### Example Request

```
curl -X GET \
  '{domain}/rest/v1/account/activity?access_token=38e896f55670311982434xxxx' \
  -H 'Accept: application/json' \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  -H 'cache-control: no-cache'
```

Kindly replace the token with your respective access_token and other params.
  
#### Example Response

```json
{
    "rows": {
        "current_page": 1,
        "data": [
           {
                "service": "S",
                "opening": "0.0000",
                "available": "0.0000",
                "sent_units": "5",
                "sent_credits": "5.0000",
                "deliv_units": "0",
                "on_date": "2019-05-07",
                "serial": 1
            },
            {
                "service": "S",
                "opening": "0.0000",
                "available": "0.0000",
                "sent_units": "16",
                "sent_credits": "16.0000",
                "deliv_units": "0",
                "on_date": "2018-05-08",
                "serial": 2
            },
        ---
        ],
        "first_page_url": "{domain}/rest/v1/account/activty?page=1",
        "from": 1,
        "last_page": 1,
        "last_page_url": "{domain}/rest/v1/account/activity?page=1",
        "next_page_url": null,
        "path": "{domain}/rest/v1/account/activity",
        "per_page": 25,
        "prev_page_url": null,
        "to": 16,
        "total": 16
    }
}
```
