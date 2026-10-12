
# 引入第三方 ADMX 文件

在组策略领域，引入 ADMX 文件的概念称为“使用” ADM 或 ADMX 文件。现在在 MDM 中，只是为了与众不同称为“引入”，对我来说听起来有点恶心。但这只是我个人感觉。

无论如何，记住之前的约定：微软维护的所有 ADMX 支持策略，都是来自微软的，正如我说的，（几乎）保证按预期工作。但对于第三方 ADMX 文件，微软态度较随意，不维护，因此不保证它们按预期工作。请记住，微软发布了我之前提到的管理模板技术预览版。截至目前，无法通过引入以点击方式添加 ADMX 模板。我衷心怀疑他们会添加此功能，似乎很容易实现。我无法展示分步操作，因为目前无内容可展示。但请留意这一可能性。

因此，目前步骤相当繁琐（又是）。

系好安全带，操作如下。

引入第三方 ADMX 分两步：

*   将第三方 ADMX 文件复制到自定义 `OMA-URI`
*   设置来自 ADMX 文件的值（与上一节所做几乎完全相同）

开始此示例，我将使用 Foxit Reader 的 ADMX，但同样，大多数第三方 ADMX 文件应适用。

你可能想知道为什么我不选 Adobe Acrobat Reader 或 Chrome 示例，我有充分理由：

*   **Google Chrome 及其 ADMX**：就要付印时，Chrome 获得了通过 MDM 遵循其 ADMX 的能力。官方分步说明见 `https://support.google.com/chrome/a/answer/9102677`。注意，并非每个 Chrome 设置在非域加入机器上实际生效。（PolicyPak 团队一成员花时间弄清哪些项目在非域加入机器上“完全正常”工作。若想查看，见：`https://kb.policypak.com/kb/article/284-which-items-in-chrome-will-and-will-not-work-when-nondomain-joined`。）

Adobe Reader 的策略支持简直糟糕透顶。我无法理解，但它只有极少数策略，我测试的几个完全无法按预期工作，而且许多所谓的策略实际上只是首选项。因此 UI 无法锁定，所以我不会在这里使用它。

Microsoft Office 有一些策略可以锁定，其他的则不行。此外，ADMX 文件到处都是，对于一个简单的示例来说过于复杂。

你可能想知道 MDM 引擎如何知道接受什么、丢弃什么。答案其实非常简单优雅。如果你查看 Microsoft 随操作系统附带的 ADMX 项目，所有策略设置都会写入类似 `HKLM or HKCU / Software / Policies / Microsoft / <something>` 的注册表项。

Adobe、Chrome、Firefox、Office、PolicyPak 等都附带 ADMX 文件来对其产品进行最终调整，但正如你所料，它们不会将值写入 Microsoft 操作系统子键。因此，所有这些设置都会被 MDM 写入并遵守，因为 MDM 系统并不负责策划这些设置。

对于我们的工作示例，我选择了 Foxit Reader 及其 ADMX 文件。如果你想跟着测试，在你的 Windows 10 终端上手动安装最新版 Foxit Reader（撰写本文时为 9.2 版）。只需访问 `www.foxitsoftware.com/pdf-reader/` 下载标准版并安装。同样，在由 MDM 管理的 Windows 10 终端上安装，并采用所有默认设置（未展示）。

安装后在 Windows 10 机器上运行 Foxit Reader，花一点时间查看自动更新状态：依次转到“文件” ➢ “首选项”，然后点击“更新程序”。你应该能看到图 3.25 所示内容，程序设置为下载更新并让用户选择是否安装。

![Figure 3.25 Foxit Reader’s default update behavior](img/c03f025.jpg)

**图 3.25** Foxit Reader 的默认更新行为

我们将使用 MDM 服务将其设置为“不自动下载或安装更新”，并将其锁定，使其用户无法更改。

