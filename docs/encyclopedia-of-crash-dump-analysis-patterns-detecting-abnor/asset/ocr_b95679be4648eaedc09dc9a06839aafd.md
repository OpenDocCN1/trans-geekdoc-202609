Loading Dump File [C:\Program Files (x86)\DebugDiag\Logs\Crash rule for all instances of
TestDefaultDebugger.exe\TestDefaultDebugger_PID_4316__ Date_11_21_2007__Time_04_28_34PM__693__
Second_Chance_Exception_C0000005.dmp]
User Mini Dump File with Full Memory: Only application data is available

Comment: 'Dump created by DbgHost. Second_Chance_Exception_C0000005'
Symbol search path is: srvc:\msst*http://msdl.microsoft.com/download/symbols
Executable search path is:
Windows Vista Version 6000 MP (2 procs) Free x86 compatible
Product: WinNt, suite: SingleUserTS
Debug session time: Wed Nov 21 16:28:34.000 2007 (GMT+0)
System Uptime: 0 days 23:45:39.313
Process Uptime: 0 days 0:01:16.000

This dump file has an exception of interest stored in it.
The stored exception information can be accessed via .ecxr.
(10dc.590): Access violation - code c0000005 (first/second chance not available)
eax=00000000 ebx=00000001 ecx=0017fe70 edx=00000000 esi=00425ae8 edi=0017fe70
eip=004014f0 esp=0017f898 ebp=0017f8a4 iopl=0 nv up ei ng nz ac pe cy
cs=0023 ss=002b ds=002b es=002b fs=0053 gs=002b efl=00010297
TestDefaultDebugger!CTestDefaultDebuggerDlg::OnBnClickedButton1:
004014f0 c7050000000000000000 mov dword ptr ds:[0],0 ds:002b:00000000=????????