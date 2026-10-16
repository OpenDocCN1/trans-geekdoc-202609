
-   [Up to this point, this book has covered the core tools and skills used for reverse engineering and cracking. However, this is an evolving field, and new methods are being developed to make it faster and easier. This section describes at a high level some advanced techniques and tools on the cutting edge of reverse engineering. Our goal with this chapter is that if at this point you're still loving software cracking and looking to take it even further to the next level, we want to present you with a plethora of rabbit holes to go down. Depending on what interests you, we hope the following will point you in the right directions to go deeper.]

### Timeless Debugging

-   [Timeless debugging is also known as reverse debugging. The core idea is: “what if we could go backwards when debugging?”]

-   [Consider the case where something went wrong while debugging. Maybe a patch failed, you missed an anti-debug check, you don't know how you got here, etc.]

-   [There are a few different tools designed for timeless debugging, including the following:]

-   [Visual Studio Ultimate (.NET)]

-   [rr]

-   [gdb]

-   [To get started, check out George Hotz @ Enigma in his 2016 USENIX Enigma talk at `www.youtube.com/watch?v=eGl6kpSajag`.]

### Binary Instrumentation

-   [Binary instrumentation is when you inject code to watch or modify a process as it executes. This can be useful for finding memory leaks, tracing key checks, performing anti-anti-debugging, etc.]

-   [Some tools for binary instrumentation include the following:]

-   [PIN]

-   [DynamoRIO]

-   [Frida]

-   [Valgrind]

-   [QBDI]

-   [For an introduction to binary instrumentation, check out the 2015 Blackhat USA talk “Augmenting Static Analysis Using Pintool: Ablation” at `www.youtube.com/watch?v=wHIlNRK_HiQ`.]

### Intermediate Representations

-   [Normally, for reversing and cracking, it's necessary to learn and write tools for each new architecture. The idea of intermediate representations is to translate all assembly code for all architectures to the same language. That way, you can learn and write tools for just that language.]

-   [There are a few different tools that can be used to work with intermediate representations, including the following:]

-   [Binary Ninja]

-   [REIL]

-   [VEX]

-   [BNIL]

-   [Ghidra PCode]

-   [IDA microcode]

-   [LLVM IR]

-   [To get started with intermediate representations, check out “Finding Bugs with Binary Ninja” by Jordan Wiens from LevelUp 0x03 at `www.youtube.com/watch?v=55gClG-sjWc`.]

### Decompiling

-   [The idea of decompiling is to recover original source code from advanced automated analysis of assembly code. Some tools that offer decompilation include the following:]

-   [IDA's Hex-Rays]

-   [Ghidra]

-   [Binary Ninja]

-   [Snowman Decompiler]

-   [To learn more about decompiling, check out “Decompiling a Virus using IDA Pro” at `www.youtube.com/watch?v=gYkDcUO9otQ`.]

### Automatic Structure Recovery

-   [Automatic structure recovery involves automatically finding patterns and links in memory to make inferences about the data types used. Some tools for this include the following:]

-   [dynStruct]

-   [Cheat Engine]

-   [To learn more about automatic structure recovery, check out the dynStruct idea and paper at `https://github.com/ampotos/dynStruct`.]

### Visualization

-   [Code listings and text can be difficult to think and reason about. Visualization can be used to deepen your understanding of file structure and execution.]

-   [Some reversing tools that offer useful visualizations include the following:]

-   [BinWalk]

-   [Hopper]

-   [IDA plugins]

-   [Veles]

-   [..cantor.dust..]

-   [Cheat Engine]

-   [A good starting point for understanding how visualization can be used for reversing includes the Derbycon talk “Dynamic Binary Visualization” from Christopher Domas at `www.youtube.com/watch?v=4bM3Gut1hIk`.]

### Deobfuscation

-   [Obfuscation is designed to slow down reversing in an attempt to get a cracker to give up. The idea is to use tools to automatically remove obfuscations from programs using tools like Tigress Protection.]

-   [Check out “Lets break modern binary code obfuscation” at `www.youtube.com/watch?v=TDnAkm6ZTYw`.]

### Theorem Provers

-   [Theorem provers use mathematics to analyze code, including reduction, deobfuscation, boundaries, inputs, etc. Some theorem proving tools for reversing include the following:]

-   [Z3]

-   [STP]

-   [Boolector]

-   [Yices]

-   [To see how theorem provers can be used, watch “Using z3 to find a password and reverse obfuscated JavaScript” at `www.youtube.com/watch?v=TpdDq56KH1I`.]

-   [Also check out the yearly SMT-COMP!, which has some really interesting benchmarks on many unique solvers at `https://smt-comp.github.io/2023`.]

### Symbolic Analysis

-   [The idea behind symbolic analysis is trying to find inputs that cause interesting results. For example, what inputs could cause a crash, pass a key check, unlock a secret, etc.]

-   [Symbolic analysis tools will trace user input through a program. At each branch, they ask a theorem prover which user input would go down the taken path. What user input would go down the not-taken path?]

-   [For example, consider the following code:]

-   [```
if (strlen(username)> 10)
       if (key_1^sum(username)==key_2)
              printf("key passed");
```]

-   [A symbolic analysis tool will automatically identify the combination of *`username`*, *`key_1`*, and *`key_2`* that will pass the checks and reach the “key passed” print statement.]

-   [Some symbolic analysis tools include the following:]

-   [Angr]

-   [Mayhem]

-   [KLEE]

-   [Triton]

-   [S2E]

-   [To see an example of symbolic analysis with Angr, check out the DEF CON 23 talk by Shoshitaishvili and Wang, “Angry Hacking: The next gen of binary analysis,” at `www.youtube.com/watch?v=oznsT-ptAbk`.]

## Summary

-   [At this point, the best way to improve your reversing and cracking skills is via more hands-on practice. On the Windows VM, the `allthethings` folder on the Desktop contains a variety of different crackmes to practice with sorted by difficulty level.]

## CHAPTER 17  

### Bonus Topics

-   [This last chapter of this book introduces software reversing and cracking. It is primarily focused on understanding how a program works and bypassing or modifying undesirable functionality (like key checkers).]

-   [This chapter takes this knowledge and applies it to real-world hacking. Stack smashing and shellcoding both use an understanding of how a program and the stack works to run malicious code within a program.]

### Stack Smashing

-   [Stack smashing, also known as stack-based buffer overflows, is one of the most classic attacks against software. It takes advantage of the fact that non-memory-safe languages such as C/C++ have no built-in protection that prevents an application from accessing or overwriting data in other parts of memory. For example, C/C++ doesn't automatically check that the data written to an array fits within the bounds of that array. If you don't know C, don't worry. As long as you know any programming language, you should be able to follow along.]

-   [Because stack smashing has been around for such a long time, there are numerous compilers that have built-in automatic guards that are put into compiled code to prevent this. While it's not as easy of an attack as it used to be, everyone should fully understand how the attack works, because:]

-   [*   Some facets of it still work.]
-   [*   It's the foundation of other types of attacks.]
-   [*   Not every application has stack protections.]

-   [For any of the following C code examples, if you build them with `gcc`, you must use the flag `-fno-stack-protector` to turn off these protections. Making the full command line for using `gcc` to build in Linux: `gcc myfile.c-fno-stack-protector`.]

-   [For example, consider the following simple C program:]

-   [```
void function(int a, int b, int c) {
   char buffer1[5];
   char buffer2[10];
}
 
void main() {
  function(1,2,3);
}
```]

-   [After this application has been compiled and the object has been dumped from memory, it results in the following assembly code:]

