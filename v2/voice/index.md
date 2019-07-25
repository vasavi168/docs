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


#### Filters

You can also use our build in filters to change data while passing to your system.

Buildin filters are `cut` and `data_format`. Filters are seperated by `|`

Ex: if you want to get the last 10 digits of the `from` number: `{from|cut:-10}`

Ex: Want to get `start_at` date in `DD/MM/YYYY` : `{start_at|date_format:d/m/Y}`

#### Conditional values

Sometimes you want to get the second values if first value not exists.

`||` can be used to evolute the conditonal statement. ex: `{caller.name||caller.email}`

Take the caller email if caller name is empty

#### Default values

Sometimes you want to get the default values if variable does not provide any value

`#` can be used to pass the default values. ex: `{caller.mobile#9190199xxxx}`

#### Other variable within variable

Sometimes you want to use the other variable value with in variable to get the right value

`[]` can used to pass the variable with in other variable. ex: `{questions.[jump].name}`

Here we are using `jump` variable to get the original value of question.

it will be `question.0.name`, `question.1.name`, `question.2.name`

#### Variables in play

We can define how to treat the variables while playing.

`digits` we want to say as digits, we can use `{otp@digits}`

`number` we want to say as number, we can use `{otp@number}`

`play` we want to download the mp3 file and play, we can use `{clip@play}`

`sound` to play in build sound files, we can use `{clip@sound}`

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
| COMPLETED | Second leg is answered.


#### Call Strategies

| Name     | Descriptions |
|----------|--------------|
| parallel | call all available agents until one answers
| sequential | Take turns calling each available agents
| random | Call random agents who ever available
| fewest | Call the one with fewest completed calls
