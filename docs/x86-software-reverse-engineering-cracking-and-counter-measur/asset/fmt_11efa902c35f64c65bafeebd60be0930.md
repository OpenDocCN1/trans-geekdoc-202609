
At this point, everything will be in assembly except those placeholders. If you had no external functions, your code would be ready to run, but since it does, you need a linker's help. The final step is to link your assembly code to the C function. If you're using `gcc` and calling functions from the C library, `gcc` can handle this automatically. For example, `gcc example.o -o example` will use the linker to fill out any addresses that it knows, transforming `call 0x????????` to `call 0x08048320`.

For example, consider the following example, which runs`printf hello world 42`:

```
extern printf
global main
 
section .text
main:
 
push 42
push world
push hello
call printf
add esp, 12
 
mov eax, 1
mov ebx, 0
int 0x80
 
section .data
hello: db "hello %s %d", 0xa, 0
world: db "world"
```

This assembly code can be assembled using `nasm –f elf example.asm` and linked with `gcc –m32 example.o –o example`.

It can be very helpful and powerful to be able to call simple things like `printf` from your assembly code while you're testing your crack/patch ideas.

### Using x86 Functions in C Code

It's also possible to call assembly functions from C code. The C program must have a prototype for the x86 functions that it wants to use. For example, in C, to use the assembly function *`f`*, you need the prototype `int f(void);`. A prototype is a fancy way of saying that you need to declare how that function definition would look if it was in a higher-level language (what's its name, what arguments does it take, and what does it return).

To use x86 functions in your C code, they need to be *exported* from your assembly code so that the linker can find them. To export an x86 function in your assembly file, label it with the `global` directive, as shown in the following example:

```
global f
f:
  mov eax, 0xdabbad00
  ret
```

Then, assemble your assembly code with `nasm` and compile and link the complete program with `gcc`.

For example, consider the following C program:

```
// x.c
 
#include <stdio.h>
 
int add(int,int);
 
int main(void) 
{
    int x=add(1,2);
    printf("%d\n",x);
    return 0;
}
```

This program uses the add function, which is defined in the following assembly code:

```
; y.asm
 
add:
  push ebp
  mov ebp, esp
 
  mov eax, [ebp+8]
  add eax, [ebp+12]
 
  leave
  ret
```

To link and assemble this program, run the following commands:

```
nasm –f elf y.asm # produces y.o object
gcc –m32 –c x.c # produces x.o object
gcc x.o y.o –o adder # produces executable adder
# run with ./adder
```

### _start vs. main()

x86 assembly programs commonly begin with a label named `_start`. C programs, on the other hand, start with a `main()` function. What's the difference?

Execution of a program (whether written in C, assembly, or any other language) doesn't really start at `main`. For example, consider the simplest possible C function, as shown here:

```
int main() 
{
return 0;
}
```

Compiling this with `gcc simple.c –o simple` translates your program to assembly. As part of this process, the compiler adds a function called `_start`, and `_start` calls `main`.

The resulting compiled `main` function has the following assembly:

```
80483b4:     55                   push   ebp
 80483b5:    89 e5                mov    ebp,esp
 80483b7:    5d                   pop    ebp
 80483b8:    c3                   ret
```

The start function looks like this:

```
8048300:     31 ed                xor    ebp,ebp
 8048302:    5e                   pop    esi
 8048303:    89 e1                mov    ecx,esp
 8048305:    83 e4 f0             and    esp,0xfffffff0
 8048308:    50                   push   eax
 8048309:    54                   push   esp
 804830a:    52                   push   edx
 804830b:    68 30 84 04 08       push   0x8048430
 8048310:    68 c0 83 04 08       push   0x80483c0
 8048315:    51                   push   ecx
 8048316:    56                   push   esi
 8048317:    68 b4 83 04 08       push   0x80483b4
 804831c:    e8 cf ff ff ff       call   80482f0 <__libc_start_main@plt>
 8048321:    f4                   hlt
```

The start function is responsible for a few different tasks, including the following:

*   Initializing the frame pointer

*   Configuring the stack

*   Setting up the standard arguments (parameters to `main()`)

*   Calling `libc_start_main`, which performs security checks, threading subsystem, `init`, calls your `main` function, and finally calls `exit()`

When writing pure assembly code, you write everything yourself. You don't need all of the setup C does and can write your own `_start` function.

When combining assembly and C, you need `gcc` to step in. Often, `gcc` wants to provide its own `_start` function and expects you to provide a `main()` function.

When writing an assembly program that will be linked against the standard C library, do the following:

1.  Use `main` instead of `_start (libc_start_main` will call `main()` for you).

2.  Set up a stack frame only, not the entire stack `(_start` has already configured your stack).

3.  Finish with `ret`, not `int 0x80` (`ret` will return to `libc_start_main`, which will call the C `exit` function, which will call `int 0x80` for you).

4.  Set the return value in *`eax`* before `ret`'ing (usually 0).

For example, consider the following stand-alone assembly program, which defines its own `_start`:

```
global _start
 
section .text
_start:
    mov  esp, stack
    mov  ebp, esp
 
    …
 
    mov  esp, ebp
 
    mov  eax, 1
    mov  ebx, 0
    int  0x80
    
section .data
times 128 db 0
stack equ $-4
```

When linking to `libc`, the program should use `main` instead.

```
global main
 
section .text
main:
    push ebp
    mov  ebp, esp
 
    …
 
    mov  eax, 0
    leave
    ret
```

### Standard Arguments

In C, arguments can be read from the command link with *`stdargs`*. For example, `main()` is commonly defined as `int main(int argc, char **argv)`, which provides access to these command-line arguments. Recall that *`argc`* is the number of arguments passed in, and *`argv`* is an array that holds those arguments.

It's also possible to access command-line arguments when writing a `main` function in assembly. Your assembly version of `main` will be automatically called with `cdecl`. Recall that the following:

*   Arguments are passed on the stack, pushed on from right to left.

*   Arguments are at `[ebp+8]`, `[ebp+12]`, etc.

*   *`argc`* will be the last argument and is at the top of the list of arguments on the stack, at `[ebp+8]`.

*   *`argv`* is the first argument pushed to the stack and will be at `[ebp+12]`.

For example, the following assembly program will print the first command-line argument:

```
extern printf
global main
 
main:
   push  ebp 
   mov   ebp, esp 
 
   mov   eax, [ebp+12]  ; load argv into eax
   push  dword [eax+4]  ; push argv[1]
   call  printf         ; print argv[1]
   add   esp, 4         ; clean up stack
   mov   eax, 0
   leave
   ret
```
