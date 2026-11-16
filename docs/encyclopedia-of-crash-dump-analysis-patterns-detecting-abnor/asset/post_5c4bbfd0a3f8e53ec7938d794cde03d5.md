
```
0x7f4cacc42cc0: 0x0   0x0
0x7f4cacc42cd0: 0x0   0x0
0x7f4cacc42ce0: 0xffffffffed  0x3ad3affa
0x7f4cacc42cf0: 0x7f4cacc42d00  0x0
0x7f4cacc42d00: 0x7f4cacc42d20  0x49c740 <default_attr>
0x7f4cacc42d10: 0x7f4cacc439c0  0x400771  <_Z6procNev19>
0x7f4cacc42d20: 0x7f4cacc42d30  0x4007aa  <_Z7bar_twov+9>
0x7f4cacc42d30: 0x7f4cacc42d40  0x4007b5  <_Z7foo_twov+9>
0x7f4cacc42d40: 0x7f4cacc42d60  0x4007c8  <_Z10thread_twoPv+17>
0x7f4cacc42d50: 0x0   0x0
0x7f4cacc42d60: 0x0   0x4140f0  <start_thread+208>
0x7f4cacc42d70: 0x0   0x7f4cacc43700
0x7f4cacc42d80: 0x0   0x0
0x7f4cacc42d90: 0x0   0x0
[...]
```

However, supposed return addresses need to be checked for **Coincidental Symbolic Information** (page 134) pattern.

## Mac OS X

This is a Mac OS X / GDB counterpart to **Execution Residue** pattern on Windows platforms (page 371):

```
(gdb) bt
#0 0x00007fff8616e82a in __kill ()
#1 0x00007fff8fa9ba9c in abort ()
#2 0x000000010269dc29 in bar_5 ()
#3 0x000000010269dc39 in bar_4 ()
#4 0x000000010269dc49 in bar_3 ()
#5 0x000000010269dc59 in bar_2 ()
#6 0x000000010269dc69 in bar_1 ()
#7 0x000000010269dc79 in bar ()
#8 0x000000010269dca0 in main (argc=1, argv=0x7fff6229cb00)

(gdb) x $rsp
0x7fff6229ca38: 0x8fab9a9c

(gdb) x/1000a 0x7ffff6229c00
0x7ffff6229c00: 0x7fff8947b000 0x7fff8947b570
0x7ffff6229c10: 0x4f3ee10c 0x7fff90cb0000
0x7ffff6229c20: 0x7fff90cbad40 0x4e938b16
[...]
0x7ffff6229c5f0: 0x7fff622d8d80 0x10269d640
0x7ffff6229c600: 0x7fff6229cad0 0x7fff622a460b
0x7fff6229c610: 0x100000000 0x269d000
0x7fff6229c620: 0x7fff6229c630 0x10269db59 <_foo_8+9>
0x7fff6229c630: 0x7fff6229c640 0x10269db69 <_foo_7+9>
0x7fff6229c640: 0x7fff6229c650 0x10269db79 <_foo_6+9>
0x7fff6229c650: 0x7fff6229c660 0x10269db89 <_foo_5+9>
0x7fff6229c660: 0x7fff6229c670 0x10269db99 <_foo_4+9>
0x7fff6229c670: 0x7fff6229c680 0x10269dba9 <_foo_3+9>
0x7fff6229c680: 0x7fff6229c690 0x10269dbb9 <_foo_2+9>
0x7fff6229c690: 0x7fff6229c6a0 0x10269dbc9 <_foo_1+9>
0x7fff6229c6a0: 0x7fff6229cac0 0x10269dbee <_foo_30>
0x7ffff6229c6b0: 0x0 0x0
0x7ffff6229c6c0: 0x0 0x0
[...]
0x7ffff6229c8d0: 0x7fff6229c960 0x7fff622b49cd
0x7ffff6229c8e0: 0x10269f05c 0x0
0x7ffff6229c8f0: 0x7fff622c465c 0x7fff8a31e5c0 <_Z21dyldGlobalLockReleas ev>
0x7ffff6229c900: 0x7fff8fab99eb <abort> 0x10269f05c
0x7ffff6229c910: 0x101000000000000 0x7fff622d2110
0x7ffff6229c920: 0x7fff622d8d80 0x10269f078
0x7ffff6229c930: 0x7fff622daac8 0x18
0x7ffff6229c940: 0x0 0x0
0x7ffff6229c950: 0x10269e030 0x0
0x7ffff6229c960: 0x7fff6229c980 0x7fff622a1922
0x7ffff6229c970: 0x0 0x0
0x7ffff6229c9a0: 0x7fff6229ca50 0x7fff8a31e716 <dyld_stub_binder_+13>
0x7ffff6229c990: 0x1 0x7fff6229cb00
0x7ffff6229c9a0: 0x7fff6229cb10 0xe223ea612ddc10b7
0x7ffff6229c9b0: 0x8 0x0
0x7ffff6229c9c0: 0xe223ea612ddc10b7 0x0
0x7fff6229c9d0: 0x0 0x0
0x7fff6229c9e0: 0x585f5f00474e414c 0x20435058005f4350
0x7fff6229c9f0: 0x0 0x0
0x7fff6229ca00: 0x0 0x0
0x7fff6229ca10: 0x0 0x0
0x7fff6229ca20: 0x0 0x0
0x7fff6229ca30: 0x7fff6229ca60 0x7fff8fab9a9c <abort+177>
0x7fff6229ca40: 0x0 0x0
0x7fff6229ca50: 0x7fffffffffff 0x0
0x7fff6229ca60: 0x7fff6229ca70 0x10269dc29 <bar_+59>
0x7fff6229ca70: 0x7fff6229ca80 0x10269dc39 <bar_+49>
0x7fff6229ca80: 0x7fff6229ca90 0x10269dc49 <bar_+39>
0x7fff6229ca90: 0x7fff6229caa0 0x10269dc59 <bar_+29>
0x7fff6229caa0: 0x7fff6229cab0 0x10269dc69 <bar_+19>
0x7fff6229cab0: 0x7fff6229cac0 0x10269dc79 <bar_+9>
0x7fff6229cac0: 0x7fff6229cad0 0x10269dca0 <main+32>
0x7fff6229cad0: 0x7fff6229cb00 0x1
0x7fff6229cae0: 0x7fff6229caf0 0x10269db34 <start+52>
0x7fff6229caf0: 0x0 0x1
0x7fff6229cb00: 0x7fff6229cc48 0x0
0x7fff6229cb10: 0x7fff6229ccae 0x7fff6229ccca
[...]
```

