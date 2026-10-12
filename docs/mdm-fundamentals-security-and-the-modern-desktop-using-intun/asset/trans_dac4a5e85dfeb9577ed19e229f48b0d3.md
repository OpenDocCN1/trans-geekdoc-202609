
Autopilot 和 Intune 随后将相互通信，但仅针对这个特定组。在它们完成“讨论”（无论两个云服务聊些什么）后，目标是获取动态组中的计算机，读取其硬件 ID，并将它们传送到 Autopilot。

然后，如果这些计算机将来确实需要被**彻底清除**，那你就手握王牌，因为计算机的硬件 ID 已经在 Autopilot 中了！

在未来的某个时刻，组中的机器被**彻底清除**，经历 OOBE（开箱即用体验），然后 Autopilot 接管并回答所有 OOBE 问题。

正如预期的那样，这个握手过程可能需要一些时间。我等了一整晚，但可能会更快。一段时间后，你应该会在 Autopilot 中看到符合条件的新设备出现。在我的例子中，名称中包含 `Computer` 的计算机是那些已注册到我的 Intune MDM 的设备。

在“Windows Autopilot 设备”边栏选项卡中进行同步和刷新后，你可以在[图 8.35](#c08.xhtml#figure8-35)中看到结果。

![Figure 8.34 Converting targeting devices for Autopilot.](images/c08f034.jpg)

[**图 8.34**](#c08.xhtml#figureanchor8-34) 将目标设备转换为 Autopilot 设备。

![Figure 8.35 Seeing newly imported devices in Autopilot](images/c08f035.jpg)

[**图 8.35**](#c08.xhtml#figureanchor8-35) 在 Autopilot 中查看新导入的设备

### Autopilot：重置、退役、擦除和全新开始

机器。变慢。随时间。结束。

我最喜欢的术语是 `Winrot`。嘿，它都收录进《都市词典》了（`www.urbandictionary.com/define.php?term=Winrot`），所以它肯定是个真存在的东西，对吧？

你可以实施各种类型的重置，将机器恢复到基准状态，然后让它从 MDM 服务重新获取所有内容。你可能想要重置计算机的其他原因。最常见的是在学期末重置教室电脑，或者当你借给学生备用电脑而完全不知道他们对电脑做了什么时。然后当学期或暑假结束时，你只需对机器发起大规模重置，搞定：全新安装。

此外，机器可能会丢失。Sally 又把笔记本电脑落在 Uber 后座上了！？？是时候直接“从天而降地核平它了！！”

所以在接下来的章节中，我们将了解“重置、退役、擦除和全新开始”。

#### Autopilot 重置：本地重置和远程重置

Autopilot 重置有两种类型：本地重置和远程重置。

这两种重置类型的要旨相同，提供的优势也相同。以下是发生情况的基础知识：

*   所有应用、设置和个人文件均被**彻底清除**。如果不在网络或外部磁盘上，就被**彻底清除**。
*   Azure AD 加入和 MDM 注册得以保留并重用。换句话说，当此过程结束时，你不会在 AD 或 MDM 中看到另一条幽灵记录。
*   如果你碰巧使用配置设计器应用了预配包，那些设置将被保留。
*   语言和键盘设置得以保留。
*   Wi-Fi 设置及任何预先已知和存储的密码得以保留。

**本地 Autopilot 重置** 这不会执行完整的 OOBE 重置。它会丢弃所有应用和数据。它还将保留 MDM 注册、Azure AD 加入和语言。

这在学校场景中非常棒，你只想**彻底清除**那些顽皮孩子弄脏的机器，并将机器恢复到基线。

然后它将重新连接到 MDM，获取任何新内容以重新加载或下载。

但你可能也想走到机器前执行此本地重置。这通过在登录屏幕按下 `Windows+Ctrl+R` 组合键启动，除非它首先被 MDM 启用，否则不会生效。

在 Intune 中，你会在“设备限制”>“常规”下找到名为“自动重新部署”的设置，如图所示。（别忘了将配置文件关联到计算机组。）

![](images/c08uf008.jpg)

![image](images/tip.jpg) 这实际上是设置 PolicyCsp，即 `PolicyCSP/CredentialProviders/DisableAutomaticReDeploymentCredentials`，并将其设置为 1。你可能需要此信息进行故障排除，或者如果你的 MDM 服务不是 Intune，需要手动设置此项。

然后尝试一下：在登录屏幕，按下 `Windows+Ctrl+R`。然后当你提供管理员凭据（本地或 Azure）时，如[图 8.36](#c08.xhtml#figure8-36)所示，机器将立即开始重置。

**远程 Autopilot 重置** 另一种选择是从舒适的控制台，通过互联网远程**彻底清除**一台或多台机器。

片刻间，你会感觉自己像“邪恶博士”一样。

那么，怎么做？使用 Intune 的“设备”>“所有设备”并点击该设备。选择“更多”，然后找到 Autopilot 重置，如[图 8.37](#c08.xhtml#figure8-37)中标记 (1) 所示。

![Figure 8.36 Use Windows+Ctrl+R at the login screen to start a reset there.](images/c08f036.jpg)

[**图 8.36**](#c08.xhtml#figureanchor8-36) 在登录屏幕使用 Windows+Ctrl+R 开始重置。

![Figure 8.37 The different kinds of wipes and resets in Intune](images/c08f037.jpg)

[**图 8.37**](#c08.xhtml#figureanchor8-37) Intune 中不同种类的擦除和重置

请注意，Autopilot 重置需要 Windows 1809 或更高版本；如果你看到此选项灰显，意味着该机器不太可能是 Windows 1809 或更高版本。

当你远程重置 PC 时，你会收到一条已启动的通知，如下所示：

![](images/c08uf009.jpg)

然后，在终端上，最终用户将收到如下消息：

![](images/c08uf010.jpg)

机器将在 45 分钟内重启并完全重置，然后重新加入 Autopilot。

最终用户不会获得开箱即用体验 (OOBE)；它直接就绪，因为它保留了 MDM 注册。

然后当机器完成时，最终用户看到正常的登录页面。但在你按下 `Ctrl+Alt+Del` 之前，用非常非常小的字母，你会看到“成功！Windows 已设置并准备就绪。”如果你眯着眼看，会看到此处显示的内容。

![](images/c08uf011.jpg)

#### 退役 PC

退役按钮可见于[图 8.37](#c08.xhtml#figure8-37)，标记为 (2)。

退役 PC 基本上将其从 Intune 中移除。这**不会**擦除 PC。你只是在 Intune 中看不到它了，因为你不再管理它。机器上的任何 MDM 策略被移除；一些设置会回退，其他可能会保留。机器上的软件通常会保留。存储在设备上的用户个人数据将保留。

#### 擦除 PC（以前称为 `Factory Reset`）

擦除按钮可见于图 8.37，标记为 (3)。

MDM 擦除功能有两种方法：保留注册状态和用户帐户……或不保留。为简单起见，我称之为“擦除+保留”和“擦除-不保留”。

在这两种情况下，擦除都将移除用户帐户、用户数据、用户安装的应用、OEM 预装应用，并将操作系统重置为默认值。

擦除+保留将保留 Intune 注册。

擦除-不保留将移除 Intune 注册（但如果设备的硬件 ID 在 Autopilot 中，它可能会被重新注册）。

关于此功能的文档位于 `https://docs.microsoft.com/en-us/intune/devices-wipe`。

#### MDM 全新开始（又称 Clean PC）

全新开始按钮可见于[图 8.37](#c08.xhtml#figure8-37)，标记为 (4)。

这是一种**小范围清除**机器的方式，但不彻底。你可以在 Intune 的“设备”>“所有设备”中看到全新开始。

全新开始（也称为 Clean PC）将移除机器上的任何 Win32 或 UWP 应用程序，并将其升级到最新版本的 Windows。可以指示设备保留（或**清除**）用户数据。

而且，如果你选择*不*保留用户数据，实际上也会将其从 Azure AD 和 MDM 服务中取消注册，所以使用此功能时要小心。

只有设备在 Autopilot 中已建立，它才会神奇地重新连接并仍由 MDM 管理。
