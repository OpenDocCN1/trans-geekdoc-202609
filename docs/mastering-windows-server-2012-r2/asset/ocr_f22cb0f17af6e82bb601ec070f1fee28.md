# PERMISSION INHERITANCE

These permissions are Read & Execute by the book. No more, no less; these atomic permissions make up Read & Execute. Consider it law.

You might have noticed that the "Applies to" drop-down list is also unavailable for the Users group entry. You couldn't remove it because of inheritance, and this is yet another result of inheritance. You can consider inheritance as an order from high. These permissions will be applied to this folder, subfolders, and files unless you disable inheritance and create your custom permissions. If you could go straight to the source, since, as the administrator, you are the rules when it comes to inheritance. If you open up the properties for the volume and edit the entries for the Users group, you can remove or modify the permissions you can then exactly where you want them throughout the volume by using the Apply button from there.

Notice there two entries for the Users group. Server 2012's default permissions are more secure than those given to you in previous server editions. In Windows 2000, Everyone had Full Control on everything! Let's examine the permissions for the other Users group:

+   1. If you are still looking at the dialog box in Figure 14.17, click Close—you don't need to modify the Read & Execute entry because that is exactly what you want for the APPS directory.
2. Back in the Advanced Security Settings for APPS window, click the other entry for the Users group and then click Edit. You'll see the dialog box shown in Figure 14.18.

# FIGURE 14.18
Editing the permissions for the Users group

![](bbox=[0.315, 0.575, 0.9, 0.875])