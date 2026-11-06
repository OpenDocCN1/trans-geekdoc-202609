
## Seizing the PDC Emulator or Infrastructure FSMOs

Seizing the PDC Emulator or Infrastructure FSMOs is still accomplished through the same GUI tool used previously: Active Directory Users and Computers. Since the DC with the lost FSMO is unavailable, the DC you are focused on should suffice. However, you can switch the focus by right-clicking on the domain object, selecting `Connect to Domain Controller…` | Enter the name of another domain controller OR Select an available domain controller, and clicking `OK` (see [Figure 7.35](#B9781931836944500131.xhtml#f0180)). To seize or force a transfer of the PDC or Infrastructure, right-click the domain object and select `Operations Masters…` | `[PDC or Infrastructure]`. Notice that the service has attempted to contact the FSMO in question, and the dialog displays a message that it is offline (see [Figure 7.37](#B9781931836944500131.xhtml#f0190)). Click `Change…` anyway. Confirm your request. This time, a warning dialog box will appear asking you again if you are sure you want to transfer the operations master role. Click `OK`. A third dialog then appears with an explanation and question:

![Figure 7.37 Failed to Connect to PDC FSMO](images/B9781931836944500131/f07-37-9781931836944.jpg)

Figure 7.37 Failed to Connect to PDC FSMO

`The current operations master cannot be contacted to perform the transfer. Under some circumstances, a forced transfer can be performed.`

`Do you want to attempt a forced transfer?`

Click `Yes` to complete the seizure or forced FSMO role transfer. To summarize, the process requires three confirmations to perform the process, so be patient. Remember, this only applies to two of the domainwide FSMOs: PDC Emulator and Infrastructure. The RID FSMO cannot be seized from the GUI tool.

## Seizing the RID Master, Domain Naming Master, and Schema Master FSMOs

Seizing the roles of `RID`, `Domain Naming`, and `Schema Master` requires the command-line utility `NTDSUTIL`. Follow these steps to perform this type of seizure:

1. Click `Start` | `Run` and type `cmd`. At the command prompt, type `ntdsutil` and press Enter.
2. Type `Roles` | Enter. The prompt will change to `fsmo maintenance:`.
3. Type `Connections` | Enter. The prompt changes to `server connections:`. As in the GUI `ADUC`, you have to change your DC focus to the DC that is receiving the transferred role.
4. Type `Connect to server <servername>` and press Enter, where `<servername>` is the name of the DC receiving the transferred role.
5. Type `Quit` and press Enter. This completes the focus change and returns you to the `fsmo maintenance:` prompt.
6. Type `Seize <fsmo> master` and press Enter, where `<fsmo>` is the operations master role you are trying to transfer: `RID`, `Domain Naming`, or `Schema`.
7. Type `Quit` and press Enter to exit the FSMO maintenance, and type `Quit` and press Enter a second time to exit `NTDSUTIL`.

Here is an example of the messages that appear when you seize the RID FSMO from the DC named `dc3.yourfirm.biz` and give it to `dcl.yourfirm.biz`:

```
C:\>ntdsutil
Ntdsutil: roles
Fsmo maintenance: connections
Server connections: connect to server dc1.yourfirm.biz
Binding to dc1.yourfirm.biz…
Connected to dc1.yourfirm.biz using credentials of locally logged on user.
Server connections: quit
Fsmo maintenance: seize rid master
```

![u07-b1-9781931836944](images/B9781931836944500131/u07-b1-9781931836944.jpg)
Note

A pop-up dialog will appear, requesting confirmation that you want to proceed.

```
Attempting safe transfer of RID FSMO before seizure.
Ldap_modify_sW error 0x34(52 (Unavailable).
Ldap extended error message is 00002DAF: SvcErr: DSID-03210300, problem 5002 (UNAVAILABLE), data 1722
Win32 error returned is 0x20af(The requested FSMO operation failed. The current FSMO holder could not be contacted.)
Depending on the error code this may indicate a connection, ldap, or role transfer error.
Transfer of RID FSMO failed, proceeding with seizure…
Searching for highest rid pool in domain
Server “dc1.yourfirm.biz” knows about 5 roles
Schema - CN=NTDS Settings,CN=DC1,CN=Servers,CN=CorpHQ,CN=Sites,CN=Configuration,DC=yourfirm, DC=biz
Domain - CN=NTDS Settings,CN=DC1,CN=Servers,CN=CorpHQ,CN=Sites,CN=Configuration,DC=yourfirm,DC=biz
PDC - CN=NTDS Settings,CN=DC1,CN=Servers,CN=CorpHQ,CN=Sites,CN=Configuration,DC=yourfirm,DC=biz
RID - CN=NTDS Settings,CN=DC1,CN=Servers,CN=CorpHQ,CN=Sites,CN=Configuration,DC=yourfirm,DC=biz
Infrastructure - CN=NTDS Settings,CN=DC1,CN=Servers,CN=CorpHQ,CN=Sites,CN=Configuration,DC=yourfirm,DC=biz
Fsmo maintenance: quit
Ntdsutil: quit
```

That’s it—no reassurance that it was completed. Instead, it is simply stated that server “dcl.yourfirm.biz” knows about five roles and it lists the change requested. Remember, this works for the Schema and Domain -Naming seizures as well. Just replace the word `rid` in the text with `schema` or `domain naming`. By the way, unless you enjoy extreme chaos, do not bring an old master back online in your domain. Format the disk and build the machine from scratch.

## EXERCISE 7.02 transferring a FSMO

In this exercise, you will transfer a FSMO in your domain from one DC to another; essentially, you will “lose” the FSMO and seize it back. To do this exercise, you must have at least two computers networked together that are both DCs. The prerequisites include:

■ Two DCs in the same domain and networked together.
■ The first DC you install automatically assumes all five FSMO roles: Schema, Domain Naming, PDC Emulator, RID, and Infrastructure. If you are doing the examples in the book, you might have transferred the schema FSMO already. As a bonus, you can seize that as well.

First, you must transfer the Infrastructure FSMO:

1. Open Active Directory Users and Computers: `Start` | `Programs` | `Administrative Tools` | `Active Directory Users and Computers`.
2. Right-click your domain object and select `Connect to Domain Controller` (see [Figure 7.39](#B9781931836944500131.xhtml#f0200)).

![Figure 7.38 Forcing a FSMO Transfer](images/B9781931836944500131/f07-38-9781931836944.jpg)

Figure 7.38 Forcing a FSMO Transfer

![Figure 7.39 Connect to Domain Controller](images/B9781931836944500131/f07-39-9781931836944.jpg)

Figure 7.39 Connect to Domain Controller

3. Select your other DC and click `OK`.
4. Right-click on the domain object again.
5. This time, select `Operations Masters`.
6. Click on the `infrastructure tab` (see [Figure 7.40](#B9781931836944500131.xhtml#f0205)).

![Figure 7.40 Infrastructure FSMO](images/B9781931836944500131/f07-40-9781931836944.jpg)

Figure 7.40 Infrastructure FSMO

7. Click `Change....`
8. Click `Yes` to confirm that you are sure. Note: You might receive a warning dialog if you are attempting to transfer the Infrastructure FSMO to a DC that is also a GC server. For our exercise, that’s fine; however, in a production environment you must avoid this because the Infrastructure FSMO cannot function on the same server as the GC.
9. Click `OK` in the Transfer Successful dialog.

Now you need to seize the Infrastructure FSMO.

10. Using the ADUC that should still be open, right-click the domain object and select `Connect to Domain Controller`.
11. Select the original DC to make it your focus.
12. To simulate the loss of this FSMO and DC, just unplug it from the network.
13. Right-click the domain object again and select `Operations Masters`.
14. Click on the `Infrastructure tab`. With the other DC offline, you get the hourglass for a minute or so and then you get the ERROR dialog shown in [Figure 7.41](#B9781931836944500131.xhtml#f0210). The message states that the FSMO cannot be transferred, which is correct—a transfer implies smooth transition and fully connectivity to all parties. We are simulating the loss of this FSMO, so an error is what we want.

![Figure 7.41 ERROR Infrastructure FSMO Offline](images/B9781931836944500131/f07-41-9781931836944.jpg)

Figure 7.41 ERROR Infrastructure FSMO Offline

15. To force the Infrastructure FSMO back to your original DC, click the `Change…` button.
