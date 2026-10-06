Additional configuration of the source computers is done through Group Policy. Specifically, you would configure the Computer Configuration > Administrative Templates > Windows Components > Event Forwarding.
The Policy setting to configure is "Configure target Subscription Manager.
You must add the fully qualified domain name of the collector computer as the subscription manager. Once you enable the setting, you can click Show and then add the name of the server on the Subscription Managers.
As an example, server named BF2 in the Bigfirm.com domain would be identified with a value of Server=BF2.Bigfirm.com, as shown in Figure 30.16.

# Figure 30.16
Configuring Group Policy for a source-initiated subscription

![](bbox=[0.343, 0.283, 0.899, 0.543])

As a reminder, Group Policy objects (GPOs) can be linked to sites, domains, and organizational units (OUs). For this scenario, it makes sense to place all the servers you want to manage in an OU and then link the GPO to the OU.
It's also possible to configure this setting on each of the source computers manually if they aren't in a domain. If your computers are in a workgroup instead of a domain, you also need to use certificates issued from a certificate authority for authentication.
Given the additional requirements for source-initiated subscriptions in a workgroup, you'll probably stick with collector-initiated subscriptions in non-domain environments.

# Selecting Events

When configuring an event subscription, you need to identify which events will be forwarded. Selecting events works for both collector-initiated and source-computer-initiated subscriptions.
You choose to forward all events for specific logs or forward only specific events. When you click the Select Events button, you will see the same page you use to filter any Event Viewer log or create a custom view.