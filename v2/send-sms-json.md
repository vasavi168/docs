# Send SMS Using JSON object

#### POST
```
{endpoint}sms/send/json
```

You can send sms using `POST` method content in body.

All params in send sms will support in JSON also.

`root` entry holds the default values for each node. You can overwite the `root` values inside `nodes` value except `dlr_url`, `service` and `time`.

#### BODY

```json
{
    "root": {
        "type": "A",
        "flash": 0,
        "sender": "TXTSMS",
        "message": "global message",
        "service": "T",
        "dlr_url": "http://www.domainname.com/dlr?status={status}",
        "time": "",
        "entity_id": "222343XXXXXX",
        "header_id": "10333XXXXXX",
        "template_id": "2290003XXXXXX"
    },
    "nodes": [
        {
            "to": "919019xxxx2",
            "custom": "346576-446565-45657-XFTR",
            "sender": "txtmes",
            "message": "Message from & json api node 1"
        },
        {
            "to": "9188xxxxxxxxxx",
            "custom": "34"
        }
    ]
}
```

####  MANDATORY PARAMETERS

| Name     | Descriptions |
|----------|--------------|
| to | Phone number to send with country prefix. (multiple numbers can be separated by comma.) |
| message | The content of the SMS |
| sender | The registered and approved Sender-id |
| service | Determines whether the SMS to be sent is Transactional, Promotional or other. |


####  OPTIONAL PARAMETERS


| Name     | Descriptions |
|----------|--------------|
| dlr_url | The Url for which the SMS response to be sent after sending the SMS can be specified using this parameter. [read more](/docs/{{version}}/sms-push-dlr)|
| time |  Schedule time (in format i.e,yyyy-mm-dd hh:mm:ss) at which the SMS has to be sent. |
| type | The SMS to be sent is Unicode, Normal or Auto detect. (value "U", "N" or "A") |
| flash | This parameter can be used to send flash sms via API ( Values 1 or 0.) |
| custom | Any customised parameters can be passed  using this parameter |
| custom1 | Any customised parameter |
| port | Port number to which SMS has to be sent |
| entity_id | Entityid registered in DLT portal |
| header_id | HeaderId registered in DLT portal |
| template_id | TemplateId registered in DLT portal|

#### Example Request

```curl
curl --request POST \
  --url {endpoint}sms/send/json \
  -H 'Authorization: Bearer 209eccd40ee3a2e14af7fe45b21xxx'
  -H 'Content-Type: application/json' \
  --data '{
    "root": {
        "type": "A",
        "flash": 0,
        "sender": "TXTSMS",
        "message": "global message",
        "service": "T",
        "dlr_url": "http://www.domainname.com/dlr?status={status}",
        "time": "",
        "entity_id": "222343XXXXXX",
        "header_id": "10333XXXXXX",
        "template_id": "2290003XXXXXX"
    },
    "nodes": [
        {
            "to": "919019xxxx2",
            "custom": "346576-446565-45657-XFTR",
            "sender": "txtmes",
            "message": "Message from & json api node 1"
        },
        {
            "to": "9188xxxxxxxxxx",
            "custom": "34"
        }
    ]
}'
```

#### Example Response

```json
{
  "status": 200,
  "message": "2 numbers accepted for delivery.",
  "data": [
    {
      "id": "b34e35ad-fe34-4a8b-977c-b21cd76cd7d6:1",
      "mobile": "919019xxxx2",
      "status": "AWAITING-DLR",
      "units": 1,
      "length": 7,
      "charges": 1,
      "customid": "346576-446565-45657-XFTR",
      "customid1": "",
      "iso_code": null,
      "submitted_at": "2018-07-09 16:27:35"
    },
    {
      "id": "b34e35ad-fe34-4a8b-977c-b21cd76cd7d6:1",
      "mobile": "9188xxxxxxxxxx",
      "status": "AWAITING-DLR",
      "units": 1,
      "length": 7,
      "charges": 1,
      "customid": "34",
      "customid1": "",
      "iso_code": null,
      "submitted_at": "2018-07-09 16:27:35"
    }
  ]
}
```