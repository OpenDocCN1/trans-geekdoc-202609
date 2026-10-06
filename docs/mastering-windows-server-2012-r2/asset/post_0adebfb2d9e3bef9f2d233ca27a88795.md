
# CHAPTER 7 ACTIVE DIRECTORY IN WINDOWS SERVER 2012

## Join the PowerShell Way

Netdom is a very good tool to manage your domain, and there are certain tasks that only Netdom can fulfill. In terms of joining computers to the domain, PowerShell can help you if you need to add multiple computers to a domain or even if you need to remotely add workgroup computers to the domain. The basic command is

```bash
Add-Computer -Name Server01 -LocalCredential Server01\Administrator -DomainName "bigfirm.com" -OU="Sales,DC=bigfirm,DC=com" -Credential bigfirm\administrator -Restart
```

You can run this command from a Windows Server 2012 domain controller and remotely join Server1 to the domain. If you run this command, you will be prompted for a password; the first prompt is to set the local administrator password (-LocalCredential parameter) and the second prompt is the account that needs permission in the domain to create the account (-Credential).

## Other Netdom Commands

Netdom includes many other commands that can be used to manage your domain. Check out the full online reference at http://technet.microsoft.com/en-us/library/cc772217.aspx.

These are some other commands that may be of interest to:

- Netdom Reset: Resets a machine's account. Sometimes you will sit down at a system and be unable to log onto the machine that has lost its domain account, or so says. Sometimes just resetting the job.
- Netdom Reset Pwd: Resets a machine's domain password. You must be sitting at the machine for this to run. If a machine has not connected to the domain for an extended period, it's possible that this account's password has expired, and this command can resolve the problem.
- Netdom Remove: Removes a system from a domain.
- Netdom query fsmo: Sometimes you need a quick way to find your Operations Master roles within your domain. Instead of clicking different GUIs, just run this and all your Operations Master roles will be displayed.

## MANAGING THE DOMAIN TIME

The Kerberos authentication protocol used by Active Directory requires that all computers in the domain be synced with each other. If any computer becomes more than five minutes from a domain controller, you will be able to connect to the network but all services might not work properly until the time is corrected.

Because of this, time synchronization is very important in a domain. Time synchronization is achieved through a hierarchy. It starts with the server holding the role of the PDC Operations Master (normally the first domain controller created in the domain) and extends to each system in a domain. You can check which server holds this role by following these steps:

- 1. Launch Active Directory Users and Computers.
- 2. Right-click the domain and select Operations Masters.
- 3. Select the PDC tab, as shown in Figure 7.28.

### FIGURE 7.28
Operations Masters PDC tab

![](img/41a83208e6906a3732620203b836cea7_342_0.png)

Ideally, the domain controller hosting the PDC role is configured to synchronize with a valid Network Time Protocol (NTP) source. The rest of the computers in the domain will get their time from this server.

- All domain controllers will synchronize their time with the time on the PDC.
- All computers and member servers will synchronize their time with the time on their authenticating domain controller.
- If a computer is specially configured so that it doesn't get its time from the authenticating DC, it should be synchronized with an NTP server just like the PDC Operations Master DC.

As long as the PDC has the correct time and users don't change the time on the systems, everything works well.

## RESTRICT TIME CHANGES WITH GROUP POLICY

It is not uncommon for administrators to configure Group Policy to prevent users from changing the time and accidentally removing their systems from the domain. The System Group Policy setting is located in Computer/Policies/Windows Settings/Security Settings/Local Policies/User Right Assignment.

You will use the Windows Time Service (w32tm) to check and synchronize the time. W32tm is executed from the command-line—you can use the following command to check five samples of current time against Microsoft’s time server (at time.windows.com) and verify how accurate they are. The output will indicate whether the time on your server is ahead (indicated with a +) or behind (indicated with a -):

```bash
w32tm /stripchart /computer:time.windows.com /samples:5 /daemon
```

