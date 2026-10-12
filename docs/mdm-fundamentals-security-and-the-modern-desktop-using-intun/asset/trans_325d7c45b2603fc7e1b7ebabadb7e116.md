
嗯，因为如果你喜欢 PolicyPak 的功能，可能想要利用不止一个版本来全面覆盖需求。PolicyPak 配合 MDM 托管设备的主要用例如下：

## 将几乎所有组策略、组策略首选项和组策略安全设置迁移到 MDM

并非所有组策略设置都在 MDM 中。我们在本书中已对此进行了大量详细介绍。Intune 中的管理模板部分是一个不错的进步，但目前它仅包含组策略中可用设置的一小部分。

## 克服 UAC 提示（PolicyPak Least Privilege Manager）

当你使用 Autopilot 部署新电脑时，你希望用户作为标准用户运行。太棒了！现在他们无法做很多重要的事情。

糟糕。使用 `PolicyPak Least Privilege Manager` 克服 UAC 提示并执行类似管理员的操作。太棒了！

## 为应用程序指定正确的设置（PolicyPak Application Manager）

应用程序通过 Intune 部署。太棒了！现在这些应用程序实际上*并未*正确配置。

糟糕。使用 `PolicyPak Application Manager` 在这些应用程序旁提供“当下的正确设置”。太棒了！

## 为 Windows 10 功能和可选功能指定正确的设置（PolicyPak Feature Manager for Windows）

你已通过 Autopilot 完成部署。太棒了！

现在功能和可选功能的状态并非你所需。

糟糕。使用 `PolicyPak Feature Manager for Windows` 实施你为支持用户需求所需的“当下的正确功能”。太棒了！

## “有大脑的开始菜单。”

你已从 Intune 下发新的 MSI 或 MSIX。太棒了！

现在你的应用程序在开始菜单右侧毫无踪迹。

糟糕。使用 `PolicyPak Start Screen & Taskbar Manager` 将应用程序图标放入组和/或放到任务栏。太棒了！

## MDM 的脚本功能可能还不够

