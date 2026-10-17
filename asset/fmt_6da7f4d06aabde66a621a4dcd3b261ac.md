
你也可以购买包含 Intune 的 Enterprise Mobility + Security 套件（如前所述）。要查看仅购买 Intune 与购买 Enterprise Mobility + Security 套件的区别，此处有一份不错的对比表：`www.microsoft.com/en-us/cloud-platform/microsoft-intune-pricing`。

总结如下：

*   可单独购买 Intune。撰写时价格为每用户 6 美元。有一种特殊的“按设备”许可证（适用于无用户登录的设备，如数字标牌），价格为每设备 2 美元。
*   可作为 Enterprise Mobility + Security E3 套件的一部分购买。
*   可作为 Enterprise Mobility + Security E5 套件的一部分购买。
*   可作为 Microsoft 365 的一部分购买。

我找到了两种试用 Windows Intune 的方法。

*   **方式 #1：** 找到前面提到的 Microsoft Enterprise Mobility + Security 定价页面，在 E5 模块中点击“立即试用”。
*   **方式 #2：** 访问“注册 Microsoft Intune 免费试用”页面：`https://docs.microsoft.com/en-us/intune/free-trial-sign-up`。

本书将使用方式 #1，注册 E5 试用版并将其连接到上一步创建的 Azure AD 试用版。因此，请再次访问：`www.microsoft.com/en-us/cloud-platform/enterprise-mobility-security-pricing`。

只需寻找“Try Now”。我创建了一个虚假的 `Outlook.com` 地址开始，耗时约 80 秒。之后，我使用的基本入门步骤可见 Figure 2.3。

![Figure 2.3 The signup page for EMS E5](img/c02f003.jpg)

**Figure 2.3** The signup page for EMS E5

接下来是创建第一个用户和公司名称。我使用的信息可见 Figure 2.4。请注意，公司名称必须在全球所有特殊的“`.onmicrosoft.com`”域中唯一。我将 `Fabrikam1000.onmicrosoft.com` 作为我的域名，贯穿本书及 `www.MDMandGPanswers.com` 的持续示例中使用。

![Figure 2.4 Create your first user and company name.](img/c02f004.jpg)

## 图 2.4：创建你的第一个用户和公司名称

然后只需坐等片刻，然后……搞定。你已准备就绪，可以大展身手了，如图 2.5 所示。

![图 2.5 EMS E5 试用成功消息](img/c02f005.jpg)

**图 2.5** EMS E5 试用成功消息

### ActiveSync、Office 365 MDM 和 Intune MDM 功能对比

你可能想知道哪个产品提供哪些功能。为此，我找到并重新整理了一份公开的 Microsoft 文档，详细列出了主要差异。

你可以在下面这个表格中看到这些差异，这样如果老板问为什么 Office 365 的 MDM 不够用，而你不得不开始购买 Intune 或其他 MDM 服务时，你就有据可依了。

![](img/c02uf001.jpg)

此外，这是我找到的最新页面，其中包含 Office 365 MDM 和 Intune 的并排对比：

`https://support.office.com/en-us/article/choose-between-mdm-for-office-365-and-microsoft-intune-c93d9ab9-efb2-4349-9b93-30c30562ee22`

又是一个丑陋的长链接，所以我制作了一个短链接：`https://bit.ly/2E20PWe`。

### Intune for Education

此处应提及另一个版本的 Windows Intune，以防这正是你的使用场景。有个 Windows Intune for Education，它拥有一项特殊的“超能力”。

也就是说，它可以从 Microsoft School Data Sync（`https://sds.microsoft.com/`）读取数据，并自动创建和保持用户组及计算机组的最新状态。

Windows Intune for Education 另一个有趣的地方在于它有两种许可方式。

*   **方式 #1** 是直接按设备购买，每台设备 30 美元。这包含你授权设备上的无限用户数。
*   **方式 #2** 是按用户付费，每年每用户 8.28 美元。别吓一跳，学生是免费的！你只需为教职员工计数。

这笔交易的“甜蜜”部分是随 Windows Intune for Education 附带的 Azure AD 类型。它有自己的版本，称为 Azure AD EDU，但它命中靶心，包含你所需的最需要的功能，包括自动注册。

你随时可以升级到 Azure AD Premium，获取一些额外的 AD 安全功能，如双因素身份验证，该功能仅在 Premium 版提供。但就我认为大多数学校需要与 Intune 配合使用的功能而言，Azure AD EDU 已经命中靶心。

请从阅读以下内容开始：

`https://www.microsoft.com/en-us/education/intune/default.aspx` 和 `https://blogs.windows.com/windowsexperience/2017/01/24/announcing-intune-education-new-windows-10-pcs-school-starting-189`

最后，我认为值得一提的是，正如有一个面向企业的名为 Microsoft 365 的全套捆绑包一样，也有一个面向教育的全套捆绑包（Office 365、Azure、Intune）以及其他一些东西，如 Minecraft（注：原文为 Mindcraft，此处应为 Minecraft 之误）。

