---
description: Experience Cloud Mobile SDKs provide General Data Protection Regulation (GDPR)-ready APIs for Controllers that allow users to retrieve locally stored identities and set opt status flags for data collection and transmission.
seo-description: Experience Cloud Mobile SDKs provide General Data Protection Regulation (GDPR)-ready APIs for Controllers that allow users to retrieve locally stored identities and set opt status flags for data collection and transmission.
seo-title: Privacy and General Data Protection Regulation overview
title: Privacy and General Data Protection Regulation overview
uuid: 56d6f155-efec-4b3f-a972-a63155729167
exl-id: 57696f2e-87f4-4f72-bec2-80c7192576f9
---
# Privacy and General Data Protection Regulation overview {#privacy-and-general-data-protection-regulation}

Experience Cloud Mobile SDKs provide General Data Protection Regulation (GDPR)-ready APIs for Controllers that allow users to retrieve locally stored identities and set opt status flags for data collection and transmission.

## New Adobe Experience Platform Mobile SDK Release

Looking for information and documentation related to the Adobe Experience Platform Mobile SDK? Click [here](https://aep-sdks.gitbook.io/docs/) for our latest documentation.

As of September 2018, we released a new, major version of the SDK. These new Adobe Experience Platform Mobile SDKs are configurable through [Experience Platform Launch](https://www.adobe.com/experience-platform/launch.html).

* To get started, go to Adobe Experience Platform Launch.
* To see what is in the Experience Platform SDK repositories, go to [Github: Adobe Experience Platform SDKs](https://github.com/Adobe-Marketing-Cloud/acp-sdks).

## Overview

>[!IMPORTANT]
>
>GDPR is supported **only** in Mobile SDK version 4.16.0 or later.

When Adobe provides software and services to an enterprise, Adobe acts as a data processor for any personal data it processes and stores as part of providing these services. As a data processor, Adobe processes personal data in accordance with your company’s permission and instructions (for example, as set out in your agreement with Adobe).

As a data controller, you can use Adobe Mobile Services SDKs to support GDPR retrieve and delete requests from your mobile apps.

For the Adobe Mobile SDK portions of your mobile apps, you can use the following settings and methods:

* To retrieve data from the SDKs, and send this data to your servers, use the `getAllIdentifiersAsync` method.

  For more information, see [Retrieving Stored Identifiers](/help/android/c-mob-privacy-gdpr-android/c-mob-gdpr-ret-stored-ids-android.md). 

* To set your opt status and help you with a GDPR data deletion request, use the following settings:

  * `privacyDefault` 
  * `setPrivacyStatus`

  For more information, see [Setting the User's Opt Status](/help/android/c-mob-privacy-gdpr-android/privacy.md).
