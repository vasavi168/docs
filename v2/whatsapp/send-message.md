# Whatsapp For Business API


#### HTTP Methods
  
  It will support only `POST` requests.

## Sending Message Using Whatsapp

#### Sending Text Message

```
{endpoint}whatsapp/message/send?from=80191912XXXX&to=918919525XXXX&type=text&text=Hi This is test sms from whatsapp for business
```

####  MANDATORY PARAMETERS

| Name     | Descriptions |
|----------|--------------|
| from | Mobile Number from which you want to send sms |
| to | Number To whom call will connect first with CountryCode|
| type | Type of the message : text / template / contact |
| text | Message text you want to send |


#### Example Request With Text Messgae

```
curl -X POST \
  'http://portal.mobtexting.co/api/v2/whatsapp/message/send?access_token=d9e1cac3812186b353c50xxxxxxx' \
  -d 'from=91886713XXXX&to=91788788XXXX&type=text&text=checking%20sms%20for%20whatspp'
```

#### Example Response

```json
{
    "status": "OK",
    "message": "Message Queued successfully"
}
```

## Sending Message Using Template

```
{endpoint}whatsapp/message/send?from=80191912XXXX&to=918919525XXXX&type=template&name=first_whatsapp&category=notification&variables=laxman,1234,laxman@gmail.com
```

####  MANDATORY PARAMETERS

| Name     | Descriptions |
|----------|--------------|
| from | Mobile Number from which you want to send sms |
| to | Number To whom call will connect first with CountryCode|
| type | Type of the message : tempalte |
| name | Name of the template |
| category | Category of the template |

#### OPTIONAL PARAMETERS

| Name     | Descriptions |
|----------|--------------|
| varibles | values of the variable comma seperated : laxman, 91891952XXX, laxman@gmail.com |
| language | Language code of the template : default English (en) |


```
Example of the template looks as follows :

{{1}} code: {{2}}. Valid for {{3}} minutes.

```
Here {{1}}, {{2}}, {{3}} are replacement variables which is different for each message. Same needs to be for `variables` parameter.

####  Example Request With Template

```
curl -X POST \
  {endpoint}whatsapp/message/send?access_token=d9e1cac3812186b353c50xxxxxxxx' \
  -H 'authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsImp0aSI6ImFjYTcwODlkMzEzMjBiYjZlMjM2Y2IyMzE2NGZmYjVjYjc5YzQ4MDIyMDk2ZTRjMjFkZWRlN2QxMmYxN2ViNjk4Y2Q0YmM3Njk2Y2IyZTYzIn0.eyJhdWQiOiI4OTI2ODA3ZjY4MTdiZDJlMDNmYzkxMTQiLCJqdGkiOiJhY2E3MDg5ZDMxMzIwYmI2ZTIzNmNiMjMxNjRmZmI1Y2I3OWM0ODAyMjA5NmU0YzIxZGVkZTdkMTJmMTdlYjY5OGNkNGJjNzY5NmNiMmU2MyIsImlhdCI6MTU3NjY2NDkyOCwibmJmIjoxNTc2NjY0OTI4LCJleHAiOjE1NzkzNDMzMjgsInN1YiI6IiIsInNjb3BlcyI6W10sImN1c3RvbWVyX2lkIjoxMDA1MDI5fQ.PqiidE2FtYQhecqMsP-xVn-3jz9GPipnCFkpYMd6M8o15yX6_M6UqtBBIGCQC4fyRtyzfcmxAi8BGC7iTf-CU4vmswvuX7npx3qUxsEQ9doUH9XdED3lhpnR8nET8Gqb8kQ4KD745VOmMsX7PSgL2LNzsT7gl5mTVaxPn63kYo7mcz_eVeaTueud3V3eBB5XuTkkhdAoId6-Q2EH4Qt8xnBPzlLFAzdxGG3lPR9qoZDsSTp5RURR5s191GJZEJIU2quxLXo_BYvDouynIGe2a-dw4iIrzQZOOM9XEb8-_XxnhQGwIQ6aKh9FGfGAXVTP6-VHMJaM514w' \
  -H 'content-type: application/x-www-form-urlencoded' \
  -d 'type=template&category=notification&name=order_update&name=order_update&variables=laxman%2C1234%2C1333.00&from=918867135684&to=918919525224'

  ```
#### Example Response

```json
{
    "status": "OK",
    "message": "Message Queued successfully"
}
```