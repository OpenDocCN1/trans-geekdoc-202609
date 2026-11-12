Administrative shares exist by default on all Windows NT–based systems (Windows NT, Windows 2000, Windows XP, and Windows Server 2003). These shares are designed to allow remote access to authorized users but have no place on a single-purpose Web server. To remove these shares, you can use the `net use driveletter /delete` command. For example, you can use this command:

```
net use c$ /delete
```

Each hard drive has an administrative share (C:\ = c$), and there are two special shares, ipc$ and admin$. Because these shares are restored on startup in certain configurations, you may need to create a batch file with the needed `net use` command entries and load the batch file into the system startup group. For a system with a single hard drive C:, you need to enter the following lines:

```
net share c$ /delete
net share admin$ /delete
net share ipc$ /delete
```

# Disabling services after setup

After you have completed the system install and you have logged onto the system as a user with administrative privileges (and before the system is connected to a public network), you need to disable a large number of services. To access and disable the services, follow these steps:

+   1. Right-click the My Computer icon on the desktop.
+   2. Select Manage from the context menu that appears.
+      The Microsoft Management Console (MMC) window appears.
+   3. Locate the Services and Applications entry. Click the + symbol next to it to expand the menu, as shown in Figure 2-1.
+   4. Find and click the Services entry.
+      The right side of the MMC window lists the services currently running on your system.
+   5. Right-click the listed service and select the Properties option from the context menu that appears.
+      The General tab of the Properties window appears, as shown in Figure 2-2.
+   6. Select Disabled from the Startup Type drop-down list.
+      The service is now disabled.