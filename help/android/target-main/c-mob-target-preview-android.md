---
description: Target Preview allows you to easily perform end-to-end QA for Target activities and preview these activities on your device.
seo-description: Target Preview allows you to easily perform end-to-end QA for Target activities and preview these activities on your device.
seo-title: Target Preview on Android
title: Target Preview on Android
uuid: f3c82d64-009c-4929-a5e6-3677b2977889
exl-id: 69103f3a-9521-4808-8ecd-7b960efca04d
---
# Target Preview on Android {#target-preview-on-android}

Target Preview allows you to easily perform end-to-end QA for Target activities and preview these activities on your device.

For more information on how to set up and use Target Preview, go to [Target Mobile Preview](https://docs.adobe.com/content/help/en/target/using/implement-target/mobile-apps/target-mobile-preview.html).

>[!IMPORTANT]
>
>To use Target Preview, you need SDK version 4.14.0 or later.

* **setPreviewRestartDeeplink**

  Sets an app deeplink that will be triggered when preview selections are applied in the Preview mode. 

  * Here is the syntax for this method:

    ```java
    public static void setPreviewRestartDeeplink(String deeplink);
    ```

  * Here is the code sample for this method:

    ```java
    Target.setPreviewRestartDeeplink(“myapp://myhost”); 
    ```
