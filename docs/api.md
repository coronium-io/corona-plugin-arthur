# mod_arthur

After you've set up your [OAuth.io](https://oauth.io) account and first oauth application, in Corona SDK, add the __mod_arthur__ module. You can [download the module here](https://github.com/develephant/mod_arthur/archive/master.zip). Place the __arthur__ folder in your project directory.

```lua
local Arthur = require("arthur.mod_arthur")
```

__Returns:__ The main Arthur module.

---

## .init

Initialize the __mod_arthur__ module with your [oauth.io](https://oauth.io) credentials for the app.


Parameter|Description|Type|Requried
---------|:----------|----|--------
app_key|The OAuth.io public application key.|String|Yes

__Returns:__

Nothing.

__Example:__

```lua
Arthur.init( '<public_app_key' )
```

---

## .api

Create a new API Object from one of your app providers configured on [oauth.io](https://oauth.io).

Parameter|Description|Type|Requried
---------|:----------|----|--------
provider|The OAuth.io provider name to connect to.|String|Yes
parameters|Additional provider parameters or `nil`.|Table|Yes
ready_callback|Callback when tokens have been obtained from the provider.|Function|Yes

__Returns:__

An API object that can be used with the __API Object methods__ below after the callback fires, allowing you to interact with the connected provider.

__Example:__

```lua
tumblr_api = Arthur.api( 'tumblr', nil, onTumblrReady )
```

---

## .trace

Outputs a human readable table tree in the console. Good for debugging content.

Parameter|Description|Type|Requried
---------|:----------|----|--------
table|The table to output.|Table|Yes

__Returns:__

Nothing. Prints to the console.

__Example:__

```lua
Arthur.trace( content_table )
```

---

# API Object

The __API Object__ is a provider instance that you can make calls against. You must first create this instance using `Arthur.api` (See above).

## :setPrefix

Many APIs contain a version prefix. You can add this prefix manually each time, or set a default that will automatically be applied to the api path in the call.

Parameter|Description|Type|Requried
---------|:----------|----|--------
prefix_str|The API version prefix.|String|Yes

__Returns:__

Nothing.

__Example:__

Consider `tumblr_api` an API Object instance.

```lua
tumblr_api:setPrefix( 'v2' )
```

---

## :get

Make a call to the instanced provider using the "GET" method.

Parameter|Description|Type|Requried
---------|:----------|----|--------
endpoint|The provider endpoint you want to access.|String|Yes
parameters|Additional parameters for the call. Or `nil` otherwise.|Table|No
callback|The callback when the response is returned.|Function|Yes

__Returns:__

The network request id. Can be ignored unless specifically needed.

__Example:__

```lua
local function callback( content )
  Arthur.trace( content ) --debug return object
end
tumblr_api:get('/v2/blog/good.tumblr.com/info', nil, callback)
```
If you use `setPrefix('v2')` above, all endpoints would no longer need the version prefixed on each call:

```lua
tumblr_api:get('/blog/good.tumblr.com/info', nil, callback)
```

---

## :post

Make a call to the instanced provider using the "POST" method.

Parameter|Description|Type|Requried
---------|:----------|----|--------
endpoint|The provider endpoint you want to access.|String|Yes
parameters|Additional parameters for the call. Or `nil` otherwise.|Table|No
post_body|The post body data to send with the post.|String|Yes
callback|The callback when the response is returned.|Function|Yes

__Returns:__

The network request id. Can be ignored unless specifically needed.

__Example:__

```lua
local function callback( content )
  Arthur.trace( content ) --debug return object
end
tumblr_api:post('/v2/blog/good.tumblr.com/info', nil, "some post body", callback)
```

---

## :put

Make a call to the instanced provider using the "PUT" method.

Parameter|Description|Type|Requried
---------|:----------|----|--------
endpoint|The provider endpoint you want to access.|String|Yes
parameters|Additional parameters for the call. Or `nil` otherwise.|Table|No
post_body|The post body data to send with the put.|String|Yes
callback|The callback when the response is returned.|Function|Yes

__Returns:__

The network request id. Can be ignored unless specifically needed.

__Example:__

```lua
local function callback( content )
  Arthur.trace( content ) --debug return object
end
tumblr_api:put('/v2/blog/good.tumblr.com/info', nil, "some post body", callback)
```

---

## :delete

Make a call to the instanced provider using the "DELETE" method.

Parameter|Description|Type|Requried
---------|:----------|----|--------
endpoint|The provider endpoint you want to access.|String|Yes
parameters|Additional parameters for the call. Or `nil` otherwise.|Table|No
callback|The callback when the response is returned.|Function|Yes

__Returns:__

The network request id. Can be ignored unless specifically needed.

__Example:__

```lua
local function callback( content )
  Arthur.trace( content ) --debug return object
end
tumblr_api:delete('/v2/blog/good.tumblr.com/info', nil, callback)
```
