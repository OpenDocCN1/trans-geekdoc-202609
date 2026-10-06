
- 1. Log on VDIHOST02 and open Server Manager.
- 2. Choose Manage ▷ Add Roles and Features.
- 3. Click Next on the You Begin screen of the Add Roles and Features Wizard.
- 4. Choose Remote Desktop Services Installation and click Next.
- 5. Select Standard Deployment for the deployment type and click Next.
- 6. For the deployment scenario, select "Virtual machine based desktop deployment."
A standard deployment will deploy the following:

- ◆ Remote Desktop Connection Broker
- ◆ Remote Desktop Web Access
- ◆ Remote Desktop Virtualization Host
- 7. For the Remote Desktop Connection Broker and Remote Desktop Web Access roles, add VDIHOST02 and click next.
- 8. For the Remote Desktop Virtualization Host role, select VDIHOST02 again, but ensure "Create a new virtual switch on the selected servers" is checked, as shown in Figure 29.12.

# FIGURE 29.12
Remote Desktop Virtualization Host options

![](img/41a83208e6906a3732620203b836cea7_1500_0.png)

9. Confirm the settings you have just configured, check the “Restart the destination server automatically if required” check box, and then click Deploy.

The server will deploy these roles and reboot once or twice; this is because it is also adding the Hyper-V role. It can take about 10–15 minutes for the installation to complete, so you have time to grab a cup of coffee.

- 10. When the reboots, log back in on VDIHOST02, and Add the Roles and Features Wizard relaunch and complete.

As with the installation of the session host earlier, ignore the license messages for now.

Next, on AD-01 you need to create an organizational unit (OU) where the VDI computer accounts will be stored.

- 11. Log on to AD-01, and Launch Active Directory Users and Computers.
- 12. Create an OU for the VDI computer accounts.

In our lab we have created an OU called VDI Computers.

- 13. Choose ➤ Advanced Features.
- 14. Right-click the VDI computers OU, and select Attribute Editor.
- 15. Scroll down to the distinguishedname and copy its contents.

For this the distinguishedname is OU=VDIComputers,OU=LAB,DC=lab,DC=NET.

- 16. Log back on to VDIHOST02; if Server Manager has closed, reopen it and click Remote Desktop Services.
- 17. In the Deployment Overview section, choose ➤ Edit Deployment Properties.
- 18. Click Active Directory, and select “Specify the distinguished name of the organization-unit.
- 19. Populate the OU as described in step 15 and as shown in Figure 29.13.

Did you notice in the bottom of the screen that it warns that the permissions have not been correctly configured and that it will correct them for you when you click Apply?

- 20. Click Apply, and it will attempt to set the permissions.

The message should change to inform you that the settings have been applied and the appropriate permissions are now in place.

We need to take a small sidestep now to create the image that will be used for the VDI deployment.

- 21. Open Hyper-V Manager on VDIHOST02.

Since you have worked with virtual machines and Hyper-V in Chapters 27 and 28, we assume you are creating a Windows 8 VM, mount an ISO, and install an operating system. In our lab we called our VM Win-Gold. We also placed it locally on the C drive in a folder called VMSTORE.

# FIGURE 29-13
Specify the AD OU properties.

![](img/41a83208e6906a3732620203b836cea7_1502_0.png)

- 22. Once the operating system is installed and you have deployed the applications you want, open an elevated command prompt and type c:\windows\system32\sysprep\sysprep.
- 23. Select the options illustrated in Figure 29.14.

# FIGURE 29.14
Sysprep options

![](img/41a83208e6906a3732620203b836cea7_1502_1.png)

- 24. Once the VM has turned itself off in Hyper-V, right-click the VM and select Export. You will be asked to specify a path. By default VDI on Windows Server 2012 R2 requires you to place it in path c:\VirtualDesktopTemplate.
- 25. Configure this path via PowerShell using Get-RDVirtualTemplateExportPath and Set-RDVirtualTemplateExportPath cmdlets.

