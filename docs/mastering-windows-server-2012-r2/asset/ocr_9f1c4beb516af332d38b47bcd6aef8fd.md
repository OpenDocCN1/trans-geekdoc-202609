If you want more details on the services, change list brief to list full. This simple tool can easily give you important documentation on multiple servers that you can easily print or save.

# ISSUING POWERSHELL COMMANDS WITH WinRS

Although WMIC is feature rich, it's not the only command you can use. Any command that you enter at the server can you enter remotely using WinRS. This includes PowerShell commands. The following link shows the PowerShell cmdlets:

```
http://msn.microsoft.com/en-us/windows/desktop/ee369371(v-vs.85).aspx
```

PowerShell commands follow a verb-noun format. The verb specifies an action, and the noun identifies the object on which the action will take.
The most popular verb is get, and if you enter get- at the PowerShell command prompt, you can tab through all the nouns associated with the get verb.
Other verbs use set, copy, move, and more. You can do the same thing with the verbs; the verb with a hyphen (-), and tab through all the nouns associated with the verb. For a list of the verbs, check this MSDN page: http://msdn.microsoft.com/en-us/library/ms714428(Vs.85).aspx.

For example, you can enter the following PowerShell command from the PowerShell prompt to check the status of services on a system:

```
Get-Service
```

You don't need to type the entire command. You can just type Get-S and press the Tab key.
This command will list all the services on the system (running or stopped), name, and display name. Using this with WinRS, you can execute the same command remotely:

```
WinRS -r:SR2012 PowerShell Get-Service
```

If you want to redirect this to a file, you can add the redirect character as follows:

```
WinRS -r:SR2012 PowerShell Get-Service > services.txt
```

The output will be stored in a file named services.txt. You can then open the file with Notepad from the command line with this command:

```
Notepad services.txt
```

# Remote Server Administration Tools

The Remote Server Administration Tools (RSAT) are tools to manage roles and features on a Windows Server 2012 R2 server from your operating system.
Although Remote Desktop Connection and Remote Desktops allow you to connect to the desktop of a server, you simply need to do a single task as resetting a password on a user account or verifying that DNS is configured correctly.

RSAT includes tools like Active Directory and Computers (ADUC) and the DNS console. After installing RSAT on a desktop, you can launch ADUC to manipulate user accounts, or you can launch the DNS console to verify DNS configuration.