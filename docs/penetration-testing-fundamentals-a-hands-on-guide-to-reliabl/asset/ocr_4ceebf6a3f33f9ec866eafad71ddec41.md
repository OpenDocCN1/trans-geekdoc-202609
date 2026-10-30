# Summary

This chapter reviewed some fundamental aspects of Microsoft Windows. It is important for a penetration tester to be familiar with the operating system he or she is testing. We also examined some specific techniques and tools that can be used in Windows to check if a system has been compromised. While some of these techniques are not, strictly speaking, penetration testing, they are part of a security audit.

Keep in mind that this is just an introduction to hacking Windows. The best approach is to learn as much as you can about the current version of Windows. This is the most effective way to test security flaws in Windows. Also keep in mind we will see other Windows hacks later in this book when we examine Metasploit.

# Test Your Skills

# MULTIPLE CHOICE QUESTIONS

1. John is trying to get a list of passwords from a machine, so that he can enter these into a rainbow table and try and retrieve the password. What tool would be most helpful to him?

+   A. pwdump
+   B. ophcrack
+   C. sid2user
+   D. regedit

2. Typing "\\ipaddress\c$" at the runline (i.e. Start > Run) is an attempt to accomplish what?

+   A. Remote desktop into target machine
+   B. Find shares on a Windows machine
+   C. Enumerate users on a target machine
+   D. Log in to a Linux machine

3. What does this script accomplish?

```
net user /domain /add localaccountname password
net group /domain "Domain Admins" /add localaccountname
```

+   A. Attempts to get the password for the domain admin
+   B. Attempts to change the password for the domain admin
+   C. Attempts to add localaccountname to the domain admins group
+   D. Nothing, because this script is incorrectly written