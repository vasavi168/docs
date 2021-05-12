## Create Smart Link

Convert long url into short and smart url.

#### API Endpoint

```
{domain}/api/{version}/
```

#### POST

```
{endpoint}link/create
```

#### PARAMETERS

| Name        | Optional | Descriptions                     |
| ----------- | -------- | -------------------------------- |
| long_url    | no       | Long Url                         |
| title       | yes      | Link title.                      |
| webhook_id  | yes      | Webhook ID created in our portal |
| is_advanced | yes      | Want to track mobile number      |

#### Example Request

```
curl -X POST \
  '{endpoint}link/create' \
    -H 'Accept: application/json' \
    -H 'Authorization: Bearer 5b02112fb7xxxxxxxxx'
    -H 'Content-Type: application/x-www-form-urlencoded' \
  -d 'title=smart%20link&long_url=https%3A%2F%2Fwww.google.com&advanced=1'
```

#### Example Response

```json
{
  "status": "OK",
  "message": "Link Created Successfully",
  "token": "e",
  "link": "http://tx9.in/e",
  "id": 12344
}
```
