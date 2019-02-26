---
description: Starting with WatchOS 2, your WatchKit Extensions will run on an Apple Watch device. Applications that run in this environment require the WatchConnectivity framework to share data with their containing iOS app.
seo-description: Starting with WatchOS 2, your WatchKit Extensions will run on an Apple Watch device. Applications that run in this environment require the WatchConnectivity framework to share data with their containing iOS app.
seo-title: Apple Watch Implementation with WatchOS 2
solution: Marketing Cloud,Analytics
title: Apple Watch Implementation with WatchOS 2
topic: Developer and implementation
uuid: 9498467e-db5e-411e-a00e-d19841f485de
---

# Apple Watch Implementation with WatchOS 2{#apple-watch-implementation-with-watchos}

Starting with WatchOS 2, your WatchKit Extensions can run on an Apple Watch. Applications that run in this environment require the `WatchConnectivity` framework to share data with their containing iOS app.

>[!TIP]
>
>Starting with `AdobeMobileLibrary` v4.6.0, `WatchConnectivity` is supported.

## Getting Started {#section_70BC28BB69414F169196953D3D264BC1}

>[!IMPORTANT]
>
>Ensure that you have a project with at least the following targets: 
>
>* The containing app 
>* The WatchKit app 
>* The WatchKit extension 
>

For more information about developing WatchKit apps, see [The Watch App Architecture](https://developer.apple.com/library/ios/documentation/General/Conceptual/WatchKitProgrammingGuide/DesigningaWatchKitApp.html#//apple_ref/doc/uid/TP40014969-CH3-SW1).

## Configuring the Containing App {#section_0A2A3995575B4E2ABD12E426BA06AEFF}

Complete the following steps in your Xcode project:

1. Drag the `AdobeMobileLibrary` folder into your project. 
1. Ensure that `ADBMobileConfig.json` is a member of the containing app’s target. 
1. In the **[!UICONTROL Build Phases]** tab of your containing app’s target, expand the **[!UICONTROL Link Binary with Libraries]** section and add the following libraries:

    * `AdobeMobileLibrary.a` 
    * `libsqlite3.tbd` 
    * `SystemConfiguration.framework`

1. In your class that implements the [!DNL UIApplicationDelegate] protocol, add the [!DNL WCSessionDelegate] protocol.

   ```objective-c
   #import <WatchConnectivity/WatchConnectivity.h> 
   @interface AppDelegate : UIResponder <UIApplicationDelegate, WCSessionDelegate>
   ```

1. In the implementation file of your app delegate class, import the `AdobeMobileLibrary`.

   ```objective-c
   #import “ADBMobile.h”
   ```

1. Before making a call to the `ADBMobile` library, in `application:didFinishLaunchingWithOptions:` of your app delegate, configure your `WCSession`.

   ```objective-c
   // check for session availability 
   if ([WCSession isSupported]) { 
       WCSession *session = [WCSession defaultSession]; 
       session.delegate = self; 
       [session activateSession]; 
   }
   ```

1. In your app delegate, implement the `session:didReceiveMessage:` and `session:didReceiveUserInfo:` methods.

   `syncSettings:` is called in the `ADBMobile` library, which returns a bool that indicates whether the dictionary was meant for consumption by the `ADBMobile` library. If it returns `No`, the message was not initiated from the Adobe SDK.

   ```objective-c
   - (void) session:(WCSession *)session didReceiveMessage:(NSDictionary<NSString *,id> *)message { 
       // pass message to ADBMobile 
       if (![ADBMobile syncSettings:message]) { 
           // handle your own custom messages 
       } 
   } 
   - (void) session:(WCSession *)session didReceiveUserInfo:(NSDictionary<NSString *,id> *)userInfo { 
       // pass userInfo to ADBMobile 
       if (![ADBMobile syncSettings:userInfo]) { 
           // handle your own custom messages 
       } 
   } 
   ```

## Configuring the WatchKit Extension {#section_5ADE31741E514330A381F2E3CFD4A814}

1. Ensure that ADBMobileConfig.json is a member of your WatchKit extension’s target. 
1. In the **[!UICONTROL Build Phases]** tab of your WatchKit extension’s target, expand the **[!UICONTROL Link Binary with Libraries]** section and add the following libraries:

    * `AdobeMobileLibrary_Watch.a`
    * `libsqlite3.tbd`

1. In your class that implements the `WKExtensionDelegate` protocol, import `WatchConnectivity` and add the `WCSessionDelegate` protocol.

   ```objective-c
   #import <WatchConnectivity/WatchConnectivity.h> 
   @interface ExtensionDelegate : NSObject <WKExtensionDelegate, WCSessionDelegate>
   ```

1. In the implementation file of your extension delegate class, import the `AdobeMobileLibrary`.

   ```objective-c
   #import “ADBMobile.h”
   ```

1. In `applicationDidFinishLaunching` of your extension delegate, configure your `WCSession` before making any calls to the `ADBMobile` library.

   ```objective-c
   // check for session availability 
   if ([WCSession isSupported]) { 
       WCSession *session = [WCSession defaultSession]; 
       session.delegate = self; 
       [session activateSession]; 
   }
   ```

1. In `applicationDidFinishLaunching` of your extension delegate, initialize the watch app for the SDK.

   ```objective-c
   [ADBMobile initializeWatch];
   ```

1. In your extension delegate, implement the `session:didReceiveMessage:` and `session:didReceiveUserInfo:` methods.

   `syncSettings:` is called in the `ADBMobile` library, which returns a bool that indicates whether the dictionary was meant for consumption by the `ADBMobile` library. If it returns `NO`, the message was not initiated from the Adobe SDK.

   ```objective-c
   - (void) session:(WCSession *)session didReceiveMessage:(NSDictionary<NSString *,id> *)message { 
       // pass message to ADBMobile 
       if (![ADBMobile syncSettings:message]) { 
           // handle your own custom messages 
       } 
   } 
   - (void) session:(WCSession *)session didReceiveUserInfo:(NSDictionary<NSString *,id> *)userInfo { 
       // pass userInfo to ADBMobile 
       if (![ADBMobile syncSettings:userInfo]) { 
           // handle your own custom messages 
       } 
   } 
   ```

## Additional Information {#section_7BCDB5CF0D424DCA97883753D1881233}

Remember the following information:

* For WatchKit apps, `a.RunMode` will be set to `Extension`. 
* Because WatchKit apps run on the watch, the apps will correctly report their names in `a.AppID`. 
* No lifecycle call is triggered on WatchOS2 apps.

