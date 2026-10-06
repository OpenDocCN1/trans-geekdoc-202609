# CHAPTER 2 INSTALLING AND UPGRADING TO WINDOWS SERVER 2012 R2

# Installing Roles Using PowerShell

You can install roles and features using PowerShell. If you are managing Windows Server 2012 R2, you'll need to use PowerShell, Microsoft's scripting and command language. The subject of PowerShell is huge. We'll use the relevant Server Manager-related cmdlets (pronounced "command-lets") here.

At first, PowerShell might seem a bit clunky to use. But you will find that after a little while it is much quicker to use than the GUI, and you can also use it in a scripted form for customizing servers. It's very handy if you use a cloning or unattended mechanism for installing Windows or if you are building loads of servers. You just deploy an image and run the appropriate script or unattended answer file to customize generic image to be the server you.

You can launch PowerShell from the superb, or a really cool way to do it is pressing the start button and right-clicking the PowerShell button box. You will see a new menu bar at the bottom. Make sure you launch it with administrative rights. The PowerShell modules related to Server Manager are not loaded by default. This command to load them:

```
PS:\Users\Administrator> import-module ServerManager
```

You can run the command with the Get-WindowsFeature cmdlet to report on what roles, role, and services are installed:

```
PS:\Users\Administrator>Get-WindowsFeature
```

The generated report is pretty long, eh? We'll have to forgive us for not including the entire thing (see Figure 2-45!) We have rain features to think about, so we've included snippets of the query results.

None of the role, role services, or features are with our IIS since we already added that one. X designates that the role, role feature, or feature is installed as is is. Here, we are working with a fairly blank server. You will see in Figure 2.46 that our Web IIS is installed.

For example, you want to install an FTP server, which you can see at the bottom of Figure 2-45 name is still available to be install. Note in figure that the role has a Name column. The FTP service name is Web-Ftp-Server. We'll use that designation with the Install-WindowsFeature cmdlet.

```
PS:\Users\Administrator>Install-WindowsFeature -Name Web-Ftp-Server -Restart..
```

| Success | RestartNeeded | Exit Code | Feature Result |
| --- | --- | --- | --- |
| True | No | Success | {Web-Ftp-Server, Web-Ftp-Service} |

```
PS:\Users\Administrator>
```

That pretty simple, eh? And it was much faster than what we wanted, and we could run it as fast as we type it, using the GUI. We knew that depending on your typing skills, may not have all of that fast!

Some roles, role services, or features will require a reboot. You can have this automatic by adding the -restart flag to each of your command.