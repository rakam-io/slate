---
title: API Reference
language_tabs:
  - shell
  - javascript
  - java
  - csharp
  - go
  - php
  - python
  - ruby

toc_footers:
 - <a href='https://app.rakam.io/register'>Register for a Developer Key</a>

includes:
    - errors
search: true
---
# Introduction

```
We have language bindings in shell, javascript, java, csharp, go, php, python, ruby! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.
```

An analytics platform API that lets you create your own analytics services.

### Version
Version: 0.8

## Contact Information
Email: contact@rakam.io

### License
License: Apache License 2.0

License url: http://www.apache.org/licenses/LICENSE-2.0.html

### URI scheme
Host: app.rakam.io
BasePath: /

# Ab testing


A/B Testing Module

## Create test

```shell
curl --request POST \
  --url https://app.rakam.io//ab-testing/create \
  --header 'master_key: 5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' \
  --data '{"name":"str","variants":[{}],"goal":{}}'
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//ab-testing/create',
  headers: { master_key: '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' },
  body: { name: 'str', variants: [ {} ], goal: {} },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"name\":\"str\",\"variants\":[{}],\"goal\":{}}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//ab-testing/create")
  .post(body)
  .addHeader("master_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")
  .build();

Response response = client.newCall(request).execute();
```

```csharp
var client = new RestClient("https://app.rakam.io//ab-testing/create");
var request = new RestRequest(Method.POST);
request.AddHeader("master_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8");
request.AddParameter("undefined", "{\"name\":\"str\",\"variants\":[{}],\"goal\":{}}", ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
```

```go
package main

import (
	"fmt"
	"strings"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://app.rakam.io//ab-testing/create"

	payload := strings.NewReader("{\"name\":\"str\",\"variants\":[{}],\"goal\":{}}")

	req, _ := http.NewRequest("POST", url, payload)

	req.Header.Add("master_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->append('{"name":"str","variants":[{}],"goal":{}}');

$request->setRequestUrl('https://app.rakam.io//ab-testing/create');
$request->setRequestMethod('POST');
$request->setBody($body);

$request->setHeaders(array(
  'master_key' => '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//ab-testing/create"

payload = "{\"name\":\"str\",\"variants\":[{}],\"goal\":{}}"
headers = {'master_key': '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'}

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.rakam.io//ab-testing/create")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["master_key"] = '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
request.body = "{\"name\":\"str\",\"variants\":[{}],\"goal\":{}}"

response = http.request(request)
puts response.read_body
```

> The above command returns JSON structured like this:

```json
{
  "message" : "str"
}
```

