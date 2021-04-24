# API OVERVIEW

API's are built on `POST` and `GET` method with `REST` standard that allows you to easily send messages to your end users and make your work easy. You can send alerts, reminders, and notifications, or you can send verification messages containing one-time passcodes (OTP) using this feature of ours.

This documentation gives you instructions on how to integrate our api through various _*HTTP*_ API and _*JSON*_ API.

We'll be helping you configure, access and use the API for SMS.

To integrate our SMS API, any HTTP recipient in any programming language can be used.

#### API Endpoint

```
{domain}/api/{{version}}/
```

Note: Few elements in endpoint may change for service to service.

## API Collection Postman link

```
https://www.getpostman.com/collections/6eaad21725156053df42
```

## AUTHENTICATION

Each API request will have to contain request headers that include your access token to authenticate the request.

Don't have an access token? You will find your access token in the `Developers -> API Keys/Access Tokens` in menu bar.

When your application can't send an Authorization header, you can use the GET parameter `access_token` to provide your access key.

We do provide incoming request whitelisting on our platform for our REST API. You can whitelist the IP addressess while generating the access token.

### CURL Example

```shell
$ curl {endpoint}account/balance \
-H 'Authorization: Bearer 38e896f55670311982434e929559xxxx'
```

### GET Example

```shell
$ curl {endpoint}account/balance?access_token=38e896f55670311982434e92955xxxx
```

If possible, please use the Authorization header.

## RATE LIMITS

To keep you in compliance, We maintains the appropriate rate limits:

| API |                                                                                 VALUE                                                                                  |
| --- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------: |
| SMS | All Pull APIs are rate limited to 1000 requests per minute. Once this limit has been crossed, your requests will be rejected with an HTTP 429 'Too Many Requests' code |

You can contact our support team to increase the limit. Our team will increase the limit case by case.

## ERROR CODES

We uses standard HTTP status codes to indicate success or failure of an API request. Codes in the 2xx range indicate that a request was successfuly processed and codes in the 4xx range indicate that there was an error that resulted from the information sent (e.g. authentication, no balance or a missing or wrong parameter).

In case of an error, the body of the response includes a JSON formatted response that tells you exactly what is wrong.

#### ATTRIBUTES

| Name    | Value                                                                                                                                     |
| ------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| status  | This represents the error type. OK or 200 is success and rest everthing is failed.                                                        |
| code    | This represents the http code. This value is optional. Not be avaliable in all responses.                                                 |
| message | A human-readable description of the error. You can provide your users with this information to indicate what they can do about the error. |

## HTTP STATUS CODES

| code | Descriptions                                                                     |
| ---- | -------------------------------------------------------------------------------- |
| 200  | OK - Everything went as planned.                                                 |
| 202  | Accepted - Request accepted.                                                     |
| 400  | Bad Request - Something in your header or request body was malformed.            |
| 401  | Unauthorised - Necessary credentials were either missing or invalid.             |
| 403  | Your credentials are valid, but you don't have access to the requested resource. |
| 404  | The resources cannot be found                                                    |
| 409  | Conflict - You might be trying to update the same resource concurrently.         |
| 422  | Validation error                                                                 |
| 429  | Too Many Requests - You are calling our APIs more frequently than we allow.      |
| 5xx  | Something went wrong on our end. Please try again                                |
