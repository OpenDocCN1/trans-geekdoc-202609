
## 将安全基线分配给组

执行此操作后，你会看到组内所有计算机出现，其“分配状态”变为“挂起”，如图 10.6 所示。

![Figure 10.6 See the computers lined up to get the baseline.](img/c10f006.jpg)

**图 10.6** 查看排队等待获取基线的计算机。

此时你可以等待，或强制刷新。

### 同步客户端以获取基线

强制刷新的最快方法是前往客户端进行同步，如你之前所见，如图 10.7 所示（同样位于“设置”应用 ➢ “访问工作或学校”）。

同步后，你应该会看到大量 CSP 设置生效，如图 10.7 所示。每个类别都在探测 CSP，基本 MDM 客户端报告会显示你探测了什么。

![Figure 10.7 After you Sync with MDM, which delivers a baseline](img/c10f007.jpg)

**图 10.7** 与 MDM 同步后，后者分发基线

现在你可以快速测试，亲自验证是否生效。

### 测试基线

许多安全基线设置难以直观查看或立即测试。但有少数可以。最简单的或许是查看是否真正为 Edge 启用了 SmartScreen，这在图 10.4 中已展示。仔细观察，图 10.4 中有一项已启用的设置名为“要求 Microsoft Edge 使用 SmartScreen”。

SmartScreen 的职责是，嗯……在用户尝试下载和/或运行内容时，智能拦截恶意内容。好，让我们看看实际效果。

使用 Edge 尝试浏览并下载以下（安全但伪装成恶意的）文件：`https://secure.eicar.org/eicar.com.txt`。

![image](img/tip.jpg) 如果你没听说过 EICAR 标准，其大意是：这些是已知安全但伪装成恶意的文件，安全和防病毒程序会识别它们。这样你就能用测试文件触发测试，而无需使用真实病毒或恶意软件。在 `https://en.wikipedia.org/wiki/EICAR_test_file` 了解更多关于 EICAR 的信息。

在图 10.8 中，可以看到 Edge 遵循 SmartScreen 设置，阻止了伪装成恶意的文件下载。

![Figure 10.8 See that Edge has been configured to honor SmartScreen via the security baselines.](img/c10f008.jpg)

**图 10.8** 可见 Edge 已通过安全基线配置为遵循 SmartScreen。

### 基线的报告与监控

目前，“安全基线”部分的报告功能仍在完善中。截至写作时，你可以在基线内查看“监视”部分，如图 10.9 所示。

![Figure 10.9 The Monitor section within a baseline](img/c10f009.jpg)

**图 10.9** 基线内的“监视”部分

我预计此监视和报告部分很快会得到改进。

但现在，你可以看到“设备状态”、“用户状态”和“按设置状态”。前两者只是告诉你基线是否已完全交付给用户组或计算机组。最后一份报告“按设置状态”会告诉你你想要应用的设置是否真的已应用。还有一列名为“冲突”。冲突列旨在告诉你设备配置文件与基线配置文件之间何时发生冲突。然后你可以调整或从其中一个配置文件中删除该设置。

接下来合乎逻辑的问题当然是：应该调整哪个配置文件？哪个配置文件应该生效？答案是你应该回去解除设备配置文件中的冲突设置，并使用基线配置文件中的设置。这是该功能发布时产品经理 Joey Glocke 直接给出的建议。但这对我来说讲得通，我基本同意。

你可以在此处的博客文章中看到该功能的公告以及 Joey Glocke 的评论：

`https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Microsoft-Intune-introduces-MDM-Security-Baselines-to-secure-the/ba-p/313442`

#### 其他资源

*   关于 Intune 配合 Windows 10 安全基线的官方文档可在此处找到：
    `https://docs.microsoft.com/en-us/intune/security-baselines`

*   关于监视、报告和故障排除的更多详细信息可在此处找到：
    `https://docs.microsoft.com/en-us/intune/security-baselines-monitor`

