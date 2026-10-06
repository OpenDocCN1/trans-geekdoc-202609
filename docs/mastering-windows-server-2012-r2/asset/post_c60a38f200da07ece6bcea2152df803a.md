
Before considering an in-place upgrade, you need to check several requirements of Windows Server 2012:

- Make sure your hardware supports 64-bit operating systems.
- Windows Server 2012 is available only in 64-bit, there is no way to use 32-bit hardware.
- The minimum hardware requirement for Windows Server 2012 is a 1.4 GHz 64-bit processor, 512 MB RAM, 32 GB free space, and a screen resolution of 800 × 600. Your requirements are probably easy to meet nowadays.
- It makes sense to do an in-place upgrade of a server that has an additional life cycle of three to four years. Make sure you get hardware vendor support for the lifespan of the server.
- Verify that each piece of software installed on the server is supported by Windows Server 2012, especially antivirus software, hardware drivers, and applications. If you try to fix incompatibility issues during the upgrade, you could get in big trouble. If you are not, we recommend removing the antivirus software before the upgrade and reinstall it after a successful upgrade.
- Make a backup of the domain controller and system state.

## UPGRADE PATH FOR WINDOWS SERVER 2012 R2

It is important to note that Windows Server 2012 R2 does not allow you to upgrade from Windows Server 2008 SP2 anymore. You need at least Windows Server 2008 R2 SP1 to upgrade from.

If you need to upgrade from Windows Server 2012 Datacenter, you can upgrade to Windows Server 2012 R2 Datacenter. If you have Windows Server 2012 Standard installed, you can upgrade to Windows Server 2012 R2 Standard or Windows Server R2 Datacenter.

The minimum requirements for Windows Server 2012 R2 are the same as for Windows Server 2012.

As a best practice I recommend backing up the C:\ partition and system state. To create the backup, I highly recommend making backups using two different backup tools. First, back up the C: partition and system state using your company backup tool that you have in place. For second backup, use the Windows internal backup tool to back up the boot partition and system state. The reason is that in case of problems Microsoft used to support only backups done with their own utility.

At this stage you have verified that your system is ready for upgrading and that you have valid backups. The next steps are to make sure that your domain controller does not have any errors or replication problems.

To verify the domain controller's health state use repadmin /bydest /sort:delta running the following command:

```
repadmin /replsum /bysrc /bydest /sort:delta
```

This command will show replication errors in your domain sorted by replication source and replication destination and largest delta of replication. If the output shows any errors, try to fix the problems in advance.

## AD Replication Status Tool

2012 Microsoft released the AD Replication Status Tool. This is a small GUI-based tool that can be installed on a Windows client or Windows server operating system. This tool allows you to analyze the replication status for the domain controller in your domain or forest. It easily shows you any errors and allows you to export the results to a CSV or XPS file for further analysis. You can download it here: http://www.microsoft.com/en-us/download/details.aspx?id=38905.

On your domain controller run the command CDIAG and make sure all tests are passed. CDIAG needs to be installed on Windows Server 2003. The source tools.msi can be found on the source. If all tests pass, open Event Viewer on your domain controller, look into the event logs for any errors or warnings, and try to fix the problems.

Here's how to do an in-place upgrade from a 2008-based AD:

1. Prep the forest's schema to be compatible with Windows Server 2012.
2. Prep the domain for Windows Server 2012.
3. Run the setup program to upgrade the domain controller.

## PREPARE THE FOREST/SCHEMA AND DOMAIN

In an in-place upgrade, not all domain controllers must be Windows Server 2008. However, some FSMO roles must be located on this server. The naming master of the forest, which is by default the first domain controller in the forest, must be Windows Server 2008. The PDC emulator of each domain within the forest is required to be Windows Server 2008 as well. These are by default the first domain controllers in each domain. It is recommended to start the upgrade process on a domain controller that doesn't hold any FSMO role. If the domain controller that you want to upgrade currently holds a FSMO role, you can move the FSMO role and then, after a successful upgrade, move the role back to the Windows 2012 domain controller.

In addition, all domain controllers need to be running Windows Server 2003 or higher. Also, before you upgrade one of your Windows Server 2003/2008 forest to Windows Server 2012, you have to change your forest schema to Windows Server 2012. You will do that on the forest's schema operations master FSMO role. Pop the Windows Server 2012 Setup CD into your computer's CD drive, open a command prompt, and navigate to support\adprep directory wherever drive holds the CD. So, for example, if your CD drive is D, you would open a command prompt, type D:, and press Enter; then you would type cd \support\adprep and press Enter. Adprep.exe is compiled in only 64-bit. There is no longer a 32-bit version.

## CHAPTER 7 ACTIVE DIRECTORY IN WINDOWS SERVER 2012

1. Run adprep on the schema master role by typing adprep /forestprep, and press Enter.

A warning will appear verifying that all servers are running Windows Server 2003 or higher.

2. Confirm by typing C and then pressing Enter.

3. Next, on the infrastructure master role in your domain that you want to prepare, run adprep /domainadprep /gpprep and press Enter.

4. Finally, run adprep /cleanupforest on the schema master.

In this stage you have verified that your system is ready for upgrading and that you have valid backups. The next steps are to make sure that your domain controller does not have any errors or replication problems.

To verify the domain controller's health state use repadmin /bydest /sort:delta running the following command:

```
repadmin /replsum /bysrc /bydest /sort:delta
```

This command will show replication errors in your domain sorted by replication source and replication destination and largest delta of replication. If the output shows any errors, try to fix the problems in advance.

## AD Replication Status Tool

