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