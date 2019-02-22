---
description: Use the Android SDK to implement the tracking of third-party deferred deep links.
seo-description: Use the Android SDK to implement the tracking of third-party deferred deep links.
seo-title: Tracking Third-Party Deferred Deep Links
title: Tracking Third-Party Deferred Deep Links
uuid: 4c798e47-7988-4a06-a191-6c4d05f6ee61
---

# Tracking Third-Party Deferred Deep Links{#tracking-third-party-deferred-deep-links}

Use the Android SDK to implement the tracking of third-party deferred deep links.

## Classic Adobe Mobile SDK Deep Linking {#section_D114FA1EB9664EAA82E036A990694B26}

The Adobe Mobile SDK currently supports deep linking where the app developer is expected to use the `collectLifecycleData` SDK API from the deep linked activity. The SDK appends the deep link data from the deep link URL parameters. For more information about how deep linking works in the Adobe Mobile SDK, see [Tracking Deep Links](/help/android/acquisition-main/tracking-deep-links/tracking-deep-links.md).

## Facebook Deep Linking {#section_6A9DACB54A2F4CDEBE9C744DEFADFDED}

An ad creator can create an ad on Facebook as a deep link. When users click the ad, it goes directly to the information in which they are interested in the app. The deep link, is **not** a fingerprinter URL. However, during ad configuration, there is an option to provide a third-party deep link URL. An app developer who is using the Adobe Mobile SDKs and services is expected to enter the Adobe Mobile Service-configured fingerprinter URL in this field. If everything is set up correctly, the Facebook SDK passes this URL to the application when the app is installed or launched.

## Setting up the SDKs {#section_834CD3109175432B8173ECB6EA7DE315}

To prepare to add Facebook deep linking support with the Adobe Mobile SDK, the app developer completes the following tasks:

* Get started with the Android SDK

  For more information, see [Getting Started Android SDK](https://developers.facebook.com/docs/android/getting-started) .

* Set up deep linking

  For more information, see [Deep Linking Set up](https://developers.facebook.com/docs/app-ads/deep-linking#os).

If the application is set up correctly, the `trackAdobeDeepLink()` API should enable collecting the deep link information from the Facebook acquisition campaign and send it to Adobe Mobile Service. If the install hit has not been sent to Adobe Mobile Service at the first launch, this information will be added to the Lifecycle hit. Otherwise, it will be sent as an Adobe deep link hit.

>[!TIP]
>
>Ensure that the deep link URL has a key called `a.deeplink.id`. If the URL is missing the deep link ID parameter, the URL parameters will not be appended to the context data.

If the link can be attributed to an acquisition, the Adobe Mobile SDK will store the acquisition data from the Facebook deep link that was used to call `trackAdobeDeepLink()`. This data will be available to the Adobe Mobile SDK in future launches. If a callback has been registered, the Adobe callback will also be used to send the data back to the client.

## Enable Deep Linking in an Android Application {#section_64C15E269E89424B8E3D029F88094620}

1. Register the application to handle deep links.

   For more information, see [Allowing Other Apps to Start your Activity](https://developer.android.com/training/basics/intents/filters.html). 

1. Link the Facebook SDKs.

   To add the Facebook gradle dependency in the app, complete the steps in [Getting Started Android SDK](https://developers.facebook.com/docs/android/getting-started). 

1. To initialize the Facebook SDK, complete the instructions in the *Android Studio Setup* section. 
1. Call `trackAdobeDeepLink()` from the main activity.

   ```java
   @Override 
   protected void onResume() { 
      super.onResume(); 
      AppEventsLogger.activateApp(this); 
      /* 
       * Adobe Tracking - Config 
       * 
       * call collectLifecycleData() to begin collecting lifecycle data 
       * must be in the onResume() of every activity in your app 
       */ 
      Config.collectLifecycleData(this);

      AppLinkData.fetchDeferredAppLinkData(this, 
            new AppLinkData.CompletionHandler() { 
               @Override 
               public void onDeferredAppLinkDataFetched(AppLinkData appLinkData) { 
                  // Process app link data 
                  if (appLinkData != null) { 
                     Config.trackAdobeDeepLink(appLinkData.getTargetUri()); 
                  } 
               } 
            } 
      ); 
   }
   ```

