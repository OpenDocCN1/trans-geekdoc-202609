8. Select ContosoSub from the Subscription drop-down menu for the SIEM pipe, as shown in Figure 8-31.

![](bbox=[0.139, 0.081, 0.821, 0.345])

FIGURE 8-31

9. Select contentosiosm-ns from the Select Event Hub Namespace drop-down menu. Leave Select Event Hub Name empty. This is optional in case you want your event to go to a specific event hub. If you leave this blank, event hubs will be created automatically.

10. From the Select Event Hub Policy Name drop-down menu, select a policy with an all-access pass, which in this example is RootManageSharedAccessKey.

11. Click OK at the bottom of the blade.

# Provision Virtual Machine used by Splunk

From the Azure platform perspective, the configuration is done, now you just need to provide a virtual machine that hosts the Splunk enterprise VM. Follow the steps below to create this VM:

+   1. Go to the Azure portal's Virtual Machine blade and click the Add button, and the Compute blade opens.

+   2. In the search box, type Splunk enterprise and select the Splunk Enterprise template VM, as shown in Figure 8-32.