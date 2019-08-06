---
description: Release notes and known issues for Android SDK 4.x for Experience Cloud Solutions.
seo-description: Release notes and known issues for Android SDK 4.x for Experience Cloud Solutions.
seo-title: Release Notes
solution: Marketing Cloud,Analytics
title: Release Notes
topic: Developer and implementation
uuid: 16bb4de8-a216-47a8-928c-0b1e1421adcf
---

# Release notes {#release-notes}

Here is the release notes, known issues, and hot fix information for Android SDK 4.x for Experience Cloud Solutions:

**August 2, 2019: Version 4.17.9**

* Visitor ID Service: Fixed the `StrictMode` violation when calling syncIdentifiers. 

  This violation was caused by reading shared preferences on the main thread.

* Adobe Target: Added the `requestLocationParameters` attribute in `TargetRequestObject`, which enables the impressionId to be sent with Target requests.

**June 6, 2019: Version 4.17.7**

* General - Networking calls on Android API levels lower than 20 will now use TLS 1.1 or TLS 1.2.
* Analytics - Appended push opt-in status to Lifecycle data when push notifications are enabled.

**July 18, 2019: Version 4.17.8**

* Adobe Target: All requests now include the client and the sessionId in the URL query parameters.
* In-app Messaging: Fixed an issue where, when a message was trigged with an empty clickthrough URL, Android apps crashed.
* Visitor ID Service: The `Visitor.appendToURL` and `Visitor.getUrlVariablesAsync` APIs no longer double-encode their return values.

   The double-encoding was causing the return values from those APIs to be flagged by certain security reviews.

**May 24, 2019: Version 4.17.6**

* visitor ID Service - The 
`setPushIdentifier` API call now sends a
sync call to the Visitor ID Service every time it is called. 

* Visitor ID Service - Increased the connect and read
timeouts from 2 seconds to 5 seconds.


For more information about the current and past release notes for all solutions, see [Adobe Experience Cloud Release Notes](https://marketing.adobe.com/resources/help/en_US/whatsnew/). 
