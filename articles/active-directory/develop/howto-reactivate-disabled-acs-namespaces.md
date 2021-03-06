---
title: How to reactivate disabled Azure Access Control Service (ACS) namespaces
description: Learn how to find and enable your Azure Access Control Service (ACS) namespaces and request an extension to keep them enabled until February 4, 2019.
services: active-directory
documentationcenter: ''
author: CelesteDG
manager: mtillman

ms.service: active-directory
ms.component: develop
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: conceptual
ms.date: 11/07/2018
ms.author: celested
ms.reviewer: jlu
ms.custom: aaddev
---

# How to: Reactivate disabled Access Control Service namespaces

On November 2017, we announced that Microsoft Azure Access Control Service (ACS), a service of Azure Active Directory (Azure AD), is being retired on November 7, 2018.

Since then, we've sent multiple emails to the ACS subscriptions’ admin email about the ACS retirement 12 months, 9 months, 6 months, 3 months, 1 month, 2 weeks, 1 week, and 1 day before the retirement date of November 7, 2018.

On October 3, 2018, we announced (through email and [a blog post](https://azure.microsoft.com/blog/one-month-retirement-notice-access-control-service/)) an extension offer to customers who can't finish their migration before November 7, 2018. The announcement also contained instructions for requesting the extension.

## Why your namespace is disabled

If you haven't opted in for the extension, we will start to disable ACS namespaces starting November 7, 2018. If you missed the communications and would still like to opt in for the extension to February 4, 2019, follow the instructions in the following sections.

> [!NOTE]
> You must be an administrator of the subscription to run the PowerShell commands and request an extension.

## Find and enable your ACS namespaces

You can use ACS PowerShell to list all your ACS namespaces and reactivate ones that have been disabled.

1. Download and install ACS PowerShell:
    1. Go to the PowerShell Gallery and download [Acs.Namespaces](https://www.powershellgallery.com/packages/Acs.Namespaces/1.0.2).
    1. Install the module:

        ```powershell
        Install-Module -Name Acs.Namespaces
        ```

    1. Get a list of all possible commands:

        ```powershell
        Get-Command -Module Acs.Namespaces
        ```

        To get help on a specific command, run:

        ```
        Get-Help [Command-Name] -Full
        ```
    
        where `[Command-Name]` is the name of the ACS command.
1. List your available Azure subscriptions using the **Get-AcsSubscription** cmdlet.
1. List your ACS namespaces using the **Get-AcsNamespace** cmdlet.
1. Confirm that the namespaces are disabled by confirming that `State` is `Disabled`.

    [![Confirm that the namespaces are disabled](./media/howto-reactivate-disabled-acs-namespaces/confirm-disabled-namespace.png)](./media/howto-reactivate-disabled-acs-namespaces/confirm-disabled-namespace.png#lightbox)

    You can also use `nslookup {your-namespace}.accesscontrol.windows.net` to confirm if the domain is still active.

1. Enable your ACS namespace(s) using the **Enable-AcsNamespace** cmdlet.

    Once you've enabled your namespace(s), you can request an extension so that the namespace(s) won't be disabled again before February 4, 2019. After that date, all requests to ACS will fail.

## Request an extension

1. Navigate to your ACS namespace's management portal by going to `https://{your-namespace}.accesscontrol.windows.net`.
1. Select the **Read Terms** button to read the [updated Terms of Use](https://azure.microsoft.com/support/legal/access-control/), which will direct you to a page with the updated Terms of Use.

    [![Select the Read Terms button](./media/howto-reactivate-disabled-acs-namespaces/read-terms-button-expanded.png)](./media/howto-reactivate-disabled-acs-namespaces/read-terms-button-expanded.png#lightbox)

1. Select **Request Extension** on the banner at the top of the page. The button will only be enabled after you read the [updated Terms of Use](https://azure.microsoft.com/support/legal/access-control/).

    [![Select the Request Extension button](./media/howto-reactivate-disabled-acs-namespaces/request-extension-button-expanded.png)](./media/howto-reactivate-disabled-acs-namespaces/request-extension-button-expanded.png#lightbox)

1. After the extension request is registered, the page will refresh with a new banner at the top of the page.

    [![Updated page with refreshed banner](./media/howto-reactivate-disabled-acs-namespaces/updated-banner-expanded.png)](./media/howto-reactivate-disabled-acs-namespaces/updated-banner-expanded.png#lightbox)

## Help and support

- If you run into any issues after following this how-to, contact [Azure support](https://portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/overview).
- If you have questions or feedback about ACS retirement, contact us at acsfeedback@microsoft.com.

## Next steps

- Review the information about ACS retirement in [How to: Migrate from the Azure Access Control Service](active-directory-acs-migration.md).