Here's the source code of the modeling application:

```
#define def_call(name,x,y) void name##_#x()( { name##_#y(); } )
#define def_final(name,x) void name##_#x()( { }
#define def_final_abort(name,x) void name##_#x()( { abort(); } )
#define def_init(name,y) void name()( { name##_#y(); } )
#define def_init_alloc(name,y,size) void name()( { int arr[size]; name##_#y(); } *arr=0; } )
def_final(foo,9)
def_call(foo,8,9)
def_call(foo,7,8)
def_call(foo,6,7)
def_call(foo,5,6)
def_call(foo,4,5)
def_call(foo,3,4)
def_call(foo,2,3)
def_call(foo,1,2)
def_init_alloc(foo,1,256)
def_final_abort(bar,5)
def_call(bar,4,5)
def_call(bar,3,4)
def_call(bar,2,3)
def_call(bar,1,2)
def_init(bar,1)
int main(int argc, const char * argv[])
{
    foo();
    bar();
}
```

## Managed Space

This is a .NET counterpart to unmanaged and native code Execution Residue pattern. Here we can use SOS extension !DumpStack command for call level execution residue (see Caller-n-Callee pattern example, page 111) and !DumpStackObjects (!dso) for managed object references found on a raw stack:

```
0:011> !DumpStackObjects
OS Thread Id: 0x8e0 (11)
ESP/REG Object Name
09efe4b8 0a2571bc System.Threading.Thread
09efe538 0a1ffddc System.Threading.Thread
09efe844 0a1ffba8 UserQuery
09efe974 0a1ffce0 System.Signature
09efea20 0a1ffd10 System.RuntimeTypeHandle[]
09efea88 08985e14 System.Object[] (System.Reflection.AssemblyName[])
09efeaea 0a1ffa78 System.Diagnostics.Stopwatch
09efeaf0 0a1ffa6c LINQPad.Extensibility.DataContext.QueryExecutionManager
09efea0c 0a1ffba8 UserQuery
09efeb00 0a1ffa58 System.RuntimeType
09efeb04 08995474 LINQPad.ObjectGraph.Formatters.XhtmlWriter
09efeb08 08985dfc System.Reflection.Assembly
09efeb0c 08985dc8 LINQPad.ExecutionModel.ResultData
09efeb10 08985458 LINQPad.ExecutionModel.Server
09efebdc 0a1ffb8e System.Reflection.RuntimeMethodInfo
09efebf0 0a1ffcc4 LINQPad.ExecutionModel.ConsoleTextReader
09efebe4 0a1fcddc System.IO.StreamReader+NullStreamReader
09efebeb 0899544c System.IO.TextWriter+SyncTextWriter
09efebec 08985efc System.Reflection.AssemblyName
09efebf0 08985d4c System.String C:\Users\Training\AppData\Local\Temp\LINQPad\fcamvgpa
09efec30 08984548 LINQPad.ExecutionModel.Server
09efeedc 08985910 System.Threading.ThreadStart

0:011> !DumpObj 0a2571bc
Name: System.Threading.Thread
MethodTable: 790fe784
EEClass: 790fe694
Size: 56(0x38) bytes
(C:)\Windows\assembly\GAC_32\mscorlib\2.0.0.0__b77a5c561934e089\mscorlib.dll)
Fields:
MT Field Offset Type VT Attr Value Name
7910a5c4 4000634 4 ...Contexts.Context 0 instance 08980ee4 m_Context
79104de8 4000635 8 ...ExecutionContext 0 instance 00000000 m_ExecutionContext
790fd8c4 4000636 c System.String 0 instance 00000000 m_Name
790fe3b0 4000637 10 System.Delegate 0 instance 00000000 m_Delegate
79130084 4000638 14 System.Object[]() 0 instance 00000000 m_ThreadStaticsBuckets
7912d7c0 4000639 18 System.Int32[]() 0 instance 00000000 m_ThreadStaticsBits
791028f4 400063a 1c ...ation.CultureInfo 0 instance 00000000 m_CurrentCulture
791028f4 400063b 20 ...ation.CultureInfo 0 instance 00000000 m_CurrentUICulture
790fdf0f 400063c 24 System.Object 0 instance 00000000 m_StartArg
791016bc 400063d 28 System.IntPtr 1 instance 8f69280 DONT_USE_InternalThread
79102229 400063e 2c System.Int32 1 instance 2 m_Priority
79102290 400063f 30 System.Int32 1 instance 11 m_ManagedThreadId
7910a7a8 4000640 168 ..LocalDataStoreMgr 0 shared static s_LocalDataStoreMgr
>> Domain:Value 007010a8:0c6c4ef4 08e65d48:00000000 <<
790fd6f0 4000641 16c System.Object 0 shared static s_SyncObject
>> Domain:Value 007010a8:017b25d8 08e65d48:0898381c <<
```

