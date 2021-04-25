## View Templates

View all templates created under your account

#### GET

```
{domain}/rest/v1/templates
```

#### Filters

| name           | Optional | value                 |
| -------------- | -------- | --------------------- |
| filter[t.name] | Yes      | Name of the template. |

#### Example Request

```
curl -X GET \
  '{domain}/rest/v1/templates?filter[t.name]=test' \
  -H 'Authorization: Bearer 81fe2ebd35xxxxxxxxxx' \
```

Kindly replace the token with your respective access_token and other params.

#### Example Response

```json
{
  "rows": {
    "current_page": 1,
    "data": [
      {
        "id": "0d85ebbc-a83a-40fc-94bd-7dc2ec392b38",
        "user_id": "78",
        "sender_id": "93af9991-f1cc-4b36-abd5-7c17221148d5",
        "sender": "txtme",
        "name": "test",
        "body": "THanks for calling",
        "body_length": "18",
        "match_count": "0",
        "percentage": "0",
        "status": "0",
        "created_at": "2019-03-05 11:26:36",
        "updated_at": "2019-03-05 11:26:36",
        "serial": 1,
        "created": "Mar 05, 2019 11:26 AM",
        "updated": "Mar 05, 2019 11:26 AM"
      }
    ],
    "first_page_url": "{domain}/rest/v1/templates?page=1",
    "from": 1,
    "last_page": 1,
    "last_page_url": "{domain}/rest/v1/templates?page=1",
    "next_page_url": null,
    "path": "{domain}/rest/v1/templates",
    "per_page": 25,
    "prev_page_url": null,
    "to": 1,
    "total": 1
  }
}
```
