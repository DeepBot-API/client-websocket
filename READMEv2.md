# client-websocket
## Overview
Documentation for the DeepBot JSON Client WebSocket Library added in version 0.11.5

## Connection

The DeepBot WebSocket server runs on port 3337 on the machine that is running DeepBot. Simply connect to this server using any websocket module to establish a connection.

To authenticate as an API consumer, you will need the client API secret. This can be found in the master settings on DeepBot.

Responses from the API will always be json objects. You can add a nonce property that will be returned back to you to identify the request.


To authenticate as an API consumer, send the below message. This is needed for most functions.

## register
```json
{
	"module": "api",
	"function": "register",
	"secret": "<DB API Secret from Master Settings>"
}
```

A successful authentication response would be a json object.
```json
{
	"function": "register",
	"msg": "success"
}
```
Failed authentication attempts will return an error message.
```json
{
	"function": "register",
	"msg": "incorrect api secret",
	"error": true
}
```

##Users

## get_user

Request:
```json
{
	"module": "api",
	"function": "get_user",
	"user": "username"
}
```

Response:
```json
{
	"function": "get_user",
	"user": {
		"user": "expertsonline",
		"points": 720.0,
		"watch_time": 13125.0,
		"vip": 10,
		"mod": 5,
		"join_date": "2014-07-05T18:09:10.3156084Z",
		"last_seen": "2015-03-01T04:17:09.545139Z",
		"vip_expiry": "2014-12-09T00:00:00+08:00"
	}
}
```

## add_points

Request:
```json
{
	"module": "api",
	"function": "add_points",
	"user": "username",
	"points": 2 
}
```
Points to be added or removed must be a valid integer

Response:
```json
{
	"function": "add_points",
	"user": "username",
	"message": "success",
	"old_points": 12,
	"new_points": 14
}
```
