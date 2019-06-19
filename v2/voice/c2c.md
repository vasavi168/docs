# Click2Call

This Voice API supports the following:

#### HTTP Methods
  
   It will support both GET and POST requests.

## Call Initiation

#### POST/GET

C2C Using To as Mobile Number
```
{endpoint}voice/c2c?bridge=80191912XX&from=80106077XX&to=901930XXX
```
C2C Using To as Flow ID
```
{endpoint}voice/c2c?bridge=80191912XX&from=80106077XX&to=flow:19
```

####  MANDATORY PARAMETERS

| Name     | Descriptions |
|----------|--------------|
| bridge | DID number for call initiation |
| from | To whom call will connect first |
| to | Phone number / IVR flow to which call has to connect |


####  OPTIONAL PARAMETERS


| Name     | Descriptions |
|----------|--------------|
| mid |  Message id for reference |r |
| v | Additional variables |

#### Example Request

```
curl -X GET \
  "{domain}/api/{{version}}/voice/c2c?access_token=209eccd40ee3a2e14af7fe45b21xxx&bridge=91801010XXX&from=9189195XXX&to=91901xxxxxx"
```

#### Example Response

```json
{
  "status": 200,
  "message": "Call initiated successfully",
}
```