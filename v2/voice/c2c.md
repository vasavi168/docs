# Click2Call

This Voice API supports the following:

#### HTTP Methods
  
  It will support both GET and POST requests.

## Call Initiation

#### API Endpoint

```
{domain}/api/{{version}}/
```

#### POST/GET

C2C Using To as Mobile Number
```
{endpoint}voice/c2c?bridge=80191912XX&from=9180106077XX&to=91901930XXX
```
C2C Using To as Flow ID
```
{endpoint}voice/c2c?bridge=80191912XX&from=9180106077XX&to=flow:19
```

####  MANDATORY PARAMETERS

| Name     | Descriptions |
|----------|--------------|
| bridge | DID number for call initiation |
| from | Number To whom call will connect first with CountryCode|
| to | Phone number with Country Code / IVR flow to which call has to connect |


####  OPTIONAL PARAMETERS

| Name     | Descriptions |
|----------|--------------|
| mid |  Message id for reference |r |
| callback | Callback url once call completed (urlencoded) |
| variables | `Array` of the variables which can be used in flow |
| record | Record this conversation (default `0`). allowed: 0 or 1 |
| duration | Limit the call duration in minutes. default (none) |

#### Example Request

```
curl -X GET \
  "{endpoint}voice/c2c?access_token=209eccd40ee3a2e14af7fe45b21xxx&bridge=91801010XXX&from=9189195XXX&to=91901xxxxxx"
```

#### Example Response

```json
{
  "status": 200,
  "message": "Call initiated successfully",
}
```

####  CALLBACK REPLACEABLE VARIABLES

Callback is a functionality to get notified through an API call when a call is completed. One needs to follow below steps to achieve valid callback

| Name     | Descriptions |
|----------|--------------|
| bridge | DID number for call initiation |
| from | To whom call will connect first |
| to | Phone number / IVR flow to which call has to connect |
| start_at | Call Start time in `YYYY-MM-DD h:i:s` format |
| end_at | Call end time in `YYYY-MM-DD h:i:s` format |
| date | Current time in `YYYY-MM-DD h:i:s` format |
| unixtime | Current time in `unixtime` format |
| duration | Duration of the call in seconds (first call) |
| billing | Duration of the call in seconds (second call) |
| status | Call Status |
| status1 | Call Status of first call |
| status2 | Call Status of second call|
| recording_url | Recording Url if call got recorded |


You can also use our build in filters to change data while passing to your system.

Buildin filters are `cut` and `data_format`. Filters are seperated by `|`

Ex: if you want to get the last 10 digits of the `from` number: `{from|cut:-10}`

Ex: Want to get `start_at` date in `DD/MM/YYYY` : `{start_at|date_format:d/m/Y}`


#### Example Callback Url

```
  https://www.domain.com/ack/receive?status={status}&start={start_at}&recording_url={recording_url}
```

Append callback value with API

```
&callback=https%3A%2F%2Fwww.domain.com%2Fack%2Freceive%3Fstatus%3D%7Bstatus%7D%26start%3D%7Bstart_at%7D%26recording_url%3D%7Brecording_url%7D
```

- The response codes other than 200 or 202 are not taken into consideration and requests for such response codes are considered as failed.
- The method used for sending the callback report onto the client’s URL is `GET`.