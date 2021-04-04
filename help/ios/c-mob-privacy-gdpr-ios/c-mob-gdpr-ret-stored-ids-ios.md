---
description: This information helps you retrieve locally stored, Experience Cloud SDK identities from your iOS app and with GDPR data access requests.
seo-description: This information helps you retrieve locally stored, Experience Cloud SDK identities from your iOS app and with GDPR data access requests.
seo-title: Retrieving Stored Identifiers
title: Retrieving Stored Identifiers
uuid: 4fb2c166-6700-4f8b-b60b-137b199e0509
exl-id: ec8592af-fb08-4ab3-99a1-51ac5697a3d8
---
# Retrieving stored identifiers{#retrieving-stored-identifiers}

This information helps you retrieve locally stored, Experience Cloud SDK identities from your iOS app and with GDPR data access requests.

For more information about GDPR, see [GDPR and Your Business](https://www.adobe.com/privacy/general-data-protection-regulation.html).

>[!IMPORTANT]
>
>The `getAllIdentifiersAsync` method retrieves identities that are stored in the Experience Cloud SDKs. You must call this method **before** the user opts-out.

Experience Cloud SDK identities (as applicable) are locally stored and returned in a JSON string, which might contain:

* Company Context - IMS Org IDs 
* User IDs 
* Experience Cloud iD (MID), formerly known as Marketing Cloud ID 
* Integration Codes (ADID, Push ID) 
* Data Source IDs (DPID, DPUUID) 
* Analytics IDs (AVID, AID, VID, and associated RSIDs) 
* Target Legacy IDs (TNTID, TNT3rdpartyID) 
* Audience Manager ID (UUID)

Here is an example of the `ADBMobile getAllIdentifiersAsync` method in iOS:

```objective-c
[ADBMobile getAllIdentifiersAsync:^(NSString * _Nullable content){
      NSLog(content) 
}]
```
