

```
WARNING: Frame IP not in any known module. Following frames may be wrong.
0160fd9c 00000000 00000000 00000000 00000000 0x7c82847c
```

```
1: kd> !pool 8ac12dc0
Pool page 8ac12dc0 region is Nonpaged pool
8ac12000 size: 858 previous size: 0 (Allocated) TWPG
8ac12858 size: 8 previous size: 858 (Free) ....
8ac12860 size: 20 previous size: 8 (Allocated) VadS
8ac12880 size: 8 previous size: 20 (Free) NtFs
8ac12888 size: 20 previous size: 8 (Allocated) VadS
8ac128a8 size: 28 previous size: 20 (Allocated) NtFn
8ac128d0 size: 30 previous size: 28 (Allocated) Vad
8ac12900 size: 40 previous size: 30 (Allocated) Muta (Protected)
8ac12940 size: 38 previous size: 40 (Allocated) Sema (Protected)
8ac12978 size: 40 previous size: 38 (Allocated) Muta (Protected)
8ac129b8 size: 270 previous size: 40 (Allocated) Thre (Protected)
8ac12c28 size: 40 previous size: 270 (Allocated) Ntfr
8ac12c68 size: d0 previous size: 40 (Allocated) DRIV
8ac12d38 is not a valid large pool allocation, checking large session pool...
8ac12d38 is freed (or corrupt) pool
Bad previous allocation size @8ac12d38, last size was 1a
```

```
***
*** An error (or corruption) in the pool was detected;
*** Attempting to diagnose the problem.
***
*** Use !poolval 8ac12000 for more details.
***
```

```
Pool page [8ac12000] is INVALID.

Analyzing linked list...
[ 8ac12c68 --> 8ac12db8 (size = 0x150 bytes)]: Corrupt region
Scanning for single bit errors...

None found
```

## JIT .NET 代码

查看进程内存转储并看到 CLR 线程（第 124 页）时，我们可以在非托管堆栈跟踪中找到 JIT 编译代码返回地址片段：

```
0:011> KL
ChildEBP RetAddr
WARNING: Frame IP not in any known module. Following frames may be wrong.
0b73e120 0572232e 0x572240f
0b73e134 6af442a 0x57223e2
0b73e1b0 6af44bcc clr!CallDescrWorkerWithHandler+0x8e
0b73e1f0 6af44c01 clr!MethodDesc::CallDescr+0x194
0b73e30c 6af44c21 clr!MethodDesc::CallTargetWorker+0x21
0b73e324 6afb7856 clr!MethodDesc::CallSite::Call+0x1c
0b73e4e8 6afb7ba3 clr!CallWithValueTypes_RetArgSlotWrapper+0x5c
0b73e7b4 6afb7d65 clr!InvokeImpl+0x621
0b73e880 6963d689 clr!RuntimeMethodHandle::InvokeMethodFast+0x180
0b73e8d4 6963d30d mscorlib_ni+0x2bd689
0b73e90c 6963bfed mscorlib_ni+0x2bbfed
0b73e934 69643284 mscorlib_ni+0x2c3284
0b73e958 6af3de7e mscorlib_ni+0x2c3284
0b73eb64 05720988 clr!ListLockEntry::Release+0x68
0b73ebc0 6962ae5b 0x5720988
0b73ebd0 695b7ff4 mscorlib_ni+0x2aae5b
0b73ebc0 695b7f34 mscorlib_ni+0x237ff4
0b73eec0 6962ade8 mscorlib_ni+0x237f34
0b73ec24 6af221db mscorlib_ni+0x2aade8
0b73ec34 6af442a clr!CallDescrWorker+0x33
0b73ecb0 6af44bcc clr!CallDescrWorkerWithHandler+0x8e
0b73ede8 6af44c01 clr!MethodDesc::CallDescr+0x194
0b73ee04 6b0bb512 clr!MethodDesc::CallTargetWorker+0x21
0b73f010 6afd5c05 clr!ThreadNative::KickOffThread_Worker+0x1e1
0b73f024 6afd5c87 clr!Thread::DoExtraWorkForFinalizer+0x114
0b73f0d4 6afd5d42 clr!Thread::ShouldChangeAbortToUnload+0x101
0b73f134 6afc37a2 clr!Thread::ShouldChangeAbortToUnload+0x399
0b73f140 6b0a6465 clr!Thread::RaiseCrossContextException+0xf38
0b73f220 6afc37cf clr!Thread::DoADCallBack+0xf0
0b73f240 6afd5c87 clr!Thread::DoExtraWorkForFinalizer+0xf4a
0b73f2f0 6afd5d42 clr!Thread::ShouldChangeAbortToUnload+0x101
0b73f350 6afd5dd9 clr!Thread::ShouldChangeAbortToUnload+0x399
0b73f374 6b0bb3e5 clr!Thread::ShouldChangeAbortToUnload+0x43a
0b73f38c 6b0bb2e clr!ManagedThreadBase::KickOff+0x15
0b73f424 6afb5a08 clr!ThreadNative::KickOffThread+0x23e
0b73fb44 76573833 clr!Thread::intermediateThreadProc+0x4b
0b73fb50 77c1a9bd kernel32!BaseThreadInitThunk+0xe
```

