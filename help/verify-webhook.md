# Webhook  Verification

Our servers will dispatch a highly configurable HTTP
request to your application endpoint which is mentioned in Webhooks section, containing many details about the messaging or any other communication channel.


####  Validation Key

On creating a webhook, we request you to verify the webhook. This is a security measure that will be useful for both of us.

It makes sure the URL you entered actually points to a valid webhook  abd able to receive messages from our servers.


We send an initial HTTP request to the webhook URL you provided. It contains a  query parameter called `token` i.e validation key you entered while creating the webhook.

You need send a response with status code 200 and a JSON object in the request body that contains a validation key.


Ex: While creating webhook validation key given as '9012XX' for the url `yourdomain.com/receive/callback`


```
curl -X POST \
  'yourdomain.com/receive/callback?token=9012XX' \
  -H 'authorization: Bearer 1233XXX'
  -H 'Content-Type: application/json' \
  -d '{
    "validation_key": "9012XXXX",
    "challenge": "a234qwe",
  }'
```

#### Expected Response From Customer End

```
{
  "validation_key": "9012XX"
}
```


#### Example Request with `secret`


Additionally, you can configure a secret for each webhook. The secret will be sent as a Bearer token in the
Authorization header of the webhook requests. This acts as a simple password system where you may check any requests for the correct token.

Ex: While creating webhook secret created as '1233XXXX' for the url `yourdomain.com/receive/callback`


```
curl -X GET \
  'yourdomain.com/receive/callback' \
  -H 'authorization: Bearer 1233XXX' 
```


#### After Verification

After successful verification you are able to receive DLR updates to your webhook as mentioned in below
format.

```
curl -X POST \ 
  https://www.domain.com/ack/receive \
  -H 'content-type: application/json' \
  -d '{
      "id": "b34e35ad-fe34-4a8b-977c-b21cd76cd7d6:1",
      "mobile": "918921269xxx",
      "status": "DELIVRD",
      "credits": "2.0000",
      "units": 2,
      "deliv_time": "2021-04-09 16:27:51",
      "sent_time": "2021-04-09 16:27:35",
      "submit_time": "2021-04-09 16:27:39",
      "cid": "1234444XXXX",
      "custom": "9882XXXX",
      "custom1": "campaign-3344",
      "custom2": "new-campXXX",
      "location": "India",
      "region" : "Bangalore",
      "provider": "Jio",
      "location_code": "in",
      "region_code": "KA",
      "provider_code": "RJ",
    }
```