#### Curl
```
curl --location --request POST '{endpoint}/api/v2/link/urls' \
--header 'Accept: application/json' \
--header 'Authorization: Bearer 7160f04c05870ee88812a435f65xxxx' \
--header 'Content-Type: application/json' \
--data-raw '{
    "long_url": "https://www.mobtexting.com",
    "title": "new-smart-link"
}'
```

#### C#
```
var client = new RestClient("{endpoint}/api/v2/link/urls");
client.Timeout = -1;
var request = new RestRequest(Method.POST);
request.AddHeader("Accept", "application/json");
request.AddHeader("Authorization", "Bearer 7160f04c05870ee88812a435f65xxxxx");
request.AddHeader("Content-Type", "application/json");
var body = @"{" + "\n" +
@"    ""long_url"": ""https://www.mobtexting.com""," + "\n" +
@"    ""title"": ""new-smart-link""" + "\n" +
@"}";
request.AddParameter("application/json", body,  ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
Console.WriteLine(response.Content);
```

#### Java Script
```
var settings = {
  "url": "{endpoint}/api/v2/link/urls",
  "method": "POST",
  "timeout": 0,
  "headers": {
    "Accept": "application/json",
    "Authorization": "Bearer 7160f04c05870ee88812a435f65xxxxx",
    "Content-Type": "application/json"
  },
  "data": JSON.stringify({
    "long_url": "https://www.mobtexting.com",
    "title": "new-smart-link"
  }),
};

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

#### Node
```
var axios = require('axios');
var data = JSON.stringify({
  "long_url": "https://www.mobtexting.com",
  "title": "new-smart-link"
});

var config = {
  method: 'post',
  url: '{endpoint}/api/v2/link/urls',
  headers: { 
    'Accept': 'application/json', 
    'Authorization': 'Bearer 7160f04c05870ee88812a435f65xxxx', 
    'Content-Type': 'application/json'
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