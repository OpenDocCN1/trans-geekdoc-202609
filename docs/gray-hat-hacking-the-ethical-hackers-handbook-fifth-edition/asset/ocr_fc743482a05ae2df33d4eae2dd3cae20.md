+   * OllyDbg 2.01
+   * DeFixed 1.10
+   * x64dbg (x32 and x64 versions)

Setting up Labeless is a painless process that requires copying the precompiled plug-in to the IDA plug-ins directory and running one of the supported debuggers, which are packaged together with the Labeless release archive.

Following is a typical reverse engineering workflow that showcases Labeless’s usefulness:

+   1. Open the reverse engineering target in the IDA disassembler to get a basic idea of the code complexity.
+   2. Fetch the function annotations from the community using the FIRST plug-in.
+   3. Identify the function or functionality that would benefit from dynamic analysis.

# Lab 4-1: Applying IDA Annotations to x64dbg Debugger

To start this lab, open the x64dbg.exe binary, located in the Labeless release package under the x64dbg folder, in both IDA and x64dbg. The following snippet is the start function (entry point) disassembly, as shown by IDA:

```
public start
start proc near
sub     rsp, 28h
call    __security_init_cookie
add     rsp, 28h
jmp     __tmainCRTStartup
start endp
```

IDA FLIRT (Fast Library Identification and Recognition Technology) signatures matched the cookie initialization __security_init_cookie and CRT startup __tmainCRTStartup and named them accordingly. At the same time, the x86dbg disassembly looks more raw and lacks any annotations, as visible from the following snippet:

```
00007FF6E96F23F8 | 48 83 EC 28      | sub rsp, 28
00007FF6E96F23FC | E8 0F 05 00 00   | call x64dbg.7FF6E96F2910
00007FF6E96F2401 | 48 83 C4 28      | add rsp, 28
00007FF6E96F2405 | E9 02 00 00 00   | jmp x64dbg.7FF6E96F240C
```

You can port all available annotations from IDA quickly by following these steps:

+   1. Open the target binary in IDA and the supported debugger (for example, x64dbg).
+   2. Find out the module base address in the debugger by opening the Memory Map window (ALT-M in x64dbg and OllyDbg). The module’s base address will appear on the same line as the target binary (for example, test.exe if the debugged binary is named test.exe in the file system).