

## 崩溃签名不变式

跨平台产品中有时会发生崩溃，其中只有 **崩溃签名**（第 153 页）的一部分相似，例如：

```
x86: cmp dword ptr [eax], 1
x64: cmp dword ptr [r10], 1
```

某个崩溃转储具有以下精简的堆栈跟踪：

```
0: kd> kc
DriverA
win32k!DrvSetMonitorPowerState
win32k!xxxSysCommand
win32k!xxxRealDefWindowProc
win32k!NtUserfnNCDESTROY
win32k!NtUserMessageCall
nt!KiSystemServiceCopyEnd
```

伴随以下有故障的指令：

```
DriverA+0x1234:
cmp word ptr [r11],1 ds:002b:00000000:00000000=????????
```

搜索 DriverA 发现了此前分析过的此 x86 崩溃：

```
0: kd> kc
DriverA
nt!IopfCallDriver
win32k!GreDeviceIoControl
win32k!DrvSetMonitorPowerState
win32k!xxxSysCommand
win32k!xxxRealDefWindowProc
win32k!xxxWrapRealDefWindowProc
win32k!NtUserfnNCDESTROY
win32k!NtUserMessageCall
nt!KiSystemServicePostCall

0: kd> r
DriverA+0x1423:
cmp dword ptr [ecx],1 ds:0023:00000000=????????
```

两个堆栈跟踪中均可见共同的函数名，整体流程相同（x64 跟踪中仅省略了 3 个函数）；我们看到相同的空指针解引用，针对相同的比较指令及相同的比较操作数 #1。

## 崩溃进程

在内核和完整内存转储中，有时可以看到崩溃进程的迹象。这里所说的“崩溃”27，例如是指进程从任务管理器中突然消失。在内存转储中，我们仍然可以将这些进程视为僵尸进程（第 1158 页）。进程列表中发现的特殊进程（第 877 页）有助于在众多僵尸进程中筛选可能的候选项。如果一个进程本应仅启动一次（作为服务），但在进程列表中后来多次以僵尸进程身份被发现，同时也以正常进程身份出现（例如，作为最后对象，第 599 页），那么这可能指向过去发生过的崩溃（或静默终止）。我们还有一个类似的跟踪分析模式：Singleton Event28。以下示例说明了这两种迹象：

```
0: kd> !process 0 0

[...]

PROCESS fffffa80088a5640
SessionId: 0 Cid: 2184 Peb: 7ffffffd7000 ParentCid: 0888
DirBase: 381b8000 ObjectTable: 00000000 HandleCount: 0
Image: WerFault.exe

PROCESS fffffa8007254b30
SessionId: 0 Cid: 20ac Peb: 7fffffffd000 ParentCid: 02cc
DirBase: b3306000 ObjectTable: 00000000 HandleCount: 0
Image: ServiceA.exe

[...]

PROCESS fffffa8007fe2b30
SessionId: 0 Cid: 2a1c Peb: 7fffffffd000 ParentCid: 02cc
DirBase: 11b649000 ObjectTable: fffffa8a014939530 HandleCount: 112
Image: ServiceA.exe
```

## Linux

我们首先在 *加速 Mac OS X 内核转储分析*29 培训中介绍了 **关键区域** 模式，但当时并未将该模式本身提交到目录中。

关键区域通常是由同步对象（如关键段和互斥体）保护的代码区域。但是，**关键区域** 分析模式涉及识别介于竞争函数调用之间的代码区域（“夹心”区域，可能涉及或不涉及同步对象及相应的同步调用，如在 **竞争** 模式中所述，第 1168 页），然后识别此类代码区域引用的任何可能共享的数据：

![](img/d6dfefc8f9ab7106c77a723ff84aaa6d_156_0.png)

