# client-websocket
## Overview
Documentation for the DeepBot Client WebSocket Library added in version 0.7.0

## Connection

The DeepBot WebSocket server runs on port 3337 on the machine that is running DeepBot. Simply connect to this server using any websocket module to establish a connection.

To authenticate as an API consumer, you will need the client API secret. This can be found in the master settings on DeepBot.

Responses from the API will always be json objects in the following format:
```
{
	"function": "",
	"param": "",
	"msg": ""
}
```

To authenticate as an API consumer, send the below message. This is needed for most functions.

## `"api|register|{secret}"`

A successful authentication response would be a json object.
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

## `api|get_users|:offset|:limit`
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
            <td><code>:offset</code></td>
            <td>integer</td>
            <td>optional. (Default = 0)</td>
        </tr>
        <tr>
            <td><code>:limit</code></td>
            <td>integer</td>
            <td>optional.(Default = 100)</td>
        </tr>
    </tbody>
</table>

```json
{
	"function": "get_users",
	"param": "users",
	"msg": {
		{
			"user": "tom",
			"points": 720.0,
			"watch_time": 13125.0,
			"vip": 10,
			"mod": 5,
			"join_date": "2014-07-05T18:09:10.3156084Z",
			"last_seen": "2015-03-01T04:17:09.545139Z",
			"vip_expiry": "2014-12-09T00:00:00+08:00"
		},
		{
			"user": "expertsonline",
			"points": 320.0,
			"watch_time": 3125.0,
			"vip": 10,
			"mod": 5,
			"join_date": "2014-07-05T18:09:10.3156084Z",
			"last_seen": "2015-03-01T04:17:09.545139Z",
			"vip_expiry": "2014-12-09T00:00:00+08:00"
		},
		{
			"user": "jon",
			"points": 120.0,
			"watch_time": 3125.0,
			"vip": 10,
			"mod": 5,
			"join_date": "2014-07-05T18:09:10.3156084Z",
			"last_seen": "2015-03-01T04:17:09.545139Z",
			"vip_expiry": "2014-12-09T00:00:00+08:00"
		}
	}
}
```

## `api|get_top_users|:offset|:limit`
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
            <td><code>:offset</code></td>
            <td>integer</td>
            <td>optional. (Default = 0)</td>
        </tr>
        <tr>
            <td><code>:limit</code></td>
            <td>integer</td>
            <td>optional.(Default = 100)</td>
        </tr>
    </tbody>
</table>

Users sorted by decending order of points.
```json
{
	"function": "get_top_users",
	"param": "users",
	"msg": {
		{
			"user": "tom",
			"points": 720.0,
			"watch_time": 13125.0,
			"vip": 10,
			"mod": 5,
			"join_date": "2014-07-05T18:09:10.3156084Z",
			"last_seen": "2015-03-01T04:17:09.545139Z",
			"vip_expiry": "2014-12-09T00:00:00+08:00"
		},
		{
			"user": "expertsonline",
			"points": 320.0,
			"watch_time": 3125.0,
			"vip": 10,
			"mod": 5,
			"join_date": "2014-07-05T18:09:10.3156084Z",
			"last_seen": "2015-03-01T04:17:09.545139Z",
			"vip_expiry": "2014-12-09T00:00:00+08:00"
		},
		{
			"user": "jon",
			"points": 120.0,
			"watch_time": 3125.0,
			"vip": 10,
			"mod": 5,
			"join_date": "2014-07-05T18:09:10.3156084Z",
			"last_seen": "2015-03-01T04:17:09.545139Z",
			"vip_expiry": "2014-12-09T00:00:00+08:00"
		}
	}
}
```

## `api|get_users_count`

