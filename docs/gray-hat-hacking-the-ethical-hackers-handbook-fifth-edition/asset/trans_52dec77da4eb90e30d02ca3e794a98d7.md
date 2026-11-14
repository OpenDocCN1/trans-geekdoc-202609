

![](img/5f597c6a70133069118d9e804ace3775_564_0.png)

## 图 20-4 识别 SPI DLL

## 步骤 3: WFSRegister

现在是时候通过 WFSRegister API 配置要从服务提供程序接收的消息了。在以下代码中，我们看到正在配置来自 SYSTEM、USER、SERVICE 和 EXECUTE 的事件：

```
if(m_hSyncService) {
    WriteScript("Do", _T("SyncRegister"), _T(" "));

    HRESULT hr = m_pfnWFSRegister (m_hSyncService
        ,SYSTEM_EVENTS | USER_EVENTS | SERVICE_EVENTS | EXECUTE_EVENTS
        , m_hWnd);
}
```

## 步骤 4: WFSExecute

最后，最后一个主要步骤（我们跳过了不需要的某些步骤）是通过 SPI 实现请求外围设备（或逻辑服务）执行操作。常见操作包括要求卡阅读器读取借记卡磁道 1 和 2 上的数据，以及要求出钞机出钞！

图 20-5 展示了 Ripper³ 恶意软件的运行情况（本章后续将使用此示例恶意软件，15632224b7e5ca0cb0a042daf2adc13），调用 WFSAsyncExecute API 并在其第二个参数中接收要执行的操作（在此例中，WFS_CMD_PIN_GET_DATA，用于读取在 PIN 密码键盘上输入的信息）。

```
xor             ebx, ebx
push            408             ; WFS_CMD_PIN_GET_DATA
inc             ebx
push            ecx
mov             [ebp+var_1A], ebx
mov             [ebp+var_A], 0C000h
mov             [edx+83Ch], bl
call            ds:WFSAsyncExecute
```

图 20-5 与 PIN 密码键盘交互

我们已经了解 XFS 合规 ATM 在处理日常操作时遵循的所有细节，并讨论了 XFS 管理器在协调这项工作中的重要性。在下一节中，我们将探讨分析 ATM 恶意软件的一些技术。

## ATM 恶意软件分析

既然你了解了 XFS 合规 ATM 从端到端的工作原理，让我们来看看一些基于野外发现的真实威胁的 ATM 恶意软件解剖有用技术。

我们将快速概述 ATM 恶意软件的主要特征，让你了解野外存在哪些类型的威胁，它们如何安装在 ATM 上，恶意软件如何与攻击者交互，以及恶意软件如何窃取信息或资金！

## ATM 恶意软件类型

ATM 恶意软件分为两种类型：影响持卡人的恶意软件和影响银行的恶意软件。

## 影响持卡人的恶意软件

这种类型的恶意软件专注于从 ATM 窃取信息，例如受害者的全名、借记卡号、到期日和加密的 PIN 码。所有这些数据随后都会在黑市上出售，在那里会制作克隆卡并进行未经授权的在线支付。从恶意软件分析的角度来看，这些威胁充当信息窃取者——在分析过程中不一定需要了解 ATM。这类威胁的示例包括在拉丁美洲发现的 PanDeBono 和 NeaBolsa。⁴ 这些威胁通过插入机器的 USB 设备窃取信息，并在内部运行的恶意软件中被识别和验证。

尽管盗刷设备与物理攻击相关，因此超出本章范围，但提及它们还是有价值的，因为它们影响持卡人。这些设备以隐藏的方式物理附加到 ATM 上，以便受害者看不见它们（参见图 20-6）。这些设备可以带有摄像头，也可以伪装成 PIN 密码键盘或卡阅读器，主要用于捕获输入的 PIN 码或窃取卡数据。它们可以通过蓝牙、GSM 或其他任何无线通信将窃取的信息实时发送给攻击者。

![](img/5f597c6a70133069118d9e804ace3775_566_0.png)

图 20-6 附加在 ATM 上的盗刷设备

在墨西哥坎昆曾发生过一起已知案例，盗刷设备被安装在 ATM 内部并通过蓝牙与攻击者通信。大多数受感染的机器位于酒店和机场这一事实表明，当地黑帮得到了来自“合法”企业人员的支持。“报警最多无济于事，甚至可能很危险；墨西哥警察臭名昭著地腐败，据我所知，读卡器诈骗者可能正在付钱给警察以换取保护，”Brian Krebs 写道。⁵

## 影响银行的恶意软件

这种类型的恶意软件会清空 ATM；因此，持卡人受影响不大，但银行会受影响。这要么通过重用机器中安装的 XFS 中间件完成，要么通过创建 XFS 合规应用程序完成。这类威胁的示例包括 Ploutus、Alice、SUCEFUL、Ripper、Padpin（后来被卡巴斯基命名为 Tyupkin）以及 GreenDispenser。

