# # Version-Specific Extension

This is a pattern similar to **Platform-Specific Debugger** pattern (page 804) by suggesting the course of the further debugging actions. Similar instructions are given when a debugger depends on specialized modules differing from platform (or application) version. We consider here a .NET example where opening a dump shows only that it was perhaps saved manually (**Manual Dump**, page 630) with possible **Hidden Exceptions** (page 457) that need to be dug out:

```
0:000> !analyze -v

FAULTING_IP:
+
00000000`00000000 ?? ???

EXCEPTION_RECORD: ffffffff`ffffffff -- (.exr 0xffffffffffffffff)
ExceptionAddress: 0000000000000000
ExceptionCode: 80000003 (Break instruction exception)
ExceptionFlags: 00000000
NumberParameters: 0
```

We notice a failed attempt for .NET analysis and the following instructions on how to correct it:

```
_MANAGED_STACK: !dumpstack -EE
Failed to load data access DLL, 0x80004005
Verify that 1) you have a recent build of the debugger (6.2.14 or newer)
2) the file mscordacwks.dll that matches your version of mscorwks.dll is in the version directory
3) or, if you are debugging a dump file, verify that the file mscordacwks_<arch>_<arch>_<version>.dll is on your symbol path.
4) you are debugging on the same architecture as the dump file. For example, an IA64 dump file must be debugged on an IA64 machine.
```

You can also run the debugger command .cordll to control the debugger's load of mscordacwks.dll .cordll -ve -u -l will do a verbose reload. If that succeeds, the SOS command should work on retry.

If you are debugging a minidump, you need to make sure that your executable path is pointing to mscorwks.dll as well.

Because we know that we have .NET framework installed on a postmortem debugging machine we check the target module version:

```
0:000> lmv m mscorwks
start end module name
00007fe`ee380000 00007fe`000007fe`eed1000 mscorwks (pdb symbols)
Loaded symbol image file: mscorwks.dll
Image path: C:\Windows\Microsoft.NET\Framework64\v2.0.50727\mscorwks.dll
Image name: mscorwks.dll
Timestamp: Sun Feb 06 20:53:54 2011 (4D4F0A62)
CheckSum: 00990593
ImageSize: 00990000
File version: 2.0.50727.5444
```