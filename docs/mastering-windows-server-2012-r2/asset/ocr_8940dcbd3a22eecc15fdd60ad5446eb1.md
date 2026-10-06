# Configuring NIC Teaming

Creating and managing a NIC team in Windows Server 2012 R2 is easy. You can either create the team with a few simple clicks directly from the graphical user interface (GUI) or use PowerShell cmdlets to achieve the same goal. This section will walk you through various scenarios.

To configure your NIC team using the GUI, follow these steps:

+   1. Log on to your Windows Server 2012 machine with an account that has administrative permissions, and open Server Manager.
2. Click Local Server from the menu on the left, and you should see in the properties pane NIC Teaming is currently disabled, as shown in Figure 4.3.

FIGURE 4-3
Verifying NIC Teaming status

![](bbox=[0.248, 0.355, 0.903, 0.621])

+   3. Click the Disabled link next to NIC Teaming to open the NIC Teaming dialog box, as shown in Figure 4.4.

+   4. While in the Adapters and Interfaces section of the NIC Teaming dialog box, hold the Ctrl key on your keyboard and then, with your mouse, click each of the adapters you want to create a new team.

+   5. Now right-click the selected adapters and choose the Add to New Team option from the context menu, as shown in Figure 4.5.

+   6. When the New Team dialog box opens, enter a name for your new team in the Name field, and ensure that all of the network adapters you want to add have selected in the Member Adapters section.