加载正确的 CLR 版本特定扩展（第 1058 页）后，我们可以检查这些地址并使用 !IP2MD WinDbg SOS 扩展命令获取其方法名、模块和类地址：

```
0:011> !IP2MD 0x572240f
MethodDesc: 057420e8
Method Name: UserQuery+ClassMain.Main()
Class: 057341d8
MethodTable: 05742108
mdToken: 06000004
Module: 05741048
IsJitted: yes
CodeAddr: 05722400
Transparency: Critical
```

```
0:011> !IP2MD 0x57223e2
MethodDesc: 0574204c
Method Name: UserQuery.RunUserAuthoredQuery()
Class: 057340a4
MethodTable: 0574206c
mdToken: 06000001
Module: 05741048
IsJitted: yes
CodeAddr: 057223d0
Transparency: Critical
```

```
0:011> !IP2MD 0x5720988
MethodDesc: 056e601c
Method Name: LINQPad.ExecutionModel.Server.StartClrQuery()
Class: 0571f6e4
MethodTable: 056e60e4
mdToken: 06000c59
Module: 056e336c
IsJitted: yes
CodeAddr: 05720910
Transparency: Critical
```

这些方法调用也可以在 **托管堆栈跟踪**（第 624 页）中看到：

```
0:011> !CLRStack
OS Thread Id: 0xac (11)
Child SP IP       Call Site
0b73e120 0572240f UserQuery+ClassMain.Main()
0b73e128 057223e2 UserQuery.RunUserAuthoredQuery()
0b73e674 6af221dd [DebuggerU2MCatchHandlerFrame: 0b73e674]
0b73e640 6af221dd [CustomGCFrame: 0b73e640]
0b73e614 6af221dd [GCFrame: 0b73e614]
0b73e5f8 6af221dd [GCFrame: 0b73e5f8]
0b73e81c 6af221dd [HelperMethodFrame_PROTECTOBJ: 0b73e81c]
System.RuntimeMethodHandle._InvokeMethodFast(System.IRuntimeMethodInfo, System.Object, System.Object[], System.SignatureStruct ByRef, System.Reflection.MethodAttributes, System.RuntimeType)
0b73e898 6963d689 System.RuntimeMethodHandle.InvokeMethodFast(System.IRuntimeMethodInfo, System.Object, System.Object[], System.SignatureStruct, System.Reflection.MethodAttributes, System.RuntimeType)
0b73e8ec 6963d3d0 System.Reflection.RuntimeMethodInfo.Invoke(System.Object, System.Reflection.BindingFlags, System.Reflection.Binder, System.Object[], System.Globalization.CultureInfo, Boolean)
0b73e928 6963bfed System.Reflection.RuntimeMethodInfo.Invoke(System.Object, System.Reflection.BindingFlags, System.Reflection.Binder, System.Object[], System.Globalization.CultureInfo)
0b73e94c 69643284 System.Reflection.MethodBase.Invoke(System.Object, System.Object[])
0b73e958 0572134c LINQPad.ExecutionModel.Server.RunClrQuery()
0b73eb6c 0572098c LINQPad.ExecutionModel.Server.StartClrQuery()
0b73ebc8 6962ae5b System.Threading.ThreadHelper.ThreadStart_Context(System.Object)
0b73ebd8 695b7ff4 System.Threading.ExecutionContext.Run(System.Threading.ExecutionContext,
System.Threading.ContextCallback, System.Object, Boolean)
0b73ebfc 695b7f34 System.Threading.ExecutionContext.Run(System.Threading.ExecutionContext,
System.Threading.ContextCallback, System.Object)
0b73ec18 6962ade8 System.Threading.ThreadHelper.ThreadStart()
0b73ee30 6af221dd [GCFrame: 0b73ee30]
0b73f0f4 6af221db [DebuggerU2MCatchHandlerFrame: 0b73f0f4]
0b73f18c 6af221db [ContextTransitionFrame: 0b73f18c]
0b73f310 6af221db [DebuggerU2MCatchHandlerFrame: 0b73f310]
```

## 模板模块

