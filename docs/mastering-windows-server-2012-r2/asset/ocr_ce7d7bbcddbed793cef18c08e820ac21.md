# Rename Computers (Including Domain Controllers)

You can use the netdom computername command to rename domain controllers and member servers. In early versions of Windows, renaming a domain controller wasn't possible unless you first promoted it. Be aware that if you use Netdom to rename a domain controller, it may take a couple of reboots before everything settles—especially in DNS. More, you should not rename servers that are certificate servers (those running Active Directory Certificate Services). A certificate server needs to keep the same name. Name embedded in a certificate identifies the server it is issued to and the server that issued it. Certificates are validated by querying the original server, but if the name is changed, none of the certificates can be validated.

Renaming a DC gives it an alternate name and changing the alternate name to the DC's primary name. For example, if you have a domain controller DC01 in the bigfirm.com but you want to rename it to DC03, first give it an alternate name of DC03 with the following command:

```
Netdom computername DC01 /add:DC03.bigfirm.com
```

At this point, the server has two names: its primary name and an alternate name. Next, rename the computer to the alternate name with this command:

```
Netdom computername DC01 /makername:DC03.bigfirm.com
```

Netdom will indicate and prompt you to reboot the server. With your reboot, your domain controller will change the alternate name to its primary name.
As a last step you need to remove the old name DC01 from the domain controller computer object with this command:

```
Netdom computername DC03 /remove:DC01.bigfirm.com
```

Now your domain controller has a new name.

# Join a Computer to a Domain

If you want to join a computer to a domain from the command prompt or via a script, you can use Netdom. The simplest implementation is as follows:

```
Netdom join server01 /d:bigfirm.com /reboot
```

This command will join the computer named server01 to the domain bigfirm.com and force a reboot. Normally, the account for a computer that has joined the domain is placed into the Computers container. As mentioned previously, you can use the redirc command to have computer accounts created somewhere else.

It is also possible to fetch get with Netdom, but it tends to be more difficult than using the directory service command-line tools (such as DSMove). For example, if you want to move the computer account from the Computers container to the Sales OU, you could follow the NetDom join with the DSMove command.

```
Dsmove "CN=Server01,CN=Computers,DC=bigfirm.com,DC=com" -newparent
"OU=Sales,DC=bigfirm.com,DC=com"
```