接下来，在你的管理站上下载并准备好 Foxit ADMX 文件。最后检查时，可在此处找到：`https://help.foxitsoftware.com/kb/available-gpo-templates.php`。

如果我要使用组策略管理 Foxit Reader（我不会），它看起来会像图 3.26 所示。我可能想用的设置是**禁用自动更新**策略设置，也见于图 3.26。

![Figure 3.26 How you would use Group Policy to set Foxit Reader to stop automatic updates](img/c03f026.jpg)

**图 3.26** 如何使用组策略设置 Foxit Reader 停止自动更新

因此，要通过 MDM 实现此目的，请先用记事本打开 Foxit ADMX 文件并准备好。然后使用 Intune 等 MDM 服务创建一个新配置文件，再创建一个自定义 `OMA-URI` 策略，就像我们之前做的那样；只是这次要清楚表明你在为 Foxit Reader 做配置。

在 `OMA-URI` 字段中，你需要指定一个特殊语法，表示你即将提供一个完整的 ADMX 文件。语法如下：

```
./Device/Vendor/MSFT/Policy/ConfigOperations/ADMXInstall/{AppName}/
{SettingType}/{FileUid or AdmxFileName}
```

好吧，这给我们出了个小难题。我们需要找出并填入以下值：

*   `AppName`：可以是任何名称，但最好用能描述我们正在做什么的名称。我将其命名为 `FoxitReader`。
*   `SettingType`：尽管这看起来可能是不同的关键字，但在实践中，引入 ADMX 时，这必须始终是单词 `Policy`。
*   `FileUid` 或 `AdmxFileName`：也可以是任何名称，但建议命名为你正在使用的 ADMX 文件名。所以我将使用值 `FoxitReaderADMX`。

将所有内容组合在一起（并决定在用户端执行）将得到如下 `OMA-URI`：

```
./Device/Vendor/MSFT/Policy/ConfigOperations/ADMXInstall/FoxitReader/
Policy/FoxitReaderAMX
```

太棒了！

![image](img/warning.jpg) 无论稍后你想分发用户还是计算机（设备）策略，ADMX 文件本身必须用 `./Device`（如上所示）描述，而非 `./User`。同样，稍后你将决定分发用户还是计算机设置；但 ADMX 文件本身必须指定为 `./Device`。

现在，回到 MDM 领域，创建一个新配置文件来包含 Foxit 策略，如图 3.27 所示。提醒一下，在 Intune 中，你需点击“设备配置 - 配置文件” ➢ “创建配置文件”。然后选择图 3.27 所示设置。

![Figure 3.27 Create a profile for Foxit policies with the Custom type.](img/c03f027.jpg)

**图 3.27** 使用自定义类型创建 Foxit 策略配置文件。

然后，在 `OMA-URI` 设置视图中，给它一个名称，粘贴你 10 秒前制作的 `OMA-URI`，提供字符串数据类型，然后是有趣的部分……将*所有* Foxit ADMX 内容粘贴到“值”字段中（见图 3.28），然后点击“确定”（未显示）。这会将整个 ADMX 文件保存到配置文件中。

随后，所有这些可能的 ADMX 定义都会被分发到终端。（这是一个有趣且鲜为人知的点，几页后将变得非常重要。详见侧边栏“替换终端上的现有 ADMX 设置”。）

![Figure 3.28 Adding an ADMX file as a custom OMA-URI. The whole ADMX file gets downloaded to the client.](img/c03f028.jpg)

**图 3.28** 作为自定义 `OMA-URI` 添加 ADMX 文件。整个 ADMX 文件将下载到客户端。

接下来，你需要深入 ADMX 文件内部找到要分发的值。在图 3.29 中，我认为我找到了正确的项，因为其名称包含“Disable”和“Updater”字样。所以我相当确定 `PREF_DisableUpdater` 就是正确的项。

![Figure 3.29 Find the policy setting within the ADMX you want to deliver.](img/c03f029.jpg)

