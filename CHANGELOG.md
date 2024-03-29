# Change Log

Kandy.js change log.

- This project adheres to [Semantic Versioning](http://semver.org/).
- This change log follows [keepachangelog.com](http://keepachangelog.com/) recommendations.

## 3.41.1 - 2022-07-20

## 3.41.0 - 2022-06-30

## 3.40.0 - 2022-05-27

## 3.39.0 - 2022-04-28

## 3.38.0 - 2022-03-25

## 3.37.1 - 2022-03-08

## 3.37.0 - 2022-02-25

## 3.36.0 - 2022-01-28

## 3.35.1 - 2022-01-17

## 3.35.0 - 2021-12-21

## 3.34.0 - 2021-11-26

### Fixed

- Fixed an issue where if the client updated the notifications config and set idCacheLength to 0 (disable duplicate checking) it wouldn't be
  used by the SDK and it would continue to check for duplicate notifications. `KJS-427`
- Fixed presence state to indicate when the client has a pending operation in progress for subscribing/unsubscribing to user presence.
  `KJS-295`

## 3.33.0 - 2021-10-29

### Fixed

- Fixed a CallHistory issue where removing a single record would remove other records as well.

## 3.32.0 - 2021-09-24

### Fixed

- Update notifications plugin state when a websocket connection is removed to indicate the websocket channel is no longer enabled. `KJS-209`

## 3.31.0 - 2021-08-30

### Fixed

- Fixed an issue with the `updateConfig()` API where it would merge arrays instead of replace them. `KJS-205`

## 3.30.0 - 2021-07-30

### Changed

- Changed the domain names used in configuration for all turn/stun servers to the newly public ones (for Kandy tutorials). `KJS-89`

## 3.29.0 - 2021-06-25

### Added

- Added the ability to customize the `X-CPaaS-Agent` header's value by appending any custom string to its value. `KJS-159`

### Fixed

- Fixed an Authentication race condition where receiving a 'Gone' notification while disconnecting would cause an unexpected error in some scenarios. `KAA-2643`
- Fixed Authentication behaviour where issues encountered while disconnecting should still unsubscribe the user locally but wouldn't.
- Fixed a Call issue where the system believes audio is still being used by SDK after a call ends because of AudioContext usage. `KAA-2646`
- Fixed Authentication behaviour where a resubscription failure would not be handled as "subscription gone" when it no longer exists. `KJS-213`

## 3.28.0 - 2021-05-28

### Fixed

- Fixed a CallHistory documentation issue to clarify a usage example for the `getCache` and `setCache` APIs. `KAA-2578`

## 3.27.0 - 2021-04-30

### Fixed

- Changed how [`destroy`](https://kandy-io.github.io/kandy-link-js-sdk-3.x/docs/#apidestroy) is used to prevent errors when destroying inside an event. `KJS-123`
- Fixed an issue where minimizing the SDK caused an error. `KJS-141`

## 3.26.0 - 2021-03-26

### Added

- Added SIP Event capability to receive unsolicited events. `KAA-2600`
- Added improved documentation for the SIP Events feature. `KAA-2590`

## 3.25.0 - 2021-02-26

## 3.24.0 - 2021-01-29

### Added

- Added explicit warning around the connectivity plugin when using `server` for the `responsibleParty` and a `pingInterval`. `KJS-58`
  - `pingInterval` is ignored when the server is responsible for pings. This has been made more explicit now.

## 3.23.0 - 2020-12-21

## 3.22.0 - 2020-11-27

### Fixed

- Minor documentation fixes.
  - Fix the Voicemail `fetch` API description to mention the correct event emitted. `KAA-2569`

## 3.21.0 - 2020-10-30

### Changed

- Action logs are now disabled by default. The client can provide either a boolean or an object with action log configuration details. If `logActions` is set to `true`, the default settings for action logs will be used. See [Config documentation](https://kandy-io.github.io/kandy-link-js-sdk-3.x/docs/#config). `KAA-2504`

## 3.20.0 - 2020-10-02

### Added

- Added `X-Cpaas-Agent` header to all call control requests. `KAA-2427`
- Added a new event `auth:credentialsSet`, to notify when connection credentials are set. `KAA-2490`
- Added the ability to name the redux store instance for debugging with redux devtools extension.

### Changed

- Updated tutorial codepens to be more robust around authentication and subscription operations. `KAA-2491`
- Removed `Creating LogManager` debug log since it was only in place to work around a bug in Chrome that has been fixed. `KAA-2494`

### Fixed

- Fixed broken links in Call History Link docs. `KAA-2497`

## 3.19.0 - 2020-08-28

### Added

- Added a new Logging tutorial. `KAA-2464`
  - Explains how the SDK's logging system works and how an application can customize its behaviour.

### Fixed

- Fixed a Call issue where an active call was not being reconnected to after successfully reconnecting to the network. `KAA-2468`

## 3.18.0 - 2020-07-31

### Fixed

- Fixed a Call issue where during call resynchronization (on WebSocket connect) the request to resync the call would not set the appropriate headers. `KAA-2436`

## 3.17.0 - 2020-06-26

### Added

- Added documentation about `CodecSelectors` for `sdpHandlers.createCodecRemover`.

### Fixed

- Fixed an issue with `sdpHandlers.createCodecRemover` where it wasn't handling multiple codecs selectors with the same name. `KAA-2416`
- Fixed a Call issue where the `changeInputDevices` API would not act on the correct call. `KAA-2404`
  - Please note that there are still known issues for changing video when there are multiple active video calls. See `KAA-2420`.

## 3.16.0 - 2020-05-29

### Changed

- Changed the Tutorial's access URL so that it does not expose configuration parameters for a specific domain/server. `KAA-2320`

### Fixed

- Removed the need for remote party properties (callNotificationParams) to be present in notifications. `KAA-2271`
- Fixed an issue with the `user.search` API where searching with a filter would not work. `KAA-2341`
- Fixed documentation for Conversation in messaging plugin. `KAA-2102`

## 3.15.1 - 2020-05-11

### Fixed

- Fixed an irregular one-way audio issue when ICE timeout is low and call updates happen in quick succession. `KAA-2345`

## 3.15.0 - 2020-04-30

### Added

- Added support for providing a Client Correlator with a user's subscription. `KAA-2204`

## 3.14.0 - 2020-03-27

### Changed

- Updated README to include a link to tutorials with Kandy-UAE configuration. `KAA-2226`

### Fixed

- Adding isVideoNegotiationAvailable flag to call objects for incoming and outgoing calls. `KAA-2203`
- Fixed an intermittent Call issue where a queued, remote, slow-start operation may not be processed properly and hang. `KAA-2079`
- Fixed an intermittent Call issue where a call would audit twice per interval if the ICE candidate gathering process took too long. `KAA-2234`
- Fixed an issue where the `conversation.subscribe` listener not being triggered. `KAA-2200`
- Fixed an issue where incoming call notifications would be dropped when on `push-channel-only` mode if the notification arrived on the websocket channel first. `KAA-2156`

## 3.13.0 - 2020-02-28

### Changed

- Changed the `kandy.notification.registerPush` API to accommodate the breaking changes forced by iOS13 for iOS push registration. This changes require a voip device Token when registering for call service notifications and device token when registering for non-call service notifications .`KAA-2153`

### Added

- Added a destroy function to allow users to wipe the SDK state and render the SDK unusable. `KAA-2181`
  - This is useful when a user is finished with the SDK and wants their data to not be available to the next SDK consumer. After destroy is called, the SDK must be recreated for an application to continue working.
- Added four API's `kandy.notification.registerApplePush`,`kandy.notification.registerAndroidPush`, `kandy.notification.unregisterAndroidPush` and `kandy.notification.unregisterApplePush` to handle the push registration notifications for Apple and Android respectively.`KAA-2153`
- Added a new call configuration to trigger a resync of all active calls upon connecting to the websocket. `KAA-2154`
  - The new call configuration `resyncOnConnect` is disabled by default.
  - The resync feature requires Kandy Link 4.7.1+.
- Added push-mode option for receiving incoming calls exclusively through push on Apple's mobile platform. `KAA-2155`
  - See `config.notifications.incomingCallNotificationMode`
- Added the wrtcsSessionId to the call state. `KAA-2172`

### Fixed

- Fixed the ICE servers documentation for the Link SDK. `KAA-2197`

## 3.12.0 - 2020-01-31

### Fixed

- Fixed an issue where PUSH notification channel was closed by default. `KAA-719`
- Fixed issue where fetching users call log with incorrect credentials throws an error. `KAA-1077`

## 3.11.1 - 2020-01-02

### Fixed

- Fixed documentation issue, introduced in 3.11.0, where portions of the documentation were missing. `KAA-2151`

## 3.11.0 - 2019-12-20

### Added

- Added a 'forceLogOut' option to the `kandy.connect` API to log out the oldest connection with the credentialed user. Helps get around errors that occur when there are too many simultaneous connections. `KAA-2082`
- Added new Logger functionality to allow applications to customize the format of information that the SDK logs.
  - See `config.logs.handler`, `config.logs.logActions.handler`, `logger.LogHandler`, and `logger.LogEntry`.
  - An application can now provide a `LogHandler` function to the SDK via configuration. The SDK will use this function for logging information. By default, the SDK will continue to log information to the console.

### Fixed

- Fixed an issue where call was failing when the user(caller) has no user@domain format. `KAA-2131`

## Deprecated

This 3.x version of the SDK is deprecated and will stop being supported as of November 1, 2020. [Please upgrade to 4.x](https://github.com/Kandy-IO/kandy-link-js-sdk). `KAA-2104`

## 3.10.0 - 2019-11-29

### Added

- Added new user event, `users:change`, to notify when we fetch information about a user. `KAA-1882`

### Changed

- Changed the event emitted when a user is fetched to `users:change`. `KAA-1882`

### Fixed

- Fixed an issue where searching the directory would fail even if a filter was provided. `KAA-1161`
  - Fixed public documentation for directory `search` API.
- Fixed public documentation hyperlinks for custom type definitions. `KAA-2011`

## 3.9.0 - 2019-11-01

### Changed

- Updated README to include a link to tutorials with Kandy-EMEA configuration. `KAA-2050`
- Improved error return when a session is created (or ended) so that it more accurately reflects the issue.

### Fixed

- Fixed an issue where the SIP number normalization was unnecessarily removing an '@' symbol. `KAA-1793`
- Fixed documentation to reflect the correct default value for checkConnectivity parameter. `KAA-1876`
- Fixed public doc links for call and media.

## 3.8.0 - 2019-09-27

### Fixed

- Fixed the ordering and nesting of types & namespaces in public documentation. `KAA-1880`

### Changed

- Changed the public API documentation groupings to namespaces. `KAA-1918`

### Added

- Support for HMAC token-based authentication. `KAA-1919`

## 3.7.1 - 2019-09-03

### Fixed

- Re-fixed an Authentication issue where connecting with invalid credentials for a pre-provisioned user would return an error event with misleading information. `KAA-1937`

## 3.7.0 - 2019-08-30

### Fixed

- Fixed an issue where the `kandy.call.history.clear()` is not clearing history data and returning an empty array. `KAA-1873`
- Fixed implementation of public API 'getAll' (for 'users' plugin) to return an array of all users instead of an object of all users, so that it aligns with current API documentation. `KAA-1923`
- Fixed an issue causing some BasicError objects to have a misleading message rather than a message about the operation that failed. `KAA-1947`
- Fixed an Authentication issue where connecting with invalid credentials for a pre-provisioned user would return an error event with misleading information. `KAA-1937`
- Fixed an issue where the screensharing for the callee would fail to stop from the Chrome notification. `KAA-601`
- Fixed an issue where the transferred call status was not being passed to the application properly. `KAA-1926`

## 3.6.0 - 2019-08-01

### Fixed

- User now automatically disconnects gracefully when internet connection is lost for too long. `KAA-1591`
- Fixed an issue where call audio would be played out of the wrong speaker after a midcall operation that re-rendered media. `KAA-1824`
- Fixed an issue where specifying min and max resolutions when making or answering a call got mixed up. `KAA-1886`
- Fixed many API documentation issues across all SDK's plugins.
- Fixed version numbering associated with public documentation. `KAA-1823`

## 3.5.0 - 2019-06-28

### Changed

- Removed the first parameter (contactId) from kandy.contacts.update() API, thus deprecating it. The user should now use the update(contact) API and ensure that contactId is now being supplied as part of the contact object which is passed to this API. `KAA-1783` `KAA-1600`

### Fixed

- Fixed an issue where the `fetchMessages` function was not available on `Conversations` returned by `kandy.conversation.getAll()`. `KAA-1795`
- Fixed Messaging from creating new conversations every time a message is received.
- Fixed Messaging from not adding the `sender` property to sent messages.

## 3.4.1 - 2019-04-26

### Fixed

- Made a hotfix release just to update the version because something went wrong with NPM and it requires a new version.

## 3.4.0 - 2019-04-26

### Added

- Added a DEBUG log at the start of every public API invocation, which will better help with future investigations `KAA-1353`
- Added the error event to the `subscription`, to prevent subscription change to emitted when there is a subscription failure `KAA-1351`

### Changed

- The `subscription:change` event is no longer emitted when there is an error. User will have to subscribe to `subscription:error` as well. `KAA-1351`
- No longer stores call stats in localstorage by default. Use the `recordCallStats` configuration to turn this back on. `KAA-1552`

## 3.3.0 - 2019-03-29

### Fixed

- Fixed an issue where JOIN_CALL was not emitting a call:error event when it failed. `KAA-922`
- Fixed an issue where disconnecting from the network would leave isConnected in the wrong state `KAA-1547`

### Changed

- Changed the callOptions parameter for the makeAnonymous API function of the CallMe SDK. It must now include a `from` property (callOptions.from), indicating the URI of the caller, as it no longer receives a default value of `anonymousUser@kandy.callMe`. `KAA-1350`

## 3.2.0 - 2019-03-01

### Added

- Added new Presence event, `presence:selfChange`, to notify when self-presence information has changed. `KAA-1153`
- Added Presence APIs for retrieving presence information. See `kandy.presence.getAll` and `kandy.presence.getSelf`. KAA-1152.
- Added Presence constants to the API. See `kandy.presence.statuses` and `kandy.presence.activities`. `KAA-1151`

### Fixed

- Fixed an issue where refreshing an empty address book generated an error. `KAA-1380`
- Fixed an issue where the states property was not being defined on the call namespace (kandy.call.states). `KAA-1349`
- Fixed a crash when using the Presence `fetch` API and receiving no data. `KAA-1169`.

## 3.1.0 - 2019-02-01

### Fixed

- Fixed an issue where track removal does not get cleaned up properly. `KAA-1305`
- Fixed an issue that sometimes cause an error when the user adds "sip:" before the destination address when making a call. `KAA-1360`
- Fixed an issue with Firefox media rendering by escaping special characters from selector in Track component. `KAA-1231`
- Fixed an issue with hold state failing to be set properly on call with certain SIP servers `KAA-938`
- Fixed an issue where audio would not stay muted when going from both hold to local hold. `KAA-1202`
- Fixed an issue where user objects were being added to the state without a userId property, causing them to be keyed by undefined. `KAA-1330`
- Fixed an issue affecting messaging whereby outgoing instant messages remained stuck in an "isPending" state. `KAA-1321`
- Fixed an issue where starting the preview video was failing. `KAA-1344`
- Fixed an issue where the content type header was not being set properly during subscription. `KAA-1331`
- Fixed an issue where Kandy Link users were not having calls added to call history. `KAA-1336`
- Fixed an issue where the presence userID was not being set in some cases in the presence notification message. `KAA-1382`
- Fixed an issue where an internally-used library was polluting the window object. `KAA-1371`
- Fixed an issue where slow-start calls that are rejected were not added to call history. `KAA-1203`

## 3.0.0 - 2018-10-29

### Important Changes

#### HTMLMediaElement.srcObject (`KAA-965`)

In this release we changed the way media streams are attached to media elements to adapt to [upcoming changes](https://www.chromestatus.com/features/5618491470118912) in Chrome. This change is currently announced for Chrome M69. Applications using older versions of the SDK will need to be updated to include these changes prior to Chrome releasing this.

#### createKandy Renamed to kandy.create()

The function to instantiate the SDK has been renamed from `createKandy()` to `Kandy.create()`. Please update your applications accordingly.

### Added

- Added user's locale to data returned in fetchSelfInfo(). `KAA-787`
- Added new Authorization name (authname) to the Kandy connect method. `KAA-606`
- Implemented originalRemoteParticipant field to call and callHistory for keeping track of the initial call "to" `feat/KAA-959`
- Implemented the ability to set and get the custom parameters set on a call. See `kandy.call.setCustomParameters` and `kandy.call.getCustomParameters`. `KAA-918`
- Implemented the ability to send the custom parameters set on a call. See `kandy.call.sendCustomParameters`. `KAA-919`
- Added ability to answer slow start call with video `KAA-858`
- Added functions getCache, setCache to callHistory plugin `KAA-546`
- Added events for tracking cache changes
- Added connectivity.method object to the connectivity configuration allowing server or client to be configured for connCheck responsibility. `KAA-614`
- Added the ability to silence the remote audio for calls and audio bridges. `KAA-1003`
- Added new API method under the _user_ namespace: `kandy.user.getAll`. `KAA-747`
- Added new API methods under the _contacts_ namespace: `kandy.contacts.fetch`, `kandy.contacts.get` and `kandy.contacts.getAll`. `KAA-747`
- Added the ability to set the video as "inactive" instead of "sendonly" when holding a call. `KAA-1067`
- Added ability to turn off log grouping by configuration log: { disableGroup: true }
- Add remote hold state when music on hold is playing with slow start. `KAA-1137`

### Changed

- Moved User Directory Search to the `kandy.user` namespace (previously on `contacts`). `KAA-747`
- Renamed API function kandy.user.fetchDetails to kandy.user.fetchSelfInfo(). `KAA-747`

### Fixed

- Fixed Safari11 and IE11 browser support `KAA-1109`
- Removed an extra colon from the eventType CALL_HISTORY_CACHE_CHANGE `KAA-546`
- Fixed the `callHistory` and `presence` plugins to work on both Link and UC platforms. `KAA-947`
- Updated API documentation for 'customParameters' parameter. `KAA-913`
- Fixed debug message falsely claiming calls may fail in Anonymous Call scenarios. `KAA-934`
- Updated logs to output slightly less noise as part of a logged item.
- Fixed and issue where Trickle ICE process is being initiated on video/stop start when Tickle ICE is disabled.
- Fixed an issue where services subscription timeout would be compounded when services took a long time to subscribe.
- Fixed a merge issue where changes for `KAA-858` were overwritten. `KAA-1065`

## 3.0.0-beta (build 12095+)

### Added

- Added a new property to call logs: `remoteParticipant`. `KAA-853`
  - This includes the `displayName` and `displayNumber` for the remote participant of the call.

### Fixed

- Fixed an issue where calls on hold would cause an unhandled error when added to an audio bridge. `KAA-678`
- Fixed an issue where call logs would have incorrect information for the remote call participant. `KAA-853`
  - Logs will now consistently display the "caller" information as the originator of the call and "callee" information as the destination of the call.
- Fixed issue with video stream for Electron interoperability with Cisco Phones. `KAA-821`
- Fixed 2 issues in Kandy's logManager:
  - The console logger's level is now being set
  - The console's logger is configured such as to not persist data in localStorage

## 3.0.0-beta (build 11497+)

### Added

- Added a getter function, `getMessage`, on conversations for retrieving specific messages. `KAA-850`
- Added the list of conversations that were affected in the `conversations:change` event. `KAA-834`

### Fixed

- Fixed an issue where messages fetched for a conversation may show up as duplicate messages. `KAA-849`
- Fixed an error when trying to fetch a conversation's messages after it received a message. `KAA-848`
- Fixed a connection issue for UC when using the SDK's default services. `KAA-807`
- Fixed an issue where call logs were missing in the logs when a fetch is made immediately after making a call. `KAA-653`
- Fixed an issue where the `remoteParticipant` property was not being added to call state. `KAA-747`

### Deprecation

- The previous event parameter, `conversationId`, for the `conversations:change` event should not be used anymore. The parameter `conversationIds` should now be used. `KAA-834`

## 3.0.0-beta (build 10805+)

### Added

- Added support for OAuth Token subscription via the UC API. `KAA-780`
- Added a more consistent structure to SDK debug logs. `KAA-685`
- Added documentation for the Config plugin's API. `KAA-728`
- Added kandy.getConfig() functionality for getting the current configuration `KAA-728`

## 3.0.0-beta (build 10484+)

### Added

- Added support for Custom SIP headers for Anonymous and regular Calls. `KAA-831`
- Added new property to call state, `remoteParticipant`, retrieved and updated from FCS. `KAA-746`
- Added transition info in the state change event for remote transfer scenarios. `KAA-746`.
  - In a `REMOTE_HOLD` to `IN_CALL` change `transition.code === 9907` signifies a remote participant change.

### Deprecation

- The previous call state properties (eg. `calleeName`) about call participants are now discouraged. Please use `remoteParticipant` for the other call participant's information.

## 3.0.0-beta (build 9354+)

### Fixed

- DTLS changes for CUCM bugs and for consultative transfer. `KAA-804`, `KAA-806`, `KAA-808`
- Tentative fix for process hold issue when on stable state.
- Fixed an issue with Early Media not doing Call Audits. `KAA-781`

## 3.0.0-beta (build 8790+)

### Added

- Added a new parameter to `auth:change` events, to notify of a forced disconnection. `KAA-799`

### Fixed

- Fixed an issue where the end of user subscriptions would not be handled properly. `KAA-799`
- Fixed an issue where the websocket would ping after disconnect, causing a websocket error.

## 3.0.0-beta (build 8760+)

### Added

- Added a retry mechanism for failed session resubscription attempts. `KAA-799`
- Added a new event, `auth:resub`, to notify the application about resub attempts. `KAA-799`

## 3.0.0-beta (build 5574+)

### Compatibility Warning

Version 3.0 is a hard break in backwards compatibility for Kandy.js. This latest beta version is also a hard break from the previous beta version. Numerous breaking changes have been made in this version, with the goal of avoiding API-related breaking changes in the future. The changes are aimed at providing a more consistent and intuitive experience across the entirety of the new API.

The summary of the breaking changes are (1) most API functions have been namespaced, (2) many API function names have been slightly changed, (3) many event names have been slightly changed, (4) event argument parameters have changed, and (5) renaming of SDK build files.

For in-depth information about what has changed, please see: <https://confluence.genband.com/display/KSDK/Kandy.js+3.0.0-beta+Breaking+Changes>

### Fixed

- Fixed the "uncaught at rootSaga" issue, which prevented actions from being processed afterwards.

### Added

- Support for partial subscriptions. `KAA-403`
- The ability to normalize call destination addresses. See the `kandy.call.make` API options. `KAA-560`
- Better functionality for retrieving media devices. See `kandy.call.getDevices` API and the `devices:change` event. `KAA-563`.

## 3.0.0-beta (build 4927+)

### Compatibility Warning

Version 3.0 is a hard break in backwards compatibility for Kandy.js. The new API is modern, reactive, ES6 friendly and more consistent.

Additionally, the new SDK replaces both FCS and Kandy.js 2.13 in a unified converged API. This allows you to write applications on Kandy that can have the benefit of running on all of the Kandy platforms.

We are continually in the process of improving the SDK and our documentation in order to help developers face the difficulty of developing a real-time communication app.

Our reactive approach to this new version of the SDK puts more responsibility on the SDK and less on the app for many tasks:

- Authentication and connection management is tracked by the SDK to a higher degree and helps developers solidify this aspect of their apps.
- Conversation and call state is tracked by the SDK alleviating this burden from the application. The application can focus on rendering these in a reactive manner.
- Converged unified APIs that allow for graceful elevation of features when they become available on the platform.
- Customizability via a plugin system that drives all interactions within the SDK.

### Added

- Completely new unified API that replaces both FCS and Kandy.js 2.x. See the reference documentation.
- New documentation portal with all new documentation and quick starts for 3.0.
