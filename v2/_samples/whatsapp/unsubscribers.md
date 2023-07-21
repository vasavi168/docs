#### Curl
```
curl -X POST\
  '{endpoint}whatsapp/suppressions/unsubscribers' \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer 7160f04c0587xxxxxxxxxxxxxxxx' \
  -H 'Content-Type: application/json' \
  -d '{
    "receiver": "98xxxxxxxx",
    "type": "xxxxxxx",
    "value": "xxxxx"
}'
```

Kindly replace the token with your respective access_token and other params.

#### C#
```
var client = new RestClient("http://127.0.0.1:8000/api/v2/whatsapp/suppressions/unsubscribers");
client.Timeout = -1;
var request = new RestRequest(Method.GET);
request.AddHeader("Authorization", "Bearer 7160f04c05870ee88812a435f65ade07");
request.AddHeader("Content-Type", "application/json");
var body = @"{" + "\n" +
@"""receiver"": ""919515199493""," + "\n" +
@"""type"": ""tag""," + "\n" +
@"""value"": 1" + "\n" +
@"" + "\n" +
@"}";
request.AddParameter("application/json", body,  ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
Console.WriteLine(response.Content);
```

####  Java Script

```
var settings = {
  "url": "http://127.0.0.1:8000/api/v2/whatsapp/suppressions/unsubscribers",
  "method": "GET",
  "timeout": 0,
  "headers": {
    "Authorization": "Bearer 7160f04c05870ee88812a435f65ade07",
    "Content-Type": "application/json"
  },
  "data": JSON.stringify({
    "receiver": "919515199493",
    "type": "tag",
    "value": 1
  }),
};

$.ajax(settings).done(function (response) {
  console.log(response);
});
```

#### Node Js
```
var axios = require('axios');
var data = JSON.stringify({
  "receiver": "919515199493",
  "type": "tag",
  "value": 1
});

var config = {
  method: 'get',
  url: 'http://127.0.0.1:8000/api/v2/whatsapp/suppressions/unsubscribers',
  headers: { 
    'Authorization': 'Bearer 7160f04c05870ee88812a435f65ade07', 
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
