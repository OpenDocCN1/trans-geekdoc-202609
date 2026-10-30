# Antivirus Killer

This particular batch file will only work if the person executing it has local administrator privileges. But fortunately, for the malware writer, many people do their day-to-day computer activities while logged on with administrative privileges.

This batch file depends on the command tskill, which will end a process. You can use the process ID or process name. For example, the following will kill antivirus processes:

```
tskill /A ZONEALARM
tskill /A mcafe*
```

This can be followed with del to delete the files for that antivirus, such as:

```
del /Q /F C:\Program Files\kasper~1\*.exe
del /Q /F C:\Program Files\kaspersky\*.*
Note /Q Quiet mode, do not give a Yes/No Prompt before deleting.
/F Ignore read-only setting and delete anyway (FORCE)
```

Later versions of Windows don’t support tskill, but will support a related command taskkill. taskkill is actually more powerful than tskill, so you may wish to use it anyway.

Parameters are listed here:

+   - **/s Computer:** You can specify a computer name or IP address and attempt to kill a task on it. The default is the current computer.
+   - **/u User:** This will run the command under a specific user’s privileges. You will need /p password with this.
+   - **/pid:** Process ID of the task you wish to kill.
+   - **/im:** The image name (i.e. the executable name).
+   - **/t:** Terminate all child processes of the process you are killing.

You may not wish to use a batch file for malware. It is actually rather simple to convert a batch file into an executable file. The website http://www.blackhost.xyz has a batch to exe free download.

# PowerShell

PowerShell is a wonderful addition to Windows. It is Microsoft’s attempt to match the power of the Linux Bash shell. It first was introduced with Windows 7 and is on all subsequent versions of Windows. It is a powerful tool used by administrators to execute a variety of Windows functions. It can also be useful for hacking.

In Windows 7 or Windows Server 2008 you get to PowerShell by Start > All Programs > Accessories > Windows PowerShell. In Windows 8 or 10 you can just type “Powershell” into the search box. You can see the PowerShell interface in Figure 5-7.