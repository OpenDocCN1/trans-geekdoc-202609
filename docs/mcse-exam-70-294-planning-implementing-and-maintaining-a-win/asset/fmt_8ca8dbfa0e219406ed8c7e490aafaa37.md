
# Active Directory Database Maintenance

## Offline Defragmentation Space Estimation

As mentioned, you should perform an offline defragmentation only when you are confident that you can recover significant free space. Offline defragmentation is a very serious process that requires taking the DC offline for a period of time and performing a highly invasive database procedure. You might be wondering how you can tell if there is enough free space available for recovery to justify the operation.

Fortunately, Microsoft provides you with a way to determine this that doesn’t require actually performing the procedure. By modifying the Registry, you can have the Directory Service generate an event log entry that estimates how much space would be freed up by an offline defragmentation. The following steps outline the process:

1. Click Start | Run.
2. In the Open: text box, type `regedt32.exe` and click the OK button.
3. In the Registry editor, navigate to `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\NTDS\Diagnostics`.
4. Double-click the `6 Garbage Collection` entry.
5. In the Edit DWORD Value dialog box, type 1 in the Value Data text box.
6. Click OK.
7. Verify that the value in the Data column for `6 Garbage Collection` is `0x00000001` (1). If it is not, repeat steps 4, 5, and 6.
8. Close the Registry editor.

### Moving the Database or Log Files

At some point, it might become necessary to move the Active Directory database or log files. Most often, this occurs because you need to move the files to a new hard drive or array of hard drives. Performance might dictate this decision. New faster drives and controllers can be used to replace slower ones as usage increases. The decision might also be dictated by a lack of free space as the Active Directory database and components grow.

Moving the database or log files is relatively simple. It is done from the command line using the `Ntdsutil` utility discussed previously. Because the database and log files cannot be open when they are moved, the operation must be carried out while in Directory Services Restore Mode. The following steps outline how to move the Active Directory database and log files.

1. Back up the system state data for fault tolerance purposes. See the Backing Up Active Directory section later in this chapter for more information.
2. Boot or reboot the computer.
3. When prompted, press F8 during Windows Server 2003 startup.
4. Select Directory Services Restore Mode (Windows DCs only) on the Windows Advanced Options menu that appears, and press the Enter key.
5. Select your operating system (for example, Windows Server 2003, Enterprise), and press the Enter key.
6. You will see a number of checks performed while the system is booting, and eventually you will receive the Safe Mode logon prompt.
7. Log on by providing the password for the local administrator account and clicking the OK button.
8. Click the OK button in the dialog box that notifies you that Windows is running in safe mode.
9. Open a command prompt.
10. Type `ntdsutil` to enter the `Ntdsutil` utility. This is a command-line utility so the command prompt will change to `ntdsutil:`.
11. Type `files`. The command prompt should change to display `file maintenance:`.
12. Use one of the following commands to move the Active Directory database or log files, or update their paths.
- Type `move DB to <drive>:\<directory>` to move the `ntds.dit` database file to the new location specified. For example, `move DB to C:\AD` moves the database file to the `c:\ad` directory and updates the Registry to point to this new location, as shown in [Figures 11.6](#B9781931836944500179.xhtml#f0035) and [11.7](#B9781931836944500179.xhtml#f0040).
![Figure 11.5 The Ntdsutil Compact To Command](images/B9781931836944500179/f11-05-9781931836944.jpg)
Figure 11.5 The Ntdsutil Compact To Command
![Figure 11.6 Moving the Active Directory Database with Ntdsutil, First Screen Portion](images/B9781931836944500179/f11-06-9781931836944.jpg)
Figure 11.6 Moving the Active Directory Database with Ntdsutil, First Screen Portion
![Figure 11.7 Moving the Active Directory Database with Ntdsutil, Second Portion of the Screen](images/B9781931836944500179/f11-07-9781931836944.jpg)
Figure 11.7 Moving the Active Directory Database with Ntdsutil, Second Portion of the Screen
- Type `move logs to <drive>:\<directory>` to move the Active Directory log files to the new location specified. For example, `move logs to C:\AD` moves the log files to the `c:\ad` directory and updates the Registry to point to this new location, as shown in [Figures 11.8](#B9781931836944500179.xhtml#f0045) and [11.9](#B9781931836944500179.xhtml#f0050).
![Figure 11.8 Moving the Active Directory Log Files with Ntdsutil, First Portion of the Screen](images/B9781931836944500179/f11-08-9781931836944.jpg)
Figure 11.8 Moving the Active Directory Log Files with Ntdsutil, First Portion of the Screen
![Figure 11.9 Moving the Active Directory Log Files with Ntdsutil, Second Portion of the Screen](images/B9781931836944500179/f11-09-9781931836944.jpg)
Figure 11.9 Moving the Active Directory Log Files with Ntdsutil, Second Portion of the Screen
13. Ensure that the database (or log files) is now referenced in the proper location by typing `info`.
14. Type `quit` to return to the `ntdsutil:` prompt.
15. Type `quit` again to exit the utility.
16. Close the command prompt window and reboot the server normally.

#### Using the Set Path Option in Ntdsutil

It’s important to properly move the Active Directory database and log files using the `Ntdsutil` command-line utility. This updates the Registry entries that point to the correct locations in the file system, thus allowing the system to find and initialize them when booting. If you are forced to restore these files to another location, or simply copy them to a new location using Windows Explorer, Active Directory will not initialize when the system is rebooted. Fortunately, Microsoft provides a way to fix this, using the `Ntdsutil` utility. To do so, follow these steps:

1. Boot or reboot the computer.
2. When prompted, press F8 during Windows Server 2003 startup.
3. Select Directory Services Restore Mode (Windows DCs only) on the Windows Advanced Options menu that appears, and press the Enter key.
4. Select your operating system (for example, Windows Server 2003, Enterprise), and press the Enter key.
5. You will see a number of checks performed while the system is booting, and you eventually will receive the Safe Mode logon prompt.
6. Log on by providing the password for the local administrator account and clicking the OK button.
7. Click the OK button in the dialog box that notifies you that Windows is running in safe mode.
8. Open a command prompt.
9. Type `ntdsutil` to enter the `Ntdsutil` utility. This is a command-line utility, so the command prompt will change to `ntdsutil:`.
10. Type `files`. The command prompt should change to display `file maintenance:`.
11. Use one of the following commands to move the Active Directory database or log files, or to update their paths.
12. Type `set path DB <drive>:\<directory>` to update the Registry to point to the new location of the `ntds.dit` file.
13. Type `set path logs <drive>:\<directory>` to update the Registry to point to the new location of the Active Directory log files.
14. Type `quit` to return to the `ntdsutil:` prompt.
15. Type `quit` again to exit the utility.
16. Close the command prompt window and reboot the server normally.

### Monitoring the Database

![u11-01-9781931836944](images/B9781931836944500179/u11-01-9781931836944.jpg)
It’s important to implement a consistent Active Directory monitoring strategy to ensure database integrity, reliability, and performance within your forest. Regular monitoring can also improve your knowledge of Active Directory and assist you in determining when a problem is in the early stages of unfolding. This will lead to performance and service issues being resolved in a much more timely manner.
