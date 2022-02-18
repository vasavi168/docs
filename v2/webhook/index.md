## View Webhooks List

View all Webhooks created under your account

#### API Endpoint

```
{domain}/api/{version}/
```

#### GET

```
{endpoint}developer/webhooks
```

#### PARAMETERS

| name         | optional | value                  |
| ------------ | -------- | ---------------------- |
| filter[name] | Yes      | name of the webhok. |

#### Example Request

```
curl -X GET \
  '{endpoint}developer/webhooks' \
    -H 'Accept: application/json' \
    -H 'Authorization: Bearer 5b02112fb7xxxxxxxxx'
```

Kindly replace the token with your respective access_token.

#### Example Response

```json
{
  "rows": {
    "current_page": 1,
    "data": [
      {
        "id": "02238e36-a4c0-4231-b2be-87f96303133a",
        "user_id": 1,
        "name": "webhoook name",
        "uri": "https://demo.mobtext.info/api/messageupdate",
        "secret": null,
        "verification_code": null,
        "payload": null,
        "status": 1,
        "created_at": "2021-05-04 17:46:58",
        "updated_at": "2021-05-04 17:46:58",
        "deleted_at": null,
        "serial": 1
      }
    ],
    "first_page_url": "{endpoint}developer/webhooks?page=1",
    "from": 1,
    "last_page": 1,
    "last_page_url": "{endpoint}/developer/webhooks?page=1",
    "next_page_url": null,
    "path": "{endpoint}/developer/webhooks",
    "per_page": 25,
    "prev_page_url": null,
    "to": 1,
    "total": 1
  }
}
```


## Create Webhook

Create a Webhook using post method under your account

#### API Endpoint

```
{domain}/api/{version}/
```

#### POST

```
{endpoint}developer/webhook/create
```

#### PARAMETERS

| Name         | optional | Descriptions                                                        |
| ------------ | -------- | --------------------------------------------------------------------|
| name         | No       | Enter the name of the webhook that you want to create.              |
| uri | No       | The URL of the server that will receive the webhook POST request.            |
| status    | yes    | Enter 1 for active or 0 for inactive.                                    |
| secret  | yes    | Enter the secret that You received as the secret.                          |
| token  | yes    | Verification token for the initial webhook verification challenge. EX:123456**|

#### Example Request

```
  curl -X POST \
  {endpoint}developer/webhook/create \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer 5b02112fb7xxxxxxxxxxxxxxxx' \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  -d name=xxxxxx \
  -d uri=xxxxx \
  -d secret=xxxxx \
  -d token=xxxxx \
  -d status=1 \
```



#### Example Response

```json
{
  "status": "OK",
  "code": 200,
  "message": "Sender saved successfully",
  "id": "f66b983b-713a-4818-a691-2c684eb4eccd"
}

{
    "status": "OK",
    "code": 200,
    "message": "Webhook saved successfully",
    "data": {
        "name": "name of webhook",
        "uri": "https://example.com/",
        "secret": "*****",
        "verification_code": "*****",
        "status": "1",
        "id": "180ebbb5-9b6f-4c51-a98a-**********",
    }
}
```

## Edit Webhook

Edit a Webhook using put method under your account

#### API Endpoint

```
{domain}/api/{version}/
```

#### PUT

```
{endpoint}developer/webhook/edit/{id}
```

#### PARAMETERS

| Name         | optional | Descriptions                                                  |
| ------------ | -------- | ------------------------------------------------------------- |
| name | No       | Enter the name of the webhook that you want to modify                 |
| uri    | No    | The URL of the server that will receive the webhook POST request.      |
| status    | yes    |Enter 1 for active or 0 for inactive.                               |
| secret    | yes    | Enter the secret that You received as the secret.                  |

#### Example Request

```
curl -X PUT \
  {endpoint}developer/webhook/edit/93af9991-f1cc-4b36-abd5-xxxxxx \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer 5b02112fb7xxxxxxxxx' \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  -d name=xxx \
  -d uri=xxxxx \
```

#### Example Response

```json
{
  "status": "OK",
  "code": 200,
  "message": "Webhook updated successfully"
}
```