*   基于组策略的安全基线版本可在此处找到：
    `https://docs.microsoft.com/en-us/windows/security/threat-protection/security-compliance-toolkit-10`

*   一个包含演练并展示冲突（及如何解决）的优秀博客文章可在此处找到：
    `https://osddeployment.dk/2019/01/27/start-using-intune-security-baseline/`

#### VMware Workspace ONE 与安全基线

Microsoft Intune 并不是唯一拥有基线的 MDM 解决方案。

VMware Workspace ONE 也有基线。作为 Workspace ONE 客户，若要查看它们，请转到 `设备 ➢ 配置文件和资源 ➢ 基线`，如图所示。

![](img/c10uf001.jpg)

然后你可以使用 CIS 基准或自定义基线。

CIS 基准与此类似，但并不完全等同于 Microsoft 通过其基线所做的事情。有人甚至可能会说 CIS 基准更加硬核。

你也可以上传自己的自定义基线，但这样做有点繁琐。基本过程是使用 Microsoft `LGPO` 工具（来自安全合规工具包）从现有计算机的本地组策略存储中提取策略并将其存储为 ZIP 文件。

然后，为了应用该策略，VMware Workspace ONE 会将 ZIP 文件放到计算机上，并再次使用 `LGPO` 来“回放”策略。`LGPO` 必须位于 `%ProgramData%\Airwatch\LGPO`（如何将其放在那里由你决定）。

请注意，此 VMware Workspace ONE 功能没有任何方法来处理组策略首选项，也没有简单的方法来更新你的 ZIP 文件，除非先回到源计算机，重新提取其“大脑”，重新制作 ZIP 文件，并将其重新推送回计算机。

话虽如此，关于该过程的视频可在 `https://youtu.be/B5VzzhH0r20` 找到，从一分钟处到约六分钟处。

## BitLocker：全盘加密

BitLocker：直接启用吧。

当然，BitLocker 是全盘加密，这样如果坏人拿到了你的笔记本电脑，他们就无法看到里面的内容。笔记本电脑价值几百到几千美元；而那台笔记本电脑上的数据无价。

关于 BitLocker 有趣的是，它是通过 Intune 配置的，但真正干活的是 Azure，最终的密钥也存储在 Azure 中。

有几种方法可以强制启用 BitLocker。

### 使用 Intune 启用 BitLocker

在使用 Intune 时，有多种方法可以启用 BitLocker。实际上，是 Intune 执行“启用”操作，但真正的强制执行是通过 Azure 进行的（BitLocker 密钥也是如此）。稍后详述。

你可以通过以下多种方式启用 BitLocker：

*   Intune 的设备配置文件
*   配合 Autopilot
*   PowerShell 和部署脚本

让我们逐一探讨这些选项。

但在此之前，我们需要谈谈设备所有者的概念。设备所有者是将设备首次注册到 Azure（随后自动注册到 MDM）的人。也许在机器已运行 Windows 后（稍后注册），注册设备的人是你的全局管理员 Frank Rizzo。也许那个人是 Jack Tors，他在使用 Autopilot 的 OOBE 页面时注册了机器。

在 `Azure ➢ 设备` 中，你可以看到每台机器的所有者，如图 10.10 所示。

![图 10.10 使用 Azure AD 查看设备所有者](img/c10f010.jpg)

**图 10.10** 使用 Azure AD 查看设备所有者

设备所有者的概念——即在 Azure 和 MDM 中首次注册设备的人——将是一个关键点。所以请在继续阅读时将其记在脑后。

#### 通过 Intune 设备配置配置文件启用 BitLocker

这是启用 BitLocker 的一种方法。请注意，这些步骤需要 Windows 1809 或更高版本才能按预期工作。

首先转到 `Intune ➢ “设备配置” ➢ 配置文件`。然后创建一个类型为“终结点保护”的新配置文件，如图 10.11 所示。然后点击进入 Windows 加密策略。

![图 10.11 如何为设备启用 BitLocker](img/c10f011.jpg)

**图 10.11** 如何为设备启用 BitLocker

