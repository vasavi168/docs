# Send SMS Using JSON object

#### POST
```
{endpoint}sms/send/json
```

You can send sms using `POST` method content in body.

All params in send sms will support in JSON also.

`root` entry holds the default values for each node. You can overwite the `root` values inside `nodes` value except `dlr_url` and `time`.

#### BODY

```json
{
    "root": {
        "unicode": "auto",
        "flash": 0,
        "sender": "TXTSMS",
        "service": "T",
        "message": "global message",
        "dlr_url": "http://www.domainname.com/dlr?status={status}",
        "time": ""
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

#### Example Request

```curl
curl --request POST \
  --url {endpoint}/send/json \
  --header 'Content-Type: application/json' \
  --data '{
    "root": {
        "unicode": "auto",
        "flash": 0,
        "sender": "TXTSMS",
        "service": "T",
        "message": "global message",
        "dlr_url": "http://www.domainname.com/dlr?status={status}",
        "time": ""
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