而且，毫不意外，它被称为 Microsoft Education。因此，如果你想结合 Microsoft Education 套件的其他组件试用 Windows Intune for Education，整套产品的试用页面可以在这里找到：

`https://docs.microsoft.com/en-us/education/get-started/get-started-with-microsoft-education`

请注意，一旦你注册 Microsoft Education 试用版，他们会进行一些验证，以确认你确实是一所学校，因此如果没有学术机构背景，你无法直接开始试用。

## VMware Workspace ONE

VMware 也凭借其名为 VMware Workspace ONE 的产品加入了 MDM 管理的行列。它曾经有一个朗朗上口的名字“AirWatch”，现在换了个更无聊的名字 Workspace ONE，而且更难输入了。

话虽如此，它还是同一个产品，且是一个可靠的 MDM 解决方案。你必须选择要使用的 VMware Workspace ONE 版本。在 `www.vmware.com/products/workspace-one.html` 有一个中等长度的对比图表，但如果你深挖一下，点击“查看完整功能对比”时可以下载一个 PDF。

查看该表格时，有一行项目格外引人注目。“高级桌面管理”，标榜“包含自定义脚本、BitLocker 加密、桌面/Win32 应用管理、Windows 10 企业版策略（包括凭据保护/设备防护）”。而这些功能需要高级版、企业版和面向 VDI 的企业版。

由 Workspace ONE 管理的计算机在配置后也可以自动注册到 Azure AD。但如果你想试验 VMware Workspace ONE，Azure AD 并非严格必需。VMware 在 VMware Identity Manager 中也有自己的身份服务，你可以在此了解：`www.vmware.com/products/workspace-one/identity-manager.html`。

如果你想开始使用，截至撰写本文时，AirWatch 品牌正在过渡到 Workspace ONE。因此，当你阅读此书时，开始使用 AirWatch（即 Workspace ONE）的方式可能会有所不同。我设法找到了一个 30 天试用版：`www.air-watch.com/lp/free-trial/`。但随后试图寻找 Workspace ONE 试用版，我只找到了一个动手实验室，这也不错，但不是我真正想要的。无论如何，如果你愿意可以在这里试用：`https://www.vmware.com/go/workspace-hol`。

既然是一个沙箱式的动手实验室，我没有尝试将其连接到真实的 Azure AD，这可能行得通也可能行不通。将 Workspace ONE（该页面上仍称为 AirWatch）与 Azure AD 结合的分步说明可以在以下网址找到：`https://docs.microsoft.com/en-us/azure/active-directory/saas-apps/airwatch-tutorial`。

对我来说，我有一个 Workspace ONE 的完整账户，这将用于书中的任何示例。如果我没记错的话，你可以通过 VMware 经销商或客户经理获得自己的完整账户。

## MobileIron

MobileIron 的网站是这一堆里最令人困惑的。我花了一段时间才找到他们谈论 Windows 10 管理的页面。但我找到了，在这里：`www.mobileiron.com/en/unified-endpoint-management/operating-systems/windows-10`。

然后，如果你想开始 MobileIron 的 30 天试用，可以在这里进行：`https://info.mobileiron.com/30DayTrial`。

要将 MobileIron 连接到 Azure AD，完整的分步说明在 Microsoft 网站上：`https://docs.microsoft.com/en-us/azure/active-directory/saas-apps/mobileiron-tutorial`。

## 设置自动注册并注册你的第一批计算机

好的。让我们回顾一下：

*   你注册了一个免费的 Outlook 账户。
*   你注册了一个免费的 Enterprise Mobile Suite + Security E5 计划。
*   你同时获得了 Azure AD Premium P2。

现在是时候在你的 Azure AD 中开启 Intune 了。

首先完全退出所有内容：Outlook、Azure AD 和/或你可能打开的任何其他 Microsoft 服务。

然后，前往 `portal.office.com`，你可能会看到如图 2.6 所示的提示。选择带有 `.onmicrosoft.com` 地址的那个并登录。

![图 2.6 使用你的 onmicrosoft.com 账户登录。](img/c02f006.jpg)

**图 2.6** 使用你的 `onmicrosoft.com` 账户登录。

### 开启 MDM 注册

MDM 注册分两步：

*   用户
*   计算机

我们先做用户端，再做计算机端。

#### 用户的 MDM 注册

单击 Azure Active Directory，如图 2.7 所示。

![图 2.7 单击以打开 Azure Active Directory。](img/c02f007.jpg)

**图 2.7** 单击以打开 Azure Active Directory。

在新标签页中，你将看到 Azure AD，可以单击“移动性 (MDM 和 MAM)”，然后单击“Microsoft Intune”，如图 2.8 所示。接着，在出现的“配置 Microsoft Intune”对话框中，如图 2.9 所示，你特别需要启用 MDM 用户范围。对于我们的示例，我建议选择“所有”（也见图 2.9）。

![图 2.8 这是开启 Intune 的点击位置。](img/c02f008.jpg)

**图 2.8** 这是你单击以启用 Intune 的位置。

![图 2.9 启用 MDM，并可选择为所有用户启用 MAM。](img/c02f009.jpg)

