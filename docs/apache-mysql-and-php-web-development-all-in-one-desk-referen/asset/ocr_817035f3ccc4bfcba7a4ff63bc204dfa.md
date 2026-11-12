client and the server. Not only is the logon information protected, but the data transferred is protected as well. Virtually all modern Linux distributions include an SSH implementation, but if it is not present, you can download it. To install SSH, you can download the source, run the ./configure script, and then run the make and make install commands. For more information on the installation process for SSH, see www.openssh.com.

# Misleading Binaries (SUID/GUID Binaries)

In addition to network services, some of the programs on your Linux system can be real liabilities because they need root privileges to do much. Some programs use a specialized bit (set on the binary itself) — called either Set User ID (SUID) or Group User ID (GUID) — to gain more privileges than the user who might run the program or use its services. For example, if users want to send e-mail, they need to use the services of an SMTP server such as Sendmail. However, they probably won't have all the rights needed to perform all the tasks that the mail server needs to do. To perform the needed tasks, Sendmail often runs with the Set User ID bit set to use root account privileges.

Any program that uses SUID/GUID to run with elevated privileges is a liability. If a malicious user gains control of the application, that user may be able to interact with the system using the elevated system rights provided by the SUID/GUID setting. Fortunately, you can easily identify the binaries that have been configured to use the SUID/GUID funtionality. If you check the file attributes of a binary and see an s where you would normally see an r or x (r-sr-xr-x, for example), you have a binary using SUID/GUID. So how do you find and, if not needed, disable these binaries? The easiest method is to use the find command to search the entire system and build a list of the SUID/GUID-enabled applications. Here's an elegant solution that uses the find command with the option to dump the output to a text file:

```
find / \ (-perm -4000 -o -perm -2000 \ ) -exec ls -ldb {} \ ;
>> /tmp/suids
```

This command creates the text file suids in the /tmp directory with information about all the binaries using the SUID/GUID capability. You can find and delete any binaries that you know you don't need. If you determine that some of the binaries may prove useful, you can refine their access rules (by using the CHMOD command) so that not just anyone can run them. This is especially useful if one of the remaining binaries needs to be granted root access.