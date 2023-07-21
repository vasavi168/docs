#### Curl
```
curl -X POST \
  '{endpoint}link/urls/{id}' \
    -H 'Accept: application/json' \
    -H 'Authorization: Bearer 5b02112fb7xxxxxxxxx'
    -H 'Content-Type: application/json' \
    -d '{
      "long_url": "https://www.example.com",
      "title": "testing",
      "webhook_id": "5558",
      "is_advanced": "1"
}'

```
#### C#
```
var client = new RestClient("{endpoint}/api/v2/link/urls/150");
client.Timeout = -1;
var request = new RestRequest(Method.PUT);
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
  "url": "{endpoint}/api/v2/link/urls/150",
  "method": "PUT",
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
  method: 'put',
  url: '{endpoint}/api/v2/link/urls/150',
  headers: { 
    'Accept': 'application/json', 
    'Authorization': 'Bearer 7160f04c05870ee88812a435f65xxxxx', 
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