**图 2.9** 启用 MDM，并可选择为所有用户启用 MAM。

然后，回到“移动性 (MDM 和 MAM)”页面（即再次看到 **图 2.8**），你将单击“Microsoft Intune 注册”。这将带你进入 **图 2.10** 所示的“Microsoft Intune 注册”页面。对于 MDM 用户范围，再次单击“全部”，然后单击“保存”。

![图 2.10 为 Intune 注册启用 MDM。](img/c02f010.jpg)

**图 2.10** 为 Intune 注册启用 MDM。

你刚刚配置的是 MDM 方程式的用户端。用户需要被提示确认使用条款等。

但真正的魔力在于设备。你需要配置设备注册颁发机构。

### 计算机的 MDM 注册

就在 10 秒前，你还在 Azure AD 控制台中。现在该进入 Intune 并告诉它你希望它接受请求并执行自动注册。

在撰写本文时，有三种方法可以进入 Intune。方法 1 是从主管理中心进入，如 **图 2.7** 所示。在管理中心内，你可以单击 Intune。

但如果你仍在 Azure 门户中，可能看不到指向 Intune 的链接。

我最喜欢的“转到 Intune”的方式就是如 **图 2.11** 所示进行搜索。只需单击搜索放大镜，输入 **Intune**，当它弹出时单击 Intune 这个词，就像我在 **图 2.11** 中所做的那样。

![图 2.11 如果你在 Azure 门户中迷路了，只需搜索 Intune。](img/c02f011.jpg)

**图 2.11** 如果你在 Azure 门户中迷路了，只需搜索 Intune。

所以，如果你迷路了只想去 Intune（或者你*找不到* Intune），请使用如 **图 2.11** 所示的放大镜。

搞定。

将 Intune 添加到 Azure 资源列表的另一种方法是单击“所有服务”（也可见于 **图 2.11**）。然后找到 Intune 并单击其旁边的星标。这将神奇地将其添加到左侧的长菜单列表中。这随后将其（基本上）放在每个页面上，使其更容易直接单击以跳转到 Intune。

### 关于 Intune UI 的一些注释和提示

我怀疑在未来几个月内，Intune 可能就会成为 Azure 主页上一个漂亮且易于查找的可点击项。在我写完这一章后，微软已经回过头来宣布了一个新页面的预览版，帮助你登录后更快地直达 Intune 和设备管理：`https://devicemanagement.microsoft.com`。

所以，请留意这一点。在本书付印前，我可能无法重新截取屏幕截图。

但同样，此处的方法应该继续与任何新方法一起工作。在本书后续内容中，我可能只会说“转到 Intune 控制台”，并假设你能找到去那里的路：从 Azure 门户、Azure 门户上一个巧妙的新图标（如果他们那样做的话），或 `https://devicemanagement.microsoft.com`。

此外，无关的是，当你在 Azure 或 Intune 中展开以执行某些有趣操作时，每个向右滑出的小窗口都有一个巧妙的名称。

它被称为 *blade*（边栏选项卡/刀片）。

这么说难道不觉得超酷吗？

再说一遍：*blade*。

不是窗口，不是窗格。不，不。那些术语太过时了。

现在它是 *blade*。

咳咳。好吧。当然。我就叫它 *blade*。

一旦进入 Intune，第一站将是“设备注册”，如 **图 2.12** 所示。这是你向 Intune 说明允许和不允许内容的地方。例如，如果你想允许 Apple 手机和 Windows 设备，但禁止 Android 设备，这就是正确的地方。

![图 2.12 在 Intune 中，使用“设备注册”来指定 MDM 颁发机构。](img/c02f012.jpg)

**图 2.12** 在 Intune 中，使用“设备注册”来指定 MDM 颁发机构。

然后，你将看到“选择 MDM 颁发机构”边栏选项卡，如 **图 2.13** 所示。只有当你以前从未执行过此步骤时，才会看到“选择 MDM 颁发机构”。

正确的选择选项是 Intune MDM 颁发机构，正如我在此处选择的那样。Configuration Manager MDM 颁发机构将启用所谓的混合 Intune + SCCM，且即将弃用。（我在 **第 4 章** 中详细讨论混合 Intune 和 SCCM、为何弃用以及什么取代了它。）

![图 2.13 选择 Intune MDM 颁发机构以管理设备。](img/c02f013.jpg)

**图 2.13** 选择 Intune MDM 颁发机构以管理设备。

![image](img/tip.jpg) 如果你想了解有关 MDM 颁发机构的更多信息，此处有一篇详细文章：`https://docs.microsoft.com/en-us/intune/mdm-authority-set`。例如，你稍后可能想将其设置为 SCCM 或其他 MDM 服务。

执行后，你将收到一条弹出通知，提示设置正确。

![image](img/note.jpg) 什么是 *toast*（弹出通知/吐司通知）？它就像一个弹出窗口。如果你从未听说过这个术语，请阅读此内容：`https://ux.stackexchange.com/questions/11998/what-is-a-toast-notification`。

### 将你的第一个用户添加到 Azure AD

手动将第一个用户添加到 Azure AD 只需片刻。