```json
{
	"function": "get_users_count",
	"param": "users",
	"msg": "250"
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
## `api|del_points|:user|:points|:fail_if_insufficient`

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
            <td>User to remove points from</td>
        </tr>
        <tr>
            <td><code>:points</code></td>
            <td>integer</td>
            <td>Amount of points to remove.</td>
        </tr>
        <tr>
            <td><code>:fail_if_insufficient</code></td>
            <td>0 or 1</td>
            <td>Optional (Default = 0). If set to 1, fail when user does not have enough points. If set to 0, bring user down to 0.</td>
        </tr>
    </tbody>
</table>

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

## `api|get_song_count`

```json
{
	"function": "get_song_count",
	"param": "songs",
	"msg": "250"
}
```

## `api|get_command_count`

```json
{
	"function": "get_command_count",
	"param": "commands",
	"msg": "250"
}
```

## `api|get_quote_count`

```json
{
	"function": "get_quote_count",
	"param": "quote",
	"msg": "250"
}
```

## `api|get_songs|:offset|:limit`
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
            <td><code>:offset</code></td>
            <td>integer</td>
            <td>optional (Default = 0)</td>
        </tr>
        <tr>
            <td><code>:limit</code></td>
            <td>integer</td>
            <td>optional (Default = 100)</td>
        </tr>
    </tbody>
</table>

```json
{  
   "function":"get_songs",
   "param":"songs",
   "msg":[  
      {  
         "songPosition":"2",
         "songID":"8d7F5ikbajU",
         "songName":"Study Music Project - Ever Eternity (Study Music Concentration)",
         "songDuration":"541",
         "requestedBy":"expertsonline"
      },
      {  
         "songPosition":"3",
         "songID":"V6HB_6ltwSA",
         "songName":"We Could Happen by AJ Rafael (Lyrics Video)",
         "songDuration":"216",
         "requestedBy":"expertsonline"
      },
      {  
         "songPosition":"4",
         "songID":"7hKeiIwypE0",
         "songName":"Krewella",
         "songDuration":"191",
         "requestedBy":"expertsonline"
      }]
}
```


## `api|get_quotes|:offset|:limit`
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
            <td><code>:offset</code></td>
            <td>integer</td>
            <td>optional (Default = 0)</td>
        </tr>
        <tr>
            <td><code>:limit</code></td>
            <td>integer</td>
            <td>optional (Default = 100)</td>
        </tr>
    </tbody>
</table>

```json
{  
   "function":"get_quotes",
   "param":"quotes",
   "msg":[  
      {  
         "quoteID":"1",
         "quotedUser":"mercury3rd",
         "Quote":"This is a test quote",
         "addedOn":"2015-10-28T19:40:19.3655576+08:00",
         "addedBy":"doktorpeng",
         "lastDisplayed":"2015-10-28T20:55:14.7852188+08:00"
      },
      {  
         "quoteID":"2",
         "quotedUser":"mercury3rd",
         "Quote":"This is another test quote",
         "addedOn":"2015-10-28T19:41:12.6709951+08:00",
         "addedBy":"doktorpeng",
         "lastDisplayed":"2015-10-28T20:55:57.0029763+08:00"
      }
   ]
}
```

## `api|get_commands|:offset|:limit`
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
            <td><code>:offset</code></td>
            <td>integer</td>
            <td>optional (Default = 0)</td>
        </tr>
        <tr>
            <td><code>:limit</code></td>
            <td>integer</td>
            <td>optional (Default = 100)</td>
        </tr>
    </tbody>
</table>

```json
{  
   "function":"get_commands",
   "param":"commands",
   "msg":[  
      {  
         "command":"!test",
         "group":"",
         "status":true,
         "message":"!test2 @target@ @editpoints@[expertsonline|10]",
         "access":"1",
         "channelUseAllowed":true,
         "whisperUseAllowed":true,
         "showInList":false
      },
      {  
         "command":"!test2",
         "group":"",
         "status":true,
         "message":"@target@",
         "access":"1",
         "channelUseAllowed":true,
         "whisperUseAllowed":true,
         "showInList":true
      },
      {  
         "command":"!test3",
         "group":"",
         "status":true,
         "message":"It's an issue.",
         "access":"1",
         "channelUseAllowed":true,
         "whisperUseAllowed":true,
         "showInList":true
      },
      {  
         "command":"!playgame",
         "group":"Game",
         "status":true,
         "message":"Play Game",
         "access":"1",
         "channelUseAllowed":true,
         "whisperUseAllowed":true,
         "showInList":true
      },
      {  
         "command":"!22",
         "group":"Game2",
         "status":true,
         "message":"22",
         "access":"1",
         "channelUseAllowed":true,
         "whisperUseAllowed":true,
         "showInList":true
      }
   ]
}
```

## `api|get_command|:commandName`

```json
{  
   "function":"get_command",
   "param":"!apitest",
   "msg":{  
      "command":"!apitest",
      "group":"api",
      "status":true,
      "message":"This is a test API message",
      "access":1,
      "channelUseAllowed":true,
      "whisperUseAllowed":true,
      "showInList":true,
      "cooldown":5,
      "sound":"F:\\DeepBot\\NewSub1.wav",
      "volume":100,
      "runAs":0,
      "widgetName":"APIWidget",
      "widgetTitle":"Test Widget",
      "widgetMessage":"@target@",
      "widgetImage":"www.twitch.tv/Kappa.png",
      "widgetAnimMode":1,
      "accessDeniedMessage":"Boo Hoo ... go away!",
      "insufficientPointsMessage":"You are too cheap for me ... go away!",
      "costAll":0,
      "costViewer":100,
      "costStreamer":0,
      "costMods":40,
      "costVIPBronze":80,
      "costVIPSilver":70,
      "costVIPGold":50,
      "OBSAction":3,
      "OBSTarget":"ShowCam",
      "chainCommand":"!chainCmd",
      "chainDelay":0,
      "chainAdminAccess":false,
      "counter":0,
      "countdown":"2016-05-07T11:58:26.6088803+08:00",
      "modVIPIfViewer":2,
      "modVIPIfBronze":3,
      "modVIPIfSilver":4,
      "modVIPIfGold":0,
      "numVIPDaysAdd":30
   }
}
```
