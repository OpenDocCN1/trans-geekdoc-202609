
log files, the HIDS is looking for certain activities that typify hostile actions or misuse, such as the following:

- Logins at odd hours
- Login authentication failures
- Addition of new user accounts
- Modification or access of critical system files
- Modification or removal of binary files (executables)
- Starting or stopping processes
- Privilege escalation
- Use of certain programs

In general, most HIDSs will operate in a very similar fashion. Figure 19-4 shows the logical layout of a typical HIDS. By considering the function and activity of each component, you can gain some insight into how HIDSs operate.

As on any IDS, the traffic collector on an HIDS pulls in the information the other components, such as the analysis engine, need to examine. For most host-based systems, the traffic collector pulls data from information the local system has already generated, such as error messages, log files, and system files. The traffic collector is responsible for reading those files, selecting which items are of interest, and forwarding them to the analysis engine. On some host-based systems, the traffic collector will also examine specific attributes of critical files, such as file size, date modified, or checksum.

![](img/922567202a944c5e8d3ba0168d2ad3a5_399_0.png)

Figure 19-4
Host-based IDS components

![](img/922567202a944c5e8d3ba0168d2ad3a5_399_1.png)

The analysis engine is perhaps the most important component of the IDS, as it must decide what activity is “okay” and what activity is “bad.” The analysis engine is a sophisticated decision-making and pattern-matching mechanism—it looks at the information provided by the traffic collector and tries to match it against known patterns of activity stored in the signature database. If the activity matches a known pattern, the analysis engine can react, usually by issuing an alert or alarm. An analysis engine may also be capable of remembering how the activity it is looking at right now compares to traffic it has already seen or may see in the near future so that it can match more complicated, multistep malicious activity patterns. An analysis engine must also be capable of examining traffic patterns as quickly as possible, as the longer it takes to match a malicious pattern, the less time the IDS or human operator has to react to malicious traffic. Most IDS vendors build a “decision tree” into their analysis engines to expedite pattern matching.

In IDSs, a decision tree is used to help the analysis engine quickly examine traffic patterns. The decision tree helps the analysis engine eliminate signatures that don’t apply to the particular traffic being examined so that the engine can make the fewest number of comparisons. For example, in the following illustration, the sample IDS decision tree shown may contain a section dividing the traffic into three sections based upon origin of the traffic (a log entry for events taken from the system logs, file changes for modifications to critical files, or user actions for something a user has done). When the analysis engine looks at the traffic pattern and starts down the decision tree, it must decide which path to follow. If it is a log entry, the analysis engine can then concentrate on only the signatures that apply to log entries; it does not need to worry about signatures that apply to file changes or user actions. This type of decision tree allows the analysis engine to function much faster, as it does not have to compare traffic to every signature in the database, just the signatures that apply to that particular type of traffic.

The *signature database* is a collection of predefined activity patterns that have already been identified and categorized—patterns that typically indicate suspicious or malicious activity. When the analysis engine has a traffic pattern to examine, it will compare that pattern to the appropriate signatures in the database. The signature database can contain anywhere from a few to a few thousand signatures, depending on the vendor, type of IDS, space available on the system to store signatures, and other factors.

The *user interface* is the visible component of the IDS—the part that humans interact with. The user interface varies widely depending on the product and vendor and could be anything from a detailed GUI to a simple command line. Regardless of the type and complexity, the interface is provided to allow the user to interact with the system: changing parameters, receiving alarms, tuning signatures and response patterns, and so on.

To better understand how a HIDS operates, take a look at examples from a Linux system and a Windows system.

On a Linux system, the HIDS is likely going to examine any of a number of system logs—basically large text files containing entries about what is happening on the system. For this example, consider the following lines from the “messages” log on a Red Hat system:

```
Jan 5 18:20:39 jeep su(pam_unix) [32478]: session opened for user bob by (uid=0)
Jan 5 18:20:47 jeep su(pam_unix) [32516]: authentication failure;
    logname= uid=502 euid=0 tty= user=bob rhost= user=root
Jan 5 18:20:53 jeep su(pam_unix) [32517]: authentication failure; logname= uid=502 euid=0 tty= ruser=bob rhost= user=root
Jan 5 18:21:06 jeep su(pam_unix) [32519]: authentication failure; logname= uid=502 euid=0 tty= ruser=bob rhost= user=root
```

In the first line, you see a session being opened by a user named bob. This usually indicates that whoever owns the account bob has logged in to the system. On the next three lines, you see authentication failures as user bob tries to become *root*—the superuser account that can do anything on the system. In this case, user bob tries three times to become root and fails on each try. This pattern of activity could mean a number of different things—bob could be an admin who has forgotten the password for the root account, bob could be an admin and someone has changed the root password without telling him, bob could be a user attempting to guess the root password, or an attacker could have compromised user bob’s account and is now trying to compromise the root account on the system. In any case, the HIDS will work through its decision tree to determine whether an authentication failure in the message log is something it needs to examine. In this instance, when the IDS examines these lines in the log, it will note the fact that three of the lines in the log match one of the patterns it has been told to look for (as determined by the information from the decision tree and the signature database), and it will react accordingly, usually by generating an alarm or alert of some type that appears on the user interface or in an e-mail, page, or other form of message.

On a Windows system, the HIDS will likely examine the Application logs generated by the OS. The three main logs (Application, System, and Security) are similar to the logs on a LINUX system, though the Windows logs are not stored as text files and typically require a utility or application, such as Event Viewer, to read them.

```
Failure Audit  1/5/2013  6:47:29 PM  Security  Logon/Logoff        529  SYSTEM
Failure Audit  1/5/2013  6:47:27 PM  Security  Logon/Logoff        529  SYSTEM
Failure Audit  1/5/2013  6:47:26 PM  Security  Logon/Logoff        529  SYSTEM
Success Audit 1/5/2013  6:47:13 PM  Security  Privilege Use        578  Administrator
Success Audit 1/5/2013  6:47:12 PM  Security  Privilege Use        577  Administrator
Success Audit 1/5/2013  6:47:12 PM  Security  Privilege Use        577  Administrator
Success Audit 1/5/2013  6:47:06 PM  Security  Account Management   643  SYSTEM
Success Audit 1/5/2013  6:46:59 PM  Security  Account Management   643  SYSTEM
```

In the first three lines of the Security log, you see a Failure Audit entry for the Logon/Logoff process. This indicates that someone has tried to log in to the system three times and has failed each time (much like our Linux example). You won’t see the name of the account until you expand the log entry within the Windows Event Viewer tool, but for this example, assume it was the Administrator account—the Windows equivalent of the root account. Here again, you see three login failures—if the HIDS has been programmed to look for failed login attempts, it will generate alerts when it examines
