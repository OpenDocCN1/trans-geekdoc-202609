operating with. By typing in whoami, we can print out the user ID of our shell. In this case, our user is the “user” user, which means that we will have privileges as that user.

WARNING If you exit the shell by using CTRL-C or if you don’t use the --uninstall flag, the service that’s created will remain on the target system. As an attacker, this is bad because you’re leaving a trace of the techniques you’re using for remote access. As a penetration tester, leaving artifacts makes it difficult to determine if another breach has occurred, and it may set off red flags after you’ve left a system. This doesn’t always come up right away. In six months, someone might ask if you left the service around. So, if you aren’t cleaning up, you’ll be left relying on notes to answer some very uncomfortable questions.

Finally, to leave our shell, we can just type exit at the command prompt. We should then see the Bash prompt, which lets us know that we have left the shell. On the server side, our service is being uninstalled and our connection closed.

# Lab 10-3: Using Winexe to Gain Elevated Privileges

In many cases, the things we want to do on a target system will require elevated privileges. In the previous lab, we were able to get access as a normal user, but we really want access as the SYSTEM user. Because this user has full privileges over the system, we can access credentials, memory, and other valuable targets.

To execute our attack, we’re going to use all the same options as our previous lab, but we’ll add in the --system flag. This will take care of escalation for us, and the end result is a highly privileged shell, as shown here:

```
# winexe -U User%Password1 --uninstall --system //192.168.1.13 cmd.exe
Microsoft Windows [Version 10.0.15063]
(c) 2017 Microsoft Corporation. All rights reserved.

C:\Windows\system32>whoami
whoami
nt authority\system
```

As you can see here, we’re now accessing the victim machine as the SYSTEM user. Although not part of the scope of this exercise, this allows us to dump credentials, create new users, reconfigure the device, and perform many other tasks that a normal user might not be able to do.

# Using WMI

Windows Management Instrumentation (WMI) is a set of specifications for accessing