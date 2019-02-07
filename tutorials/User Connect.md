---
layout: page
categories: quickstarts-javascript
title: User Connect
permalink: /quickstarts/javascript/link/User%20Connect
---

# Connecting and Disconnecting

In this quickstart we will cover how to connect and disconnect to the Kandy Platform using Kandy.js. We will provide snippets of code below, which together will form a working demo application.

The first step with Kandy.js is always to initialize it. You will need to know the server information for the Kandy platform that you are using for initialization. Depending on your platform, the only required configuration is the server address, as the others have generic defaults.

``` exclude javascript
import { create } from kandy
const kandy = create({
    authentication: {
        subscription: {
            server: 'spidr-ucc.genband.com'
        },
        websocket: {
            server: 'spidr-ucc.genband.com'
        }
    }
})
```

``` hidden javascript
const { create } = Kandy
const kandy = create({
    authentication: {
        subscription: {
            server: 'spidr-ucc.genband.com'
        },
        websocket: {
            server: 'spidr-ucc.genband.com'
        }
    }
})
```

To learn more about initializing Kandy, see our [Configuration Quickstart](index.html#Configurations).

Since we're going to be making a working demo, we also need some HTML. The HTML for this demo is quite simple.

``` html
<div id='auth-state'>Connected: false</div>

<input type="submit" value="Login" onclick="login();">
<input type="submit" value="Logout" onclick="logout();">

<div id="messages"> </div>
```

What we have is a simple div containing the connected state of our app, two buttons, and an element for logging messages to.


## Step 1: Connecting

To connect using Kandy, you will need two things:
1. A username. This is the full username of a user on your domain. (Example: your-user@your-domain.kandy.io)
1. A password. Don't worry, its safe with us.

``` hidden javascript
var username = "UsernameHere";
var password = "PasswordHere";
```

With these three things, you can call the connect function on Kandy.

``` javascript
function login() {
  kandy.connect({
    username: username,
    password: password
  });
}
```

## Step 2: Connection Events

The `kandy.connect()` function does not return a value. Instead, Kandy.js uses events to tell you when something has changed. You can find a list of the authentication events [here](../docs#authentication).

To subscribe to these events, you use `kandy.on()`. Here is the example for our demo app:

``` javascript
kandy.on('auth:change', function() {
   let isConnected = kandy.getConnection().isConnected;
   document.getElementById('auth-state').innerHTML = 'Connected: ' + isConnected;
   log('Connection state changed.');
});
```

If something goes wrong when we try to connect (invalid credentials maybe), we want to know. Kandy.js has an `auth:error` event to support this.

``` javascript
// Listen for authentication errors.
kandy.on('auth:error', function(params) {
  log('Connect error: ' + params.error.message + ' (' + params.error.code + ')');
});
```

In the above piece of code we subscribe an anonymous function to the `auth:change` event. Now, whenever Kandy fires off an `auth:change` event, that function will be called. Inside this function we call `kandy.getConnection()`. This function returns an object that looks like so:

``` javascript exclude
{ isConnected: true, isPending: false, error: undefined }
```

To learn more about the response from this API checkout the documentation for `getConnection` [here](../docs#authentication).

## Step 3: Disconnecting

To disconnect, you simply call disconnect.

``` javascript
function logout() {
  kandy.disconnect();
}
```

Calling this function will trigger a change in the connection state, which in turn will trigger any listeners to the `auth:change` event. You can therefore use your `auth:change` listener to detect if the disconnect was successful.

``` hidden javascript
// Utility function for appending messages to the message div.
function log(message) {
  document.getElementById('messages').innerHTML += '<div>' + message + '</div>';
}
```

### Live Demo

Want to play around with this example for yourself? Feel free to edit this code on Codepen.

``` codepen
{
	"title": "Kandy.io Authentication Demo",
	"editors": "101",
	"js_external": "https://localhost:3000/kandy/kandy.link.js"
}
```
