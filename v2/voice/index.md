## Voice Flow


###  REPLACEABLE VARIABLES

We generate some of the variables in flow process, those can used to pass the information your system.

All variables should be enclosed between `{}` braces. ex: `{to}`
You can access the Array of the variables with `.` dot notation. Example if you want to access the caller name information from caller object `{caller.name}`

#### FLOW VARIABLES

| Name     | Scope | Description |
|----------|-------|-------------|
| id | global | Call unique id |
| from | global | Call from number with country code |
| to | global | Call to number with country code |
| bridge | global | DID number with country code |
| start_at | global | Call Start time in `YYYY-MM-DD h:i:s` format |
| end_at | global | Call end time in `YYYY-MM-DD h:i:s` format |
| date | global | Current time in `YYYY-MM-DD h:i:s` format |
| unixtime | global | Current time in `unixtime` format |
| caller.country | global | Caller two letters country code. ex: `IN` (India) |
| caller.provider | global | Caller two letters operator code. ex: `RJ` (Reliance JIO) |
| caller.region | global | Caller two letters region code. ex: `KA` (karnataka) |
| caller.name | global | Caller name if avaliable in contacts |
| caller.email | global | Caller email if avaliable in contacts |


You can also use our build in filters to change data while passing to your system.

Buildin filters are `cut` and `data_format`. Filters are seperated by `|`

Ex: if you want to get the last 10 digits of the `from` number: `{from|cut:-10}`

Ex: Want to get `start_at` date in `DD/MM/YYYY` : `{start_at|date_format:d/m/Y}`

###  CALL STATUS

#### Description of Status:

| Name     | Descriptions |
|----------|--------------|
| ANSWER | Call is answered. A successful dial. The caller reached the callee.
| BUSY | Busy signal. The dial command reached its number but the number is busy.
| NOANSWER | The dial command reached its number, the number rang for too long, then the dial timed out.
| CANCEL | Call is cancelled. The dial command reached its number but the caller hung up before the callee picked up.
| CONGESTION | This status is usually a sign that the dialled number is not recognised.
| CHANUNAVAIL | Channel unavailable. On SIP, peer may not be registered.
| RECEIVED | Call received in ivr system but not call forward happen.
| MISSED | Call received in ivr system but not agent responsed to the call.
