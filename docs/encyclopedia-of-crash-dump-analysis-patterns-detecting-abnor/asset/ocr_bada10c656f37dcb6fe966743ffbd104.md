# I/O Requests

Such requests are implemented via the so-called I/O request packets (IRP) that “travel” from a device driver to a device driver similar to a C++ class method to another C++ class method (where a device object address is similar to a C++ object instance address). An IRP stack is used to keep track of the current driver processing an IRP that is reused between device drivers. It is basically an array of structures describing how a particular driver function was called with appropriate parameters similar to a call frame on an execution thread stack. A long time ago we created a UML diagram depicting the flow of an IRP through the driver (device) stack197. An I/O stack location pointer is decremented (from the bottom to the top) as a thread stack pointer (ESP or RSP). We can list active and completed I/O requests with their stack traces using !irpfind -v WinDbg command:

```
1: kd> !irpfind -v

Scanning large pool allocation table for Tag: Irp? (832c7000 : 833c7000)

Irp [ Thread ] irpStack: (Mj,Mn) DevObj [Driver] MDL Process
8883dc18: Irp is active with 1 stacks 1 is current (= 0x8883dc88)
No Mdl: No System Buffer: Thread 888f8950: Irp stack trace.
cmd flg cl Device File Completion-Context
> [ d, 0] 5 1 88515ae8 888f82f0 00000000-00000000 pending
\FileSystem\Npfs
Args: 00000000 00000000 00110008 00000000

891204c8: Irp is active with 1 stacks 1 is current (= 0x89120538)
No Mdl: No System Buffer: Thread 889635b0: Irp stack trace.
cmd flg cl Device File Completion-Context
> [ 3, 0] 0 1 88515ae8 84752028 00000000-00000000 pending
\FileSystem\Npfs
Args: 0000002a 00000000 00000000 00000000

89120ce8: Irp is active with 1 stacks 1 is current (= 0x89120d58)
No Mdl: No System Buffer: Thread 89212030: Irp stack trace.
cmd flg cl Device File Completion-Context
> [ 3, 0] 0 1 88515ae8 8921be00 00000000-00000000 pending
\FileSystem\Npfs
Args: 00000022 00000000 00000000 00000000

Searching NonPaged pool (80000000 : ffc00000) for Tag: Irp?

[...]

892cbe48: Irp is active with 9 stacks 9 is current (= 0x892cbfd8)
No Mdl: No System Buffer: Thread 892add78: Irp stack trace.
cmd flg cl Device File Completion-Context
[ [ 0, 0] 0 0 00000000 00000000 00000000-00000000
```