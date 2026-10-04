To configure this option, follow these steps:

+   1. In the left navigation area, click Security Center.

+   2. In the Security Center left navigation, under Policy & Compliance, click Security Policy, and click Edit Settings next to the subscription you want to configure.

+   3. Click Email notifications, and the Email Notifications blade appears, as shown in Figure 2-24:

![](bbox=[0.226, 0.183, 0.922, 0.383])

**Figure 2-24** Email notification settings

+   4. In Email address, type the email that you want to receive notification.

+   5. In the Phone number field, type your phone number (just one) using international format. For example, +1-415-555-5555. Again, this number will be used by Azure security so that they can contact you regarding possible compromise of your resources. Make sure to audit this number periodically; put it in on your policies and procedures documents to review this because it's easy to forget what number was placed here and there is always a chance that this number has changed.

+   6. Under Email notification settings, make sure to select both options.

+   7. Click Save.

# # Onboard resources using PowerShell

In large deployments, you may consider using Security Center PowerShell modules to help you quickly perform onboarding operations. To prepare the environment you must first install the Az.Security module using the commands below:

```
Set-ExecutionPolicy -Policy AllSigned
Install-Module -Name Az.Security -Force
```

When you finish, use the Connect-AzAccount PowerShell command to log in to your Azure account. Next step is to register your subscriptions to the Security Resource Provider.