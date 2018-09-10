# Send SMS Using XML object

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
      <flash>0</flash>
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

#### Example Request

```curl
curl -X POST \
  {endpont}sms/send/xml \
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