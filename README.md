# React Native Login Example

This example app shows how to create a React Native application and add Login with Okta.

To see how this example was created, please read [Create a React Native App with Login in 10 Minutes](https://developer.okta.com/blog/2019/11/14/react-native-login).

**Prerequisites:** [Node.js](https://nodejs.org/), [React Native CLI](https://www.npmjs.com/package/react-native-cli), and Xcode (for iOS/Mac) or Android Studio (for Android).

> [Okta](https://developer.okta.com/) has Authentication and User Management APIs that reduce development time with instant-on, scalable user infrastructure. Okta's intuitive API and expert support make it easy for developers to authenticate, manage, and secure users and roles in any application.

* [Getting Started](#getting-started)
* [Links](#links)
* [Help](#help)
* [License](#license)

## Getting Started

To install this example application, run the following commands:

```bash
git clone https://github.com/oktadeveloper/okta-react-native-login-example.git react-native-login
cd react-native-login
```

This will get a copy of the project installed locally.

### Create Native Application in Okta

Before you can run this React Native example, you'll need a free Okta developer account. Install the [Okta CLI](https://cli.okta.com/) and run `okta register` to sign up for a new account. If you already have an account, run `okta login`.

Then, run `okta apps create`. Select the default app name, or change it as you see fit. Choose **Native** and press **Enter**.

Use `com.okta.dev-133337:/callback` for the Redirect URI and the Logout Redirect URI (where `dev-133337.okta.com` is your Okta domain name). Your domain name is reversed to provide a unique scheme to open your app on a device.

The Okta CLI will create an OIDC Native App in your Okta Org. It will add the redirect URIs you specified and grant access to the Everyone group. You will see output like the following when it's finished:

```shell
Okta application configuration:
Issuer:    https://dev-133337.okta.com/oauth2/default
Client ID: 0oab8eb55Kb9jdMIr5d6
```

NOTE: You can also use the Okta Admin Console to create your app. See [Create a Native App](https://developer.okta.com/docs/guides/sign-into-mobile-app/-/create-okta-application/) for more information.

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

Update `android/app/build.gradle` to replace the redirect scheme (`com.okta.dev-######`) with the one that matches your native app's redirect URI.

### Run the App

To run the app on iOS, you'll first need to install CocoaPods:

```bash
sudo gem install cocoapods
```

Then, run `pod install --project-directory=ios`. You can run the following command to start and deploy the app into iOS Simulator.

```bash
npm run ios
```

To run the app on Android, you'll have to an Android Virtual Device (AVD). Open Android Studio, select open existing project, and choose the `android` directory in your cloned project. If you're prompted to update anything, approve it.

To create a new AVD, navigate to **Tools** > **AVD Manager**. Create a new Virtual Device and run it.

```bash
npm run android
```

## Links

This example uses the following libraries:

* [Okta React Native SDK](https://github.com/okta/okta-oidc-js/tree/master/packages/okta-react-native)
* [OktaDev Schematics](https://github.com/oktadeveloper/schematics)

## Help

Please post any questions as comments on [the blog post](https://developer.okta.com/blog/2019/11/14/react-native-login), as issues in this project, or visit our [Okta Developer Forums](https://devforum.okta.com/).

## License

Apache 2.0, see [LICENSE](LICENSE).
