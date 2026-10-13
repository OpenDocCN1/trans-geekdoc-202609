
[FIGURE 5-10:](#c05.xhtml#rc05-fig-0010) Azure VM TCP/IP settings in the Azure portal.

![Tip](images/tip.png)Here are some points to ponder concerning your Azure VM’s IP addresses:

*   Remember that giving a VM a public IP address may not be required or even a good idea. Plenty of other options exist for Internet-based access to your VMs, such as Azure Firewall, a manually configured jump box, a load balancer, or a virtual private network.
*   Your private IP address comes from its subnet on its given virtual network. You can assign a static private IP address here instead of relying on Azure dynamic address distribution.

7.  **Revisit the VM’s Networking blade and verify your changes.**

    You should see the NSG inbound port rules at least. Good deal!

## Starting, Stopping, and Resizing VMs

![Remember](images/remember.png)Before I teach you how to start and stop VMs, I want to remind you that Microsoft charges you for each minute the VM is running or stopped but in an allocated state. A rule I stated earlier applies here too: Perform as much Azure-related VM management as possible from outside the VM.

If you shut down the VM by using the Azure portal, PowerShell, or the Azure command-line interface, depending on what parameters you add, you shut down and deallocate the VM, which stops billing.

Just know that deallocating a VM releases any dynamic resources it has been assigned, such as public/private IP addresses and temporary storage.

### Starting and stopping a VM

You may have noticed the Start, Restart, and Stop buttons on the VM’s Overview blade in the Azure portal. You can use those buttons to control your VM’s allocation state (and, therefore, billing), but I’m going to teach you how to stop and start a VM by using PowerShell. [Figure 5-11](#c05.xhtml#c05-fig-0011) shows the interface.

![FIGURE 5-11: Use the toolbar to start, stop, or restart a VM in the Azure portal.](images/9781119612148-fg0511.png)

[FIGURE 5-11:](#c05.xhtml#rc05-fig-0011) Use the toolbar to start, stop, or restart a VM in the Azure portal.

When you use Cloud Shell, Azure automatically authenticates your user account to Azure Active Directory. By contrast, you need to authenticate manually before you can use Azure PowerShell on your local computer.

Follow these steps to use PowerShell on your Windows 10 workstation to stop and then start a given VM:

1.  **Open an administrative PowerShell console, and log into Azure.**

    To do so, run `Connect-AzAccount`, and authenticate to Azure.

    ![Tip](images/tip.png)If you have more than one subscription, and Azure associates your session with the incorrect one, use the following command to make the switch:

    `Set-AzContext -SubscriptionName 'MySubscription'`

2.  **List the VMs in a resource group.**

    You may not remember your VM’s name, but if you remember the resource group name, try this:

    `Get-AzVM -ResourceGroupName 'Wiley'`

    ![Tip](images/tip.png)You can enclose string (character) data in either single or double quotes in PowerShell. PowerShell was designed not to be fussy about such things.

3.  **Stop the target VM with this command:**

    `Stop-AzVM -Name 'vm-win-test' -ResourceGroupName 'Wiley' -Force`

    Make sure to include the `-Force` switch parameter to ensure that you both stop and deallocate the VM.

4.  **Start the VM.**

    Whoa — whiplash! But this step is a good learning opportunity. Check out this technique:

    `Get-AzVM -Name 'vm-win-test' -ResourceGroupName 'Wiley' | Start-AzVM`

    The pipe (`|`) character passes the results of the first segment (getting a reference to the target VM) to the second segment. This technique is called *pipelining*.

### Resizing a VM

As I mention earlier, the ability to resize your VM dynamically is a huge paradigm shift from maintaining on-premises hardware.

![Warning](images/warning.png)VM resizes in Azure have one drawback: They restart your VM. Be sure to perform this operation only during a predefined maintenance window.

To resize a VM, follow these steps:

1.  **In your VM settings, select Size.**

    The Size blade contains a table of all VM sizes that are available in your region. Not all VM sizes are available in every region.

2.  **Edit the filters to filter available VM sizes.**

    You can filter the VM size by using any combination of the following properties:

    *   *Size:* Choices are Small, Medium, and Large.
    *   *Generation:* Choices are Current, Previous, and Older.
    *   *Family:* Choices are General Purpose, GPU, High Performance Compute, Compute Optimized, Memory Optimized, and Storage Optimized.
    *   *Premium Disk:* Choices are Supported and Not Supported.
    *   *vCPUs:* Choices range from 1 to 64 vCPU cores.
    *   *RAM:* Choices range from 2 to 432 GB.

3.  **Select your desired VM size, and click Resize.**

    Your VM restarts with the new virtual hardware resources. Isn’t that a world easier than requesting, ordering, and installing hardware in your on-premises data center?

### Extending your VM’s capabilities

As you enter this chapter’s home stretch, I want to show you how to configure basic diagnostics logging for Windows Server and Linux VMs in Azure.

#### Enabling diagnostic logging

Microsoft offers three increasingly granular monitoring options for Linux and Windows Server VMs:

*   **Host-level metrics:** Basic CPU, disk, and network utilization data pulled by the Azure platform that requires no agent software
*   **Guest-level monitoring:** More detailed monitoring; requires the Azure Diagnostics agent
*   **Azure Monitor Log Analytics:** Most robust monitoring; requires the Log Analytics agent and an associated Azure Monitor Log Analytics workspace

In this chapter, I work with guest-level monitoring. To access it, open the Diagnostic Settings blade, and select Enable Guest-Level Monitoring.

Guest-level monitoring picks up the following data from your Windows Server VMs:

*   **Selected performance monitor counters:** CPU, memory, disk, and network.
*   **Event log messages:** Application, Security, and System.
*   **CPU kernel crash dump data:** This data can be helpful to Microsoft support representatives to diagnose problems with your VM.

Guest-level monitoring includes the following metrics and logs from your Linux VMs:

*   CPU, memory, network, file system, and disk metrics
*   Syslog log data for authentication, task scheduling, CPU, and other facilities

![Technical stuff](images/technicalstuff.png)In Azure monitoring nomenclature, a *metric* is a time series of measured values that are stored for later analysis.

#### Viewing diagnostics data in Azure Monitor

Suppose that you need to plot CPU utilization data for the Linux and Windows Server VMs you’ve created to generate baseline data for your manager.

Follow these steps to create a monitoring chart in Azure Monitor:

1.  **In the Azure portal, open Monitor, and navigate to the Metrics blade.**

    I show you Azure Monitor in [Figure 5-12](#c05.xhtml#c05-fig-0012).

2.  **In the Chart Title field, give the new chart a descriptive name.**

    For this exercise, I called mine Windows Server vs. Linux CPU Comparison.

3.  **Configure the initial metric row to plot CPU data for one of your VMs.**

    Here are the properties I specified for my Windows Server VM:

    *   *Resource:* vm-win-test
    *   *Metric Namespace:* Virtual Machine Host
    *   *Metric:* Percentage CPU
    *   *Aggregation:* Avg

    ![FIGURE 5-12: Azure Monitor is a central point for infrastructure and application monitoring.](images/9781119612148-fg0512.png)

    [FIGURE 5-12:](#c05.xhtml#rc05-fig-0012) Azure Monitor is a central point for infrastructure and application monitoring.

4.  **Click Add Metric, and configure the metric row to plot CPU for your other VM.**

    Being able to plot metrics from multiple Azure resources can be enormously helpful in your monitoring.
