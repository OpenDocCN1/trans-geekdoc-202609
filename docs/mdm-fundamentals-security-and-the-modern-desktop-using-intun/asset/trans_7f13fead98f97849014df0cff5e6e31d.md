
如果在测试期间，你发现 BitLocker 没有按预期自动启动，也许你正在做我曾经做过的事：我（哎呀）在电脑里留了一张 DVD；确切地说，是虚拟机的“虚拟 DVD”驱动器加载了一个 ISO 文件。当你这样做时，BitLocker 不会启动，直到移除 DVD 并重新启动计算机，正如事件日志中所述，具体是在 BitLocker - API 的事件日志中，如图 10.20 所示。

请记住，当你以标准用户身份登录时，BitLocker 完全没有任何指示；它是完全静默的。静默成功，静默失败。

![图 10.20 不要在驱动器中留下 DVD，否则 BitLocker 将无法启动。](images/c10f020.jpg)

**图 10.20** 不要在驱动器中留下 DVD，否则 BitLocker 将无法启动。

此外，Windows 10 Pro 计算机的加密自动启动应仅发生在 Windows 10 1809 及更高版本中；否则，旧版 Windows 10 Pro 计算机将不会自动执行加密。

你可以查看 Intune 终端保护文档：

`https://docs.microsoft.com/en-us/intune/endpoint-protection-windows-10#windows-encryption`

底层的 BitLocker CSP 提示和详细信息请见此处：

`https://docs.microsoft.com/en-us/windows/client-management/mdm/BitLocker-csp`

BitLocker 的未来目前一片光明。这篇文章展示了一个针对希望迁移到现代管理（甚至保持本地部署）的本地客户的建议路线图。值得一读，也值得持续关注：

`https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Microsoft-expands-BitLocker-management-capabilities-for-the/ba-p/544329`

## 使用 AppLocker 或 PolicyPak Least Privilege Manager 进行应用程序白名单管理

白名单的理念是：只有经过批准的应用程序才能运行。只有我们了解并信任的东西才能运行。其他所有东西，砰！拒绝！

AppLocker 作为一种白名单解决方案已经存在很长时间了，自 Windows 7 以来就有。但 AppLocker 结合组策略仅适用于 Windows 10 Enterprise 和 Education 版本。而结合 MDM，AppLocker 也适用于 Windows 10 Pro，这是一个不错的小惊喜。AppLocker 功能相当强大，在 Intune 或其他 MDM 服务中设置它并不算太难，但也不是你想象中的“点点鼠标”那么简单。它需要一个自定义 OMA-URI，我们稍后将探讨。

而且，既然 AppLocker 并非适合所有人的工具，我想介绍一个替代方案：PolicyPak Least Privilege Manager，它可以执行类似 AppLocker 的职责，还有更多功能。事实上，在上一节讨论进程提权和克服 UAC 提示时，我们已经看到了 PolicyPak Least Privilege Manager，而这是 AppLocker 做不到的，也不是它试图做的。

但现在，我们将从获取一些本地 AppLocker 规则并将其转换为 Intune 可用的规则开始。

然后，我们将探索 PolicyPak Least Privilege Manager 以执行类似 AppLocker 的白名单管理。

### 使用 AppLocker 进行白名单管理

使用 AppLocker 的第一部分涉及打开组策略编辑器并进行一些小规模测试。是时候获取一本绿色的组策略书（`www.MDMandGPanswers.com/book`），并遵循“使用组策略实施安全性”章节中的说明来创建一些初始 AppLocker 规则。

怎么说？没时间？没有这本书？（或者，老天保佑，你不*想要*这本书？）好吧，我将长话短说，给你一个速成示例让你快速上手。但说实话，我在组策略书中以 500 级别的深度详细介绍了 AppLocker，所以我不会在这里重复所有那些细节。

#### 创建本地组策略 AppLocker 规则

作为 Windows 10 计算机的本地管理员，运行 `GPedit.msc`。然后导航到“计算机配置” ➢ “Windows 设置” ➢ “安全设置” ➢ “应用程序控制策略” ➢ “AppLocker”。

右键单击 AppLocker 节点并选择“属性”。对于此示例，仅选择“可执行规则”，并验证是否选中了“强制执行规则”（如图 10.21 所示），然后单击“确定”。

然后在空白处右键单击并选择“创建默认规则”，如图 10.22 所示。默认规则有助于防止你在使用 AppLocker 时“自废武功”，因此建议在首次测试时使用。

![图 10.21 使用 AppLocker 指定要阻止的项目类型](images/c10f021.jpg)

**图 10.21** 使用 AppLocker 指定要阻止的项目类型

![图 10.22 创建 AppLocker 默认规则](images/c10f022.jpg)

**图 10.22** 创建 AppLocker 默认规则

让我们保持简单，制作规则暂时到此为止。对于其他所有内容，你都必须创建一条“允许规则”，以便开放 AppLocker 允许项目运行。因此，这是一个相当强力的配置，也是一个完美的首次测试。

要导出这些规则，请右键单击 AppLocker 节点并选择“导出策略”，如图 10.23 所示。

![图 10.23 导出 AppLocker 策略](images/c10f023.jpg)

**图 10.23** 导出 AppLocker 策略

妥善保管新生成的导出 XML 文件；稍后在 Intune 中你将需要它。

#### 执行小规模/本地 AppLocker 测试

现在，我建议你可以通过下载一个应被 AppLocker 阻止的可执行文件来进行小规模本地测试。我建议你下载 Chrome Portable，这是一个无需安装的 Chrome 版本，来源为 `https://portableapps.com/apps/internet/google_chrome_portable`。你需要先解压它。在我们在本地开启 AppLocker 之前，先快速试运行一下。

接下来，你应该启用 Application Identity 服务（你需要以管理员身份执行，就像 Frank Rizzo 一样），然后等待几分钟让它生效。（开启服务后大约需要两三分钟。）

请注意，有一个奇怪的现象：你可能无法使用 MMC 管理单元将 AppLocker 的 AppID 服务设置为自动启动。但是，你可以使用提升权限的命令行：

```
sc.exe config appidsvc start=auto
```

这工作正常。

然后，以标准用户身份尝试再次运行 Chrome Portable。你应该会看到图 10.24 所示的结果。在尝试将其引入 Intune 之前，请务必先在小规模本地测试中让 AppLocker 正常工作。

![图 10.24 通过 AppLocker 阻止未经批准的应用程序。请注意，Application Identity 服务必须运行几分钟，AppLocker 首次才会生效。](images/c10f024.jpg)

**图 10.24** 通过 AppLocker 阻止未经批准的应用程序。请注意，Application Identity 服务必须运行几分钟，AppLocker 首次才会生效。

### 在 Intune 中使用你的 AppLocker 规则

下一站：Intune。

好吧，不完全是。首先我们必须检查导出的文件并进行裁剪。然后我们将进入 Intune 并提供裁剪好的 AppLocker XML 文件。

#### 裁剪 AppLocker XML

让我们检查 AppLocker 导出的输出。你将看到我在 Notepad++ 中查看 XML 的屏幕截图（因此左侧会显示行号）。AppLocker 奇怪的地方在于，你不能直接拿导出的 XML 原样“硬塞”进 Intune。那行不通！你需要仔细找到类别类型的开头和结尾；在我们的示例中，是“可执行规则”。所以在图 10.25 中，你可以看到一行左右确切要复制并粘贴到 Intune 中的内容（稍后）。

![图 10.25 分离出用于 Intune 的 AppLocker 部分](images/c10f025.jpg)

**图 10.25** 分离出用于 Intune 的 AppLocker 部分
