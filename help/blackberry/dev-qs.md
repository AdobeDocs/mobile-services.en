---
title: Developer Quick Start
seo-title: BlackBerry Developer Quick Start for Adobe Mobile Services
description: The BlackBerry Developer Quick Start Guide helps you understand the process to implement the BlackBerry library for Adobe Mobile Services.
seo-description: The BlackBerry Developer Quick Start Guide helps you understand the process to implement the BlackBerry library for Adobe Mobile Services.
exl-id: 65f39667-541a-4bbd-af9b-823638aa6f42
---
# Developer quick start

This information helps you understand the process to implement the BlackBerry library.

## Get the SDK

**The SDK requires BlackBerry 10 or later.**

After unzipping the downloaded SDK, verify that the following files exist in an `AdobeMobile` folder:

* `Device-Coverage/libADBMobileShared.so`
* `Device-Debug/libADBMobileShared.so`
* `Device-Profile/libADBMobileShared.so`
* `Device-Release/libADBMobileShared.so`
* `public/ADBMediaAnalytics.hpp`
* `public/ADBMediaSharedHeader.hpp`
* `public/ADBMediaState.hpp`
* `public/ADBMobile.hpp`
* `Simulator-Coverage/libADBMobileShared.so`
* `Simulator-Debug/libADBMobileShared.so`
* `Simulator-Profile/libADBMobileShared.so`

## Add the SDKs to your Project

1. Right-click on your project and select **[!UICONTROL Configure]** > **[!UICONTROL Add Library]**.
1. Select **[!UICONTROL External library]** and click **[!UICONTROL Next]**.
1. Click **[!UICONTROL Browse]** next to the **[!UICONTROL Device library]** field.
1. Navigate to the `ADBMobile-4.0.0BETA-BlackBerry` folder.
1. In the `Device-Debug` folder, select `libADBMobileShared.so` and click **[!UICONTROL Open]**.
1. Click **[!UICONTROL Browse]** next to the **[!UICONTROL Simulator library]** field.
1. Navigate to the `ADBMobile-4.0.0BETA-BlackBerry` folder.
1. In the `Device-Debug` folder, select `libADBMobileShared.so` and click **[!UICONTROL Open]**.
1. Click **[!UICONTROL Add]** next to the **[!UICONTROL Include folders]** field.
1. Navigate to the `ADBMobile-4.0.0BETA-BlackBerry` folder.
1. Add the `public` folder to your includes.
1. In the `ADBMobile-4.0.0BETA-BlackBerry` folder, there is a `.json` config file named `ADBMobileConfig.json`. 

    Copy that file into the root of your project.
1. Right-click on your project and select **[!UICONTROL Refresh]**. 

    The `.json` file should now be visible in your **[!UICONTROL Project Explorer]**.
1. Open the `bar-descriptor.xml` file for your project.
1. At the bottom of the window select the **[!UICONTROL Assets]** tab.
1. Confirm that **[!UICONTROL (All Configurations)]** is selected, then click the **[!UICONTROL Add Files]** in the **[!UICONTROL Assets]** section of the window. 
      >[!TIP]
      >
      >There is a bug in the QNX Momentics IDE that sometimes prevents those buttons from being visible. If you can't see the buttons, resize the windows until they appear.

1. Click **[!UICONTROL Workspace]**.
1. Find the `ADBMobileConfig.json` file in your project and click **[!UICONTROL OK]**.

Your application can import the classes/interfaces from the `adobeMobileLibrary.jar` library by using `#include <ADBMobile.hpp>`.

## Add app permissions

In `bar-descriptor.xml` in the project directory, add the line `<permission>access_internet</permission>`, or in the QNX Momentics IDE, select the **[!UICONTROL Internet]** box on the permissions section of the **[!UICONTROL Application]** tab.

## Update the `ADBMobileConfig.json` config file

The `ADBMobileConfig.json` file contains global SDK settings. You need to update a few values to get started.

The following is an example of an `ADBMobileConfig.json` file:

```json
{
    "version" : "1.0",
    "analytics" : {
        "rsids" : "coolApp",
        "server" : "my.CoolApp.com",
        "charset" : "UTF-8",
        "ssl" : true,
        "offlineEnabled" : true,
        "lifecycleTimeout" : 5,
        "privacyDefault" : "optedin",
    }
}
```

You must at least update the `rsids` and `server` parameters. For more details, see [Adobe Mobile class and method reference](/help/blackberry/methods.md).

You can now implement Analytics in your BlackBerry 10 app.
