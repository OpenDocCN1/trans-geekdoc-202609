
# USING SERVER MANAGER TO CONFIGURE YOUR SERVERS

You can alternatively accomplish the previous remaining procedure by running the netdom command from the command prompt

```cmd
C:\netdom /renamecomputer WIN-DCL9MRNLVHO /newname:BIGFIRMAPPSVR1
This operation will rename the computer WIN-DCL9MRNLVHO
```

Certain services, such as the Certificate Authority, rely on a fixed machine name. If any services of this type are running on WIN-DCL9MRNLVHO, then a computer name change would have an adverse impact.

Do you want to proceed (Y or N)?
y
The computer needs to be restarted in order to complete the operation.

The command completed successfully.
C:\

The syntax for /renamecomputer <Current Computer Name> /newname:<Desired Computer Name>

You will need to manually reboot the server after running this netdom command.
After the reboot, log in again, and fire up Server Manager. You'll see that your new computer name is present in Computer Information.

# JOINING A DOMAIN

Odds are you want to join the server so that it can use shared resources and be centrally managed. Return to the Computer name properties.
We are joining this server to a domain that has the DNS name of Big.com (see Figure 2.32). Once you've entered that name, click OK. You will be asked to enter the username and password of a user with permission to add this server to the domain. That might be bigfirm\administrator, or it might be bigfirm\blogs if your blogs have been those delegated rights in Active Directory. Close all the dialog boxes and reboot, and you'll see a server is a member of the domain and able to take advantage of Group Policy, Active Directory user accounts and security groups, centralized administration, and so on.
Alternatively, you can also do the procedure from command line:

```cmd
C:\netdom join bigfirmapppsvr1 /Domain:big.com /UserD:bigfirm\administrator /PasswordD:*
```

Type the password associated with the domain user:
The command completed successfully.
C:\

The syntax for the command is as follows:
netdom join <name of computer joining domain> /Domain:<domain to be joined> /UserD:<name of domain user with permission to join the domain> /PasswordD:*

# CHAPTER 2 INSTALLING AND UPGRADING WINDOWS SERVER 2012 R2

FIGURE 2.32
Domain membership change

![](img/41a83208e6906a3732620203b836cea7_89_0.png)

After you run this command, you are prompted for the username of the user account. Once the join command is run, you are told that you need to reboot. You could initiate automated reboot by adding the /REBOOT flag, as shown here. You might prefer to control the timing of reboots as much as possible and initiate a manual reboot.

```cmd
net dom join bigfirmappsv1 /Domain: bigfirm.com /UserD:bigfirm\administrator /PasswordD:* /REBOOT
```

# WHY THE COMMAND LINE?

You might be wondering why we are showing you these command-line alternatives. You will need to know these if you are doing any of the following:

- *Working with Windows Server 2012 R2 Server Core where there is no alternative. Windows Server 2012 R2 includes a handy tool called configserver.*
- Being able to run these commands without reference can be quicker than navigating through a GUI.
- If you are building many servers by hand or using some third-party cloning solution, then you might want to script as as much as possible.

# ENABLING REMOTE ADMINISTRATION

Most Windows administrators want to be able to manage their servers from their desktops. Who really wants to go grotting off the computer room every time they need to make some change on a server? You can do this by enabling Remote Desktop on your server. You can use the Remote Desktop tool on your PC or laptop to connect to it over TCP 3389, in other words, the Remote Desktop Protocol (RDP). Your organization's security policies will define when remote administration can be enabled, if at all.

If you want to enable RDP access, inside the Local Server Properties window click the link next to Remote Desktop, which should clearly be labeled Disabled.
You can see in Figure 2.33 that RDP is disabled by default.

FIGURE 2.33
Configuring Remote Desktop
Local Server

![](img/41a83208e6906a3732620203b836cea7_90_0.png)

There are two other options:

**Allow Connections from Computers Running Any Remote Desktop (Less Secure)** This allows the versions of the Remote Desktop tool prior to version 6 to connect to your new server. Server 8 includes new security functionality, so Microsoft would prefer you to use it. Note that Remote Desktop version 8 is included in Windows Server 2012 R2. Older operating systems such as Windows XP and Windows Server 2003 require a free update that you can get from Windows Update or from the Microsoft website.

**Allow Connections Only from Computers Running Remote Desktop with Network Level Authentication (More Secure)** This is Microsoft's preference if you enable RDP access. Note that you must have at least version 6 of Remote Desktop on all possible administrative computers to use this option.

By default, only people who are members of the local Administrators group on your server will be able to access it via RDP. That suits most scenarios. However, you might want to delegate certain low-level functions to non-administrators. If so, you will need to Select Users and add the account names or, preferably, the security group names of those to whom you are granting RDP connectivity.

At this point, your server is on the network, you have added it to a domain, and you have enabled Remote Desktop so that you can work on it from your desktop. It's time to add some functionality to your Windows Server 2012 R2.

# Adding and Removing Roles and Features

So far, you have installed a new Windows Server 2012 R2 machine, and you have configured so that it is on the network and can be managed remotely. You're ideally standing at your desk with a nice drink. It sounds much better than standing in a cold server room.

Before you go forward with Server Manager, we'll define some terminology that you've seen several times in this chapter:

- **Roles**: A role is a generic function that a server hosts. It could be something like a DNS server or a web server. Each role comes with a set of functionality that can be installed onto a server to perform these tasks. They're called *role services*.
- **Features**: A feature is a piece of software that has a granular function of particular.

One important note that we should mention is Features are now part of the Add Roles and Features Wizard. In Windows Server 2008 R2 it was a separate tool. This set is extensible. It means that other roles and features can be made available by Microsoft as time goes.

## INHERITED ROLES AND FEATURES

A clean installation of Windows Server 2012 R2 will have no installed features or roles. Microsoft is not going to make any assumptions for you. This allows you to build customized servers with a minimized security risk. However, an upgraded server will include roles and features that Windows Server 2012 R2 can identify. For example, if your Windows 2008 server was a DNS server, then your upgraded server with Windows Server 2012 R2 will have a DNS server role installed. You may actually decide that you want to remove some of these inherited roles or features they are inappropriate for your Windows 2012 R2.

# ADDING A ROLE

A role can be described as a major function that a server can play in your network. When you install a role, you are installing a set of components to enable that functionality. There is a default set of components for each role that you can customize.

You'll learn how you can add a role using Server Manager and PowerShell. First, fire up Server Manager. You can see on the left side of the Server Manager dashboard the menu items Dashboard, Local Server, All Servers, and File and Storage Services. What you don't see any
