# User Space

Windows imposes a restriction on the number of GDI handles per process, and by default, it is approx. 10,000. If this number is reached, we can have abnormal software behavior symptoms such as hangs, glitches in visual appearance, and out-of-memory exceptions resulted in error messages and crashes. We already documented this analysis pattern for kernel and complete memory dumps that we called Handle Limit (GDI, Kernel Space, page 417). However, one of Software Diagnostics Services’ training customers reported an out-of-memory exception with trace analysis diagnostics pointing to 10,000 leaked GDI objects. The process memory dump was saved, and the customer asked whether it was possible to analyze it, or similar memory dumps to find out from the dump itself whether we have GDI leak and what GDI objects were involved.

We recreated one of the applications from the kernel pattern variant (the one that leaks fonts) with one modification that it just stops after 10,000 font creation attempts. After launch, we tried to open About dialog box, but the whole application became unresponsive, and no dialog box was visible. We save the process memory dump and found out that its Main Thread (page 614) was inside Dialog Box (page 232) processing:

```
0:000> kc
 # Call Site
00 user32!NtUserWaitMessage
01 user32!DlgLogBox2
02 user32!InternalDialogBox
03 user32!DlgLogBoxIndirectParamAorW
04 user32!DlgLogBoxParamW
05 GUIHandleLeak!WndProc
06 user32!UserCallWinProcCheckWow
07 user32!DispatchMessageWorker
08 GUIHandleLeak!WinMain
09 GUIHandleLeak!invoke_main
0a GUIHandleLeak!__scrt_common_main_seh
0b kernel32!BaseThreadInitThunk
0c ntdll!RtlUserThreadStart
```

In order to look at GDI handle table we studied the relevant chapters in Feng Yuan’s book “Windows Graphics Programming” and the post86 which has all necessary structure definitions.

We get the current process GDI table address from the disassembly:

```
0:000> .asm no_code_bytes
Assembly options: no_code_bytes

0:000> uf gdi32!GdiQueryTable
gdi32!GdiQueryTable:
00007ffc`7f172610 sub     rsp,38h
00007ffc`7f172614 or      qword ptr [rsp+20h],0FFFFFFFFFFFFFFFh
```

86 http://stackoverflow.com/questions/13905661/how-to-get-list-of-gdi-handles