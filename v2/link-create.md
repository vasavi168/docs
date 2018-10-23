## Create Smart Link 

Convert long url into short and smart url.

#### POST

```
{domain}/rest/v1/link/create
```

#### PARAMETERS

| Name     | Optinal | Descriptions |
|----------|--------------|----------|
| title | yes |  Link title.|
| long_url | | Long Url|
| webhook | yes | Long Url|
| is_advanced | yes | Want to track mobile number |


#### Example Request

```
curl -X POST \
  '{domain}/rest/v1/link/create?access_token=20afe0df418f6004axxxx' \
  -H 'Accept: application/json' \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  -H 'cache-control: no-cache' \
  -d 'title=smart%20link&long_url=https%3A%2F%2Fwww.google.com&advanced=1'
```

Kindly replace the token with your respective access_token and other params.
  
#### Example Response

```json
{
  {
    "status": "OK",
    "message": "Link Created Successfully",
    "token": "e",
    "link": "http://tx9.in/e"
  }
}
```
