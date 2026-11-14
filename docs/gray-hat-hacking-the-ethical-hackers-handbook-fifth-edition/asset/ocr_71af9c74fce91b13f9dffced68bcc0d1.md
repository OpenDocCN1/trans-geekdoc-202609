# # Attack Highlights

Host name: 10.0.0.162
IP Address: 10.0.0.162
Port: 3210
Login: cyber\user (SMB1)
Start Timestamp: 29/06/2017 14:49:57
End Timestamp: 29/06/2017 14:52:57

# SMB 445
Name: GothamFinancial3_MT
IP address: 10.0.0.16
Emulation type: Windows Station
OS: Microsoft Windows 7

+   - Login: 4
+   - Files: 4
+   - Process: 4
+   - Service: 1
+   - Connection: 4

# ## Files

+   - PSEXESVC.exe 87dfa38f5776f5f20724455e8832a8
+   - file.exe c67e2af589b417e720c6c11e47a03f

# ## Attack Details

| Time | Description |
|---|---|
| 14:49:57 | Logon: cyber\user (SMB1) |
| 14:49:57 | Connect: \\10.0.0.16\ADMIN$ |
| 14:49:57 | Connect: \\10.0.0.16\IPC$ |
| 14:49:57 | Connect: \\10.0.0.16\C$ |
| 14:49:57 | Dir: C:\* |
| 14:49:57 | Remove directory: C:\folder1 |
| 14:49:57 | AT Execute: id 2, zoom.exe |
| 14:49:57 | AT list: |
| 14:49:57 | Create File: C:\windows\PSEXESVC.exe |
| 14:49:57 | Create Service: Service Name: PSEXESVC, Binary Path: %SystemRoot%\PSEXESVC.exe |
| 14:49:57 | Create File: C:\windows\file.exe |

# ## Static Analysis

Notice how the attacker started the PSEXEC service and created a file (file.exe). You may view the dynamic analysis of that file in a sandbox report that includes behavior, network activity, processes, artifacts, registry key activity, and file-system activity.