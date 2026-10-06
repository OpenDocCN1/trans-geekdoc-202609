
# MANAGING PRINTER PROPERTIES 863

selecting the check box. This page includes the "List in the directory" check box that can be modified or by right-clicking the printer and selecting List in Directory.

## Printer Properties Ports Tab

The Tabs allow you to add, delete, and configure ports used by the printer. Most printers can receive data to print and also send data to the server to report on conditions such as low toner, power, and paper jam conditions. This page includes the "Enable bidirectional support" check box, which is selected by default to enable the printer to send and receive.

The most common reason to access this tab is to enable printer pooling. Printer-pooling allows you to add multiple print devices to a single printer.

As mentioned earlier in this chapter, the ratio of printers to print devices isn't always one. You'll see how to create multiple printers for a single print device, but here you'll see how to single printer multiple print devices.

Why would you do this? It's mostly a matter of efficiency. With the fast print devices available, busy offices have more jobs coming in than one device can handle. Keep things running smooth and reduce delays, you can distribute print jobs among multiple print devices. Print clients will all send their print jobs to the same printer, and the jobs will go to the printer that's least busy at any given time. This is called printer pooling. 16.31 shows the Ports tab with printer pooling enabled.

### FIGURE 16-31
Enabling pooling from the Ports tab

![](img/41a83208e6906a3732620203b836cea7_898_0.png)

In the figure that two ports are enabled. This is possible only when you add as many ports as you have print devices and your needs require.

There are a couple of catches to printer pooling. The first devices in the pool must use the same driver. Since many print devices use the same or similar internal parts, it's possible to have different print devices that use the same driver. However, if the devices require different drivers, they won't work in the same printer pool.

Second, we highly recommend putting the pooled print devices in the same physical location. Since users don't know which printer their job will print at, you don't have to wander from place to place looking for their print jobs.

## SEPARATOR PAGES

Consider separator pages with usernames in printer pools since users will not necessarily know which printer their job went to. Separator pages are explained in greater depth later in this chapter.

## Printer Properties Security Tab

Those familiar with current Windows-based operating system know that you secure the printer by defining user rights for what people can do on the network and setting permissions for the resources that people can use. Printer security is controlled with permissions on a per-group or per-user basis. Permissions generally stack—that, is, the most permissive set of permissions available to you applies—unless you're talking about denied access. Denied access overrides any allowed permissions.

You can use the Security tab to modify the permissions for the printer. You can assign basic permissions to any user or group, as shown in Figure 16.32. Print permissions can be assigned as Allow or Deny if you use other permissions in Windows.

### FIGURE 16-32
Printer permissions shown on the Security tab

![](img/41a83208e6906a3732620203b836cea7_899_0.png)

## MANAGING PRINTER PROPERTIES

Although three basic permissions are showing, there are actually granular permissions available.

You may remember from Chapter 10 that NTFS has basic permissions as Read that map to granular permissions; the basic Read permission maps to the four granular permissions of Read Data, Read Permissions, Read Attributes, and Read Extended Attributes. By assigning NTFS permission work similarly, though they aren't as complex. There are three basic permissions and three additional granular permissions. The basic permissions are as follows:

- Print: The user can send jobs to the printer. Print includes Read Permissions. The Everyone group is granted Print Permissions by default.
- Manage This Printer: The user can change printer properties and permissions on the printer. Manage This printer includes the following: Print, Read Permissions, Change Permissions, and Take Ownership. The Administrators, Server Operators, and Print Operators are all assigned the Manage This printer by default.
- Manage Documents: User can control document-specific settings and pause, restart, and delete spooled print jobs. This permission includes the following: Read Permissions, Change Permissions, and Take Ownership. The Creator Owner, Administrators, Server Operators, and Print Operators are all assigned the Manage Documents permissions by default.

When users send print jobs to the printer, they become a member of the Creator Owner group for that print job and manage that document.

## PERMISSIONS CUMULATIVE

If a user is granted multiple permissions because the user is a member of multiple groups, that person will be granted the cumulative value of all the permissions. For example, if a user is a member of the Everyone group and is granted Print permission and is also a member of another group and is granted Manage This printer permission, they have a combination of all the permissions.

The only exception is if Deny is used. If a user is a member of a group granted Print permission and a member of another group that is assigned Deny permission, Deny will always win. Just as Deny takes precedence in NTFS and share permissions with printer permissions.

You can use the basic permissions to accomplish most, if not all, of your requirements. However, if you click the Advanced button on the Security tab, you'll see... Figure 16.33.

## CHAPTER 16 SHARING PRINTERS ON WINDOWS SERVER 2012 R NETWORKS

### FIGURE 16-33
Editing permissions

![](img/41a83208e6906a3732620203b836cea7_901_0.png)

### AUDITING PRINTER ACCESS

Curious to know who's doing what to the printers under your care? You can turn to the Auditing tab (by clicking the Advanced button in the Security section of a printer's properties) to set up auditing. All auditing events will be recorded in the Security log.

It's relatively easy to enable auditing. The following steps will enable auditing of any successful printing to a printer:

- 1. Access the properties of the printer you want to audit, and select the Security tab.
- 2. Click Advanced, and select the Auditing tab.
- 3. Click Add, and then click the link "Select a principal."
- 4. Enter the name of the group you want to audit. If you want to audit all users, enter Everyone.
- 5. Select Check Names to ensure the group is recognized.
- 6. Your display will look similar to Figure 16.34. Click OK.
