
For example, if you `#include <stdio.h>`, that library gets dynamically linked when your program loads. When you call `printf` or `fopen`, that is calling into the standard C library. This construct holds true for all programming languages, which all include a notion of including external libraries.

#### `strace`

`strace` (system trace) is a Linux command-line utility that traces system calls. The syntax of the command is `strace <`*`command`*`>`.

System calls are calls by your application into the operating system, which manages things like files and your console window. Functions like `fopen` and `printf` eventually, in their inner workings, must make calls into the operating system. Just like with `ltrace`, this holds true for all programming languages; it's rare for an application to exist that doesn't utilize OS-level functionality.

#### `strace` Example: `echo`

Monitoring system calls provides a crude way to trace through a program. Suppose you wrote the `echo` utility and wanted to watch how it was running.

`echo` is a Linux command that echoes the input to the output. For example, the command `echo hello!` prints `"hello!"` to the terminal.

But what is it actually doing? Running `strace echo hello!` will produce output similar to [Figure 9.3](#c09.xhtml#c09-fig-0003).

![Figure 9.3: strace output for echo hello!](images/c09f003.png)

[**Figure 9.3**](#c09.xhtml#R_c09-fig-0003): `strace output` for `echo hello!`

This image is complex and can be a lot to decipher. Looking through the result, you can see some standard system calls at the beginning that are used to get the `echo` program up and running.

The following lines are the interesting output, which are found at the very end:

```
```
write(1, "hello!\n", 7hello!
)                 = 7
close(1)          = 0
```

This says that `echo` wrote a string to stream 1, which, remember, is *`stdout`*. The `write` command had a return value of 7 because seven characters were written. Finally, `echo` closed stream 1, which returned 0 for success. While this seems simple, imagine using this to track where an application wrote a piece of configuration data. Say you change a setting and want to see how it stores that on the system.

#### `strace` Example: Malicious Kittens

Comet Cursor was an early example of spyware on the Windows OS. It allowed users to change the appearance of the mouse cursor and websites to use customized cursors. The application installed itself without user permission and secretly tracked users.

As shown in [Figure 9.4](#c09.xhtml#c09-fig-0004), numerous kitten cursor applications exist in the wild. This example uses an example cursor application that secretly calls out to a Russian IP address.

Running the code shows no signs of the malicious functionality, as shown here:

```
deltaop@deltaleph-ubuntu:~$ ./kittens 
Registering kitten cursor!
Done!  Enjoy the kitties!
deltaop@deltaleph-ubuntu:~$ 
```

![Figure 9.4: Kitten cursor applications](images/c09f004.png)

[**Figure 9.4**](#c09.xhtml#R_c09-fig-0004): Kitten cursor applications

However, analyzing the code in `strace` tells a different story, as shown here:

```
deltaop@deltaleph-ubuntu:~$ strace ./kittens
...
poll([{fd=3, events=POLLOUT}], 1, 0)    = 1 ([{fd=3, revents=POLLOUT}])
send(3, "!$\1\0\0\1\0\0\0\0\0\0\7kremlin\2ru\0\0\34\0\1", 
      28, MSG_NOSIGNAL) = 28
poll([{fd=3, events=POLLIN}], 1, 5000)  = 1 ([{fd=3, revents=POLLIN}])
ioctl(3, FIONREAD, [28])                = 0 
recvfrom(3, "!$\201\200\0\1\0\0\0\0\0\0\7kremlin\2ru\0\0\34\0\1", 1024,
       0, {sa_family=AF_INET, sin_port=htons(53),sin_addr=inet_
          addr("192.168.1.1")}, [16]) = 28
close(3)                                = 0 
socket(PF_INET, SOCK_DGRAM|SOCK_NONBLOCK, IPPROTO_IP) = 3 
connect(3, {sa_family=AF_INET, sin_port=htons(53),
       sin_addr=inet_addr("192.168.1.1")}, 16) = 0 
...
```

This sample output from `strace` shows multiple events. To focus on events of interest, use `grep` (which limits results to lines that match your search string, in this case `connect`).

```
deltaop@deltaleph-ubuntu:~$ strace -f ./kittens 2>&1 | grep connect
 
connect(3, {sa_family=AF_FILE, path="/var/run/nscd/socket"},
       110) = -1 ENOENT
connect(3, {sa_family=AF_FILE, path="/var/run/nscd/socket"},
       110) = -1 ENOENT
connect(3, {sa_family=AF_INET, sin_port=htons(53),
       sin_addr=inet_addr("192.168.1.1")}, 16) = 0
connect(3, {sa_family=AF_INET, sin_port=htons(53),
       sin_addr=inet_addr("192.168.1.1")}, 16) = 0
connect(3, {sa_family=AF_INET, sin_port=htons(53),
       sin_addr=inet_addr("192.168.1.1")}, 16) = 0
connect(3, {sa_family=AF_INET, sin_port=htons(80),
       sin_addr=inet_addr("195.208.24.91")}, 16) = 0
write(2, "connected.\n", 11) = 11
```

The previous sample output looks for events with the word *connect* in them. This includes multiple Internet connections, including one to 195.208.24.91, which is suspicious as it's an external IP address, and why would your cursor need to do that?

### `strings`

`strings` is a Linux utility designed to extract the printable strings used by an application. It looks for a series of ASCII printable characters with a (configurable) minimum length and prints any that it finds.

`strings` can be very useful in reverse engineering because it provides a high-level understanding of the sorts of things that a program might do. Also, once you find strings of interest, you'll see later how you can use those strings to easily locate the associated piece of code. For example, a string that says `"incorrect password"` can be used to quickly trace where the password handling code is. For example, the following strings provide valuable hints about an application:

*   `"Enter password:"`

*   `"open_socket"`

*   `"YOUR FILES HAVE BEEN ENCRYPTED!"`

The syntax of the command is `strings program`. While it is commonly used with no options, the following flags are sometimes useful when reverse engineering:

*   **`-a`**: Show all strings in the file, as opposed to only those in the loaded sections of object files. This is often useful when dealing with obfuscated, nested, or otherwise unusual binaries.

*   `-n`: Specify the minimum length of successive printable characters for a sequence of bytes to be considered a string. The default is 4. It is often useful to expand or limit the number of strings found by the tool.

### Dependency Walker

Dependency walking is a technique used to quickly understand the imports and exports of an application. Dependency Walker is one example of such a tool. (See the “Tools” section of our repository for links.)

Dependency walking provides a valuable, high-level view into what actions a program will perform and is often a useful first step in cracking. Most applications don't implement all their own functions; they will use functions from the operating system, or external libraries. Each time an application reaches outside of its code, that will show up as an imported function. Also, often applications will share functionality with other applications, and anytime a function is something “available to be shared,” it will show up as an export of the application.

Loading a program into a program like Dependency Walker shows the DLLs that it uses and the API calls it is expected to make. [Figure 9.5](#c09.xhtml#c09-fig-0005) shows that the program will create several registry keys.

![Figure 9.5: Examining registry modifications in Dependency Walker](images/c09f005.png)

[**Figure 9.5**](#c09.xhtml#R_c09-fig-0005): Examining registry modifications in Dependency Walker

## Reverse Engineering Strategy

Reverse engineering is still more of an art than a science. While great tools and techniques are available to help, effective reversing ultimately relies heavily on intuition and experience.
