# CHAPTER 7 ACTIVE DIRECTORY IN WINDOWS SERVER 2012

W32tm /stripchart /computer:time.windows.com /samples:5 /daemonly

You can synchronize the time with the PDC Operations manual using an internal time source if you have one or an external time source if not. If you synchronize with an external NTP server using the w32tm service, you need to ensure that UDP port 123 is open.

Use the following command to have your system synchronize it with an external time server. Time servers are available, but this example uses Microsoft's time server (time.windows.com) and the NIST time server (time.nist.gov).

```
w32tm /config "manualpeerlist:nist.gov,time.windows.com" /syncfromflags:manual/reliable:yes /update
```

The syncflags parameter specifies that the server will synchronize with one of the servers in the manualpeerlist group. You can add a single time server (and omit quotes) or add multiple time servers separated by comma, as shown.

It is also good idea to restart the service using the following commands:

```
Net start w32tm
Net stop w32tm
```

After you restart, you can use the early w32tm command to verify that the time is now accurate. If you change the time, it may take as long as five minutes before w32tm synchronizes again and resets the time to the proper time.

This section covered several maintenance tasks and techniques you will likely find useful to keep your network running. It is certainly not an all-encompassing list, but it should help you master some of the basics. A neat newer feature that can help reduce the amount of maintenance you need to do is fine-grained password policies. This feature allows you to set multiple password account lockout policies without creating a new domain.

# FSMO ROLES AND HOW TO MOVE THEM

Active Directory holds the Flexible Master Operations roles (FSMO), which are used for different tasks within the forest and domain. There are two-forest roles and three domain-wide roles. Table 7.1 lists the role name, scope, and its purpose.

| Table 7.1: | FSMO roles |
|---|---|---|
| FSMO ROLE | SCOPE | PURPOSE |
| Schema Master | Forest | Hold the forest's schema |
| Domain Naming Master | Forest | Manage the domain names |
| Infrastructure Master | Domain | Ensure-cross-domain object references |
| PDC Emulator | Domain | Responsible for the time in the forest
Handle password changes
Connection point for managing GPOs
Account lockouts |
| RID Master | Domain | Manage and replenish the RID pools |