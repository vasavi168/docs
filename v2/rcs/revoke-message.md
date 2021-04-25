# RCS Messaging Api

#### API Endpoint

```
{domain}/api/{version}/
```

## Revoking Message

Your agent can revoke messages that it has sent but that the RBM platform hasn't delivered to the user. If the RBM platform successfully revokes a message, the platform deletes the message from the user's message queue and doesn't deliver the message.

```
{endpoint}rcs/message/revoke
```

#### MANDATORY PARAMETERS

| Name | Descriptions                                           |
| ---- | ------------------------------------------------------ |
| to   | Mobile number of the user you want to send rcs message |
| id   | Message Id you want to revoke                          |

#### Example Request With Text Messgae

```
curl -X DELETE \
  'http://portal.mobtexting.co/api/v2/rcs/message/revoke?access_token=d9e1cac3812186b353c5022xxxxxxxxd&to=9640024149&id=1233444xxxxxxxx
```

#### Example Response For Success

```json
{
    "code": "200",
    "status": "OK",
    "data": {
        "features": {
            "RICHCARD_STANDALONE",
            "ACTION_CREATE_CALENDAR_EVENT",
            "ACTION_DIAL",
            "ACTION_OPEN_URL",
            "ACTION_SHARE_LOCATION",
            "ACTION_VIEW_LOCATION",
            "RICHCARD_CAROUSEL"
        }
    }
}
```

#### Example Response For Failure

```json
{
  "code": 404,
  "status": "failed",
  "message": null,
  "data": {
    "error": {
      "code": 404,
      "message": "The specified phone number cannot be reached by RBM at this time.",
      "status": "NOT_FOUND"
    }
  }
}
```
