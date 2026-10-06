# UNDERSTANDING ACTIVE DIRECTORY'S

dots in it). The DNS client is supposed to perform the query to the GlobalName zone when the primary and alternate DNS suffixes have failed.

The steps to configure this are not difficult given the earlier discussions:

+   1. Create a zone with the name GlobalNames.

An Active Directory integrated zone is recommended to provide replication to other domain controllers.
2. Enable GlobalNames support with the Set-DNSServerGlobalNameZone command:
:\Users\Administrator.DC1>Set-DNSServerGlobalNameZone -Enable $True
3. Replicate the zone to other domain controllers.

Remember to add these domain controllers to the specific hosts.
4. Add CNAME records in the zone to redirect to specific hosts.

In our example, we redirected to hostrecord.PrimaryZone.local, as shown in Figure 6.29.

![](bbox=[0.19, 0.396, 0.903, 0.626])

+   5. Add a service location record if you need any other Active Directory forests to query the global name:

You can use the Nlookup utility to test the resolution of the global name:

```
C:\Users\Administrator.DC1>nslookup
Default Server: DC01.bigfirm.com
Address: 192.168.0.1
```

+   > WWW
Server: DC01.bigfirm.com
Address: 192.168.0.1

Name: hostrecord.primaryzone.local
Address: 192.168.0.21
Aliases: bigfirm.com