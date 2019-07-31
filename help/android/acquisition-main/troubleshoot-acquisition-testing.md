---
description: This topic provides information about how to troubleshoot issues you might face during Acquisition testing.
keywords: android;library;mobile;sdk
seo-description: This topic provides information about how to troubleshoot issues you might face during Acquisition testing.
seo-title: Troubleshoot Acquisition testing
solution: Marketing Cloud,Analytics
title: Troubleshoot Acquisition testing
topic: Developer and implementation
---

# Troubleshoot Acquisition testing {#troubleshoot-acquisition-testing}

This topic provides information about how to troubleshoot issues you might face during Acquisition testing.

* If not otherwise specified, the ADBMobileConfig.json file should be placed in the `assets` folder.

  The name is case sensitive, so do not use lower case letters.

* Ensure that `Config.setContext(this.getApplicationContext())` is called from your main activity.

  For more information, see [Configuration methods](https://docs.adobe.com/content/help/en/mobile-services/android/configuration-android/methods.html).

* There are a few user permissions missing from the provided `AndroidManifest.xml` file, and these permissions are required to send data and record offline tracking calls:
 
    ```html
    <manifest ..>
    ... 
    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
    </manifest>
    ```

* In your configuration the referrer, if the `referrerTimeout` is set to 5, you need to send the install intent in a 5-second timeframe after the application was installed and launched for the first time to see the the referrer information appended to the install hit. 

  For manual testing, increase the `referrerTimeout` to 10-15 seconds, so that you have sufficient time to send the referrer information before the install hit is processed.

* Run all the steps in [Testing Marketing Link acquisition](https://docs.adobe.com/content/help/en/mobile-services/android/acquisition-android/t-testing-marketing-link-acquisition.html) and ensure you execute `adb` shell first and then the following:

    ```java
    am broadcast -a com.android.vending.INSTALL_REFERRER -n nl.postnl.app/.tracking.AdobeAcquisitionLinkBroadcastReceiver --es "referrer" "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<the newly generated id at step #7>"
    ```

>[!IMPORTANT]
>
>To process the referrer intent correctly, you must run these two commands independently. Otherwise `adb` will double escape the referrer information and the data received by the broadcast receiver will be incomplete.

