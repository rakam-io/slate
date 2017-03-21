---
title: API Reference
language_tabs:
  - java
  - c#
  - go
  - node
  - php
  - python
  - ruby
toc_footers:
 - <a href='#'>Sign Up for a Developer Key</a>
includes:
    - errors
search: true
---
# Introduction

```
We have language bindings in java, c#, go, node, php, python, ruby! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.
```

An analytics platform API that lets you create your own analytics services.

### Version
Version: 0.7

## Contact Information
Email: contact@rakam.io

### License
License: Apache License 2.0

License url: http://www.apache.org/licenses/LICENSE-2.0.html

### URI scheme
Host: app.rakam.io
BasePath: /

# Event explorer


Event Explorer

## Perform simple query on event data
```curl
curl "app.rakam.io/event-explorer/analyze" -H "read_key: myread_key" -X POST -d @- << EOF 
{
  "startDate" : "2016-03-03T10:15:30.00Z",
  "endDate" : "2016-03-03T10:15:30.00Z",
  "collections" : [ "str" ]
}
EOF
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"startDate\":\"str\",\"endDate\":\"str\",\"collections\":[\"str\"]}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//event-explorer/analyze")
  .post(body)
  .build();

Response response = client.newCall(request).execute();
```

```c#
var client = new RestClient("https://app.rakam.io//event-explorer/analyze");
var request = new RestRequest(Method.POST);
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

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```node
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//event-explorer/analyze',
  body: { startDate: 'str', endDate: 'str', collections: [ 'str' ] },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

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

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//event-explorer/analyze"

payload = "{\"startDate\":\"str\",\"endDate\":\"str\",\"collections\":[\"str\"]}"
response = requests.request("POST", url, data=payload)

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
|startDate|true|string (date-time)||
|endDate|true|string (date-time)||
|collections|true|string array||


