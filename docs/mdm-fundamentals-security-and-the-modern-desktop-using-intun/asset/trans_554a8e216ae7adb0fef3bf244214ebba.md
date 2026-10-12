
教师随后可以连接 Internet，根据需要下载并运行软件。如果该软件需要本地管理员权限才能完全安装，您可以使用 `PolicyPak Least Privilege Manager` 创建规则来绕过 UAC 提示。

软件由教师安装，因此教师成为文件的所有者。

软件安装完成后，教师注销。

当学生登录时，软件即可运行，因为教师已妥善安装了软件，并在安装过程中写入了文件，成为这些文件的所有者。此外，教师在“可信列表”中。

因此，许多人喜爱 `PolicyPak SecureRun™`，因为它会自动阻止以下类型的文件：

*   `.MSIs`
*   `.EXEs`
*   `.JAR` (Java 文件)
*   `.PS1` (PowerShell 脚本)
*   `.BAT`
*   `.CMD`
*   `.JS`
*   `.JSE`
*   `.VBS`
*   `.VBE`
*   `.PS1`

要全面了解 `PolicyPak SecureRun™`，您需要观看相关视频。如果您有时间，以下是三个最佳链接：

*   [https://www.policypak.com/video/stop-cryptolocker-and-other-unknown-zero-day-attacks-with-policypak-secureruntm.html](https://www.policypak.com/video/stop-cryptolocker-and-other-unknown-zero-day-attacks-with-policypak-secureruntm.html)
*   [https://www.policypak.com/video/policypak-application-control-with-pp-least-privilege-manager.html](https://www.policypak.com/video/policypak-application-control-with-pp-least-privilege-manager.html)
*   [https://www.policypak.com/video/policypak-mdm-using-least-privilege-managers-securerun-feature.html](https://www.policypak.com/video/policypak-mdm-using-least-privilege-managers-securerun-feature.html)

关于 `PolicyPak MDM` 的更多通用信息（如如何安装、创建规则并将其上传到 MDM）将在下一章介绍。

## 条件访问

在上一章中，我们使用 Intune 的合规性策略来定义合规性的标准。机器是否需要启用 BitLocker？是否需要启用防火墙？是否需要运行特定版本或更高版本的 Windows？

这些只是问题。如果您想在答案不符合预期时采取行动，这就是条件访问，它是 Azure 的一部分。

条件访问包含多个活动部件，如[图 10.30](#c10.xhtml#figure10-30)所示。

1.  **Windows 10 本身**将与 `System Guard Runtime Attestation (SGRA)` 核对，查看是否有任何项目不符合您期望的标准。
2.  **SGRA（可选）**挂钩 `Windows Defender ATP`（本章后面将解释），这是一个附加安全产品。该产品可以增加健康和/或风险行为信号。部分风险等级在此处评估。
3.  如果未发现机器有风险，则由您的 **Intune 合规性策略** 进行评估（我们在上一章中探讨过）。
4.  根据您设置的所有策略，合规性状态为“合规”或“不合规”。
5.  如果状态为“合规”，机器能够访问 Azure AD 资源（如 Office 365）和/或任何其他 Azure AD 连接的资源。如果状态为“不合规”，您指定的资源将被阻止。

现在让我们看看如何设置 Azure 条件访问。

![Figure 10.30 Windows 10 with internal and external security components](images/c10f030.jpg)

**图 10.30** Windows 10 与内部和外部安全组件

### 设置 Azure 条件访问

Azure 条件访问的第一部分根本不在 Azure 中。

它在 Intune 中。我假设您已在上一章中创建了一个或两个 Intune 合规性策略。在上一章中，您应具有如下 Intune 合规性策略：

*   计算机未启用 BitLocker。
*   计算机未启用防火墙。

完成所有设置后，是时候收紧控制，将 Intune 的合规性策略连接到 Azure 的条件访问了。

在 Azure 中，单击“条件访问”，如[图 10.31](#c10.xhtml#figure10-31)所示。

![Figure 10.31 Kicking off Azure conditional access](images/c10f031.jpg)

**图 10.31** 启动 Azure 条件访问

在“条件访问”页面上，单击“新建策略”以开始。然后，如[图 10.32](#c10.xhtml#figure10-32)所示，添加您的第一个条件访问策略，名称如“Azure Cond Access Policy 1”。

![Figure 10.32 Creating a conditional access Policy](images/c10f032.jpg)

**图 10.32** 创建条件访问策略

在条件访问策略中，您将看到以下部分：

*   用户和组
*   云应用
*   条件
*   授予
*   会话

我们将在此处探讨这些部分。

请记住条件访问的要点：如果不遵守您在 Intune 中设置的标准，Azure 将执行阻碍用户操作的“脏活”。

#### 分配：用户和组、云应用和条件

在“用户和组”中，您需要准确指定谁必须遵守您创建的第一个策略。

建议您为首次尝试指定一个非常具体的单个用户，如 `Jack Tors`。您可以看到我在[图 10.33](#c10.xhtml#figure10-33)中添加 `Jack Tors` 作为单个用户。很容易创建一个阻止“所有用户”的访问策略，然后……哦 <faceplant>！您刚刚把自己（管理员）锁在了 Azure 和 Intune 之外。

![image](images/note.jpg) 关于被这样锁定的亲身经历（以及恢复之路），请查看 [https://www.itpromentor.com/conditional-access-misadventures/](https://www.itpromentor.com/conditional-access-misadventures/)。

![Figure 10.33 Use Jack Tors as your single user to have the policy apply to.](images/c10f033.jpg)

**图 10.33** 使用 Jack Tors 作为策略应用对象的单个用户

请注意，条件访问策略还允许您尝试定位一些特殊组，如“所有来宾用户”（包括来自其他 Azure 租户的人员）和“目录角色”，您可以在其中要求（例如）所有服务台人员和管理员登录时进行双因素身份验证。

接下来，您将单击“云应用”部分。这是您指定要阻止的应用程序的地方。这很奇怪，因为正如您在[图 10.34](#c10.xhtml#figure10-34)中所见，您位于“包含”选项卡中。因此，您是*包含*您想要*阻止*的项目。

选择 `Office 365 Exchange Online`，这将阻止访问 Office 等 Web 服务项目。您也可以选择 `Office 365 SharePoint Online`，这将阻止访问 SharePoint 和 OneDrive 等 Web 服务项目。在[图 10.34](#c10.xhtml#figure10-34)中，我选择了这两项，但您也可以只用一项进行测试。

![Figure 10.34 Picking the cloud apps to block when noncompliance is detected](images/c10f034.jpg)

**图 10.34** 检测到不合规时选择要阻止的云应用

然后在“条件”中，您将选择何时应用此策略。为保持简单，单击“客户端应用”，选择“配置”，然后保留所有默认值，如[图 10.35](#c10.xhtml#figure10-35)所示。在我们的测试示例中，我们将对浏览器实施限制，但为稳妥起见保留所有默认值。

![Figure 10.35 Expressing which client apps will adhere to this policy](images/c10f035.jpg)

**图 10.35** 表示哪些客户端应用将遵守此策略

#### 访问控制：授予和会话

下一个主要部分是“访问控制”，包含“授予”和“会话”（见[图 10.36](#c10.xhtml#figure10-36)）。

“授予”设置见[图 10.36](#c10.xhtml#figure10-36)，同样违反直觉。

在此上下文中，“阻止访问”设置基本上意味着“不执行任何操作”。

而是“授予访问权限”连接到您想要强制用户遵守的内容。我们要表达的是：当机器不合规时，我们要阻止访问。因此，正确的复选框是“要求设备标记为合规”。
