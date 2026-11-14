![](bbox=[0.12, 0.085, 0.88, 0.235])

![](bbox=[0.14, 0.265, 0.25, 0.34])

NOTE  Various good plug-ins are available for OllyDbg and Immunity Debugger that can do this search for you. You can also manually search by pressing CTRL-S in the dissassembler pane and putting in the exact desired instructions.

Now, using the address we discovered, let's craft the exploit in a program, which we will call sploit.c. This program creates the attack buffer and writes it to a file so it can be fed to the vulnerable program. This code is based on the Sysdream.com team code but was heavily modified, as mentioned in the credit comment at the beginning of the code.