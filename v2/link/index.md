## View Smart Links

View all smart links created under your account


#### API Endpoint

```
{domain}/api/{{version}}/
```

#### GET

```
{domain}/rest/v1/link
```

#### PARAMETERS


#### Example Request

```
curl -X GET \
  '{domain}/rest/v1/link?access_token=38e896f55670311982434xxxx' \
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
                "id": "27",
                "user_id": "26",
                "title": "teletack",
                "token": "secQ42",
                "long_url": "https://o5o4o6.com/?a=1457&c=298748&s1=TN(air(40_50)",
                "webhook": null,
                "options": null,
                "visits": "0",
                "last_visited": null,
                "is_advanced": "0",
                "status": "1",
                "created_at": "2018-07-30 10:22:44",
                "updated_at": "2018-07-30 10:22:44",
                "serial": 1,
                "created": "Jul 30, 2018 10:22 AM",
                "updated": "Jul 30, 2018 10:22 AM",
                "short_url": "http://tx9.in/secQ42",
                "short_link": "http://tx9.in/secQ42"
            },
        ---
        ],
        "first_page_url": "{domain}/rest/v1/link?page=1",
        "from": 1,
        "last_page": 1,
        "last_page_url": "{domain}/rest/v1/link?page=1",
        "next_page_url": null,
        "path": "{domain}/rest/v1/link",
        "per_page": 25,
        "prev_page_url": null,
        "to": 16,
        "total": 16
    }
}
```
