
# Active Directory Maintenance and Backup

## Garbage Collection Process

D. The Garbage Collection process deletes all tombstoned objects from the Active Directory database.

☑ A, C. Answer A is correct; the Garbage Collection process runs every 12 hours by default, although you can change this interval. Answer C is also correct, because the Garbage Collection process deletes expired objects from the Active Directory database. Objects are marked as expired at the end of the tombstone interval.

⌧ Answer B is incorrect. Offline defragmentation must be performed manually by an administrator. Because the Garbage Collection process deletes objects from the Active Directory database, it produces fragmentation. The Active Directory database is defragmented at the end of the Garbage Collection process by an automatically run online defragmentation. Answer D is also incorrect. When an object is deleted from the Active Directory database, it is first marked as tombstoned and moved to the deleted objects container. This provides time for any other DCs to learn of the deletion. After the default tombstone interval (60 days) expires, the object is marked as expired. Although the objects removed by Garbage Collection have been tombstoned, they must have been tombstoned for 60 days and marked as expired to be deleted by Garbage Collection.

## Performing Active Directory Maintenance Tasks

### 5. Your Windows Server 2003 DC is running out of disk space on the partition containing the database and log files. Which of the following steps will best rectify the situation before critical failure and additional performance degradation occurs? (Choose all that apply.)

A. You can compress the database file using, NTFS compression.

B. You can install an additional hard drive.

C. You can move the Active Directory database and log files, using Windows Explorer, and reboot the server.

D. You can move the Active Directory database and log files, using the `Ntdstuil` utility

☑ B, D. The best option is to either delete data from the hard drive to free up space, or move the database to another disk drive. Answer B is correct because it specifies adding a hard drive, which can be used in relocating the Active Directory database and log files. Answer D is also correct. The proper way to move the database is to boot into `Directory Services Restore Mode` and use the `Ntdsutil` command-line utility. This utility moves the database and log files and updates all Registry references to them.

⌧ Answer A is incorrect. The Active Directory database is already heavily optimized for size. Using NTFS compression will have little effect on it and is not the best solution. Answer C is also incorrect. It is not possible to move the Active Directory database and active log files while Active Directory is initialized on the server. Booting to the `Directory Services Restore Mode` will allow it, but simply copying the files to a new location does not update their location pointers in the Registry. Upon reboot, the Windows Server 2003 will not be able to find the files and initialize Active Directory.

### 6. You recently started a new job as a network administrator. Upon reviewing the servers for which you are responsible, you notice that Active Directory is failing to start on one of your DCs. Further investigation reveals that Active Directory cannot find the location of the log files. You verify that the log files are located in the `D:\\ADLogs` directory. Which of the following actions is the best to use in resolving this problem?

A. You can delete the log files so that they are automatically recreated.

B. You can boot into `Directory Services Restore Mode` and use the `set path logs` command within the `Ntdsutil` utility.

C. You can boot into `Directory Services Restore Mode` and use the `move logs to` command within the `Ntdsutil` utility.

D. You can directly modify the Registry so that it points to the new location.

☑ B. The `set path logs` command within `Ntdsutil` allows you to tell Active Directory where the logs are currently located. It is designed to be used in situations exactly like the one described in the question. The command must be run from within `Directory Services Restore Mode` so that the Active Directory database is not initialized during the operation.

⌧ Answer A is incorrect. In most situations like this one, Active Directory does not recreate the log files when they are deleted. Answer C is also incorrect. The `move logs to` command within `Ntdsutil` cannot be used when Active Directory is not aware of the current location of the log files. Answer D is incorrect. Although it might work, it is important to remember that Microsoft always recommends using a provided utility in lieu of directly modifying the Registry. Thus, this is not the best solution.

### 7. You have been promoted to network engineer and are training someone from the help desk to move up to your previous network admin role. You stress the importance of monitoring the log files each day to spot Active Directory problems early. Which of the following logs do you specify as important for the new admin to monitor? (Choose all that apply.)

A. The System event log

B. The Application event log

C. The Directory Service event log

D. The File Replication Service event log

E. The DNS Server event log

☑ A, B, C, D, E. All of these event logs are important to monitor. Answer A is correct because the directory service depends on the core functionality of the operating system, which writes messages to this event log. Answer B is also correct. The Application event log contains Group Policy and other related AD events. Answer C is correct because it is the primary log file to which AD writes messages. Answer D is also correct. The File Replication Service log deals with directory connection objects and replication of Group Policy. Finally, Windows 2000 and later clients depend on the DNS server service to locate Active Directory DCs, so Answer E is correct.

⌧ All answers are correct.

### 8. The network engineer for whom you work is concerned about the impact of monitoring too many performance counters. She asks that you limit your monitoring to the core directory service performance object and its counters only. Which of the following will this allow you to monitor?

A. `DS Search sub-operations/sec`

B. `DRA inbound and outbound counters`

C. `Context Switches/sec`

D. `% DPC Time`

☑ A, B. The primary directory service performance object is the `NTDS object`. Answers A and B are counters within this object. `DRA inbound and outbound counters` are used to track the amount of replication information that flows into and out of a site. Significant changes can indicate a major increase in the amount of replication traffic or a shift in the site replication topology. Significant changes in the `DS Search sub-operations/sec` counter can indicate an application that is incorrectly targeting a DC, or performance problems involving the DC.

⌧ Answer C is incorrect because this counter is tracked using the `System object`, not the `NTDS object`. `Context Switches/sec` tracks when the processor switches between waiting processes. This counter can indicate too many applications (including operating system applications) for the processor to service, or applications that are too active for the processor to keep up with. Answer D is incorrect because this counter is tracked using the `Processor object`. `% DPC Time` is valuable in alerting you to delayed execution of processes resulting from the DC being too busy to execute them.

## Backing Up and Restoring Active Directory

### 9. You’ve just taken over a new job and have been reviewing the backup logs. On one of your new DCs, the log shows that the Active Directory database is failing to back up. It also shows that several key components of the operating system, such as the Registry, are not even selected for backup. Which of the following is the best option for ensuring that these critical system components get backed up?

A. Verify that `Volume Shadow Copy` is enabled
