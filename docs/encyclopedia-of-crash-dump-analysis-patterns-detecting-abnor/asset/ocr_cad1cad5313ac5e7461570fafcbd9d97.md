```
0573ffb8 77e64829 mscorwks!Thread::intermediateThreadProc+0x49
0573ffec 00000000 kernel32!BaseThreadStart+0x34
```

So we run x86 WinDbg and get the better picture of **Nested Exceptions** (page 723):

```
0:010> !analyze -v

[...]

MANAGED_STACK: !dumpstack -EE
OS Thread Id: 0xc68 (15)
Current frame:
ChildEBP RetAddr  Caller,Callee

EXCEPTION_OBJECT: !pe 16584f0
Exception object: 016584f0
Exception type: System.InvalidOperationException
Message: There is an error in XML document (12, 12182).
InnerException: System.IO.IOException, use !PrintException 0164f6dc to see more
[...]

StackTraceString: <none>
HResult: 80131509
There are nested exceptions on this thread. Run with -nested for details

EXCEPTION_OBJECT: !pe 164f6dc
Exception object: 0164f6dc
Exception type: System.IO.IOException
Message: Unable to read data from the transport connection: The connection was closed.
InnerException: <none>
[...]

StackTraceString: <none>
HResult: 80131620
There are nested exceptions on this thread. Run with -nested for details

MANAGED_OBJECT: !dumpojb 1655a38
Name: System.String
MethodTable: 790fd8c4
EEClass: 790fd824
Size: 270(0x10e) bytes
(C:\WINDOWS\assembly\GAC_32\mscorlib\2.0.0.0__[...]\mscorlib.dll)
String: Unable to read data from the transport connection: The connection was closed.

EXCEPTION_MESSAGE: Unable to read data from the transport connection: The connection was closed.

MANAGED_OBJECT_NAME: System.IO.IOException
```

There are other pattern instances of this kind when we need a **Platform-Specific Debugger**, for example, to do live debugging of an x86 process on an x64 machine (we need an x64 debugger) or we need to load an old 32-bit DLL extension (we need an x86 debugger) for a postmortem analysis.