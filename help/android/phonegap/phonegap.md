---
description: This plug-in allows you to send Android AppMeasurement calls from your PhoneGap project.
keywords: android;library;mobile;sdk
seo-description: This plug-in allows you to send Android AppMeasurement calls from your PhoneGap project.
seo-title: PhoneGap Plug-in
solution: Marketing Cloud,Analytics
title: PhoneGap Plug-in
topic: Developer and implementation
uuid: c5c32357-d8df-458a-b0e8-e0c56040241d
---

# PhoneGap Plug-in {#phonegap-plug-in}

This plug-in allows you to send Android AppMeasurement calls from your PhoneGap project. To create a PhoneGap project, see [PhoneGap](https://helpx.adobe.com/experience-manager/6-4/mobile/using/phonegap.html).

## Install the plug-in using npm {#section_43229E57C16944C0B51531CB92089189}

Run the following command:

```
cordova plugin add adobe-mobile-services
```

# Manually install the plug-in {#section_EA1FD59C484D44878AB509954DEE6037}

## Include the Plug-in

1. Drag the `ADBMobile_PhoneGap.java` file to your `src` folder.

   To move this file, click **[!UICONTROL OK]**. 

1. Drag the `ADB_Helper.js` file into the folder that contains the `index.html` file 

   To move this file, click **[!UICONTROL OK]**. 

1. In the `res/xml` folder, open the `config.xml` file and register an new plugin by adding the following:

   ```xml
   <feature name="ADBMobile_PhoneGap"> 
     <param name="android-package" value="[YOUR_PACKAGE_NAME].ADBMobile_PhoneGap" /> 
   </feature>
   ```

   For example, if your package is named `com.example.phonegaptest`, your `android-package` value would be the following: 

   ```xml
   <param name="android-package" value="com.example.phonegaptest.ADBMobile_PhoneGap" />
   ```

## Include the AppMeasurement Library

1. To download the AppMeasurement library, see [Get the SDK](/help/android/getting-started/dev-qs.md). 
1. Drag the the `adobeMobileLibrary.jar` file to your `src` folder.

   To move this file, click **[!UICONTROL OK]**. 

1. Right-click the `adobeMobileLibrary.jar file and select **[!UICONTROL Add as Library]**. 
1. Based on the requirements of your project, enter the name, level, and location for the library. 
1. Drag the `ADBMobileConfig.json` file to your `assets` folder in the application root. 
1. Confirm that you have selected the root application and **not** an application in an application.

   To move this file, click **[!UICONTROL OK]**.

## Add app permissions

The AppMeasurement library requires the following permissions to send data and record offline tracking calls:

* `INTERNET` 
* `ACCESS_NETWORK_STATE`

To add these permissions, add the following lines to your `AndroidManifest.xml` file, which is in the application project directory:

```xml
<uses-permission android:name="android.permission.INTERNET" /> 
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

To enable in-app messaging:

Update [!DNL AndroidManifest.xml] to declare the full screen activity and enable the Message Notification Handler:

```java
<activity  
android:name="com.adobe.mobile.MessageFullScreenActivity"  
android:theme="@android:style/Theme.Translucent.NoTitleBar" /> 
<receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
```

If you select modal layout when you create a message in Adobe mobile services, select one of the following themes:

* `Theme.Translucent.NoTitleBar.Fullscreen` 
* `Theme.Translucent.NoTitleBar` 
* `Theme.Translucent`

For example:

```java
<activity 
android:name="com.adobe.mobile.MessageFullScreenActivity" 
android:theme="@android:style/Theme.Translucent.NoTitleBar.Fullscreen" 
android:windowSoftInputMode="adjustUnspecified|stateHidden" /> 
<receiver android:name="com.adobe.mobile.MessageNotificationHandler" />
```

## Implement Custom Tracking {#section_FD102B3CDAA4492FB04E56BF17E28663}

In `html` files, add the following to the `<head>` tag where you want to use tracking:

```
<script type="text/javascript" charset="utf-8" src="ADB_Helper.js"></script>
```

