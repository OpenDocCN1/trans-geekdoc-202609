
## Not My Version

### Hardware

This is a hardware counterpart of Not My Version pattern for software (page 744). Some problems manifest themselves on different hardware not used at the time of the product testing. In such cases we can look at the kernel and complete memory dumps, extract hardware information using lsysinfo command and compare differences. This is similar to Virtualized System pattern (page 1075) and might provide troubleshooting hints. One example we have seen in the past, involved a graphics intensive application that relied heavily on hardware acceleration features. It was tested with certain processors and chipsets but after a few years failed to work on one computer despite the same OS image and drivers. lsysinfo command revealed significant hardware differences: the failing client computer was a newer faster multiprocessor machine.

### Software

**Not My Version** is another basic pattern of DLL Hell variety. It is when we look at component timestamps and paths and realize that one of the modules from the production environment is older than we had during development and testing. The **lmft** WinDbg command will produce the necessary output. If there are many modules, we may want to create a CAD graph (Component Age Diagram 158) to spot anomalies visually. Component version check is one of the basic troubleshooting and system administration activities. Here is one example (module start and end load addresses are removed for visual clarity):

```
0:000> kL
Child-SP          RetAddr           Call Site
00000000`0012fed8 00000001`40001093 MyDLL!fnMyDLL
00000000`0012fee0 00000001`40001344 2DLls+0x1093
00000000`0012ff10 00000000`773acdcd 2DLls+0x1344
00000000`0012fff0 00000000`774fc6e1 kernel32!BaseThreadInitThunk+0xd
00000000`0012ff90 00000000`00000000 ntdll!RtlUserThreadStart+0x1d
```

```
0:000> lmft
module name
MyDLL   C:\OLD\MyDLL.dll   Wed Jun 18 14:49:13 2004
user32   C:\Windows\System32\user32.dll   Thu Feb 15 05:22:33 2007
kernel32 C:\Windows\System32\kernel32.dll Thu Nov 02 11:14:48 2006
ntdll   C:\Windows\System32\ntdll.dll   Thu Nov 02 11:16:02 2006
2DLls   C:\2DLls\2DLls.exe   Thu Jun 19 10:46:44 2008 (485A2B04)
uxtheme C:\Windows\System32\uxtheme.dll Thu Nov 02 11:15:07 2006
rpcrt4 C:\Windows\System32\rpcrt4.dll Tue Jul 17 05:21:15 2007
lpk C:\Windows\System32\lpk.dll   Thu Nov 02 11:12:33 2006
oleaut32 C:\Windows\System32\oleaut32.dll Thu Dec 06 05:09:35 2007
usp10 C:\Windows\System32\usp10.dll   Thu Nov 02 11:15:03 2006
ole32   C:\Windows\System32\ole32.dll   Thu Nov 02 11:14:31 2006
advapi32 C:\Windows\System32\advapi32.dll Thu Nov 02 11:11:35 2006
gdi32   C:\Windows\System32\gdi32.dll   Thu Feb 21 04:40:51 2008
msvcrt C:\Windows\System32\msvcrt.dll   Thu Nov 02 11:13:37 2006
imm32   C:\Windows\System32\imm32.dll   Thu Nov 02 11:13:15 2006
msctf   C:\Windows\System32\msctf.dll   Thu Nov 02 11:13:42 2006
```

This pattern should be checked when we have instances of **Module Variety** (page 703) and, especially, **Duplicated Module** (page 287). Note that this pattern can also easily become an anti-pattern when applied to **Unknown Component** (page 1035) 159.

## NULL Pointer

### Linux

#### Code

This is a Linux variant of **NULL Pointer** (code) pattern previously described for Mac OS X (page 747) and Windows (page 750) platforms:

```
(gdb) bt
#0 0x0000000000000000 in ?? ()
#1 0x000000000040531 in procB ()
#2 0x00000000004005f8 in bar_four ()
#3 0x0000000000400608 in foo_four ()
#4 0x0000000000400620 in thread_four ()
#5 0x0000000000401630 in start_thread (arg=<optimized out>)
 at pthread_create.c:304
#6 0x00000000004324e9 in clone ()
#7 0x0000000000000000 in ?? ()

(gdb) disassemble procB
Dump of assembler code for function procB:
0x0000000000400516 <+0>: push %rbp
0x0000000000400517 <+1>: mov %rsp,%rbp
0x000000000040051a <+4>: sub $0x10,%rsp
0x000000000040051e <+8>: movq $0x0,-0x8(%rbp)
0x0000000000400526 <+16>: mov -0x8(%rbp),%rdx
0x000000000040052a <+20>: mov $0x0,%eax
0x000000000040052f <+25>: callq *%rdx
0x0000000000400531 <+27>: leaveq 
0x0000000000400532 <+28>: retq 
End of assembler dump.

(gdb) info r rdx
rdx 0x0 0
```

#### Data

This is a Linux variant of **NULL Pointer** (data) pattern previously described for Mac OS X (page 745) and Windows (page 752) platforms:

```
(gdb) bt
#0  0x0000000000400500 in procA ()
#1  0x000000000040057a in bar_two ()
#2  0x000000000040058a in foo_two ()
#3  0x00000000004005a2 in thread_two ()
#4  0x0000000000401630 in start_thread (arg=<optimized out>) at pthread_create.c:304
#5  0x00000000004324e9 in clone ()
#6  0x0000000000000000 in ?? ()

(gdb) x/i 0x400500
=> 0x400500 <procA+16>:   movl   $0x1,(%rax)

(gdb) info r $rax
rax            0x0  0

(gdb) x $rax
0x0: Cannot access memory at address 0x0
```

