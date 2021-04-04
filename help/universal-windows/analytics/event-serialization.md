---
description: Event serialization is not supported by processing rules. In the mobile SDK, you must use a special syntax within the context data parameter to set serialized events directly on the server call.
seo-description: Event serialization is not supported by processing rules. In the mobile SDK, you must use a special syntax within the context data parameter to set serialized events directly on the server call.
seo-title: Event serialization
solution: Experience Cloud,Analytics
title: Event serialization
topic: Developer and implementation
uuid: 7220a001-1174-4013-91ff-e8603d8ab265
exl-id: 9cb8d739-8b77-4fe7-8592-22e8cff172d4
---
# Event serialization {#event-serialization}

Event serialization is not supported by processing rules. In the mobile SDK, you must use a special syntax in the context data parameter to set serialized events directly on the server call.

```js
cdata["&&events"] = "event1:12341234";
```

For example:

```js
//create a context data dictionary 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
 
// add events 
cdata["&&events"] = "event1:12341234"; 
 
var ADB = ADBMobile; 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
ADB.Analytics.trackAction("action", cdata); 
// trackState example: 
ADB.Analytics.trackState("State Name", cdata);
```