2012 Microsoft released the AD Replication Status Tool. This is a small GUI-based tool that can be installed on a Windows client or Windows server operating system. This tool allows you to analyze the replication status for the domain controller in your domain or forest. It easily shows you any errors and allows you to export the results to a CSV or XPS file for further analysis. You can download it here: http://www.microsoft.com/en-us/download/details.aspx?id=38905.

On your domain controller run the command CDIAG and make sure all tests are passed. CDIAG needs to be installed on Windows Server 2003. The source tools.msi can be found on the source. If all tests pass, open Event Viewer on your domain controller, look into the event logs for any errors or warnings, and try to fix the problems.

Here's how to do an in-place upgrade from a 2008-based AD:

1. Prep the forest's schema to be compatible with Windows Server 2012.
2. Prep the domain for Windows Server 2012.
3. Run the setup program to upgrade the domain controller.

## PREPARE THE FOREST/SCHEMA AND DOMAIN

In an in-place upgrade, not all domain controllers must be Windows Server 2008. However, some FSMO roles must be located on this server. The naming master of the forest, which is by default the first domain controller in the forest, must be Windows Server 2008. The PDC emulator of each domain within the forest is required to be Windows Server 2008 as well. These are by default the first domain controllers in each domain. It is recommended to start the upgrade process on a domain controller that doesn't hold any FSMO role. If the domain controller that you want to upgrade currently holds a FSMO role, you can move the FSMO role and then, after a successful upgrade, move the role back to the Windows 2012 domain controller.

In addition, all domain controllers need to be running Windows Server 2003 or higher. Also, before you upgrade one of your Windows Server 2003/2008 forest to Windows Server 2012, you have to change your forest schema to Windows Server 2012. You will do that on the forest's schema operations master FSMO role. Pop the Windows Server 2012 Setup CD into your computer's CD drive, open a command prompt, and navigate to support\adprep directory wherever drive holds the CD. So, for example, if your CD drive is D, you would open a command prompt, type D:, and press Enter; then you would type cd \support\adprep and press Enter. Adprep.exe is compiled in only 64-bit. There is no longer a 32-bit version.

## CHAPTER 7 ACTIVE DIRECTORY IN WINDOWS SERVER 2012

1. Run adprep on the schema master role by typing adprep /forestprep, and press Enter.

A warning will appear verifying that all servers are running Windows Server 2003 or higher.

2. Confirm by typing C and then pressing Enter.

3. Next, on the infrastructure master role in your domain that you want to prepare, run adprep /domainadprep /gpprep and press Enter.

4. Finally, run adprep /cleanupforest on the schema master.

In this stage you have verified that your system is ready for upgrading and that you have valid backups. The next steps are to make sure that your domain controller does not have any errors or replication problems.

To verify the domain controller's health state use repadmin /bydest /sort:delta running the following command:

```
repadmin /replsum /bysrc /bydest /sort:delta
```

This command will show replication errors in your domain sorted by replication source and replication destination and largest delta of replication. If the output shows any errors, try to fix the problems in advance.

## AD Replication Status Tool

2012 Microsoft released the AD Replication Status Tool. This is a small GUI-based tool that can be installed on a Windows client or Windows server operating system. This tool allows you to analyze the replication status for the domain controller in your domain or forest. It easily shows you any errors and allows you to export the results to a CSV or XPS file for further analysis. You can download it here: http://www.microsoft.com/en-us/download/details.aspx?id=38905.

On your domain controller run the command CDIAG and make sure all tests are passed. CDIAG needs to be installed on Windows Server 2003. The source tools.msi can be found on the source. If all tests pass, open Event Viewer on your domain controller, look into the event logs for any errors or warnings, and try to fix the problems.

Here's how to do an in-place upgrade from a 2008-based AD:

1. Prep the forest's schema to be compatible with Windows Server 2012.
2. Prep the domain for Windows Server 2012.
3. Run the setup program to upgrade the domain controller.

## PREPARE THE FOREST/SCHEMA AND DOMAIN

In an in-place upgrade, not all domain controllers must be Windows Server 2008. However, some FSMO roles must be located on this server. The naming master of the forest, which is by default the first domain controller in the forest, must be Windows Server 2008. The PDC emulator of each domain within the forest is required to be Windows Server 2008 as well. These are by default the first domain controllers in each domain. It is recommended to start the upgrade process on a domain controller that doesn't hold any FSMO role. If the domain controller that you want to upgrade currently holds a FSMO role, you can move the FSMO role and then, after a successful upgrade, move the role back to the Windows 2012 domain controller.

In addition, all domain controllers need to be running Windows Server 2003 or higher. Also, before you upgrade one of your Windows Server 2003/2008 forest to Windows Server 2012, you have to change your forest schema to Windows Server 2012. You will do that on the forest's schema operations master FSMO role. Pop the Windows Server 2012 Setup CD into your computer's CD drive, open a command prompt, and navigate to support\adprep directory wherever drive holds the CD. So, for example, if your CD drive is D, you would open a command prompt, type D:, and press Enter; then you would type cd \support\adprep and press Enter. Adprep.exe is compiled in only 64-bit. There is no longer a 32-bit version.

## CHAPTER 7 ACTIVE DIRECTORY IN WINDOWS SERVER 2012

1. Run adprep on the schema master role by typing adprep /forestprep, and press Enter.

A warning will appear verifying that all servers are running Windows Server 2003 or higher.

2. Confirm by typing C and then pressing Enter.

3. Next, on the infrastructure master role in your domain that you want to prepare, run adprep /domainadprep /gpprep and press Enter.

4. Finally, run adprep /cleanupforest on the schema master.
