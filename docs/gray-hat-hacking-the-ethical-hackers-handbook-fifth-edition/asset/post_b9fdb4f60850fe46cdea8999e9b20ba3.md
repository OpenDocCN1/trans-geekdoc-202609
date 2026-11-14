
RemoteAgent.Monitor.WindowsDebugEngine.description.txt, contains the best information about the crash. An example of a crash log (with some lines removed for brevity) is presented next:

```
C:\peach3\Logs\fuzz_TRUN.xml_TestTRUN_20170529164655\Faults\EXPLOITABLE_0x1b1e681f_0x191a342e\185>type RemoteAgent.Monitor.WindowsDebugEngine.description.txt
******************************************************************************** Symbol Path validation summary **************************************************************************************
Response                   Time (ms)     Location
Deferred                   SRV*http://msdl.microsoft.com/download/symbols

 Microsoft (R) Windows Debugger Version 10.0.15063.400 AMD64
Copyright (c) Microsoft Corporation. All rights reserved.

CommandLine: C:\users\test\downloads\vulnserver.exe

******************************************************************************** Symbol Path validation summary **************************************************************************************
Response                   Time (ms)     Location
Deferred                   SRV*http://msdl.microsoft.com/download/symbols
Symbol search path is: SRV*http://msdl.microsoft.com/download/symbols
Executable search path is:
ModLoad: 00000000`00400000 00000000`00407000   image00000000`00400000
ModLoad: 00007ff8`aefd0000 00007ff8`af1a1000   ntdll.dll
ModLoad: 00000000`777c0000 00000000`77943000   ntdll.dll
ModLoad: 00000000`72100000 00000000`72152000   C:\WINDOWS\System32\wow64.dll
ModLoad: 00000000`72160000 00000000`721d7000   C:\WINDOWS\System32\wow64win.dll
ModLoad: 00000000`000c0000 00000000`0016c000   WOW64_IMAGE_SECTION
...truncated for brevity
ModLoad: 00000000`74ba0000 00000000`74bfa000   C:\WINDOWS\SysWOW64\bcryptPrimitives.dll
ModLoad: 73200000 7324e000   C:\WINDOWS\SysWOW64\mswsock.dll
(5970.5bd4): Access violation - code c0000005 (first chance)
eax=0108f1f8 ebx=00000104 ecx=00e8551c edx=00000000 esi=00401848 edi=00401848
eip=80f88881 esp=0108f9d8 ebp=80808080 iopl=0         nv up ei pl zr na pe nc
cs=0023  ss=002b  ds=002b  es=002b  fs=0053  gs=002b             efl=00010246
80f88881 ??        ???
...truncated for brevity
xmm7=0 0 0 0
80f88881 ??        ???

kb
ChildEBP RetAddr  Args to Child
WARNING: Frame IP not in any known module. Following frames may be wrong.
0108f9d4 c0b88080 80fe69b1 80808080 ac80e0ae 0x80f88881
0108f9d8 80fe69b1 80808080 ac80e0ae e03cb3c0 0xc0b88080
...truncated for brevity

