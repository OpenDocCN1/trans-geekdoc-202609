memory address pointing to the top of *the stack*, for example, is commonly stored in a register – “commonly” being an understatement here. This specific usage of a register is so prevalent that most CPUs have a single, designated register just for storing this pointer, the so called *stack pointer*. The operands and the results of certain CPU instructions may also be stored in registers. If a CPU would need to add two numbers, both of them would be stored in registers and the result of the addition would end up in one too. That’s not all, though. There are many more use cases for registers. Here’s another one: if there’s a large piece of data frequently being accessed in a program it makes sense to store the address of it to a register so it can be accessed by the CPU really fast. The most important one for us, though, is the *stack pointer*. We’ll meet that one again soon.

And now… take a deep breath, lean back and relax, because: that’s it! Now that we’ve mentioned registers and know what a stack pointer is, we’ve covered everything we need to know about how real machines work. It’s time for us to go abstract, from the physical to the virtual.

# What Is a Virtual Machine?

Let me get straight to the point: a virtual machine is a computer built with software. It’s a software entity that mimics how a computer works. I’ll admit, “software entity” doesn’t say much, but I used this phrase on purpose, to drive home one point: a virtual machine can be anything. A function, a struct, an object, a module, or even a whole program. What matters is what it does.

A virtual machine has a run loop that goes through the fetch-decode-execute cycle, just like a computer. It has a program counter; it fetches instructions; it decodes and executes them. It also has a stack, just like a real computer. Sometimes it has a call stack and sometimes even registers. All built in software.

Let me put code where my mouth is. Here is a virtual machine in 50 lines of JavaScript:

```
```javascript
let virtualMachine = function(program) {
    let programCounter = 0;
    let stack = [];
    let stackPointer = 0;

    while (programCounter < program.length) {
        let currentInstruction = program[programCounter];
```
```