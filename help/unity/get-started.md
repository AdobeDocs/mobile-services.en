---
description: This Plug-in lets you send Adobe Analytics calls from your Unity applications.
keywords: Unity
seo-description: This Plug-in lets you send Adobe Analytics calls from your Unity applications.
seo-title: Unity Plug-in for the iOS and Android 4.x SDKs
solution: Marketing Cloud,Developer
title: Unity Plug-in for the iOS and Android 4.x SDKs
uuid: 83289a73-982d-4472-a8c8-00b562dc80f5
---

# Unity Plug-in for the iOS and Android 4.x SDKs {#unity-plug-in-for-the-ios-and-android-x-sdks}

This Plug-in lets you send Adobe Analytics calls from your Unity applications.

Last Updated: **October 20, 2016**

## Getting started {#section_246D1F9B32ED47EABC41BDA8D0BD0CC7}

Download the [ADBMobile.unitypackage](https://github.com/Adobe-Marketing-Cloud/mobile-services/releases) file from GitHub or Developer Connection.

Here are the contents of the `ADBMobile.unitypackage` file:

* Assets (root)

  * ADBMobile

    * Demo

      * ADBMobileDemo.cs 
      * BooDemo.boo 
      * BooScene.unity 
      * CSharpScene.unity 
      * JavaScriptDemo.js 
      * JavaScriptScene.unity 
      * SecondScene.unity 
      * SecondSceneScript.cs

  * Plugins

    * ADBMobile.cs 
    * Android

      * adobeMobileLibrary-{version}.jar 
      * AndroidManifest.xml 
      * assets

        * ADBMobileConfig.json

    * iOS

      * ADBMobile.h 
      * ADBMobileConfig.json 
      * ADBMobileWrapper.h 
      * ADBMobileWrapper.mm 
      * AdobeMobileLibrary.a

Optional folders: The Demo folder contains Unity scenes and sample code for each of the supported scripting languages.

## Importing the ADBMobile plug-in to your Unity project {#section_35FB6DAE49FB4FA1ACB749A1F9480FE0}

1. Open your Unity project. 
1. Double-click **[!UICONTROL ADBMobile.unitypackage]**. 
1. Select the folders that you want to import.

