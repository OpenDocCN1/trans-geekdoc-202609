# CHAPTER 16 SHARING PRINTERS ON WINDOWS SERVER 2012 R NETWORKS

have different print devices that use the same driver. However, if the devices require different drivers, they won't work in the same printer pool.

Second, we highly recommend putting the pooled print devices in the same physical location. Since users don't know which printer their job will print at, you don't have to wander from place to place looking for their print jobs.

# SEPARATOR PAGES

Consider separator pages with usernames in printer pools since users will not necessarily know which printer their job went to. Separator pages are explained in greater depth later in this chapter.

# Printer Properties Security Tab

Those familiar with current Windows-based operating system know that you secure the printer by defining user rights for what people can do on the network and setting permissions for the resources that people can use. Printer security is controlled with permissions on a per-group or per-user basis. Permissions generally stack—that, is, the most permissive set of permissions available to you applies—unless you're talking about denied access. Denied access overrides any allowed permissions.

You can use the Security tab to modify the permissions for the printer. You can assign basic permissions to any user or group, as shown in Figure 16.32. Print permissions can be assigned as Allow or Deny if you use other permissions in Windows.

FIGURE 16-32nPrinter permissions shown on the Security tab

![](bbox=[0.343, 0.542, 0.715, 0.87])