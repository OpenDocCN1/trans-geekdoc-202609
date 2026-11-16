# Incomplete Session

It is a useful pattern for the analysis of memory dumps from terminal services environments. Normally, session processes include csrss.exe, winlogon.exe, wfshell.exe (in the case of some Citrix products), explorer.exe and a few user defined processes such as winword.exe, for example:

```
0: kd> !session
Sessions on machine: 6
Valid Sessions: 0 1 3 5 6 8

0: kd> !sprocess 6
Dumping Session 6

__MM_SESSION_SPACE fffffffa6009447000
__MMSESSION fffffffa6009447b40
PROCESS fffffffa800fcce630
SessionId: 6 Cid: 1974 Peb: 7fffffd5000 ParentCid: 147c
DirBase: 158baf000 ObjectTable: ffffff8801ef13b00 HandleCount: 532.
Image: csrss.exe

PROCESS fffffffa800fc77040
SessionId: 6 Cid: 1ae4 Peb: 7fffffd0e00 ParentCid: 147c
DirBase: 152db4000 ObjectTable: ffffff8802084b570 HandleCount: 238.
Image: winlogon.exe

PROCESS fffffffa800fe61040
SessionId: 6 Cid: 1edc Peb: 7efdf000 ParentCid: 1ec8
DirBase: 14df74000 ObjectTable: ffffff88020f486e0 HandleCount: 313.
Image: wfshell.exe

PROCESS fffffffa800ff5a660
SessionId: 6 Cid: 2054 Peb: 7fffffd000 ParentCid: 1dbc
DirBase: 201a81000 ObjectTable: ffffff88020dd56e0 HandleCount: 447.
Image: explorer.exe

PROCESS fffffffa800fe28040
SessionId: 6 Cid: 1ce4 Peb: 7efdf000 ParentCid: 13a8
DirBase: 11f552000 ObjectTable: ffffff8801fe96990 HandleCount: 1842.
Image: WINWORD.EXE

PROCESS fffffffa800f119c10
SessionId: 6 Cid: 2074 Peb: 7efdf000 ParentCid: 2054
DirBase: 2d994f000 ObjectTable: ffffff8801e76aec0 HandleCount: 673.
Image: iexplore.exe
```