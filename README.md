# react-native-jitsi-meet
React native wrapper for Jitsi Meet SDK

Forked from https://github.com/skrafft/react-native-jitsi-meet

For the complete README, please refer to the original repository.

This version of *react-native-jitsi-meet* allows setting the Jitsi *Feature Flags*, when calling the `JitsiMeet.call()` and `JitsiMeet.audioCall()` functions.

The flags are defined in https://jitsi.github.io/handbook/docs/dev-guide/mobile-feature-flags

Example call:

```
JitsiMeet.call(url, userInfo, featureFlags);
```

where *featureFlags* is defined for example as:
```
const featureFlags = {
    "chat.enabled": false,
    "conference-timer.enabled": false,
    "invite.enabled": false,
    "meeting-name.enabled": false,
    "notifications.enabled": false,
    "overflow-menu.enabled": false,
};
```
Note: This package uses version 3.+ of the Jitsi Meet Android SDK.

**Warning**: There is no check of a flag's validity. A typo in the flag identificator might crash the package. The only allowed flag value type is Boolean.

## Install

`npm i git+https://github.com/alariej/react-native-jitsi-meet.git`

## Android setup

1. If your AndroidManifest.xml contains `android:allowBackup="false"` in the Application section, you will get a compile error due to that parameter being set to *true* in the Jitsi Meet SDK. You will either need to use `android:allowBackup="true"` in your Android manifest, or use the manifest merge tools to manage that conflict.

2. In /android/build.gradle, add to the repositories:

```
maven {
    url "https://github.com/jitsi/jitsi-maven-repository/raw/master/releases"
}
```

and set:

```
buildToolsVersion = "28.0.3"
minSdkVersion = 23
compileSdkVersion = 29
targetSdkVersion = 29
```

## iOS setup

TBD