
# REMOTE SERVER ADMINISTRATION TOOLS

FIGURE 17-40

Adding the Remote Server Administration Tools feature

![](img/41a83208e6906a3732620203b836cea7_960_0.png)

You can pick and choose individual feature and role administration tools if desired, You can simply add them all by selecting the Remote Server Administration Tools check box.

- 1. Click OK. The tools will be configured to work on your system.

If Administrative Tools does not show on your Start menu, you can add the tools by following these steps:

- 1. Right-click the Start menu, and select Properties.
- 2. Ensure that the Start Menu tab is selected, and click Customize.
- 3. Scroll to the "System administrative tools" section to the bottom of the customization window. Select "Display on All Programs and the Start menu.".
- 4. Click OK twice.

Once RSAT is installed on a system, you can use the tools in the same way you would use them on a server.

# Remote Desktop and PowerShell

Before we close this chapter, let's discuss how you can use PowerShell to remotely connect another PowerShell session. If you do not plan on using PowerShell to remotely administer your server, then you can skip this section. If you plan on using PowerShell, then stick around and see how you can connect remotely using PowerShell cmdlets.

When you are sending cmdlets to the server, you will need to provide a username and password just like in the Remote Desktop UI. If you have to type several commands, you will have to enter this username and password for each command. To get around you can assign the username and password to a session variable that will be held the credentials for you.

When you enter the following command, you will see a login pop-up appear to enter your credentials (see Figure 17.41).

$cr = Get-Credential -Credential jpwebconsulting\administrator

![](img/41a83208e6906a3732620203b836cea7_961_0.png)

Now all your login information is stored in the $cr variable. You will see in the next cmdlet how this will be use of you. The next cmdlet you will use is your connection to the remote system. You can now see the variable in use:

```
Enter-PSSession -Computer TestServer-1 -Credential $cr
```

You are connected remotely to the server via PowerShell. You should see the following command prompt, and you will see that it switched to TestServer-1. You can now administer the server as if you were sitting in front of it. I bet you didn't think that was easy![TestServer-1]: PS C:\Users\Administrator\Documents>

# The Bottom Line

Configure Windows Server 2012 R2 servers for remote administration. Servers must be configured to allow remote administration before administrators can connect remotely.

**Master It** Configure a server to allow remote connections by clients running RDC version 6.0 or greater.

Remotely connect to Windows Server 2012 R2 servers using Remote Desktop Connection. You can remotely connect to servers to do almost any administrative work. Servers are often located in a secure server room that is kept cool to protect the electronics. They can be in a different room, a different building, or even a separate geographical location, but they can still be remotely administered using either RDC or Remote Desktops.

**Master It** Connect to a server using RDC. Ensure your local drives are accessible when connected to the remote server.

Remotely connect to Windows Server 2012 R2 servers using a Remote Desktop Protocol file. If you regularly connect to a remote server using RDC, you can configure an RDP file that can be preconfigured based on your needs for this server. This RDP file will store all the settings you configure for this connection.

**Master It** Create an RDP file that you can use to connect with a server named Server1. Configure the file to automatically launch Server Manager when connected.

Configure a server for Remote Assistance. When your environment includes remote locations where junior administrators may occasionally need assistance, you can use Remote Assistance to access their session and demonstrate procedures.

**Master It** Configure a server for Remote Assistance.

Install the Remote Server Administration Tools. The Remote Assistance Administration Tools (RSAT) include the snap-ins and command-line tools needed to manage Server 2003, Server 2012.

**Master It** Install the Remote Server Administration Tools.
