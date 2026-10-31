
In this chapter, we learned pointers to structures with respect to reverse engineering. We discussed about structures code pattern in disassembled code and how structures are stored in memory. The main point to understand is that, pointer to the structure points to the first element of structure as structures are always stored in contiguous memory locations. We also covered structures program with optimized and non-optimized code.

# Chapter 13

## Scanf Program Pattern in Reverse Engineering

Imagine you downloaded some hacking software from the internet. On running this software, it asks you to enter the password. The password is not mentioned anywhere on the site from where you downloaded this software. Using reverse engineering, we can break the password. Breaking a password is unethical and against laws until and unless we are permitted to do so. Now you must be thinking how one can break a password. Breaking a password is dependent on the quality of the software code. If the code is written with security in mind, chances are that a stronger mechanism must have been used.

In this chapter, we will discuss the reverse engineering part of the mechanism used by a software developer to capture user input. We will be talking about `scanf` function, which is used to capture the user input from the console.

### Structure

In this chapter, we will cover the following topics:

* Function `scanf` with Integers
* Function `scanf` without Optimization
* Function `scanf` with Optimization

### Objective

In this chapter, we will understand the `scanf` function with respect to reverse engineering. We will talk about the `scanf` code pattern in the disassembled code and understand how `scanf` inputs are stored in memory. We will also cover the `scanf` program with both optimized and non-optimized code.

### Function scanf with Integers

In this simple C/C++ code, we ask the user to input a number of type integer and print it on the console. We use `scanf` to capture user input and `printf` to print the number entered by the user in our C/C++ code:

![](images/Figure-13.1.jpg)

**Figure 13.1:** `scanfWithIntegers.cpp`

### Function scanf without Optimization

Compile the code without optimization in the MSVC compiler on the same x86 Windows machine. Run the following commands on the Windows command prompt to set the environment for `cl.exe` (VS compiler), and then compile the code with the following switches:

* `/Fa`: Name of the output assembly listing file
* `/Fe`: Name of the output executable file

```
cd C:\Program Files\Microsoft Visual Studio 10.0\VC
vcvarsall.bat
cd C:\JitenderN\REBook\scanfWithIntegers\scanfWithIntegers
cl scanfWithIntegers.cpp /FascanfWithIntegers.asm /FescanfWithIntegers.exe
```

The following is the output of running the preceding commands:

![](images/Figure-13.2.jpg)

**Figure 13.2:** Function `scanf` without Optimization

This will generate the assembly code and the EXE file. This time, before analyzing, we will disable the **Address Space Layout Randomization** (**ASLR**). It’s a security mechanism by which the base address of the PE file is randomized on every load of the **Portable Executable** (**PE**) file generated with our MSVC compiler. This will help us reload the PE file without randomizing its base address. To disable ASLR, refer to the *Appendix*.

We will now use the PE file with the disabled ASLR for further analysis using `x32dbg`. Let’s move to the generated assembly listing:

![](images/Figure-13.3.jpg)

**Figure 13.3:** `scanfWithIntegers.asm`-Part-1

![](images/Figure-13.4.jpg)

**Figure 13.4:** `scanfWithIntegers.asm`-Part-2

Let’s walk through the code:

**Line 27-30**

```
; Line 7
push ebp
mov ebp, esp
push ecx
```

The code starts with a simple `main` function prologue.

**Line 31-34**

```
; Line 9
push OFFSET $SG4678
call _printf
add esp, 4
```

The C/C++ code on line 9 prints the string constant on the console:

`printf ("Enter a Number: ");`

In our assembly code, before calling the `printf` function, the string constant `$SG4678` stored in the `.rdata` segment is pushed onto the stack. Once the arguments to the `printf` functions are pushed onto the stack, the call to the `printf` function is made. On return, 4 bytes are added to `ESP` for stack cleaning. For analyzing the assembly instruction, we will load the PE file in `x32dbg`, and then put two breakpoints. The first breakpoint is at the start of the .TEXT segment and the other breakpoint is just after the `scanf` function return. Now, after loading the PE file in `x32dbg`, run the code. The execution will stop at the first breakpoint. From the first breakpoint **step into** the code using `x32dbg`, until you hit the preceding `add esp,4` instruction. The `ADD` instruction cleans the stack and the following is how the stack looks after executing the `ADD` instruction:

`[ESP-0x4] 0012FF38 0040A140 "Enter a Number: ", arg to 1st printf`

`[ESP] 0012FF3C 00000001 ECX pushed, later to store Integer input passed`

`[ESP+0x4] 0012FF40 0012FF88 [EBP]`

`[ESP+0x8] 0012FF44 004012C4 return to 0x004012C4 from 0x00401000`

![](images/Figure-13.5.jpg)

**Figure 13.5:** Stack after ADD insruction

**Line 35-40**

```
; Line 10
lea eax, DWORD PTR _iInput$[ebp]
push eax
push OFFSET $SG4679
call _scanf
add esp, 8
```

The C/C++ code on line 10 calls the `scanf` function, which accepts the following two arguments:

`scanf ("%d", &iInput);`

In the assembly code, the `LEA` instruction is evaluated to:

`lea eax, ss:[ebp-0x4]`

`LEA` will store the input placeholder memory location in `EAX`. By 'input placeholder memory location’, we mean the memory location which will be used to store the integer input by the user. Once this input placeholder memory location is stored in `EAX`, then it is pushed onto the stack as a parameter to the `scanf` function. Then another push instruction pushes the string constant `$SG4679` on the stack.

The call to `scanf` is made after pushing both the arguments. On return, 8 bytes are added to `ESP` for stack cleaning. The breakpoint is added at the `0x0040101F` memory location. The stack state at breakpoint is as follows:

`[ESP] 0012FF34 0040A154 "%d", parameter to scanf ()`

`[ESP+0x4] 0012FF38 0012FF3C Input placeholder memory location`

`[ESP+0x8] 0012FF3C 00000007 Input placeholder, Number 7 is entered by user`

`[ESP+0xC] 0012FF40 0012FF88 [EBP]`

`[ESP+0x10] 0012FF44 004012C4 return to 0x004012C4 from 0x00401000`

![](images/Figure-13.6.jpg)

**Figure 13.6:** User entered number on stack

**Line 41-46**

```
; Line 11
mov ecx, DWORD PTR _iInput$[ebp]
push ecx
push OFFSET $SG4680
call _printf
add esp, 8
```

The C/C++ code on line 11 calls the `printf` function. This will print the number entered by the user:

`printf ("Number you entered is %d\n", iInput);`

In the assembly code, the `MOV` instruction is evaluated to:

`mov ecx, dword ptr ss:[ebp-0x4]`

The `MOV` instruction will move the user input stored at `ss:[ebp-0x4]` to `ECX`. Now, both the arguments the first is the string constant and the second is the number that the user entered to the `printf` function are pushed on the stack:

`[ESP-0x8] 0012FF34 0040A158 "Number you entered is %d\n", arg to 2nd printf()`

`[ESP-0x4] 0012FF38 00000007 Number 7 is entered by user, arg to 2nd printf()`

`[ESP] 0012FF3C 00000007 Input placeholder, Number 7 is entered by user`

`[ESP+0x4] 0012FF40 0012FF88 [EBP]`

`[ESP+0x8] 0012FF44 004012C4 return to 0x004012C4 from 0x00401000`

![](images/Figure-13.7.jpg)

**Figure 13.7:** After `printf` function

**Line 47-55**

```
; Line 12
xor eax, eax
; Line 13
mov esp, ebp
pop ebp
ret 0
_main ENDP
_TEXT ENDS
END
```