然后，里面有大量设置。唯一严格要求使其工作的设置见图 10.12——即将“加密设备”设置为“必需”。但如果这是你选择的唯一设置，则 BitLocker 只有在本地管理员登录时才会激活并开始加密，而标准用户则不行。为了调整这一点，请将“其他磁盘加密的警告”设为“阻止”，这将使你能够将“允许标准用户在 Azure AD 加入期间启用加密”设为“允许”。该策略名称本身有点误导性，因为（我测试过）它在机器已加入 Azure AD 后生效，并不一定是在 Azure AD 加入“期间”或“加入那一刻”，正如名称暗示的那样。也许更好的名称应该是“允许标准用户在机器已加入 Azure AD 时启用加密”。

我也是以下两个设置的粉丝：“将 BitLocker 恢复信息保存到 Azure Active Directory”和“在启用 BitLocker 前将恢复信息存储在 Azure Active Directory 中”（均见图 10.13）。就我而言，我喜欢密钥被托管（或代表计算机保存）的想法。我也喜欢加密甚至不会开始，直到我知道密钥已在云端某处的想法。（稍后详述。）但我也能理解不强制执行此操作的逻辑，代价只是确保“野外”所有机器都已加密，即使将恢复密钥存储在 Azure AD 中存在一些问题。

另一个非常好的主意是阻止“未受 BitLocker 保护的固定数据驱动器的写入访问权限”（未显示）。

完成所有设置并保存后，你可以将其分配给一个组。在我的示例中，我创建了一个包含单台测试机器的组，但如果你的实验室足够小，你也可以尝试将配置文件分配给“所有设备”（实际生产环境中不推荐，但这里应该没问题）。

![图 10.12 为主驱动器启用 BitLocker 加密并允许标准用户加密驱动器](img/c10f012.jpg)

**图 10.12** 为主驱动器启用 BitLocker 加密并允许标准用户加密驱动器

![Figure 10.13 Forcing BitLocker encryption for removable drives and storing the recovery information to Azure AD](img/c10f013.jpg)

**图 10.13** 强制对可移动驱动器进行 BitLocker 加密并将恢复信息存储到 Azure AD

然后，正如你所料，与 Intune 同步。

接下来会发生什么？

嗯，这取决于你*是谁*。更具体地说，当你收到策略时，你是以何种身份登录的——标准用户还是本地管理员。

如果你在收到策略时是标准用户，*似乎完全没有任何反应*。但实际上，在底层，BitLocker 加密已启动并正在执行其任务，如图 10.14 所示。

![Figure 10.14 No indication BitLocker has started for a Standard User, but the drive begins encryption](img/c10f014.jpg)

**图 10.14** 标准用户无任何 BitLocker 已启动的迹象，但驱动器开始加密

如果你在收到策略时是管理员，你会收到一个简单的弹出通知，提示 BitLocker 加密已开始（此处不展示）。

此时便进入全速运行阶段。

### 在 Autopilot 过程中启用 BitLocker

设备所有权问题是个真正的棘手难题。虽然有办法绕过它，但你必须深思熟虑，并使用 Autopilot 向最终用户部署全新机器。

如果你还记得第 2 章“Set Up Azure AD and MDM”中的内容，当我们通过开箱即用体验 (OOBE) 手动将机器注册到 MDM 时，执行注册的人会成为本地管理员，这也意味着他们成为了设备所有者。同样，也在第 2 章中，当我们通过“设置工作或学校账户”手动将机器注册到 MDM 时，该人员也会成为本地管理员，并且当时他们也成为了设备所有者。

只有当我们使用 Autopilot 时，奇迹才会发生：当机器通过 Autopilot 完成 MDM 注册后，最终用户在设备上只是一个标准用户，而……*他们*成为了设备所有者。

因此，如果可能，使用 Autopilot 进行部署在同时推出 BitLocker 时具有巨大优势。设备上的最终用户成为所有者，他们可以在自己的门户信息页面中查看自己的 BitLocker 恢复密钥（稍后将在“BitLocker 密钥恢复与管理”部分详述）。

