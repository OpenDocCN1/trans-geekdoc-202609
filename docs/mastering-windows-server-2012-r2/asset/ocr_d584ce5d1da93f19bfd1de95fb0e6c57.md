Windows servers located on the opposite side of the North American continent using this method. This is a reliable option for Server Core.

With Windows Server 2012 Server Core, you have to realize the desktop is still just the command prompt and few GUI tools. It's methods for publishing the command prompt of Server Core to your RemoteApp, but we don't recommend doing so. You will still need GUI tools as Task Manager, Notepad, and the Registry Editor, which are part of your Server Core essentials.

Remember, Remote Desktop and its firewall policy must be enabled to be available. We will tell this earlier in the "Initial Configurations for Server Core" section.

# MANAGING REMOTELY WITH MMC SNAP-INS

Administrators have found the Microsoft Management Console to be a versatile method of managing computers. Its strength lies in the use of the RPC protocol and integrated Windows authentication, making it quick and efficient in managing domain-based computers within a LAN.

You can run the authentication with alternate credentials. On the workstation, you can run the remote command to register these credentials:

```
cdkey /bfs1 /user:administrator /pass:P@ssw0
```

You could opt to leave the pass parameter empty to be prompted for password. After registering your credentials, you can connect to the server through the snap-ins.

In previous versions of Windows Server, you need to install the adminpak.msi package to have the snap-ins manage all the Windows services. In Windows Server 2012, the adminpak.msi package is replaced by the Remote Server Administration Tools. This features makes its installation easier and more fine-tuned. In Figure 3.10, you can see that Remote Server Administration Tools has been enabled through the Roles and Features Wizard.

FIGURE 3.10
Installing the Remote Administration Tools features

![](bbox=[0.298, 0.583, 0.882, 0.903])