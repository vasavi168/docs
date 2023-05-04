## View Unsubscribers

View all created unsubscribers

#### API Endpoint

```
{domain}/api/{version}/
```

#### GET

```
{endpoint}outgoing/suppressions/unsubscribers
```

#### Example Request

```
curl -X GET \
  '{endpoint}outgoing/suppressions/unsubscribers' \
    -H 'Accept: application/json' \
    -H 'Authorization: Bearer 7160f04c0587xxxxxxxxxxxxxxxx'
```

Kindly replace the token with your respective access_token and other params.

#### Example Response

```json
{
    "status": "OK",
    "code": 200,
    "message": "Unsubscribers list",
    "data": [
        {
            "id": "0e3fdaad-2b46-4dcf-8b14-xxxxxxxxxxxx",
            "mobile": "9198xxxxxxxx",
            "country": "IN",
            "type": "xxxxxxx",
            "value": "xxxxx",
            "created_at": "2023-04-11T12:53:29.000000Z"
        },
        ....
    ],
    "links": {
        "first": "{endpoint}outgoing/suppressions/unsubscribers?page=1",
        "last": "{endpoint}outgoing/suppressions/unsubscribers?page=1",
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
                "url": "{endpoint}outgoing/suppressions/unsubscribers?page=1",
                "label": "1",
                "active": true
            },
            {
                "url": null,
                "label": "Next &raquo;",
                "active": false
            }
        ],
        "path": "{endpoint}outgoing/suppressions/unsubscribers",
        "per_page": 15,
        "to": 6,
        "total": 6
    }
}
```

## Create Unsubscriber

Create contact using POST method.

#### API Endpoint

```
{domain}/api/{version}/
```

#### POST

```
{endpoint}outgoing/suppressions/unsubscribers
```

#### PARAMETERS

| Name   | optional | Descriptions                                        |
| ------ | -------- | --------------------------------------------------- |
| mobile | No       | Enter the mobile that you want to create            |
| type   | Mixed    | Type of the mobile like (tag, product, sender, all) |
| value  | Mixed    | Input the value of the type                         |

#### Example Request

```
curl -X POST\
  '{endpoint}outgoing/suppressions/unsubscribers' \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer 7160f04c0587xxxxxxxxxxxxxxxx' \
  -H 'Content-Type: application/json' \
  -d '{
    "mobile": "98xxxxxxxx",
    "type": "xxxxxxx",
    "value": "xxxxx"
}'
```

#### Example Response

```json
{
  "status": "OK",
  "code": 200,
  "message": "Contact added successfully",
  "data": {
    "id": "848c22a0-6969-455a-b5dc-4b119016b55b",
    "mobile": "919876xxxxxx",
    "country": "IN",
    "type": "tag",
    "value": "promo",
    "created_at": "2023-04-11T12:50:17.000000Z"
  }
}
```

## Edit Unsubscriber

Edit contact using put method.

#### API Endpoint

```
{domain}/api/{version}/
```

#### PUT

```
{endpoint}outgoing/suppressions/unsubscribers/{id}
```

Replace the {id} with the actual id of the mobile that you would like to Edit.

#### PARAMETERS

| Name   | optional | Descriptions                                        |
| ------ | -------- | --------------------------------------------------- |
| mobile | No       | Enter the mobile that you want to edit              |
| type   | Mixed    | Type of the mobile like (tag, product, sender, all) |
| value  | Mixed    | Input the value of the type                         |

#### Example Request

```
curl -X PUT \
  '{endpoint}outgoing/suppressions/unsubscribers/848c22a0-6969-455a-b5dc-4b119016b55b' \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer 7160f04c0587xxxxxxxxxxxxxxxx' \
  -H 'Content-Type: application/json' \
  -d '{
    "mobile": "98xxxxxxxx",
    "type": "xxxxxxx",
    "value": "xxxxx"
}'

```

#### Example Response

```json
{
  "status": "OK",
  "code": 200,
  "message": "Contact updated successfully",
  "data": {
    "id": "848c22a0-6969-455a-b5dc-xxxxxxxxxxxx",
    "mobile": "919876xxxxxx",
    "country": "IN",
    "type": "tag",
    "value": "promo1",
    "created_at": "2023-04-11T12:50:17.000000Z"
  }
}
```

## View Single Unsubscriber

View one created contact

#### API Endpoint

```
{domain}/api/{version}/
```

#### GET

```
{endpoint}outgoing/suppressions/unsubscribers/{id}
```

#### Example Request

```
curl -X GET \
  '{endpoint}outgoing/suppressions/unsubscribers/0e3fdaad-2b46-4dcf-8b14-xxxxxxxxxxxx' \
    -H 'Accept: application/json' \
    -H 'Authorization: Bearer 7160f04c0587xxxxxxxxxxxxxxxx'
```

Kindly replace the token with your respective access_token .

#### Example Response

```json
{
  "status": "OK",
  "code": 200,
  "message": "Unsubscribers data",
  "data": {
    "id": "0e3fdaad-2b46-4dcf-8b14-xxxxxxxxxxxx",
    "mobile": "9198xxxxxxxx",
    "country": "IN",
    "type": "xxxxxxx",
    "value": "xxxxxx",
    "created_at": "2023-04-11T12:53:29.000000Z"
  }
}
```

## Import Unsubscriber

Import contacts by uploading a file

#### API Endpoint

```
{domain}/api/{version}/
```

#### POST

```
{endpoint}/outgoing/suppressions/unsubscribers/import
```

#### Example Request

```
curl -X POST\
  '{endpoint}outgoing/suppressions/unsubscribers/import' \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer 7160f04c0587xxxxxxxxxxxxxxxx' \
  -H 'Content-Type: application/form-data' \
  -F 'file=@"yourfilepath/contacts.xlsx"'
```

#### PARAMETERS

```
| Name     | Description                                              | Limits | Required |
| -------- | -------------------------------------------------------- | ------ | -------- |
| url      | Public url of the contact file. Either HTTP/HTTPS link.  | 100 MB | Yes      |
| caption  | some text for contact caption                            | N/A    | No       |
| filename | contact file name                                        | N/A    | No       |
```

#### EXAMPLE RESPONSE

```json
{
  "status": "OK",
  "message": "Contacts accepted for import"
}
```

## Delete Unsubscriber

Delete contact using delete method

#### API Endpoint

```
{domain}/api/{version}/
```

#### DELETE

```
{endpoint}outgoing/suppressions/unsubscribers/{id}
```

Replace the {id} with the actual id of the contact that you would like to delete.

#### Example Request

```
curl -X DELETE \
  '{endpoint}outgoing/suppressions/unsubscribers/0e3fdaad-2b46-4dcf-8b14-aafffbxxxxxx' \
    -H 'Accept: application/json' \
    -H 'Authorization: Bearer 7160f04c0587xxxxxxxxxxxxxxxx'
```

#### Example Response

```json
{
  "status": "OK",
  "code": 200,
  "message": "Deleted Successfully",
  "data": []
}
```

## Cleanup Unsubscriber

Delete all contacts at once

#### API Endpoint

```
{domain}/api/{version}/
```

#### POST

```
{endpoint}outgoing/suppressions/unsubscribers
```

#### Example Request

```
curl -X DELETE \
  '{endpoint}outgoing/suppressions/unsubscribers' \
    -H 'Accept: application/json' \
    -H 'Authorization: Bearer 7160f04c0587xxxxxxxxxxxxxxxx'
```

#### Example Response

```json
{
  "status": "OK",
  "code": 200,
  "message": "Deleted Successfully",
  "data": []
}
```
