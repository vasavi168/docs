# RCS Messaging - Getting Started

RCS Messaging is evolution of SMS enabling enterprises and individuals to exchange rich media like images, videos and interactive content with the same ease as SMS.

## Features of RCS Messaging

Verified Messages

Sending rich card messages like images and audio video files

Rich card carousels

Message with suggestion action list

Message with suggested reply set

Two Way Messaging

Messaging revoking for undelivered SMS

#### API Endpoint

```
{domain}/api/{version}/rcs
```

Note: Few elements in endpoint may change for service to service.

## AUTHENTICATION

Each API request will have to contain request headers that include your access token to authenticate the request.

Don't have an access token? You will find your access token in the `Developers -> API Keys/Access Tokens` in menu bar.

When your application can't send an Authorization header, you can use the GET parameter `access_token` to provide your access key.

We do provide incoming request whitelisting on our platform for our REST API. You can whitelist the IP addressess while generating the access token.

### CURL Example

```shell
$ curl {endpoint}v2/rcs/message/send \
-H 'Authorization: Bearer 38e896f55670311982434e929559xxxx'
```

### Response Codes

| Code | Description                             |
| ---- | --------------------------------------- |
| 401  | Unauthorised or Authentication failure. |
| 200  | Authentication success.                 |