**图 3.29** 在 ADMX 中查找要分发的策略设置。

我们需要将其转换为 MDM 格式。表达所需内容的方式如下：

```
./Device/Vendor/MSFT/Policy/Config/
{AppName}∼{SettingType}∼{CategoryPathFromADMX}/{SettingFromADMX}
```

或

```
./User/Vendor/MSFT/Policy/Config/
{AppName}∼{SettingType}∼{CategoryPathFromADMX}/{SettingFromADMX}
```

很好，又是一个需要拼凑的谜题。各部分如下：

*   `AppName`：应与配置 ADMX 文件引入时使用的应用名称相同。记得我用的是 `FoxitReaderADMX`。
*   `SettingType`：同样，这始终只是单词 `Policy`。
*   `CategoryPathFromADMX`：在图 3.29 中，我高亮了两个区域。一个是策略名称，另一个是 `parentCategory`。这就是这里要填的内容；在我们的例子中称为 `PREFERENCES`。但这还不够，因为任何设置可能有一个或多个 `parentCategory`（或完全没有 `parentCategory`）。我花了一段时间追踪 Foxit ADMX 文件，第一次甚至弄错了。但有两个父类别：一个是图 3.29 中高亮的，还有一个（未显示）在文件顶部称为 `FOXIT`。
*   `SettingFromADMX`：这是我们要配置的设置，也见于图 3.29。在我们的例子中是 `PREF_DisableUpdater`。

将所有内容组合在一起，我们得到：

```
./User/Vendor/MSFT/Policy/Config/
FoxitReader∼Policy∼FOXIT∼PREFERENCES/PREF_DisableUpdater
```

或

```
./Device/Vendor/MSFT/Policy/Config/
FoxitReader∼Policy∼FOXIT∼PREFERENCES/PREF_DisableUpdater
```

## 关于 ADMX 文件设置的说明

请注意，并非每个 ADMX 文件都会在用户端和计算机端都完美地拥有相同的设置，但 Foxit Reader 的这个文件确实如此。

现在，你可以将第二个策略添加到配置文件中。为此，请在 `OMA-URI` 设置边栏选项卡中单击**添加**，然后当出现**添加行**时，你可以添加禁用 Foxit Updater 的策略。

你将填入 10 秒前创建的名称、用户或设备 `OMA-URI`（我的示例中将使用设备），将其数据类型设为 String，然后在 Value 中输入 `<enabled/>`，中间不带空格。如果你想在计算机端分发该设置，可以看到图 3.30（左侧）中的策略；如果你想在用户端分发该设置，可以看到图 3.30（右侧）中的策略。

![Figure 3.30 Add the value to disable Foxit Updater. You can deliver the value to Device (left) or User (right).](img/c03f030a.jpg)

**图 3.30** 添加值以禁用 Foxit Updater。你可以将该值分发到设备（左侧）或用户（右侧）。

单击**保存**以保存该值，然后再次单击以保存配置文件。接着将其分配给**所有设备**。请注意，即使你希望设置影响用户端，你也必须将配置文件分配给设备。是不是很奇怪？这是因为 ADMX 设置本身的 URI（`./User` 或 `./Device`）会在设置分发到设备端后发挥作用。

回到你的 Windows 10 计算机上，如果 Foxit Reader 仍在打开状态，请将其关闭。然后与 MDM 服务同步。你应该会看到图 3.31 所示的内容，显示你引入的自定义 ADMX 设置。

![Figure 3.31 You can see the ingested custom ADMX policies in the MDM sync (after you close and reopen the page).](img/c03f031.jpg)

**图 3.31** 你可以在 MDM 同步中看到引入的自定义 ADMX 策略（关闭并重新打开页面后）。

然后打开 Foxit Reader，转到**文件** ➢ **首选项** ➢ **更新程序**。

你应该会看到 Foxit Reader 的 UI 被锁定，用户无法进行配置，如图 3.32 所示。