### Mac OS X

#### Code

This is a Mac OS X / GDB counterpart to NULL Pointer (Code) pattern:

```
(gdb) bt
#0 0x0000000000000000 in ?? ()
#1 0x000000010e8cce73 in bar (ps=0x7fff6e4cbac0)
#2 0x000000010e8cce95 in foo (ps=0x7fff6e4cbac0)
#3 0x000000010e8cced5 in main (argc=1, argv=0x7fff6e4cbb08)

(gdb) disass 0x000000010e8cce73-3 0x000000010e8cce73
Dump of assembler code from 0x10e8cce70 to 0x10e8cce73:
0x000000010e8cce70 : callq *0x8(%rdi)
End of assembler dump.

(gdb) info r rdi
rdi 0x7fff6e4cbac0 140735043910336

(gdb) x/2 0x7fff6e4cbac0
0x7fff6e4cbac0: 0x00000000a 0x00000000

(gdb) p/x *($rdi+8)
$7 = 0x0

(gdb) bt
#0 0x0000000000000000 in ?? ()
#1 0x000000010e8cce73 in bar (ps=0x7fff6e4cbac0)
#2 0x000000010e8cce95 in foo (ps=0x7fff6e4cbac0)
#3 0x000000010e8cced5 in main (argc=1, argv=0x7fff6e4cbb08)

(gdb) ptype MYSTRUCT
type = struct _MyStruct_tag {
    int data;
    PFUNC pfunc;
}

(gdb) print {MYSTRUCT}0x7fff6e4cbac0
$2 = {data = 10, pfunc = 0}
```

Here's the source code of the modeling application:

```c
typedef void (*PFUNC)(void);

typedef struct _MyStruct_tag
{
    int data;
    PFUNC pfunc;
} MYSTRUCT;

void bar(MYSTRUCT *ps)
{
    ps->pfunc();
}

void foo(MYSTRUCT *ps)
{
    bar(ps);
}

int main(int argc, const char * argv[])
{
    MYSTRUCT pstruct = {10, NULL};

    foo(&pstruct);

    return 0;
}
```

#### Data

This is a Mac OS X / GDB counterpart to NULL Pointer (Data) pattern:

```
(gdb) bt
#0 0x000000010d3b0e90 in bar () at main.c:15
#1 0x000000010d3b0ea9 in foo () at main.c:20
#2 0x000000010d3b0ec4 in main (argc=1,
argv=0x7fff5fc6faf8) at main.c:25

(gdb) disassemble
Dump of assembler code for function bar:
0x000000010d3b0e80 <bar+0>:   push  %rbp
0x000000010d3b0e81 <bar+1>:   mov   %rsp,%rbp
0x000000010d3b0e84 <bar+4>:   movq  $0x0,-0x8(%rbp)
0x000000010d3b0e8c <bar+12>:  mov   -0x8(%rbp),%rax
0x000000010d3b0e90 <bar+16>:  movl  $0x1,(%rax)
0x000000010d3b0e96 <bar+22>:  pop   %bp
0x000000010d3b0e97 <bar+23>:  retq
End of assembler dump.

(gdb) p/x $rax
$1 = 0x0
```

### Windows

#### Code

NULL Pointer is a specialization of Invalid Pointer pattern (page 589), and it is the most easily recognized pattern with a straightforward fix most of the time according to our debugging experience. Checking the pointer value to be non-NULL might not work if the pointer value is random (Wild Pointer pattern, page 1151) but at least it eliminates this class of problems. NULL pointers can be NULL Data Pointers (page 752) or NULL Code Pointers. The latter happens when we have a pointer to some function, and we try to call it. Consider this example:

```
0:002> r
eax=00000000 ebx=00000000 ecx=93630000 edx=00000000 esi=00000000 edi=00000000
eip=00000000 esp=0222ffbc ebp=0222ffec iopl=0 nv up ei pl zr na pe nc
cs=0023 ss=002b ds=002b es=002b fs=0053 gs=002b efl=00010246
00000000 ??
     ???
0:002> kv
ChildEBP RetAddr  Args to Child
WARNING: Frame IP not in any known module. Following frames may be wrong.
0222ffbb 7d4dfe21 00000000 00000000 00000000 0x0
0222ffec 00000000 00000000 00000000 00000000 kernel32!BaseThreadStart+0x34
```

Clearly, we have a NULL code pointer here and if we disassemble backward the return address 7d4dfe21 or BaseThreadStart+0x34 address we would suspect that BaseThreadStart function tried to call a thread start procedure:

```
0:002> ub 7d4dfe21
kernel32!BaseThreadStart+0x10:
7d4dfdfd mov      eax,dword ptr fs:[00000018h]
7d4dfe03 cmp      dword ptr [eax+10h],1E00h
7d4dfe0a jne      kernel32!BaseThreadStart+0x2e (7d4dfe1b)
7d4dfe0c cmp      byte ptr [kernel32!BaseRunningInServerProcess (7d560008)],0
7d4dfe13 jne      kernel32!BaseThreadStart+0x2e (7d4dfe1b)
7d4dfe15 call     dword ptr [kernel32!_imp__CsrNewThread (7d4d0310)]
7d4dfe1b push     dword ptr [ebp+0Ch]
7d4dfe1e call     dword ptr [ebp+8]
```

```
0:002> dp ebp+8 l1
0222fff4 00000000
```
