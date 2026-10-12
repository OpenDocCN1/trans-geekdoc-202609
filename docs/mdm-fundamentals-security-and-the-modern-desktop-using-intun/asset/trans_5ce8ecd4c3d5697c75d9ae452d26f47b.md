

## 参考资源

*   `https://docs.microsoft.com/en-us/intune/windows-update-for-business-configure`
*   关于 WUfB 和 MDM 的优秀博客文章：`https://www.petervanderwoude.nl/post/easily-configuring-windows-update-for-business-via-windows-10-mdm/`
*   Windows 10 服务通道名称变更说明（SAC 与 SAC-T 术语已废弃）：`https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/Windows-Update-for-Business-and-the-retirement-of-SAC-T/ba-p/339523`
*   详细推出指南和官方文档：`https://docs.microsoft.com/en-us/windows/deployment/update/index`

总而言之，你的目标是使用组策略或 MDM（二选一，切勿同时使用）向大量计算机指明：在执行自动升级时应使用哪个服务通道、延迟接收更新多少天以及活动时段。

## 使用管理模板控制 Office 365 通道

类似于使用 WUfB 设置控制计算机获取哪个 Windows 通道，你也将为 Office 365 ProPlus 执行类似操作。

这些设置同时存在于组策略和 MDM 中。

### 组策略中的设置

在组策略中，当你将组策略存储（本地或中央存储）更新为最新的 Office ADMX 文件时即可找到这些设置。（上次检查 URL 为 `www.microsoft.com/en-us/download/details.aspx?id=49030`，但建议在页面中搜索“Administrative Template files (ADMX/ADML) and Office Customization Tool for Office 365 ProPlus, Office 2019, and Office 2016”。）更新存储后，所需的 Office 策略位于：`计算机配置` ➢ `策略` ➢ `管理模板` ➢ `Microsoft Office 2016 (Machine)` ➢ `更新`。关键的组策略设置是 **Update Channel**（更新通道），如图 9.4 所示。

![图 9.4 Office 更新通道组策略设置](images/c09f004.jpg)

**图 9.4** Office **Update Channel** 组策略设置

其他设置记录于此：`https://docs.microsoft.com/en-us/deployoffice/configure-update-settings-for-office-365-proplus`

### MDM 中的设置

在 MDM 中，这些设置配置为 ADMX 支持的策略设置。在 Intune 中，这些相同设置位于管理模板部分，非常方便，无需自行摸索自定义 URI。起始步骤：转到 `Intune` ➢ `设备配置配置文件` ➢ `创建配置文件`。命名，选择平台为 `Windows 10 and later`，配置文件类型选择 `Administrative Templates`。

然后在设置中，查找并选择名为 **Update Channel** 的策略。可看到如图 9.5 所示的 MDM 管理模板设置。

![图 9.5 Intune 管理模板设置](images/c09f005.jpg)

**图 9.5** Intune 管理模板设置

随后，将配置文件分配给目标计算机。

搞定，很简单。

包含故障排除步骤的优秀博客文章（关于通过 Intune 管理模板设置管理 Office 设置）：`https://www.petervanderwoude.nl/post/easily-controlling-the-office-update-channel-by-using-administrative-templates/`

## Office 和应用程序就绪

Windows 10 与旧版 Windows 的整体兼容性无与伦比。很少有人会说：“我有个旧的 Windows XP 应用程序，该死的东西拒绝在 Windows 10 上启动。” 虽然会发生，但很少见。以下是该领域最常见的两种情况：

*   “我的系统级软件（防病毒、安全软件或 VPN 软件）不想在 Windows 10 上工作。”
*   “我尝试以标准用户身份启动这个旧的 BrainScan 12.0 应用（供应商已倒闭），它却提示我输入 UAC 凭据。”

是的，这些情况确实经常发生。

![提示](images/tip.jpg) 为克服棘手应用程序的 UAC 提示，请查看 PolicyPak Least Privilege Manager：`www.policypak.com/products/least-privilege-manager.html`。它适用于组策略或 MDM。（我们将在接下来的两章中略微探讨 PolicyPak Least Privilege Manager，但不会深入。）

但总体而言，应用程序一旦启动，Windows 10 兼容性相当不错。微软也言出必行。如果你有超过 500 台计算机，可以利用微软的资源通过 Desktop App Assure 计划解决桌面兼容性问题。详情请阅读 AppCompat 专家 Chris Jackson 的文章：`https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/What-is-Desktop-App-Assure/ba-p/270232`

另一个有趣的资源是 [readyforwindows.com](http://readyforwindows.com)，你可以输入产品名称，查看你的应用程序是否被列为“Supported on Windows 10”。

话虽如此，我想介绍两个工具帮助你为 Office 365 和 Windows 10 做好准备。嘿，也许你已经在使用 Office 365 和 Windows 10 了。

那很酷。还是运行这些工具以获取见解吧。

让我们从 Office 开始，然后回溯到应用程序。

### Office 365 就绪工具包

Office 365 就绪工具包的任务是：在单台计算机上手动运行，或通过脚本在多台计算机上运行，返回一份漂亮的电子表格，列出包含 VBA 宏和需要关注的 Office 外接程序的文档。

为什么需要知道这些？因为你可能已有一大批运行旧版 MSI 版 Office 的计算机，想切换到具有（不同的）即点即运安装程序的 Office 365 ProPlus。你需要知道今天使用的内容明天能否在新版 Office 中正常工作。

Office 365 就绪工具包完整文档：`https://docs.microsoft.com/en-us/DeployOffice/use-the-readiness-toolkit-to-assess-application-compatibility-for-office-365-pro`

工具包实际下载地址：`https://www.microsoft.com/en-us/download/details.aspx?id=55983`

我仅快速演示一下该工具。如前所述，你可以在单台计算机上手动运行以快速获取见解。这是我在自己的计算机上运行的结果。在现实世界中，你会运行脚本版本以跨多台计算机收集详细信息。

图 9.6 展示了运行就绪工具包时的情况。

![图 9.6 运行 Office 就绪工具包](images/c09f006.jpg)

**图 9.6** 运行 Office 就绪工具包

随后，你将选择报告位置，如图 9.7 所示。

![图 9.7 选择报告位置和其他选项](images/c09f007.jpg)

**图 9.7** 选择报告位置和其他选项

下一屏幕如图 9.8 所示。为了获得最有用的数据，你需要询问 Microsoft 你拥有的外接程序或宏是否会有问题。只有选择加入与 Microsoft 共享发现数据，工具才能告诉你结果。

![图 9.8 高级报告将数据发送给 Microsoft 以评估计算机数据](images/c09f008.jpg)

**图 9.8** 高级报告将数据发送给 Microsoft 以评估计算机数据

随后工具开始工作，如图 9.9 所示。

![图 9.9 就绪工具包开始创建报告](images/c09f009.jpg)

