to Meterpreter for some of this work. Once we have compromised a Windows system and have a Meterpreter shell, we can use the clearev command. You can see this in the following code. One of the challenges of this approach, though, is that you need to have the right set of permissions.

# ## Clearing Event Viewer with Meterpreter

```
```
meterpreter > clearev
[*] Wiping 635 records from Application...
[-] stdapi_sys_eventlog_clear: Operation failed: Access is denied.
meterpreter > getuid
Server username: NT AUTHORITY\LOCAL SERVICE
```
```

You can see from the output that the compromise used didn't have adequate permissions to be able to clear the system event log. Based on the user ID, we have the LOCAL SERVICE user rather than the LOCALSYSTEM user. The LOCALSYSTEM user would have had the permissions necessary to adjust the logs. This user has limited permissions.

The process would be different on Unix-like systems. Logs there are commonly written in plaintext files. With the right permissions, these files could be altered by just erasing them or even getting in and removing any lines out of the logs that may seem incriminating. Unless there is auditing enabled on the system, editing the logs would be undetectable, which means you could easily alter them without any downside. You could also just stop the syslog process when you get on the system. Anything that happens before that related to gaining access will be logged, but you would be able to do anything else on the system without it being logged. Similarly, if auditing is enabled on the system, you could disable the audit daemon.

# ## Hiding Data

Hiding data is a common activity. Some files can be hidden in plain sight. For example, on a Windows system, there are files that are stored in temporary directories. This is especially true for anything downloaded from the Internet. Figure 7.3 shows a directory listing for the temporary Internet files on a Windows system. This is not a directory most people visit, so it wouldn't be hard to place a file here and just have it never get noticed.

The path to that directory is C:\Users\username\AppData\Local\Microsoft\Windows \Temporary Internet Files, which has a lot of waypoints where you can similarly hide files where they won't be seen. This is in part because, by default, many of the directories shown here are hidden in Windows Explorer unless you change the setting to show them. Essentially, files anywhere in the AppData directory would be lost in the shuffle of a lot of temporary files and application-specific files.

On a Linux system, you can use dot files and dot directories to do the same sort of thing. A dot file has a filename that starts with a dot, such as .bashrc. Regular file listings won't show files that start with a dot. Similarly, you won't see directories that start with a dot. If you put files into one of those directories, they may get lost or overlooked.