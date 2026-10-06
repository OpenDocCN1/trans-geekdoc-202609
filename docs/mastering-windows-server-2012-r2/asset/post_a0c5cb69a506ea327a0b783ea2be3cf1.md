
# FIGURE 13.6 Selecting additional features for role services

![](img/41a83208e6906a3732620203b836cea7_691_0.png)

- 9. Click Install.

The final page of the wizard is the Results page. An installation progress bar will be displayed. The task will run in the background if you wish to finish the page and exit. You can always view task details in the command bar by clicking Notifications.

- 10. Upon successful installation, reboot the server manually, or if you select the Restart Automatically from the Confirmation page, the server will reboot when the install has finished.

At this point, Server Manager now includes all of the roles and features you installed from the exercise. If you use Server Manager and go to your dashboard, you will see that you can now view and use the installed roles and features by clicking them and selecting the desired resource. The File Server Manager features are shown in Figure 13.7.

# FIGURE 13.7 File Server Resource Manager tools

![](img/41a83208e6906a3732620203b836cea7_691_1.png)

# Creating Shares

The process of creating shares has undergone some nice changes in this server edition. It feels as though everything has a wizard to guide us through our tasks and actions. There are many different ways to create shares that are discussed throughout this Mastering Book. In this section we will focus on creating shares using Server Manager. No matter which method you use, you'll need either Administrator or Power User rights on the computer where you're creating the shares.

Once a share is created, it can be published to Active Directory to make it easy for users to locate the share. You'll learn how to create shares using Server Manager and publish the shares to Active Directory in this section.

# Creating Shares with Server Manager

It's relatively easy to add shares using Server Manager. The tabs, found in File and Storage Services, has a New Share Wizard to help you with this task:

- 1. If not already started, launch Server Manager by selecting the Server Manager icon to the taskbar or your desktop, or by selecting the Server Manager tile from the Start screen.
- 2. Select File and Storage Services, and then select Shares.
- 3. Right-click the Shared Folder location page, and click New Share. You can also select New Share from the Tasks drop-down menu. Either action will launch the New Share Wizard, as shown in Figure 13.8.

![](img/41a83208e6906a3732620203b836cea7_692_0.png)

# CHAPTER 13 FILES, FOLDERS, BASIC SHARES

The first screen, Select Profile, gives you the choice of which profile protocols to use when creating your share. There are two main choices and a few subchoices. You can either create an SMB share or an NFS share. In general:

- SMB shares are used for Windows operating systems. 
- NFS shares are used to talk to Unix-based machines.

SMB and NFS have both Quick and Advanced share profile options. The Advanced profile has a few configuration options that include enabling quotas. You can always add the extra features later using Server Manager. If you decide to enable quotas, you will be required to build a new quota template first or edit an existing template. SMB has one extra profile called SMB Share - Applications. This creates an SMB file share with additional settings used in a virtual environment.

- 4. For this exercise let's use the SMB Share - Quick profile shown in Figure 13.9. Select the Quick profile and click Next.

# 13.9
Selecting a profile

![](img/41a83208e6906a3732620203b836cea7_693_0.png)

# NFS FOR UNIX CLIENTS

The NFS option will not be usable if the Services for Network File System role is not added to the server. If you later decide you want to support for Unix clients, you can always add the service. The NFS selection will be available to use in the New Share Wizard once the feature is turned on.

- 5. On the Share Location page, choose which server will host the share, and also select which volume on the server will serve as the share location.

Please note that you can only create a share on a server that has the File Services Resource Manager installed.

- 6. Click Next.

The Share Name page allows you to define the name of the share and provide a share description, and it shows you both the local and remote network paths needed to reach it.

- 7. Take note of this information, because you will need to provide these network paths to your users for access. Figure 13.10 provides an example of naming a share. Click Next.

FIGURE 13.10
Naming a share

![](img/41a83208e6906a3732620203b836cea7_694_0.png)

The Other Settings page gives you four additional features to help make your share more robust:

- The "Enable access-based enumeration" feature will automatically hide a folder from a user who does not have permission to read the folder.
- The "Allow caching" option provides offline users access to the shared data when offline.
- Since you installed the BranchCache role in the previous exercise, you can now select the "Enable BranchCache" option on the file share on this page of the wizard.
- The last option on this page, "Encrypt data access," secures remote file access to and from the share.

# CHAPTER 13 FILES, FOLDERS, AND BASIC SHARES

If you have not yet turned on encryption for server, go ahead and select this option now. If it's greyed out and already checked, then you already have encryption turned on for this server.

- 8. Make your selections and click Next.

- 9. The Permissions page gives you an opportunity to change the NTFS permissions if desired. We'll cover NTFS permissions later in the chapter, but for now click Next to accept the default NTFS permissions.

- 10. The Confirmation page gives you a summary of all the choices you have made for creating your share. Review them for accuracy, make any desired changes, and then click Create. Figure 13.11 shows the Confirmation page.

# Figure 13.11 The Confirmation

![](img/41a83208e6906a3732620203b836cea7_695_0.png)

The final page of this wizard is the Results page. Two progress bars will be displayed: one bar for the Create SMB task and one bar for the Set SMB Permissions task. Once the Status shows Completed, the share is built and ready for use.

- 11. Click Close to finish the wizard.

# Creating Shares on Remote Computers Using Server Manager

It's also possible to perform the previous procedure to create shares on remote computers using Server Manager. Just like in previous editions, Server Manager can perform much tasks on remote computers. Remote Management is installed and enabled by default with servers running Server 2012. In Figure 13.12 you can see the different options that Server Manager provides when another server has been added.

# FIGURE 13.12
Management tasks on a remote server

![](img/41a83208e6906a3732620203b836cea7_696_0.png)

# MANAGING WINDOWS SERVER 2008 FROM SERVER 2012

In order to fully manage servers running Windows 2008, a few updates are required. First, install .NET Framework 4.0 and then install Windows Management 3.0. You will need to ensure the remote computer is configured correctly, which can be done by entering these commands:

- 1. Enter the following command on the computer you want to administer. This will enable WinRM:
winrm qc
- 2. When prompted, type Y and press Enter.
- 3. Ensure the Virtual Disk Service is running on the remote computer. You can do this with the command line:
sc config vds= auto
net start vds

# Real World Scenario

### SETTING USER LIMITS

You can configure how many users can connect to a share by configuring the "User limit" option on the properties page. To set the user limit; open Administrative Tools, double-click Computer Management, expand Shared Folders, right-click the share you wish to set a limit on, and then select Properties. Here is a screenshot of setting the user limit on a share.

![](img/41a83208e6906a3732620203b836cea7_697_0.png)

As an example, if an application under your share is licensed for 100 concurrent users, you can configure your server share to maintain that limit, even though you have 200 users on your network. Just select the "Allow this number of users" radio button, and fill in the appropriate number (defaults to 1). As users connect to the share, they build up to the user limit. As users log off or disconnect from the share, the number drops.

Be careful with your licensing, though. Not all applications have a concurrent license mode, although they might have a client license mode. With client license mode, the manufacturer doesn't care how many users are accessing the application at any given time; they just care how many people have installed the application altogether. This user limit option will not protect you in these cases.

Another thing to keep in mind is that this user concurrency limit is based on the entire share. It cannot be defined for each folder within a share. For example, you could have two applications in a single share. Application 1 has a concurrency limit of 100, and application 2 has no limits. You might inadvertently limit access to application 2 when the share limits the connections to 100. The easy solution is to use different shares if different limits are needed.
