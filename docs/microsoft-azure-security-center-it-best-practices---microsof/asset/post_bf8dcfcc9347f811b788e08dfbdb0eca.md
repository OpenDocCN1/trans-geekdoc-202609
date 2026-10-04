
6. On this page, you should click the appropriate Windows Agent (64- or 32-bit version), and if you are installing on a Linux operating system, click Agent for Linux hyperlink. Make sure to copy the Workspace ID, and Primary Key to the clipboard; you will need those values when installing on the target system. When you finish downloading, you can close the Security Center dashboard by closing your browser. Then copy the agent installation file to a shared network location where the client can access it.

For this example, the agent installation will be on a Windows Server 2016 computer located on-premises. However, the same set of procedures apply to a non-Azure VM located in the cloud. Log on to the target system, and follow the steps below to perform the installation:

- 1. Double-click the MMASetup-AMD64.exe file, and if you open the Open File – Security Warning dialog appears, click Run.

- 2. If the User Access Control dialog appears, click Yes.

- 3. In the Welcome To The Monitoring Agent Setup Wizard, click Next. Read the Microsoft License Terms, and click I Agree.

- 5. On the Destination Folder page, leave the default selection, and click Next. The Agent Setup Options page appears, as shown in Figure 2-18.

![](img/4b11e95292819ab1a383a41ef73aedb4_57_0.png)

FIGURE 2-18 Selecting the target service

6. Select Connect The Agent To Azure Log Analytics (OMS), as shown in Figure 2-18, and click Next. The **Azure Log Analytics** page appears, as shown in Figure 2-19.

![](img/4b11e95292819ab1a383a41ef73aedb4_58_0.png)

**FIGURE 2-19** Providing the workspace ID and primary key

7. On this page, you need to type the Workspace ID and the Primary Key that were obtained in step 5 of the previous procedure. Notice that the Primary Key should be entered in the **Workspace Key** field. If this computer is behind a proxy server, you need to click the **Advanced** button and provide the Proxy URL and authentication, if needed. Once you finish filling in these options, click **Next**.

8. On the **Microsoft Update** page, select **Use Microsoft Update for Updates (Recommended)**, and click **Next**.

9. On the **Ready To Install** page, review the summary field and click **Install.**

10. The **Installing The Microsoft Monitoring Agent** page appears, and the installation proceeds.

11. Once the installation is finished, the **Monitoring Agent configuration Completed Successfully** page appears; click **Finish.**

You can also perform this installation using the command-line interface (CLI), for that, using the following sample:

```
MMASetup-AMD64.exe /Q:A /R:N /C:/setup.exe /qn ADD_OPINSIGHTS_WORKSPACE=1 OPINSIGHTS_
WORKSPACE_AZURE_CLOUD_TYPE=0 OPINSIGHTS_WORKSPACE_ID=<workspaceid> OPINSIGHTS_
WORKSPACE_KEY=<workspaceprimarykey> AcceptEndUserLicenseAgreement=1
```

IMPORTANT The /C switch in this example uses IExpress as its self-extractor. For more information about IExpress, see https://support.microsoft.com/en-us/help/197147.

Most of the parameters that you saw in the agent installation are self-explanatory; the only exception is the OPINSIGHTS_WORKSPACE_AZURE_CLOUD_TYPE, which is the cloud environment specification. The default is 0, which represents Azure commercial cloud; only use 1 if you are installing the agent in an Azure government cloud.

It can take some time for this new-Azure computer to appear in Security Center, but if you want to validate the connectivity between this computer and the workspace, you can use the TestCloudConnection tool. On the target computer, open the command prompt and navigate to the folder \Program Files\Microsoft Monitoring Agent\Agent. From there, execute the command TestCloudConnection.exe, and if the connectivity is working properly, you should see all tests followed by

Test passed for all hosts for workspace id <workspace id>

# Creating workspace

Whatever the reason be, if you decide that you need more than one workspace, you can easily create one using Log Analytics:

