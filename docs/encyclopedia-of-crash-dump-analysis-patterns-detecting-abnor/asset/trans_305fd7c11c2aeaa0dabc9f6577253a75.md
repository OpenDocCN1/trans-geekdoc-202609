
产品版本: 2.0.50727.5444
文件标志: 0 (掩码 3F)
文件操作系统: 4 未知 Win32
文件类型: 2.0 Dll
文件日期: 00000000.00000000
翻译: 0409.04b0
公司名称: Microsoft Corporation
产品名称: Microsoft® .NET Framework
内部名称: mscorwks.dll
原始文件名: mscorwks.dll
产品版本: 2.0.50727.5444
文件版本: 2.0.50727.5444 (Win7SP1GDR.050727-5400)
文件描述: Microsoft .NET 运行库 公共语言运行时 - 工作站
法律版权: © Microsoft Corporation. 保留所有权利。
注释: Flavor=Retail

它比我们已安装的版本略新（.5444 对 .3619）。客户还将其框架版本连同内存转储文件一起发送过来。因此我们卸载当前的 SOS 扩展（有关详细信息，请参阅 **托管代码异常模式**，第 617 页）：

```
0:000> .chain
Extension DLL chain:
C:\Windows\Microsoft.NET\Framework64\v2.0.50727\sos: image 2.0.50727 3619, API 1.0.0, built Mon Oct 25 06:52:09 2010
[path: C:\Windows\Microsoft.NET\Framework64\v2.0.50727\sos.dll]
dbghelp: image 6.11.0001.404, API 6.1.6, built Thu Feb 26 02:10:27 2009
[path: C:\Program Files\Debugging Tools for Windows (x64)\dbghelp.dll]
ext: image 6.11.0001.404, API 1.0.0, built Thu Feb 26 02:10:26 2009
[path: C:\Program Files\Debugging Tools for Windows (x64)\winext\ext.dll]
exts: image 6.11.0001.404, API 1.0.0, built Thu Feb 26 02:10:17 2009
[path: C:\Program Files\Debugging Tools for Windows (x64)\WINXP\exts.dll]
ntsdexts: image 6.1.7601.5, API 1.0.0, built Thu Feb 26 02:09:22 2009
[path: C:\Program Files\Debugging Tools for Windows (x64)\WINXP\ntsdexts.dll]
0:000> .unload C:\Windows\Microsoft.NET\Framework64\v2.0.50727\sos
Unloading C:\Windows\Microsoft.NET\Framework64\v2.0.50727\sos extension DLL
```

加载客户版本：

```
0:000> .load \\MyData\\sos.dll
0:000> .chain
Extension DLL chain:
\\MyData\\sos.dll: image 2.0.50727.5444, API 1.0.0, built Sun Feb 06 21:14:12 2011
[path: \\MyData\\sos.dll]
dbghelp: image 6.11.0001.404, API 6.1.6, built Thu Feb 26 02:10:27 2009
[path: C:\Program Files\Debugging Tools for Windows (x64)\dbghelp.dll]
ext: image 6.11.0001.404, API 1.0.0, built Thu Feb 26 02:10:26 2009
[path: C:\Program Files\Debugging Tools for Windows (x64)\winext\ext.dll]
exts: image 6.11.0001.404, API 1.0.0, built Thu Feb 26 02:10:17 2009
[path: C:\Program Files\Debugging Tools for Windows (x64)\WINXP\exts.dll]
uext: image 6.11.0001.404, API 1.0.0, built Thu Feb 26 02:10:20 2009
[path: C:\Program Files\Debugging Tools for Windows (x64)\winext\uext.dll]
ntsdexts: image 6.1.7015.0, API 1.0.0, built Thu Feb 26 02:09:22 2009
[path: C:\Program Files\Debugging Tools for Windows (x64)\WINXP\ntsdexts.dll]

0:000> .cordll -ve -u -1
CLR DLL status: No load attempts
```

然后我们尝试加载：

```
0:000> !CLRStack
CLR DLL: C:\Windows\Microsoft.NET\Framework64\v2.0.50727\mscordacwks.dll:2.0.50727.3619 f:0
doesn't match desired version 2.0.50727.5444 f:0
CLR DLL: Unable to find mscordacwks_AMD64_AMD64_2.0.50727.5444.dll by mscorwks search
CLR DLL: Unable to find 'mscordacwks_AMD64_AMD64_2.0.50727.5444.dll' on the path
CLR DLL: Unable to get version info for
'c:\ms\mscorwks.dll\4D4F0A6299d000\mscordacwks_AMD64_AMD64_2.0.50727.5444.dll', Win32 error 0n87
CLR DLL: ERROR: Unable to load DLL mscordacwks_AMD64_AMD64_2.0.50727.5444.dll, Win32 error 0n87
Failed to load data access DLL, 0x80004005
Verify that:
- you have a recent build of the debugger (6.2.14 or newer)
- the file mscordacwks.dll that matches your version of mscorwks.dll is in the version directory
- or, if you are debugging a dump file, verify that the file mscordacwks_<arch>_<arch>_<version>.dll is on your symbol path.
- you are debugging on the same architecture as the dump file. For example, an IA64 dump file must be debugged on an IA64 machine.

You can also run the debugger command .cordll to control the debugger's load of mscordacwks.dll. .cordll
-ve -u -l will do a verbose reload. If that succeeds, the SOS command should work on retry.

If you are debugging a minidump, you need to make sure that your executable path is pointing to
mscorwks.dll as well.
```

