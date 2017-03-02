---
title: API Reference
language_tabs:
  - curl
  - null
toc_footers:
 - <a href='#'>Sign Up for a Developer Key</a>
includes:
    - errors
search: true
---
# Introduction

```
We have language bindings in html! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.
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

> The above command returns JSON structured like this:

```json
1
```

### HTTP Request
`POST /user/create`
### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|id|true|object|The value may be a string or a numeric value.|
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

> The above command returns JSON structured like this:

```json
1
```

### HTTP Request
`POST /user/set_properties`
### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|id|true|object|The value may be a string or a numeric value.|
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

> The above command returns JSON structured like this:

```json
1
```

### HTTP Request
`POST /user/set_properties_once`
### Body Parameters
|Parameter|Required|Type|Description|
|----|----|----|----|
|id|true|object|The value may be a string or a numeric value.|
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
|id|The value may be a string or a numeric value.|true|object||
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


