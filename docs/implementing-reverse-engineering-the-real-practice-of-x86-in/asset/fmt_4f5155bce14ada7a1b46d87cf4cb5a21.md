
The `SUB` instruction is creating room for the local variables of the `main` function on the stack, `iNumber1` and `iNumber2`. To check the stack state, we will open the PE file in `x32dbg` and place our first breakpoint at the start of the `main` procedure. The stack state and the `x32dbg` screenshot after the `SUB` instruction is as follows:

```
[ESP] 0012FF3C 0040444A right now is JUNK, Input placeholder for `iNumber1`
[ESP+0x4] 0012FF40 00000000 right now is JUNK, Input placeholder for `iNumber2`
[ESP+0x8] 0012FF44 004012F3 return to 0x004012F3 from 0x00401000
```

![](images/Figure-9.16.jpg)

Figure 9.16: Creating room for our local variable

### Line 36-38

```
; Line 10
push OFFSET $SG4679
call _printf
```

The C/C++ equivalent of the ASM is:

`printf(“Input Number1 : “);`

It will print the string constant `$SG4679` on the console. `$SG4679` was pushed on the stack before the `printf` function call. The stack state after the `CALL` instruction is as follows:

```
[ESP] 0012FF38 0040A140 “Input Number1 : “, parameter to `printf()`
[ESP+0x4] 0012FF3C 0040444A right now is JUNK, Input placeholder for `iNumber1`
[ESP+0x8] 0012FF40 00000000 right now is JUNK, Input placeholder for `iNumber2`
[ESP+0xC] 0012FF44 004012F3 return to 0x004012F3 from 0x00401000
```

### Line 39-43

```
; Line 11
lea eax, DWORD PTR _iNumber1$[esp+12]
push eax
push OFFSET $SG4680
call _scanf
```

The C/C++ code on line 11 asks the user to input the first number, `iNumber1`. This number will be stored at the `&iNumber1` location.

`scanf("%d", &iNumber1);`

In ASM, the LEA instruction is evaluated to:

`lea eax, ss:[esp+0x4]`

This will load the effective address of `ESP+0x4` to `EAX`. This is the memory location on the stack where the `iNumber1` input by the user will be stored. As the `scanf` function expects two arguments, so both the arguments to `scanf` are pushed onto the stack before the `CALL` instruction. Arguments to `scanf` are memory location, on which `iNumber1` is stored, and the string constant `$SG4680`. When a call to `scanf` is done, it will ask the user to enter the number. We have inserted one more breakpoint after the `scanf` function to view the stack after the `scanf` call. Refer to the stack state and `x32dbg` in the following screenshot:

```
[ESP] 0012FF30 0040A154 “%d”, parameter to `scanf()`
[ESP+0x4] 0012FF34 0012FF3C Memory location of Input placeholder for `iNumber1`
[ESP+0x8] 0012FF38 0040A140 “Input Number1 : “, parameter to `printf()`
[ESP+0xC] 0012FF3C 00000007 7 is stored here, Input placeholder for `iNumber1`
[ESP+0x10] 0012FF40 00000000 right now is JUNK, Input placeholder for `iNumber2`
[ESP+0x14] 0012FF44 004012F3 return to 0x004012F3 from 0x00401000
```

![](images/Figure-9.17.jpg)

Figure 9.17: Breakpoint after the first scanf

### Line 44-46

```
; Line 12
push OFFSET $SG4681
call _printf
```

The C/C++ code on line 12 prints the following message on the console:

`printf(“Input Number2 : “);`

In ASM, it does the same by pushing the string constant `$SG4681` on the stack and the call `printf` function.

```
[ESP] 0012FF2C 0040A158 “Input Number2 : “, parameter to `printf()`
[ESP+0x4] 0012FF30 0040A154 “%d”, parameter to `scanf()`
[ESP+0x8] 0012FF34 0012FF3C Memory location of Input placeholder for `iNumber1`
[ESP+0xC] 0012FF38 0040A140 “Input Number1 : “, parameter to `printf()`
[ESP+0x10] 0012FF3C 00000007 7 is stored here, Input placeholder for `iNumber1`
[ESP+0x14] 0012FF40 00000000 right now is JUNK, Input placeholder for `iNumber2`
[ESP+0x18] 0012FF44 004012F3 return to 0x004012F3 from 0x00401000
```

### Line 47-51

```
; Line 13
lea ecx, DWORD PTR _iNumber2$[esp+24]
push ecx
push OFFSET $SG4682
call _scanf
```

The C/C++ code on line 13 asks the user to input the second number, `iNumber2`. This number will be stored at the `&iNumber2` location.

`scanf("%d", &iNumber2);`

In ASM, the LEA instruction is evaluated to:

`lea ecx, ss:[esp+0x14]`

