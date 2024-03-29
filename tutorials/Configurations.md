---
layout: page
categories: quickstarts-javascript
title: Configurations
permalink: /quickstarts/javascript/link/Configurations
---

# Kandy Configurations

The first step for any application is to initialize Kandy.js. When doing this, you can customize certain features by providing a configurations object. Kandy's configuration object is separated by feature, and is provided to the Kandy Factory as seen in the example below.

```javascript 
// Initialize an instance of Kandy.js.
import { create } from kandy
const kandy = create({
    authentication: {
        subscription: {
            server: '$SUBSCRIPTIONFQDN$'
        },
        websocket: {
            server: '$WEBSOCKETFQDN$'
        }
    },
    call: {
    serverProvidedTurnCredentials: true,
    iceserver:[
        {
            url: '$KANDYTURN1$'
        },
        {
            url: '$KANDYTURN2$'
        },
        {
            url: '$KANDYSTUN1$'
        },
        {
            url: '$KANDYSTUN2$'
        }
    ]
    },
    logs: {
        // Log output configs.
    },
    // Other feature configs.
    ...
});
```

In most cases, the default values will suffice for an application, but specifying your own configurations allows you to customize certain behaviours. The exception is the authentication configurations, which are always required. This quickstart will showcase a few samples of why you may want to use certain configurations. For a full list of the possible configurations, see the see the `config` API.

## Example Configurations

### Logs

The Logs configs are used to change the SDK's internal logging behaviour. The SDK will generate logs that provide information about what it is doing, such as info and debug messages, warnings, and errors. These configurations allow an application to select which levels they would like to see logs for, and how those logs should be handled.

By default, the SDK will include logs for all levels (the default `logLevel` is 'debug') and will print the logs to the browser's console (via the default `handler` function) at their appropriate level (for example, 'info' logs will use `console.info` and 'debug' logs will use `console.debug`).

These defaults work well for development purposes, but may conflict with browser or other behaviours. For example, since the default Log Handler uses the browser's console, the browser may also filter logs based on its own settings. Many browsers do not show the 'debug' level by default, so it would be an extra step for a user to enable those logs in their browser. A custom Log Handler can be used to avoid this behaviour conflict, by always using the same level for the browser's console. For this reason, it is recommended that all applications actively set the `logLevel` and `handler` configurations for logs, to ensure the SDK's logging behaviour is well suited for your application and its users.

```javascript
logs: {
  // Set the log level to 'debug' to output more detailed logs.
  logLevel: 'debug',
  // Provide a custom Log Handler function.
  handler: function yourLogHandler (logEntry) { ... }
}
```

### Call

The Call configs are used to initialize call/network settings and to set the starting behaviour of a call. They are split into call behaviour configs (under a `callDefaults` object), and call initialization configs. These configs will be used as the default for a call if they are not provided when the call is made.

```javascript
call: {
    callDefaults: {
        // Set the default behaviour for a call to an audio call where video
        //      is enabled, so can be used later on.
        isVideoEnabled: true,
        sendInitialVideo: false,
        // Set the default HTML elements that should be used to display call media.
        remoteVideoContainer: document.getElementById('remote-media'),
        localVideoContainer: document.getElementById('local-media')
    },
    // Specify the browser extension to use (for Chrome) when doing screensharing.
    chromeExtensionId: 'abc123...'
}
```

### Authentication

The Authentication configs are used to specify the backend service that Kandy.js should connect to.The value provided is the host for the Kandy Link that the application is targeting.
Also if the Kandy Link is deployed on-prem, it will be up to the user to define the host.
Note: It is important to always include these configurations.

```javascript
authentication: {
    subscription: {
        server: '$SUBSCRIPTIONFQDN$'
    },
    websocket: {
        server: '$WEBSOCKETFQDN$'
    }
}
call: {
    serverProvidedTurnCredentials: true,
    iceserver:[
        {
            url: '$KANDYTURN1$'
        },
        {
            url: '$KANDYTURN2$'
        },
        {
            url: '$KANDYSTUN1$'
        },
        {
            url: '$KANDYSTUN2$'
        }
    ]
}
```

Examples of the Kandy Link Systems include:

NA:

- RESTURL: webrtc-na.kandy.io port 443
- WebSocketURL: webrtc-na.kandy.io port 443
- iceserver:
  - turn-na-1.kandy.io port 3478 for STUN and 443 for TURNS
  - turn-na-2.kandy.io port 3478 for STUN and 443 for TURNS

EMEA:

- RESTURL: webrtc-em.kandy.io port 443
- WebSocketURL: webrtc-em.kandy.io port 443
- iceserver:
  - turn-em-1.kandy.io port 3478 for STUN and 443 for TURNS
  - turn-em-2.kandy.io port 3478 for STUN and 443 for TURNS

APAC:

- RESTURL: webrtc-ap.kandy.io port 443
- WebSocketURL: webrtc-ap.kandy.io port 443
- iceserver:
  - turn-ap-1.kandy.io port 3478 for STUN and 443 for TURNS
  - turn-ap-2.kandy.io port 3478 for STUN and 443 for TURNS

### Connectivity

The Connectivity configs are used to customize the behaviour of the websocket and connectivity checks. These settings should only be needed if the default configs are not sufficient, and you want to tweak the behaviour for your application's scenario.

```javascript
connectivity: {
    // Specify that a ping should be sent every 30 seconds, and an error should
    //      be reported after 3 missed pong responses.
    method: 'pingPong',
    pingInterval: 30000, // milliseconds
    maxMissedPings: 3
}
```

