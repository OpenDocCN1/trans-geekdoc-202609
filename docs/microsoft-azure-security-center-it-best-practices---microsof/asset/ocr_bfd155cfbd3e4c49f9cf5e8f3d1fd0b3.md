![](bbox=[0.205, 0.019, 0.915, 0.269])

FIGURE **8-32** Select Splunk Enterprise.

+   3. Read the documentation carefully and set up any required licenses as detailed.
4. When you are ready, click **Create**.
5. On the **Basic** page, select a VM username and password. We recommend that you select **Store All Passwords In Key Vault**.
6. Select the **Contosub** subscription for the SIEM pipe.
7. Under **Resource Group**, select the Create New option button.
8. Make the new resource group name `SiemPipeSplunkVMrg`.
9. Open the location drop-down menu and select the location associated with the re-source group.
10. Mark the address space (for example, use the 10.2.0.0/16 mask for 65,536 addresses). The **Create Subnet Configuration** page opens.
11. Enter a **Head Subnet** name (use any meaningful name, such as shsubnet).
12. In the Search Head Subnet Address Prefix Field, select an address prefix that matches the address space (for example, use 10.2.0.0/24 for 32,768 addresses).
13. Enter the index subnet name—for example, idxsubnet.
14. Enter the index subnet address prefix, 10.2.0.0/24.
15. Select a deployment type for the Splunk VM (select based on expected load).
16. Select a VM size (select based on expected load).
17. Select a new IP name. Click the button and create a new name. This can be static or dynamic. (Note that static names may incur additional charges).
18. Set up a unique domain name (network unique) for the Splunk VM (for example, contento.splunk.example.vm).
19. Set up an admin password (the user will be admin—that is, preconfigured in the VM). Recommendation: Store the password in Key Vault (see the steps earlier in this chapter). The **Optional** page opens.