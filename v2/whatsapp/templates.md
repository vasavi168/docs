# Whatsapp Template

## API Endpoint

```
{domain}/api/{version}/
```

## View Template

View all the Templates list.

#### GET

```
{endpoint}whatsapp/templates
```

#### PARAMETERS

| name           | optional | value                                                 |
| -------------- | -------- | ----------------------------------------------------- |
| filter[id]     | Yes      | The id is template id                                 |
| filter[name]   | Yes      | The name is template name                             |
| filter[type]   | Yes      | The type is template type EX: (text, template)        |
| filter[status] | Yes      | (0, 2 are Pending),(1 is Approved),or (3 is Rejected) |

#### Example Request

```
curl -X GET \
  '{endpoint}whatsapp/templates' \
    -H 'Accept: application/json' \
    -H 'Authorization: Bearer 5b02112fb7xxxxxxxxx'
```

Kindly replace the token with your respective access_token and other params.

#### Example Response

```json
{
    "status": "OK",
    "code": 200,
    "message": "Templates List",
    "data": [
        {
            "id": "2cf9e59f-d4f1-47ba-81d3-a288f31ca164",
            "name": "text_template",
            "number": "91861xxxxxxx",
            "type": "text",
            "category": "Marketing",
            "language": "English",
            "body": "Hi,This is WhatsApp text template message.",
            "payload": "{\"type\":\"text\",\"payload\":{\"text\":\"Hi,This is WhatsApp text template message.\",\"language\":\"en\"}}",
            "status": "Pending",
            "created_at": "2023-02-08T10:41:30.000000Z",
            "updated_at": "2023-02-08T10:41:30.000000Z"
        }
    ],
    "links": {
        "first": "{endpoint}whatsapp/templates?page=1",
        "last": "{endpoint}whatsapp/templates?page=1",
        "prev": null,
        "next": null
    },
    "meta": {
        "current_page": 1,
        "from": 1,
        "last_page": 1,
        "links": [
            {
                "url": null,
                "label": "&laquo; Previous",
                "active": false
            },
            {
                "url": "{endpoint}whatsapp/templates?page=1",
                "label": "1",
                "active": true
            },
            {
                "url": null,
                "label": "Next &raquo;",
                "active": false
            }
        ],
        "path": "{endpoint}whatsapp/templates",
        "per_page": 15,
        "to": 1,
        "total": 1
    }
}
```

## Create Templates

#### POST

```
{endpoint}whatsapp/templates
```

#### PARAMETERS

