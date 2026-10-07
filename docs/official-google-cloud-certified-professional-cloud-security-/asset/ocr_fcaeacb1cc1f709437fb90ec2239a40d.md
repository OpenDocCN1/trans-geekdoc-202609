# Using Cloud IAP for TCP forwarding

In this section, we will look at how you can use IAP for TCP forwarding. When you create GCE instances, they appear on the Identity-Aware Proxy page under SSH AND TCP RESOURCES.

# Identity-Aware Proxy + ON-PREM CONNECTORS SETUP Premium

Identity-Aware Proxy (IAP) lets you manage who has access to services hosted on App Engine, Compute Engine, or an HTTPS Load Balancer. Learn more

To get started with IAP, add an Engine app, a Compute Engine instance or configure an HTTPS Load Balancer.

![](bbox=[0.143, 0.375, 0.857, 0.575])

| Resource | Configuration |
| --- | --- |
| All Tunnel Resources | |
| us-central1-a | Error |
| instance-1 | |

Figure 8.9 – The Identity-Aware Proxy dashboard

So, let's create the firewall rule and revisit this page and see the error message disappear. Let's look at how you can create the firewall rule:

+   1. Click on the error message and it will take you to a page that provides details of the missing access level with the source IP address range that you need to add to your firewall rule.