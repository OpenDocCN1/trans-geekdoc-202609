
In the following sections, we will talk about some protection techniques and ask the question of if they are a strong protection. The assessments are meant to, at a very high level, bucket which areas each protection has the strongest impact. The focus of our book is predominately offensive, but we felt it important to take a quick look at some of the defenses. In each section, to evaluate the effectiveness of an anti-cracking defense, we will use something called the CIA triad (CIA stands for confidentiality, integrity, and availability). For those not familiar with this, it's a common way to think about security controls, as not all security controls cover all three parts of the triad, so it's important to know which is useful in each pillar. *Integrity* is the authenticity of something. Is it as it was originally intended, or has it been modified? *Confidentiality* is the ability of something to be accessible to only authorized parties. *Availability* is the level to which something is available to perform its intended function. These three together are commonly known as the CIA triad. Evaluating packers against the CIA triad:

*   **Confidentiality:** Yes, aside from the unpacking portion of the code, the rest of it is in nonreadable format.

*   **Integrity:** Yes, modifications to the binary would cause corruption of the packed sections, causing likely application failure.

*   **Availability:** Packers can have a negative effect on performance, which can affect availability. However, if configured carefully, this effect can be minimized.

### Defeating Packing

So, how can packers be defeated? Debug the program and watch for the program to decrypt in memory. Once it is unpacked in memory, you can analyze it, but any patching done will be viable only on the unpacked binary. Patching can't be saved back to the packed binary.

One natural thought that occurs to people is once it's unpacked in memory, can't I just memory dump that out to a new unpacked binary? This is technically possible but difficult to do. Applications include a lot of startup code, and getting it loading in the right spot in memory, setting up the stack, etc., doesn't naturally come from dumping memory and just calling it an EXE.

Another option is to see if you can unpack the program. Some of the common packers out there have unpacking tools that can be used to reverse the protections put in place; some examples include UPX, MEW, and ASPack.

However, there may be no stand-alone unpacker, and the unpacking code exists only in the packed executable. However, that doesn't mean we're stuck! There are a number of great plugins and tools built specifically for this purpose, such as OllyDumpEx and ImpRec, which aim to reconstruct the import table. This is a complex but doable process, but not the focus of our book. However, if this is of interest, there are some great blogs to be found online on import reconstruction.

### PEiD

Often when approaching a file, it can be difficult to figure out what types of manipulations were done to it. If you somehow know out of the gate it was packed with a certain tool, then it's easy to start down that path. But cracking doesn't typically come with a handy playbook telling you what defenses are in place. PEiD is a tool to detect most common packers, cryptors, and compilers for portable execution files (e.g., applications). It can detect the signatures of more than 470 different obfuscation tools. Another more recent tool in this space is Detect it Easy.

As we've mentioned, many defensive tools such as packers and cryptors have unpackers and decryptors as well. Identifying the one used can reduce analysis time by an order of magnitude by allowing you to strip away many of an application's protections.

[Figure 13.2](#c13.xhtml#c13-fig-0002) shows an example of using PEiD. To start, select the file to check. PEiD will then show the details of its packing, crypting, and compiling.

![Figure 13.2: Identifying packers with PEiD](images/c13f002.png)

[**Figure 13.2**](#c13.xhtml#R_c13-fig-0002): Identifying packers with PEiD

## Lab: Detecting and Unpacking

This lab explores how to detect and defeat the use of a common packer. Labs and all associated instructions can be found in their corresponding folder here:

`https://github.com/DazzleCatDuo/X86-SOFTWARE-REVERSE-ENGINEERING-CRACKING-AND-COUNTER-MEASURES`

For this lab, please locate Lab Detecting and Unpacking and follow the provided instructions.

### Skills

Packers are a common protection against reversing. This lab explores the use of IDA, Cheat Engine, and PEiD to test the following skills:

*   Detecting the presence of packers

*   Unpacking programs with existing tools

*   Unpacking programs with advanced debugging

### Takeaways

Off-the-shelf unpackers are available for many packers (don't reinvent the wheel). When unpackers are not available, the unpacked, original program can still be manually recovered from memory.

## Virtualization

Virtualization provides a form of obfuscation and packing. It translates a program into a custom machine language and generates a virtual environment/machine (VM) to interpret it. The VM is embedded into the application and runs when the application is executed. Note that in this case we're not talking about typical large virtual machines such as Windows or Linux running in a hypervisor. Virtualization in this case can quite simply mean a layer of abstraction/interpretation being added between the host (x86) and the code.

For example, consider the following simple “hello world” program:

```
#include <stdio.h>
int main(void)
{
       printf(“hello, world!\n”); 
       return 0; 
}
```

This program could then be compiled to an arbitrary machine language. For example, this is what it looks like in Brain$#@!:

```
++++++++[>++++[>++>+++>+++>+<<<<-]>+>+>->>+[<]<-]>>.>---
      .+++++++..+++.>>.<-.<.+++.------.--------.>>+.>++.#
```

The application is then packaged with an interpreter written in the target architecture (i.e., x86).

```
#include <stdio.h>
 
char data[30000];
char program[30000];
int ip=0; /* instruction pointer */
int dp=0; /* data pointer */
 
char read_byte(void) { return getchar(); }
void write_byte(char b) { putchar(b); }
 
int main(void) {
  int i=0; char b;
 
  do {
    b=read_byte();
    program[i]=b;
    i++;
  } while (b!='#');
  while (1) {
    b=program[ip];
    if (b==0) {
      break;
    } else if (b=='>') {
      dp++;
    } else if (b=='<') {
      dp--;
    } else if (b=='+') {
      data[dp]++;
    } else if (b=='-') {
      data[dp]--;
    } else if (b=='.') {
      write_byte(data[dp]);
    } else if (b==',') {
      data[dp]=read_byte();
    } else if (b=='[') {
      if (!data[dp]) {
        int c=1;
        do {
          ip++;
          if (program[ip]=='[‘) { c++; }
          else if (program[ip]==']‘) { c--; }
        } while (c);
      }
    } else if (b==']') {
      if (data[dp]) {
        int c=1;
        do {
          ip--;
          if (program[ip]=='[‘) { c--; }
          else if (program[ip]==']‘) { c++; }
        } while (c);
      }
    } else {
      /* do nothing */
    }
    ip++;
  }
  return 0;
}
```

This adds a layer of abstraction that a cracker or reverse engineer must get through. First, reverse engineer the intermediate VM language. For those familiar with the programming language Java, Java runs inside of a VM, called the Java virtual machine (JVM). While that was done for portability, not security, it does add a layer of complexity. There are other languages that run inside of a VM, but you can also create your own (as with the example).

### How Code Virtualization Works

Unlike in the simplistic example, a good virtualizer will create a unique, arbitrary machine language on the fly, as opposed to using a static or known language. This makes it more difficult to develop devirtualization tools.
