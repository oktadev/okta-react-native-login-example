# React Native Login Example
 
This example app shows how to create a React Native application and add Login with Okta.

**Prerequisites:** [Node.js](https://nodejs.org/), [React Native CLI](https://www.npmjs.com/package/react-native-cli), and Xcode (for iOS/Mac) or Android Studio (for Android).

> [Okta](https://developer.okta.com/) has Authentication and User Management APIs that reduce development time with instant-on, scalable user infrastructure. Okta's intuitive API and expert support make it easy for developers to authenticate, manage, and secure users and roles in any application.

* [Getting Started](#getting-started)
* [Links](#links)
* [Help](#help)
* [License](#license)

## Getting Started

To install this example application, run the following commands:

```bash
git clone hhttps://github.com/oktadeveloper/okta-react-native-login-example.git
cd okta-react-native-login-example
```

This will get a copy of the project installed locally.

### Create Native Application in Okta

Before you can run this React Native example, you'll need an application to log in to. If you don't have an Okta Developer account, [get one today](https://developer.okta.com/signup/)!

Log in to your Okta Developer account and navigate to **Applications** > **Add Application**. Click **Native** and click the **Next** button. Give the app a name you’ll remember (e.g., `React Native`), select `Refresh Token` as a grant type, in addition to the default `Authorization Code`. Copy the **Login redirect URI** (e.g., `com.okta.dev-123456:/callback`) and save it somewhere. You'll need this value when configuring your app.

Click **Done** and you should see a client ID next screen. Copy and save this value as well. 

### Specify Your Issuer, Client ID, and Redirect URI

Open `auth.config.js` and configure OIDC with your settings.

```js
export default {
  oidc: {
    clientId: '{yourClientId}',
    redirectUri: 'com.okta.dev-######:/callback',
    endSessionRedirectUri: 'com.okta.dev-######:/callback',
    discoveryUri: 'https://dev-######.okta.com/oauth2/default',
    scopes: ['openid', 'profile', 'offline_access'],
    requireHardwareBackedKeyStore: false,
  },
};
```

Update `android/app/build.gradle` to replace the redirect scheme (`com.okta.dev-123456`) with the one that matches your native app's redirect URI.

### Run the App

To run the app on iOS, you'll first need to install CocoaPods:

```bash
sudo gem install cocoapods
```

Then `cd` into the `ios` directory and run `pod install`. Then you can run the following command to start and deploy the app into iOS Simulator.

```bash
react-native run-ios
```

To run the app on Android, you'll have to an Android Virtual Device (AVD). Open Android Studio, select open existing project, and choose the `android` directory in your cloned project. If you're prompted to update anything, approve it.

To create a new AVD, navigate to **Tools** > **AVD Manager**. Create a new Virtual Device and run it. 
 
```bash
react-native run-android
```

## Links

This example uses the following libraries:

* [Okta React Native SDK](https://github.com/okta/okta-oidc-js/tree/master/packages/okta-react-native)
* [OktaDev Schematics](https://github.com/oktadeveloper/schematics)

## Help

Please post any questions as issues on this project, or visit our [Okta Developer Forums](https://devforum.okta.com/). 

## License

Apache 2.0, see [LICENSE](LICENSE).