![Figure 3.32 Successful lockout of Foxit reader with ingested ADMX file](img/c03f032.jpg)

**图 3.32** 成功通过引入的 ADMX 文件锁定 Foxit Reader

你可以检查几个位置，查看设置是否已写入注册表（请注意，这些也是很好的故障排除步骤）。

请记住，ADMX 定义本质上是分发到客户端并在本地存储的。位置在哪里？在 `HKLM\Software\Microsoft\PolicyManager\AdmxDefault\{GUID}` 中，正如你在图 3.33 中所见。你应该会看到我们分发下去的完整 Foxit Reader ADMX。

![Figure 3.33 The entire ADMX downloaded into the Registry](img/c03f033.jpg)

**图 3.33** 完整的 ADMX 已下载到注册表中

接着，我们要验证的实际内容——组策略写入的位置，可以在图 3.34 中看到。你要找的是 `HKLM\Software\Policies\Foxit\Reader 9.0\Preferences`，并查看 `DisableUpdate` 是否设置为 0（这有点不寻常；大多数编写良好的 ADMX 文件通常会将 `DisableUpdate` 设置为 1，但我可以接受）。

![Figure 3.34 The Group Policy location is written to by the ADMX.](img/c03f034.jpg)

**图 3.34** 组策略位置由 ADMX 写入。

![image](img/tip.jpg) 如果这看起来工作量大得惊人，嗯，你说得对，确实如此。同样，Intune 很可能会为第三方 ADMX 设置提供某种 ADMX“引入”例程。但也请注意，PolicyPak MDM 也可以做到这一点，适用于几乎所有应用程序，并锁定这些设置（甚至包括许多没有内置锁定功能的应用程序）。这是通过 PolicyPak MDM 中的 PolicyPak Application Manager 组件实现的。这些应用程序的锁定设置可以使用组策略或你的 MDM 服务进行部署。请查看 `www.policypak.com/products/policypak-application-manager-including-policypak-designstudio.html` 上的演示视频，它们能极大地减轻这一过程中的挫败感。

你可以通过以下 URL 了解更多关于将 ADMX 文件引入 MDM 服务的信息：

*   `https://docs.microsoft.com/en-us/windows/client-management/mdm/understanding-admx-backed-policies`（搜索关键词 Ingest）
*   `https://docs.microsoft.com/en-us/windows/client-management/mdm/win32-and-centennial-app-policy-configuration`
*   `https://www.petervanderwoude.nl/post/deep-dive-ingesting-third-party-admx-files/`

### 替换终结点上的现有 ADMX 设置

好的，让我们稍微展望一下未来。

你已经部署了 Foxit Reader 9.2，并使用了随附的 ADMX 设置。

随后，你使用 MDM 服务推出 Foxit Reader 9.3，其中包含一些可通过 ADMX 控制的功能。也许 Foxit Reader 9.3 有一个新设置（我在这里编造一个），即主题颜色。

“太棒了！”你心想，“我只需更新并覆盖我之前放入配置文件中的 ADMX 定义（回到图 3.28）！当我粘贴更新后的 ADMX 设置时，我就能获得管理 Foxit Reader 9.3 所提供的酷炫新主题颜色策略设置的能力了！”

砰。直接掉进蛇坑里了！

我本来也猜不到会有这种行为，但显然 MDM 引擎无法处理这种情况。

追查此事，我在 `PolicyCSP` 文档中发现了一个非常“细则”式的推理：

`https://docs.microsoft.com/en-us/windows/client-management/mdm/policy-configuration-service-provider`

引述如下：

> Policy/ConfigOperations/ADMXInstall/AppName/Preference/UniqueID 在 Windows 10 版本 1703 中添加。指定包含要导入的首选项的应用程序 ADMX 文件的唯一 ID。支持的操作为 Add 和 Get。不支持 Delete。
