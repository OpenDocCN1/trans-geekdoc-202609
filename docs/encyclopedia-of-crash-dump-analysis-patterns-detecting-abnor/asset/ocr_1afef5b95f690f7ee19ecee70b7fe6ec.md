# Mixed Exception

Sometimes we have **Managed Code Exception** (page 617) that was enveloping a handled unmanaged code exception, **(Mixed) Nested Exception** (page 723):

```
0:000> !analyze -v

[...]

EXCEPTION_RECORD: ffffffff -- (.exr 0xffffffffffffffff)
ExceptionAddress: 00000000
  ExceptionCode: 80000003 (Break instruction exception)
ExceptionFlags: 00000000
NumberParameters: 0

ERROR_CODE: (NTSTATUS) 0x80000003 - {EXCEPTION}  Breakpoint  A breakpoint has been reached.

FAULTING_THREAD: 00000cfc

[...]

EXCEPTION_OBJECT: !pe 1f9aflac
Exception object: 1f9aflac
**Exception type: System.AccessViolationException**
Message: Attempted to read or write protected memory. This is often an indication that other memory is corrupt.
InnerException: <none>
StackTrace (generated):
   SP               IP               Function
   0012EF3C 28DD9AF9 DLLALComponent.getFirstField()+0x11

   [...]
   0012EFC8 7B194170 System_Windows_Forms_ni!System.Windows.Forms.Control.OnClick(System.EventArgs)+0x70
   0012EFE0 7B6F74B4
System_Windows_Forms_ni!System.Windows.Forms.Control.WmMouseUp(System.Windows.Forms.Message ByRef,
System.Windows.Forms.MouseButtons, Int32)+0x170
   0012F06C 7BA29B66
System_Windows_Forms_ni!System.Windows.Forms.Control.WndProc(System.Windows.Forms.Message ByRef)+0x861516
   0012F0C4 7B1D1D6A
System_Windows_Forms_ni!System.Windows.Forms.ScrollableControl.WndProc(System.Windows.Forms.Message
ByRef)+0x2a
   0012F0D0 7B1C8640
System_Windows_Forms_ni!System.Windows.Forms.Control+ControlNativeWindow.OnMessage(System.Windows.Forms.M
essage ByRef)+0x10
   0012F0D8 7B1C85C1
System_Windows_Forms_ni!System.Windows.Forms.Control+ControlNativeWindow.WndProc(System.Windows.Forms.Mes
sage ByRef)+0x31
   0012F0EC 7B1C849A System_Windows_Forms_ni!System.Windows.Forms.NativeWindow.Callback(IntPtr, Int32,
IntPtr, IntPtr)+0x5a

[...]
```