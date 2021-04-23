# Send SMS Using XML object

#### API Endpoint

```
{domain}/api/{{version}}/
```

#### POST
```
{endpoint}sms/send/xml
```

You can send sms using `POST` method content in body.

`root` entry holds the default values for each node. You can overwite the `root` values inside `nodes` value except `dlr_url`, `service` and `time`.

#### BODY

```xml
<?xml version="1.0" encoding="UTF-8"?>
<data>
	
   <root>
      <dlr_url><![CDATA[http://domain.com/status]]></dlr_url>
      <message><![CDATA[global message]]></message>
      <sender>SANKAR</sender>
      <service>T</service>
      <time>2018-07-05 10:30AM</time>
      <type>N</type>
      <entity_id>1233555XXXXXXXXX</entity_id>
      <template_id>9002929XXXXXXX</template_id>
   </root>
   
   <nodes>
      <node>
         <custom>9190199556xx</custom>
         <custom1>9190199556xx</custom1>
         <message><![CDATA[this message will be used insted of root]]></message>
         <sender>SANKAR</sender>
         <to>919019955622</to>
      </node>
      <node>
         <custom>34</custom>
         <to>9188671356xx</to>
         <sender>SANKAR</sender>
      </node>
   </nodes>

</data>
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
| template_id | TemplateId registered in DLT portal|

#### Example Request

```curl
curl -X POST \
  "{endpoint}sms/send/xml" \
  -H 'Authorization: Bearer 425b8dec5d6b618fa9c08xxxx' \
  -H 'Cache-Control: no-cache' \
  -H 'Content-Type: application/xml' \
  -d '<?xml version="1.0" encoding="UTF-8"?>
<data>
	
   <root>
      <dlr_url><![CDATA[http://domain.com/status]]></dlr_url>
      <message><![CDATA[global message]]></message>
      <sender>SANKAR</sender>
      <service>T</service>
      <time>2018-07-05 10:30AM</time>
      <type>N</type>
      <flash>0</flash>
      <entity_id>1233555XXXXXXXXX</entity_id>
      <template_id>9002929XXXXXXX</template_id>
   </root>
   
   <nodes>
      <node>
         <message><![CDATA[this message will be used insted of root]]></message>
         <sender>SANKAR</sender>
         <to>9190199556xx</to>
         <custom>9190199556xx</custom>
         <custom1>9190199556xx</custom1>
      </node>
      <node>
         <custom>34</custom>
         <to>9188671356xx</to>
         <sender>SANKAR</sender>
      </node>
   </nodes>

</data>'
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