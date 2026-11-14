
round.

Once we remove the breakpoint and press F7, we jump to the address 0x0041FD12. From there, we follow the same strategy to find a command such as CALL <register>. In the following commands, we will find one here:

```
0041FD78 FFD0 CALL EAX
```

By stepping into the preceding call, we jump to a new address space. In this example, EAX is now equal to 0x002042C2. Here is the content of some instructions at this offset:

```
002042C2 PUSH EBP
002042C3 MOV EBP,ESP
002042C5 AND ESP,FFFFFFF8
002042C8 SUB ESP,34
002042CB PUSH EBX
002042CC PUSH ESI
002042CD PUSH EDI
002042CE PUSH 2203F8
002042D3 PUSH 64
002042D5 PUSH 220558
002042DA PUSH 220404
002042DF PUSH 220418
002042E4 PUSH 22042C
002042E9 CALL DWORD PTR DS:[20F018] ; kernel32.GetPrivateProfileStringA
```

In case you did not notice it yet, this code is the same as the one shown in the entry point, just in a new location, as expected. Let’s again apply our formula to find a CALL EAX, which is base_address + 0x1885 (in this case, 0x00200000 + 0x1885). And there it is —we found our instruction again at the expected offset:

```
00201885 FFD0 CALL EAX
```

This time, EAX is equal to 0x0021FD12 at runtime, so after stepping into this call, we get the following instructions:

```
0021FD12 PUSH EBP
0021FD13 MOV EBP,ESP
0021FD15 AND ESP,FFFFFFF8
0021FD18 SUB ESP,30
0021FD1B PUSH ESI
0021FD1C PUSH EDI
0021FD1D MOV DWORD PTR SS:[ESP+2C],0
0021FD25 MOV DWORD PTR SS:[ESP+34],0
0021FD2D LEA EAX,DWORD PTR SS:[ESP+18]
0021FD31 PUSH EAX
0021FD32 PUSH DWORD PTR SS:[EBP+1C]
0021FD35 PUSH DWORD PTR SS:[EBP+18]
0021FD38 PUSH DWORD PTR SS:[EBP+14]
0021FD3B PUSH DWORD PTR SS:[EBP+10]
0021FD3E PUSH DWORD PTR SS:[EBP+C]
0021FD41 PUSH DWORD PTR SS:[EBP+8]
0021FD44 CALL 0021D0DB
0021FD49 MOV EAX,DWORD PTR SS:[EBP+1C]
0021FD4C MOV DWORD PTR SS:[ESP+C],EAX
0021FD50 MOV EAX,DWORD PTR SS:[ESP+2C]
0021FD54 TEST EAX,EAX
0021FD56 JE 0021FDF1
0021FD5C MOV EAX,DWORD PTR SS:[ESP+34]
0021FD60 TEST EAX,EAX
0021FD62 JE 0021FDF1
```

A couple of things happened here. First, we cannot find another CALL EAX instruction in the addresses, so we are probably close to the end of the decoding phase. Actually, if we step over the call at 0x0021FD44 (by pressing F8), the malware will terminate itself. Therefore, let's step into that call. For the sake of brevity, we will take a shortcut. Eventually, the malware will jump back to the resources section at offset 0x0041FB50, where new decoded instructions are waiting. So let's go there quickly by setting a hardware breakpoint on execution at that address; we can do this by executing the instruction dd 0x41fb50 at the command box from the debugger and then right-clicking the first byte (in the lower-left pane, which is the Memory window) and selecting Breakpoint | Hardware, On Execution, as shown here.

![](img/5f597c6a70133069118d9e804ace3775_533_0.png)

Now when we press F9 to run the malware, we hit our hardware breakpoint successfully. Here are the first instructions at our offset; as expected, we can see a new set of decoded instructions ready to be executed:

```
0041FB50       60      PUSHAD
0041FB51      BE 00414100    MOV ESI,locker.00414000
0041FB56      8DBE 00D0FEFF  LEA EDI,DWORD PTR DS:[ESI+FFFFD000]
0041FB5C      57      PUSH EDI
0041FB5D      EB 0B      JMP SHORT locker.0041FB6A
0041FB5F      90      NOP
```

The common instruction PUSHAD is used to preserve the current values of the CPU registers. This is normally used before decoding data in memory, which is the case here because the ".text" section of the malware was zeroed out and will be filled with the next instructions. This clearly tells us that the malware is decoding itself in memory with the real malicious set of instructions. We can print the current content by entering the command dd 0x401000 in the command box from the debugger:

```
00401000 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 .......00401010 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 .......00401020 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 .......00401030 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 .......00401040 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 .......
```

By stepping into the next instructions, we see that the whole text section is loaded with the real malicious instructions. If we keep stepping into the code, we see that the processes are enumerated. Therefore, let’s set a breakpoint on the proper API in the debugger command box again:

```
bp CreateToolhelp32Snapshot
```

Press F9, and when the breakpoint is hit, press ALT-F9 to return to the malware code at the address 0x0040DE6B. There, we see instructions without them being properly disassembled by the debugger, as shown here:

![](img/5f597c6a70133069118d9e804ace3775_534_0.png)

Let’s make the debugger display those instructions properly by right-clicking any instruction in the upper-left window and selecting the option Analysis | Remove Analysis from Module, as shown here:

![](img/5f597c6a70133069118d9e804ace3775_535_0.png)

After this step, we see the proper assembly code displayed. Here are some important addresses that give us evidence that the processes are being enumerated:

```
0040DE65    CALL DWORD PTR DS:[413A34]    ; kernel32.CreateToolhelp32Snapshot
0040DE85    CALL DWORD PTR DS:[413A4C]    ; kernel32.Process32First
0040DEA5    CALL DWORD PTR DS:[413A50]    ; kernel32.Process32Next
```

## Anti-Debugging Checks

As shown in the previous steps, the first anti-debugging technique of the ransomware is to copy itself to other locations so that if an int3 (0xCC) is set, it will be carried over to the next memory space and will break the code changing the opcodes. Let's see what other anti-debugging techniques will be used by the malware.

Let's remove all the breakpoints (ALT-B). Then, in the upper-left disassembly window, press CTRL-G, go to the address 0x0040E185, set a breakpoint there, and press F9. At this point, the malware will check whether a well-known debugger is running in the infected system by enumerating all the processes and its related modules, trying to find a process or module with the name OLLYDBG, DBG, DEBUG, IDAG, or W32DSM, as shown here.

```
0040E170 8E 16FEFFFF CALL locker.0040F098
0040E182 8B55 FB MOV EDX,DWORD PTR SS:[EBP-8]
0040E185 BB 80E54000 MOV EBX,locker.0040E580
0040E18A 8E 59FFFEFF CALL locker.00405E88
0040E18F 85C0 TEST EAX,EAX
0040E191 74 08 JE SHORT locker.0040E196
0040E193 C886 01 MOV BYTE PTR DS:[ESI],1
0040E196 8D45 EC LEA EAX,DWORD PTR SS:[EBP-14]
0040E199 8057 24 LEA EDX,DWORD PTR DS:[EDI+24]
0040E199 B9 04001000 MOV ECX,104
0040E1A1 8E 75FF7FFF CALL locker.00403924
0040E1A6 8BA5 EC MOV EAX,DWORD PTR SS:[EBP-14]
0040E1A9 8055 F0 LEA EAX,DWORD PTR SS:[EBP-10]
0040E1AC 8E 7FFDFFFF CALL locker.0040F0F8
0040E1B1 8B55 FB MOV EDX,DWORD PTR SS:[EBP-10]
0040E1B4 BB 80E54000 MOV EBX,locker.0040E580
0040E1B9 8E 2A5FFFFF CALL locker.00403924
0040E1BE 85C0 TEST EAX,EAX
0040E1C0 74 08 JE SHORT locker.0040E1C5
0040E1C2 C886 01 MOV BYTE PTR DS:[ESI],1
0040E1C5 8D45 24 LEA EAX,DWORD PTR SS:[EBP+24]
0040E1C8 B9 04001000 MOV ECX,104
0040E1CD 8B 4F57FFFF CALL locker.00403924
0040E1D5 8B45 F4 MOV EAX,DWORD PTR SS:[EBP-1C]
0040E1D8 8D55 EC LEA EDX,DWORD PTR SS:[EBP-14]
0040E1DB 8E 8FFDFFFF CALL locker.0040F098
0040E1E3 8B55 FB MOV EDX,DWORD PTR SS:[EBP-10]
0040E1E6 BB 80E54000 MOV EBX,locker.0040E580
0040E1ED 8E 59FFFEFF CALL locker.004038EC
0040E1F2 85C0 TEST EAX,EAX
0040E1F4 74 08 JE SHORT locker.0040E1F4
0040E1F6 C886 01 MOV BYTE PTR DS:[ESI],1
0040E1F9 8D45 DC LEA EAX,DWORD PTR SS:[EBP-24]
0040E1FF B9 04001000 MOV ECX,104
0040E204 8E 2A5FFFFF CALL locker.00403924
0040E20C 8B45 DC MOV EAX,DWORD PTR SS:[EBP-24]
0040E20F 8D55 E8 LEA EAX,DWORD PTR SS:[EBP-18]
0040E212 B9 04001000 CALL locker.0040F0F8
0040E217 BB 80E54000 MOV EBX,locker.0040E580
0040E21C 8E C55FFFFF CALL locker.004038EC
0040E221 85C0 TEST EAX,EAX
0040E223 74 08 JE SHORT locker.0040E223
0040E225 C886 01 MOV BYTE PTR DS:[ESI],1
0040E228 8D45 24 LEA EAX,DWORD PTR SS:[EBP+24]
0040E22B B9 04001000 MOV ECX,104
0040E230 8E 1165FFFF CALL locker.00403924
0040E236 8B45 D4 MOV EAX,DWORD PTR SS:[EBP-2C]
0040E239 8D55 D8 LEA EDX,DWORD PTR SS:[EBP-28]
0040E23C BB 80E54000 MOV EBX,locker.0040F098
0040E243 8E D9FFFEFF CALL locker.0040E05C
0040E246 BB 80E54000 MOV EBX,locker.0040E580
0040E24B 85C0 TEST EAX,EAX
0040E24D 74 08 JE SHORT locker.0040E252
```

Because we are using Immunity Debugger, we are not going to be caught by this check, but even if we were using OllyDbg, we could either change the name of the executable before running it or patch the binary in memory to force the malware to keep running.

Then, if we keep “stepping into,” the malware will try to find a debugger based on the common names of the drivers installed in the system inside c:\windows\system32\drivers, such as sice.sys and ntice.sys (related to SoftICE) and syser.sys (related to the Syser Kernel Debugger), among others. Also, other checks exist for old virtual drivers (with a .vxd extension), as well as loaded services with paths such as \\.\SICE, \\.\TRW, \\.\SYSER, and so on. Here’s an example of this anti-debugging check.
