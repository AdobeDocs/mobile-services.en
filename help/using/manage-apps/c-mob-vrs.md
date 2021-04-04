---
description: A virtual report suite (VRS) is a report suite that is created by applying one or more segment definition to a report suite. This allows users to maintain their data in one report suite but manage the data as if it were in separate report suites.
seo-description: A virtual report suite (VRS) is a report suite that is created by applying one or more segment definition to a report suite. This allows users to maintain their data in one report suite but manage the data as if it were in separate report suites.
seo-title: Virtual Report Suites
title: Virtual Report Suites
uuid: 3f467cad-43e7-4cd0-889b-89f8c61febbd
exl-id: c9ce7f7c-2023-4a9d-9e4d-bacc21f9ad40
---
# Virtual report suites {#virtual-report-suites}

A virtual report suite (VRS) is a report suite that is created by applying one or more segment definition to a report suite. This allows users to maintain their data in one report suite, but manage the data as if it was in separate report suites.

Apps that use VRSs do the same thing as apps that use a regular report suite, except for managing the following features:

* Processing rules 
* evars/props/listvars/events 
* Timestamp-enabled option 
* Dimension flags (lifecycle, location, and so on) 
* Classifications

These values are managed in the parent report suite and are shared with the VRSs that belong to the same parent report suite.

The following areas can be accessed in the Adobe Mobile Services UI independent of the parent report suite:

* The config file 
* Manage Points of Interest 
* Manage Link Destinations 
* Manage Postbacks 
* Message links 
* Acquisition

A VRS can help you complete the following tasks:

* Restrict data access

  A multi-national company has an app that sends data to a report suite for all geo locations. However, the company wants to restrict the business user in one region from viewing the data in another region. The company’s admin can create a VRS to segment users by region and give permission to the VRS only to the business user who manages the region.

  This restriction prevents business users from viewing data that is not related to their region. For example, a business user in EMEA does not need to see data for the APAC region. 

* Allow the control of in-app/push messaging, location POIs, acquisition, and postbacks with all data being sent to one report suite.

  A multi-national company wants all the data to be sent to the same report suite for all geo locations. However, the company wants the marketing team from each region to handle their own in-app/push messaging. The company’s admin can create regional VRSs, and each team can manage their own app based on that VRS.

  The regional team builds their app by using the config file from the VRS. The data is sent to the parent report suite, but in-app/push messaging, location POIs, acquisition, and postbacks are controlled in the app that was created from the VRS.

## Create a virtual report suite in Adobe Analytics {#section_D56B90B2653847D68ECA1F9B39204330}

>[!IMPORTANT]
>
>Only Adobe Analytics admins can create and modify virtual report suites in Adobe Analytics. To create a virtual report suite, see [Create virtual report suites](https://docs.adobe.com/content/help/en/analytics/components/virtual-report-suites/vrs-workflow/vrs-create.html).

Each VRS has a unique ID. To view the parent report suite ID in Adobe Mobile Services UI, on the Manage App Settings page, in the **[!UICONTROL App Information]** section, click **[!UICONTROL More Details]**.

In the Adobe Mobile Services UI, you can use a VRS to create an app and segment data to a specific group in your organization. This way, for example, a business user in Spain cannot see the data that is relevant to a business user in Japan.

>[!TIP]
>
>You cannot modify the values that are inherited from the parent report suite.

A VRS is a server-side segment definition that is attached to a parent report suite. As a result, you cannot perform data collection to a VRS, because the SDK sends hits only to the parent report suite, which in turn records the hits.

## Virtual report suite in Adobe Mobile Services and data collection {#section_8ED8FBA5B44044D9ABC2151A39C577D4}

In Adobe Mobile Services, you can create an app based on a parent report suite or a virtual report suite. When creating an app based on a virtual report suite, we recommend that you align the VRS segment with the definition of the app.

>[!TIP]
>
>Push certifications are attached at the app level in the Mobile Services UI.

To ensure that your push messages are sent correctly, the audience segment must be correctly defined. For more information, see [Audience: Define and Configure Audience Segments for Push Messages](/help/using/in-app-messaging/t-create-push-message/c-audience-push-message.md).

## Understanding time zones {#section_498E1EED22D741C3BDED44F01FACA72A}

The time zone property on the Manage App Settings page is different from the time zone property that you use to create the VRS in Adobe Analytics. The property on the Manage App Settings page is inherited from the parent report suite, which is used to send data to Adobe Analytics. The property that you specify when you create the VRS in Adobe Analytics is used to display the reports in the Mobile Services UI and might be different from the parent report suite.

## Select a virtual report suite in the Mobile Services UI {#section_3212D0FC01FD43DCAF30FBAA354CD6E4}

To use a VRS when you create an app, select the VRS from the **[!UICONTROL Report Suite]** drop-down list on the App Information page. This list contains parent and virtual reporting suites.

>[!IMPORTANT]
>
>To select a VRS from the list, locate an option with the blue dot and the `vrs_` *`<company_name>`* `_` *`<unique name>`* naming convention.

## Virtual Report Suite properties {#section_20ECE6243F664C4FB4347ADB4FF0458A}

Here are the properties for VRSs:

>[!TIP]
>
>The read-only properties are inherited from the parent report suite.

| Property | Inherited from the parent reporting suite | Editable? | Notes |
|--- |--- |--- |--- |
|`target.clientCode`|No|Yes||
|`target.timeout`|No|Yes||
|`audienceManager.server`|No|Yes||
|`audienceManager.analyticsForwardingEnabled`|Yes|Yes||
|`audienceManager.timeout`|No|Yes||
|`acquisition.server`|No|No||
|`acquisition.appid`|No|No||
|`analytics.rsids`|Yes|No||
|`analytics.server`|No|No||
|`analytics.ssl`|No|Yes||
|`analytics.offlineEnabled`|Yes|||
|`analytics.charset`|Yes|No||
|`analytics.lifecycleTimeout`|No|Yes|Should be the parent reporting suite, if users do not want their data to be inconsistent.|
|`analytics.privacyDefault`|No|Yes||
|`analytics.batchLimit`|No|Yes||
|`analytics.timezone`|Yes|Yes, when you first create the app.|This time zone property is used to send data to Adobe Analytics and is different from the time zone property that is set when a VRS is created.|
|`analytics.timezoneOffset`|Yes|No||
|`analytics.referrerTimeout`|No|Yes||
|`analytics.backdateSessionInfo`|Yes|Yes||

## Additional Information {#section_4C4446F1FBE64F659BC0A2362C9F3E59}

Here is some additional information about virtual report suites:

* For more information about VRSs, see [Virtual Report Suites](https://docs.adobe.com/content/help/en/analytics/components/virtual-report-suites/vrs-about.html).
* For more information about planning a VRS implementation, see [Virtual report suite workflow](https://docs.adobe.com/content/help/en/analytics/components/virtual-report-suites/vrs-workflow/vrs-workflow.html).