按照说明，我们将 mscordacwks.dll 重命名为 mscordacwks_AMD64_AMD64_2.0.50727.5444.dll，然后重试：

```
0:000> .cordll -ve -u -1
CLR DLL status: No load attempts

0:000> !CLRStack
CLR DLL: C:\Windows\Microsoft.NET\Framework64\v2.0.50727\mscordacwks.dll:2.0.50727.3619 f:0
doesn't match desired version 2.0.50727.5444 f:0
CLR DLL: Loaded DLL \MyData\mscordacwks_AMD64_AMD64_2.0.50727.5444.dll
OS Thread Id: 0x16e8 (0)
Child-SP RetAddr Call Site
0000000002fe570 00007feeb8e378 System.Windows.Forms.Application+ComponentManager.System.Windows.Forms.UnsafeNativeMethods.IMsoComponentManager.FPushMessageLoop(Int32, Int32, Int32)
0000000002fe7c0 00007feebf8de5 System.Windows.Forms.Application+ThreadContext.RunMessageLoopInner(Int32,
System.Windows.Forms.ApplicationContext)
0000000002fe910 00007ff002364b6 System.Windows.Forms.Application+ThreadContext.RunMessageLoop(Int32,
System.Windows.Forms.ApplicationContext)
00000000002fe970 00007feee6414c2 MyApplication.Main(System.String[])
```

```
0:000> !pe
Exception object: 0000000034a13f8
Exception type: System.IO.FileNotFoundException
Message: Could not load file or assembly 'System.Windows.Forms.XmlSerializers, Version=2.0.0.0,
Culture=neutral, PublicKeyToken = ...' or one of its dependencies. The system cannot find the file
specified.
InnerException: System.IO.FileNotFoundException, use !PrintException 0000000034a1b28 to see more
StackTrace (generated):
SP IP Function
000000002FD0A0 0000000000000001
mscorlib_ni!System.Reflection.Assembly._nLoad(System.Reflection.AssemblyName, System.String,
System.Security.Policy.Evidence, System.Reflection.Assembly, System.Threading.StackCrawlMark ByRef,
Boolean, Boolean)+0x2
000000002FD0A0 0000007FEED7ABF61
mscorlib_ni!System.Reflection.Assembly.InternalLoad(System.Reflection.AssemblyName,
System.Security.Policy.Evidence, System.Threading.StackCrawlMark ByRef, Boolean)+0x1a1
000000002FD130 0000007FEED7E4804
mscorlib_ni!System.Reflection.Assembly.Load(System.Reflection.AssemblyName)+0x24
0000000002FD170 0000007FEE7855C0A
System.Xml_ni!System.Xml.Serialization.TempAssembly.LoadGeneratedAssembly(System.Type, System.String,
System.Xml.Serialization.XmlSerializerImplementation ByRef)+0x11a

StackTraceString: <none>
HResult: 80070002

0:000> !PrintException 0000000034a1b28
Exception object: 0000000034a1b28
Exception type: System.IO.FileNotFoundException
Message: Could not load file or assembly 'System.Windows.Forms.XmlSerializers, Version=2.0.0.0,
Culture=neutral, PublicKeyToken = ...' or one of its dependencies. The system cannot find the file
specified.
InnerException: <none>
StackTrace (generated):
<none>
StackTraceString: <none>
HResult: 80070002
```

## WOW64

有时我们会从 x64 Windows 获取进程转储，并在 WinDbg 中加载它，输出会告知我们异常或断点源自 wow64.dll。例如：

```
Loading Dump File [X:\ppid2088.dmp]
User Mini Dump File with Full Memory: Only application data is available

Comment: 'Userdump generated complete user-mode minidump with Exception Monitor function on SERVER01'
Symbol search path is: srv*c:\mss*http://msdl.microsoft.com/download/symbols
Executable search path is:
Windows Server 2003 Version 3790 (Service Pack 2) MP (4 procs) Free x64
Product: Server, suite: TerminalServer
Debug session time: Tue Sep  4 13:36:14.000 2007 (GMT+2)
System Uptime: 6 days 3:32:26.081
Process Uptime: 0 days 0:01:54.0000
WARNING: tsappcmp overlaps ws2_32
WARNING: msvcp60 overlaps oleacc
WARNING: tapij32 overlaps rasapi32
WARNING: rtutils overlaps rasman
WARNING: dnsapi overlaps rasapi32
WARNING: wldap32 overlaps dnsapi
WARNING: ntshrui overlaps userenv
WARNING: wtsapi32 overlaps dnsapi
WARNING: winsta overlaps setupapi
WARNING: activds overlaps rtutils
WARNING: actedvs overlaps rasman
WARNING: adsldpc overlaps actedvs
WARNING: drprov overlaps apphelp
WARNING: netui1 overlaps netui0
WARNING: davclnt overlaps apphelp
...
This dump file has an exception of interest stored in it.
The stored exception information can be accessed via .ecxr.
(2088.2fe4): Unknown exception - code 000006d9 (first/second chance not available)
wow64!Wow64NotifyDebugger+0x9:
00000000`b606369 b001    mov     al,1
```

分析表明，引发了运行时异常（**软件异常**，第 875 页），但堆栈跟踪显示所有进程线程中仅有 WOW64 CPU 模拟代码：

```
0:000> !analyze -v
****************************************************************************************
*                                                                                      *
*                                  Exception Analysis                                  *
*                                                                                      *
****************************************************************************************
```
