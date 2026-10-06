9. Confirm the settings you have just configured, check the “Restart the destination server automatically if required” check box, and then click Deploy.

The server will deploy these roles and reboot once or twice; this is because it is also adding the Hyper-V role. It can take about 10–15 minutes for the installation to complete, so you have time to grab a cup of coffee.

10. When the reboots, log back in on VDIHOST02, and Add the Roles and Features Wizard relaunch and complete.

As with the installation of the session host earlier, ignore the license messages for now.

Next, on AD-01 you need to create an organizational unit (OU) where the VDI computer accounts will be stored.

11. Log on to AD-01, and Launch Active Directory Users and Computers.

12. Create an OU for the VDI computer accounts.

In our lab we have created an OU called VDI Computers.

13. Choose  ➤ Advanced Features.

14. Right-click the VDI computers OU, and select Attribute Editor.

15. Scroll down to the distinguishedname and copy its contents.

For this the distinguishedname is OU=VDIComputers,OU=LAB,DC=lab,DC=NET.

16. Log back on to VDIHOST02; if Server Manager has closed, reopen it and click Remote Desktop Services.

17. In the Deployment Overview section, choose  ➤ Edit Deployment Properties.

18. Click Active Directory, and select “Specify the distinguished name of the organization-unit.

19. Populate the OU as described in step 15 and as shown in Figure 29.13.

Did you notice in the bottom of the screen that it warns that the permissions have not been correctly configured and that it will correct them for you when you click Apply?

20. Click Apply, and it will attempt to set the permissions.

The message should change to inform you that the settings have been applied and the appropriate permissions are now in place.

We need to take a small sidestep now to create the image that will be used for the VDI deployment.

21. Open Hyper-V Manager on VDIHOST02.

Since you have worked with virtual machines and Hyper-V in Chapters 27 and 28, we assume you are creating a Windows 8 VM, mount an ISO, and install an operating system. In our lab we called our VM Win-Gold. We also placed it locally on the C drive in a folder called VMSTORE.