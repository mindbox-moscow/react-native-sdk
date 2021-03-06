# mindbox-sdk

This module is a wrapper over the native Mindbox([iOS](https://github.com/mindbox-moscow/ios-sdk),
[Android](https://github.com/mindbox-moscow/android-sdk)) libraries that allows to 
receive and handle push notifications.

## Features

* Receive and show push notification in both mobile platforms.
* Receive push notification data(links) in React Native.

## Getting started

This plugin depends on the configuration of push notifications on native platforms. It's necessary 
to follow the steps specified in the guide:

* [Mindbox React Native SDK](https://developers.mindbox.ru/docs/react-native-sdk)

## Installation

```sh
npm install mindbox-sdk
```

## Usage

```js
import MindboxSdk from "mindbox-sdk";
```

### Methods

#### initialize (Promise)

Initialization of MindboxSdk. It is recommended to do this on app's launch.

```js
await MindboxSdk.initialize({
  domain: 'api.mindbox.ru',
  endpointId: 'your-endpoint-id-here',
  subscribeCustomerIfCreated: true,
  shouldCreateCustomer: true,
  previousInstallId: '',
  previousUuid: '',
});
```

#### getDeviceUUID

Requires a callback that will return device UUID.

```js
MindboxSdk.getDeviceUUID((uuid: string) => { ... });
```

#### getToken

Requires a callback that will return FMS (Android) / APNS (iOS) token.

```js
MindboxSdk.getToken((token: string) => { ... });
```

#### updateToken (Promise)

Updates your FMS/APNS token.

```js
await MindboxSdk.updateToken('your-fms/apns-token');
```

#### onPushClickReceived

Requires a callback that will return push notification link or push notification button link when it clicked.

```js
MindboxSdk.onPushClickReceived((pushClickRecievedData: string) => { ... });
```

#### executeAsyncOperation

Makes request to backend API without waiting any response.

```js
MindboxSdk.executeAsyncOperation({
  operationSystemName: '--YOUR SYSTEM NAME HERE--',
  operationBody: { ... },
});
```

#### executeSyncOperation

Makes request to backend API and waits response.

```js
MindboxSdk.executeSyncOperation({
  operationSystemName: '--YOUR SYSTEM NAME HERE--',
  operationBody: { ... },
  onSuccess: (data) => { ... },
  onError: (error) => { ... },
});
```
