```
uext: image 6.11.0001.404, API 1.0.0, built Thu Feb 26 02:10:20 2009
[path: C:\Program Files\Debugging Tools for Windows (x64)\winext\uext.dll]
tsdexts: image 6.1.7015.0, API 1.0.0, built Thu Feb 26 02:09:22 2009
[path: C:\Program Files\Debugging Tools for Windows (x64)\WINXP\ntsdexts.dll]

0:000> .cordll -ve -u -1
CLR DLL status: No load attempts
```

Then we do a load attempt:

```
0:000> !CLRStack
CLRDLl: C:\Windows\Microsoft.NET\Framework64\v2.0.50727\mscordacwks.dll:2.0.50727.3619 f:0
doesn't match desired version 2.0.50727.5444 f:0
CLRDLl: Unable to find mscordacwks_AMD64_AMD64_2.0.50727.5444.dll by mscorwks search
CLRDLl: Unable to find 'mscordacwks_AMD64_AMD64_2.0.50727.5444.dll' on the path
CLRDLl: Unable to get version info for
'c:\ms\mscorwks.dll\4D4F0A6299d000\mscordacwks_AMD64_AMD64_2.0.50727.5444.dll', Win32 error 0n87
CLRDLl: ERROR: Unable to load DLL mscordacwks_AMD64_AMD64_2.0.50727.5444.dll, Win32 error 0n87
Failed to load data access DLL, 0x80004005
Verify that 1) you have a recent build of the debugger (6.2.14 or newer)
2) the file mscordacwks.dll that matches your version of mscorwks.dll is in the version directory
3) or, if you are debugging a dump file, verify that the file mscordacwks_<arch>_<arch>_<version>.dll is
on your symbol path.
4) you are debugging on the same architecture as the dump file. For example, an IA64 dump file must be
debugged on an IA64 machine.

You can also run the debugger command .cordll to control the debugger's load of mscordacwks.dll. .cordll
-ve -u -l will do a verbose reload. If that succeeds, the SOS command should work on retry.

If you are debugging a minidump, you need to make sure that your executable path is pointing to
mscorwks.dll as well.
```

Following instructions we rename mscordacwks.dll to mscordacwks_AMD64_AMD64_2.0.50727.5444.dll
and retry:

```
0:000> .cordll -ve -u -1
CLR DLL status: No load attempts

0:000> !CLRStack
CLRDLl: C:\Windows\Microsoft.NET\Framework64\v2.0.50727\mscordacwks.dll:2.0.50727.3619 f:0
doesn't match desired version 2.0.50727.5444 f:0
CLRDLl: Loaded DLL \MyData\mscordacwks AMD64 AMD64 2.0.50727.5444.dll
OS Thread Id: 0x16e8 (0)
Child-SP RetAddr Call Site
0000000002fe570 00007feeb8e378 System.Windows.Forms.Application+ComponentManager.System.Windows.Forms.UnsafeNativeMethods.IMsoComponentManager.FPushMessageLoop(Int32, Int32, Int32)
0000000002fe7c0 00007feebf8de5 System.Windows.Forms.Application+ThreadContext.RunMessageLoopInner(Int32,
System.Windows.Forms.Forms.ApplicationContext)
0000000002fe910 00007ff002364b6 System.Windows.Forms.Application+ThreadContext.RunMessageLoop(Int32,
System.Windows.Forms.ApplicationContext)
00000000002fe970 00007feee6414c2 MyApplication.Main(System.String[])
```