我在[第 6 章](#c06.xhtml)中已介绍 PolicyPak 的这一方面。Intune 内置脚本引擎的问题在于它只能运行 PowerShell，且存在大小限制。此外，脚本仅应用一次。

借助 `PolicyPak Scripts Manager` 组件，你的脚本可以是 `.VBS` (Visual Basic)、JavaScript (`.JS`)、Shell (`.BAT` 或 `.CMD`) 或 PowerShell。脚本可应用一次、始终（每小时）、或再次应用（重新触发时）。脚本没有大小限制。你可以对脚本进行排序。而且，脚本可以利用项级定向 (ILT) 来检测条件何为真、何为假（而不是让你尝试将其烘焙进脚本中）。

既然已在[第 6 章](#c06.xhtml)中介绍，我在此不再赘述。但 PolicyPak Scripts 的视频可在以下网址找到：`www.policypak.com/products/scripts-manager.html`。

## Windows 10 的 AppLocker 功能可能还不够

在[第 10 章](#c10.xhtml)“使用基线、BitLocker、AppLocker 和条件访问实现安全”中，我解释了 AppLocker 很棒，但你可能需要不断监管它以反复添加规则。因此，在[第 10 章](#c10.xhtml)中我展示了 `PolicyPak Least Privilege Manager` 及其 SecureRun™ 功能，该功能可让你实现一键白名单。你可以在此查看该功能：

`https://www.policypak.com/video/stop-cryptolocker-and-other-unknown-zero-day-attacks-with-policypak-secureruntm.html`

## MDM 的文件部署功能可能需要增强

这是另一个我在[第 6 章](#c06.xhtml)中已详细介绍的主题，具体涉及 `PolicyPak File Delivery Manager`。`PolicyPak File Delivery Manager` 使你能够从 Amazon S3 等源下载文件（包括超大文件）。如果文件是 ZIP，它可自动解压，从而确保一组文件始终保持最新。同样，详情和屏幕截图请参见[第 6 章](#c06.xhtml)。

### PolicyPak 入门

要开始使用 PolicyPak（任何版本），我们要求你首先参加“为成功试用做准备”网络研讨会。这将为你提供最新知识，并解释 PolicyPak 可解决的最新问题。之后我们会提供安装包，你可以自行试用。PolicyPak 下载内容如[图 11.16](#c11.xhtml#figure11-16)所示。

![Figure 11.16 将 PolicyPak 客户端扩展 MSI 安装到终结点，在你的电脑上安装管理控制台 MSI，仅此而已。 ](images/c11f016.jpg)

[**图 11.16**](#c11.xhtml#figureanchor11-16) 将 `PolicyPak 客户端扩展 MSI` 安装到终结点，在你的电脑上安装 `管理控制台 MSI`，仅此而已。

安装简单，如下所示：

*   **你的电脑：** 拥有组策略管理控制台以创建和编辑组策略及 PolicyPak 项目。在那里安装 `PolicyPak 管理控制台 MSI`。你可以看到[图 11.17](#c11.xhtml#figure11-17)所示的结果。

*   **终结点电脑：** 使用 Intune 或其他 MDM 部署 `PolicyPak 客户端扩展 (CSE)`。

*   **PolicyPak 许可证文件：** 它是一个 MSI。上传到 Intune 并部署到客户端电脑。

想要一份可爱的概览动画，请查看：

`https://www.policypak.com/video/policypak-and-mdm-deploying-real-group-policy-and-extra-policypak-settings-overview.html`

获得所需设置后，只需将它们导出为 XML。（稍后我们会做更多此类操作。）拥有“XML 篮子”后，你需要将它们打包成一个 `.MSI` 文件。PolicyPak 有一个名为 `Group Policy Exporter utility`（组策略导出工具）的工具正好能做这件事。

所以，计划如下：

*   使用 PolicyPak 创建无法通过其他方式创建的策略设置。
*   将这些设置导出为 XML 文件。
*   将 XML 文件打包进 `.MSI` 文件。
*   将 MSI 上传到 Intune 或其他 MDM 服务。
*   将 MSI 分配给组（用户或计算机）。
*   MSI 被下载，魔法生效。

想要了解 PolicyPak 和 Intune 的总体概览，请查看此视频：

`https://www.policypak.com/video/policypak-and-microsoft-intune.html`

![Figure 11.17 PolicyPak 直接挂钩到你已熟知的组策略编辑器。 ](images/c11f017.jpg)

[**图 11.17**](#c11.xhtml#figureanchor11-17) PolicyPak 直接挂钩到你已熟知的组策略编辑器。

### 使用 PolicyPak 将现有组策略导出到 MDM

拥有 4,000 多个组策略设置、10,000 种组策略首选项变体和无数安全设置，MDM 根本无法全部覆盖。因此 PolicyPak 使你能够获取现有的组策略、组策略首选项和组策略安全设置，并将其导出以供使用。

这将是导出真实组策略设置的三个组件：

*   `PolicyPak Admin Templates Manager`
*   `PolicyPak Preferences Manager`
*   `PolicyPak Security Settings Manager`

正如你在[图 11.18](#c11.xhtml#figure11-18)中所见，你可以创建源自 ADMX/管理模板的新策略。这只需使用你现有的 ADMX 存储、本地存储或域的中央存储。因此，你当前用于创建组策略 ADMX 设置的任何模板，都是你现在可以使用和导出的模板。在[图 11.18](#c11.xhtml#figure11-18)中，我正在创建一项将**禁止访问控制面板和电脑设置**的策略。

![Figure 11.18 使用 PolicyPak Admin Templates Manager 创建并导出组策略 ADMX 设置 ](images/c11f018.jpg)

[**图 11.18**](#c11.xhtml#figureanchor11-18) 使用 `PolicyPak Admin Templates Manager` 创建并导出组策略 ADMX 设置
