---
description: Android SDK 4.x for Experience Cloud Solutions allows you to measure native Android applications, deliver targeted content in your app, and leverage and collect audience data through audience management.
keywords: android;library;mobile;sdk
seo-description: Android SDK 4.x for Experience Cloud Solutions allows you to measure native Android applications, deliver targeted content in your app, and leverage and collect audience data through audience management.
seo-title: Android SDK 4.x for Experience Cloud Solutions
solution: Experience Cloud,Analytics
title: Android SDK 4.x for Experience Cloud Solutions
topic: Developer and implementation
uuid: 56f1ff41-0365-41dd-bdde-245c823dff07
exl-id: c2454e94-a9af-42f3-ab45-14f68531faab
---
# Android SDK 4.x for Experience Cloud solutions{#android-sdk-x-for-experience-cloud-solutions}

Android SDK 4.x for Experience Cloud Solutions allows you to measure native Android applications, deliver targeted content in your app, and leverage and collect audience data through audience management.

## New Adobe Experience Platform Mobile SDK Release

Looking for information and documentation related to the Adobe Experience Platform Mobile SDK? Click [here](https://aep-sdks.gitbook.io/docs/) for our latest documentation.

As of September 2018, we released a new, major version of the SDK. These new Adobe Experience Platform Mobile SDKs are configurable through [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* To get started, go to Adobe Experience Platform Launch.
* To see what is in the Experience Platform SDK repositories, go to [Github: Adobe Experience Platform SDKs](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

>[!IMPORTANT]
>
>The Adobe Analytics Mobile Marketing Add-on SKU is required to enable Mobile Services access to mobile acquisition, deep linking, geolocation, and mobile messaging capabilities. For more information, contact your Adobe CSM.

>[!IMPORTANT]
>
>Although you can configure features in the UI, these features will not work until you download the generated configuration file and add this file to the SDK. For information about downloading and configuring the SDKs, see [Core Implementation and Lifecycle](/help/android/getting-started/dev-qs.md).

The SDKs support the following versions of Android:

* Version 4.6.0 or earlier supports Android 2.2(API 8) - Android 5.1.1 (API 22) 
* Version 4.6.1 or later supports Android 2.3(API 9) or later

Some information to remember:

* In version 4.2 and later, all hits are now sent using HTTP POST.

  This has no impact on the data that is collected or reported, but you need to use a packet analyzer that supports inspecting POST data to view hits.

* If you are upgrading from a previous version, see the [4.x Migration Guide](/help/android/getting-started/migration-v3.md).

## Adobe Mobile user documentation {#section_7583FD5FDED143619048E9744A3F2D21}

Adobe Mobile services provides a UI that brings together mobile marketing capabilities for mobile applications from across the Adobe Experience Cloud. To learn more about the UI and read the user documentation, see [Adobe Mobile Services](https://docs.adobe.com/content/help/en/mobile-services/using/home.html).

## Release notes {#section_F8181DC052D44DD2A99AB40A41F6792C}

For the latest information about Experience Cloud releases, see [Experience Cloud Release Notes](https://docs.adobe.com/content/help/en/release-notes/experience-cloud/current.html). 

## Using Bloodhound

>[!IMPORTANT]
>
>As of **April 30, 2017**, Adobe Bloodhound has been sunset. Starting on May 1, 2017, no additional enhancements and no additional Engineering or Adobe Expert Care support will be provided.
