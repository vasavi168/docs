#### WEBHOOK (OR) CALLBACK URL

Callback is a functionality to get notified through an API call when a call is completed. One needs to follow below steps to achieve valid callback

| Name          | Descriptions                                 |
| ------------- | -------------------------------------------- |
| to            | Phone number to which call has connected     |
| start_at      | Call Start time in `YYYY-MM-DD h:i:s` format |
| end_at        | Call end time in `YYYY-MM-DD h:i:s` format   |
| duration      | Duration of the call in seconds (first call) |
| status        | Call Status                                  |
| recording_url | Recording Url if call got recorded           |

You can also use our build in filters to change data while passing to your system.

Buildin filters are `cut` and `data_format`. Filters are seperated by `|`

Ex: if you want to get the last 10 digits of the `from` number: `{from|cut:-10}`

Ex: Want to get `start_at` date in `DD/MM/YYYY` : `{start_at|date_format:d/m/Y}`

#### Example Callback Url

```
  https://www.domain.com/ack/receive?status={status}&start={start_at}&recording_url={recording_url}&endat={end_at}
```

Webook value can be provided while doing the campaign from panel.

If you are doing OBD using api, we need to send `callback` paramater to send webhook url.

```
&callback=https%3A%2F%2Fwww.domain.com%2Fack%2Freceive%3Fstatus%3D%7Bstatus%7D%26start%3D%7Bstart_at%7D%26recording_url%3D%7Brecording_url%7D
```

- The response codes other than 200 or 202 are not taken into consideration and requests for such response codes are considered as failed.

- The method used for sending the callback report onto the client’s URL is `GET`.
