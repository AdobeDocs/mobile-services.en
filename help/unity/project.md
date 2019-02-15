---
description: null
keywords: Unity
seo-description: null
seo-title: Building your project
solution: Marketing Cloud,Developer
title: Building your project
uuid: 5550a394-6f3f-4b87-b840-89621d8a0c1e
---

# Building your project{#building-your-project}

## iOS

When you build for iOS, an Xcode Project is created. By default, the `ADBMobileWrapper.mm` and  `AdobeMobileLibrary.a` files will be in your new project's Libraries group. Perform the following manual steps required to build you app:

1. Add your `ADBMobileConfig.json` file to the project.

   Ensure that it is a member of the build any targets necessary. 

1. In the **[!UICONTROL Build Phases]** tab of your project, add a link to the following libraries:

   * `SystemConfiguration.framework`
      (This library might be linked already.)

   * `libsqlite3.0.dylib`

>[!TIP]
>
>To use Local Notification In-App messages from the SDK, you must call `ADBMobile.EnableLocalNotifications();` from the Start method in your first Unity Scene.

## Android

When you build for Android, the [!DNL `apk`] file already includes the [!DNL `ADBMobileConfig.json`] file in the correct location. By default, the [!DNL `AndroidManifest.xml`] file in your [!DNL /Plugins/Android] folder is also used.

If you need to use your own custom manifest file, the following changes should be added.

Add permissions for:

* `INTERNET` 
* `ACCESS_NETWORK_STATE`

```java
<uses-permission android:name="android.permission.INTERNET" /> 
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

If you are using In-app messaging, add the following activity and receiver:

```java
<activity android:name="com.adobe.mobile.MessageFullScreenActivity"  
android:theme="@android:style/Theme.Translucent.NoTitleBar" /> 
<receiver android:name="com.adobe.mobile.MessageNotificationHandler" /> 
```

If you are using acquisition, add the following receiver:

```java
<receiver android:name="com.your.package.name.GPBroadcastReceiver" android:exported="true"> 
   <intent-filter> 
      <action android:name="com.android.vending.INSTALL_REFERRER" /> 
   </intent-filter> 
</receiver>
```