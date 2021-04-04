---
description: You can use the Adobe SDK to collect personally identifiable information (PII) and send it to a third-party endpoint.
seo-description: You can use the Adobe SDK to collect personally identifiable information (PII) and send it to a third-party endpoint.
seo-title: PII Postbacks
title: PII Postbacks
uuid: 08f76a52-75dd-4fc1-b4cc-4f5eef93d0f7
exl-id: 180c21f7-0fba-4b9b-ab7f-7afe81b85f38
---
# PII postbacks {#pii-postbacks}

You can use the Adobe SDK to collect personally identifiable information (PII) and send it to a third-party endpoint.

When you want to use the Adobe SDK to collect PII, you should send a track PII call. Although using this call enables collection of PII data, the SDK does not automatically send the data to any Adobe endpoint. A PII type postback needs to be configured with the appropriate endpoint.

>[!TIP]
>
>An endpoint that supports HTTPS is required to use the PII postback type.

## Tracking PII postbacks {#section_36B967B888CF467EACCDEF61DFA0B12B}

1. Add the library to your project and implement lifecycle. 

   For more information, see *Add the SDK and Config File to your Project* in [Core Implementation and Lifecycle](/help/ios/getting-started/dev-qs.md). 
1. Import the library:

   ```objective-c
   #import "ADBMobile.h"
   ```

1. When you are ready to capture PII, call `trackPII` to send a hit for this action, event, or view:

   ```objective-c
   [ADBMobile collectPII data:nil];
   ```
