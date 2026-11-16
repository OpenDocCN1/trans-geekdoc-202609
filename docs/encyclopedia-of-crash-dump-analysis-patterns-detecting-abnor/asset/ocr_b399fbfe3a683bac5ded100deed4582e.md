# Template Module

It is a common technique in driver development to copy/paste an entire driver sample from WDK and modify it for a specific device or a filter value-adding functionality in a specific driver stack or framework. The problem here is that developers sometimes forget to change module resources and a certain amount of detective work is required to find out the module vendor. Here is an example. In a spooler service there were many **Blocked Threads** (page 82) in displaying **Dialog Box** (page 230):

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