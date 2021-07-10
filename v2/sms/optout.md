## OPTOUT

Traditionally, SMS campaigns are targeted to those customers who are registered subscribers to your SMS
services. You can block the customer's number using our optout feature. Once the customer's number is blocked, meanwhile if you try to trigger Sms to the customer's number then our system will automatically reject the Sms triggered and the customer will not recieve the sms.

#### API Endpoint

```
{domain}/api/{version}/
```

#### POST

```
{endpoint}sms/optout
```

#### MANDATORY PARAMETERS

| Name   | Descriptions                           |
| ------ | -------------------------------------- |
| number | Mobile numbers that you want to block. |

#### Example Request

```
curl -X POST \
  '{endpoint}sms/optout'
   -H 'Content-Type: application/x-www-form-urlencoded' \
   -H 'Accept: application/json' \
   -H 'Authorization: Bearer 38e896f55670311982434e929559xxxx'
   -F number=9174114xxxxx
```

On triggering the above API the specified numbers will be added to your optout list.

#### Example Response

```json
{
  'status'  => 200,
  'message' => 'Number added to optout list'
}
```
