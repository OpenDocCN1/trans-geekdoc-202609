
# FIGURE 26.39

Setting up advanced folder redirection under a root path

![](img/41a83208e6906a3732620203b836cea7_1350_0.png)

# FIGURE 26.40

Advanced redirection to the user's home directory

![](img/41a83208e6906a3732620203b836cea7_1350_1.png)

In Figure 26.41, we have configured three different security groups to redirect Documents using various methods within a single Group Policy object. This demonstrates how flexible folder redirection can be and how it can adjust to the needs of the organization.

# CHAPTER 26 ADVANCED USER ACCOUNT MANAGEMENT AND USER SUPPORT

# FIGURE 26.41

A variety of advanced folder redirection settings

![](img/41a83208e6906a3732620203b836cea7_1351_0.png)

# Managing Folder Redirection

You use Group Policy to configure folder redirection (see Table 26.6). You can use other Group Policy settings to manage how folder redirection is processed.

# TABLE 26.6 Folder Redirection Management GPO

| PATH | ENTRY | DESCRIPTION |
| --- | --- | --- |
| Computer Configuration \ Administrative Templates\Folder Redirection | Use localized subfolder names for Start and My Documents | 'The special folders in a profile will normally be localized; for example, what you see in an English version of Windows will be different from a German version. By default, folder redirection does not maintain these names. Enabling this policy will allow localized on a per-system basis. |
| Computer Configuration \ Administrative Templates\Folder Redirection | Redirect folders on primary computers only | Redirects only if the computer has been designated as the user's primary computer. |
| Computer Configuration \ Administrative Templates\Group Policy | Configure redirection policy processing | You can force folder redirection to work over links (off by default). You can also configure a folder redirection policy to process even if the policy has not changed. |

# TABLE 26.6 Folder Redirection GPO (CONTINUED)

| PATH | DESCRIPTION |
| --- | --- |
| User Configuration \ Administrative Templates\ System\Folder Redirection Do not automatically make redirected folders available offline | Redirected folders automatically synchronized with Offline Files. You can disable this behavior. |
| User Configuration \ Administrative Templates\System\Folder Redirection Do not automatically make specific redirected folders available offline | Allows you to prevent redirected shell folders from being available offline. |
| Computer Configuration \ Administrative Templates\System\Folder Redirection Redirect folders on primary computers only | Redirects only if the computer has been designated as the user's primary computer. |
| User Configuration \ Administrative Templates\System\Folder Redirection Use localized subfolder names when redirecting Start and My Documents | Provides the same functionality as the computer setting but on a user base. |
| User Configuration \ Administrative Templates\System\Folder Redirection Use localized subfolder names when redirecting Start and My Documents | The special folders in a profile will be localized; what you see in an English version of Windows will be different from a German version. By default, folder redirection does not maintain these names. Enabling this policy will allow localized names on a per-user base. |

# PRIMARY COMPUTER SUPPORT

Windows 2012 and Windows 8 have added Primary Computer, or user device affinity support to roaming profiles and folder redirection. What does this mean for you? You now have the ability to control what computers can access your user's redirected folders and/or roaming profiles. This feature can be enabled in many ways:

- * Reduces the login time when logging onto the user's primary computer.
- Reduces the risk of sensitive data left behind on a non-primary computer the user has logged onto, such as a conference room or kiosk computer.
- Prevents corruption of the user's profiles when using computers with different hardware configurations, such as x86 and x64 systems.

In order to take advantage of primary computer support, you will need to designate at least one primary computer for each user, following these steps:
1. Get the distinguished name of the user's computer.
   This can be accomplished using Active Directory Users and Computers using the advanced view. Open the properties window of the computer object, scroll down to the distinguishedName attribute, and copy it.

# CHAPTER 26 ADVANCED USER ACCOUNT MANAGEMENT AND USER SUPPORT

2. Get the distinguished name of the user's computer.
   This can be accomplished using Active Directory Users and Computers using the advanced view. Open the properties window of the computer object, scroll down to the distinguishedName attribute, and copy it.
![](img/41a83208e6906a3732620203b836cea7_1352_0.png)

3. Get the distinguished name of the user's computer.
   This can be accomplished using Active Directory Users and Computers using the advanced view. Open the properties window of the computer object, scroll down to the distinguishedName attribute, and copy it.
![](img/41a83208e6906a3732620203b836cea7_1352_1.png)

# Work Folders

Another new feature in Windows Server 2012 is Work Folders. This feature allows users to sync their data across multiple devices. When a user logs on to any computer, their Work Folders are available. This differs from folder redirection because Work Folders are presented in the same way as local folders. This is particularly useful for users who have access to multiple workstations.

# Installing Work Folders

Log on to the server. Open Server Manager console and add the Work Folders role; it can be found under Files and Storage Services. Or install the role by using the following command:

```powershell
Install-WindowsFeature FS-SyncServer
```

I should also point out that Work Folders clients communicate to the server only via SSL, so you will need to configure a public certificate or a self-signed certificate and make sure it's installed on all clients. You will also need to make the server available over the Internet, possibly via a reverse proxy or network gateway.

# Sync Share Configuration

The Work Folders interface is very simple and easy to use; you will find it as a node under Files and Storage Services. To create a new sync share, right-click in the Work Folders window and select New Sync Share, or select New Sync from the Tasks drop-down list. The Sync Share Wizard will open and guide you through the process.

- 1. The Server and Path screen will display all servers that have been added to your server with Work Folders. You have option of selecting an share from one of these servers or specifying a local path. Enter a local path of D:\SyncShare, as shown in Figure 26.42, and click Next.
- 2. The User structure that appears next will have two options: you can accept the default of "User alias" or "User alias@domain". "User alias" creates the folders as you currently do with folder redirection and home folders, whereas "User alias@domain" creates the @domain of each account to the folder name, which is useful if you have multiple domains with names that have the potential to conflict; see Figure 26.43. You also have the ability to single out a specific folder to be synced, omitting all the others that appear in the share. This could be useful for folder redirection, giving you the ability to sync the Documents folder but leave all of the redirected folders alone.

# FIGURE 26.42

New Sync Share
Wizard - User
and Path

![](img/41a83208e6906a3732620203b836cea7_1355_0.png)

# FIGURE 26.43

New Sync Share
Wizard - User
Folder Structure

![](img/41a83208e6906a3732620203b836cea7_1355_1.png)