```
(gdb) thread apply all bt

Thread 6 (Thread 0x7f2665377700 (LWP 17000)):
#0 0x00000000004151a1 in __int_malloc ()
#1 0x0000000000416cf8 in malloc ()
#2 0x00000000004005a4 in proc ()
#3 0x0000000000400604 in bar_two ()
#4 0x0000000000400614 in foo_two ()
#5 0x000000000040062c in thread_two ()
#6 0x00000000004016c0 in start_thread (arg=<optimized out>)
at pthread_create.c:304
#7 0x0000000000432589 in clone ()
#8 0x0000000000000000 in ?? ()

Thread 5 (Thread 0x7f2664b76700 (LWP 17001)):
#0 __lll_unlock_wake_private ()
at ../nptl/sysdeps/unix/sysv/linux/x86_64/lowlevelLock.S:343
#1 0x000000000041886d in __L_lock_9670 ()
#2 0x0000000000416d22 in malloc ()
#3 0x00000000004005a4 in proc ()
#4 0x0000000000400641 in bar_three ()
#5 0x0000000000400651 in foo_three ()
#6 0x0000000000400669 in thread_three ()
#7 0x00000000004016c0 in start_thread (arg=<optimized out>)
at pthread_create.c:304
#8 0x0000000000432589 in clone ()
#9 0x0000000000000000 in ?? ()

Thread 4 (Thread 0x7f2665b78700 (LWP 16999)):
#0 __lll_lock_wait_private ()
at ../nptl/sysdeps/unix/sysv/linux/x86_64/lowlevelLock.S:97
#1 0x0000000000418836 in __L_lock_9558 ()
#2 0x0000000000416c1c in free ()
#3 0x0000000000400586 in proc ()
#4 0x00000000004005c7 in bar_one ()
#5 0x00000000004005d7 in foo_one ()
#6 0x00000000004005ef in thread_one ()
#7 0x00000000004016c0 in start_thread (arg=<optimized out>)
at pthread_create.c:304
#8 0x0000000000432589 in clone ()
#9 0x0000000000000000 in ?? ()

Thread 3 (Thread 0x1ab1860 (LWP 16998)):
#0 0x000000000042fed1 in nanosleep ()
#1 0x000000000042fda0 in sleep ()
#2 0x000000000040078a in main ()

Thread 2 (Thread 0x7f2663b74700 (LWP 17003)):
#0 __lll_lock_wait_private ()
at ../nptl/sysdeps/unix/sysv/linux/x86_64/lowlevelLock.S:97
#1 0x0000000000418836 in __L_lock_9558 ()
#2 0x0000000000416c1c in free ()
#3 0x0000000000400586 in proc ()
#4 0x00000000004006bb in bar_five ()
#5 0x00000000004006cb in foo_five ()
#6 0x00000000004006e3 in thread_five ()
#7 0x00000000004016c0 in start_thread (arg=<optimized out>)
at pthread_create.c:304
#8 0x0000000000432589 in clone ()
#9 0x0000000000000000 in ?? ()
Thread 1 (Thread 0x7f2664375700 (LWP 17002)):
#0 0x000000000043ef65 in raise ()
#1 0x0000000000409fc0 in abort ()
#2 0x00000000004bf5b in __libc_message ()
#3 0x0000000000412042 in malloc_printerr ()
#4 0x0000000000416c27 in free ()
#5 0x0000000000400586 in proc ()
#6 0x000000000040067e in bar_four ()
#7 0x000000000040068e in foo_four ()
#8 0x00000000004006a6 in thread_four ()
#9 0x00000000004016c0 in start_thread (arg=<optimized out>)
at pthread_create.c:304
#10 0x0000000000432589 in clone ()
#11 0x0000000000000000 in ?? ()
```

从线程 #4 和 #5 中，我们可以识别出这样一个带有共享缓冲区 0x6b8fc0 的区域，该区域可能进一步指向堆条目。

