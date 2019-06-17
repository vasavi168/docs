## Voice


###  REPLACEABLE VARIABLES

We generate some of the variables in flow process, those can used to pass the information your system.

All variables should be enclosed between `{}` braces. ex: `{to}`
You can access the Array of the variables with `.` dot notation. Example if you want to access the caller name infomration from caller object `{caller.name}`

####  GLOBAL VARIABLES

| Name     | Description |
|----------|--------------|
| from | Call from number with country code |
| to | Call to number with country code |
| caller.country | Caller two letters country code |
| caller.provider | Caller two letters operator code |
| caller.region | Caller two letters region code |
| caller.name | Caller name if avaliable in contacts |
| caller.email | Caller email if avaliable in contacts |
