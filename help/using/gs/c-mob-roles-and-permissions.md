---
description: In Adobe Analytics, you can manage roles on the Admin Tools Home page.
seo-description: In Adobe Analytics, you can manage roles on the Admin Tools Home page.
seo-title: Roles and Permissions
title: Roles and Permissions
uuid: ad350f8d-ef51-4519-98aa-3025bc0f5588
exl-id: 70f0b427-60d5-4a79-a8d3-e03274edd917
---
# Roles and permissions{#roles-and-permissions}

In Adobe Analytics, you can manage roles on the Admin Tools Home page.

## Overview {#section_91B8192891E14E5285718C8118912500}

The following roles manage permissions in the Mobile Services UI:

### Analytics Admin

An Analytics Admin manages user groups and assigns permissions, one of which is the Mobile App Admin. The Experience Cloud Admin links your Adobe ID to your Adobe Analytics account, which allows you to log in to the Mobile Services UI by using your Adobe ID. For more information about the Experience Cloud Administrator, see [Administration - User Management and FAQ](https://docs.adobe.com/content/help/en/core-services/interface/manage-users-and-products/admin-getting-started.html).

>[!TIP]
>
>An existing Analytics Admin has the ability to assign the Analytics Admin role to any user.

For more information about this role, see the following content:

* [User management overview](https://docs.adobe.com/content/help/en/analytics/admin/user-product-management/user-management/users.html)

* [User and Group permission changes](https://docs.adobe.com/content/help/en/analytics/admin/user-product-management/user-management/permissions-changes.html)

### Mobile App Admin

This role is the Admin for the Mobile Services UI.

>[!IMPORTANT]
>
>For some features, such as push messaging, the Analytics Admin must select the **[!UICONTROL Segment Creation]** check box in User Management.

## Managing access {#section_E6939C2695AA4A0DBF432D50B2670920}

Here is some additional information about accessing options in the Mobile Services UI:

### Apps and report suites

All Mobile Service apps are tied to report suites. If users do not have access to a report suite, they will not have access to that report suite's associated app.

### Mobile Services and Analytics features

If your company does not have an Analytics contract to access a feature in the UI, such as Push Messaging, no user in your company will have access to that feature, regardless of permission level.

## Roles and permissions {#section_20AA029D5B8C413C8659777E79B11620}

Here are the roles in the Mobile Services UI, with their relevant permissions:

### Analytics Admin

* All User and Mobile App Admin Permissions
* Create App with new report suite
* Delete App from Mobile Services

  >[!IMPORTANT]
  >
  >Although the app has been deleted in the Mobile Services UI, the report suite still exists in Analytics.

* Manage App Settings

  * Enable Lifecycle Reporting
  * Enable Location Reporting
  * Create/Update/Delete Variables and Metrics

### Mobile App Admin

* All User Permissions
* Create App with existing report suite
* Manage App Settings

  * Configure App's Mobile SDK options
  * Configure App's UI settings
  * Configure linked App Store apps
  * Configure App's Universal Link options
  * Configure Push Services certs and API keys
  * Create/Update/Activate/Deactivate/Duplicate/Archive/Delete Postbacks
  * Create/Update/Archive/Delete Link Destinations

* Create/Update/Archive Marketing Links
* Create/Import/Update/Delete Legacy Acquisition Links
* Create/Import/Update/Delete Places (Points of Interest) configuration
* Create/Update/Send/Schedule/Cancel/Duplicate/Archive/Delete Push Messages
* Create/Update/Activate/Deactivate/Duplicate/Archive/Delete In-App Messages

For more information about groups and users, see:

* [User group settings](https://docs.adobe.com/content/help/en/analytics/admin/user-product-management/user-groups/groups.html)
* [Add a user to a group](https://docs.adobe.com/content/help/en/analytics/admin/user-product-management/user-management/t-add-user-to-group.html)

### Mobile Services user

This role has view-only permissions and can provide feedback in the Mobile Services UI.

* Provide Feedback on Mobile Services UI
* View Apps

  >[!IMPORTANT]
  >
  >Users can only see the report suites for which they have access in Adobe Analytics.

* View App Settings

  * Download App SDK configuration
  * View all UI and SDK settings
  * View Variables and Metrics configuration
  * View Postbacks 
  * View Link Destinations

* View and Run Reports
* View Marketing Links
* View and Export Legacy Acquisition Links
* View and Export Places (Points of Interest) configuration
* View Push Messages
* View In-App Messages
