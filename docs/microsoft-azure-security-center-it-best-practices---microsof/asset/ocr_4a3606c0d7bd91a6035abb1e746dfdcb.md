# Integration with Splunk

The configuration process isn't trivial. There are a lot of steps, and you need to make sure to get one right. Figure 8-8 provides a high-level view of the overall architecture of the solution. The key enabling features for the solution include Azure Event Hub, Azure Monitor, and a Security incident and event management (SIEM) connector add-on that enables the SIEM to poll the event hub to bring the information into the on-premises SIEM.

![](bbox=[0.142, 0.185, 0.755, 0.563])

FIGURE 8-8 Security alert for an IoT device

Splunk integration involves the following processes:
1. Confirm that are accessible logs in Azure Monitor.
2. Configure required permissions in a subscription for the SIEM pipe.
3. Create and configure a resource group for the SIEM pipe.
4. Set up an Azure AD application to provide an access control identity.
5. Create a key vault to contain credentials.
6. Put the app password into the key vault.
7. Make an event hub.
8. Create a shared access key for event hub access control.
9. Put the event hub shared access key in Azure Key Vault.
10. Hook up the event hub to Azure Monitor.
11. Spin up the virtual machine that hosts the Splunk enterprise VM.
12. Install and configure the Azure Monitor add-on for Splunk.