### HTTP Request
`POST /ab-testing/create`
### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|name|true|string||
|variants|true|[Variant](#variant) array||
|goal|true|[Goal](#goal)||
|options|false|object||
|id|false|integer (int32)||
|collectionName|false|string||
|connectorField|false|string||


### Responses for status codes
|200|403|
|----|----|
|[SuccessMessage](#successmessage)|[ErrorMessage](#errormessage)|


## Delete report

```shell
curl --request POST \
  --url https://app.rakam.io//ab-testing/delete \
  --header 'master_key: 5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' \
  --data '{"id":4}'
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//ab-testing/delete',
  headers: { master_key: '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' },
  body: { id: 4 },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"id\":4}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//ab-testing/delete")
  .post(body)
  .addHeader("master_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")
  .build();

Response response = client.newCall(request).execute();
```

```csharp
var client = new RestClient("https://app.rakam.io//ab-testing/delete");
var request = new RestRequest(Method.POST);
request.AddHeader("master_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8");
request.AddParameter("undefined", "{\"id\":4}", ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
```

```go
package main

import (
	"fmt"
	"strings"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://app.rakam.io//ab-testing/delete"

	payload := strings.NewReader("{\"id\":4}")

	req, _ := http.NewRequest("POST", url, payload)

	req.Header.Add("master_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->append('{"id":4}');

$request->setRequestUrl('https://app.rakam.io//ab-testing/delete');
$request->setRequestMethod('POST');
$request->setBody($body);

$request->setHeaders(array(
  'master_key' => '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//ab-testing/delete"

payload = "{\"id\":4}"
headers = {'master_key': '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'}

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.rakam.io//ab-testing/delete")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["master_key"] = '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
request.body = "{\"id\":4}"

response = http.request(request)
puts response.read_body
```

> The above command returns JSON structured like this:

```json
{
  "message" : "str"
}
```

### HTTP Request
`POST /ab-testing/delete`
### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|id|true|integer (int32)||


### Responses for status codes
|200|403|
|----|----|
|[SuccessMessage](#successmessage)|[ErrorMessage](#errormessage)|


## Get report

```shell
curl --request POST \
  --url https://app.rakam.io//ab-testing/get \
  --header 'read_key: 5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' \
  --data '{"id":4}'
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//ab-testing/get',
  headers: { read_key: '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' },
  body: { id: 4 },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"id\":4}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//ab-testing/get")
  .post(body)
  .addHeader("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")
  .build();

Response response = client.newCall(request).execute();
```

```csharp
var client = new RestClient("https://app.rakam.io//ab-testing/get");
var request = new RestRequest(Method.POST);
request.AddHeader("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8");
request.AddParameter("undefined", "{\"id\":4}", ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
```

```go
package main

import (
	"fmt"
	"strings"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://app.rakam.io//ab-testing/get"

	payload := strings.NewReader("{\"id\":4}")

	req, _ := http.NewRequest("POST", url, payload)

	req.Header.Add("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->append('{"id":4}');

$request->setRequestUrl('https://app.rakam.io//ab-testing/get');
$request->setRequestMethod('POST');
$request->setBody($body);

$request->setHeaders(array(
  'read_key' => '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//ab-testing/get"

payload = "{\"id\":4}"
headers = {'read_key': '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'}

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.rakam.io//ab-testing/get")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["read_key"] = '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
request.body = "{\"id\":4}"

response = http.request(request)
puts response.read_body
```

> The above command returns JSON structured like this:

```json
{
  "name" : "str",
  "variants" : [ {
    "name" : "str",
    "weight" : 1,
    "data" : "object"
  } ],
  "goal" : {
    "collection" : "str"
  }
}
```

### HTTP Request
`POST /ab-testing/get`
### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|id|true|integer (int32)||


### Responses for status codes
|200|403|
|----|----|
|[ABTestingReport](#abtestingreport)|[ErrorMessage](#errormessage)|


## List reports

```shell
curl --request GET \
  --url https://app.rakam.io//ab-testing/list \
  --header 'read_key: 5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
```

```javascript
var request = require("request");

var options = { method: 'GET',
  url: 'https://app.rakam.io//ab-testing/list',
  headers: { read_key: '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```java
OkHttpClient client = new OkHttpClient();

Request request = new Request.Builder()
  .url("https://app.rakam.io//ab-testing/list")
  .get()
  .addHeader("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")
  .build();

Response response = client.newCall(request).execute();
```

```csharp
var client = new RestClient("https://app.rakam.io//ab-testing/list");
var request = new RestRequest(Method.GET);
request.AddHeader("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8");
IRestResponse response = client.Execute(request);
```

```go
package main

import (
	"fmt"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://app.rakam.io//ab-testing/list"

	req, _ := http.NewRequest("GET", url, nil)

	req.Header.Add("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$request->setRequestUrl('https://app.rakam.io//ab-testing/list');
$request->setRequestMethod('GET');
$request->setHeaders(array(
  'read_key' => '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//ab-testing/list"

headers = {'read_key': '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'}

response = requests.request("GET", url, headers=headers)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.rakam.io//ab-testing/list")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Get.new(url)
request["read_key"] = '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'

response = http.request(request)
puts response.read_body
```

> The above command returns JSON structured like this:

```json
[ {
  "name" : "str",
  "variants" : [ {
    "name" : "str",
    "weight" : 1,
    "data" : "object"
  } ],
  "goal" : {
    "collection" : "str"
  }
} ]
```

### HTTP Request
`GET /ab-testing/list`
### Responses for status codes
|200|403|
|----|----|
|[ABTestingReport](#abtestingreport) array|[ErrorMessage](#errormessage)|


## Update report

```shell
curl --request POST \
  --url https://app.rakam.io//ab-testing/update \
  --header 'master_key: 5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' \
  --data '{"name":"str","variants":[{}],"goal":{}}'
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//ab-testing/update',
  headers: { master_key: '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' },
  body: { name: 'str', variants: [ {} ], goal: {} },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"name\":\"str\",\"variants\":[{}],\"goal\":{}}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//ab-testing/update")
  .post(body)
  .addHeader("master_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")
  .build();

Response response = client.newCall(request).execute();
```

```csharp
var client = new RestClient("https://app.rakam.io//ab-testing/update");
var request = new RestRequest(Method.POST);
request.AddHeader("master_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8");
request.AddParameter("undefined", "{\"name\":\"str\",\"variants\":[{}],\"goal\":{}}", ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
```

```go
package main

import (
	"fmt"
	"strings"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://app.rakam.io//ab-testing/update"

	payload := strings.NewReader("{\"name\":\"str\",\"variants\":[{}],\"goal\":{}}")

	req, _ := http.NewRequest("POST", url, payload)

	req.Header.Add("master_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->append('{"name":"str","variants":[{}],"goal":{}}');

$request->setRequestUrl('https://app.rakam.io//ab-testing/update');
$request->setRequestMethod('POST');
$request->setBody($body);

$request->setHeaders(array(
  'master_key' => '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//ab-testing/update"

payload = "{\"name\":\"str\",\"variants\":[{}],\"goal\":{}}"
headers = {'master_key': '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'}

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.rakam.io//ab-testing/update")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["master_key"] = '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
request.body = "{\"name\":\"str\",\"variants\":[{}],\"goal\":{}}"

response = http.request(request)
puts response.read_body
```

> The above command returns JSON structured like this:

```json
{
  "name" : "str",
  "variants" : [ {
    "name" : "str",
    "weight" : 1,
    "data" : "object"
  } ],
  "goal" : {
    "collection" : "str"
  }
}
```

### HTTP Request
`POST /ab-testing/update`
### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|name|true|string||
|variants|true|[Variant](#variant) array||
|goal|true|[Goal](#goal)||
|options|false|object||
|id|false|integer (int32)||
|collectionName|false|string||
|connectorField|false|string||


### Responses for status codes
|200|403|
|----|----|
|[ABTestingReport](#abtestingreport)|[ErrorMessage](#errormessage)|


# Event explorer


Event Explorer

## Perform simple query on event data

```shell
curl --request POST \
  --url https://app.rakam.io//event-explorer/analyze \
  --header 'read_key: 5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' \
  --data '{"startDate":"str","endDate":"str","collections":["str"]}'
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//event-explorer/analyze',
  headers: { read_key: '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' },
  body: { startDate: 'str', endDate: 'str', collections: [ 'str' ] },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"startDate\":\"str\",\"endDate\":\"str\",\"collections\":[\"str\"]}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//event-explorer/analyze")
  .post(body)
  .addHeader("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")
  .build();

Response response = client.newCall(request).execute();
```

```csharp
var client = new RestClient("https://app.rakam.io//event-explorer/analyze");
var request = new RestRequest(Method.POST);
request.AddHeader("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8");
request.AddParameter("undefined", "{\"startDate\":\"str\",\"endDate\":\"str\",\"collections\":[\"str\"]}", ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
```

```go
package main

import (
	"fmt"
	"strings"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://app.rakam.io//event-explorer/analyze"

	payload := strings.NewReader("{\"startDate\":\"str\",\"endDate\":\"str\",\"collections\":[\"str\"]}")

	req, _ := http.NewRequest("POST", url, payload)

	req.Header.Add("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->append('{"startDate":"str","endDate":"str","collections":["str"]}');

$request->setRequestUrl('https://app.rakam.io//event-explorer/analyze');
$request->setRequestMethod('POST');
$request->setBody($body);

$request->setHeaders(array(
  'read_key' => '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//event-explorer/analyze"

payload = "{\"startDate\":\"str\",\"endDate\":\"str\",\"collections\":[\"str\"]}"
headers = {'read_key': '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'}

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.rakam.io//event-explorer/analyze")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["read_key"] = '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
request.body = "{\"startDate\":\"str\",\"endDate\":\"str\",\"collections\":[\"str\"]}"

response = http.request(request)
puts response.read_body
```

> The above command returns JSON structured like this:

```json
{
  "metadata" : [ {
    "name" : "str",
    "type" : "STRING"
  } ],
  "result" : [ [ "object" ] ],
  "error" : {
    "message" : "str"
  },
  "properties" : {
    "prop" : { }
  }
}
```

### HTTP Request
`POST /event-explorer/analyze`
### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|measure|false|[Measure](#measure)||
|grouping|false|[Reference](#reference)||
|segment|false|[Reference](#reference)||
|filterExpression|false|string||
|startDate|true|string (date)||
|endDate|true|string (date)||
|timezone|false|[ZoneId](#zoneid)||
|collections|true|string array||


### Responses for status codes
|200|403|
|----|----|
|[QueryResult](#queryresult)|[ErrorMessage](#errormessage)|


## Event statistics

```shell
curl --request GET \
  --url https://app.rakam.io//event-explorer/extra_dimensions \
  --header 'read_key: 5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
```

```javascript
var request = require("request");

var options = { method: 'GET',
  url: 'https://app.rakam.io//event-explorer/extra_dimensions',
  headers: { read_key: '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```java
OkHttpClient client = new OkHttpClient();

Request request = new Request.Builder()
  .url("https://app.rakam.io//event-explorer/extra_dimensions")
  .get()
  .addHeader("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")
  .build();

Response response = client.newCall(request).execute();
```

```csharp
var client = new RestClient("https://app.rakam.io//event-explorer/extra_dimensions");
var request = new RestRequest(Method.GET);
request.AddHeader("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8");
IRestResponse response = client.Execute(request);
```

```go
package main

import (
	"fmt"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://app.rakam.io//event-explorer/extra_dimensions"

	req, _ := http.NewRequest("GET", url, nil)

	req.Header.Add("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$request->setRequestUrl('https://app.rakam.io//event-explorer/extra_dimensions');
$request->setRequestMethod('GET');
$request->setHeaders(array(
  'read_key' => '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//event-explorer/extra_dimensions"

headers = {'read_key': '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'}

response = requests.request("GET", url, headers=headers)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.rakam.io//event-explorer/extra_dimensions")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Get.new(url)
request["read_key"] = '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'

response = http.request(request)
puts response.read_body
```

> The above command returns JSON structured like this:

```json
{
  "prop" : { }
}
```

### HTTP Request
`GET /event-explorer/extra_dimensions`
### Responses for status codes
|200|403|
|----|----|
|object|[ErrorMessage](#errormessage)|


## Create Pre-computed table

```shell
curl --request POST \
  --url https://app.rakam.io//event-explorer/pre_calculate \
  --header 'master_key: 5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' \
  --data '{"collections":["str"],"dimensions":["str"],"aggregations":["COUNT"],"measures":["str"],"tableName":"str"}'
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//event-explorer/pre_calculate',
  headers: { master_key: '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' },
  body: 
   { collections: [ 'str' ],
     dimensions: [ 'str' ],
     aggregations: [ 'COUNT' ],
     measures: [ 'str' ],
     tableName: 'str' },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"collections\":[\"str\"],\"dimensions\":[\"str\"],\"aggregations\":[\"COUNT\"],\"measures\":[\"str\"],\"tableName\":\"str\"}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//event-explorer/pre_calculate")
  .post(body)
  .addHeader("master_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")
  .build();

Response response = client.newCall(request).execute();
```

```csharp
var client = new RestClient("https://app.rakam.io//event-explorer/pre_calculate");
var request = new RestRequest(Method.POST);
request.AddHeader("master_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8");
request.AddParameter("undefined", "{\"collections\":[\"str\"],\"dimensions\":[\"str\"],\"aggregations\":[\"COUNT\"],\"measures\":[\"str\"],\"tableName\":\"str\"}", ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
```

```go
package main

import (
	"fmt"
	"strings"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://app.rakam.io//event-explorer/pre_calculate"

	payload := strings.NewReader("{\"collections\":[\"str\"],\"dimensions\":[\"str\"],\"aggregations\":[\"COUNT\"],\"measures\":[\"str\"],\"tableName\":\"str\"}")

	req, _ := http.NewRequest("POST", url, payload)

	req.Header.Add("master_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->append('{"collections":["str"],"dimensions":["str"],"aggregations":["COUNT"],"measures":["str"],"tableName":"str"}');

$request->setRequestUrl('https://app.rakam.io//event-explorer/pre_calculate');
$request->setRequestMethod('POST');
$request->setBody($body);

$request->setHeaders(array(
  'master_key' => '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//event-explorer/pre_calculate"

payload = "{\"collections\":[\"str\"],\"dimensions\":[\"str\"],\"aggregations\":[\"COUNT\"],\"measures\":[\"str\"],\"tableName\":\"str\"}"
headers = {'master_key': '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'}

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.rakam.io//event-explorer/pre_calculate")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["master_key"] = '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
request.body = "{\"collections\":[\"str\"],\"dimensions\":[\"str\"],\"aggregations\":[\"COUNT\"],\"measures\":[\"str\"],\"tableName\":\"str\"}"

response = http.request(request)
puts response.read_body
```

> The above command returns JSON structured like this:

```json
{
  "name" : "str",
  "tableName" : "str"
}
```

### HTTP Request
`POST /event-explorer/pre_calculate`
### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|collections|true|string array||
|dimensions|true|string array||
|aggregations|true|enum (COUNT, COUNT_UNIQUE, SUM, MINIMUM, MAXIMUM, AVERAGE, APPROXIMATE_UNIQUE) array||
|measures|true|string array||
|tableName|true|string||


### Responses for status codes
|200|403|
|----|----|
|[PrecalculatedTable](#precalculatedtable)|[ErrorMessage](#errormessage)|


## Event statistics

```shell
curl --request POST \
  --url https://app.rakam.io//event-explorer/statistics \
  --header 'read_key: 5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' \
  --data '{"startDate":"str","endDate":"str"}'
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//event-explorer/statistics',
  headers: { read_key: '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' },
  body: { startDate: 'str', endDate: 'str' },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"startDate\":\"str\",\"endDate\":\"str\"}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//event-explorer/statistics")
  .post(body)
  .addHeader("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")
  .build();

Response response = client.newCall(request).execute();
```

```csharp
var client = new RestClient("https://app.rakam.io//event-explorer/statistics");
var request = new RestRequest(Method.POST);
request.AddHeader("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8");
request.AddParameter("undefined", "{\"startDate\":\"str\",\"endDate\":\"str\"}", ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
```

```go
package main

import (
	"fmt"
	"strings"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://app.rakam.io//event-explorer/statistics"

	payload := strings.NewReader("{\"startDate\":\"str\",\"endDate\":\"str\"}")

	req, _ := http.NewRequest("POST", url, payload)

	req.Header.Add("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->append('{"startDate":"str","endDate":"str"}');

$request->setRequestUrl('https://app.rakam.io//event-explorer/statistics');
$request->setRequestMethod('POST');
$request->setBody($body);

$request->setHeaders(array(
  'read_key' => '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//event-explorer/statistics"

payload = "{\"startDate\":\"str\",\"endDate\":\"str\"}"
headers = {'read_key': '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'}

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.rakam.io//event-explorer/statistics")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["read_key"] = '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
request.body = "{\"startDate\":\"str\",\"endDate\":\"str\"}"

response = http.request(request)
puts response.read_body
```

> The above command returns JSON structured like this:

```json
{
  "metadata" : [ {
    "name" : "str",
    "type" : "STRING"
  } ],
  "result" : [ [ "object" ] ],
  "error" : {
    "message" : "str"
  },
  "properties" : {
    "prop" : { }
  }
}
```

### HTTP Request
`POST /event-explorer/statistics`
### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|collections|false|string array||
|dimension|false|string||
|startDate|true|string (date)||
|endDate|true|string (date)||
|timezone|false|[ZoneId](#zoneid)||


### Responses for status codes
|200|403|
|----|----|
|[QueryResult](#queryresult)|[ErrorMessage](#errormessage)|


# Funnel


Funnel Analyzer

## Execute query

```shell
curl --request POST \
  --url https://app.rakam.io//funnel/analyze \
  --header 'read_key: 5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' \
  --data '{"steps":[{}],"startDate":"str","endDate":"str"}'
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//funnel/analyze',
  headers: { read_key: '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' },
  body: { steps: [ {} ], startDate: 'str', endDate: 'str' },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"steps\":[{}],\"startDate\":\"str\",\"endDate\":\"str\"}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//funnel/analyze")
  .post(body)
  .addHeader("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")
  .build();

Response response = client.newCall(request).execute();
```

```csharp
var client = new RestClient("https://app.rakam.io//funnel/analyze");
var request = new RestRequest(Method.POST);
request.AddHeader("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8");
request.AddParameter("undefined", "{\"steps\":[{}],\"startDate\":\"str\",\"endDate\":\"str\"}", ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
```

```go
package main

import (
	"fmt"
	"strings"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://app.rakam.io//funnel/analyze"

	payload := strings.NewReader("{\"steps\":[{}],\"startDate\":\"str\",\"endDate\":\"str\"}")

	req, _ := http.NewRequest("POST", url, payload)

	req.Header.Add("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->append('{"steps":[{}],"startDate":"str","endDate":"str"}');

$request->setRequestUrl('https://app.rakam.io//funnel/analyze');
$request->setRequestMethod('POST');
$request->setBody($body);

$request->setHeaders(array(
  'read_key' => '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//funnel/analyze"

payload = "{\"steps\":[{}],\"startDate\":\"str\",\"endDate\":\"str\"}"
headers = {'read_key': '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'}

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.rakam.io//funnel/analyze")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["read_key"] = '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
request.body = "{\"steps\":[{}],\"startDate\":\"str\",\"endDate\":\"str\"}"

response = http.request(request)
puts response.read_body
```

> The above command returns JSON structured like this:

```json
{
  "metadata" : [ {
    "name" : "str",
    "type" : "STRING"
  } ],
  "result" : [ [ "object" ] ],
  "error" : {
    "message" : "str"
  },
  "properties" : {
    "prop" : { }
  }
}
```

### HTTP Request
`POST /funnel/analyze`
### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|steps|true|[FunnelStep](#funnelstep) array||
|dimension|false|string||
|startDate|true|string (date)||
|window|false|[FunnelWindow](#funnelwindow)||
|endDate|true|string (date)||
|connectors|false|string array||
|strictOrdering|false|boolean||
|approximate|false|boolean||
|funnelType|false|enum (NORMAL, APPROXIMATE, ORDERED)||
|timezone|false|string||


### Responses for status codes
|200|403|
|----|----|
|[QueryResult](#queryresult)|[ErrorMessage](#errormessage)|


# Retention


Retention Analyzer module

## Execute query

```shell
curl --request POST \
  --url https://app.rakam.io//retention/analyze \
  --header 'read_key: 5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' \
  --data '{"first_action":{},"returning_action":{},"dimension":"str","date_unit":"DAY","startDate":"str","endDate":"str"}'
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//retention/analyze',
  headers: { read_key: '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' },
  body: 
   { first_action: {},
     returning_action: {},
     dimension: 'str',
     date_unit: 'DAY',
     startDate: 'str',
     endDate: 'str' },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"first_action\":{},\"returning_action\":{},\"dimension\":\"str\",\"date_unit\":\"DAY\",\"startDate\":\"str\",\"endDate\":\"str\"}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//retention/analyze")
  .post(body)
  .addHeader("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")
  .build();

Response response = client.newCall(request).execute();
```

```csharp
var client = new RestClient("https://app.rakam.io//retention/analyze");
var request = new RestRequest(Method.POST);
request.AddHeader("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8");
request.AddParameter("undefined", "{\"first_action\":{},\"returning_action\":{},\"dimension\":\"str\",\"date_unit\":\"DAY\",\"startDate\":\"str\",\"endDate\":\"str\"}", ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
```

```go
package main

import (
	"fmt"
	"strings"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://app.rakam.io//retention/analyze"

	payload := strings.NewReader("{\"first_action\":{},\"returning_action\":{},\"dimension\":\"str\",\"date_unit\":\"DAY\",\"startDate\":\"str\",\"endDate\":\"str\"}")

	req, _ := http.NewRequest("POST", url, payload)

	req.Header.Add("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->append('{"first_action":{},"returning_action":{},"dimension":"str","date_unit":"DAY","startDate":"str","endDate":"str"}');

$request->setRequestUrl('https://app.rakam.io//retention/analyze');
$request->setRequestMethod('POST');
$request->setBody($body);

$request->setHeaders(array(
  'read_key' => '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//retention/analyze"

payload = "{\"first_action\":{},\"returning_action\":{},\"dimension\":\"str\",\"date_unit\":\"DAY\",\"startDate\":\"str\",\"endDate\":\"str\"}"
headers = {'read_key': '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'}

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.rakam.io//retention/analyze")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["read_key"] = '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
request.body = "{\"first_action\":{},\"returning_action\":{},\"dimension\":\"str\",\"date_unit\":\"DAY\",\"startDate\":\"str\",\"endDate\":\"str\"}"

response = http.request(request)
puts response.read_body
```

> The above command returns JSON structured like this:

```json
{
  "metadata" : [ {
    "name" : "str",
    "type" : "STRING"
  } ],
  "result" : [ [ "object" ] ],
  "error" : {
    "message" : "str"
  },
  "properties" : {
    "prop" : { }
  }
}
```

### HTTP Request
`POST /retention/analyze`
### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|first_action|true|[RetentionAction](#retentionaction)||
|returning_action|true|[RetentionAction](#retentionaction)||
|dimension|true|string||
|date_unit|true|enum (DAY, WEEK, MONTH)||
|period|false|integer (int32)||
|startDate|true|string (date)||
|timezone|false|string||
|approximate|false|boolean||
|endDate|true|string (date)||


### Responses for status codes
|200|403|
|----|----|
|[QueryResult](#queryresult)|[ErrorMessage](#errormessage)|


# Event stream


Event Stream Module

# User


User

## Batch operation on a single user properties

```shell
curl --request POST \
  --url https://app.rakam.io//user/batch \
  --header 'write_key: 5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' \
  --data '{"id":{},"api":{},"data":[{}]}'
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//user/batch',
  headers: { write_key: '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' },
  body: { id: {}, api: {}, data: [ {} ] },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"id\":{},\"api\":{},\"data\":[{}]}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//user/batch")
  .post(body)
  .addHeader("write_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")
  .build();

Response response = client.newCall(request).execute();
```

```csharp
var client = new RestClient("https://app.rakam.io//user/batch");
var request = new RestRequest(Method.POST);
request.AddHeader("write_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8");
request.AddParameter("undefined", "{\"id\":{},\"api\":{},\"data\":[{}]}", ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
```

```go
package main

import (
	"fmt"
	"strings"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://app.rakam.io//user/batch"

	payload := strings.NewReader("{\"id\":{},\"api\":{},\"data\":[{}]}")

	req, _ := http.NewRequest("POST", url, payload)

	req.Header.Add("write_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->append('{"id":{},"api":{},"data":[{}]}');

$request->setRequestUrl('https://app.rakam.io//user/batch');
$request->setRequestMethod('POST');
$request->setBody($body);

$request->setHeaders(array(
  'write_key' => '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//user/batch"

payload = "{\"id\":{},\"api\":{},\"data\":[{}]}"
headers = {'write_key': '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'}

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.rakam.io//user/batch")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["write_key"] = '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
request.body = "{\"id\":{},\"api\":{},\"data\":[{}]}"

response = http.request(request)
puts response.read_body
```

> The above command returns JSON structured like this:

```json
1
```

### HTTP Request
`POST /user/batch`
### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|id|true|object||
|api|true|[UserContext](#usercontext)||
|data|true|[SingleUserBatchOperations](#singleuserbatchoperations) array||


### Responses for status codes
|200|404|403|
|----|----|----|
|integer (int32)|[ErrorMessage](#errormessage)|[ErrorMessage](#errormessage)|


## Create multiple new users

```shell
curl --request POST \
  --url https://app.rakam.io//user/batch/create \
  --header 'write_key: 5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' \
  --data '{"users":[null]}'
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//user/batch/create',
  headers: { write_key: '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' },
  body: { users: [ null ] },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"users\":[null]}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//user/batch/create")
  .post(body)
  .addHeader("write_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")
  .build();

Response response = client.newCall(request).execute();
```

```csharp
var client = new RestClient("https://app.rakam.io//user/batch/create");
var request = new RestRequest(Method.POST);
request.AddHeader("write_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8");
request.AddParameter("undefined", "{\"users\":[null]}", ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
```

```go
package main

import (
	"fmt"
	"strings"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://app.rakam.io//user/batch/create"

	payload := strings.NewReader("{\"users\":[null]}")

	req, _ := http.NewRequest("POST", url, payload)

	req.Header.Add("write_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->append('{"users":[null]}');

$request->setRequestUrl('https://app.rakam.io//user/batch/create');
$request->setRequestMethod('POST');
$request->setBody($body);

$request->setHeaders(array(
  'write_key' => '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//user/batch/create"

payload = "{\"users\":[null]}"
headers = {'write_key': '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'}

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.rakam.io//user/batch/create")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["write_key"] = '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
request.body = "{\"users\":[null]}"

response = http.request(request)
puts response.read_body
```

> The above command returns JSON structured like this:

```json
[ "object" ]
```

### HTTP Request
`POST /user/batch/create`
### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|users|true|[User](#user) array||


### Responses for status codes
|200|403|
|----|----|
|object array|[ErrorMessage](#errormessage)|



Returns user ids. User id may be string or numeric.

## Batch operations on user properties

```shell
curl --request POST \
  --url https://app.rakam.io//user/batch_operations \
  --header 'master_key: 5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' \
  --data '{"api":{},"data":[{}]}'
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//user/batch_operations',
  headers: { master_key: '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' },
  body: { api: {}, data: [ {} ] },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"api\":{},\"data\":[{}]}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//user/batch_operations")
  .post(body)
  .addHeader("master_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")
  .build();

Response response = client.newCall(request).execute();
```

```csharp
var client = new RestClient("https://app.rakam.io//user/batch_operations");
var request = new RestRequest(Method.POST);
request.AddHeader("master_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8");
request.AddParameter("undefined", "{\"api\":{},\"data\":[{}]}", ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
```

```go
package main

import (
	"fmt"
	"strings"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://app.rakam.io//user/batch_operations"

	payload := strings.NewReader("{\"api\":{},\"data\":[{}]}")

	req, _ := http.NewRequest("POST", url, payload)

	req.Header.Add("master_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->append('{"api":{},"data":[{}]}');

$request->setRequestUrl('https://app.rakam.io//user/batch_operations');
$request->setRequestMethod('POST');
$request->setBody($body);

$request->setHeaders(array(
  'master_key' => '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//user/batch_operations"

payload = "{\"api\":{},\"data\":[{}]}"
headers = {'master_key': '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'}

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.rakam.io//user/batch_operations")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["master_key"] = '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
request.body = "{\"api\":{},\"data\":[{}]}"

response = http.request(request)
puts response.read_body
```

> The above command returns JSON structured like this:

```json
1
```

### HTTP Request
`POST /user/batch_operations`
### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|api|true|[UserContext](#usercontext)||
|data|true|[BatchUserOperations](#batchuseroperations) array||


### Responses for status codes
|200|404|403|
|----|----|----|
|integer (int32)|[ErrorMessage](#errormessage)|[ErrorMessage](#errormessage)|


## Create new user

```shell
curl --request POST \
  --url https://app.rakam.io//user/create \
  --data '{"id":{},"api":{},"properties":{}}'
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//user/create',
  body: { id: {}, api: {}, properties: {} },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"id\":{},\"api\":{},\"properties\":{}}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//user/create")
  .post(body)
  .build();

Response response = client.newCall(request).execute();
```

```csharp
var client = new RestClient("https://app.rakam.io//user/create");
var request = new RestRequest(Method.POST);
request.AddParameter("undefined", "{\"id\":{},\"api\":{},\"properties\":{}}", ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
```

```go
package main

import (
	"fmt"
	"strings"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://app.rakam.io//user/create"

	payload := strings.NewReader("{\"id\":{},\"api\":{},\"properties\":{}}")

	req, _ := http.NewRequest("POST", url, payload)

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->append('{"id":{},"api":{},"properties":{}}');

$request->setRequestUrl('https://app.rakam.io//user/create');
$request->setRequestMethod('POST');
$request->setBody($body);

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//user/create"

payload = "{\"id\":{},\"api\":{},\"properties\":{}}"
response = requests.request("POST", url, data=payload)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.rakam.io//user/create")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request.body = "{\"id\":{},\"api\":{},\"properties\":{}}"

response = http.request(request)
puts response.read_body
```

> The above command returns JSON structured like this:

```json
1
```

### HTTP Request
`POST /user/create`
### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|id|true|object||
|api|true|[UserContext](#usercontext)||
|properties|true|object||


### Responses for status codes
|200|
|----|
|integer (int32)|


## Get events of the user

```shell
curl --request POST \
  --url https://app.rakam.io//user/create_segment \
  --header 'master_key: 5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' \
  --data '{"name":"str","table_name":"str","cache_eviction":"str"}'
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//user/create_segment',
  headers: { master_key: '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' },
  body: { name: 'str', table_name: 'str', cache_eviction: 'str' },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"name\":\"str\",\"table_name\":\"str\",\"cache_eviction\":\"str\"}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//user/create_segment")
  .post(body)
  .addHeader("master_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")
  .build();

Response response = client.newCall(request).execute();
```

```csharp
var client = new RestClient("https://app.rakam.io//user/create_segment");
var request = new RestRequest(Method.POST);
request.AddHeader("master_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8");
request.AddParameter("undefined", "{\"name\":\"str\",\"table_name\":\"str\",\"cache_eviction\":\"str\"}", ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
```

```go
package main

import (
	"fmt"
	"strings"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://app.rakam.io//user/create_segment"

	payload := strings.NewReader("{\"name\":\"str\",\"table_name\":\"str\",\"cache_eviction\":\"str\"}")

	req, _ := http.NewRequest("POST", url, payload)

	req.Header.Add("master_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->append('{"name":"str","table_name":"str","cache_eviction":"str"}');

$request->setRequestUrl('https://app.rakam.io//user/create_segment');
$request->setRequestMethod('POST');
$request->setBody($body);

$request->setHeaders(array(
  'master_key' => '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//user/create_segment"

payload = "{\"name\":\"str\",\"table_name\":\"str\",\"cache_eviction\":\"str\"}"
headers = {'master_key': '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'}

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.rakam.io//user/create_segment")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["master_key"] = '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
request.body = "{\"name\":\"str\",\"table_name\":\"str\",\"cache_eviction\":\"str\"}"

response = http.request(request)
puts response.read_body
```

> The above command returns JSON structured like this:

```json
{
  "message" : "str"
}
```

### HTTP Request
`POST /user/create_segment`
### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|name|true|string||
|table_name|true|string||
|filter_expression|false|string||
|event_filters|false|[EventFilter](#eventfilter) array||
|cache_eviction|true|string||


### Responses for status codes
|200|404|403|
|----|----|----|
|[SuccessMessage](#successmessage)|[ErrorMessage](#errormessage)|[ErrorMessage](#errormessage)|


## Get user

```shell
curl --request POST \
  --url https://app.rakam.io//user/get \
  --header 'read_key: 5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' \
  --data '{"user":{}}'
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//user/get',
  headers: { read_key: '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' },
  body: { user: {} },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"user\":{}}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//user/get")
  .post(body)
  .addHeader("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")
  .build();

Response response = client.newCall(request).execute();
```

```csharp
var client = new RestClient("https://app.rakam.io//user/get");
var request = new RestRequest(Method.POST);
request.AddHeader("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8");
request.AddParameter("undefined", "{\"user\":{}}", ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
```

```go
package main

import (
	"fmt"
	"strings"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://app.rakam.io//user/get"

	payload := strings.NewReader("{\"user\":{}}")

	req, _ := http.NewRequest("POST", url, payload)

	req.Header.Add("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->append('{"user":{}}');

$request->setRequestUrl('https://app.rakam.io//user/get');
$request->setRequestMethod('POST');
$request->setBody($body);

$request->setHeaders(array(
  'read_key' => '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//user/get"

payload = "{\"user\":{}}"
headers = {'read_key': '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'}

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.rakam.io//user/get")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["read_key"] = '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
request.body = "{\"user\":{}}"

response = http.request(request)
puts response.read_body
```

> The above command returns JSON structured like this:

```json
{
  "id" : "object",
  "api" : { },
  "properties" : "object"
}
```

### HTTP Request
`POST /user/get`
### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|user|true|object||


### Responses for status codes
|200|404|403|
|----|----|----|
|[User](#user)|[ErrorMessage](#errormessage)|[ErrorMessage](#errormessage)|


## Get events of the user

```shell
curl --request POST \
  --url https://app.rakam.io//user/get_events \
  --header 'read_key: 5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' \
  --data '{"user":"str"}'
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//user/get_events',
  headers: { read_key: '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' },
  body: { user: 'str' },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"user\":\"str\"}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//user/get_events")
  .post(body)
  .addHeader("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")
  .build();

Response response = client.newCall(request).execute();
```

```csharp
var client = new RestClient("https://app.rakam.io//user/get_events");
var request = new RestRequest(Method.POST);
request.AddHeader("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8");
request.AddParameter("undefined", "{\"user\":\"str\"}", ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
```

```go
package main

import (
	"fmt"
	"strings"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://app.rakam.io//user/get_events"

	payload := strings.NewReader("{\"user\":\"str\"}")

	req, _ := http.NewRequest("POST", url, payload)

	req.Header.Add("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->append('{"user":"str"}');

$request->setRequestUrl('https://app.rakam.io//user/get_events');
$request->setRequestMethod('POST');
$request->setBody($body);

$request->setHeaders(array(
  'read_key' => '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//user/get_events"

payload = "{\"user\":\"str\"}"
headers = {'read_key': '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'}

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.rakam.io//user/get_events")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["read_key"] = '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
request.body = "{\"user\":\"str\"}"

response = http.request(request)
puts response.read_body
```

> The above command returns JSON structured like this:

```json
[ { } ]
```

### HTTP Request
`POST /user/get_events`
### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|user|true|string||
|limit|false|integer (int32)||
|properties|false|string array||
|offset|false|string (date-time)||


### Responses for status codes
|200|404|403|
|----|----|----|
|[CollectionEvent](#collectionevent) array|[ErrorMessage](#errormessage)|[ErrorMessage](#errormessage)|


## Set user property

```shell
curl --request POST \
  --url https://app.rakam.io//user/increment_property \
  --header 'master_key: 5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' \
  --data '{"api":{},"id":"str","property":"str","value":7}'
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//user/increment_property',
  headers: { master_key: '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' },
  body: { api: {}, id: 'str', property: 'str', value: 7 },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"api\":{},\"id\":\"str\",\"property\":\"str\",\"value\":7}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//user/increment_property")
  .post(body)
  .addHeader("master_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")
  .build();

Response response = client.newCall(request).execute();
```

```csharp
var client = new RestClient("https://app.rakam.io//user/increment_property");
var request = new RestRequest(Method.POST);
request.AddHeader("master_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8");
request.AddParameter("undefined", "{\"api\":{},\"id\":\"str\",\"property\":\"str\",\"value\":7}", ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
```

```go
package main

import (
	"fmt"
	"strings"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://app.rakam.io//user/increment_property"

	payload := strings.NewReader("{\"api\":{},\"id\":\"str\",\"property\":\"str\",\"value\":7}")

	req, _ := http.NewRequest("POST", url, payload)

	req.Header.Add("master_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->append('{"api":{},"id":"str","property":"str","value":7}');

$request->setRequestUrl('https://app.rakam.io//user/increment_property');
$request->setRequestMethod('POST');
$request->setBody($body);

$request->setHeaders(array(
  'master_key' => '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//user/increment_property"

payload = "{\"api\":{},\"id\":\"str\",\"property\":\"str\",\"value\":7}"
headers = {'master_key': '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'}

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.rakam.io//user/increment_property")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["master_key"] = '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
request.body = "{\"api\":{},\"id\":\"str\",\"property\":\"str\",\"value\":7}"

response = http.request(request)
puts response.read_body
```

> The above command returns JSON structured like this:

```json
{
  "message" : "str"
}
```

### HTTP Request
`POST /user/increment_property`
### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|api|true|[UserContext](#usercontext)||
|id|true|string||
|property|true|string||
|value|true|number (double)||


### Responses for status codes
|200|404|403|
|----|----|----|
|[SuccessMessage](#successmessage)|[ErrorMessage](#errormessage)|[ErrorMessage](#errormessage)|


## Get user storage metadata

```shell
curl --request GET \
  --url https://app.rakam.io//user/metadata \
  --header 'read_key: 5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
```

```javascript
var request = require("request");

var options = { method: 'GET',
  url: 'https://app.rakam.io//user/metadata',
  headers: { read_key: '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```java
OkHttpClient client = new OkHttpClient();

Request request = new Request.Builder()
  .url("https://app.rakam.io//user/metadata")
  .get()
  .addHeader("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")
  .build();

Response response = client.newCall(request).execute();
```

```csharp
var client = new RestClient("https://app.rakam.io//user/metadata");
var request = new RestRequest(Method.GET);
request.AddHeader("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8");
IRestResponse response = client.Execute(request);
```

```go
package main

import (
	"fmt"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://app.rakam.io//user/metadata"

	req, _ := http.NewRequest("GET", url, nil)

	req.Header.Add("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$request->setRequestUrl('https://app.rakam.io//user/metadata');
$request->setRequestMethod('GET');
$request->setHeaders(array(
  'read_key' => '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//user/metadata"

headers = {'read_key': '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'}

response = requests.request("GET", url, headers=headers)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.rakam.io//user/metadata")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Get.new(url)
request["read_key"] = '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'

response = http.request(request)
puts response.read_body
```

> The above command returns JSON structured like this:

```json
{ }
```

### HTTP Request
`GET /user/metadata`
### Responses for status codes
|200|403|
|----|----|
|[MetadataResponse](#metadataresponse)|[ErrorMessage](#errormessage)|


## Search users

```shell
curl --request POST \
  --url https://app.rakam.io//user/search \
  --header 'read_key: 5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' \
  --data '{"columns":["str"],"filter":"str","event_filters":[{}],"sorting":{},"offset":"str","limit":4}'
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//user/search',
  headers: { read_key: '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' },
  body: 
   { columns: [ 'str' ],
     filter: 'str',
     event_filters: [ {} ],
     sorting: {},
     offset: 'str',
     limit: 4 },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"columns\":[\"str\"],\"filter\":\"str\",\"event_filters\":[{}],\"sorting\":{},\"offset\":\"str\",\"limit\":4}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//user/search")
  .post(body)
  .addHeader("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")
  .build();

Response response = client.newCall(request).execute();
```

```csharp
var client = new RestClient("https://app.rakam.io//user/search");
var request = new RestRequest(Method.POST);
request.AddHeader("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8");
request.AddParameter("undefined", "{\"columns\":[\"str\"],\"filter\":\"str\",\"event_filters\":[{}],\"sorting\":{},\"offset\":\"str\",\"limit\":4}", ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
```

```go
package main

import (
	"fmt"
	"strings"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://app.rakam.io//user/search"

	payload := strings.NewReader("{\"columns\":[\"str\"],\"filter\":\"str\",\"event_filters\":[{}],\"sorting\":{},\"offset\":\"str\",\"limit\":4}")

	req, _ := http.NewRequest("POST", url, payload)

	req.Header.Add("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->append('{"columns":["str"],"filter":"str","event_filters":[{}],"sorting":{},"offset":"str","limit":4}');

$request->setRequestUrl('https://app.rakam.io//user/search');
$request->setRequestMethod('POST');
$request->setBody($body);

$request->setHeaders(array(
  'read_key' => '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//user/search"

payload = "{\"columns\":[\"str\"],\"filter\":\"str\",\"event_filters\":[{}],\"sorting\":{},\"offset\":\"str\",\"limit\":4}"
headers = {'read_key': '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'}

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.rakam.io//user/search")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["read_key"] = '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
request.body = "{\"columns\":[\"str\"],\"filter\":\"str\",\"event_filters\":[{}],\"sorting\":{},\"offset\":\"str\",\"limit\":4}"

response = http.request(request)
puts response.read_body
```

> The above command returns JSON structured like this:

```json
{
  "metadata" : [ {
    "name" : "str",
    "type" : "STRING"
  } ],
  "result" : [ [ "object" ] ],
  "error" : {
    "message" : "str"
  },
  "properties" : {
    "prop" : { }
  }
}
```

### HTTP Request
`POST /user/search`
### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|columns|false|string array||
|filter|false|string||
|event_filters|false|[EventFilter](#eventfilter) array||
|sorting|false|[Sorting](#sorting)||
|offset|false|string||
|limit|false|integer (int32)||


### Responses for status codes
|200|403|
|----|----|
|[QueryResult](#queryresult)|[ErrorMessage](#errormessage)|


## Set user properties

```shell
curl --request POST \
  --url https://app.rakam.io//user/set_properties \
  --data '{"id":{},"api":{},"properties":{}}'
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//user/set_properties',
  body: { id: {}, api: {}, properties: {} },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"id\":{},\"api\":{},\"properties\":{}}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//user/set_properties")
  .post(body)
  .build();

Response response = client.newCall(request).execute();
```

```csharp
var client = new RestClient("https://app.rakam.io//user/set_properties");
var request = new RestRequest(Method.POST);
request.AddParameter("undefined", "{\"id\":{},\"api\":{},\"properties\":{}}", ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
```

```go
package main

import (
	"fmt"
	"strings"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://app.rakam.io//user/set_properties"

	payload := strings.NewReader("{\"id\":{},\"api\":{},\"properties\":{}}")

	req, _ := http.NewRequest("POST", url, payload)

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->append('{"id":{},"api":{},"properties":{}}');

$request->setRequestUrl('https://app.rakam.io//user/set_properties');
$request->setRequestMethod('POST');
$request->setBody($body);

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//user/set_properties"

payload = "{\"id\":{},\"api\":{},\"properties\":{}}"
response = requests.request("POST", url, data=payload)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.rakam.io//user/set_properties")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request.body = "{\"id\":{},\"api\":{},\"properties\":{}}"

response = http.request(request)
puts response.read_body
```

> The above command returns JSON structured like this:

```json
1
```

### HTTP Request
`POST /user/set_properties`
### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|id|true|object||
|api|true|[UserContext](#usercontext)||
|properties|true|object||


### Responses for status codes
|200|404|
|----|----|
|integer (int32)|[ErrorMessage](#errormessage)|


## Set user properties once

```shell
curl --request POST \
  --url https://app.rakam.io//user/set_properties_once \
  --data '{"id":{},"api":{},"properties":{}}'
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//user/set_properties_once',
  body: { id: {}, api: {}, properties: {} },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"id\":{},\"api\":{},\"properties\":{}}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//user/set_properties_once")
  .post(body)
  .build();

Response response = client.newCall(request).execute();
```

```csharp
var client = new RestClient("https://app.rakam.io//user/set_properties_once");
var request = new RestRequest(Method.POST);
request.AddParameter("undefined", "{\"id\":{},\"api\":{},\"properties\":{}}", ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
```

```go
package main

import (
	"fmt"
	"strings"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://app.rakam.io//user/set_properties_once"

	payload := strings.NewReader("{\"id\":{},\"api\":{},\"properties\":{}}")

	req, _ := http.NewRequest("POST", url, payload)

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->append('{"id":{},"api":{},"properties":{}}');

$request->setRequestUrl('https://app.rakam.io//user/set_properties_once');
$request->setRequestMethod('POST');
$request->setBody($body);

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//user/set_properties_once"

payload = "{\"id\":{},\"api\":{},\"properties\":{}}"
response = requests.request("POST", url, data=payload)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.rakam.io//user/set_properties_once")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request.body = "{\"id\":{},\"api\":{},\"properties\":{}}"

response = http.request(request)
puts response.read_body
```

> The above command returns JSON structured like this:

```json
1
```

### HTTP Request
`POST /user/set_properties_once`
### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|id|true|object||
|api|true|[UserContext](#usercontext)||
|properties|true|object||


### Responses for status codes
|200|404|
|----|----|
|integer (int32)|[ErrorMessage](#errormessage)|


## Unset user property

```shell
curl --request POST \
  --url https://app.rakam.io//user/unset_properties \
  --data '{"api":{},"id":{},"properties":["str"]}'
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//user/unset_properties',
  body: { api: {}, id: {}, properties: [ 'str' ] },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"api\":{},\"id\":{},\"properties\":[\"str\"]}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//user/unset_properties")
  .post(body)
  .build();

Response response = client.newCall(request).execute();
```

```csharp
var client = new RestClient("https://app.rakam.io//user/unset_properties");
var request = new RestRequest(Method.POST);
request.AddParameter("undefined", "{\"api\":{},\"id\":{},\"properties\":[\"str\"]}", ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
```

```go
package main

import (
	"fmt"
	"strings"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://app.rakam.io//user/unset_properties"

	payload := strings.NewReader("{\"api\":{},\"id\":{},\"properties\":[\"str\"]}")

	req, _ := http.NewRequest("POST", url, payload)

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->append('{"api":{},"id":{},"properties":["str"]}');

$request->setRequestUrl('https://app.rakam.io//user/unset_properties');
$request->setRequestMethod('POST');
$request->setBody($body);

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//user/unset_properties"

payload = "{\"api\":{},\"id\":{},\"properties\":[\"str\"]}"
response = requests.request("POST", url, data=payload)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.rakam.io//user/unset_properties")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request.body = "{\"api\":{},\"id\":{},\"properties\":[\"str\"]}"

response = http.request(request)
puts response.read_body
```

> The above command returns JSON structured like this:

```json
{
  "message" : "str"
}
```

### HTTP Request
`POST /user/unset_properties`
### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|api|true|[UserContext](#usercontext)||
|id|true|object||
|properties|true|string array||


### Responses for status codes
|200|404|
|----|----|
|[SuccessMessage](#successmessage)|[ErrorMessage](#errormessage)|


# User action


User Action

# Recipe


Recipe

## Export recipe

```shell
curl --request GET \
  --url https://app.rakam.io//recipe/export \
  --header 'accept: str' \
  --header 'master_key: 5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
```

```javascript
var request = require("request");

var options = { method: 'GET',
  url: 'https://app.rakam.io//recipe/export',
  headers: 
   { master_key: '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8',
     accept: 'str' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```java
OkHttpClient client = new OkHttpClient();

Request request = new Request.Builder()
  .url("https://app.rakam.io//recipe/export")
  .get()
  .addHeader("accept", "str")
  .addHeader("master_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")
  .build();

Response response = client.newCall(request).execute();
```

```csharp
var client = new RestClient("https://app.rakam.io//recipe/export");
var request = new RestRequest(Method.GET);
request.AddHeader("master_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8");
request.AddHeader("accept", "str");
IRestResponse response = client.Execute(request);
```

```go
package main

import (
	"fmt"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://app.rakam.io//recipe/export"

	req, _ := http.NewRequest("GET", url, nil)

	req.Header.Add("accept", "str")
	req.Header.Add("master_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$request->setRequestUrl('https://app.rakam.io//recipe/export');
$request->setRequestMethod('GET');
$request->setHeaders(array(
  'master_key' => '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8',
  'accept' => 'str'
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//recipe/export"

headers = {
    'accept': "str",
    'master_key': "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8"
    }

response = requests.request("GET", url, headers=headers)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.rakam.io//recipe/export")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Get.new(url)
request["accept"] = 'str'
request["master_key"] = '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'

response = http.request(request)
puts response.read_body
```

> The above command returns JSON structured like this:

```json
{ }
```

### HTTP Request
`GET /recipe/export`
### Header Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|Accept|true|string||


### Responses for status codes
|200|403|
|----|----|
|[Recipe](#recipe)|[ErrorMessage](#errormessage)|


## Install recipe

```shell
curl --request POST \
  --url https://app.rakam.io//recipe/install \
  --header 'master_key: 5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//recipe/install',
  headers: { master_key: '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```java
OkHttpClient client = new OkHttpClient();

Request request = new Request.Builder()
  .url("https://app.rakam.io//recipe/install")
  .post(null)
  .addHeader("master_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")
  .build();

Response response = client.newCall(request).execute();
```

```csharp
var client = new RestClient("https://app.rakam.io//recipe/install");
var request = new RestRequest(Method.POST);
request.AddHeader("master_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8");
IRestResponse response = client.Execute(request);
```

```go
package main

import (
	"fmt"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://app.rakam.io//recipe/install"

	req, _ := http.NewRequest("POST", url, nil)

	req.Header.Add("master_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$request->setRequestUrl('https://app.rakam.io//recipe/install');
$request->setRequestMethod('POST');
$request->setHeaders(array(
  'master_key' => '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//recipe/install"

headers = {'master_key': '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'}

response = requests.request("POST", url, headers=headers)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.rakam.io//recipe/install")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["master_key"] = '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'

response = http.request(request)
puts response.read_body
```

> The above command returns JSON structured like this:

```json
{
  "message" : "str"
}
```

### HTTP Request
`POST /recipe/install`
### Responses for status codes
|200|403|
|----|----|
|[SuccessMessage](#successmessage)|[ErrorMessage](#errormessage)|


# Admin


System related actions

## List installed modules

```shell
curl --request GET \
  --url https://app.rakam.io//admin/configurations \
  --header 'master_key: 5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
```

```javascript
var request = require("request");

var options = { method: 'GET',
  url: 'https://app.rakam.io//admin/configurations',
  headers: { master_key: '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```java
OkHttpClient client = new OkHttpClient();

Request request = new Request.Builder()
  .url("https://app.rakam.io//admin/configurations")
  .get()
  .addHeader("master_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")
  .build();

Response response = client.newCall(request).execute();
```

```csharp
var client = new RestClient("https://app.rakam.io//admin/configurations");
var request = new RestRequest(Method.GET);
request.AddHeader("master_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8");
IRestResponse response = client.Execute(request);
```

```go
package main

import (
	"fmt"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://app.rakam.io//admin/configurations"

	req, _ := http.NewRequest("GET", url, nil)

	req.Header.Add("master_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$request->setRequestUrl('https://app.rakam.io//admin/configurations');
$request->setRequestMethod('GET');
$request->setHeaders(array(
  'master_key' => '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//admin/configurations"

headers = {'master_key': '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'}

response = requests.request("GET", url, headers=headers)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.rakam.io//admin/configurations")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Get.new(url)
request["master_key"] = '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'

response = http.request(request)
puts response.read_body
```

> The above command returns JSON structured like this:

```json
[ { } ]
```

### HTTP Request
`GET /admin/configurations`
### Responses for status codes
|200|403|
|----|----|
|[ModuleDescriptor](#moduledescriptor) array|[ErrorMessage](#errormessage)|


## List event mappers

```shell
curl --request GET \
  --url https://app.rakam.io//admin/event_mappers \
  --header 'master_key: 5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
```

```javascript
var request = require("request");

var options = { method: 'GET',
  url: 'https://app.rakam.io//admin/event_mappers',
  headers: { master_key: '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```java
OkHttpClient client = new OkHttpClient();

Request request = new Request.Builder()
  .url("https://app.rakam.io//admin/event_mappers")
  .get()
  .addHeader("master_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")
  .build();

Response response = client.newCall(request).execute();
```

```csharp
var client = new RestClient("https://app.rakam.io//admin/event_mappers");
var request = new RestRequest(Method.GET);
request.AddHeader("master_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8");
IRestResponse response = client.Execute(request);
```

```go
package main

import (
	"fmt"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://app.rakam.io//admin/event_mappers"

	req, _ := http.NewRequest("GET", url, nil)

	req.Header.Add("master_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$request->setRequestUrl('https://app.rakam.io//admin/event_mappers');
$request->setRequestMethod('GET');
$request->setHeaders(array(
  'master_key' => '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//admin/event_mappers"

headers = {'master_key': '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'}

response = requests.request("GET", url, headers=headers)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.rakam.io//admin/event_mappers")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Get.new(url)
request["master_key"] = '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'

response = http.request(request)
puts response.read_body
```

> The above command returns JSON structured like this:

```json
[ { } ]
```

### HTTP Request
`GET /admin/event_mappers`
### Responses for status codes
|200|403|
|----|----|
|[EventMapperDescription](#eventmapperdescription) array|[ErrorMessage](#errormessage)|


## Check lock key

```shell
curl --request POST \
  --url https://app.rakam.io//admin/lock_key \
  --header 'master_key: 5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' \
  --data '{"lock_key":"str"}'
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//admin/lock_key',
  headers: { master_key: '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' },
  body: { lock_key: 'str' },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"lock_key\":\"str\"}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//admin/lock_key")
  .post(body)
  .addHeader("master_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")
  .build();

Response response = client.newCall(request).execute();
```

```csharp
var client = new RestClient("https://app.rakam.io//admin/lock_key");
var request = new RestRequest(Method.POST);
request.AddHeader("master_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8");
request.AddParameter("undefined", "{\"lock_key\":\"str\"}", ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
```

```go
package main

import (
	"fmt"
	"strings"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://app.rakam.io//admin/lock_key"

	payload := strings.NewReader("{\"lock_key\":\"str\"}")

	req, _ := http.NewRequest("POST", url, payload)

	req.Header.Add("master_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->append('{"lock_key":"str"}');

$request->setRequestUrl('https://app.rakam.io//admin/lock_key');
$request->setRequestMethod('POST');
$request->setBody($body);

$request->setHeaders(array(
  'master_key' => '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//admin/lock_key"

payload = "{\"lock_key\":\"str\"}"
headers = {'master_key': '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'}

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.rakam.io//admin/lock_key")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["master_key"] = '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
request.body = "{\"lock_key\":\"str\"}"

response = http.request(request)
puts response.read_body
```

> The above command returns JSON structured like this:

```json
true
```

### HTTP Request
`POST /admin/lock_key`
### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|lock_key|false|string||


### Responses for status codes
|200|403|
|----|----|
|boolean|[ErrorMessage](#errormessage)|


## Get types

```shell
curl --request GET \
  --url https://app.rakam.io//admin/types \
  --header 'master_key: 5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
```

```javascript
var request = require("request");

var options = { method: 'GET',
  url: 'https://app.rakam.io//admin/types',
  headers: { master_key: '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```java
OkHttpClient client = new OkHttpClient();

Request request = new Request.Builder()
  .url("https://app.rakam.io//admin/types")
  .get()
  .addHeader("master_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")
  .build();

Response response = client.newCall(request).execute();
```

```csharp
var client = new RestClient("https://app.rakam.io//admin/types");
var request = new RestRequest(Method.GET);
request.AddHeader("master_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8");
IRestResponse response = client.Execute(request);
```

```go
package main

import (
	"fmt"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://app.rakam.io//admin/types"

	req, _ := http.NewRequest("GET", url, nil)

	req.Header.Add("master_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$request->setRequestUrl('https://app.rakam.io//admin/types');
$request->setRequestMethod('GET');
$request->setHeaders(array(
  'master_key' => '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//admin/types"

headers = {'master_key': '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'}

response = requests.request("GET", url, headers=headers)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.rakam.io//admin/types")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Get.new(url)
request["master_key"] = '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'

response = http.request(request)
puts response.read_body
```

> The above command returns JSON structured like this:

```json
{
  "prop" : { }
}
```

### HTTP Request
`GET /admin/types`
### Responses for status codes
|200|403|
|----|----|
|object|[ErrorMessage](#errormessage)|


## Create API Keys

```shell
curl --request POST \
  --url https://app.rakam.io//project/check-api-keys \
  --data '{"keys":[{}],"project":"str"}'
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//project/check-api-keys',
  body: { keys: [ {} ], project: 'str' },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"keys\":[{}],\"project\":\"str\"}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//project/check-api-keys")
  .post(body)
  .build();

Response response = client.newCall(request).execute();
```

```csharp
var client = new RestClient("https://app.rakam.io//project/check-api-keys");
var request = new RestRequest(Method.POST);
request.AddParameter("undefined", "{\"keys\":[{}],\"project\":\"str\"}", ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
```

```go
package main

import (
	"fmt"
	"strings"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://app.rakam.io//project/check-api-keys"

	payload := strings.NewReader("{\"keys\":[{}],\"project\":\"str\"}")

	req, _ := http.NewRequest("POST", url, payload)

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->append('{"keys":[{}],"project":"str"}');

$request->setRequestUrl('https://app.rakam.io//project/check-api-keys');
$request->setRequestMethod('POST');
$request->setBody($body);

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//project/check-api-keys"

payload = "{\"keys\":[{}],\"project\":\"str\"}"
response = requests.request("POST", url, data=payload)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.rakam.io//project/check-api-keys")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request.body = "{\"keys\":[{}],\"project\":\"str\"}"

response = http.request(request)
puts response.read_body
```

> The above command returns JSON structured like this:

```json
[ true ]
```

### HTTP Request
`POST /project/check-api-keys`
### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|keys|true|[ProjectApiKeys](#projectapikeys) array||
|project|true|string||


### Responses for status codes
|200|
|----|
|boolean array|


## Get collection names

```shell
curl --request POST \
  --url https://app.rakam.io//project/collection \
  --header 'read_key: 5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//project/collection',
  headers: { read_key: '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```java
OkHttpClient client = new OkHttpClient();

Request request = new Request.Builder()
  .url("https://app.rakam.io//project/collection")
  .post(null)
  .addHeader("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")
  .build();

Response response = client.newCall(request).execute();
```

```csharp
var client = new RestClient("https://app.rakam.io//project/collection");
var request = new RestRequest(Method.POST);
request.AddHeader("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8");
IRestResponse response = client.Execute(request);
```

```go
package main

import (
	"fmt"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://app.rakam.io//project/collection"

	req, _ := http.NewRequest("POST", url, nil)

	req.Header.Add("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$request->setRequestUrl('https://app.rakam.io//project/collection');
$request->setRequestMethod('POST');
$request->setHeaders(array(
  'read_key' => '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//project/collection"

headers = {'read_key': '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'}

response = requests.request("POST", url, headers=headers)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.rakam.io//project/collection")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["read_key"] = '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'

response = http.request(request)
puts response.read_body
```

> The above command returns JSON structured like this:

```json
[ "str" ]
```

### HTTP Request
`POST /project/collection`
### Responses for status codes
|200|403|
|----|----|
|string array|[ErrorMessage](#errormessage)|


## Create project

```shell
curl --request POST \
  --url https://app.rakam.io//project/create \
  --data '{"name":"str"}'
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//project/create',
  body: { name: 'str' },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"name\":\"str\"}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//project/create")
  .post(body)
  .build();

Response response = client.newCall(request).execute();
```

```csharp
var client = new RestClient("https://app.rakam.io//project/create");
var request = new RestRequest(Method.POST);
request.AddParameter("undefined", "{\"name\":\"str\"}", ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
```

```go
package main

import (
	"fmt"
	"strings"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://app.rakam.io//project/create"

	payload := strings.NewReader("{\"name\":\"str\"}")

	req, _ := http.NewRequest("POST", url, payload)

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->append('{"name":"str"}');

$request->setRequestUrl('https://app.rakam.io//project/create');
$request->setRequestMethod('POST');
$request->setBody($body);

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//project/create"

payload = "{\"name\":\"str\"}"
response = requests.request("POST", url, data=payload)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.rakam.io//project/create")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request.body = "{\"name\":\"str\"}"

response = http.request(request)
puts response.read_body
```

> The above command returns JSON structured like this:

```json
{ }
```

### HTTP Request
`POST /project/create`
### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|lock_key|false|string||
|name|true|string||


### Responses for status codes
|200|
|----|
|[ProjectApiKeys](#projectapikeys)|


## Create API Keys

```shell
curl --request POST \
  --url https://app.rakam.io//project/create-api-keys \
  --header 'master_key: 5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//project/create-api-keys',
  headers: { master_key: '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```java
OkHttpClient client = new OkHttpClient();

Request request = new Request.Builder()
  .url("https://app.rakam.io//project/create-api-keys")
  .post(null)
  .addHeader("master_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")
  .build();

Response response = client.newCall(request).execute();
```

```csharp
var client = new RestClient("https://app.rakam.io//project/create-api-keys");
var request = new RestRequest(Method.POST);
request.AddHeader("master_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8");
IRestResponse response = client.Execute(request);
```

```go
package main

import (
	"fmt"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://app.rakam.io//project/create-api-keys"

	req, _ := http.NewRequest("POST", url, nil)

	req.Header.Add("master_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$request->setRequestUrl('https://app.rakam.io//project/create-api-keys');
$request->setRequestMethod('POST');
$request->setHeaders(array(
  'master_key' => '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//project/create-api-keys"

headers = {'master_key': '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'}

response = requests.request("POST", url, headers=headers)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.rakam.io//project/create-api-keys")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["master_key"] = '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'

response = http.request(request)
puts response.read_body
```

> The above command returns JSON structured like this:

```json
{ }
```

### HTTP Request
`POST /project/create-api-keys`
### Responses for status codes
|200|403|
|----|----|
|[ProjectApiKeys](#projectapikeys)|[ErrorMessage](#errormessage)|


## Delete project

```shell
curl --request DELETE \
  --url https://app.rakam.io//project/delete \
  --header 'master_key: 5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
```

```javascript
var request = require("request");

var options = { method: 'DELETE',
  url: 'https://app.rakam.io//project/delete',
  headers: { master_key: '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```java
OkHttpClient client = new OkHttpClient();

Request request = new Request.Builder()
  .url("https://app.rakam.io//project/delete")
  .delete(null)
  .addHeader("master_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")
  .build();

Response response = client.newCall(request).execute();
```

```csharp
var client = new RestClient("https://app.rakam.io//project/delete");
var request = new RestRequest(Method.DELETE);
request.AddHeader("master_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8");
IRestResponse response = client.Execute(request);
```

```go
package main

import (
	"fmt"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://app.rakam.io//project/delete"

	req, _ := http.NewRequest("DELETE", url, nil)

	req.Header.Add("master_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$request->setRequestUrl('https://app.rakam.io//project/delete');
$request->setRequestMethod('DELETE');
$request->setHeaders(array(
  'master_key' => '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//project/delete"

headers = {'master_key': '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'}

response = requests.request("DELETE", url, headers=headers)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.rakam.io//project/delete")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Delete.new(url)
request["master_key"] = '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'

response = http.request(request)
puts response.read_body
```

> The above command returns JSON structured like this:

```json
{
  "message" : "str"
}
```

### HTTP Request
`DELETE /project/delete`
### Responses for status codes
|200|403|
|----|----|
|[SuccessMessage](#successmessage)|[ErrorMessage](#errormessage)|


## List created projects

```shell
curl --request POST \
  --url https://app.rakam.io//project/list \
  --header 'read_key: 5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' \
  --data '{"lock_key":"str"}'
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//project/list',
  headers: { read_key: '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' },
  body: { lock_key: 'str' },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"lock_key\":\"str\"}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//project/list")
  .post(body)
  .addHeader("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")
  .build();

Response response = client.newCall(request).execute();
```

```csharp
var client = new RestClient("https://app.rakam.io//project/list");
var request = new RestRequest(Method.POST);
request.AddHeader("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8");
request.AddParameter("undefined", "{\"lock_key\":\"str\"}", ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
```

```go
package main

import (
	"fmt"
	"strings"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://app.rakam.io//project/list"

	payload := strings.NewReader("{\"lock_key\":\"str\"}")

	req, _ := http.NewRequest("POST", url, payload)

	req.Header.Add("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->append('{"lock_key":"str"}');

$request->setRequestUrl('https://app.rakam.io//project/list');
$request->setRequestMethod('POST');
$request->setBody($body);

$request->setHeaders(array(
  'read_key' => '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//project/list"

payload = "{\"lock_key\":\"str\"}"
headers = {'read_key': '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'}

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.rakam.io//project/list")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["read_key"] = '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
request.body = "{\"lock_key\":\"str\"}"

response = http.request(request)
puts response.read_body
```

> The above command returns JSON structured like this:

```json
[ "str" ]
```

### HTTP Request
`POST /project/list`
### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|lock_key|false|string||


### Responses for status codes
|200|403|
|----|----|
|string array|[ErrorMessage](#errormessage)|


## Revoke API Keys

```shell
curl --request POST \
  --url https://app.rakam.io//project/revoke-api-keys \
  --data '{"project":"str","master_key":"str"}'
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//project/revoke-api-keys',
  body: { project: 'str', master_key: 'str' },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"project\":\"str\",\"master_key\":\"str\"}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//project/revoke-api-keys")
  .post(body)
  .build();

Response response = client.newCall(request).execute();
```

```csharp
var client = new RestClient("https://app.rakam.io//project/revoke-api-keys");
var request = new RestRequest(Method.POST);
request.AddParameter("undefined", "{\"project\":\"str\",\"master_key\":\"str\"}", ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
```

```go
package main

import (
	"fmt"
	"strings"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://app.rakam.io//project/revoke-api-keys"

	payload := strings.NewReader("{\"project\":\"str\",\"master_key\":\"str\"}")

	req, _ := http.NewRequest("POST", url, payload)

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->append('{"project":"str","master_key":"str"}');

$request->setRequestUrl('https://app.rakam.io//project/revoke-api-keys');
$request->setRequestMethod('POST');
$request->setBody($body);

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//project/revoke-api-keys"

payload = "{\"project\":\"str\",\"master_key\":\"str\"}"
response = requests.request("POST", url, data=payload)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.rakam.io//project/revoke-api-keys")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request.body = "{\"project\":\"str\",\"master_key\":\"str\"}"

response = http.request(request)
puts response.read_body
```

> The above command returns JSON structured like this:

```json
{
  "message" : "str"
}
```

### HTTP Request
`POST /project/revoke-api-keys`
### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|project|true|string||
|master_key|true|string||


### Responses for status codes
|200|
|----|
|[SuccessMessage](#successmessage)|


## Get collection schema

```shell
curl --request POST \
  --url https://app.rakam.io//project/schema \
  --header 'read_key: 5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' \
  --data '{"names":["str"]}'
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//project/schema',
  headers: { read_key: '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' },
  body: { names: [ 'str' ] },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"names\":[\"str\"]}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//project/schema")
  .post(body)
  .addHeader("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")
  .build();

Response response = client.newCall(request).execute();
```

```csharp
var client = new RestClient("https://app.rakam.io//project/schema");
var request = new RestRequest(Method.POST);
request.AddHeader("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8");
request.AddParameter("undefined", "{\"names\":[\"str\"]}", ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
```

```go
package main

import (
	"fmt"
	"strings"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://app.rakam.io//project/schema"

	payload := strings.NewReader("{\"names\":[\"str\"]}")

	req, _ := http.NewRequest("POST", url, payload)

	req.Header.Add("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->append('{"names":["str"]}');

$request->setRequestUrl('https://app.rakam.io//project/schema');
$request->setRequestMethod('POST');
$request->setBody($body);

$request->setHeaders(array(
  'read_key' => '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//project/schema"

payload = "{\"names\":[\"str\"]}"
headers = {'read_key': '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'}

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.rakam.io//project/schema")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["read_key"] = '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
request.body = "{\"names\":[\"str\"]}"

response = http.request(request)
puts response.read_body
```

> The above command returns JSON structured like this:

```json
[ { } ]
```

### HTTP Request
`POST /project/schema`
### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|names|false|string array||


### Responses for status codes
|200|403|
|----|----|
|[Collection](#collection) array|[ErrorMessage](#errormessage)|


## Add fields to collections

```shell
curl --request POST \
  --url https://app.rakam.io//project/schema/add \
  --header 'master_key: 5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' \
  --data '{"collection":"str","fields":[{}]}'
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//project/schema/add',
  headers: { master_key: '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' },
  body: { collection: 'str', fields: [ {} ] },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"collection\":\"str\",\"fields\":[{}]}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//project/schema/add")
  .post(body)
  .addHeader("master_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")
  .build();

Response response = client.newCall(request).execute();
```

```csharp
var client = new RestClient("https://app.rakam.io//project/schema/add");
var request = new RestRequest(Method.POST);
request.AddHeader("master_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8");
request.AddParameter("undefined", "{\"collection\":\"str\",\"fields\":[{}]}", ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
```

```go
package main

import (
	"fmt"
	"strings"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://app.rakam.io//project/schema/add"

	payload := strings.NewReader("{\"collection\":\"str\",\"fields\":[{}]}")

	req, _ := http.NewRequest("POST", url, payload)

	req.Header.Add("master_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->append('{"collection":"str","fields":[{}]}');

$request->setRequestUrl('https://app.rakam.io//project/schema/add');
$request->setRequestMethod('POST');
$request->setBody($body);

$request->setHeaders(array(
  'master_key' => '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//project/schema/add"

payload = "{\"collection\":\"str\",\"fields\":[{}]}"
headers = {'master_key': '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'}

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.rakam.io//project/schema/add")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["master_key"] = '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
request.body = "{\"collection\":\"str\",\"fields\":[{}]}"

response = http.request(request)
puts response.read_body
```

> The above command returns JSON structured like this:

```json
[ {
  "name" : "str",
  "type" : "STRING"
} ]
```

### HTTP Request
`POST /project/schema/add`
### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|collection|true|string||
|fields|true|[SchemaField](#schemafield) array||


### Responses for status codes
|200|403|
|----|----|
|[SchemaField](#schemafield) array|[ErrorMessage](#errormessage)|


## Add fields to collections by transforming other schemas

```shell
curl --request POST \
  --url https://app.rakam.io//project/schema/add/custom \
  --header 'master_key: 5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' \
  --data '{"collection":"str","schema_type":"AVRO","schema":"str"}'
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//project/schema/add/custom',
  headers: { master_key: '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' },
  body: { collection: 'str', schema_type: 'AVRO', schema: 'str' },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"collection\":\"str\",\"schema_type\":\"AVRO\",\"schema\":\"str\"}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//project/schema/add/custom")
  .post(body)
  .addHeader("master_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")
  .build();

Response response = client.newCall(request).execute();
```

```csharp
var client = new RestClient("https://app.rakam.io//project/schema/add/custom");
var request = new RestRequest(Method.POST);
request.AddHeader("master_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8");
request.AddParameter("undefined", "{\"collection\":\"str\",\"schema_type\":\"AVRO\",\"schema\":\"str\"}", ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
```

```go
package main

import (
	"fmt"
	"strings"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://app.rakam.io//project/schema/add/custom"

	payload := strings.NewReader("{\"collection\":\"str\",\"schema_type\":\"AVRO\",\"schema\":\"str\"}")

	req, _ := http.NewRequest("POST", url, payload)

	req.Header.Add("master_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->append('{"collection":"str","schema_type":"AVRO","schema":"str"}');

$request->setRequestUrl('https://app.rakam.io//project/schema/add/custom');
$request->setRequestMethod('POST');
$request->setBody($body);

$request->setHeaders(array(
  'master_key' => '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//project/schema/add/custom"

payload = "{\"collection\":\"str\",\"schema_type\":\"AVRO\",\"schema\":\"str\"}"
headers = {'master_key': '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'}

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.rakam.io//project/schema/add/custom")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["master_key"] = '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
request.body = "{\"collection\":\"str\",\"schema_type\":\"AVRO\",\"schema\":\"str\"}"

response = http.request(request)
puts response.read_body
```

> The above command returns JSON structured like this:

```json
[ {
  "name" : "str",
  "type" : "STRING"
} ]
```

### HTTP Request
`POST /project/schema/add/custom`
### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|collection|true|string||
|schema_type|true|enum (AVRO)||
|schema|true|string||


### Responses for status codes
|200|403|
|----|----|
|[SchemaField](#schemafield) array|[ErrorMessage](#errormessage)|


## Get project stats

```shell
curl --request POST \
  --url https://app.rakam.io//project/stats \
  --data '{}'
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//project/stats',
  body: {},
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//project/stats")
  .post(body)
  .build();

Response response = client.newCall(request).execute();
```

```csharp
var client = new RestClient("https://app.rakam.io//project/stats");
var request = new RestRequest(Method.POST);
request.AddParameter("undefined", "{}", ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
```

```go
package main

import (
	"fmt"
	"strings"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://app.rakam.io//project/stats"

	payload := strings.NewReader("{}")

	req, _ := http.NewRequest("POST", url, payload)

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->append('{}');

$request->setRequestUrl('https://app.rakam.io//project/stats');
$request->setRequestMethod('POST');
$request->setBody($body);

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//project/stats"

payload = "{}"
response = requests.request("POST", url, data=payload)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.rakam.io//project/stats")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request.body = "{}"

response = http.request(request)
puts response.read_body
```

> The above command returns JSON structured like this:

```json
{
  "prop" : { }
}
```

### HTTP Request
`POST /project/stats`
### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|array|false|object||


### Responses for status codes
|200|
|----|
|object|


# Collect


Collect data

## Collect multiple events

```shell
curl --request POST \
  --url https://app.rakam.io//event/batch \
  --data '{"api":{},"events":[{}]}'
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//event/batch',
  body: { api: {}, events: [ {} ] },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"api\":{},\"events\":[{}]}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//event/batch")
  .post(body)
  .build();

Response response = client.newCall(request).execute();
```

```csharp
var client = new RestClient("https://app.rakam.io//event/batch");
var request = new RestRequest(Method.POST);
request.AddParameter("undefined", "{\"api\":{},\"events\":[{}]}", ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
```

```go
package main

import (
	"fmt"
	"strings"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://app.rakam.io//event/batch"

	payload := strings.NewReader("{\"api\":{},\"events\":[{}]}")

	req, _ := http.NewRequest("POST", url, payload)

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->append('{"api":{},"events":[{}]}');

$request->setRequestUrl('https://app.rakam.io//event/batch');
$request->setRequestMethod('POST');
$request->setBody($body);

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//event/batch"

payload = "{\"api\":{},\"events\":[{}]}"
response = requests.request("POST", url, data=payload)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.rakam.io//event/batch")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request.body = "{\"api\":{},\"events\":[{}]}"

response = http.request(request)
puts response.read_body
```

> The above command returns JSON structured like this:

```json
1
```

### HTTP Request
`POST /event/batch`
### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|api|true|[EventContext](#eventcontext)||
|events|true|[Event](#event) array||


### Responses for status codes
|200|409|
|----|----|
|integer (int32)|integer (int32) array|



Returns 1 if the events are collected.

## Collect Bulk events

```shell
curl --request POST \
  --url https://app.rakam.io//event/bulk \
  --data '{"api":{},"events":[{}]}'
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//event/bulk',
  body: { api: {}, events: [ {} ] },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"api\":{},\"events\":[{}]}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//event/bulk")
  .post(body)
  .build();

Response response = client.newCall(request).execute();
```

```csharp
var client = new RestClient("https://app.rakam.io//event/bulk");
var request = new RestRequest(Method.POST);
request.AddParameter("undefined", "{\"api\":{},\"events\":[{}]}", ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
```

```go
package main

import (
	"fmt"
	"strings"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://app.rakam.io//event/bulk"

	payload := strings.NewReader("{\"api\":{},\"events\":[{}]}")

	req, _ := http.NewRequest("POST", url, payload)

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->append('{"api":{},"events":[{}]}');

$request->setRequestUrl('https://app.rakam.io//event/bulk');
$request->setRequestMethod('POST');
$request->setBody($body);

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//event/bulk"

payload = "{\"api\":{},\"events\":[{}]}"
response = requests.request("POST", url, data=payload)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.rakam.io//event/bulk")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request.body = "{\"api\":{},\"events\":[{}]}"

response = http.request(request)
puts response.read_body
```

> The above command returns JSON structured like this:

```json
{
  "message" : "str"
}
```

### HTTP Request
`POST /event/bulk`
### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|api|true|[EventContext](#eventcontext)||
|events|true|[Event](#event) array||


### Responses for status codes
|200|
|----|
|[SuccessMessage](#successmessage)|



Bulk API requires master_key as api key and built for importing the data without modifying (enrichment / sanitization http://rakam.io/doc/buremba/rakam-wiki/master/Event-Mappers). This endpoint is also more efficient then batch endpoint.The endpoint also accepts application/avro and text/csv formats. You need need to set 'collection' and 'master_key' query parameters if the content-type is not application/json.

## Collect bulk events from remote

```shell
curl --request POST \
  --url https://app.rakam.io//event/bulk/remote \
  --data '{"collection":"str","urls":["str"],"type":"AVRO"}'
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//event/bulk/remote',
  body: { collection: 'str', urls: [ 'str' ], type: 'AVRO' },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"collection\":\"str\",\"urls\":[\"str\"],\"type\":\"AVRO\"}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//event/bulk/remote")
  .post(body)
  .build();

Response response = client.newCall(request).execute();
```

```csharp
var client = new RestClient("https://app.rakam.io//event/bulk/remote");
var request = new RestRequest(Method.POST);
request.AddParameter("undefined", "{\"collection\":\"str\",\"urls\":[\"str\"],\"type\":\"AVRO\"}", ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
```

```go
package main

import (
	"fmt"
	"strings"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://app.rakam.io//event/bulk/remote"

	payload := strings.NewReader("{\"collection\":\"str\",\"urls\":[\"str\"],\"type\":\"AVRO\"}")

	req, _ := http.NewRequest("POST", url, payload)

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->append('{"collection":"str","urls":["str"],"type":"AVRO"}');

$request->setRequestUrl('https://app.rakam.io//event/bulk/remote');
$request->setRequestMethod('POST');
$request->setBody($body);

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//event/bulk/remote"

payload = "{\"collection\":\"str\",\"urls\":[\"str\"],\"type\":\"AVRO\"}"
response = requests.request("POST", url, data=payload)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.rakam.io//event/bulk/remote")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request.body = "{\"collection\":\"str\",\"urls\":[\"str\"],\"type\":\"AVRO\"}"

response = http.request(request)
puts response.read_body
```

> The above command returns JSON structured like this:

```json
1
```

### HTTP Request
`POST /event/bulk/remote`
### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|collection|true|string||
|urls|true|string array||
|type|true|enum (AVRO, CSV, JSON)||
|compression|false|enum (GZIP)||
|options|false|object||


### Responses for status codes
|200|409|
|----|----|
|integer (int32)|integer (int32) array|


## Collect event

```shell
curl --request POST \
  --url https://app.rakam.io//event/collect \
  --data '{"collection":"str","api":{},"properties":{}}'
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//event/collect',
  body: { collection: 'str', api: {}, properties: {} },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"collection\":\"str\",\"api\":{},\"properties\":{}}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//event/collect")
  .post(body)
  .build();

Response response = client.newCall(request).execute();
```

```csharp
var client = new RestClient("https://app.rakam.io//event/collect");
var request = new RestRequest(Method.POST);
request.AddParameter("undefined", "{\"collection\":\"str\",\"api\":{},\"properties\":{}}", ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
```

```go
package main

import (
	"fmt"
	"strings"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://app.rakam.io//event/collect"

	payload := strings.NewReader("{\"collection\":\"str\",\"api\":{},\"properties\":{}}")

	req, _ := http.NewRequest("POST", url, payload)

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->append('{"collection":"str","api":{},"properties":{}}');

$request->setRequestUrl('https://app.rakam.io//event/collect');
$request->setRequestMethod('POST');
$request->setBody($body);

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//event/collect"

payload = "{\"collection\":\"str\",\"api\":{},\"properties\":{}}"
response = requests.request("POST", url, data=payload)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.rakam.io//event/collect")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request.body = "{\"collection\":\"str\",\"api\":{},\"properties\":{}}"

response = http.request(request)
puts response.read_body
```

> The above command returns JSON structured like this:

```json
1
```

### HTTP Request
`POST /event/collect`
### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|collection|true|string|The collection of event (pageview, touch, click etc.)|
|api|true|[EventContext](#eventcontext)||
|properties|true|object|The properties of the event|


### Responses for status codes
|200|
|----|
|integer (int32)|


## Copy events directly to database

```shell
curl --request POST \
  --url https://app.rakam.io//event/copy \
  --data '{"api":{},"events":[{}]}'
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//event/copy',
  body: { api: {}, events: [ {} ] },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"api\":{},\"events\":[{}]}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//event/copy")
  .post(body)
  .build();

Response response = client.newCall(request).execute();
```

```csharp
var client = new RestClient("https://app.rakam.io//event/copy");
var request = new RestRequest(Method.POST);
request.AddParameter("undefined", "{\"api\":{},\"events\":[{}]}", ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
```

```go
package main

import (
	"fmt"
	"strings"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://app.rakam.io//event/copy"

	payload := strings.NewReader("{\"api\":{},\"events\":[{}]}")

	req, _ := http.NewRequest("POST", url, payload)

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->append('{"api":{},"events":[{}]}');

$request->setRequestUrl('https://app.rakam.io//event/copy');
$request->setRequestMethod('POST');
$request->setBody($body);

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//event/copy"

payload = "{\"api\":{},\"events\":[{}]}"
response = requests.request("POST", url, data=payload)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.rakam.io//event/copy")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request.body = "{\"api\":{},\"events\":[{}]}"

response = http.request(request)
puts response.read_body
```

> The above command returns JSON structured like this:

```json
1
```

### HTTP Request
`POST /event/copy`
### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|api|true|[EventContext](#eventcontext)||
|events|true|[Event](#event) array||


### Responses for status codes
|200|
|----|
|integer (int32)|


# Query


Analyze data

## Execute query on event data-set

```shell
curl --request POST \
  --url https://app.rakam.io//query/execute \
  --header 'read_key: 5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' \
  --data '{"query":"str"}'
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//query/execute',
  headers: { read_key: '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' },
  body: { query: 'str' },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"query\":\"str\"}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//query/execute")
  .post(body)
  .addHeader("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")
  .build();

Response response = client.newCall(request).execute();
```

```csharp
var client = new RestClient("https://app.rakam.io//query/execute");
var request = new RestRequest(Method.POST);
request.AddHeader("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8");
request.AddParameter("undefined", "{\"query\":\"str\"}", ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
```

```go
package main

import (
	"fmt"
	"strings"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://app.rakam.io//query/execute"

	payload := strings.NewReader("{\"query\":\"str\"}")

	req, _ := http.NewRequest("POST", url, payload)

	req.Header.Add("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->append('{"query":"str"}');

$request->setRequestUrl('https://app.rakam.io//query/execute');
$request->setRequestMethod('POST');
$request->setBody($body);

$request->setHeaders(array(
  'read_key' => '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//query/execute"

payload = "{\"query\":\"str\"}"
headers = {'read_key': '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'}

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.rakam.io//query/execute")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["read_key"] = '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
request.body = "{\"query\":\"str\"}"

response = http.request(request)
puts response.read_body
```

> The above command returns JSON structured like this:

```json
{ }
```

### HTTP Request
`POST /query/execute`
### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|query|true|string||
|export_type|false|enum (AVRO, CSV, JSON)||
|sampling|false|[QuerySampling](#querysampling)||
|default_schema|false|string|collection|
|limit|false|integer (int32)||
|timezone|false|[ZoneId](#zoneid)||


### Responses for status codes
|200|403|
|----|----|
|[ResponseQueryResult](#responsequeryresult)|[ErrorMessage](#errormessage)|


## Explain query

```shell
curl --request POST \
  --url https://app.rakam.io//query/explain \
  --header 'read_key: 5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' \
  --data '{"query":"str"}'
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//query/explain',
  headers: { read_key: '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' },
  body: { query: 'str' },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"query\":\"str\"}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//query/explain")
  .post(body)
  .addHeader("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")
  .build();

Response response = client.newCall(request).execute();
```

```csharp
var client = new RestClient("https://app.rakam.io//query/explain");
var request = new RestRequest(Method.POST);
request.AddHeader("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8");
request.AddParameter("undefined", "{\"query\":\"str\"}", ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
```

```go
package main

import (
	"fmt"
	"strings"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://app.rakam.io//query/explain"

	payload := strings.NewReader("{\"query\":\"str\"}")

	req, _ := http.NewRequest("POST", url, payload)

	req.Header.Add("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->append('{"query":"str"}');

$request->setRequestUrl('https://app.rakam.io//query/explain');
$request->setRequestMethod('POST');
$request->setBody($body);

$request->setHeaders(array(
  'read_key' => '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//query/explain"

payload = "{\"query\":\"str\"}"
headers = {'read_key': '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'}

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.rakam.io//query/explain")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["read_key"] = '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
request.body = "{\"query\":\"str\"}"

response = http.request(request)
puts response.read_body
```

> The above command returns JSON structured like this:

```json
{ }
```

### HTTP Request
`POST /query/explain`
### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|query|true|string|Query|


### Responses for status codes
|200|403|
|----|----|
|[ResponseQuery](#responsequery)|[ErrorMessage](#errormessage)|


## Test query

```shell
curl --request POST \
  --url https://app.rakam.io//query/metadata \
  --header 'read_key: 5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' \
  --data '{"query":"str"}'
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//query/metadata',
  headers: { read_key: '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' },
  body: { query: 'str' },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"query\":\"str\"}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//query/metadata")
  .post(body)
  .addHeader("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")
  .build();

Response response = client.newCall(request).execute();
```

```csharp
var client = new RestClient("https://app.rakam.io//query/metadata");
var request = new RestRequest(Method.POST);
request.AddHeader("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8");
request.AddParameter("undefined", "{\"query\":\"str\"}", ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
```

```go
package main

import (
	"fmt"
	"strings"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://app.rakam.io//query/metadata"

	payload := strings.NewReader("{\"query\":\"str\"}")

	req, _ := http.NewRequest("POST", url, payload)

	req.Header.Add("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->append('{"query":"str"}');

$request->setRequestUrl('https://app.rakam.io//query/metadata');
$request->setRequestMethod('POST');
$request->setBody($body);

$request->setHeaders(array(
  'read_key' => '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//query/metadata"

payload = "{\"query\":\"str\"}"
headers = {'read_key': '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'}

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.rakam.io//query/metadata")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["read_key"] = '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
request.body = "{\"query\":\"str\"}"

response = http.request(request)
puts response.read_body
```

> The above command returns JSON structured like this:

```json
[ {
  "name" : "str",
  "type" : "STRING"
} ]
```

### HTTP Request
`POST /query/metadata`
### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|query|true|string||


### Responses for status codes
|200|403|
|----|----|
|[SchemaField](#schemafield) array|[ErrorMessage](#errormessage)|


# Materialized view


Materialized view

## Change materialized view

```shell
curl --request POST \
  --url https://app.rakam.io//materialized-view/change \
  --header 'master_key: 5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' \
  --data '{"table_name":"str","real_time":true}'
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//materialized-view/change',
  headers: { master_key: '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' },
  body: { table_name: 'str', real_time: true },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"table_name\":\"str\",\"real_time\":true}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//materialized-view/change")
  .post(body)
  .addHeader("master_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")
  .build();

Response response = client.newCall(request).execute();
```

```csharp
var client = new RestClient("https://app.rakam.io//materialized-view/change");
var request = new RestRequest(Method.POST);
request.AddHeader("master_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8");
request.AddParameter("undefined", "{\"table_name\":\"str\",\"real_time\":true}", ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
```

```go
package main

import (
	"fmt"
	"strings"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://app.rakam.io//materialized-view/change"

	payload := strings.NewReader("{\"table_name\":\"str\",\"real_time\":true}")

	req, _ := http.NewRequest("POST", url, payload)

	req.Header.Add("master_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->append('{"table_name":"str","real_time":true}');

$request->setRequestUrl('https://app.rakam.io//materialized-view/change');
$request->setRequestMethod('POST');
$request->setBody($body);

$request->setHeaders(array(
  'master_key' => '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//materialized-view/change"

payload = "{\"table_name\":\"str\",\"real_time\":true}"
headers = {'master_key': '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'}

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.rakam.io//materialized-view/change")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["master_key"] = '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
request.body = "{\"table_name\":\"str\",\"real_time\":true}"

response = http.request(request)
puts response.read_body
```

> The above command returns JSON structured like this:

```json
{
  "message" : "str"
}
```

### HTTP Request
`POST /materialized-view/change`
### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|table_name|true|string||
|real_time|true|boolean||


### Responses for status codes
|200|403|
|----|----|
|[SuccessMessage](#successmessage)|[ErrorMessage](#errormessage)|


## Create view

```shell
curl --request POST \
  --url https://app.rakam.io//materialized-view/create \
  --header 'master_key: 5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' \
  --data '{"table_name":"str","name":"str","query":"str"}'
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//materialized-view/create',
  headers: { master_key: '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' },
  body: { table_name: 'str', name: 'str', query: 'str' },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"table_name\":\"str\",\"name\":\"str\",\"query\":\"str\"}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//materialized-view/create")
  .post(body)
  .addHeader("master_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")
  .build();

Response response = client.newCall(request).execute();
```

```csharp
var client = new RestClient("https://app.rakam.io//materialized-view/create");
var request = new RestRequest(Method.POST);
request.AddHeader("master_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8");
request.AddParameter("undefined", "{\"table_name\":\"str\",\"name\":\"str\",\"query\":\"str\"}", ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
```

```go
package main

import (
	"fmt"
	"strings"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://app.rakam.io//materialized-view/create"

	payload := strings.NewReader("{\"table_name\":\"str\",\"name\":\"str\",\"query\":\"str\"}")

	req, _ := http.NewRequest("POST", url, payload)

	req.Header.Add("master_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->append('{"table_name":"str","name":"str","query":"str"}');

$request->setRequestUrl('https://app.rakam.io//materialized-view/create');
$request->setRequestMethod('POST');
$request->setBody($body);

$request->setHeaders(array(
  'master_key' => '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//materialized-view/create"

payload = "{\"table_name\":\"str\",\"name\":\"str\",\"query\":\"str\"}"
headers = {'master_key': '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'}

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.rakam.io//materialized-view/create")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["master_key"] = '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
request.body = "{\"table_name\":\"str\",\"name\":\"str\",\"query\":\"str\"}"

response = http.request(request)
puts response.read_body
```

> The above command returns JSON structured like this:

```json
{
  "message" : "str"
}
```

### HTTP Request
`POST /materialized-view/create`
### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|table_name|true|string||
|name|true|string||
|query|true|string||
|update_interval|false|string||
|incremental|false|boolean||
|real_time|false|boolean||
|options|false|object||


### Responses for status codes
|200|403|
|----|----|
|[SuccessMessage](#successmessage)|[ErrorMessage](#errormessage)|


## Delete materialized view

```shell
curl --request POST \
  --url https://app.rakam.io//materialized-view/delete \
  --header 'master_key: 5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' \
  --data '{"table_name":"str"}'
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//materialized-view/delete',
  headers: { master_key: '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' },
  body: { table_name: 'str' },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"table_name\":\"str\"}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//materialized-view/delete")
  .post(body)
  .addHeader("master_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")
  .build();

Response response = client.newCall(request).execute();
```

```csharp
var client = new RestClient("https://app.rakam.io//materialized-view/delete");
var request = new RestRequest(Method.POST);
request.AddHeader("master_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8");
request.AddParameter("undefined", "{\"table_name\":\"str\"}", ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
```

```go
package main

import (
	"fmt"
	"strings"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://app.rakam.io//materialized-view/delete"

	payload := strings.NewReader("{\"table_name\":\"str\"}")

	req, _ := http.NewRequest("POST", url, payload)

	req.Header.Add("master_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->append('{"table_name":"str"}');

$request->setRequestUrl('https://app.rakam.io//materialized-view/delete');
$request->setRequestMethod('POST');
$request->setBody($body);

$request->setHeaders(array(
  'master_key' => '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//materialized-view/delete"

payload = "{\"table_name\":\"str\"}"
headers = {'master_key': '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'}

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.rakam.io//materialized-view/delete")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["master_key"] = '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
request.body = "{\"table_name\":\"str\"}"

response = http.request(request)
puts response.read_body
```

> The above command returns JSON structured like this:

```json
{
  "message" : "str"
}
```

### HTTP Request
`POST /materialized-view/delete`
### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|table_name|true|string||


### Responses for status codes
|200|403|
|----|----|
|[SuccessMessage](#successmessage)|[ErrorMessage](#errormessage)|


## Get view

```shell
curl --request POST \
  --url https://app.rakam.io//materialized-view/get \
  --header 'read_key: 5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' \
  --data '{"table_name":"str"}'
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//materialized-view/get',
  headers: { read_key: '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' },
  body: { table_name: 'str' },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"table_name\":\"str\"}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//materialized-view/get")
  .post(body)
  .addHeader("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")
  .build();

Response response = client.newCall(request).execute();
```

```csharp
var client = new RestClient("https://app.rakam.io//materialized-view/get");
var request = new RestRequest(Method.POST);
request.AddHeader("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8");
request.AddParameter("undefined", "{\"table_name\":\"str\"}", ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
```

```go
package main

import (
	"fmt"
	"strings"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://app.rakam.io//materialized-view/get"

	payload := strings.NewReader("{\"table_name\":\"str\"}")

	req, _ := http.NewRequest("POST", url, payload)

	req.Header.Add("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->append('{"table_name":"str"}');

$request->setRequestUrl('https://app.rakam.io//materialized-view/get');
$request->setRequestMethod('POST');
$request->setBody($body);

$request->setHeaders(array(
  'read_key' => '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//materialized-view/get"

payload = "{\"table_name\":\"str\"}"
headers = {'read_key': '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'}

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.rakam.io//materialized-view/get")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["read_key"] = '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
request.body = "{\"table_name\":\"str\"}"

response = http.request(request)
puts response.read_body
```

> The above command returns JSON structured like this:

```json
{
  "table_name" : "str",
  "name" : "str",
  "query" : "str"
}
```

### HTTP Request
`POST /materialized-view/get`
### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|table_name|true|string||


### Responses for status codes
|200|403|
|----|----|
|[MaterializedView](#materializedview)|[ErrorMessage](#errormessage)|


## List views

```shell
curl --request POST \
  --url https://app.rakam.io//materialized-view/list \
  --header 'read_key: 5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//materialized-view/list',
  headers: { read_key: '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```java
OkHttpClient client = new OkHttpClient();

Request request = new Request.Builder()
  .url("https://app.rakam.io//materialized-view/list")
  .post(null)
  .addHeader("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")
  .build();

Response response = client.newCall(request).execute();
```

```csharp
var client = new RestClient("https://app.rakam.io//materialized-view/list");
var request = new RestRequest(Method.POST);
request.AddHeader("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8");
IRestResponse response = client.Execute(request);
```

```go
package main

import (
	"fmt"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://app.rakam.io//materialized-view/list"

	req, _ := http.NewRequest("POST", url, nil)

	req.Header.Add("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$request->setRequestUrl('https://app.rakam.io//materialized-view/list');
$request->setRequestMethod('POST');
$request->setHeaders(array(
  'read_key' => '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//materialized-view/list"

headers = {'read_key': '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'}

response = requests.request("POST", url, headers=headers)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.rakam.io//materialized-view/list")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["read_key"] = '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'

response = http.request(request)
puts response.read_body
```

> The above command returns JSON structured like this:

```json
[ {
  "table_name" : "str",
  "name" : "str",
  "query" : "str"
} ]
```

### HTTP Request
`POST /materialized-view/list`
### Responses for status codes
|200|403|
|----|----|
|[MaterializedView](#materializedview) array|[ErrorMessage](#errormessage)|


## Get schemas

```shell
curl --request POST \
  --url https://app.rakam.io//materialized-view/schema \
  --header 'read_key: 5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' \
  --data '{"names":["str"]}'
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//materialized-view/schema',
  headers: { read_key: '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' },
  body: { names: [ 'str' ] },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"names\":[\"str\"]}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//materialized-view/schema")
  .post(body)
  .addHeader("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")
  .build();

Response response = client.newCall(request).execute();
```

```csharp
var client = new RestClient("https://app.rakam.io//materialized-view/schema");
var request = new RestRequest(Method.POST);
request.AddHeader("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8");
request.AddParameter("undefined", "{\"names\":[\"str\"]}", ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
```

```go
package main

import (
	"fmt"
	"strings"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://app.rakam.io//materialized-view/schema"

	payload := strings.NewReader("{\"names\":[\"str\"]}")

	req, _ := http.NewRequest("POST", url, payload)

	req.Header.Add("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->append('{"names":["str"]}');

$request->setRequestUrl('https://app.rakam.io//materialized-view/schema');
$request->setRequestMethod('POST');
$request->setBody($body);

$request->setHeaders(array(
  'read_key' => '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//materialized-view/schema"

payload = "{\"names\":[\"str\"]}"
headers = {'read_key': '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'}

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.rakam.io//materialized-view/schema")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["read_key"] = '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
request.body = "{\"names\":[\"str\"]}"

response = http.request(request)
puts response.read_body
```

> The above command returns JSON structured like this:

```json
[ { } ]
```

### HTTP Request
`POST /materialized-view/schema`
### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|names|false|string array||


### Responses for status codes
|200|403|
|----|----|
|[MaterializedViewSchema](#materializedviewschema) array|[ErrorMessage](#errormessage)|


# Continuous query


Continuous query

## Create stream

```shell
curl --request POST \
  --url https://app.rakam.io//continuous-query/create \
  --header 'master_key: 5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' \
  --data '{"continuous_query":{}}'
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//continuous-query/create',
  headers: { master_key: '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' },
  body: { continuous_query: {} },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"continuous_query\":{}}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//continuous-query/create")
  .post(body)
  .addHeader("master_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")
  .build();

Response response = client.newCall(request).execute();
```

```csharp
var client = new RestClient("https://app.rakam.io//continuous-query/create");
var request = new RestRequest(Method.POST);
request.AddHeader("master_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8");
request.AddParameter("undefined", "{\"continuous_query\":{}}", ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
```

```go
package main

import (
	"fmt"
	"strings"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://app.rakam.io//continuous-query/create"

	payload := strings.NewReader("{\"continuous_query\":{}}")

	req, _ := http.NewRequest("POST", url, payload)

	req.Header.Add("master_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->append('{"continuous_query":{}}');

$request->setRequestUrl('https://app.rakam.io//continuous-query/create');
$request->setRequestMethod('POST');
$request->setBody($body);

$request->setHeaders(array(
  'master_key' => '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//continuous-query/create"

payload = "{\"continuous_query\":{}}"
headers = {'master_key': '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'}

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.rakam.io//continuous-query/create")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["master_key"] = '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
request.body = "{\"continuous_query\":{}}"

response = http.request(request)
puts response.read_body
```

> The above command returns JSON structured like this:

```json
{
  "message" : "str"
}
```

### HTTP Request
`POST /continuous-query/create`
### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|continuous_query|true|[ContinuousQuery](#continuousquery)||
|replay|false|boolean||


### Responses for status codes
|200|400|403|
|----|----|----|
|[SuccessMessage](#successmessage)|[ErrorMessage](#errormessage)|[ErrorMessage](#errormessage)|



Creates a new continuous query for specified SQL query.
Rakam will process data in batches keep the result of query in-memory all the time.
Compared to reports, continuous queries continuously aggregate the data on the fly and the result is always available either in-memory or disk.

## Delete stream

```shell
curl --request POST \
  --url https://app.rakam.io//continuous-query/delete \
  --header 'master_key: 5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' \
  --data '{"table_name":"str"}'
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//continuous-query/delete',
  headers: { master_key: '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' },
  body: { table_name: 'str' },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"table_name\":\"str\"}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//continuous-query/delete")
  .post(body)
  .addHeader("master_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")
  .build();

Response response = client.newCall(request).execute();
```

```csharp
var client = new RestClient("https://app.rakam.io//continuous-query/delete");
var request = new RestRequest(Method.POST);
request.AddHeader("master_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8");
request.AddParameter("undefined", "{\"table_name\":\"str\"}", ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
```

```go
package main

import (
	"fmt"
	"strings"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://app.rakam.io//continuous-query/delete"

	payload := strings.NewReader("{\"table_name\":\"str\"}")

	req, _ := http.NewRequest("POST", url, payload)

	req.Header.Add("master_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->append('{"table_name":"str"}');

$request->setRequestUrl('https://app.rakam.io//continuous-query/delete');
$request->setRequestMethod('POST');
$request->setBody($body);

$request->setHeaders(array(
  'master_key' => '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//continuous-query/delete"

payload = "{\"table_name\":\"str\"}"
headers = {'master_key': '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'}

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.rakam.io//continuous-query/delete")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["master_key"] = '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
request.body = "{\"table_name\":\"str\"}"

response = http.request(request)
puts response.read_body
```

> The above command returns JSON structured like this:

```json
{
  "message" : "str"
}
```

### HTTP Request
`POST /continuous-query/delete`
### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|table_name|true|string||


### Responses for status codes
|200|403|
|----|----|
|[SuccessMessage](#successmessage)|[ErrorMessage](#errormessage)|


## Get continuous query

```shell
curl --request POST \
  --url https://app.rakam.io//continuous-query/get \
  --header 'read_key: 5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' \
  --data '{"table_name":"str"}'
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//continuous-query/get',
  headers: { read_key: '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' },
  body: { table_name: 'str' },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"table_name\":\"str\"}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//continuous-query/get")
  .post(body)
  .addHeader("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")
  .build();

Response response = client.newCall(request).execute();
```

```csharp
var client = new RestClient("https://app.rakam.io//continuous-query/get");
var request = new RestRequest(Method.POST);
request.AddHeader("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8");
request.AddParameter("undefined", "{\"table_name\":\"str\"}", ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
```

```go
package main

import (
	"fmt"
	"strings"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://app.rakam.io//continuous-query/get"

	payload := strings.NewReader("{\"table_name\":\"str\"}")

	req, _ := http.NewRequest("POST", url, payload)

	req.Header.Add("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->append('{"table_name":"str"}');

$request->setRequestUrl('https://app.rakam.io//continuous-query/get');
$request->setRequestMethod('POST');
$request->setBody($body);

$request->setHeaders(array(
  'read_key' => '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//continuous-query/get"

payload = "{\"table_name\":\"str\"}"
headers = {'read_key': '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'}

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.rakam.io//continuous-query/get")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["read_key"] = '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
request.body = "{\"table_name\":\"str\"}"

response = http.request(request)
puts response.read_body
```

> The above command returns JSON structured like this:

```json
{
  "name" : "str",
  "query" : "str"
}
```

### HTTP Request
`POST /continuous-query/get`
### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|table_name|true|string||


### Responses for status codes
|200|403|
|----|----|
|[ContinuousQuery](#continuousquery)|[ErrorMessage](#errormessage)|


## List queries

```shell
curl --request POST \
  --url https://app.rakam.io//continuous-query/list \
  --header 'read_key: 5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//continuous-query/list',
  headers: { read_key: '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```java
OkHttpClient client = new OkHttpClient();

Request request = new Request.Builder()
  .url("https://app.rakam.io//continuous-query/list")
  .post(null)
  .addHeader("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")
  .build();

Response response = client.newCall(request).execute();
```

```csharp
var client = new RestClient("https://app.rakam.io//continuous-query/list");
var request = new RestRequest(Method.POST);
request.AddHeader("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8");
IRestResponse response = client.Execute(request);
```

```go
package main

import (
	"fmt"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://app.rakam.io//continuous-query/list"

	req, _ := http.NewRequest("POST", url, nil)

	req.Header.Add("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$request->setRequestUrl('https://app.rakam.io//continuous-query/list');
$request->setRequestMethod('POST');
$request->setHeaders(array(
  'read_key' => '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//continuous-query/list"

headers = {'read_key': '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'}

response = requests.request("POST", url, headers=headers)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.rakam.io//continuous-query/list")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["read_key"] = '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'

response = http.request(request)
puts response.read_body
```

> The above command returns JSON structured like this:

```json
[ {
  "name" : "str",
  "query" : "str"
} ]
```

### HTTP Request
`POST /continuous-query/list`
### Responses for status codes
|200|403|
|----|----|
|[ContinuousQuery](#continuousquery) array|[ErrorMessage](#errormessage)|


## Get query schema

```shell
curl --request POST \
  --url https://app.rakam.io//continuous-query/schema \
  --header 'read_key: 5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' \
  --data '{"names":["str"]}'
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//continuous-query/schema',
  headers: { read_key: '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' },
  body: { names: [ 'str' ] },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"names\":[\"str\"]}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//continuous-query/schema")
  .post(body)
  .addHeader("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")
  .build();

Response response = client.newCall(request).execute();
```

```csharp
var client = new RestClient("https://app.rakam.io//continuous-query/schema");
var request = new RestRequest(Method.POST);
request.AddHeader("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8");
request.AddParameter("undefined", "{\"names\":[\"str\"]}", ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
```

```go
package main

import (
	"fmt"
	"strings"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://app.rakam.io//continuous-query/schema"

	payload := strings.NewReader("{\"names\":[\"str\"]}")

	req, _ := http.NewRequest("POST", url, payload)

	req.Header.Add("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->append('{"names":["str"]}');

$request->setRequestUrl('https://app.rakam.io//continuous-query/schema');
$request->setRequestMethod('POST');
$request->setBody($body);

$request->setHeaders(array(
  'read_key' => '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//continuous-query/schema"

payload = "{\"names\":[\"str\"]}"
headers = {'read_key': '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'}

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.rakam.io//continuous-query/schema")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["read_key"] = '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
request.body = "{\"names\":[\"str\"]}"

response = http.request(request)
puts response.read_body
```

> The above command returns JSON structured like this:

```json
[ { } ]
```

### HTTP Request
`POST /continuous-query/schema`
### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|names|false|string array||


### Responses for status codes
|200|403|
|----|----|
|[Collection](#collection) array|[ErrorMessage](#errormessage)|


## Test continuous query

```shell
curl --request POST \
  --url https://app.rakam.io//continuous-query/test \
  --header 'read_key: 5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' \
  --data '{"query":"str"}'
```

```javascript
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//continuous-query/test',
  headers: { read_key: '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8' },
  body: { query: 'str' },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"query\":\"str\"}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//continuous-query/test")
  .post(body)
  .addHeader("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")
  .build();

Response response = client.newCall(request).execute();
```

```csharp
var client = new RestClient("https://app.rakam.io//continuous-query/test");
var request = new RestRequest(Method.POST);
request.AddHeader("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8");
request.AddParameter("undefined", "{\"query\":\"str\"}", ParameterType.RequestBody);
IRestResponse response = client.Execute(request);
```

```go
package main

import (
	"fmt"
	"strings"
	"net/http"
	"io/ioutil"
)

func main() {

	url := "https://app.rakam.io//continuous-query/test"

	payload := strings.NewReader("{\"query\":\"str\"}")

	req, _ := http.NewRequest("POST", url, payload)

	req.Header.Add("read_key", "5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8")

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->append('{"query":"str"}');

$request->setRequestUrl('https://app.rakam.io//continuous-query/test');
$request->setRequestMethod('POST');
$request->setBody($body);

$request->setHeaders(array(
  'read_key' => '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//continuous-query/test"

payload = "{\"query\":\"str\"}"
headers = {'read_key': '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'}

response = requests.request("POST", url, data=payload, headers=headers)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.rakam.io//continuous-query/test")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request["read_key"] = '5o5efo7u3s46jbplbe2h0b8ub2jf4nt06t4k8gadqmjh2lqvmao6fpjdtsijfha8'
request.body = "{\"query\":\"str\"}"

response = http.request(request)
puts response.read_body
```

> The above command returns JSON structured like this:

```json
true
```

### HTTP Request
`POST /continuous-query/test`
### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|query|true|string||


### Responses for status codes
|200|403|
|----|----|
|boolean|[ErrorMessage](#errormessage)|



## Definitions
### User
|name|description|required|schema|default|
|----|----|----|----|----|
|id||true|object||
|api||true|[UserContext](#usercontext)||
|properties||true|object||


### Recipe
|name|description|required|schema|default|
|----|----|----|----|----|
|strategy||false|enum (DEFAULT, SPECIFIC)||
|collections||false|object||
|materialized_views||false|[MaterializedView](#materializedview) array||
|continuous_queries||false|[ContinuousQuery](#continuousquery) array||


### FunnelWindow
|name|description|required|schema|default|
|----|----|----|----|----|
|value||false|integer (int32)||
|type||false|enum (DAY, WEEK, MONTH)||


### QueryResult
|name|description|required|schema|default|
|----|----|----|----|----|
|metadata||true|[SchemaField](#schemafield) array||
|result|Each row is an array that contains the values for the columns that are defined in metadata property.|true|object array array||
|error||true|[QueryError](#queryerror)||
|properties||true|object||
|failed||false|boolean||


### Goal
|name|description|required|schema|default|
|----|----|----|----|----|
|collection||true|string||
|filter||false|string||


### ContinuousQuery
|name|description|required|schema|default|
|----|----|----|----|----|
|table_name||false|string||
|name|Name|true|string||
|query|The sql query that will be executed and materialized|true|string||
|partition_keys||false|string array||
|options|Additional information about the continuous query|false|object||
|windowDuration||false|string||


### SuccessMessage
|name|description|required|schema|default|
|----|----|----|----|----|
|message||true|string||
|success||false|boolean||


### MetadataResponse
|name|description|required|schema|default|
|----|----|----|----|----|
|columns||false|[SchemaField](#schemafield) array||
|identifierColumn||false|string||


### Measure
|name|description|required|schema|default|
|----|----|----|----|----|
|column||false|string||
|aggregation||true|enum (COUNT, COUNT_UNIQUE, SUM, MINIMUM, MAXIMUM, AVERAGE, APPROXIMATE_UNIQUE)||


### ABTestingReport
|name|description|required|schema|default|
|----|----|----|----|----|
|name||true|string||
|variants||true|[Variant](#variant) array||
|goal||true|[Goal](#goal)||
|options||false|object||
|id||false|integer (int32)||
|collectionName||false|string||
|connectorField||false|string||


### ZoneId
|name|description|required|schema|default|
|----|----|----|----|----|
|id||false|string||
|rules||false|[ZoneRules](#zonerules)||


### BatchUserOperations
|name|description|required|schema|default|
|----|----|----|----|----|
|id||true|object||
|set_properties||false|object||
|set_properties_once||false|object||
|increment_properties||false|object||
|unset_properties||false|string array||
|time||false|integer (int64)||


### CollectionEvent
|name|description|required|schema|default|
|----|----|----|----|----|
|collection||false|string||
|properties||false|object||


### UserContext
|name|description|required|schema|default|
|----|----|----|----|----|
|api_key||false|string||
|library||false|[Library](#library)||
|upload_time||false|integer (int64)||
|checksum||false|string||


### Reference
|name|description|required|schema|default|
|----|----|----|----|----|
|type||true|enum (COLUMN, REFERENCE)||
|value||true|string||


### QuerySampling
|name|description|required|schema|default|
|----|----|----|----|----|
|method||false|enum (BERNOULLI, SYSTEM)||
|percentage||false|integer (int32)||


### EventMapperDescription
|name|description|required|schema|default|
|----|----|----|----|----|
|name||false|string||
|description||false|string||
|dependentFields||false|object||
|constantFields||false|[SchemaField](#schemafield) array||


### PrecalculatedTable
|name|description|required|schema|default|
|----|----|----|----|----|
|name||true|string||
|tableName||true|string||


### RetentionAction
|name|description|required|schema|default|
|----|----|----|----|----|
|collection||false|string||


### ResponseQuery
|name|description|required|schema|default|
|----|----|----|----|----|
|with||false|object||
|groupBy||false|[GroupBy](#groupby) array||
|orderBy||false|[Ordering](#ordering) array||
|limit||false|integer (int64)||
|queryLocation||false|[NodeLocation](#nodelocation)||


### ProjectApiKeys
|name|description|required|schema|default|
|----|----|----|----|----|
|master_key||false|string||
|read_key||false|string||
|write_key||false|string||


### EventFilter
|name|description|required|schema|default|
|----|----|----|----|----|
|collection||false|string||
|timeframe||false|[Timeframe](#timeframe)||
|aggregation||false|[EventFilterAggregation](#eventfilteraggregation)||
|filterExpression||false|string||


### Sorting
|name|description|required|schema|default|
|----|----|----|----|----|
|column||false|string||
|order||false|enum (asc, desc)||


### EventContext
|name|description|required|schema|default|
|----|----|----|----|----|
|api_key||false|string||
|library|Optional library information for statistics|false|[Library](#library)||
|api_version||false|string||
|upload_time||false|integer (int64)||
|uuid|Optional UUID for deduplication|false|string||
|checksum|Optional checksum for verify the body content|false|string||


### Variant
|name|description|required|schema|default|
|----|----|----|----|----|
|name||true|string||
|weight||true|integer (int32)||
|data||true|object||


### SchemaField
|name|description|required|schema|default|
|----|----|----|----|----|
|name||true|string||
|type||true|enum (STRING, INTEGER, DECIMAL, DOUBLE, LONG, BOOLEAN, DATE, TIME, TIMESTAMP, BINARY, ARRAY_STRING, ARRAY_INTEGER, ARRAY_DECIMAL, ARRAY_DOUBLE, ARRAY_LONG, ARRAY_BOOLEAN, ARRAY_DATE, ARRAY_TIME, ARRAY_TIMESTAMP, ARRAY_BINARY, MAP_STRING, MAP_INTEGER, MAP_DECIMAL, MAP_DOUBLE, MAP_LONG, MAP_BOOLEAN, MAP_DATE, MAP_TIME, MAP_TIMESTAMP, MAP_BINARY)||
|unique||false|boolean||
|descriptiveName||false|string||
|description||false|string||
|category||false|string||


### ModuleDescriptor
|name|description|required|schema|default|
|----|----|----|----|----|
|name||false|string||
|description||false|string||
|className||false|string||
|isActive||false|boolean||
|condition||false|[Condition](#condition)||
|properties||false|[ConfigItem](#configitem) array||


### MaterializedViewSchema
|name|description|required|schema|default|
|----|----|----|----|----|
|name||false|string||
|fields||false|[SchemaField](#schemafield) array||


### SingleUserBatchOperations
|name|description|required|schema|default|
|----|----|----|----|----|
|set_properties||false|object||
|set_properties_once||false|object||
|increment_properties||false|object||
|unset_properties||false|string array||
|time||true|integer (int64)||
|user||false|object||


### Event
|name|description|required|schema|default|
|----|----|----|----|----|
|collection|The collection of event (pageview, touch, click etc.)|true|string||
|api||true|[EventContext](#eventcontext)||
|properties|The properties of the event|true|object||


### Collection
|name|description|required|schema|default|
|----|----|----|----|----|
|name||false|string||
|fields||false|[SchemaField](#schemafield) array||


### MaterializedView
|name|description|required|schema|default|
|----|----|----|----|----|
|table_name||true|string||
|name||true|string||
|query||true|string||
|update_interval||false|string||
|incremental||false|boolean||
|real_time||false|boolean||
|options||false|object||


### ErrorMessage
|name|description|required|schema|default|
|----|----|----|----|----|
|error||true|string||
|error_code||true|integer (int32)||


### ResponseQueryResult
|name|description|required|schema|default|
|----|----|----|----|----|
|data||false|[QueryResult](#queryresult)||
|status||false|[HttpResponseStatus](#httpresponsestatus)||
|cookies||false|[Cookie](#cookie) array||


### FunnelStep
|name|description|required|schema|default|
|----|----|----|----|----|
|collection||false|string||


