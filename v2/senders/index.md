## View Senders List

View all Sender-ids created under your account

#### GET

```
{domain}/rest/v1/senders
```

#### PARAMETERS

| name         | optional | value                  |
| ------------ | -------- | ---------------------- |
| filter[name] | Yes      | name of the sender-id. |

#### Example Request

```
curl -X GET \
  '{domain}//rest/v1/senders?access_token=38e896f55670311982434xxxx' \
  -H 'Accept: application/json' \
  -H 'Content-Type: application/x-www-form-urlencoded' \
```

Kindly replace the token with your respective access_token and other params.

#### Example Response

```json
{
  "rows": {
    "current_page": 1,
    "data": [
      {
        "id": "b7a85301-dd60-4834-9c2a-xxxxxxxxxxx",
        "user_id": "72",
        "name": "test",
        "entity_name": "test",
        "message": "smstxt",
        "document": null,
        "status": "1",
        "is_open": "0",
        "created_at": "2019-03-01 11:13:09",
        "updated_at": "2019-03-01 11:13:56",
        "serial": 1,
        "created": "Mar 01, 2019 11:13 AM",
        "updated": "Mar 01, 2019 11:13 AM"
      }
    ],
    "first_page_url": "{domain}/rest/v1/senders?page=1",
    "from": 1,
    "last_page": 1,
    "last_page_url": "{domain}/rest/v1/senders?page=1",
    "next_page_url": null,
    "path": "{domain}/rest/v1/senders",
    "per_page": 25,
    "prev_page_url": null,
    "to": 1,
    "total": 1
  }
}
```
