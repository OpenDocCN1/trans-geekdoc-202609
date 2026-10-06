# CHAPTER 22 ADDING MORE LOCATIONS: SITES IN ACTIVE DIRECTORY

+   4. Browse to the Computer Configuration > Policies > Administrative Templates > System > Net Logon > DC Locator DNS Records policy folder.

+   5. Double-click the Next Clos Site setting, and click Enabled. Your display will look similar to Figure 22.21. Click OK.

![](bbox=[0.165, 0.23, 0.905, 0.56])

+   6. Close the Group Policy Manager Editor and the Group Policy Management console.

You can wait until Group Policy is applied through the normal refresh cycle or use the gupdate /force command from the command to update any individual clients.

# Configuring Next Closest Site through the Registry

Group Policy allows you to configure a setting once and affect many clients. However, if you want only a single client to use the next closest site, you can modify the registry.

> BE CAREFUL WITH THE REGISTRY

You should be cautious anytime you modify the registry. Incorrectly editing the registry may severely damage your system. It is recommended that you back up all data on your computer before modifying the registry.