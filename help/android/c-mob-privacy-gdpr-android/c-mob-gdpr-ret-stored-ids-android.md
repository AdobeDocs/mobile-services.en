---
description: This information helps you retrieve locally stored, SDK identities from your Android app and with GDPR data access requests.
seo-description: This information helps you retrieve locally stored, SDK identities from your Android app and with GDPR data access requests.
seo-title: Retrieving stored identifiers
title: Retrieving stored identifiers
uuid: 6fd3d202-b0a1-4c80-96f4-369fc24ac0a3
exl-id: 86c990d8-334b-4003-b0ac-d5404cb598e4
---
# Retrieving stored identifiers{#retrieving-stored-identifiers}

This information helps you retrieve locally stored, SDK identities from your Android app and with GDPR data access requests.

>[!IMPORTANT]
>
>The `getAllIdentifiersAsync` method retrieves identities stored in the SDK. You must call this method **before** the user opts-out.

SDK identities (as applicable) are locally stored and returned in a JSON string, which might contain:

* Company Context - IMS Org IDs 
* User IDs 
* Experience Cloud iD (MID), formerly known as Marketing Cloud ID 
* Integration Codes (ADID, Push ID) 
* Data Source IDs (DPID, DPUUID) 
* Analytics IDs (AVID, AID, VID, and associated RSIDs) 
* Target Legacy IDs (TNTID, TNT3rdpartyID) 
* Audience Manager ID (UUID)

Here is an example of the `ADBMobile getAllIdentifiersAsync` method in Android:

```java
Config.getAllIdentifiersAsync(new ConfigCallback<String>() { 
     @Override 
     public void call(String identitiesJson) {                 
         Log.d("ADBMobile Identities", identitiesJson); 
     } 
});
```
