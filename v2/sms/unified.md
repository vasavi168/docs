# Send Message Using SMS Channel

## Channel Info

```
{
	"channels": [{
		"name": "sms",
		"from": "MOBTXT",
		"recipient": {
			"group_id": "{segment_id}",
			"to": ["9189195xxxx", "91886713xxxx"]
		}
	}]
	"recipient": {
		"group_id": "{segment_id}",
		"to": ["91XXXXXX", "91XXXXXX"]
	}
}
```

#### Example Response

```json
{
  "status": "OK",
  "message": "Message Queued successfully",
  "data": [
    {
      "id": "a418d672-9781-4d97-b517-a56f7d95ad8a",
      "channel": "sms",
      "from": "MOBTXT",
      "to": "9190199xxxxx",
      "credits": 1,
      "created_at": "2021-06-18 14:48:06",
      "status": "AWAITING-DLR",
    }
  ]
}
```

#### PARAMETERS

| Name      | Description                                                 | type                | Required                       |
| --------- | ----------------------------------------------------------- | ------------------- | ------------------------------ |
| channels  | This block contains information realted messaging channel   | N/A                 | Yes                            |
| name      | Name of Messaging Channel. Ex: `sms`                   | `string`            | Yes                            |
| from      | Sender or From Number                                       | `number`            | Yes                            |
| recipient | This block contains contacts information related to channel | N/A                 | Yes                            |
| group_id  | Segment id which contain list of phone numbers              | `string` or `array` | Yes if `to` param not present  |
| to        | Receiver mobile numbers : `text`                            | `array`             | Yes, if `group_id` not present |

`Note` : The `recipient` block inside channel is related to particular communication channel and it is optional. The outside `recipient` channel contain common recipients for every channel.

#### HTTP Methods

It will support only `POST` requests.

#### API Endpoint

```
{domain}/api/{version}/
```

## Sending Text Message

```
{endpoint}sms/message/send
```

#### Example Request With Text Message

```
curl -X POST \
  '{endpoint}sms/message/send' \
  -H 'authorization: Bearer d9e1cac3812186b353c5022xxxxx' \
  -H 'content-type: application/json' \
  -d '{
	"channels": [{
		"name": "sms",
		"from": "MOBTXT"
	}],
	"recipient": {
		"to": "91XXXXXX"
	},
	"message": {
        "type": "text",
		"payload": {
			"text": "This is a simple text message from sms channel"
		}
	}
}'
```

#### PARAMETERS

| Name    | Description                                 | Limits              | Required |
| ------- | ------------------------------------------- | ------------------- | -------- |
| payload | Messaage Payload section                    | N/A                 | Yes      |
| to      | Destination mobile number with country code | NA                  | Yes      |
| text    | Message Content you want to send            | Max 4096 Characters | Yes      |

## Sending Template Message

#### API Endpoint

```
{domain}/api/{version}/
```

```
{endpoint}sms/message/send
```

#### Example Request With Template

```
curl -X POST \
  '{endpoint}sms/message/send' \
  -H 'authorization: Bearer d9e1cac3812186b353c5022xxxxx' \
  -H 'content-type: application/json' \
  -d '{
	"channels": [{
		"name": "sms",
		"from": "MOBTXT"
	}],
	"recipient": {
		"to": "91XXXXXX"
	},
	"message": {
        "type": "template",
		"payload": {
			"name": "otp",
      "namespace: "",
			"language": "en",
			"header_params": ["Replacement Text"],
			"body_params": ["223344", "10"],
      "components": {

            }
		}
	}
}'
```

#### PARAMETERS

| Name          | Description                                                                                                                                                                                         | Limits                                                                     | Required |
| ------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------- | -------- |
| name          | Template Name                                                                                                                                                                                       | N/A                                                                        | yes      |
| namespace     | Namespace of the template                                                                                                                                                                           | N/A                                                                        | yes      |
| language      | Language to send the template in. Default `en`                                                                                                                                                      | N/A                                                                        | No       |
| header_params | Can only used when there is a header of type text in the template. Up to 60 characters for all parameters and predefined template header text.                                                      | Up to 60 characters for all parameters and predefined template header text | No       |
| body_params   | Up to 1024 characters for all parameters and predefined template text.                                                                                                                              | Up to 1024 characters for all parameters and predefined template text      | No       |