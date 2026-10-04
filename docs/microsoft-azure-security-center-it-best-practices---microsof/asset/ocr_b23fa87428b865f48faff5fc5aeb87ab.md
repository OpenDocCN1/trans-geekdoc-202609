Before you can begin, you need to be sure you have the prerequisites for integration.
required components are as follows:

+   - An Azure subscription (with administrative access)
- Resource groups to contain the required resources
- An Azure Active Directory (AAD) application for service access
- A key vault in which to store required credentials
- An event hub namespace (event hubs will be created automatically as needed)
- A Splunk server (in the cloud or on-premises)
- Microsoft’s Splunk add-on to read logs from event hubs

# Confirming accessible logs in Azure Monitor

To confirm there are accessible logs in Azure Monitor, open the Azure portal’s **Monitor** blade and click **Activity log**. Run a simple query to confirm that the data is usable (see Figure 8-9).

![](bbox=[0.078, 0.366, 0.235, 0.403])

**FIGURE 8-9** Activity log option in Monitor blade.

# Configuring the subscription for the Splunk SIEM pipe

If you have an existing subscription, make sure you have Owner, Administrator, or Co-Administrator access. If not, request access to that subscription to create the pipe. In this example, the subscription is named ContosoSub..

# Creating and configuring a resource group for the Splunk SIEM pipe

To create and configure a resource group for the Splunk SIEM pipe, follow these steps:

+   1. Open the Azure Portal **ResourceGroup** blade. Confirm that the subscription for the SIEM pipe is selected in the filter at the top (ContosoSub, in this example).
2. Click the Add button at the top of the screen (see Figure 8-10). A new blade will open and enable you to configure the resource group (see Figure 8-11).
3. Enter a unique resource group name (for example, SiemPipeRG).
4. Click the Subscription drop-down menu and select the desired subscription (in this case, ContosoSub).

![](bbox=[0.133, 0.776, 0.203, 0.796])

**FIGURE 8-10** Click the Add button in the Resource Group blade.