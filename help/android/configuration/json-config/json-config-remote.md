---
description: You can load a different ADBMobile JSON config file when the application starts.
seo-description: You can load a different ADBMobile JSON config file when the application starts.
seo-title: Override the ADBMobile JSON Config Path
solution: Experience Cloud,Analytics
title: Override the ADBMobile JSON Config Path
topic-fix: Developer and implementation
uuid: 6872a5d7-0c5a-4fdc-b7bf-ad1534763a6a
exl-id: 6ca8e264-af79-4734-aeb9-824582980953
---
# Override the ADBMobile JSON config path {#override-the-adbmobile-json-config-path}

You can load a different ADBMobile JSON config file when the application starts.

The `Config.overrideConfigStream(configInput)` method allows you to specify the path to a different `ADBMobile.json` configuration file when the application starts. This method must be called before any other Experience Cloud SDK call (before `Config.collectLifecycleData()` ), typically in the `onCreate` method of your first loaded activity.

Calling this method with a different path causes a one-time override of the configuration file until the application is closed.

```java
 try { 
   InputStream configInput = getAssets().open("ExampleJSONFile.json"); 
   Config.overrideConfigStream(configInput); 
   } catch (IOException ex) { 
   // do something with the exception if needed 
}
```
