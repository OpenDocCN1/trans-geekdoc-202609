```
00c1f5b8 7738cee9 USER32!NtUserMessageCall+0xc
00c1f5d8 01438f73 USER32!SendMessageA+0x7f

5: kd> !thread 86214750
THREAD 86214750 Cid 0b94.1238 Teb: 7ffdb000 Win32Thread: bc2f5ea8 RUNNING on processor 2
Not impersonating
DeviceMap		 e3482310
Owning Process		 85790020 Image: SomeExe.exe
Wait Start TickCount	 1415535 Ticks: 0
Context Switch Count	 1745682 LargeStack
UserTime		 00:01:20.031
KernelTime		 00:04:03.484
Win32 Start Address 0x75ec1c3f
Start Address kernel32!BaseThreadStartThunk (0x77e617ec)
Stack Init b4861000 Current b4860558 Base b4861000 Limit b4856000 Call 0
Priority 13 BasePriority 13 PriorityDecrement 0
ChildEBP RetAddr
b4860db8 bf8ada99 nt!PsGetThreadProcess
b4860bf4 bf89d6e6 win32k!IsRestricted+0x2f
b4860c90 bf89da19 win32k!xxxCallHook2+0x12d
b4860cab bf8a137a win32k!xxxCallHook+0x26
b486cec bf85af67 win32k!xxxSendMessageTimeout+0x1e3
b486d010 bf8c182c win32k!xxxWrapSendMessage+0x1b
b486d040 8088978c win32k!NtUserMessageCall+0x9d
b486d040 7c82854c nt!KiFastCallEntry+0xfc
00c1f5fc 00000000 ntdll!KiFastSystemCallRet
```

```
5: kd> !thread 86f87020 1f
THREAD 86f87020 Cid 0238.0ae8 Teb: 7ffa5000 Win32Thread: 00000000 RUNNING on processor 3
IRP List:
86869200: (0006,0094) Flags: 00000900 Mdl: 00000000
85b2a7f0: (0006,0094) Flags: 00000900 Mdl: 00000000
86f80a20: (0006,0094) Flags: 00000800 Mdl: 00000000
85e6af68: (0006,0094) Flags: 00000900 Mdl: 00000000
892ac678: (0006,0094) Flags: 00000900 Mdl: 00000000
85d06070: (0006,0094) Flags: 00000900 Mdl: 00000000
85da35e0: (0006,0094) Flags: 00000900 Mdl: 00000000
87216340: (0006,0094) Flags: 00000900 Mdl: 00000000
Not impersonating
DeviceMap		 e1003940
Owning Process		 8850e020 Image: lsass.exe
Wait Start TickCount	 1415535 Ticks: 0
Context Switch Count	 39608
UserTime		 00:00:01.625
KernelTime		 00:00:05.437
Win32 Start Address RPCRT4!ThreadStartRoutine (0x77c7b0f5)
Start Address kernel32!BaseThreadStartThunk (0x77e617ec)
Stack Init f4925000 Current f4924c38 Base f4925000 Limit f4922000 Call 0
Priority 10 BasePriority 9 PriorityDecrement 0
ChildEBP RetAddr
f4924640 80972e8e nt!SePrivilegeCheck+0x24
f4924678 80944aa0 nt!SeSinglePrivilegeCheck+0x3a
f4924770 8088978c nt!NtOpenProcess+0x13a
f4924770 8082eff5 nt!KiFastCallEntry+0xfc
f49247f8 f6037bee nt!ZwOpenProcess+0x11
```