---
description: The following Acquisition methods are provided by the Android library 
keywords: android;library;mobile;sdk
seo-description: The following Acquisition methods are provided by the Android library 
seo-title: Acquisition Methods
solution: Experience Cloud,Analytics
title: Acquisition Methods
topic-fix: Developer and implementation
uuid: 22ec432f-e7ae-4e89-be07-26206bbeacf8
exl-id: 0ce1b8fb-fd45-45de-8f97-e297e4c6529f
---
# Acquisition methods{#acquisition-methods}

The following Acquisition method is provided by the Android library:

* **campaignStartForApp**

  Allows developers to start an app acquisition campaign as if the user clicked a link. This is helpful for creating manual acquisition links and handling the app store redirect yourself. 

  * Here is the syntax for this method:

    ```java
    public static void campaignStartForApp(final String appId final Map<String Object> data); 
    ```

  * Here is the code sample for this method:

    ```java
    Acquisition.campaignStartForApp("0652024f-adcd-49f9-9bd7-2552a4564d2f" new 
    HashMap<String Object (){{
         put("custom.key" "value");
    }}); 
    ```
