# mod_arthur

__A Corona SDK plugin for interfacing with the OAuth.io service.__

<a href="https://twitter.com/share" class="twitter-share-button" data-via="develephant" data-size="large" data-hashtags="oauth,api,coronasdk,appdev,Lualang">Tweet</a>
<script>!function(d,s,id){var js,fjs=d.getElementsByTagName(s)[0],p=/^http:/.test(d.location)?'http':'https';if(!d.getElementById(id)){js=d.createElement(s);js.id=id;js.src=p+'://platform.twitter.com/widgets.js';fjs.parentNode.insertBefore(js,fjs);}}(document, 'script', 'twitter-wjs');</script>

---

## Setting Up

To use __mod_arthur__ you'll need to take care of a few things first:

1. Create an account at [OAuth.io](https://oauth.io) (it's free).
1. Create a new application at OAuth.io and select API providers.
1. Get a hold of your public key for that application.

## Download

Get the __mod_arthur__ module directory and add it to your project.

__[Click Here to Download Module](https://github.com/develephant/mod_arthur/archive/master.zip)__

## Add the Module

Once you have the __mod_arthur__ module directory in your project, you'll need to `require` it:

```lua
local Arthur = require("arthur.mod_arthur")
```

This will return a _master_ Arthur object instance.

## Initialization

Once you have the OAuth.io public application key, use it to initialize the module:

```lua
Arthur.init( '<public_application_key' )
```

__Continue on to the [API section](/api) to learn more about how to use mod_arthur.__
