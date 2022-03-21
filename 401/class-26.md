# Reading Notes 26 -- Android Fundamentals

From the [Android Developers Pages](https://developer.android.com/guide/components/fundamentals#Resources)

- Android package files (*.apk*) contain all the required files that are required at runtime.
- Android app bundle files (*.aab*) contain extra meta-data and are the publishing format.
- Apps run in their own process that has it's own isolated virtual machine and with it's own user (Linux).
  - Apps can be designed to share user IDs and belong to the same certificate.
- Apps run with the least privilege necessary.

## App Components

**Activities** are the entry point for a user to interact with the app, this could be directly by starting the app or through another app. An activity is seen as a single screen with a UI. The activity keeps track of what is on screen, helps connect previous apps and provide a flow bebetween apps.

An activity is implemented as a subclass of `Activity`.

**Services** is a generic entry point for keeping something running in the background. Services the user is aware of should be prioritized while less important services may be killed and restarted as the system decides. Services can be *bound services* and seen as a dependency to the app.

A service is implemented as a subclass of `Services`.

**Broadcast Receivers** allow events to reach the user that are outside the usual user flow, e.g. alarms and notifications. The broadcast receiver is typically lightweight and acts as a gateway to other components.

A broadcast receiver is implemented as a subclass of `Broadcast Receiver` and delivered as an `Intent`.

**Content Providers** take care of that app data that can be stored in the file system. Data can be mapped to a URI that doesn't require the app to be running in order for other apps (with permissions) to access. The security as it relates to URI permissions also provides a very fine-grained model to benefit the user.

A content provider as a subclass of `ContentProvider`.

### Activating Components

Activities, services, and broadcast receivers are activated by intents. Intents are asynchronous messages, and for activities and services these are actions to perform. Broadcast receivers the intent is the thing being broadcast.

Content providers are not activated via intents but instead from a `ContentResolver`

## Android Manifest File

The manifest file defines the required user permissions, minimum API level, hardware requirements and external libraries needed. The manifest uses an XML format to build an outline of the app's components.

The manifest can also, optionally, include intent filters that allow it to respond to the intents from other apps.