You can synchronize the time with the PDC Operations manual using an internal time source if you have one or an external time source if not. If you synchronize with an external NTP server using the w32tm service, you need to ensure that UDP port 123 is open.

Use the following command to have your system synchronize it with an external time server. Time servers are available, but this example uses Microsoft's time server (time.windows.com) and the NIST time server (time.nist.gov).

```bash
w32tm /config "manualpeerlist:nist.gov,time.windows.com" /syncfromflags:manual/reliable:yes /update
```

The syncflags parameter specifies that the server will synchronize with one of the servers in the manualpeerlist group. You can add a single time server (and omit quotes) or add multiple time servers separated by comma, as shown.

It is also a good idea to restart the service using the following commands:

```bash
Net start w32tm
Net stop w32tm
```

After you restart, you can use the early w32tm command to verify that the time is now accurate. If you change the time, it may take as long as five minutes before w32tm synchronizes again and resets the time to the proper time.

This section covered several maintenance tasks and techniques you will likely find useful to keep your network running. It is certainly not an all-encompassing list, but it should help you master some of the basics. A neat newer feature that can help reduce the amount of maintenance you need to do is fine-grained password policies. This feature allows you to set multiple password account lockout policies without creating a new domain.

## FSMO ROLES AND HOW TO MOVE THEM

Active Directory holds the Flexible Master Operations roles (FSMO), which are used for different tasks within the forest and domain. There are two-forest roles and three domain-wide roles. Table 7.1 lists the role name, scope, and its purpose.

| Table 7.1: FSMO roles | | |
| :--- | :--- | :--- |
| FSMO ROLE | SCOPE | PURPOSE |
| Schema Master | Forest | Hold the forest's schema |
| Domain Naming Master | Forest | Manage domain names |
| Infrastructure Master | Domain | Ensure cross-domain object references |
| PDC Emulator | Domain | Responsible for time in the domain |
| RID Master | Domain | Handle account lockouts |
| Master | Domain | Manage and replenish RID pools |

In certain situations, for example, decommissioning a domain controller, upgrading the domain, or even for performance issues, you will need to move these roles to a new domain controller. One way to migrate or move these to a new domain is using the NTDSUtil command. To move domain FSMO roles, follow these steps:

- 1. Open a command prompt (cmd.exe) and type NTDSUtil. Press Enter.
- 2. Type roles and Enter.
- 3. Type connections and Enter.
- 4. Now you need to connect to the server that will hold FSMO roles in the future. connect to server [Hostname] and Enter.
- 5. Type quit and Enter.
- 6. First you will transfer the PDC Emulator role. Type transfer pdc and Enter. You need to confirm your request by Yes.
- 7. If you need to transfer rid master and Enter to move the RID Master role. You need to confirm your request by Yes.
- 8. If you need to transfer infrastructure master and Enter to move the Infrastructure Master role. You need to confirm your request by Yes.
- 9. Now that you have finished moving all domain FSMO roles, press Enter; then quit to exit to the command prompt.

Of course, you will need to repeat these steps for each domain. If you decide to move the forest-wide FSMO roles, follow these steps:

- 1. Open a command prompt (cmd.exe) and type NTDSUtil. Press Enter.
- 2. Type roles and Enter.
- 3. Type connections and Enter.
- 4. Now you need to connect to the server that will hold FSMO roles in the future. connect to server [Hostname] and Enter.
- 5. Type quit and Enter.
- 6. First you will transfer the Schema Master role. Type transfer schema master and Enter. You need to confirm your request by Yes.
- 7. If you need, transfer naming master and Enter to move the Domain Naming Master role. You need to confirm your request by Yes.

After you have moved all your FSMO roles to the new domain controller(s), you might want to see if everything is the way you expect. We suggest that you run the netdom query fsmo command in the command prompt, which will show you which domain controller holds FSMO role.