## INSTALLING, USING, AND ADMINING REMOTE DESKTOP SERVICES

- 26. Allow the export to complete, and then delete your VM.
- 27. Import the VM you just exported from C:\VirtualDesktopTemplate\Win-Gold.
- 28. Return now to Server Manager > Remote Desktop Services > Collections.
- 29. Choose Tasks > Create Virtual Desktop Collection.
- 30. Click Next on the You Begin screen.
- 31. Enter a collection name, and click Next. In our lab we created Win8-VDI-Pooled.
- 32. Select Pooled Desktop Collection and click Next. The template you configured now appears in the list.
- 33. Click Next to continue.
- 34. Select "Provide unattended installation settings" and click Next. You can use an existing sysprep answer file if your organization has one.
- 35. Set the time zone where you are located, and then specify the distinguishedname you recorded and click Next.
- 36. Add the groups you wish to authorize to the VDI pool. Define the number of VDI desktops that you need in your pool (remember to size appropriate to the hardware as well), and finally specify a prefix. See Figure 29.15 for the options selected in our lab.
- 37. Select the correct server (if you have more than one in the environment), but take a second to review the information on memory and processor. You can configure where you want to place the new VDI desktop hard disks.
- 38. In this case, select the default because we have only one hard disk in the server. In production you would consider the other options depending on the infrastructure. At the very least, if you choose "Specify a separate path to store parent disk," will be the following best practices and allowing for optimal storage performance.
- 39. Uncheck "Enable User Profiles Disk" because we are not using it in our environment. Note that most enterprises using VDI generally have the users profile redirected to a file share, so this option is not required.
- 40. Confirm all the settings and click Create. Depending on your hardware, this process can take 5–30 minutes on average.
- 41. Click Close that you can create your second collection for personal connections.
- 42. Create a new virtual desktop collection.

# FIGURE 29.15
Specifying users and user groups

![](img/41a83208e6906a3732620203b836cea7_1504_0.png)

- 43. Name the collection Win8-VDI-Personal.
- 44. Select Personal Virtual Desktop Collection and click Next.
- 45. Select the Win-Gold image again. You will be notified that it is in use by other collections. Because this is a personal desktop collection, you can choose Automatic Assignment or Disable Automatic Assignment.
- 46. To alleviate overhead choose Automatic Assignment. Automatic assignment is best, but there could be times when you need to manually assign a user to a VM. As before, you can provide a sysprep answer file if your organization has one.
- 47. In this case, select “Provide unattended installation settings."
- 48. Set the time zone and the appropriate OU as before.
- 49. Configure the appropriate group for access and assignment to the virtual desktop. Configure the number of desktops you wish to deploy and the prefix. Figure 29.16 shows the options selected in our lab.
- 50. Review the allocation screen as you did previously, and click Next. For the virtual desktop storage, notice how the default option has changed and that you have less to select from.

# FIGURE 29.16
Configured options for personal VDI

![](img/41a83208e6906a3732620203b836cea7_1505_0.png)

- 51. For the lab choose on Each RD Virtualization Host Server.
- 52. Review and confirm the settings and click Create.
- 53. Close the screen and monitor the deployment progress.
- 54. From a remote client, log on to https://vydihost2.lab_net/rdweb (this is our URL). Ignore the certificate errors, since by default it deploys a self-signed certificate.
- 55. Enter the credentials of a domain user, in case lab\john.

Figure 29.17 shows you the sample web page when we get log on.
- 56. First, test the Win8-VDI-Pooled connection by clicking it. You will be prompted to confirm the connection.
- 57. Click Connect. This will log you onto a pooled VDI VM.
- 58. Sign out after you have verified your apps and network connectivity.
- 59. Second, test the Win8-VDI-Personal connection by clicking it.
- 60. Again, click Connect when prompted.

Essentially it should be the same experience, but now every time you log on you will get the same VM.