在驱动程序开发中，从 WDK 复制/粘贴整个驱动程序示例并针对特定设备或特定驱动程序堆栈或框架中的筛选器增值功能进行修改是一种常见技术。这里的问题是，开发人员有时会忘记更改模块资源，需要进行一定的侦查工作才能找出模块厂商。下面是一个示例。在打印机后台处理程序服务中，显示对话框时有许多 **阻塞线程**（第 82 页）：

```
0:000> ~34kL 100
 Child-SP          RetAddr           Call Site
00000000`08449368 00000000`774c5118 user32!NtUserWaitMessage+0xa
00000000`08449370 00000000`774c5770 user32!DialogBox2+0x261
00000000`084493f0 00000000`774c57e6 user32!InternalDialogBox+0x134
00000000`08449450 00000000`774c3e36 user32!DialogBoxIndirectParamAorW+0x58
00000000`08449490 00000000`fa27c97  user32!DialogBoxParamW+0x66
00000000`084494d0 000007fe`fa28832b unidrvui!ICheckConstraintsDlg+0xbf
00000000`08449950 000007fe`fa29423d unidrvui!UpdateUISettingForOEM+0x2f
00000000`08449980 00000000`50036d2c unidrvui!CPrintOemDriverUI::DrvUpdateUISetting+0x1d
00000000`084499b0 00000000`50038a1d Module2!DllGetClassObject+0x1fe74
[...]
00000000`0844b250 000007fe`f759546b unidrvui!OEMDevicePropertySheets+0x56
00000000`0844b280 000007fe`f759653e compstui!CallpfnPSUI+0x137
00000000`0844b330 000007fe`f7596b84 compstui!InsertPSUIPage+0x24a
00000000`0844b5f0 000007fe`fa2880e9 compstui!CPSUICallBack+0x3ec
00000000`0844b4a0 000007fe`fa2836c4 unidrvui!AddOemUIPluginPages+0x12d
00000000`0844b6d0 000007fe`f759546b unidrvui!DrvDevicePropertySheets+0x2c8
00000000`0844bb60 000007fe`f759653e compstui!CallpfnPSUI+0x137
00000000`0844bc10 000007fe`f7596b84 compstui!InsertPSUIPage+0x24a
00000000`0844bbed 000007fe`fb452838 compstui!CPSUICallBack+0x3ec
00000000`0844bf80 000007fe`f759546b winspool!DevicePropertySheets+0x108
00000000`0844fbf0 000007fe`f759653e compstui!CallpfnPSUI+0x137
00000000`0844c060 000007fe`f7596b84 compstui!InsertPSUIPage+0x24a
00000000`0844c320 000007fe`f759758e compstui!CPSUICallBack+0x3ec
00000000`0844c3d0 000007fe`f75976b2 compstui!DoCommonPropertySheetUI+0xbe
00000000`0844c430 000007fe`fb446339 compstui!CommonPropertySheetUIW+0xe
00000000`0844c470 000007fe`fb44b425 winspool!CallCommonPropertySheetUI+0x65
00000000`0844c4c0 00000000`5003623c winspool!PrinterPropertiesNative+0x121
00000000`0844c950 00000000`50035d16 Module2!DllGetClassObject+0x1f384
[...]
00000000`0844dd70 000007fe`fb4472d8 unidrvui!DrvPrinterEvent+0x419
00000000`0844de00 000007fe`fb4473f winspool!SpoolerPrinterEventNative+0x84
00000000`0844de60 000007fe`faedc957 winspool!SpoolerPrinterEvent+0x13
00000000`0844dea0 000007fe`faedc8c7 localspl!SplDriverEvent+0x4f
00000000`0844def0 000007fe`faec3d74 localspl!PrinterDriverEvent+0xcf
00000000`0844df30 000007fe`fa771f20 localspl!SplAddPrinter+0xae0
00000000`0844e4e0 000007fe`fa7941d8 win32spl!NCSRCommon::TLocalPrinter::AddPrinterW+0xb4
00000000`0844e5b0 000007fe`fa747511 win32spl!TPrintOpen::AddLocalPrinter+0xb8
00000000`0844e6b0 000007fe`fa746dbf win32spl!TPrintOpen::AddAndInstallLocalPrinter+0x34d
00000000`0844e830 000007fe`fa746bb0 win32spl!TPrintOpen::ReEstablishCacheConnectionNoGuidPrinter+0x157
00000000`0844e900 000007fe`fa7467d1 win32spl!TPrintOpen::ReEstablishCacheConnection+0x178
00000000`0844e980 000007fe`fa7465c1 win32spl!TPrintOpen::ReEstablishPrinterConnection+0x16d
00000000`0844ea30 000007fe`fa73e5ad win32spl!TPrintOpen::ReEstablishConnectionFromKey+0x1fd
00000000`0844eb30 000007fe`fa733492 win32spl!TPrintOpen::RediscoverPrinterConnections+0xd7
```

