# Reading Notes 38 -- Intent Filters

From [Android Developers Training Guide](https://developer.android.com/training/basics/intents/filters)

The `ACTION_SEND` intent filter allows other apps to start your activity. Adding the `<intent-filter>` element in the manifest file lets the system know when it installs your app that it is ready to respond to outside intents.

## Add an Intent Filters

The `<intent-filter>` element can multiple `<action>`, `<category>`, and `<data>` elements to define exactly what types of intents your app is able to fulfill. 

- Action types describe the action to perform like `ACTION_SEND` or `ACTION_VIEW`.
- Data types can list the exact types of MIME data types accepted.
- Category types describe which of the system categories are appropriate. Typically this is just set to `CATEGORY_DEFAULT`

Example from the Docs:
```java
<activity android:name="ShareActivity">
    <!-- filter for sending text; accepts SENDTO action with sms URI schemes -->
    <intent-filter>
        <action android:name="android.intent.action.SENDTO"/>
        <category android:name="android.intent.category.DEFAULT"/>
        <data android:scheme="sms" />
        <data android:scheme="smsto" />
    </intent-filter>
    <!-- filter for sending text or images; accepts SEND action and text or image data -->
    <intent-filter>
        <action android:name="android.intent.action.SEND"/>
        <category android:name="android.intent.category.DEFAULT"/>
        <data android:mimeType="image/*"/>
        <data android:mimeType="text/plain"/>
    </intent-filter>
</activity>
```

## Handling the Intent

To handle the intent use a `getIntent()` call early from inside the `onCreate()`. To respond to an intent create an intent to deliver some kind of result. Call `setResult()` with the result intent. Use `finish()` to close and destroy your activity. Also if the result is just an integer, then it doesn't even need to intent, just use `setResult()`.
