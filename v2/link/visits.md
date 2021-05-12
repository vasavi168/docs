## View Smart Link Visits

Access the perticular Link Visits

#### API Endpoint

```
{domain}/api/{version}/
```

#### GET

```
{endpoint}link/visits/{id}
```

#### PARAMETERS

| Name | Optinal | Descriptions   |
| ---- | ------- | -------------- |
| id   |         | Smart Link id. |

#### Example Request

```
curl -X GET \
  '{endpoint}link/visits/4' \
    -H 'Accept: application/json' \
    -H 'Authorization: Bearer 5b02112fb7xxxxxxxxx'
```

Kindly replace the token with your respective access_token and other params.

#### Example Response

```json
{
    "status": "OK",
    "rows": {
        "current_page": 1,
        "data": [
            {
                "id": "835b7433-0aaf-457c-88e7-7433b00d6a80",
                "user_id": "26",
                "link_id": "20",
                "client_ip": "127.0.0.1",
                "scheme": null,
                "host": null,
                "query_string": "",
                "user_agent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_13_6) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/67.0.3396.99 Safari/537.36",
                "browser": "Chrome",
                "browser_version": "67.0.3396.99",
                "browser_lang": "en",
                "browser_engine": "Blink",
                "resolution": null,
                "platform": "Mac",
                "platform_version": "10.13.6",
                "platform_name": "MAC",
                "device_type": "desktop",
                "device_brand": "Apple",
                "device_model": "",
                "touch_enabled": "0",
                "latitude": "",
                "longitude": "",
                "country": "localhost",
                "country_code": "",
                "region": "",
                "city": "localhost",
                "zipcode": "",
                "timezone": "",
                "options": null,
                "created_at": "2018-08-13 11:36:18",
                "visit_id": "58a26f02-73e2-40ef-ab35-de427e9a6c6b",
                "token": "JFlCjw",
                "message_id": "JFlCjw",
                "mobile": "9019955622",
                "serial": 1,
                "created": "Aug 13, 2018 11:36 AM"
            },
        ----

        ],
        "first_page_url": "{domain}/rest/v1/link/visits/20?page=1",
        "from": 1,
        "last_page": 1,
        "last_page_url": "{domain}/rest/v1/link/visits/20?page=1",
        "next_page_url": null,
        "path": "{domain}/rest/v1/link/visits/20",
        "per_page": 25,
        "prev_page_url": null,
        "to": 21,
        "total": 21
    },
    "id": "20"
}
```
