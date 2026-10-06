# STOPPING AND RESTARTING ACTIVE DIRECTORY

Before performing an offline defragmentation, it would be wise to back up the system state and critical data of the domain controller to ensure you can recover from any errors that might occur. You should verify that there is ample free space on the volume that contains the AD database (Ndsdit) for temporary space. Microsoft recommends free space up to at least 15 percent of the Ndsdit file size for temporary space needs.

Active Directory performs offline defragmentation to optimize the storage of data within the Ndsdit file of the daily garbage-collection process. This does help optimize the database, but it does nothing to reduce the size of the database file. Offline defragmentation is the only effective way to reduce the size of the database.

# PERFORMING OFFLINE DEFRAGMENTATION OF NTDS.DIT

These steps assume you have stopped the Active Directory Domain Services, as discussed earlier, and you are compacting the Ndsdit file to a local folder. If you plan to defagment and compact the database to a shared folder, map a drive to that shared folder before you begin these steps, and use that driver in the path where appropriate.

+   1. Open an elevated command prompt.
2. Type ntdsutil, and then press Enter.
3. Type Activate NTDS, and then press Enter.
4. At the resulting ntdsutil prompt, type Files (case sensitive), and then press Enter.
5. At the file maintenance prompt, type compact to followed by the path to the destination folder for the defragmentation, and then press Enter.

If there are spaces in your path to the destination, double the entire path in quotation marks (such as `C:\temp folder\`). Ndsutil.exe will display a progress indicator. Upon completion, it will prompt you to perform an independent backup of the original and the compacted files.

+   6. Copy the new Nds.dit file to your %systemroot%\NTDS\ directory (for example, c:\Windows)
7. Delete to exit file maintenance mode, and then type quit and Enter again to exit ntdsutil.exe.
8. After you complete all these steps, restart AD DS.

It's interesting to note that you will not be able to access files and folders on the server computer after stopping AD DS without providing the Domain administrator credentials.

# Checking the Integrity of an Active Directory Database

Active Directory uses the same indexed sequential access manager (ISAM) database engine that is used in Exchange Server, and the version used in Windows Server 2012 R2 is called the Extensible Storage Engine (ESE).