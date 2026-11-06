
That's one Active Directory function that requires the PDC Emulator in a Windows Server 2003-only environment, but what's the other one? Domains need to track changes constantly, and time is of the essence. If there is a change to Becca's account at 2:30 p.m. and another change at 2:35 p.m. that conflicts with the original change, the domain must recognize in what order to perform these changes, based on the timestamp. In a multidomain forest, it is difficult to keep everyone's time synchronized. Microsoft deals with this by setting up a forestwide time synchronization system, using the PDC Emulator FSMO. Each PDC Emulator in each domain acts as the timekeeper for its domain. All DCs check in with their respective PDC Emulators to synchronize their time. So, how do the PDC Emulators know what time to use? They go to the master timekeeper: the first PDC Emulator installed in your forest. Remember that the first DC of the forest that you create contains all five FSMOs, so it is the first PDC Emulator you created with which all other PDC Emulators synchronize their time.

## Configuring & Implementing…

### Authoritative Time Server

As mentioned, Microsoft provides a time-keeping process to try to establish a common time among all the computers in the domain. It uses a hierarchical scheme as follows:

■ Each client workstation nominates its authenticating DC as its timekeeper.
■ Each member server does the same.
■ Each DC in a domain nominates the PDC Emulator as its timekeeper.
■ Each PDC Emulator follows the same hierarchy as the domains in the forest, selecting the PDC Emulator above as its timekeeper until the “root” PDC Emulator is reached, which is nominated as the master timekeeper for the forest.

The time service that Microsoft uses and is required by Kerberos authentication is `W32Time`. This service is automatically in place and working between the DCs in your forest. It is a good idea to find your master timekeeper PDC Emulator and set up a time server for it to synchronize

You can use the Simple Network Time Protocol (`SNTP`) to establish a time standard for your domain. Use the following command to access an SNTP server:

`net time /setsntp:server_list`. A list of servers can be found on the Internet. Here are two provided by the United States Naval Observatory:

■ `Ntp2.usno.navy.mil` (192.5.41.209)
■ `Tock.usno.navy.mil` (192.5.41.41)

Other time servers are managed by the National Institute of Standards and Technology (NIST) found at [`www.nist.gov`](http://www.nist.gov). For in-depth instruction and reference on this topic, refer to Microsoft’s white paper, `wintimeserv.doc` on their Web site.

### Infrastructure Master

According to Microsoft, without the Infrastructure Master, changes between your DCs would be slow. The Infrastructure Master speeds this process up. There is one infrastructure FSMO per domain, and it is on the first DC you installed for that domain, unless you have transferred or seized the role (discussed in the next section).

The Infrastructure FSMO appears to be somewhat enigmatic in how it does its role. We have seen references to this FSMO indicating as just stated that the speed of services managing the domain is increased—but how? First, it updates the group-to-user references whenever a change is made; and second, this FSMO is in charge of seeking and destroying those stale objects floating around your Ethernet. Actually, this refers to the references that are no longer valid. This can occur when an object is moved, renamed, or deleted. The infrastructure FSMO uses the GC to check for these stale references and then removes them. Because the GC and the Infrastructure FSMO have to work so closely together, Microsoft recommends that these two roles run on separate DCs. Of course, by default, they are on the same DC, so it is up to you to move one of these roles to your second DC as soon as you have one.

![u07-03-9781931836944](images/B9781931836944500131/u07-03-9781931836944.jpg)

## Transferring and Seizing Operations Master Roles

With your newfound understanding of FSMOs, you can see that they are essential for domain consistency and integrity. It has been said more than once that these roles are created automatically, but the defaults assigned by that automatic creation might not suit your environment, and you might consequently need to either transfer these roles to a better machine or move them before retiring a server. It is also possible for you to lose a DC containing one or more of these roles and be unable to recover it. This section describes how to transfer and seize these operations master roles.

### Transferring FSMOs

You’ve decided to transfer your FSMOs from the original location, on the first DC, to another server that will be your super-server. When the transfer is planned, you can manually move these roles by following the steps outlined in the next sections.

#### Transferring the Schema FSMO

First, you must be a member of the `Schema Admins` group. Next, you need to access the `Active Directory Schema` snap-in, which is not in the Administrative Tools menu but must be added to an MMC.

To install the Active Directory Schema snap-in, follow these steps:

1. Open a command prompt [Start | Run | `cmd`, and click OK.
2. At the command prompt, type `regsvr32 schmmgmt.dll`. This command will register `schmmgmt.dll` on your computer. Successful registration produces the dialog box shown in [Figure 7.28](#B9781931836944500131.xhtml#f0145).

![Figure 7.28 Register Service](images/B9781931836944500131/f07-28-9781931836944.jpg)

Figure 7.28 Register Service

3. Click Start | Run… and type `mmc /a`. Then, click OK. This opens a blank MMC in author’s mode.
4. On the File menu, click Add/Remove Snap-in, and then click Add.
5. Under Snap-in, double-click `Active Directory Schema`, click Close, and then click OK.

Looking at the schema attributes, you can identify a few [Figure 7.29](#B9781931836944500131.xhtml#f0150) shows the `cn` or Common-Name attribute, which is mandatory in a user account. Right-clicking on the object named Active Directory Schema affords you several options (see [Figure 7.30](#B9781931836944500131.xhtml#f0155)). From this tool, you can see which DC is currently assigned the Schema Master by selecting `Operations Master…`, and you can transfer the FSMO to another DC by selecting `Change Domain Controller`.

![Figure 7.29 Active Directory Schema Tool](images/B9781931836944500131/f07-29-9781931836944.jpg)

Figure 7.29 Active Directory Schema Tool

![Figure 7.30 Management Options](images/B9781931836944500131/f07-30-9781931836944.jpg)

Figure 7.30 Management Options

[Figure 7.31](#B9781931836944500131.xhtml#f0160) depicts the next dialog in our quest. You are then given the choice to transfer the FSMO to Any DC or Specify a Name. Specify the new location and click OK. The new location is the `FQDN` of the DC to which you are transferring the FSMO. The system will refresh the screen and you will see that the focus has changed to the other DC you just specified (see [Figure 7.32](#B9781931836944500131.xhtml#f0165)). To complete the task, you still need to right-click the Active Directory Schema object again, and this time choose `Operations Master`, which brings up the dialog box shown in [Figure 7.33](#B9781931836944500131.xhtml#f0170). In our example, we are moving the schema FSMO to the DC, `skyline.yourfim.biz`. Click Change and the system will ask you to verify that you really want to make this change. Click OK. After a short pause, the confirmation dialog in [Figure 7.34](#B9781931836944500131.xhtml#f0175) appears. Click OK. The Schema FSMO is now on the `skyline.yourfirm.biz` DC.

![Figure 7.31 Change Domain Controller](images/B9781931836944500131/f07-31-9781931836944.jpg)

Figure 7.31 Change Domain Controller

![Figure 7.32 Change in Focus Prior to FSMO Transfer](images/B9781931836944500131/f07-32-9781931836944.jpg)

Figure 7.32 Change in Focus Prior to FSMO Transfer
