---
title: App hidden by default
description: Understand how Teams admins can customize your app.
localization_priority: Normal
ms.author: surbhigupta
ms.topic: conceptual
---

# Hide app until Admin allows it

You can customize Microsoft Teams app experience by hiding the app from users by default until Admin allows it. When an app is published to the global app store, Admins can configure the app before making it available to users. Admins can allow or not allow the app to ensure the app experience is not affected until the app is fully set up. A fully configured app enables better adoption and reduces roadblocks in users’ cognitive understanding.

This feature allows you to specify whether your app can be hidden from users by default until configured.

## Scenario

Contoso Electronics is an independent software vendor (ISV) that has created a help desk app for Microsoft Teams. To enable appropriate functioning of the app, Contoso Electronics’ wants its customers to first set up specific properties of the app. The ISV can specify if they want their app to be blocked by default. The app is available to users only after the Admin allows it.

## Solution

Allowing IT Admins to configure apps before making them available to users helps drive a better user experience, and thus drive greater usage of third-party apps.

![App configure before enabling](../assets/images/apps-in-meetings/appconfiguremessage.png)

To optionally specify whether the app is blocked by default in a new section in the app manifest, add the `defaultHideUntilAdminAction:true` manifest field.

### App configuration support not required

By default, all first-party and third-party apps are allowed. App is blocked by default only when the following options are chosen:

* You opt for default hiding or blocking the app until it is configured or customized by an Admin.
* You submit a new version of app to the store with the default block property specified.

### Option to not hide app by default

If you choose not to hide the app by default, you can remove it by updating their manifest accordingly. When the new version of the app is approved:

* The app will be allowed by default as long as the Admin has not taken specific action to block it.  

* Tenants who have previously blocked the app continue to see it as blocked.

* For tenants who had never taken an action, that is app remained in `PendingConfig` state, the app will now be allowed.

### IT Admin experience

Apps that are default hidden until Admin action continue to be treated as their original app type whether first-party or third-party.

Customized apps appear in the third-party category of the store when viewed during permission policy configuration and don't show as custom apps in the management experience.

After an Admin allows an app, you can toggle it to allow or block as the current experience allows.

When an ISV sets `defaultHideUntilAdminAction:true`, a notification is sent to an Admin that the app has requested action by the Admin before being allowed to users. The app status shows as `Pending Configuration`.

The app with `Pending Configuration` status shows as pending configuration in **Manage apps** page and Admins can allow the app from that page.

Saving the app configuration doesn't affect the app status and the Admin must allow the app.

## User experience within Teams runtime

Teams Store 

If an app is submitted with the default status as Blocked, the app will be default hidden from users until an admin takes an action to Allow it.

Desktop/Web 

When app is set to default Block by an app developer, the app will be hidden everywhere where that experience is served by Teams, until Admin Allows it.  This includes but is not limited to the personal app bar, the tab/ME galleries, in chat as a bot, through the meetings experience, etc.

Mobile 

Same experience as in 4.2 will be reflected in Mobile as well.

App upgrades result in no change of behavior except as relates to removal of default Block support 

When an app developer submits an update of a given app, the normal upgrade process will be followed. If the developer once again specifies `defaultHideUntilAdminAction:true`, the app will be default hidden until Admin takes action once again.


Developers can measure how many tenants allow their apps 

We will deliver telemetry to partner center that allows developer to track how many tenants have allowed their apps, and how many users are using it

Default hidden is supported in GCC/GCCH/DOD 

Customers in GCC/GCCH/DOD will also be affected as above when an app developer choose to have their app default Blocked until an Admin takes action. Admin action to allow must be handled in transit and in storage in compliance with the GCC requirements 

Guest users 

Guests will view the app if it is set to Allow in the tenant that they are currently active in.

Anonymous users 

Anonymous users will view the app if it is set to Allow by the tenant that they are currently joined to 

Federated users 

Federated users are technically not supported.

Users in shared channels 

Not currently supported and therefore out of scope.

**To change the configuration settings for the app**

1. In Microsoft Teams admin center, select **Settings** in the app's **Manage apps** page.
1. In **Landing Site URL**, enter the URL and select **Save**. The **Desktop settings are updated** message appears.

    ![Change settings for app](../assets/images/apps-in-meetings/appsettingschange.png)

1. For **Status** for the app, select **Allowed**.