现在，世界上有两种支持 BitLocker 的设备：

*   硬件安全测试接口 (HSTI) 和/或支持 InstantGo
*   不支持 HSTI/不支持 InstantGo

较新的硬件支持 HTSI/InstantGo；较旧的硬件和虚拟机为非 HSTI/InstantGo。

根据你的目标机器，你需要稍微不同地设置 BitLocker 设置。

请注意，如果你跟随 Autopilot 章节（第 8 章“Rollouts and Refreshes with Configuration Designer and Autopilot”）进行了操作，那么你可能拥有各种 Autopilot 部署配置文件。我建议暂时取消分配除“所有设备”配置文件以外的所有配置文件，然后再继续，这将执行基本的用户驱动体验。这样你就不会因冲突的 Autopilot 配置文件或异常、复杂的 Autopilot 场景而陷入麻烦。还请记住，如果虚拟机拥有虚拟 TPM 2.0 芯片，此方法也适用于虚拟机。

![](img/c10uf002.jpg)

#### 面向非 HTSI/非 InstantGo 设备的 BitLocker

此场景非常简单。

只需将你之前创建的 BitLocker 测试配置文件分配给 Autopilot（所有设备）组。

BitLocker 测试配置文件设置为尽快开启磁盘加密并托管密钥。

因为首次在 Autopilot 中注册机器的人将是像 Jack Tors 这样的标准用户……宾果。Jack 通过 Autopilot 登录，将机器注册到 Azure AD 和 Intune MDM，BitLocker 对机器进行加密。

Jack 成为设备所有者，一切皆大欢喜。

如果你正在使用 VMware Workstation 进行测试，并使用 vTPM 2.0 芯片而非真实硬件，这里有个小提示。对我而言，除非移除 vTPM 芯片然后重新添加，否则 Autopilot 不会启动。具体来说，我是在 Autopilot 发现机器并在重命名后重启机器的那个时间点，能够添加 vTPM 芯片。此时我关闭虚拟机并添加 vTPM 芯片。只有那时 Autopilot 才会被引导启动，识别机器，识别 vTPM，并毫无事故地继续后续过程。

同样，在拥有真实 TPM 硬件的真实环境中，你不需要做那些繁琐的操作。也许在 VMware Workstation 中对你来说也是“开箱即用”，只是我当时碰巧遇到了一些怪事。

#### 面向 HTSI/InstantGo 设备的 BitLocker

这类机器在加入 Azure AD 后会自动开始执行 BitLocker 加密。哇。

如果你想了解有关 InstantGo 以及加入 Azure AD 时自动进行 BitLocker 加密的详细信息，请查看：

`https://blogs.technet.microsoft.com/home_is_where_i_lay_my_head/2016/03/14/automatic-BitLocker-on-windows-10-during-azure-ad-join/`

但关键点如下；这很奇怪，请耐心往下看。具有讽刺意味的是，Intune 配置文件中的 Windows 加密设置需要将“加密设备”设置为“未配置”，如图 10.15 所示。

有两篇博客文章给了我这个配方：

`https://osddeployment.dk/2018/11/18/how-to-delivering-BitLocker-policy-to- Autopilot-devices-to-set-256-bit-encryption/`

`https://techcommunity.microsoft.com/t5/Microsoft-Intune/BitLocker-Encryption-Policy-for-Autopilot-Devices-Windows-10/td-p/291187`

让我基于你在本书中已完成的设置，通过一个视角来为你拆解：

*   *不要* 重复使用你之前创建的包含 BitLocker 设置的设备配置文件。相反，创建一个全新的 Windows 10 设备配置文件，并配置“终结点保护”策略设置。（博客中的 MVP 报告称，如果在使用现有配置文件时应用这些设置，将不会生效！但我没有尝试过。）

*   在“Windows 加密”设置窗格中，这很奇怪：将“加密设备”设置保留为“未配置”。这是关键步骤！请参阅图 10.15。