This will load the effective address of `ESP+0x14` to `ECX`. This is memory location on the stack where the `iNumber2` input by the user will be stored. As the `scanf` function expects two arguments, so both the arguments to `scanf` are pushed onto the stack before the `CALL` to the `scanf` function. Arguments to scanf are `iNumber2` and the string constant `$SG4682`. When a call to `scanf` is done, it will ask the user to enter the number. This time, we have entered the same number, 7. We have inserted one more breakpoint after the `scanf` function to view the stack after the `scanf` call. Refer to the stack state and `x32dbg` in the following screenshot:

```
[ESP] 0012FF24 0040A16C "%d"
[ESP+0x4] 0012FF28 0012FF40
[ESP+0x8] 0012FF2C 0040A158 "Input Number2 : ", parameter to `printf()`
[ESP+0xC] 0012FF30 0040A154 "%d", parameter to `scanf()`
[ESP+0x10] 0012FF34 0012FF3C Memory location of Input placeholder for `iNumber1`
[ESP+0x14] 0012FF38 0040A140 "Input Number1 : ", parameter to `printf()`
[ESP+0x18] 0012FF3C 00000007 7 is stored here, Input placeholder for `iNumber1`
[ESP+0x1C] 0012FF40 00000007 7 is stored here, Input placeholder for `iNumber2`
[ESP+0x20] 0012FF44 004012F3 return to 0x004012F3 from 0x00401000
```

![](images/Figure-9.18.jpg)

Figure 9.18: Breakpoint after the second scanf

### Line 51-56

```
; Line 14
mov edx, DWORD PTR _iNumber1$[esp+32]
add esp, 24     ; 00000018H
cmp edx, DWORD PTR _iNumber2$[esp+8]
jne SHORT $LN2@main
```

The C/C++ code on line 14 compares the two numbers:

`if (iNumber1 == iNumber2)`

In ASM, the `MOV` instruction will move `iNumber1` stored at `ss:[esp+0x18]` to `EDX`. The `ADD` instruction will clean the stack by adding 24 bytes to `ESP`. Once the stack is cleaned, the `CMP` instruction compares the value at `EDX` with `ss:[esp+0x4].` As both the numbers are equal, it will set `ZF=1`. As Jump if Not Equal (`JNE`) condition is not met, the instruction pointer will move to the next instruction following the `JNE`. Refer to the stack state after the `JNE` instruction execution and `x32dbg` in the following screenshot:

```
[ESP-0x18] 0012FF24 0040A16C JUNK
[ESP-0x14] 0012FF28 0012FF40 JUNK
[ESP-0x10] 0012FF2C 0040A158 JUNK
[ESP-0xC] 0012FF30 0040A154 JUNK
[ESP-0x8] 0012FF34 0012FF3C JUNK
[ESP-0x4] 0012FF38 0040A140 JUNK
[ESP] 0012FF3C 00000007 7 is stored here, Input placeholder for `iNumber1`
[ESP+0x4] 0012FF40 00000007 7 is stored here, Input placeholder for `iNumber2`
[ESP+0x8] 0012FF44 004012F3 return to 0x004012F3 from 0x00401000
```

![](images/Figure-9.19.jpg)

Figure 9.19: Stack state after JNE

### Line 57-61

```
; Line 15
push OFFSET $SG4684
; Line 17
call _printf
add esp, 4
```

This will push the string constant `$SG4684` on the stack for the `printf` function to print on the console. The `ADD` instruction will perform the stack cleaning. Refer to the stack state and `x32dbg` after the `ADD` instruction in the following screenshot:

```
[ESP-0x4] 0012FF38 0040A170 Now JUNK, "Number1 and Number2 are equal\n"
[ESP] 0012FF3C 00000007 7 is stored here, Input placeholder for `iNumber1`
[ESP+0x4] 0012FF40 00000007 7 is stored here, Input placeholder for `iNumber2`
[ESP+0x8] 0012FF44 004012F3 return to 0x004012F3 from 0x00401000
```

![](images/Figure-9.20.jpg)

Figure 9.20: Stack state after the ADD instruction

### Line 62-65

```
; Line 18
xor eax, eax
add esp, 8
ret 0
_main ENDP
_TEXT ENDS
END
```

`XOR` and the function epilogue will clean up the `EAX` and stack, respectively. `END` will end the code by returning 0. Refer to the stack state and `x32dbg` after the stack cleaning in the following screenshot:

```
[ESP-0xC] 0012FF38 0040A170 Now JUNK, "Number1 and Number2 are equal\n"
[ESP-0x8] 0012FF3C 00000007 Now JUNK, `iNumber1` number 7 entered was stored here
[ESP-0x4] 0012FF40 00000007 Now JUNK, `iNumber1` number 7 entered was stored here
```