| name     | description                                                                                                                       | Type                  | Required |
| -------- | --------------------------------------------------------------------------------------------------------------------------------- | --------------------- | -------- |
| type     | values are `text`, `template`, `json` only                                                                                        | `string`              | Yes      |
| name     | special characters not allowed, should be unique.                                                                                 | `string`              | Yes      |
| category | `marketing`, `OTP` or `transactional` if you are using `kaleyra` template                                                         | `string`              | Yes      |
| language | Example : `eu`, `en_US`                                                                                                           | `string`              | Yes      |
| number   | business number Ex:(91861xxxxxxxx)                                                                                               | `string` or `integer` | Yes      |
| body     | if `text` type only content message, `template` type content message with variables @{{#var#}}, `json` type should be json format | `string` or `json`    | Yes      |

## Text Type

### Example Request

```
curl -X POST \
  '{endpoint}whatsapp/templates' \
  -H 'authorization: Bearer 5b02112fb7xxxxxxxxx' \
  -H 'content-type: application/json' \
  -d '{
    "type": "text",
    "name": "new_text",
    "category": "Marketing",
    "language": "en",
    "number": "91861xxxxxxxx",
    "body": "Hi,This is WhatsApp test message."
}'
```

### Example Response

```
{
    "status": "OK",
    "code": 200,
    "message": "Template created successfully.",
    "data": []
}
```

## Template Type

In body content message don't use the variables @{{#var#}} at end.

### Example Request

```
curl -X POST \
  '{endpoint}whatsapp/templates' \
  -H 'authorization: Bearer 5b02112fb7xxxxxxxxx' \
  -H 'content-type: application/json' \
  -d '{
    "type": "template",
    "name": "new_template",
    "category": "Marketing",
    "language": "en",
    "number": "91861xxxxxxxx",
    "body": "Hi @{{#var#}}, Thank you for using the template message."
}'
```

### Example Response

```
{
    "status": "OK",
    "code": 200,
    "message": "Template created successfully.",
    "data": []
}
```

## Json Type

In body content message should be json format.

### Example Request

```
curl -X POST \
  '{endpoint}whatsapp/templates' \
  -H 'authorization: Bearer 5b02112fb7xxxxxxxxx' \
  -H 'content-type: application/json' \
  -d '{
    "type": "json",
    "name": "new_json",
    "category": "Marketing",
    "language": "en",
    "number": "91861xxxxxxxx",
    "body": {"message" : "Hello user this is the json message"}
}'
```

### Example Response

```
{
    "status": "OK",
    "code": 200,
    "message": "Template created successfully.",
    "data": []
}
```

## Interactive Type

#### PARAMETERS

| name        | description                                                               | Type                  | Required |
| ----------- | ------------------------------------------------------------------------- | --------------------- | -------- |
| type        | values are `interactive` or `media` only                                  | `string`              | Yes      |
| name        | special characters not allowed, should be unique.                         | `string`              | Yes      |
| category    | `marketing`, `OTP` or `transactional` if you are using `kaleyra` template | `string`              | Yes      |
| language    | Example : `eu`, `en_US`                                                   | `string`              | Yes      |
| number      | business number Ex:(91861xxxxxxxx)                                       | `string` or `integer` | Yes      |
| header      | Inside header `header_type` is required                                   | `object`              | Yes      |
| header_type | value is `text` or `media`                                                | `string`              | Yes      |
| body        | body content message, optional variable @{{#var#}}                        | `string`              | Yes      |
| footer      | footer content message                                                    | `string`              | Yes      |

### Header type is Text

`Note` : if `header_type` value is `text` then `content` field and value is required.

### Example Request

```
curl -X POST \
  '{endpoint}whatsapp/templates' \
  -H 'authorization: Bearer 5b02112fb7xxxxxxxxx' \
  -H 'content-type: application/json' \
  -d '{
    "type": "interactive",
    "name": "new_interactive_with_text",
    "language": "en",
    "category": "ACCOUNT_UPDATE",
    "number": 91861xxxxxxxx,
    "header": {
        "header_type": "text",
        "content" : "Hello @{{#var#}}"
    },
    "body": "Welcome to @{{#var#}},Thank you for using.",
    "footer": "from whatsapp template"
}'
```

### Header type is media

`Note` : if `header_type` value is `media` then `media` object is required inside `media` object.
`media_type` and `url` is required. `media_type` are `image`, `video`, `audio` or `document`.`name`, `caption` are optional.

### Example Request

```
curl -X POST \
  '{endpoint}whatsapp/templates' \
  -H 'authorization: Bearer 5b02112fb7xxxxxxxxx' \
  -H 'content-type: application/json' \
  -d '{
    "type": "interactive",
    "name": "new_interactive_with_media",
    "language": "en",
    "category": "ACCOUNT_UPDATE",
    "number": 91861xxxxxxxx,
    "header": {
        "header_type": "media",
        "media" : {
            "media_type" : "image",
            "url": "https://www.gstatic.com/webp/gallery/4.sm.jpg",
            "name": "image",
        }
    },
    "body": "Hi @{{#var#}},This is WhatsApp test message.",
    "footer": "footer content"
}'
```

### Example Response

```
{
    "status": "OK",
    "code": 200,
    "message": "Template created successfully.",
    "data": []
}
```

## Media Type

`Note` : `body` and `footer` fields are not required.

### Example Request

```
curl -X POST \
  '{endpoint}whatsapp/templates' \
  -H 'authorization: Bearer 5b02112fb7xxxxxxxxx' \
  -H 'content-type: application/json' \
  -d '{
    "type": "media",
    "name": "new_media",
    "language": "en",
    "category": "ACCOUNT_UPDATE",
    "number": 91861xxxxxxxx,
    "header": {
        "header_type": "media",
        "media" : {
            "media_type" : "image",
            "url": "https://www.gstatic.com/webp/gallery/4.sm.jpg",
            "name": "media",
            "caption":"caption"
        }
    }
}'
```

### Example Response

```
{
    "status": "OK",
    "code": 200,
    "message": "Template created successfully.",
    "data": []
}
```

## Delete Templates

#### DELETE

```
{endpoint}whatsapp/templates/{id}
```

Replace the {id} with the actual id of the template that you would like to delete.

#### Example Request

```
curl -X DELETE \
  {endpoint}whatsapp/templates/7d77d0ef-63df-4ffb-83d6-xxxxxxxx \
    -H 'Accept: application/json' \
    -H 'Authorization: Bearer 5b02112fb7xxxxxxxxx'
```

#### Example Response

```json
{
    "status": "OK",
    "code": 200,
    "message": "Template Successfully Deleted",
    "data": []
}
```
