5. Don't choose any of the options from the Select Server Roles dialog box; just click Next here to move on.

6. When you reach the Select Features dialog box, scroll down until you find the IP Address Management (IPAM) Server option from the Features list and check the box beside it, as shown in Figure 5.3. You'll be prompted to add some required features here, such as the Group Policy Management console and the Windows Internal Database, so just click the Add Features button in the window that pops up. Click Next to continue.

# FIGURE 5-3
Choosing the feature

![](bbox=[0.273, 0.276, 0.88, 0.626])

7. When you see the Confirm Installation Selections dialog box, review your selection and then click the Install button to start the installation of IPAM.

8. When the installation is complete, click the Close button to finish off the wizard.

# INSTALLING IPAM with POWERShell

You can install the IPAM server feature using PowerShell by following these simple steps:

+   1. Opens a Windows PowerShell prompt with elevated permissions by right-clicking the shortcut and choosing the Run As Administrator option. Then enter your admin credentials as required.

+   2. Type the following command into PowerShell and then press Enter:

```
Install-WindowsFeature IPAM -IncludeManagementTools
```