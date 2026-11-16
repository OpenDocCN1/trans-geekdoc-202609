
## Deviant Module

When looking at the module list (!mv), searching for modules (!imgscan) or examining the particular module (!address, !dh) we may notice one of them as deviant. The deviation may be in (but not limited to as anything is possible):

- suspicious module name
- suspicious protection
- suspicious module load address

```
0:005> !imgscan
MZ at 00040000, prot 00000040, type 00020000 - size 1d000
MZ at 00340000, prot 00000002, type 01000000 - size 9c000
Name: iexplore.exe
MZ at 02250000, prot 00000002, type 00040000 - size 2000
MZ at 023b0000, prot 00000002, type 01000000 - size b000
Name: msimtf.dll
MZ at 03f80000, prot 00000002, type 00040000 - size 2000
MZ at 10000000, prot 00000004, type 00020000 - size 5000
Name: screens_dll.dll
MZ at 16080000, prot 00000002, type 01000000 - size 25000
Name: mdnsNSP.dll
MZ at 6ab50000, prot 00000002, type 01000000 - size 26000
Name: DSSENH.dll
MZ at 6b030000, prot 00000002, type 01000000 - size 5b0000
Name: MSHTML.dll
MZ at 6ba10000, prot 00000002, type 01000000 - size b4000
Name: JSCRIPT.dll
MZ at 6cec0000, prot 00000002, type 01000000 - size 1b000
Name: CRYPTNET.dll
MZ at 6d260000, prot 00000002, type 01000000 - size e000
Name: PNGFILTER.DLL
MZ at 6d2f0000, prot 00000002, type 01000000 - size 29000
Name: msls31.dll
MZ at 6d700000, prot 00000002, type 01000000 - size 30000
Name: MLANG.dll
MZ at 6d740000, prot 00000002, type 01000000 - size 4d000
Name: SSV.DLL
MZ at 6d7b0000, prot 00000002, type 01000000 - size c000
Name: ImgUtil.dll
MZ at 6ddb0000, prot 00000002, type 01000000 - size 2f000
Name: iepeers.DLL
MZ at 6df20000, prot 00000002, type 01000000 - size 33000
Name: IEShims.dll
MZ at 6eb80000, prot 00000002, type 01000000 - size a94000
Name: IEFRAME.dll
MZ at 703b0000, prot 00000002, type 01000000 - size 53000
Name: SWEPRX.dll
MZ at 70740000, prot 00000002, type 01000000 - size 40000
Name: SWEEPRX.dll
MZ at 725a0000, prot 00000002, type 01000000 - size 12000
Name: PNPRNPNP.dll
MZ at 725d0000, prot 00000002, type 01000000 - size 8000
Name: WINRNR.dll
MZ at 725e0000, prot 00000002, type 01000000 - size 136000
Name: MSXML3.dll
MZ at 72720000, prot 00000002, type 01000000 - size c000
Name: wshbth.dll
MZ at 72730000, prot 00000002, type 01000000 - size f000
Name: NAPINSP.dll
MZ at 72890000, prot 00000002, type 01000000 - size 6000
Name: SensApi.dll
MZ at 72ec0000, prot 00000002, type 01000000 - size 42000
Name: WINSPOOL.DRV
MZ at 734b0000, prot 00000002, type 01000000 - size 6000
Name: rasadhlp.dll
MZ at 736b0000, prot 00000002, type 01000000 - size 85000
Name: COMCTL32.dll
MZ at 73ac0000, prot 00000002, type 01000000 - size 7000
Name: MIDIMAP.dll
MZ at 73ae0000, prot 00000002, type 01000000 - size 14000
Name: MSACM32.dll
MZ at 73b00000, prot 00000002, type 01000000 - size 66000
Name: audioeng.dll
MZ at 73c30000, prot 00000002, type 01000000 - size 9000
Name: MSACM32.DRV
MZ at 73c60000, prot 00000002, type 01000000 - size 21000
Name: AudioSes.DLL
MZ at 73c90000, prot 00000002, type 01000000 - size 2f000
Name: WINMMDRV.DLL
MZ at 74290000, prot 00000002, type 01000000 - size bb000
Name: PROPSYS.dll
MZ at 74390000, prot 00000002, type 01000000 - size f000
Name: nlaapi.dll
MZ at 743a0000, prot 00000002, type 01000000 - size 4000
Name: kuser.dll
MZ at 74430000, prot 00000002, type 01000000 - size 15000
Name: Cabinet.dll
MZ at 74450000, prot 00000002, type 01000000 - size 3d000
Name: OLEACC.dll
MZ at 74490000, prot 00000002, type 01000000 - size 1ab000
Name: gdiplus.dll
MZ at 74640000, prot 00000002, type 01000000 - size 28000
Name: MMDevAPI.DLL
MZ at 74670000, prot 00000002, type 01000000 - size 32000
Name: WINMM.dll
MZ at 746b0000, prot 00000002, type 01000000 - size 31000
Name: TAPI32.dll
MZ at 749e0000, prot 00000002, type 01000000 - size 19e000
Name: COMCTL32.dll
MZ at 74b80000, prot 00000002, type 01000000 - size 7000
Name: AVRT.dll
MZ at 74ba0000, prot 00000002, type 01000000 - size 4a000
Name: RASAPI32.dll
MZ at 74ce0000, prot 00000002, type 01000000 - size 3f000
Name: UxTheme.dll
MZ at 74de0000, prot 00000002, type 01000000 - size 2d000
Name: WINTRUST.dll
MZ at 74ea0000, prot 00000002, type 01000000 - size 14000
Name: rasman.dll
MZ at 74f70000, prot 00000002, type 01000000 - size c000
Name: rtutils.dll
MZ at 74f80000, prot 00000002, type 01000000 - size 5000
Name: WSHTCPIP.dll
MZ at 7f4b0000, prot 00000002, type 01000000 - size 21000
Name: NTMARTA.dll
MZ at 75010000, prot 00000002, type 01000000 - size 3b000
Name: RSAENH.dll
MZ at 75050000, prot 00000002, type 01000000 - size 5000
Name: MSIMG32.dll
MZ at 75060000, prot 00000002, type 01000000 - size 15000
Name: GAPAPI.dll
MZ at 750a0000, prot 00000002, type 01000000 - size 46000
Name: SCHANNEL.dll
MZ at 752b0000, prot 00000002, type 01000000 - size 3b000
Name: MSWSOCK.dll
MZ at 75370000, prot 00000002, type 01000000 - size 45000
Name: bcrypt.dll
MZ at 753f0000, prot 00000002, type 01000000 - size 5000
Name: WSHPiP6.dll
MZ at 75400000, prot 00000002, type 01000000 - size 8000
Name: VERSION.dll
MZ at 75420000, prot 00000002, type 01000000 - size 7000
Name: CREDSSP.dll
MZ at 75430000, prot 00000002, type 01000000 - size 35000
Name: ncrypt.dll
MZ at 75480000, prot 00000002, type 01000000 - size 22000
Name: dhcpcsvc6.DLL
MZ at 754b0000, prot 00000002, type 01000000 - size 7000
Name: WINNSI.DLL
MZ at 754c0000, prot 00000002, type 01000000 - size 35000
Name: dhcpcsvc.DLL
MZ at 75500000, prot 00000002, type 01000000 - size 19000
Name: IPHLPAPI.DLL
MZ at 75590000, prot 00000002, type 01000000 - size 3a000
Name: slc.dll
MZ at 755d0000, prot 00000002, type 01000000 - size f2000
Name: CRYPT32.dll
MZ at 75740000, prot 00000002, type 01000000 - size 12000
Name: MSASN1.dll
MZ at 75760000, prot 00000002, type 01000000 - size 11000
Name: SAMLIB.dll
MZ at 75780000, prot 00000002, type 01000000 - size 76000
Name: NETAPI32.dll
MZ at 75800000, prot 00000002, type 01000000 - size 2c000
Name: DNSAPI.dll
MZ at 75a70000, prot 00000002, type 01000000 - size 5f000
Name: sxs.dll
MZ at 75ad0000, prot 00000002, type 01000000 - size 2c000
Name: apphelp.dll
MZ at 75b30000, prot 00000002, type 01000000 - size 14000
Name: Secur32.dll
MZ at 75b50000, prot 00000002, type 01000000 - size 1e000
Name: USERENV.dll
MZ at 75c90000, prot 00000002, type 01000000 - size 7000
Name: PSAPI.DLL
MZ at 75ca0000, prot 00000002, type 01000000 - size c3000
Name: RPCRT4.dll
MZ at 75d70000, prot 00000002, type 01000000 - size 73000
Name: COMDLG32.dll
MZ at 75df0000, prot 00000002, type 01000000 - size 9000
Name: LPK.dll
MZ at 75e00000, prot 00000002, type 01000000 - size dc000
Name: KERNEL32.dll
MZ at 75ee0000, prot 00000002, type 01000000 - size aa000
Name: msvcrt.dll
MZ at 75f90000, prot 00000002, type 01000000 - size 1e8000
Name: iertutil.dll
MZ at 76180000, prot 00000002, type 01000000 - size 29000
Name: imagehlp.dll
MZ at 761b0000, prot 00000002, type 01000000 - size 6000
Name: NSI.dll
MZ at 761c0000, prot 00000002, type 01000000 - size 84000
Name: CLBCatQ.DLL
MZ at 76250000, prot 00000002, type 01000000 - size 49000
Name: WLDAP32.dll
MZ at 762a0000, prot 00000002, type 01000000 - size c6000
Name: ADVAPI32.dll
MZ at 76370000, prot 00000002, type 01000000 - size 4b000
Name: GDI32.dll
MZ at 763c0000, prot 00000002, type 01000000 - size 59000
Name: SHLWAPI.dll
MZ at 76420000, prot 00000002, type 01000000 - size e6000
Name: WININET.dll
MZ at 76510000, prot 00000002, type 01000000 - size b10000
Name: SHELL32.dll
MZ at 77020000, prot 00000002, type 01000000 - size 145000
Name: ole32.dll
MZ at 77170000, prot 00000002, type 01000000 - size 7d000
Name: USP10.dll
MZ at 771f0000, prot 00000002, type 01000000 - size 8d000
Name: OLEAUT32.dll
MZ at 77280000, prot 00000002, type 01000000 - size 18a000
Name: SETUPAPI.dll
MZ at 77410000, prot 00000002, type 01000000 - size 9d000
Name: USER32.dll
MZ at 774b0000, prot 00000002, type 01000000 - size 133000
Name: urlmon.dll
MZ at 775f0000, prot 00000002, type 01000000 - size 127000
Name: ntdll.dll
MZ at 77720000, prot 00000002, type 01000000 - size 3000
Name: Normaliz.dll
MZ at 77730000, prot 00000002, type 01000000 - size 2d000
Name: WS2_32.dll
MZ at 77760000, prot 00000002, type 01000000 - size 1e000
Name: IMM32.DLL
MZ at 77780000, prot 00000002, type 01000000 - size c8000
Name: MSCTF.dll
MZ at 7c340000, prot 00000002, type 01000000 - size 56000
Name: MSVCR71.dll
```
