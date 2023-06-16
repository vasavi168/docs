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

| name           | optional | value                                                |
| -------------- | -------- | ---------------------------------------------------- |
| filter[id]     | Yes      | The id is template id                                |
| filter[name]   | Yes      | The name is template name                            |
| filter[type]   | Yes      | The type is template type EX: (text, template)       |
| filter[status] | Yes      | (1 is Approved), (2 are Pending) and (3 is Rejected) |

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
            "alias": "text-template",
            "number": "91861xxxxxxx",
            "type": "text",
            "category": "marketing",
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

| name          | description                                    | Type                  | Required |
| ------------- | ---------------------------------------------- | --------------------- | -------- |
| type          | values are `text`, `template`, `mediatemplate` | `string`              | Yes      |
| name          | name should be a alphanumeric                  | `string`,`integer`    | Yes      |
| category      | `marketing`, `authentication` or `utility`     | `string`              | Yes      |
| language      | Example : `eu`, `en_US`                        | `string`              | Yes      |
| number        | business number Ex:(91861xxxxxxxx)             | `string` or `integer` | Yes      |
| meta_approval | Send to meta approval                          | boolean               | Yes      |

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
    "category": "marketing",
    "language": "en",
    "number": "91861xxxxxxxx",
    "meta_approval" : true,
    "payload": {
        "type": "text",
        "payload": {
            "text": "This is a simple text message from whatsapp channel"
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

## Template Type

### Example Request

```
curl -X POST \
  '{endpoint}whatsapp/templates' \
  -H 'authorization: Bearer 5b02112fb7xxxxxxxxx' \
  -H 'content-type: application/json' \
  -d '{
    "type": "template",
    "name": "new_template",
    "category": "marketing",
    "language": "en",
    "number": "91861xxxxxxxx",
    "meta_approval" : true,
    "payload": {
        "type": "template",
        "payload": {
            "text": "Hello @{{#var#}}, This is a simple text message from whatsapp channel",
            "body_params": ["user"]
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
    "category": "marketing",
    "language": "en",
    "number": "91861xxxxxxxx",
    "meta_approval" : true,
    "payload": {
        "type": "json",
        "payload" : {
            "text" : {"name" : "hlo"}
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

## Media Template Type

### With Button

#### PARAMETERS

| name                                | optional | value                                 |
| ----------------------------------- | -------- | ------------------------------------- |
| payload.type                        | No       | `mediatemplate`                       |
| payload.payload.header              | No       | The header content                    |
| payload.payload.body                | No       | The body content                      |
| payload.payload.footer              | No       | The footer content                    |
| choices                             | Yes      | The choices buttons is optional       |
| choices.type                        | No       | `actions`                             |
| choices.actions                     | No       | expect the object at least one        |
| choices.actions.type                | No       | `phone_number`, `url`                 |
| choices.actions.phone_number_text   | No       | max 20 characters                     |
| choices.actions.phone_number        | No       | country code prefix required Ex:(+91) |
| choices.actions.website_url_type    | No       | value is `Static`                     |
| choices.actions.website_button_text | No       | max 20 characters                     |
| choices.actions.website_url         | No       | should be url                         |

### Example Request

```
curl -X POST \
  '{endpoint}whatsapp/templates' \
  -H 'authorization: Bearer 5b02112fb7xxxxxxxxx' \
  -H 'content-type: application/json' \
  -d '{
    "type": "mediatemplate",
    "name": "mediatemplate_with_buttons",
    "category": "marketing",
    "language": "en",
    "number": "91861xxxxxxxx",
    "meta_approval" : true,
    "payload": {
        "type": "mediatemplate",
        "payload": {
            "name": "mediatemplate_with_buttons",
            "language": "en",
            "body_params": [],
            "header_params": [],
            "header": {
                "type": "text",
                "payload": {
                    "text": "Welcome"
                }
            },
            "body": {
                "type": "text",
                "payload": {
                    "text": "Any doubts please contact us"
                }
            },
            "footer": {
                "type": "text",
                "payload": {
                    "text": "Thank you!"
                }
            },
            "url": null,
            "choices": {
                "type": "actions",
                "actions": [
                    {
                        "type": "phone_number",
                        "phone_number_text": "Any queries call",
                        "phone_number": "+91861xxxxxxx"
                    },
                    {
                        "type": "url",
                        "website_url_type" => "Static"
                        "website_button_text" => "More info visit"
                        "website_url" => "www.mobtexting.com"
                    }
                ]
            }
        }
    }
}'
```

### With Reply

#### PARAMETERS

| name                       | optional | value                           |
| -------------------------- | -------- | ------------------------------- |
| choices                    | Yes      | The choices buttons is optional |
| choices.type               | No       | `reply`                         |
| choices.reply              | No       | object can not be empty         |
| choices.reply.type         | No       | `quick_reply`                   |
| choices.reply.quick_reply1 | No       | max 20 characters               |
| choices.reply.quick_reply2 | No       | max 20 characters               |
| choices.reply.quick_reply3 | Yes      | value is `Static`               |

### Example Request

```
curl -X POST \
  '{endpoint}whatsapp/templates' \
  -H 'authorization: Bearer 5b02112fb7xxxxxxxxx' \
  -H 'content-type: application/json' \
  -d '{
    "type": "mediatemplate",
    "name": "mediatemplate_with_reply",
    "category": "marketing",
    "language": "en",
    "number": "91861xxxxxxxx",
    "meta_approval" : true,
    "payload": {
        "type": "mediatemplate",
        "payload": {
            "name": "mediatemplate_with_reply",
            "language": "en",
            "body_params": [],
            "header_params": [],
            "header": {
                "type": "text",
                "payload": {
                    "text": "Hello User"
                }
            },
            "body": {
                "type": "text",
                "payload": {
                    "text": "Do you like template?"
                }
            },
            "footer": {
                "type": "text",
                "payload": {
                    "text": "Thank you!"
                }
            },
            "url": null,
            "choices": {
                "type": "reply",
                "reply": {
                    "type": "quick_reply",
                    "quick_reply1": "Yes",
                    "quick_reply2": "No"
                    "quick_reply3": "maybe"
                }
            }
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

## Media Type

#### PARAMETERS

| name         | optional | value                                   |
| ------------ | -------- | --------------------------------------- |
| payload.type | No       | `image`, `audio`, `video` or `document` |

### Example Request

```
curl -X POST \
  '{endpoint}whatsapp/templates' \
  -H 'authorization: Bearer 5b02112fb7xxxxxxxxx' \
  -H 'content-type: application/json' \
  -d '{
    "type": "media",
    "name": "new_media",
    "category": "marketing",
    "language": "en",
    "number": "91861xxxxxxxx",
    "meta_approval" : true,
    "payload": {
        "type": "image",
        "payload": {
            "url": "https://www.buildquickbots.com/whatsapp/media/sample/jpg/sample01.jpg",
            "filename": "filename",
            "caption": "caption",
            "language": "en"
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