- 1. Open Azure Portal and sign in with a user that has Security Admin privileges.
- 2. In the left navigation pane, click More Services, and type Log Analytics.
- 3. On the Log Analytics page, click Add button.
- 4. On the Workspace page, click Create New, and type the Workspace name in the Workspace field.
- 5. Select the subscription that will be used for this workspace.
- 6. Under Resource group, select the resource group you want to use, or create a new one.
- 7. Under Location, select the geolocation for this workspace.
- 8. If your workspace is on the free pricing tier, you're limited to sending 500 MB of data per to the service. When you reach the daily limit, data collection stops until the next day. Click Pricing Tier, change it to Per Node and click OK.
- 9. Click OK to finish the configuration and create the workspace.

Your new workspace appears under the Log Analytics page, as shown in Figure 2-20. If it doesn't appear, click the Refresh button to update the page.

# Moving computers to a new workspace

- 1. In the left navigation pane, click Security Center.

- 2. In the Security Center navigation pane, under General, click Security Policy, and select your subscription.

- 3. On the Security Policy – Data Collection page, click Use Another Workspace, and select the workspace from the drop-down menu, as shown in Figure 2-21.

![](img/4b11e95292819ab1a383a41ef73aedb4_60_0.png)

FIGURE 2-21 Changing the default workspace

- 4. Click Save to commit the changes. You will be asked if you would like to reconfigure monitored VMs that were previously connected to a default workspace: Select No if you want the new workspace settings to apply on new VMs only. The new workspace settings only apply to new agent installations, newly discovered VMs that do not have the Microsoft Monitoring Agent installed. Select Yes if you want the new workspace settings to apply on all VMs. In this case every VM connected to a Security Center workspace is reconnected to the new target workspace.

If you select Yes, Security Center will update all VMs and computers to report to this new workspace. remapping time will vary according to the amount of VMs and computers that you have in your environment. Follow the steps below to quickly identify which VMs were already migrated to the new workspace:

- 1. Open Azure Portal and sign in with a user that has Security Admin privileges.
- 2. In the left navigation pane, click More Services, and type Log Analytics.
- 3. On the Log Analytics page, click on the workspace you created.
- 4. In the workspace's page, under Workspace Data Source, click Virtual Machines, and you will see the list of machines shown in Figure 2-22.

![](img/4b11e95292819ab1a383a41ef73aedb4_61_0.png)

FIGURE 2-22 Visualizing the VMs that belong to the workspace

You can also use PowerShell to obtain the VM's attribute, which includes the extension (in this case MonitoringAgent) and the workspace ID, by using the Get-AzureVMxtension-command, as shown in Listing 2-1.

LISTING 2-1 The Get-AzureVMxtension-command

```
C:\> Get-AzureVMxtension -ResourceGroupName "CONTOSST" -VMName "W2012Web" -Name "MonitoringAgent"
ResourceGroupName : CONTOSST
VMName : W2012Web
Name : MonitoringAgent
Location : central
Etag : null
Publisher : Microsoft.EnterpriseCloud.Monitoring
ExtensionType : MonitoringAgent
HandlerVersion : 1.0
Id : /subscriptions/XXXXXXXXXXXX-b4a7ecb1a70/resourceGroups
```
CONTOSOCSD/providers/Microsoft.Compute/virtualMachines/W2012Web/extensions/
MonitoringAgent
PublicSettings	: {
  "workspaceId": "XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX",
  "azureResourceId": "subscriptions/XXXXXXXX-4a7ecb1a70/resourcegroups/contosocsd/providers/microsoft.compute/virtualmachines/w2012web",
  "stopOnMultipleConnections": true
}
ProtectedSettings	:
ProvisioningState	: Succeeded
Statuses	:
SubStatuses
AutoUpgradeMinorVersion	: True
ForceUpdateTag	 :
```

# E-mail notifications

It is highly recommended that you fill all the security contact emails. You can enter as many email addresses as you want. Security Center will send an email notification on the first daily occurrence of an alert and only for high-severity alerts. Email preferences can only be configured for subscription policies. Resource groups within a subscription will inherit these settings. The email that you receive looks similar to the one shown in Figure 2-23.

![](img/4b11e95292819ab1a383a41ef73aedb4_62_0.png)

**FIGURE 2-23** Sample of a high severity alert email.
