# Managed Space

Here we have a managed space counterpart to unmanaged **Stack Trace Collection** (page 943) pattern. When looking at crash dumps from a different than a postmortem analysis machine we might need the appropriate **Version-Specific SOS Extension** (page 1058). To list all managed stack traces we use this combined command:

```
0:000> ~*e !CLRStack
OS Thread Id: 0x36F0 (0)
Child SP               IP Call Site
0031cf84 779b0f34 [HelperMethodFrame: 0031cf84]
0031cfd8 6b65665e System.Collections.ArrayList.GetEnumerator()
0031cfe4 059f4c92 ActiproSoftware.SyntaxEditor.EditorView.a(System.Windows.Forms.PaintEventArgs,
System.Drawing.Rectangle, ActiproSoftware.SyntaxEditor.DocumentLine,
ActiproSoftware.SyntaxEditor.DisplayLine, ActiproSoftware.SyntaxEditor.EditPositionRange, Int32 ByRef)
0031e158 05a1798 ActiproSoftware.SyntaxEditor.EditorView.OnRender(System.Windows.Forms.PaintEventArgs)
0031e748 04c5f888 ActiproSoftware.WinUICore.UIElement.Render(System.Windows.Forms.PaintEventArgs)
0031e758 04c5f602 ActiproSoftware.WinUICore.Control.OnRenderChildElements(System.Windows.Forms.PaintEventArgs)
0031e80c 04c5flac ActiproSoftware.WinUICore.WinUICore.UIControl.Render(System.Windows.Forms.PaintEventArgs)
0031e81c 04c5e6fe ActiproSoftware.WinUICore.UIControl.a(System.Windows.Forms.PaintEventArgs)
0031e9a4 04c5e415 ActiproSoftware.WinUICore.UIControl.OnPaint(System.Windows.Forms.PaintEventArgs)
0031e9d4 6f9156f5 System.Windows.Forms.Control.PaintWithErrorHandling(System.Windows.Forms.PaintEventArgs, Int16)
0031e9e8 69f1809e System.Windows.Forms.Control.WmPaint(System.Windows.Forms.Forms.Message ByRef)
0031ead4 69f873b1 System.Windows.Forms.Control.WndProc(System.Windows.Forms.Forms.Message ByRef)
0031lead8 69f102aa [InlinedCallFrame: 0031lead8]
0031eb2c 69f102aa System.Windows.Forms.ScrollableControl.WndProc(System.Windows.Forms.Forms.Message ByRef)
0031eb38 048269c3 ActiproSoftware.SyntaxEditor.SyntaxEditor.WndProc(System.Windows.Forms.Forms.Message ByRef)
0031ebe8 69f870f3 System.Windows.Forms.Control+ControlNativeWindow.OnMessage(System.Windows.Forms.Forms.Message
ByRef)
0031ebf0 69f07071 System.Windows.Forms.Control+ControlNativeWindow.WndProc(System.Windows.Forms.Forms.Message
ByRef)
0031eec4 69f96fb6 System.Windows.Forms.NativeWindow.CallBack(IntPtr, Int32, IntPtr, IntPtr)
0031eee4 00e71365 [InlinedCallFrame: 0031eee4]
0031eee40 69f22eec DomainNeutralILStubClass.IL_STUB_PInvoke(MSG ByRef)
0031eee44 69f171ff [InlinedCallFrame: 0031eee44]
System.Windows.Forms.Forms.UnsafeNativeMethods.DispatchMessageW(MSG ByRef)
0031eee88 69f171ff System.Windows.Forms.Forms.Application+ComponentManager.System.Windows.Forms.Forms.
UnsafeNativeMethods.IMsoComponentManager.FPushMessageLoop(IntPtr, Int32, Int32)
0031eee8c 69f1e62c [InlinedCallFrame: 0031eee8c]
0031ef24 69f1e62c System.Windows.Forms.Forms.Application+ThreadContext.RunMessageLoopInner(Int32,
System.Windows.Forms.Forms.ApplicationContext)
0031ef7c 69f16c81 System.Windows.Forms.Forms.Application+ThreadContext.RunMessageLoop(Int32,
System.Windows.Forms.Forms.ApplicationContext)
0031efac 69ea366d System.Windows.Forms.Forms.Application.Run(System.Windows.Forms.Forms.Form)
0031fcf0 003c3fd0 LINQPad.Program.Run(System.String, Boolean, System.String, Boolean, Boolean,
System.String)
0031f0b4 003c1515 LINQPad.Program.Go(System.String[])
0031f2e4 003c0584 LINQPad.Program.Start(System.String[])
0031f324 003c034f LINQPad.Program.Main.Run(System.String[])
0031f330 003c00f5 LINQPad.Loader.Main(System.String[])
0031f570 6c1721db [GCFrame: 0031f570]
OS Thread Id: 0x36F0 (1)
Unable to walk the managed stack. The current thread is likely not a
```