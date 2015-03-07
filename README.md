# client-websocket
## Overview
Documentation for the DeepBot Client WebSocket Library

## Connection

The DeepBot WebSocket server runs on port 3337. Simply connect to this server using any websocket module to establish a connection.

To authenticate as an API consumer, you will need the client API secret. This can be found in the master settings.

Responses will always be json objects in the following format:
```
{
	"function": "",
	"param": "",
	"msg": ""
}
```

To authenticate, send the below message.

## `"api|register|{secret}"`

A successful  would be a json object.
```json
{
	"function": "register",
	"param": "register",
	"msg": "success"
}
```
##Users

## `api|get_user|:user`

```json
{
	"function": "get_user",
	"param": "expertsonline",
	"msg": {
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

## `api|get_points|:user`

```json
{
	"function": "get_points",
	"param": "expertsonline",
	"msg": "720.00"
}
```

## `api|get_hours|:user`

```json
{
	"function": "get_hours",
	"param": "expertsonline",
	"msg": "218.75"
}
```

## `api|get_rank|:user`

```json
{
	"function": "get_rank",
	"param": "expertsonline",
	"msg": "Sergeant - Star 2"
}
```

## `api|set_points|:user|:points`

```json
{
	"function": "set_points",
	"param": "expertsonline",
	"msg": "success"
}
```

## `api|add_points|:user|:points`

```json
{
	"function": "add_points",
	"param": "expertsonline",
	"msg": "success"
}
```
## `api|del_points|:user|:points`

```json
{
	"function": "del_points",
	"param": "expertsonline",
	"msg": "success"
}
```
## `api|add_to_escrow|:user|:points`

```json
{
	"function": "add_to_escrow",
	"param": "expertsonline",
	"msg": "success" or "Not enough points" or "points should be a positive number" or "user not found"
}
```
## `api|commit_user_escrow|:user`

```json
{
	"function": "commit_user_escrow",
	"param": "expertsonline",
	"msg": "success" or "No points in escrow" or "user not found"
}
```
## `api|cancel_escrow|:user`

<table>
    <thead>
        <tr>
            <th>Name</th>
            <th width="50">Type</th>
            <th width=100%>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><code>:user</code></td>
            <td>string</td>
            <td>username or 'all'</td>
        </tr>
    </tbody>
</table>

```json
{
	"function": "cancel_escrow",
	"param": "expertsonline",
	"msg": "success" or "No points in escrow" or "user not found"
}
```
## `api|set_vip|:user|:level|:days`

<table>
    <thead>
        <tr>
            <th>Name</th>
            <th width="50">Type</th>
            <th width=100%>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td><code>:level</code></td>
            <td>integer</td>
            <td>Desired VIP Level. 0 or 10 = Normal user. 1 = VIP Bronze, 2 = Silver, 3 = Gold</td>
        </tr>
        <tr>
            <td><code>:days</code></td>
            <td>integer</td>
            <td>Number of days to add to VIP Expiry.</td>
        </tr>
    </tbody>
</table>

```json
{
	"function": "set_vip",
	"param": "expertsonline",
	"msg": "success"
}
```

