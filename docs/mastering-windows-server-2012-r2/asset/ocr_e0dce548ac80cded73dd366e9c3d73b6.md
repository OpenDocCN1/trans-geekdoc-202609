By default, only people who are members of the local Administrators group on your server will be able to access it via RDP. That suits most scenarios. However, you might want to delegate certain low-level functions to non-administrators. If so, you will need to Select Users and add the account names or, preferably, the security group names of those to whom you are granting RDP connectivity.

At this point, your server is on the network, you have added it to a domain, and you have enabled Remote Desktop so that you can work on it from your desktop. It's time to add some functionality to your Windows Server 2012 R2.

# Adding and Removing Roles and Features

So far, you have installed a new Windows Server 2012 R2 machine, and you have configured so that it is on the network and can be managed remotely. You're ideally standing at your desk with a nice drink. You can complete the rest of the configuration in relaxed comfort. It sounds much better than standing in front of a noisy machine in a cold server room.

Before you go forward with Server Manager, we'll define some terminology that you've seen several times in this chapter already:

+   **Roles** A role is a generic function that a server hosts. It could be something like a DNS server or a web server. Each role comes with a set of functionality that can be installed onto a server to allow that to perform these tasks. They're called *role services*.

+   **Features** A feature is a piece of software that has a very granular function of particular.

One important note that we should mention is Features are now part of the Add Roles and Features Wizard. In Windows Server 2008 R2 it was a separate tool. This set is extensible. It means that other roles and features can be made available by Microsoft as time goes.

> INHERITED ROLES AND FEATURES

A clean installation of Windows Server 2012 R2 will have no installed features or roles. Microsoft is not going to make any assumptions for you. This allows you to build customized servers with a minimized security risk. However, an upgraded server will include roles and features that Windows Server 2012 R2 can identify. For example, if your Windows 2008 server was a DNS server, then your upgraded server with Windows Server 2012 R2 will have a DNS server role installed. You may actually decide that you want to remove some of these inherited roles or features they are inappropriate for your Windows 2012 R2.

# ADDING A ROLE

A role can be described as a major function that a server can play in your network. When you install a role, you are installing a set of components to enable that functionality. There is a default set of components for each role that you can customize.

You'll learn how you can add a role using Server Manager and PowerShell. First, fire up Server Manager. You can see on the left side of the Server Manager dashboard the menu items Dashboard, Local Server, All Servers, and File and Storage Services. What you don't see any