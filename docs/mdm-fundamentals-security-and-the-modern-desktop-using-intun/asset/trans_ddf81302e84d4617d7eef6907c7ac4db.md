

![Figure 10.13 Forcing BitLocker encryption for removable drives and storing the recovery information to Azure AD](images/c10f013.jpg)

**Figure 10.13** 强制对可移动驱动器进行 BitLocker 加密并将恢复信息存储到 Azure AD

然后，正如你所料，与 Intune 同步。

接下来会发生什么？

嗯，这取决于你*是谁*。更具体地说，当你收到策略时，你是以何种身份登录的——标准用户还是本地管理员。

如果你在收到策略时是标准用户，*似乎完全没有任何反应*。但实际上，在底层，BitLocker 加密已启动并正在执行其任务，如 **Figure 10.14** 所示。

![Figure 10.14 No indication BitLocker has started for a Standard User, but the drive begins encryption](images/c10f014.jpg)

**Figure 10.14** 标准用户无任何 BitLocker 已启动的迹象，但驱动器开始加密

如果你在收到策略时是管理员，你会收到一个简单的弹出通知，提示 BitLocker 加密已开始（此处不展示）。

此时便进入全速运行阶段。

### 在 Autopilot 过程中启用 BitLocker

设备所有权问题是个真正的棘手难题。虽然有办法绕过它，但你必须深思熟虑，并使用 Autopilot 向最终用户部署全新机器。

如果你还记得 **Chapter 2** “Set Up Azure AD and MDM” 中的内容，当我们通过开箱即用体验 (OOBE) 手动将机器注册到 MDM 时，执行注册的人会成为本地管理员，这也意味着他们成为了设备所有者。同样，也在 **Chapter 2** 中，当我们通过“设置工作或学校账户”手动将机器注册到 MDM 时，该人员也会成为本地管理员，并且当时他们也成为了设备所有者。

只有当我们使用 Autopilot 时，奇迹才会发生：当机器通过 Autopilot 完成 MDM 注册后，最终用户在设备上只是一个标准用户，而……*他们*成为了设备所有者。

因此，如果可能，使用 Autopilot 进行部署在同时推出 BitLocker 时具有巨大优势。设备上的最终用户成为所有者，他们可以在自己的门户信息页面中查看自己的 BitLocker 恢复密钥（稍后将在“BitLocker 密钥恢复与管理”部分详述）。

现在，世界上有两种支持 BitLocker 的设备：

*   硬件安全测试接口 (HSTI) 和/或支持 InstantGo
*   不支持 HSTI/不支持 InstantGo

较新的硬件支持 HTSI/InstantGo；较旧的硬件和虚拟机为非 HSTI/InstantGo。

根据你的目标机器，你需要稍微不同地设置 BitLocker 设置。

请注意，如果你跟随 Autopilot 章节（**Chapter 8** “Rollouts and Refreshes with Configuration Designer and Autopilot”）进行了操作，那么你可能拥有各种 Autopilot 部署配置文件。我建议暂时取消分鐵除“所有设备”配置文件以外的所有配置文件，然后再继续，这将执行基本的用户驱动体验。这样你就不会因冲突的 Autopilot 配置文件或异常、复杂的 Autopilot 场景而陷入麻烦。还请记住，如果虚拟机拥有虚拟 TPM 2.0 芯片，此方法也适用于虚拟机。

![](images/c10uf002.jpg)

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

但关键点如下；这很奇怪，请耐心往下看。具有讽刺意味的是，Intune 配置文件中的 Windows 加密设置需要将“加密设备”设置为“未配置”，如 **Figure 10.15** 所示。

有两篇博客文章给了我这个配方：

`https://osddeployment.dk/2018/11/18/how-to-delivering-BitLocker-policy-to- Autopilot-devices-to-set-256-bit-encryption/`

`https://techcommunity.microsoft.com/t5/Microsoft-Intune/BitLocker-Encryption-Policy-for-Autopilot-Devices-Windows-10/td-p/291187`

让我基于你在本书中已完成的设置，通过一个视角来为你拆解：

*   *不要* 重复使用你之前创建的包含 BitLocker 设置的设备配置文件。相反，创建一个全新的 Windows 10 设备配置文件，并配置“终结点保护”策略设置。（博客中的 MVP 报告称，如果在使用现有配置文件时应用这些设置，将不会生效！但我没有尝试过。）
*   在“Windows 加密”设置窗格中，这很奇怪：将“加密设备”设置保留为“未配置”。这是关键步骤！请参阅 **Figure 10.15**。
*   请选择将“其他磁盘加密警告”设置为“阻止”，将“允许标准用户在 Azure AD 加入期间启用加密”设置为“允许”。
*   配置该页面上你希望的其他设置。
*   为 Autopilot 创建一个新的 Azure AD 组或使用现有组。我将把我的新 BitLocker 与 Autopilot 配置文件分配给 **Chapter 8** “Rollouts and Refreshes with Configuration Designer and Autopilot” 中的 Autopilot（所有设备）组，这将作用于每台 Autopilot 设备。
*   确保为所有 Autopilot 设备启用了 Windows 10 ESP（注册状态页）。这是我们设置时的默认值（如果你想复查我的意思，可以参考远在 Figure 8.31 中的 Windows 10 ESP 示例）。

![Figure 10.15 For hardware with HTSI/InstantGo, do not select to perform encryption; that happens automatically.](images/c10f015.jpg)

**Figure 10.15** 对于具有 HTSI/InstantGo 的硬件，请勿选择执行加密；加密会自动发生。

现在，重置或以其他方式让“已在 Autopilot 中注册的机器”启动并开始 OOBE 过程。

### 通过 PowerShell 脚本启用 BitLocker

还有一种启用 BitLocker 的替代方法，我未尝试但看起来很有前景。而且，如果由于某种原因你使用的是早于 1809 版本的 Windows 10，此方法也适用。当只有标准用户可用时，有一种更笨拙的方法来启动 BitLocker。

基本上，你可以使用 PowerShell 脚本方法以 SYSTEM 身份操控 BitLocker，用户对此毫不知情。

除非绝对必要，我不会建议以这种方式操作，但具体细节和脚本请见此处。