Although unmanaged, CLR and JIT-code residue is useful for analysis, for example, as shown in **Handled Exception** (page 428) pattern examples.

## Comments

Sometimes, if no exceptions are found on raw stack we can search all runtime types, for example:

```
0:000> !DumpRuntimeTypes
[...]
09b893e8 05179888 05622254 CustomException
[...]
09bcd368 ? 6969470c System.NullReferenceException
[...]
```

For the pattern about **NULL Code Pointer** (page 750), we created a simple program that crashes when we pass a NULL thread procedure pointer to `CreateThread` function. We might expect to see little in the raw stack data 72 because there was no user-supplied thread code. In reality, if we dump it we will see a lot of symbolic information for code and data including ASCII and UNICODE fragments that we call **Execution Residue** patterns, and one of them is **Exception Handling Residue** 73 we can use to check for **Hidden Exceptions** (page 457) and differentiate between 1st and 2nd chance exceptions 74. Code residues are very powerful in reconstructing stack traces manually 75 or looking for partial stack traces and **Historical Information** (page 483).

To show typical execution residues we created another small program with two additional threads based on Visual Studio Win32 project. After we dismiss `About` box we create the first thread, and then we crash the process when creating the second thread because of the NULL thread procedure:

```
typedef DWORD (WINAPI *THREADPROC)(PVOID);

DWORD WINAPI ThreadProc(PVOID pvParam)
{
    for (unsigned int i = 0xFFFFFFFF; i; --i);
    return 0;
}

// Message handler for about box.
INT_PTR CALLBACK About(HWND hDlg, UINT message, WPARAM wParam, LPARAM lParam)
{
    UNREFERENCED_PARAMETER(lParam);
    switch (message)
    {
    case WM_INITDIALOG:
        return (INT_PTR)TRUE;

    case WM_COMMAND:
        if (LOWORD(wParam) == IDOK || LOWORD(wParam) == IDCANCEL)
        {
            EndDialog(hDlg, LOWORD(wParam));
            THREADPROC thProc = ThreadProc;
            HANDLE hThread = CreateThread(NULL, 0, ThreadProc, 0, 0, NULL);
            CloseHandle(hThread);
            Sleep(1000);
        }
        hThread = CreateThread(NULL, 0, NULL, 0, 0, NULL);
```