### Responses for status codes
|200|403|
|----|----|
|[QueryResult](#queryresult)|[ErrorMessage](#errormessage)|


## Event statistics
```curl
curl "app.rakam.io/event-explorer/extra_dimensions" -H "read_key: myread_key" -X GET
```

```java
OkHttpClient client = new OkHttpClient();

Request request = new Request.Builder()
  .url("https://app.rakam.io//event-explorer/extra_dimensions")
  .get()
  .build();

Response response = client.newCall(request).execute();
```

```c#
var client = new RestClient("https://app.rakam.io//event-explorer/extra_dimensions");
var request = new RestRequest(Method.GET);
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

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```node
var request = require("request");

var options = { method: 'GET',
  url: 'https://app.rakam.io//event-explorer/extra_dimensions' };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$request->setRequestUrl('https://app.rakam.io//event-explorer/extra_dimensions');
$request->setRequestMethod('GET');
$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//event-explorer/extra_dimensions"

response = requests.request("GET", url)

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
```curl
curl "app.rakam.io/event-explorer/pre_calculate" -H "master_key: mymaster_key" -X POST -d @- << EOF 
{
  "collections" : [ "str" ],
  "dimensions" : [ "str" ],
  "aggregations" : [ "COUNT" ],
  "measures" : [ "str" ],
  "tableName" : "str"
}
EOF
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"collections\":[\"str\"],\"dimensions\":[\"str\"],\"aggregations\":[\"COUNT\"],\"measures\":[\"str\"],\"tableName\":\"str\"}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//event-explorer/pre_calculate")
  .post(body)
  .build();

Response response = client.newCall(request).execute();
```

```c#
var client = new RestClient("https://app.rakam.io//event-explorer/pre_calculate");
var request = new RestRequest(Method.POST);
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

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```node
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//event-explorer/pre_calculate',
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

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->append('{"collections":["str"],"dimensions":["str"],"aggregations":["COUNT"],"measures":["str"],"tableName":"str"}');

$request->setRequestUrl('https://app.rakam.io//event-explorer/pre_calculate');
$request->setRequestMethod('POST');
$request->setBody($body);

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//event-explorer/pre_calculate"

payload = "{\"collections\":[\"str\"],\"dimensions\":[\"str\"],\"aggregations\":[\"COUNT\"],\"measures\":[\"str\"],\"tableName\":\"str\"}"
response = requests.request("POST", url, data=payload)

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
```curl
curl "app.rakam.io/event-explorer/statistics" -H "read_key: myread_key" -X POST -d @- << EOF 
{
  "startDate" : "2016-03-03T10:15:30.00Z",
  "endDate" : "2016-03-03T10:15:30.00Z"
}
EOF
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"startDate\":\"str\",\"endDate\":\"str\"}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//event-explorer/statistics")
  .post(body)
  .build();

Response response = client.newCall(request).execute();
```

```c#
var client = new RestClient("https://app.rakam.io//event-explorer/statistics");
var request = new RestRequest(Method.POST);
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

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```node
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//event-explorer/statistics',
  body: { startDate: 'str', endDate: 'str' },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

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

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//event-explorer/statistics"

payload = "{\"startDate\":\"str\",\"endDate\":\"str\"}"
response = requests.request("POST", url, data=payload)

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
|startDate|true|string (date-time)||
|endDate|true|string (date-time)||


### Responses for status codes
|200|403|
|----|----|
|[QueryResult](#queryresult)|[ErrorMessage](#errormessage)|


# Funnel


Funnel Analyzer

## Execute query
```curl
curl "app.rakam.io/funnel/analyze" -H "read_key: myread_key" -X POST -d @- << EOF 
{
  "steps" : [ { } ],
  "startDate" : "2015-01-20",
  "endDate" : "2015-01-20"
}
EOF
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"steps\":[{}],\"startDate\":\"str\",\"endDate\":\"str\"}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//funnel/analyze")
  .post(body)
  .build();

Response response = client.newCall(request).execute();
```

```c#
var client = new RestClient("https://app.rakam.io//funnel/analyze");
var request = new RestRequest(Method.POST);
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

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```node
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//funnel/analyze',
  body: { steps: [ {} ], startDate: 'str', endDate: 'str' },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

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

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//funnel/analyze"

payload = "{\"steps\":[{}],\"startDate\":\"str\",\"endDate\":\"str\"}"
response = requests.request("POST", url, data=payload)

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
|timezone|false|string||


### Responses for status codes
|200|403|
|----|----|
|[QueryResult](#queryresult)|[ErrorMessage](#errormessage)|


# Realtime


Realtime

## Create report
```curl
curl "app.rakam.io/realtime/create" -H "master_key: mymaster_key" -X POST -d @- << EOF 
{
  "name" : "str",
  "measures" : [ {
    "column" : "str",
    "aggregation" : "COUNT"
  } ],
  "table_name" : "str",
  "collections" : [ "str" ]
}
EOF
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"name\":\"str\",\"measures\":[{}],\"table_name\":\"str\",\"collections\":[\"str\"]}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//realtime/create")
  .post(body)
  .build();

Response response = client.newCall(request).execute();
```

```c#
var client = new RestClient("https://app.rakam.io//realtime/create");
var request = new RestRequest(Method.POST);
request.AddParameter("undefined", "{\"name\":\"str\",\"measures\":[{}],\"table_name\":\"str\",\"collections\":[\"str\"]}", ParameterType.RequestBody);
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

	url := "https://app.rakam.io//realtime/create"

	payload := strings.NewReader("{\"name\":\"str\",\"measures\":[{}],\"table_name\":\"str\",\"collections\":[\"str\"]}")

	req, _ := http.NewRequest("POST", url, payload)

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```node
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//realtime/create',
  body: 
   { name: 'str',
     measures: [ {} ],
     table_name: 'str',
     collections: [ 'str' ] },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->append('{"name":"str","measures":[{}],"table_name":"str","collections":["str"]}');

$request->setRequestUrl('https://app.rakam.io//realtime/create');
$request->setRequestMethod('POST');
$request->setBody($body);

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//realtime/create"

payload = "{\"name\":\"str\",\"measures\":[{}],\"table_name\":\"str\",\"collections\":[\"str\"]}"
response = requests.request("POST", url, data=payload)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.rakam.io//realtime/create")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request.body = "{\"name\":\"str\",\"measures\":[{}],\"table_name\":\"str\",\"collections\":[\"str\"]}"

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
`POST /realtime/create`
### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|name|true|string||
|measures|true|[Measure](#measure) array||
|table_name|true|string||
|collections|true|string array||
|filter|false|string||
|dimensions|false|string array||


### Responses for status codes
|200|403|
|----|----|
|[SuccessMessage](#successmessage)|[ErrorMessage](#errormessage)|


## Delete report
```curl
curl "app.rakam.io/realtime/delete" -H "master_key: mymaster_key" -X POST -d @- << EOF 
{
  "table_name" : "str"
}
EOF
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"table_name\":\"str\"}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//realtime/delete")
  .post(body)
  .build();

Response response = client.newCall(request).execute();
```

```c#
var client = new RestClient("https://app.rakam.io//realtime/delete");
var request = new RestRequest(Method.POST);
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

	url := "https://app.rakam.io//realtime/delete"

	payload := strings.NewReader("{\"table_name\":\"str\"}")

	req, _ := http.NewRequest("POST", url, payload)

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```node
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//realtime/delete',
  body: { table_name: 'str' },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->append('{"table_name":"str"}');

$request->setRequestUrl('https://app.rakam.io//realtime/delete');
$request->setRequestMethod('POST');
$request->setBody($body);

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//realtime/delete"

payload = "{\"table_name\":\"str\"}"
response = requests.request("POST", url, data=payload)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.rakam.io//realtime/delete")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
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
`POST /realtime/delete`
### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|table_name|true|string||


### Responses for status codes
|200|403|
|----|----|
|[SuccessMessage](#successmessage)|[ErrorMessage](#errormessage)|


## Get report
```curl
curl "app.rakam.io/realtime/get" -H "read_key: myread_key" -X POST -d @- << EOF 
{
  "table_name" : "str",
  "measure" : {
    "column" : "str",
    "aggregation" : "COUNT"
  }
}
EOF
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"table_name\":\"str\",\"measure\":{}}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//realtime/get")
  .post(body)
  .build();

Response response = client.newCall(request).execute();
```

```c#
var client = new RestClient("https://app.rakam.io//realtime/get");
var request = new RestRequest(Method.POST);
request.AddParameter("undefined", "{\"table_name\":\"str\",\"measure\":{}}", ParameterType.RequestBody);
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

	url := "https://app.rakam.io//realtime/get"

	payload := strings.NewReader("{\"table_name\":\"str\",\"measure\":{}}")

	req, _ := http.NewRequest("POST", url, payload)

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```node
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//realtime/get',
  body: { table_name: 'str', measure: {} },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->append('{"table_name":"str","measure":{}}');

$request->setRequestUrl('https://app.rakam.io//realtime/get');
$request->setRequestMethod('POST');
$request->setBody($body);

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//realtime/get"

payload = "{\"table_name\":\"str\",\"measure\":{}}"
response = requests.request("POST", url, data=payload)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.rakam.io//realtime/get")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request.body = "{\"table_name\":\"str\",\"measure\":{}}"

response = http.request(request)
puts response.read_body
```

> The above command returns JSON structured like this:

```json
{ }
```

### HTTP Request
`POST /realtime/get`
### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|table_name|true|string||
|filter|false|string||
|measure|true|[Measure](#measure)||
|dimensions|false|string array||
|aggregate|false|boolean||
|date_start|false|string (date-time)||
|date_end|false|string (date-time)||


### Responses for status codes
|200|400|403|
|----|----|----|
|[RealTimeQueryResult](#realtimequeryresult)|[ErrorMessage](#errormessage)|[ErrorMessage](#errormessage)|


## List queries
```curl
curl "app.rakam.io/realtime/list" -H "read_key: myread_key" -X POST
```

```java
OkHttpClient client = new OkHttpClient();

Request request = new Request.Builder()
  .url("https://app.rakam.io//realtime/list")
  .post(null)
  .build();

Response response = client.newCall(request).execute();
```

```c#
var client = new RestClient("https://app.rakam.io//realtime/list");
var request = new RestRequest(Method.POST);
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

	url := "https://app.rakam.io//realtime/list"

	req, _ := http.NewRequest("POST", url, nil)

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```node
var request = require("request");

var options = { method: 'POST', url: 'https://app.rakam.io//realtime/list' };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$request->setRequestUrl('https://app.rakam.io//realtime/list');
$request->setRequestMethod('POST');
$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//realtime/list"

response = requests.request("POST", url)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.rakam.io//realtime/list")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)

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
`POST /realtime/list`
### Responses for status codes
|200|403|
|----|----|
|[ContinuousQuery](#continuousquery) array|[ErrorMessage](#errormessage)|


# Retention


Retention Analyzer module

## Execute query
```curl
curl "app.rakam.io/retention/analyze" -H "read_key: myread_key" -X POST -d @- << EOF 
{
  "first_action" : { },
  "returning_action" : { },
  "dimension" : "str",
  "date_unit" : "DAY",
  "startDate" : "2015-01-20",
  "endDate" : "2015-01-20"
}
EOF
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"first_action\":{},\"returning_action\":{},\"dimension\":\"str\",\"date_unit\":\"DAY\",\"startDate\":\"str\",\"endDate\":\"str\"}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//retention/analyze")
  .post(body)
  .build();

Response response = client.newCall(request).execute();
```

```c#
var client = new RestClient("https://app.rakam.io//retention/analyze");
var request = new RestRequest(Method.POST);
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

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```node
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//retention/analyze',
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

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->append('{"first_action":{},"returning_action":{},"dimension":"str","date_unit":"DAY","startDate":"str","endDate":"str"}');

$request->setRequestUrl('https://app.rakam.io//retention/analyze');
$request->setRequestMethod('POST');
$request->setBody($body);

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//retention/analyze"

payload = "{\"first_action\":{},\"returning_action\":{},\"dimension\":\"str\",\"date_unit\":\"DAY\",\"startDate\":\"str\",\"endDate\":\"str\"}"
response = requests.request("POST", url, data=payload)

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
```curl
curl "app.rakam.io/user/batch" -H "write_key: mywrite_key" -X POST -d @- << EOF 
{
  "id" : "object",
  "api" : { },
  "data" : [ {
    "time" : 1
  } ]
}
EOF
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"id\":{},\"api\":{},\"data\":[{}]}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//user/batch")
  .post(body)
  .build();

Response response = client.newCall(request).execute();
```

```c#
var client = new RestClient("https://app.rakam.io//user/batch");
var request = new RestRequest(Method.POST);
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

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```node
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//user/batch',
  body: { id: {}, api: {}, data: [ {} ] },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

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

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//user/batch"

payload = "{\"id\":{},\"api\":{},\"data\":[{}]}"
response = requests.request("POST", url, data=payload)

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
```curl
curl "app.rakam.io/user/batch/create" -H "write_key: mywrite_key" -X POST -d @- << EOF 
{
  "users" : [ {
    "id" : "object",
    "api" : { },
    "properties" : "object"
  } ]
}
EOF
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"users\":[null]}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//user/batch/create")
  .post(body)
  .build();

Response response = client.newCall(request).execute();
```

```c#
var client = new RestClient("https://app.rakam.io//user/batch/create");
var request = new RestRequest(Method.POST);
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

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```node
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//user/batch/create',
  body: { users: [ null ] },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

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

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//user/batch/create"

payload = "{\"users\":[null]}"
response = requests.request("POST", url, data=payload)

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
```curl
curl "app.rakam.io/user/batch_operations" -H "master_key: mymaster_key" -X POST -d @- << EOF 
{
  "api" : { },
  "data" : [ {
    "id" : "object"
  } ]
}
EOF
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"api\":{},\"data\":[{}]}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//user/batch_operations")
  .post(body)
  .build();

Response response = client.newCall(request).execute();
```

```c#
var client = new RestClient("https://app.rakam.io//user/batch_operations");
var request = new RestRequest(Method.POST);
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

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```node
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//user/batch_operations',
  body: { api: {}, data: [ {} ] },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

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

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//user/batch_operations"

payload = "{\"api\":{},\"data\":[{}]}"
response = requests.request("POST", url, data=payload)

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
```curl
curl "app.rakam.io/user/create" -X POST -d @- << EOF 
{
  "id" : "object",
  "api" : { },
  "properties" : "object"
}
EOF
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

```c#
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

```node
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
```curl
curl "app.rakam.io/user/create_segment" -H "master_key: mymaster_key" -X POST -d @- << EOF 
{
  "name" : "str",
  "table_name" : "str",
  "cache_eviction" : "str"
}
EOF
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"name\":\"str\",\"table_name\":\"str\",\"cache_eviction\":\"str\"}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//user/create_segment")
  .post(body)
  .build();

Response response = client.newCall(request).execute();
```

```c#
var client = new RestClient("https://app.rakam.io//user/create_segment");
var request = new RestRequest(Method.POST);
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

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```node
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//user/create_segment',
  body: { name: 'str', table_name: 'str', cache_eviction: 'str' },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

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

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//user/create_segment"

payload = "{\"name\":\"str\",\"table_name\":\"str\",\"cache_eviction\":\"str\"}"
response = requests.request("POST", url, data=payload)

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
```curl
curl "app.rakam.io/user/get" -H "read_key: myread_key" -X POST -d @- << EOF 
{
  "user" : "object"
}
EOF
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"user\":{}}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//user/get")
  .post(body)
  .build();

Response response = client.newCall(request).execute();
```

```c#
var client = new RestClient("https://app.rakam.io//user/get");
var request = new RestRequest(Method.POST);
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

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```node
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//user/get',
  body: { user: {} },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

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

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//user/get"

payload = "{\"user\":{}}"
response = requests.request("POST", url, data=payload)

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
```curl
curl "app.rakam.io/user/get_events" -H "read_key: myread_key" -X POST -d @- << EOF 
{
  "user" : "str"
}
EOF
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"user\":\"str\"}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//user/get_events")
  .post(body)
  .build();

Response response = client.newCall(request).execute();
```

```c#
var client = new RestClient("https://app.rakam.io//user/get_events");
var request = new RestRequest(Method.POST);
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

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```node
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//user/get_events',
  body: { user: 'str' },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

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

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//user/get_events"

payload = "{\"user\":\"str\"}"
response = requests.request("POST", url, data=payload)

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
```curl
curl "app.rakam.io/user/increment_property" -H "master_key: mymaster_key" -X POST -d @- << EOF 
{
  "api" : { },
  "id" : "str",
  "property" : "str",
  "value" : 1.0
}
EOF
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"api\":{},\"id\":\"str\",\"property\":\"str\",\"value\":7}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//user/increment_property")
  .post(body)
  .build();

Response response = client.newCall(request).execute();
```

```c#
var client = new RestClient("https://app.rakam.io//user/increment_property");
var request = new RestRequest(Method.POST);
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

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```node
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//user/increment_property',
  body: { api: {}, id: 'str', property: 'str', value: 7 },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

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

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//user/increment_property"

payload = "{\"api\":{},\"id\":\"str\",\"property\":\"str\",\"value\":7}"
response = requests.request("POST", url, data=payload)

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
```curl
curl "app.rakam.io/user/metadata" -H "read_key: myread_key" -X GET
```

```java
OkHttpClient client = new OkHttpClient();

Request request = new Request.Builder()
  .url("https://app.rakam.io//user/metadata")
  .get()
  .build();

Response response = client.newCall(request).execute();
```

```c#
var client = new RestClient("https://app.rakam.io//user/metadata");
var request = new RestRequest(Method.GET);
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

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```node
var request = require("request");

var options = { method: 'GET', url: 'https://app.rakam.io//user/metadata' };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$request->setRequestUrl('https://app.rakam.io//user/metadata');
$request->setRequestMethod('GET');
$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//user/metadata"

response = requests.request("GET", url)

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
```curl
curl "app.rakam.io/user/search" -H "read_key: myread_key" -X POST -d @- << EOF 
{ }
EOF
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"columns\":[\"str\"],\"filter\":\"str\",\"event_filters\":[{}],\"sorting\":{},\"offset\":\"str\",\"limit\":4}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//user/search")
  .post(body)
  .build();

Response response = client.newCall(request).execute();
```

```c#
var client = new RestClient("https://app.rakam.io//user/search");
var request = new RestRequest(Method.POST);
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

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```node
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//user/search',
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

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->append('{"columns":["str"],"filter":"str","event_filters":[{}],"sorting":{},"offset":"str","limit":4}');

$request->setRequestUrl('https://app.rakam.io//user/search');
$request->setRequestMethod('POST');
$request->setBody($body);

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//user/search"

payload = "{\"columns\":[\"str\"],\"filter\":\"str\",\"event_filters\":[{}],\"sorting\":{},\"offset\":\"str\",\"limit\":4}"
response = requests.request("POST", url, data=payload)

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
```curl
curl "app.rakam.io/user/set_properties" -X POST -d @- << EOF 
{
  "id" : "object",
  "api" : { },
  "properties" : "object"
}
EOF
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

```c#
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

```node
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
```curl
curl "app.rakam.io/user/set_properties_once" -X POST -d @- << EOF 
{
  "id" : "object",
  "api" : { },
  "properties" : "object"
}
EOF
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

```c#
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

```node
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
```curl
curl "app.rakam.io/user/unset_properties" -X POST -d @- << EOF 
{
  "api" : { },
  "id" : "object",
  "properties" : [ "str" ]
}
EOF
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

```c#
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

```node
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

## Apply batch operation
```curl
curl "app.rakam.io/user/action/email/batch" -H "read_key: myread_key" -X POST -d @- << EOF 
{
  "config" : {
    "title" : "str",
    "content" : "str"
  }
}
EOF
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"config\":{}}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//user/action/email/batch")
  .post(body)
  .build();

Response response = client.newCall(request).execute();
```

```c#
var client = new RestClient("https://app.rakam.io//user/action/email/batch");
var request = new RestRequest(Method.POST);
request.AddParameter("undefined", "{\"config\":{}}", ParameterType.RequestBody);
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

	url := "https://app.rakam.io//user/action/email/batch"

	payload := strings.NewReader("{\"config\":{}}")

	req, _ := http.NewRequest("POST", url, payload)

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```node
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//user/action/email/batch',
  body: { config: {} },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->append('{"config":{}}');

$request->setRequestUrl('https://app.rakam.io//user/action/email/batch');
$request->setRequestMethod('POST');
$request->setBody($body);

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//user/action/email/batch"

payload = "{\"config\":{}}"
response = requests.request("POST", url, data=payload)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.rakam.io//user/action/email/batch")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request.body = "{\"config\":{}}"

response = http.request(request)
puts response.read_body
```

> The above command returns JSON structured like this:

```json
1
```

### HTTP Request
`POST /user/action/email/batch`
### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|filter|false|string||
|event_filters|false|[EventFilter](#eventfilter) array||
|config|true|[EmailActionConfig](#emailactionconfig)||


### Responses for status codes
|200|403|
|----|----|
|integer (int64)|[ErrorMessage](#errormessage)|


## Perform action for single user
```curl
curl "app.rakam.io/user/action/email/single" -H "read_key: myread_key" -X POST -d @- << EOF 
{
  "user" : "str",
  "config" : {
    "title" : "str",
    "content" : "str"
  }
}
EOF
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"user\":\"str\",\"config\":{}}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//user/action/email/single")
  .post(body)
  .build();

Response response = client.newCall(request).execute();
```

```c#
var client = new RestClient("https://app.rakam.io//user/action/email/single");
var request = new RestRequest(Method.POST);
request.AddParameter("undefined", "{\"user\":\"str\",\"config\":{}}", ParameterType.RequestBody);
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

	url := "https://app.rakam.io//user/action/email/single"

	payload := strings.NewReader("{\"user\":\"str\",\"config\":{}}")

	req, _ := http.NewRequest("POST", url, payload)

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```node
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//user/action/email/single',
  body: { user: 'str', config: {} },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$body = new http\Message\Body;
$body->append('{"user":"str","config":{}}');

$request->setRequestUrl('https://app.rakam.io//user/action/email/single');
$request->setRequestMethod('POST');
$request->setBody($body);

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//user/action/email/single"

payload = "{\"user\":\"str\",\"config\":{}}"
response = requests.request("POST", url, data=payload)

print(response.text)
```

```ruby
require 'uri'
require 'net/http'

url = URI("https://app.rakam.io//user/action/email/single")

http = Net::HTTP.new(url.host, url.port)
http.use_ssl = true
http.verify_mode = OpenSSL::SSL::VERIFY_NONE

request = Net::HTTP::Post.new(url)
request.body = "{\"user\":\"str\",\"config\":{}}"

response = http.request(request)
puts response.read_body
```

> The above command returns JSON structured like this:

```json
true
```

### HTTP Request
`POST /user/action/email/single`
### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|user|true|string||
|config|true|[EmailActionConfig](#emailactionconfig)||


### Responses for status codes
|200|403|
|----|----|
|boolean|[ErrorMessage](#errormessage)|


# Recipe


Recipe

## Export recipe
```curl
curl "app.rakam.io/recipe/export" -H "master_key: mymaster_key" -X GET
```

```java
OkHttpClient client = new OkHttpClient();

Request request = new Request.Builder()
  .url("https://app.rakam.io//recipe/export")
  .get()
  .addHeader("accept", "str")
  .build();

Response response = client.newCall(request).execute();
```

```c#
var client = new RestClient("https://app.rakam.io//recipe/export");
var request = new RestRequest(Method.GET);
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

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```node
var request = require("request");

var options = { method: 'GET',
  url: 'https://app.rakam.io//recipe/export',
  headers: { accept: 'str' } };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$request->setRequestUrl('https://app.rakam.io//recipe/export');
$request->setRequestMethod('GET');
$request->setHeaders(array(
  'accept' => 'str'
));

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//recipe/export"

headers = {'accept': 'str'}

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
```curl
curl "app.rakam.io/recipe/install" -H "master_key: mymaster_key" -X POST
```

```java
OkHttpClient client = new OkHttpClient();

Request request = new Request.Builder()
  .url("https://app.rakam.io//recipe/install")
  .post(null)
  .build();

Response response = client.newCall(request).execute();
```

```c#
var client = new RestClient("https://app.rakam.io//recipe/install");
var request = new RestRequest(Method.POST);
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

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```node
var request = require("request");

var options = { method: 'POST', url: 'https://app.rakam.io//recipe/install' };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$request->setRequestUrl('https://app.rakam.io//recipe/install');
$request->setRequestMethod('POST');
$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//recipe/install"

response = requests.request("POST", url)

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
```curl
curl "app.rakam.io/admin/configurations" -H "master_key: mymaster_key" -X GET
```

```java
OkHttpClient client = new OkHttpClient();

Request request = new Request.Builder()
  .url("https://app.rakam.io//admin/configurations")
  .get()
  .build();

Response response = client.newCall(request).execute();
```

```c#
var client = new RestClient("https://app.rakam.io//admin/configurations");
var request = new RestRequest(Method.GET);
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

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```node
var request = require("request");

var options = { method: 'GET',
  url: 'https://app.rakam.io//admin/configurations' };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$request->setRequestUrl('https://app.rakam.io//admin/configurations');
$request->setRequestMethod('GET');
$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//admin/configurations"

response = requests.request("GET", url)

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
```curl
curl "app.rakam.io/admin/event_mappers" -H "master_key: mymaster_key" -X GET
```

```java
OkHttpClient client = new OkHttpClient();

Request request = new Request.Builder()
  .url("https://app.rakam.io//admin/event_mappers")
  .get()
  .build();

Response response = client.newCall(request).execute();
```

```c#
var client = new RestClient("https://app.rakam.io//admin/event_mappers");
var request = new RestRequest(Method.GET);
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

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```node
var request = require("request");

var options = { method: 'GET',
  url: 'https://app.rakam.io//admin/event_mappers' };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$request->setRequestUrl('https://app.rakam.io//admin/event_mappers');
$request->setRequestMethod('GET');
$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//admin/event_mappers"

response = requests.request("GET", url)

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
```curl
curl "app.rakam.io/admin/lock_key" -H "master_key: mymaster_key" -X POST -d @- << EOF 
{ }
EOF
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"lock_key\":\"str\"}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//admin/lock_key")
  .post(body)
  .build();

Response response = client.newCall(request).execute();
```

```c#
var client = new RestClient("https://app.rakam.io//admin/lock_key");
var request = new RestRequest(Method.POST);
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

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```node
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//admin/lock_key',
  body: { lock_key: 'str' },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

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

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//admin/lock_key"

payload = "{\"lock_key\":\"str\"}"
response = requests.request("POST", url, data=payload)

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
```curl
curl "app.rakam.io/admin/types" -H "master_key: mymaster_key" -X GET
```

```java
OkHttpClient client = new OkHttpClient();

Request request = new Request.Builder()
  .url("https://app.rakam.io//admin/types")
  .get()
  .build();

Response response = client.newCall(request).execute();
```

```c#
var client = new RestClient("https://app.rakam.io//admin/types");
var request = new RestRequest(Method.GET);
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

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```node
var request = require("request");

var options = { method: 'GET', url: 'https://app.rakam.io//admin/types' };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$request->setRequestUrl('https://app.rakam.io//admin/types');
$request->setRequestMethod('GET');
$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//admin/types"

response = requests.request("GET", url)

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
```curl
curl "app.rakam.io/project/check-api-keys" -X POST -d @- << EOF 
{
  "keys" : [ { } ],
  "project" : "str"
}
EOF
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

```c#
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

```node
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
```curl
curl "app.rakam.io/project/collection" -H "read_key: myread_key" -X POST
```

```java
OkHttpClient client = new OkHttpClient();

Request request = new Request.Builder()
  .url("https://app.rakam.io//project/collection")
  .post(null)
  .build();

Response response = client.newCall(request).execute();
```

```c#
var client = new RestClient("https://app.rakam.io//project/collection");
var request = new RestRequest(Method.POST);
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

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```node
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//project/collection' };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$request->setRequestUrl('https://app.rakam.io//project/collection');
$request->setRequestMethod('POST');
$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//project/collection"

response = requests.request("POST", url)

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
```curl
curl "app.rakam.io/project/create" -X POST -d @- << EOF 
{
  "name" : "str"
}
EOF
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

```c#
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

```node
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
```curl
curl "app.rakam.io/project/create-api-keys" -H "master_key: mymaster_key" -X POST
```

```java
OkHttpClient client = new OkHttpClient();

Request request = new Request.Builder()
  .url("https://app.rakam.io//project/create-api-keys")
  .post(null)
  .build();

Response response = client.newCall(request).execute();
```

```c#
var client = new RestClient("https://app.rakam.io//project/create-api-keys");
var request = new RestRequest(Method.POST);
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

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```node
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//project/create-api-keys' };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$request->setRequestUrl('https://app.rakam.io//project/create-api-keys');
$request->setRequestMethod('POST');
$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//project/create-api-keys"

response = requests.request("POST", url)

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
```curl
curl "app.rakam.io/project/delete" -H "master_key: mymaster_key" -X DELETE
```

```java
OkHttpClient client = new OkHttpClient();

Request request = new Request.Builder()
  .url("https://app.rakam.io//project/delete")
  .delete(null)
  .build();

Response response = client.newCall(request).execute();
```

```c#
var client = new RestClient("https://app.rakam.io//project/delete");
var request = new RestRequest(Method.DELETE);
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

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```node
var request = require("request");

var options = { method: 'DELETE',
  url: 'https://app.rakam.io//project/delete' };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$request->setRequestUrl('https://app.rakam.io//project/delete');
$request->setRequestMethod('DELETE');
$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//project/delete"

response = requests.request("DELETE", url)

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
```curl
curl "app.rakam.io/project/list" -H "read_key: myread_key" -X POST -d @- << EOF 
{ }
EOF
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"lock_key\":\"str\"}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//project/list")
  .post(body)
  .build();

Response response = client.newCall(request).execute();
```

```c#
var client = new RestClient("https://app.rakam.io//project/list");
var request = new RestRequest(Method.POST);
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

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```node
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//project/list',
  body: { lock_key: 'str' },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

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

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//project/list"

payload = "{\"lock_key\":\"str\"}"
response = requests.request("POST", url, data=payload)

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
```curl
curl "app.rakam.io/project/revoke-api-keys" -X POST -d @- << EOF 
{
  "project" : "str",
  "master_key" : "str"
}
EOF
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

```c#
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

```node
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
```curl
curl "app.rakam.io/project/schema" -H "read_key: myread_key" -X POST -d @- << EOF 
{ }
EOF
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"names\":[\"str\"]}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//project/schema")
  .post(body)
  .build();

Response response = client.newCall(request).execute();
```

```c#
var client = new RestClient("https://app.rakam.io//project/schema");
var request = new RestRequest(Method.POST);
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

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```node
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//project/schema',
  body: { names: [ 'str' ] },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

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

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//project/schema"

payload = "{\"names\":[\"str\"]}"
response = requests.request("POST", url, data=payload)

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
```curl
curl "app.rakam.io/project/schema/add" -H "master_key: mymaster_key" -X POST -d @- << EOF 
{
  "collection" : "str",
  "fields" : [ {
    "name" : "str",
    "type" : "STRING"
  } ]
}
EOF
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"collection\":\"str\",\"fields\":[{}]}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//project/schema/add")
  .post(body)
  .build();

Response response = client.newCall(request).execute();
```

```c#
var client = new RestClient("https://app.rakam.io//project/schema/add");
var request = new RestRequest(Method.POST);
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

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```node
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//project/schema/add',
  body: { collection: 'str', fields: [ {} ] },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

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

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//project/schema/add"

payload = "{\"collection\":\"str\",\"fields\":[{}]}"
response = requests.request("POST", url, data=payload)

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
```curl
curl "app.rakam.io/project/schema/add/custom" -H "master_key: mymaster_key" -X POST -d @- << EOF 
{
  "collection" : "str",
  "schema_type" : "AVRO",
  "schema" : "str"
}
EOF
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"collection\":\"str\",\"schema_type\":\"AVRO\",\"schema\":\"str\"}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//project/schema/add/custom")
  .post(body)
  .build();

Response response = client.newCall(request).execute();
```

```c#
var client = new RestClient("https://app.rakam.io//project/schema/add/custom");
var request = new RestRequest(Method.POST);
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

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```node
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//project/schema/add/custom',
  body: { collection: 'str', schema_type: 'AVRO', schema: 'str' },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

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

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//project/schema/add/custom"

payload = "{\"collection\":\"str\",\"schema_type\":\"AVRO\",\"schema\":\"str\"}"
response = requests.request("POST", url, data=payload)

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
```curl
curl "app.rakam.io/project/stats" -X POST -d @- << EOF 
[ "object" ]
EOF
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

```c#
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

```node
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
```curl
curl "app.rakam.io/event/batch" -X POST -d @- << EOF 
{
  "api" : { },
  "events" : [ {
    "collection" : "str",
    "api" : { },
    "properties" : "object"
  } ]
}
EOF
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

```c#
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

```node
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
```curl
curl "app.rakam.io/event/bulk" -X POST -d @- << EOF 
{
  "api" : { },
  "events" : [ {
    "collection" : "str",
    "api" : { },
    "properties" : "object"
  } ]
}
EOF
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

```c#
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

```node
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



Bulk API requires master_key as api key and designed to handle large value of data. The endpoint also accepts application/avro and text/csv formats. You need need to set 'collection' and 'master_key' query parameters if the content-type is not application/json.

## Collect bulk events from remote
```curl
curl "app.rakam.io/event/bulk/remote" -X POST -d @- << EOF 
{
  "collection" : "str",
  "urls" : [ "str" ],
  "type" : "AVRO"
}
EOF
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

```c#
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

```node
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
```curl
curl "app.rakam.io/event/collect" -X POST -d @- << EOF 
{
  "collection" : "str",
  "api" : { },
  "properties" : "object"
}
EOF
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

```c#
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

```node
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
```curl
curl "app.rakam.io/event/copy" -X POST -d @- << EOF 
{
  "api" : { },
  "events" : [ {
    "collection" : "str",
    "api" : { },
    "properties" : "object"
  } ]
}
EOF
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

```c#
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

```node
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
```curl
curl "app.rakam.io/query/execute" -H "read_key: myread_key" -X POST -d @- << EOF 
{
  "query" : "str"
}
EOF
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"query\":\"str\"}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//query/execute")
  .post(body)
  .build();

Response response = client.newCall(request).execute();
```

```c#
var client = new RestClient("https://app.rakam.io//query/execute");
var request = new RestRequest(Method.POST);
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

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```node
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//query/execute',
  body: { query: 'str' },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

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

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//query/execute"

payload = "{\"query\":\"str\"}"
response = requests.request("POST", url, data=payload)

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


### Responses for status codes
|200|403|
|----|----|
|[ResponseQueryResult](#responsequeryresult)|[ErrorMessage](#errormessage)|


## Explain query
```curl
curl "app.rakam.io/query/explain" -H "read_key: myread_key" -X POST -d @- << EOF 
{
  "query" : "str"
}
EOF
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"query\":\"str\"}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//query/explain")
  .post(body)
  .build();

Response response = client.newCall(request).execute();
```

```c#
var client = new RestClient("https://app.rakam.io//query/explain");
var request = new RestRequest(Method.POST);
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

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```node
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//query/explain',
  body: { query: 'str' },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

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

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//query/explain"

payload = "{\"query\":\"str\"}"
response = requests.request("POST", url, data=payload)

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
```curl
curl "app.rakam.io/query/metadata" -H "read_key: myread_key" -X POST -d @- << EOF 
{
  "query" : "str"
}
EOF
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"query\":\"str\"}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//query/metadata")
  .post(body)
  .build();

Response response = client.newCall(request).execute();
```

```c#
var client = new RestClient("https://app.rakam.io//query/metadata");
var request = new RestRequest(Method.POST);
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

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```node
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//query/metadata',
  body: { query: 'str' },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

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

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//query/metadata"

payload = "{\"query\":\"str\"}"
response = requests.request("POST", url, data=payload)

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

## Create view
```curl
curl "app.rakam.io/materialized-view/create" -H "master_key: mymaster_key" -X POST -d @- << EOF 
{
  "table_name" : "str",
  "name" : "str",
  "query" : "str"
}
EOF
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"table_name\":\"str\",\"name\":\"str\",\"query\":\"str\"}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//materialized-view/create")
  .post(body)
  .build();

Response response = client.newCall(request).execute();
```

```c#
var client = new RestClient("https://app.rakam.io//materialized-view/create");
var request = new RestRequest(Method.POST);
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

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```node
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//materialized-view/create',
  body: { table_name: 'str', name: 'str', query: 'str' },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

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

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//materialized-view/create"

payload = "{\"table_name\":\"str\",\"name\":\"str\",\"query\":\"str\"}"
response = requests.request("POST", url, data=payload)

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
|options|false|object||


### Responses for status codes
|200|403|
|----|----|
|[SuccessMessage](#successmessage)|[ErrorMessage](#errormessage)|


## Delete materialized view
```curl
curl "app.rakam.io/materialized-view/delete" -H "master_key: mymaster_key" -X POST -d @- << EOF 
{
  "table_name" : "str"
}
EOF
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"table_name\":\"str\"}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//materialized-view/delete")
  .post(body)
  .build();

Response response = client.newCall(request).execute();
```

```c#
var client = new RestClient("https://app.rakam.io//materialized-view/delete");
var request = new RestRequest(Method.POST);
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

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```node
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//materialized-view/delete',
  body: { table_name: 'str' },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

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

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//materialized-view/delete"

payload = "{\"table_name\":\"str\"}"
response = requests.request("POST", url, data=payload)

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
```curl
curl "app.rakam.io/materialized-view/get" -H "read_key: myread_key" -X POST -d @- << EOF 
{
  "table_name" : "str"
}
EOF
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"table_name\":\"str\"}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//materialized-view/get")
  .post(body)
  .build();

Response response = client.newCall(request).execute();
```

```c#
var client = new RestClient("https://app.rakam.io//materialized-view/get");
var request = new RestRequest(Method.POST);
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

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```node
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//materialized-view/get',
  body: { table_name: 'str' },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

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

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//materialized-view/get"

payload = "{\"table_name\":\"str\"}"
response = requests.request("POST", url, data=payload)

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
```curl
curl "app.rakam.io/materialized-view/list" -H "read_key: myread_key" -X POST
```

```java
OkHttpClient client = new OkHttpClient();

Request request = new Request.Builder()
  .url("https://app.rakam.io//materialized-view/list")
  .post(null)
  .build();

Response response = client.newCall(request).execute();
```

```c#
var client = new RestClient("https://app.rakam.io//materialized-view/list");
var request = new RestRequest(Method.POST);
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

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```node
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//materialized-view/list' };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$request->setRequestUrl('https://app.rakam.io//materialized-view/list');
$request->setRequestMethod('POST');
$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//materialized-view/list"

response = requests.request("POST", url)

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
```curl
curl "app.rakam.io/materialized-view/schema" -H "read_key: myread_key" -X POST -d @- << EOF 
{ }
EOF
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"names\":[\"str\"]}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//materialized-view/schema")
  .post(body)
  .build();

Response response = client.newCall(request).execute();
```

```c#
var client = new RestClient("https://app.rakam.io//materialized-view/schema");
var request = new RestRequest(Method.POST);
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

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```node
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//materialized-view/schema',
  body: { names: [ 'str' ] },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

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

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//materialized-view/schema"

payload = "{\"names\":[\"str\"]}"
response = requests.request("POST", url, data=payload)

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
```curl
curl "app.rakam.io/continuous-query/create" -H "master_key: mymaster_key" -X POST -d @- << EOF 
{
  "continuous_query" : {
    "name" : "str",
    "query" : "str"
  }
}
EOF
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"continuous_query\":{}}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//continuous-query/create")
  .post(body)
  .build();

Response response = client.newCall(request).execute();
```

```c#
var client = new RestClient("https://app.rakam.io//continuous-query/create");
var request = new RestRequest(Method.POST);
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

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```node
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//continuous-query/create',
  body: { continuous_query: {} },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

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

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//continuous-query/create"

payload = "{\"continuous_query\":{}}"
response = requests.request("POST", url, data=payload)

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
```curl
curl "app.rakam.io/continuous-query/delete" -H "master_key: mymaster_key" -X POST -d @- << EOF 
{
  "table_name" : "str"
}
EOF
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"table_name\":\"str\"}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//continuous-query/delete")
  .post(body)
  .build();

Response response = client.newCall(request).execute();
```

```c#
var client = new RestClient("https://app.rakam.io//continuous-query/delete");
var request = new RestRequest(Method.POST);
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

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```node
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//continuous-query/delete',
  body: { table_name: 'str' },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

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

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//continuous-query/delete"

payload = "{\"table_name\":\"str\"}"
response = requests.request("POST", url, data=payload)

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
```curl
curl "app.rakam.io/continuous-query/get" -H "read_key: myread_key" -X POST -d @- << EOF 
{
  "table_name" : "str"
}
EOF
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"table_name\":\"str\"}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//continuous-query/get")
  .post(body)
  .build();

Response response = client.newCall(request).execute();
```

```c#
var client = new RestClient("https://app.rakam.io//continuous-query/get");
var request = new RestRequest(Method.POST);
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

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```node
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//continuous-query/get',
  body: { table_name: 'str' },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

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

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//continuous-query/get"

payload = "{\"table_name\":\"str\"}"
response = requests.request("POST", url, data=payload)

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
```curl
curl "app.rakam.io/continuous-query/list" -H "read_key: myread_key" -X POST
```

```java
OkHttpClient client = new OkHttpClient();

Request request = new Request.Builder()
  .url("https://app.rakam.io//continuous-query/list")
  .post(null)
  .build();

Response response = client.newCall(request).execute();
```

```c#
var client = new RestClient("https://app.rakam.io//continuous-query/list");
var request = new RestRequest(Method.POST);
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

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```node
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//continuous-query/list' };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

```

```php
<?php

$client = new http\Client;
$request = new http\Client\Request;

$request->setRequestUrl('https://app.rakam.io//continuous-query/list');
$request->setRequestMethod('POST');
$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//continuous-query/list"

response = requests.request("POST", url)

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
```curl
curl "app.rakam.io/continuous-query/schema" -H "read_key: myread_key" -X POST -d @- << EOF 
{ }
EOF
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"names\":[\"str\"]}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//continuous-query/schema")
  .post(body)
  .build();

Response response = client.newCall(request).execute();
```

```c#
var client = new RestClient("https://app.rakam.io//continuous-query/schema");
var request = new RestRequest(Method.POST);
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

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```node
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//continuous-query/schema',
  body: { names: [ 'str' ] },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

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

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//continuous-query/schema"

payload = "{\"names\":[\"str\"]}"
response = requests.request("POST", url, data=payload)

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
```curl
curl "app.rakam.io/continuous-query/test" -H "read_key: myread_key" -X POST -d @- << EOF 
{
  "query" : "str"
}
EOF
```

```java
OkHttpClient client = new OkHttpClient();

MediaType mediaType = MediaType.parse("application/json");
RequestBody body = RequestBody.create(mediaType, "{\"query\":\"str\"}");
Request request = new Request.Builder()
  .url("https://app.rakam.io//continuous-query/test")
  .post(body)
  .build();

Response response = client.newCall(request).execute();
```

```c#
var client = new RestClient("https://app.rakam.io//continuous-query/test");
var request = new RestRequest(Method.POST);
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

	res, _ := http.DefaultClient.Do(req)

	defer res.Body.Close()
	body, _ := ioutil.ReadAll(res.Body)

	fmt.Println(res)
	fmt.Println(string(body))

}
```

```node
var request = require("request");

var options = { method: 'POST',
  url: 'https://app.rakam.io//continuous-query/test',
  body: { query: 'str' },
  json: true };

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});

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

$client->enqueue($request)->send();
$response = $client->getResponse();

echo $response->getBody();
```

```python
import requests

url = "https://app.rakam.io//continuous-query/test"

payload = "{\"query\":\"str\"}"
response = requests.request("POST", url, data=payload)

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


### RealTimeQueryResult
|name|description|required|schema|default|
|----|----|----|----|----|
|start||false|integer (int64)||
|end||false|integer (int64)||
|result||false|object||


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
|column||true|string||
|aggregation||true|enum (COUNT, COUNT_UNIQUE, SUM, MINIMUM, MAXIMUM, AVERAGE, APPROXIMATE_UNIQUE)||


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


### EmailActionConfig
|name|description|required|schema|default|
|----|----|----|----|----|
|title||true|string||
|content||true|string||
|columnName||false|string||
|defaultValues||false|object||
|richText||false|boolean||


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
|checksum|Optional checksum for verify the body content|false|string||


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