2 !exploitable -m
IDENTITY:HostMachine\HostUser
PROCESSOR:X86
...truncated for brevity
STACK_FRAME:mswsock!DllMain+0x17f
STACK_FRAME:msvcrt!_initptd+0xb6
STACK_FRAME:essfunc+0x10ed
STACK_FRAME:mswsock!DllMainCRTStartup+0x1b
INSTRUCTION_ADDRESS:0xffffff80f88881
INVOKING_STACK_FRAME:3
DESCRIPTION:Data Execution Prevention Violation
SHORT_DESCRIPTION:DEPViolation
3 CLASSIFICATION:EXPLOITABLE
BUG_TITLE:Exploitable - Data Execution Prevention Violation starting at Unknown Symbol @
0xffffff80f88881 called
from mswsock!DllMain+0x00000000000017f (Hash=0x1b1e681f.0x191a342e)
EXPLANATION:User mode DEP access violations are exploitable.
C:\peach3\Logs\Fuzz_TRUN.xml_TestTRUN_20170529164655\Faults\EXPLOITABLE_0x1b1e681f_0x191a342e\185>
```

The file consists of two main sections:

- Crash information collected from the debugger, including loaded module names, information about CPU registers, and an excerpt from memory. This information starts at 1 in the preceding log.

- An !exploitable report that contains information about and a classification of the crash. Information that can be found in this part of the log gives more context to the crash and includes exception code, stack frames information, bug title, and classification. Classification is the !exploitable conclusion about the potential exploitability of the crash. It can contain one of four possible values: Exploitable, Probably Exploitable, Probably Not Exploitable, or Unknown. This information spans from 2 to 3 in the preceding log.

A quick glance at the classification on line 3 will let us know if we need to spend more time on this potential vulnerability. In this case, we see it is vulnerable, but we'll leave the details of further analysis and exploitation for another chapter.

## Lab 3-2: Generation Fuzzing with Peach

You can follow along with the preceding example by performing the following lab steps:

- 1. Download the vulnerable server application (the .exe and .dll) to your test lab or build it yourself (https://github.com/stephenbradshaw/vulnserver). Then place the executable in C:\vulnserver.

- 2. Launch the vulnerable server, like so (note the warning in the output):
  C:\vulnserver>vulnserver.exe

- 3. Download and install the A/V safe version of netcat (without -e) for Windows (https://joncraton.org/blog/46/netcat-for-windows/).

- 4. From another window, test the vulnerable server, like so:
  C:\Users\test\downloads\nc111nt_safe>nc localhost 9999

- 5. Copy the fuzz_TRUN.xml file listed previously (available from the book download site) to the C:\peach3\ folder.

- 6. From an administrator command prompt, start your Peach agent:
  C:\peach3> peach -a tcp

- 7. From a new administrator command prompt, launch the Peach Pit:
  C:\peach3> peach fuzz_TRUN.xml TestTRUN

- 8. Monitor and review the Logs folder (C:\peach3\logs).

![](img/5f597c6a70133069118d9e804ace3775_101_0.png)

**CAUTION** Depending on your version of Windows, you may experience warnings or the vulnerable server may crash and you need to restart testing again. Depending on how lucky (or unlucky) you are, you may need to generate many test cases—even as many as a thousand—before the program generates faults.

## Genetic or Evolutionary Fuzzing with AFL

When it comes to genetic or evolutionary fuzzing, the best option is AFL, particularly for file-based parsers written in C or C++. When source code is available, the application may be instrumented with AFL during compilation with either clang or g++. For this section, we will take a look at this file-parsing application, which would pose a significant challenge to a mutation fuzzer. This program has been adapted from an example given by Gynvael Coldwind (Michael Skłodnikiewicz) during an excellent video blog on genetic fuzzing (see “For Further Reading”). As Gynvael explains, when an application has many nested if/then blocks, it is often difficult, if not impossible, for a mutation fuzzer to reach full code coverage, at least in our lifetime. Consider this simple example:

![](img/5f597c6a70133069118d9e804ace3775_102_0.png)

**NOTE** At this time, we will switch to Kali Linux 2017, which you can download from kali.org.

```
root@kali:~/afl-2.41b# cat input/file.txt
aaaaaaa
root@kali:~/afl-2.41b# cat asdf3.c
#include <stdio.h>
#include <stdlib.h>
#code adapted with permission from Gynvael -
#https://github.com/gynvael/stream-en/tree/master/019-genetic-fuzzing
```

```c
int main(int argc, char **argv) {
    FILE *f = fopen(argv[1], "rb");
    if (!f) {
        return 1;
    }

    char buf[16] = {0};
    fread(buf, 1, 16, f);
    fclose(f);

    if (buf[0] == 'a') {
        if (buf[1] == 'b') {
            if (buf[2] == 'c') {
                if (buf[3] == 'd') {
                    if (buf[4] == 'e') {
                        if (buf[5] == 'f') {
                            if (buf[6] == 'g') {
                                if (buf[7] == 'h') { ① abort();
                                }
                            }
                        }
                    }
                }
            }
        }
    }
    return 0;
}
```

The abort() statement at ① will cause the program to crash. The question is whether the fuzzer will find it. Using a mutation fuzzer, if we submit one input file at a time, we would have a 1 in 256^8 chance of hitting that innermost code block. If your computer was able to process 1,000 files per second (and you were unlucky), it might take upward of a number
