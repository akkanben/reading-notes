# Reading Notes 36 -- Amazon Cognito

Amazon Cognito allows for secure access control for web and mobile apps. Cognito works with common standards like OAuth and OpenID. Coginto also supports sign in through social identity providers like Apple, Google, Facebook and Amazon.

## Getting Started

To configure an application with Amplify Auth use the Amplify CLI with the command `amplfy add auth`. This will prompt a few questions afterwhich you can push these new changes with `amplify push`. After the push the *amplifyconfiguration.json* should be updated with backend auth resources.

- Add dependencies to the application's *build.gradle* file.
  - `implementation 'com.amplifyframework:aws-auth-cognito:1.33.0'`
- Add Auth plugin to the app somewhere that they will be called before calling *Amplify.configure*
  - `Amplify.addPlugin(new AWSCognitoAuthPlugin());`
  - `Amplify.configure(getApplicationContext());`

Add the following lines to the main activity's `onCreate` method:

```java
Amplify.Auth.fetchAuthSession(
    result -> Log.i("AmplifyQuickstart", result.toString()),
    error -> Log.e("AmplifyQuickstart", error.toString())
);
```

## Example

"It's really just that easy" from the Cognito overview
```java
//Android
// 1) -- Create an instance of Auth --
Auth.Builder builder = new Auth.Builder()
  .setAppClientId(getString(R.string.cognito_client_id));    
  .setAppCognitoWebDomain(getString(R.string.cognito_web_domain));
  .setApplicationContext(getApplicationContext());
  .setAuthHandler(new callback());
  .setSignInRedirect(getString(R.string.app_redirect_signin));
  .setSignOutRedirect(getString(R.string.app_redirect_signout));
  .setScopes(userScopes);
  auth = builder.build();
 
// 2) – Set up url redirect in your app manifest --
<intent-filter>
  <data android:host="YOUR_REDIRECT_URI_AUTHORITY"android:scheme="YOUR_REDIRECT_SCHEME"/>
</intent-filter>
 
// 3) -- Get tokens for your user --
auth.getSession();
```