## 在 ATM 上安装恶意软件的技术

本节将描述攻击者用于在 ATM 上感染恶意软件的不同技术。

### 物理攻击和虚拟攻击

对于物理攻击，攻击者打开 ATM 的上部（参见图 20-1），并通过以下技术传输恶意软件：

- 连接 USB 或 CD-ROM 并重启机器。发生这种情况后，BIOS 顺序会更改为从新连接的设备启动并开始恶意软件安装。
- 移除 ATM 的硬盘，将其作为从盘连接到攻击者的笔记本电脑，并传输恶意软件。或者，用攻击者已为目标型号准备好的硬盘替换 ATM 硬盘。

![](img/5f597c6a70133069118d9e804ace3775_567_0.png)

> 注意 Ploutus 团伙已知在拉丁美洲的 ATM 上使用这两种技术。

对于虚拟攻击，攻击者入侵银行的网络或支付网关。进入后，目标是找到 ATM 连接的网络段并定位漏洞，以便通过网络将恶意软件投放到出纳机上。这种攻击非常强大，因为它可以感染全球任何 ATM。Ripper ATM 恶意软件就是如此；攻击者通过银行网络感染了泰国的机器，然后*骡子*（负责接收机器吐出现金的人）飞往该地区，在几小时内清空了机器！

### 恶意软件与攻击者交互

一旦恶意软件在 ATM 内部安装完成，攻击者需要一种与之交互而又不被持卡人注意的方法。这意味着恶意软件界面只在接收到某种激活后才会在屏幕上弹出。

最早已知的交互案例（由 MD5 为 488acf3e6ba215edef77fd900e6eb33b 的 Ploutus 恶意软件使用）涉及连接到 ATM 的外部键盘。Ploutus 执行所谓的“键盘记录”，这使攻击者能够拦截任何按键输入，一旦找到正确的按键组合，它就会激活允许攻击者按需出钞的 GUI。在以下代码清单中，Ploutus 正在检查是否输入了任何 F 键以执行特定命令。例如，F4 键将隐藏 GUI 界面。

```
if (PloutusService.MemoryData.GuiEnable)
{
    if (KeyData.KeyCode == System.Windows.Forms.Keys.F1)
    PloutusService.Keyboard.ProcessCommandGui(1);
    if (KeyData.KeyCode == System.Windows.Forms.Keys.F2)
    PloutusService.Keyboard.ProcessCommandGui(2);
    if (KeyData.KeyCode == System.Windows.Forms.Keys.F3)
    PloutusService.Keyboard.ProcessCommandGui(3);
    if (KeyData.KeyCode == System.Windows.Forms.Keys.F4)
    {
    PloutusService.Program.NCRV.UIDisable();
    PloutusService.Program.NCRV.ClearText();
    PloutusService.MemoryData.Command = System.String.Empty;
    }
    if (KeyData.KeyCode == System.Windows.Forms.Keys.F5)
    PloutusService.Program.NCRV.KeyControlUp();
    if (KeyData.KeyCode == System.Windows.Forms.Keys.F6)
    PloutusService.Program.NCRV.KeyControlDown();
    if (KeyData.KeyCode == System.Windows.Forms.Keys.F7)
    PloutusService.Program.NCRV.KeyControlNext();
    if (KeyData.KeyCode == System.Windows.Forms.Keys.F8)
    PloutusService.Program.NCRV.KeyControlBack();
}
```

第二种交互形式是通过 PIN 密码键盘，攻击者输入一组数字以调出恶意软件界面。为了实现这一点，恶意软件需要使用 XFS API，如图 20-5 所示，其中命令 PIN_GET_DATA 正在读取输入的信息。

最后一种交互形式是通过 ATM 的卡阅读器。与 PIN 密码键盘策略类似，恶意软件使用 XFS API，但这次是为了与目标设备交互并读取借记卡磁道 1 和 2 上的数据。如果提供了攻击者期望的魔数，GUI 将被激活。在 Ripper 等情况下，这就是开始清空 ATM 的触发点。

## 信息或资金如何被窃取

在目标是持卡人数据的情况下，如果使用盗刷设备，这些设备已经带有 GSM 等无线协议，允许攻击者实时接收窃取的信息。当使用恶意软件实现此目标时，例如 PanDeBono 或 NeaBolsa 恶意软件的情况，窃取的信息会被复制到插入 ATM 的攻击者的 USB 中。

关于现金，所有威胁都只需使用 XFS API 即可与 ATM 出钞机交互（无需漏洞利用或身份验证绕过），且没有任何限制，出钞机就会开始提供现金。有关如何缓解这些风险的建议，请参阅本章后面的“ATM 恶意软件对策”部分。

