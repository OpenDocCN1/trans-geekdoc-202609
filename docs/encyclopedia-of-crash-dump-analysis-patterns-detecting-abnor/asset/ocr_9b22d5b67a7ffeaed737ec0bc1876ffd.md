```
nt!MmCleanProcessAddressSpace+0x6b
nt!PspExitThread+0x5F1
nt!PspTerminateThreadByPointer+0x4b
nt!PspSystemThreadStartup+0x3c
nt!KiThreadStartup+0x16
```

+   - [88629310 winlogon.exe]
+   - [88a4d9b0 cssrs.exe]
+   - [88d9f8b0 winlogon.exe]
+   - [88cd5840 wfshell.exe]
+   - [8a252440 OUTLOOK.EXE]
+   - [8a194fb8 WINWORD.EXE]
+   - [88aabd20 ctfmon.exe]
+   - [889ef440 EXCEL.EXE]
+   - [88bec838 HoggiaGUI2.exe]
+   - [88692020 cssrs.exe]
+   - [884dd508 winlogon.exe]
+   - [88be1d88 wfshell.exe]
+   - [886a7d88 OUTLOOK.EXE]
+   - [889baa70 WINWORD.EXE]
+   - [8861e3d0 ctfmon.exe]
+   - [887bbb68 EXCEL.EXE]
+   - [884e4020 cssrs.exe]
+   - [8889d218 winlogon.exe]
+   - [887c8020 wfshell.exe]

Threads Processed: 1101

What if we have a list of processes from a complete memory dump by using !process 0 0 command and we want to interrogate the specific process? In this case, we need to switch to that process and reload user space symbol files (.process /r /p address).