
`https://docs.microsoft.com/en-us/windows/client-management/mdm/oma-dm-protocol-support`

### CSP：配置服务提供程序

对我来说，MDM 最有趣的部分是 CSP（配置服务提供程序）。这些是 Windows 10 MDM 实现中内置的微型接收器。它们接受 OMA-DM 指令（XML 格式），进行处理，然后……bingo，客户端上就会发生相应操作。

在组策略领域，我们使用 CSE（客户端扩展）。如果你还记得，组策略有 39 个“开箱即用”的 CSE。比如你熟知的管理模板、文件夹重定向、组策略首选项打印机等。组策略 CSE 仅在真正的 Windows 版本上可用，即便如此，也不是所有 CSE 都在所有真正的 Windows 版本上可用。例如，组策略首选项 CSE（共 21 个）在 Windows 家庭版上不可用。

现在在 MDM 领域，我们使用 CSP。关键在于：CSP 不仅存在于真正的 Windows（如专业版和企业版）中，也存在于这些新型 Windows 类型中，如 Windows Mobile、Windows IoT 以及未来的版本。

它们也存在于非 Windows 设备上。如 iOS、Android、Mac、Chromebook 等。

这意味着你需要随时关注 Microsoft 发布的新 CSP，但实际上，你只需关注桌面版本的即可。请记住，每次 Windows 10 发布，现有 CSP 可能会新增设置，甚至会出现全新的 CSP。

三个 CSP 示例及其适用的 Windows 10 版本矩阵可见 [表 1.1](#c01.xhtml#table1-1)。

**表 1.1 示例 CSP 及其适用的 Windows 版本**

| | 家庭版 | 专业版 | 商业版 | 企业版 | 教育版 | 移动版 | 移动企业版 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| AppLocker CSP | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| Firewall CSP | ✗ | ✓ | ✓ | ✓ | ✓ | ✗ | ✗ |
| Policy CSP | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |

所有详细信息均在 Microsoft 的配置服务提供程序参考中，地址：

`https://docs.microsoft.com/en-us/windows/client-management/mdm/configuration-service-provider-reference`

在你冲向使用 MDM 服务的道路上，有一个 CSP 你必须非常非常熟悉。

它叫 `PolicyCSP`，有两大能力。一方面，它可以间接驱动设置；另一方面，它可以执行所谓的 ADMX-backed policies（ADMX 支持的策略）。顾名思义，ADMX-backed policies 关联回真正的组策略设置。

我目前还不准备详细讲解 `PolicyCSP`——得等你选定 MDM 服务，并了解如何与其交互后再说。所以请保持关注，这个话题将在 [第 3 章](#c03.xhtml) 再次详细讨论。

![image](images/tip.jpg) 关于 IT 专业人员的 CSP 详细信息，请阅读：

`https://docs.microsoft.com/en-us/windows/configuration/provisioning-packages/how-it-pros-can-use-configuration-service-providers`

#### WMI-to-CSP Bridge（WMI 到 CSP 桥接器）

Windows 10 有一个小妙招，用于在机器没有 MDM 服务可通信时使用。它叫 `WMI-to-CSP Bridge`。

这是一种通过脚本、C# 和/或 WMI 传递某些 CSP 命令的方式。你可以使用任何你喜欢的方式传递这些命令。你可以编写登录脚本，通过 SCCM 传递命令，或用某个自定义程序来完成。

关键是，如果你查看 CSP 列表，会发现有很多 MDM 设置可以通过脚本或编程方式进行探测和管理……而完全不需要订阅任何 MDM 服务。

好吧，确实，你得自己动手，用脚本或某种编程方式。总之，它就在系统里，想用就用。这里有两个资源值得查看：

MDM Bridge WMI Provider 文档：

`https://docs.microsoft.com/en-us/windows/desktop/DMWmiBridgeProv/mdm-bridge-wmi-provider-portal`

配合 WMI Bridge Provider 使用 PowerShell 脚本：

`https://docs.microsoft.com/en-us/windows/client-management/mdm/using-powershell-scripting-with-the-wmi-bridge-provider`

### MDM 服务

选择作为服务的 MDM 系统将在下一章讨论；但这里有个大秘密。这个秘密太大了，保护得太严实了，我简直不敢相信它居然保密了这么久。

准备好听秘密了吗？

秘密是：**没有任何单一的 MDM 系统能从根本上比其他 MDM 系统更好地管理 Windows。**

我是不是刚炸裂了你的大脑？

“你为什么这么说？”我听到你在哭喊！因为归根结底，所有 MDM 服务都受限于使用 Microsoft 在 MDM 平台上为 Windows 10 提供的 CSP，且截至目前，编写自定义 CSP 是不被允许的。

所以所有 MDM 提供商必须按下相同的按钮，远程使用 `OMA-DM` 协议，拨动 CSP 的比特位来完成相同的工作。仅此而已。

不过这里有个有趣的警告：不同的 MDM 厂商可能会在其 UI 中以不同方式暴露并“美化”可用的 CSP 设置。我们将在 [第 3 章](#c03.xhtml) 看到更多相关内容。但简短的说法是：有些厂商在将可用的 CSP 设置以漂亮的可点击 MDM UI 形式呈现方面做得比其他厂商好。

我听这被称为“First Class”（一等）设置。所以如果你的 MDM 提供商没有将某个特定设置作为“First Class”可点击设置提供，你总是可以手动探测并设置该设置。我听这被称为“Third Class”（三等）设置。同样，我们将在 [第 3 章](#c03.xhtml) 看到这一点。

稍微眯眯眼，你可以扩展 MDM 服务，使其超出原本预期的功能。事实上，MDM 服务有一些附加产品。请看下一节了解如何实现。

但从根本上说，“任何 MDM 都行。”

因为它们都在按相同的按钮、拉相同的开关，因为它们最终都在戳 Windows 10 内置 CSP 的设置。

### 使用第三方工具扩展你的 MDM 服务

尽管所有 MDM 服务都受限于使用相同的 CSP，但 MDM 服务（或任何人）仍有可能通过其他方式扩展 Windows 管理，并利用 MDM 作为传输手段。

例如，MobileIron 有一个付费附加产品叫 `MobileIron Bridge`，这是一种部署 PowerShell 脚本的花哨方式。它只是利用 MDM 内置的 CSP 部署 MSI 文件，然后在机器上放置一个 PowerShell 脚本，并用一个小“运行程序”来执行这些脚本。

Intune 本身也是由某种“内置”第三方工具组成的。它叫 `Intune Management Extension`。目前，它增加了客户一直要求的两项功能：运行 PowerShell 脚本和安装 Win32 应用（.EXE 和多文件 .MSI 应用）。它通过在 Windows 10 注册入 Intune 后向 Windows 安装一个服务来实现。也许 `Intune Management Extension` 未来会增长更多功能，但截至目前，它就做这些。你可以在以下链接了解更多关于运行 PowerShell 脚本的信息：

`https://docs.microsoft.com/en-us/intune/intune-management-extension`

你可以在以下链接了解更多关于 Win32 应用管理的信息：

`https://docs.microsoft.com/en-us/intune/apps-win32-app-management`

另一个 MDM 扩展的例子是我们用 `PolicyPak MDM` 的方式。为 200% 明确起见，`PolicyPak MDM` *不是* 像 Microsoft Intune 或 Workspace ONE 那样的独立 MDM 服务。相反，`PolicyPak MDM` 的目标是添加到你现有的 MDM 服务（无论你选了哪个）之上，并用它“做更多”事情。
