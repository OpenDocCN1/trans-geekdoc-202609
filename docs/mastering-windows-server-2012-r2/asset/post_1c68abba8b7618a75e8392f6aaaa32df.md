
- 7. If that works—if there are no error messages—then you're finished. But if the transfer fails, then type seize fsmotype master: That's a bit more drastic, but it always works.
- 8. Type quit, and you should be finished.

For example, here is a session where we seized the RID Master role from a computer Bfi2.com to a computer named Bfi1.com (what we typed is in bold; the computer's responses are not bold)

```
C:\ntdsutil
tdsutil: roles
fsmo maintenance: connections
server connections: connect to server bfi1.test.com
Binding to bfi1.test.com using credentials of locally logged on user.
server connections: quitifsmo maintenance: transfer rid master
ldap_modify_sw error 0x3452 (Unavailable)
ldap extended error message is 00020AF: SvcErr: DSID-03210CB1, problem 5002
(UNAVAILABLE), data 1722
```

Win32 error returned is 0x20af(The requested FSMO operation failed.
The current FSMO holder could not be contacted.)

Depending on the error code this may indicate a connection,ldap, or role error.

Server "bfi.test.com" knows about 5 roles
Schema = CN-NTDS Settings,CN=BF1,CN=Servers,CN=Default-First-Site-Name,CN=Sites,CN=Configuration,DC=test,DC=com
Naming Master = CN-NTDS Settings,CN=BF1,CN=Servers,CN=Default-First-Site-Name,CN=Sites,CN=Configuration,DC=test,DC=com
PDC = CN-NTDS Settings,CN=BF1,CN=Servers,CN=Default-First-Site-Name,CN=Sites,CN=Configuration,DC=test,DC=com
RID = CN-NTDS Settings,CN=BF2,CN=Servers,CN=Default-First-Site-Name,CN=Sites,CN=Configuration,DC=test,DC=com
Infrastructure = CN-NTDS Settings,CN=BF1,CN=Servers,CN=Default-First-Site-Name,CN=Sites,CN=Configuration,DC=test,DC=com

fsmo maintenance:
Hmm, the transfer didn't work. Let's seize:

```
fsmo maintenance: seize rid master
Attempting safe seize of RID FSMO before seizure.
ldap_modify_sw error 0x3452 (Unavailable).
ldap extended error message is 00020AF: SvcErr: DSID-03210CB1, problem 5002
(UNAVAILABLE), data 1722
```

Win32 error returned is 0x20af(The requested FSMO operation failed.
The current FSMO holder could not be contacted.) Depending on the error code this may indicate a connection, ldap, or role transfer error.
Transfer of RID FSMO, proceeding with seizure ... Searching for highest rid pool in domain
Server "bfi.test.com" knows about 5 roles
Schema CN=NTDS Settings,CN=BF1,CN=Servers,CN=Default-First-Site-Name,CN=Sites
CN=Configuration,DC=bigfig,DC=com
Naming Master CN=NTDS Settings,CN=BF1,CN=Servers,CN=Default-First-Site-Name,CN=Sites
CN=Configuration,DC=test,DC=com
PDC CN=NTDS Settings,CN=BF1,CN=Servers,CN=Default-First-Site-Name,CN=Sites
CN=Configuration,DC=test,DC=com
RID CN=NTDS Settings,CN=BF1,CN=Servers,CN=Default-First-Site-Name,CN=Sites
CN=Configuration,DC=bigfig,DC=com
Infrastructure CN=NTDS Settings,CN=BF1,CN=Servers,CN=Default-First-Site-Name,CN=Sites
CN=Configuration,DC=test,DC=cmsmo maintenance:

## SEIZE AND SLICK

If you seize RID, domain name, or schema master, make sure the old master never comes
again, or AD havoc will result! If this domain controller comes up, it will still think
the FSMO role. So, contention between the old and the new one will occur.
It is highly recommended that you remove the network cable and erase the hard drive. We recommend
gending the installation CD and booting up to delete the system partition for a clean
installation.

## Time Sync

When it comes to replication and trusts, the AD needs all of its domain controllers to pretty
much agree about the current time and date. They don't have to be exactly the same, but they
need to be close—Kerberos fails if a domain controller, and the system trying to use that DC
authenticate, designate about what time it is by more than five minutes. Windows servers include
a service called Windows Time service that keeps all your Workstations and
servers in good sync.
Mines in AD stay in sync. The PDC emulator FSMO of the forest root—the
first created domain controller—is the "Master Server Dude." All other
servers automatically create a hierarchy, sort of like a "telephone tree," to distribute time
synchronization information. Everyone below top dog automatically gets synced from
some above it in the hierarchy, specifically:

- Member servers and workstations synchronize to the DC that has them in.
- DCs in a domain all look to the DC in their domain that holds the PDC Emulator
Operations Master role
- If there is more than one domain in the forest, then there will be more than one PDC emulator, because each domain has a PDC emulator.

## CHAPTER 24 CREATING LARGER ACTIVE DIRECTORY ENVIRONMENTS: BEYOND ONE DOMAIN

The PDC emulators must agree on the time, so they choose one of their numbers to be “source”—the PDC emulator for the first domain in the forest, the forest root. So, again, it’s the PDC Emulator FSMO for the forest root domain that is the ultimate authority.

But who syncs that top dog, don't need to sync the FSMO. All that matters in AD is that all the servers think it's the same time. So, it'd be nice if it was the actual time, but that's not necessary. If your whole enterprise was 10 minutes early, that would constitute no problem for AD, as all the servers are 10 minutes early.

## TIME ZONES AND SYNC

But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
But it's very important that you set the time correctly on the time.