```
(gdb) disassemble proc
Dump of assembler code for function proc:
0x00000000004004f0 <+0>: push %rbp
0x00000000004004f1 <+1>: mov %rsp,%rbp
0x00000000004004f4 <+4>: push %rbx
0x00000000004004f5 <+5>: sub $0x18,%rsp
0x00000000004004f9 <+9>: callq 0x40ac70 <rand>
0x00000000004004fe <+14>: mov %eax,%ecx
0x0000000000400500 <+16>: mov $0x6b8dbbad,%edx
0x0000000000400505 <+21>: mov %ecx,%eax
0x0000000000400507 <+23>: imul %edx
0x0000000000400509 <+25>: sar $0xc,%edx
0x000000000040050c <+28>: mov %ecx,%eax
0x000000000040050e <+30>: sar $0x1f,%eax
0x0000000000400511 <+33>: mov %edx,%ebx
0x0000000000400513 <+35>: sub %eax,%ebx
0x0000000000400515 <+37>: mov %ebx,%eax
0x0000000000400517 <+39>: mov %eax,-0x14(%rbp)
0x000000000040051a <+42>: mov -0x14(%rbp),%eax
0x000000000040051d <+45>: imul $0x2710,%eax,%eax
0x0000000000400523 <+51>: mov %ecx,%edx
0x0000000000400525 <+53>: sub %eax,%edx
0x0000000000400527 <+55>: mov %edx,%eax
0x0000000000400529 <+57>: mov %eax,-0x14(%rbp)
0x000000000040052c <+60>: callq 0x40ac70 <rand>
0x0000000000400531 <+65>: mov %eax,%ecx
0x0000000000400533 <+67>: mov $0x6b8dbbad,%edx
0x0000000000400538 <+72>: mov %ecx,%eax
0x000000000040053a <+74>: imul %edx
0x000000000040053c <+76>: sar $0xc,%edx
0x000000000040053f <+79>: mov    %ecx,%eax
0x0000000000400541 <+81>:   sar    $0x1f,%eax
0x0000000000400544 <+84>:   mov    %edx,%ebx
0x0000000000400546 <+86>:   sub    %eax,%ebx
0x0000000000400548 <+88>:   mov    %ebx,%eax
0x000000000040054a <+90>:   mov    %eax,-0x18(%rbp)
0x000000000040054d <+93>:   mov    -0x18(%rbp),%eax
0x0000000000400550 <+96>:   imul   $0x2710,%eax,%eax
0x0000000000400556 <+102>:  mov    %ecx,%edx
0x0000000000400558 <+104>:  sub    %eax,%edx
0x000000000040055a <+106>:  mov    %edx,%eax
0x000000000040055c <+108>:  mov    %eax,-0x18(%rbp)
0x000000000040055f <+111>:  mov    -0x14(%rbp),%eax
0x0000000000400562 <+114>:  cltq
0x0000000000400564 <+116>:  mov    0x6b8fc0(,%rax,8),%rax
0x000000000040056c <+124>:  test   %rax,%rax
0x000000000040056f <+127>:  je     0x400597 <proc+167>
0x0000000000400571 <+129>:  mov    -0x14(%rbp),%eax
0x0000000000400574 <+132>:  cltq
0x0000000000400576 <+134>:  mov    0x6b8fc0(,%rax,8),%rax
0x000000000040057e <+142>:  mov    %rax,%rdi
0x0000000000400581 <+145>:  callq  0x416bc0 <free>
0x0000000000400586 <+150>:  mov    -0x14(%rbp),%eax
0x0000000000400589 <+153>:  cltq
0x000000000040058b <+155>:  movq   $0x0,0x6b8fc0(,%rax,8)
0x0000000000400597 <+167>:  mov    -0x18(%rbp),%eax
0x000000000040059a <+170>:  cltq
0x000000000040059c <+172>:  mov    %rax,%rdi
0x000000000040059f <+175>:  callq  0x416c90 <malloc>
0x00000000004005a4 <+180>:  mov    %rax,%rdx
0x00000000004005a7 <+183>:  mov    -0x14(%rbp),%eax
0x00000000004005aa <+186>:  cltq
0x00000000004005ac <+188>:  mov    %rdx,0x6b8fc0(,%rax,8)
0x00000000004005b4 <+196>:  jmpq   0x4004f9 <proc+9>
End of assembler dump.
```

