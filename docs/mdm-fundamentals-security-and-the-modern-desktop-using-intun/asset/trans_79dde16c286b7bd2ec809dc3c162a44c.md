

# 关于 ADMX 文件设置的说明

请注意，并非每个 ADMX 文件都会在用户端和计算机端都完美地拥有相同的设置，但 Foxit Reader 的这个文件确实如此。

现在，你可以将第二个策略添加到配置文件中。为此，请在 OMA-URI 设置边栏选项卡中单击**添加**，然后当出现**添加行**时，你可以添加禁用 Foxit Updater 的策略。

你将填入 10 秒前创建的名称、用户或设备 OMA-URI（我的示例中将使用设备），将其数据类型设为 String，然后在 Value 中输入 `<enabled/>`，中间不带空格。如果你想在计算机端分发该设置，可以看到 [图 3.30](#c03.xhtml#figure3-30)（左侧）中的策略；如果你想在用户端分发该设置，可以看到 [图 3.30](#c03.xhtml#figure3-30)（右侧）中的策略。

![Figure 3.30 Add the value to disable Foxit Updater. You can deliver the value to Device (left) or User (right).](images/c03f030a.jpg)

[**图 3.30**](#c03.xhtml#figureanchor3-30) 添加值以禁用 Foxit Updater。你可以将该值分发到设备（左侧）或用户（右侧）。

单击**保存**以保存该值，然后再次单击以保存配置文件。接着将其分配给**所有设备**。请注意，即使你希望设置影响用户端，你也必须将配置文件分配给设备。是不是很奇怪？这是因为 ADMX 设置本身的 URI（`./User` 或 `./Device`）会在设置分发到设备端后发挥作用。

回到你的 Windows 10 计算机上，如果 Foxit Reader 仍在打开状态，请将其关闭。然后与 MDM 服务同步。你应该会看到 [图 3.31](#c03.xhtml#figure3-31) 所示的内容，显示你引入的自定义 ADMX 设置。

![Figure 3.31 You can see the ingested custom ADMX policies in the MDM sync (after you close and reopen the page).](images/c03f031.jpg)

[**图 3.31**](#c03.xhtml#figureanchor3-31) 你可以在 MDM 同步中看到引入的自定义 ADMX 策略（关闭并重新打开页面后）。

然后打开 Foxit Reader，转到**文件** ➢ **首选项** ➢ **更新程序**。

你应该会看到 Foxit Reader 的 UI 被锁定，用户无法进行配置，如 [图 3.32](#c03.xhtml#figure3-32) 所示。

![Figure 3.32 Successful lockout of Foxit reader with ingested ADMX file](images/c03f032.jpg)

[**图 3.32**](#c03.xhtml#figureanchor3-32) 成功通过引入的 ADMX 文件锁定 Foxit Reader

你可以检查几个位置，查看设置是否已写入注册表（请注意，这些也是很好的故障排除步骤）。

请记住，ADMX 定义本质上是分发到客户端并在本地存储的。位置在哪里？在 `HKLM\Software\Microsoft\PolicyManager\AdmxDefault\{GUID}` 中，正如你在 [图 3.33](#c03.xhtml#figure3-33) 中所见。你应该会看到我们分发下去的完整 Foxit Reader ADMX。

![Figure 3.33 The entire ADMX downloaded into the Registry](images/c03f033.jpg)

[**图 3.33**](#c03.xhtml#figureanchor3-33) 完整的 ADMX 已下载到注册表中

接着，我们要验证的实际内容——组策略写入的位置，可以在 [图 3.34](#c03.xhtml#figure3-34) 中看到。你要找的是 `HKLM\Software\Policies\Foxit\Reader 9.0\Preferences`，并查看 DisableUpdate 是否设置为 0（这有点不寻常；大多数编写良好的 ADMX 文件通常会将 DisableUpdate 设置为 1，但我可以接受）。

![Figure 3.34 The Group Policy location is written to by the ADMX.](images/c03f034.jpg)

[**图 3.34**](#c03.xhtml#figureanchor3-34) 组策略位置由 ADMX 写入。

![image](images/tip.jpg) 如果这看起来工作量大得惊人，嗯，你说得对，确实如此。同样，Intune 很可能会为第三方 ADMX 设置提供某种 ADMX“引入”例程。但也请注意，PolicyPak MDM 也可以做到这一点，适用于几乎所有应用程序，并锁定这些设置（甚至包括许多没有内置锁定功能的应用程序）。这是通过 PolicyPak MDM 中的 PolicyPak Application Manager 组件实现的。这些应用程序的锁定设置可以使用组策略或你的 MDM 服务进行部署。请查看 `www.policypak.com/products/policypak-application-manager-including-policypak-designstudio.html` 上的演示视频，它们能极大地减轻这一过程中的挫败感。

你可以通过以下 URL 了解更多关于将 ADMX 文件引入 MDM 服务的信息：

*   `https://docs.microsoft.com/en-us/windows/client-management/mdm/understanding-admx-backed-policies`（搜索关键词 Ingest）
*   `https://docs.microsoft.com/en-us/windows/client-management/mdm/win32-and-centennial-app-policy-configuration`
*   `https://www.petervanderwoude.nl/post/deep-dive-ingesting-third-party-admx-files/`

## 替换终结点上的现有 ADMX 设置

好的，让我们稍微展望一下未来。

你已经部署了 Foxit Reader 9.2，并使用了随附的 ADMX 设置。

随后，你使用 MDM 服务推出 Foxit Reader 9.3，其中包含一些可通过 ADMX 控制的功能。也许 Foxit Reader 9.3 有一个新设置（我在这里编造一个），即主题颜色。

“太棒了！”你心想，“我只需更新并覆盖我之前放入配置文件中的 ADMX 定义（回到 [图 3.28](#c03.xhtml#figure3-28)）！当我粘贴更新后的 ADMX 设置时，我就能获得管理 Foxit Reader 9.3 所提供的酷炫新主题颜色策略设置的能力了！”

砰。直接掉进蛇坑里了！

我本来也猜不到会有这种行为，但显然 MDM 引擎无法处理这种情况。

当你尝试整体替换自定义应用程序的 ADMX 定义时，它就是不起作用。

追查此事，我在 PolicyCSP 文档中发现了一个非常“细则”式的推理：

`https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-configuration-service-provider`

引述如下：

> Policy/ConfigOperations/ADMXInstall/AppName/Preference/UniqueID 在 Windows 10 版本 1703 中添加。指定包含要导入的首选项的应用程序 ADMX 文件的唯一 ID。支持的操作为 Add 和 Get。不支持 Delete。

你看到问题了吗？**“不支持 Delete。”**

所以你升级了（实际上是替换了）带有较新版本的 ADMX 定义。MDM 引擎检测到更改并说：“爱莫能助，兄弟。”

结果（至少）是在 Microsoft ➢ Windows ➢ DeviceManagement-Enterprise-Diagnostics-Provider 日志中出现错误，如此处事件 454 所示。

![](images/c03uf003.jpg)

因为现有的 ADMX 定义无法删除，所以无法替换。因此引擎陷入一种僵局，你也得不到更新。

请注意，这个故事不仅限于 Foxit Reader；它可能指的是用稍新的版本升级 Office 2016 ADMX、用稍新的版本升级 Firefox ADMX 等。

那么如何摆脱这个困境？以我目前来看，有三个答案：

*   **选择 1：** 为较新的应用程序专门创建一个新配置文件。
*   **选择 2：** 预先运行某种自定义清理 PowerShell 脚本，手动从注册表中清除数据。你的目标是移除存储 ADMX 内容的 `HKLM\Software\Microsoft\PolicyManager\AdmxDefault\{GUID}` 数据。
*   **选择 3：** 使用 PolicyPak MDM，通过 PolicyPak Admin Templates Manager、PolicyPak Preferences Manager 或 PolicyPak Application Manager 来分发设置（视情况而定）。当需要更改值时，**PolicyPak 只需更改它即可**。

也许这在 Windows 的某个后续版本中就会修复。也许等到你读到这本书时已经解决了……也可能没有。但我要确保如果这是“那些不容易快速修复的问题”之一，你也知道了。

## 创建和使用组

到目前为止，在本书中，我们已经创建了一些测试配置文件，然后将它们链接到 All Users 或 All Computers，这两个是 Intune 中存在的默认组。

