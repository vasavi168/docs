#### Curl

```
curl --location --request GET '{endpoint}/api/v2/link/urls' \
--header 'Accept: application/json' \
--header 'Authorization: Bearer 7160f04c05870ee88812a435f65xxxxx' \
--header 'Content-Type: application/x-www-form-urlencoded' \
--data-urlencode 'long_url=https://www.mobtexting.com' \
--data-urlencode 'title=new-smart-link'
```

Kindly replace the token with your respective access_token and other params.

#### C#
```
var client = new RestClient("{endpoint}/api/v2/link/urls");
client.Timeout = -1;
var request = new RestRequest(Method.GET);
request.AddHeader("Accept", "application/json");
request.AddHeader("Authorization", "Bearer 7160f04c05870ee88812a435f65xxxxx");
request.AddHeader("Content-Type", "application/x-www-form-urlencoded");
request.AddParameter("long_url", "https://www.mobtexting.com");
request.AddParameter("title", "new-smart-link");
IRestResponse response = client.Execute(request);
Console.WriteLine(response.Content);
```

#### Java Script
```
var settings = {
  "url": "{endpoint}/api/v2/link/urls",
  "method": "GET",
  "timeout": 0,
  "headers": {
    "Accept": "application/json",
    "Authorization": "Bearer 7160f04c05870ee88812a435f65xxxxx",
    "Content-Type": "application/x-www-form-urlencoded"
  },
  "data": {
    "long_url": "https://www.mobtexting.com",
    "title": "new-smart-link"
  }
};

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

#### Node
```
var axios = require('axios');
var qs = require('qs');
var data = qs.stringify({
  'long_url': 'https://www.mobtexting.com',
  'title': 'new-smart-link' 
});
var config = {
  method: 'get',
  url: '{endpoint}/api/v2/link/urls',
  headers: { 
    'Accept': 'application/json', 
    'Authorization': 'Bearer 7160f04c05870ee88812a435f65xxxxx', 
    'Content-Type': 'application/x-www-form-urlencoded'
  },
  data : data
};

axios(config)
.then(function (response) {
  console.log(JSON.stringify(response.data));
})
.catch(function (error) {
  console.log(error);
});
```
