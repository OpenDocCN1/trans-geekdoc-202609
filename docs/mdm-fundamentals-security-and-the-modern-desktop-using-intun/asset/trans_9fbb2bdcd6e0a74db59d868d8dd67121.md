

## 使用共享计算机激活

如果你有在不同计算机间漫游的用户，此选项适合你。包含 Microsoft 对所有这些设置描述的页面位于 `https://docs.microsoft.com/en-us/DeployOffice/overview-of-shared-computer-activation-for-office-365-proplus`。

此处有许多关于共享许可令牌的详细信息、30 天无人登录会发生什么情况，以及你想了解的其他详细信息。

## 语言

Office 将升级为计算机上已安装的语言（如果有）或操作系统语言。如果需要，你可以在此处添加其他语言。

你可以在 [图 6.44](#c06.xhtml#figure6-44) 中查看我的设置。

![图 6.44 Office 应用套件设置边栏选项卡](images/c06f044.jpg)

[**图 6.44**](#c06.xhtml#figureanchor6-44) Office 应用套件设置边栏选项卡

除此之外没什么更多内容了，这是一个不错的节奏变化。

正如你所见，缺少的是使其更加定制化的能力。例如，你可能想要卸载终结点上的每一个旧版 Office 应用程序，但保留 Access 97，以免会计部门抓狂。

就写作时而言，你无法做到这一点。没有方法让 Intune 了解这是你想要的。但我有理由相信，等到你阅读此文时，你将具备向 Intune 提供 Office 配置 XML 以执行特殊操作的能力。请参阅标题为“Office 部署工具和 Office 策略配置工具”的边栏。

获得配置文件后，将其分配给用户或计算机，然后……等待奇迹发生。在我的示例中，我可以看到 Word 和 Excel 已添加到 Windows 10“开始”菜单（如 [图 6.45](#c06.xhtml#figure6-45) 所示），以及“设置”➢“应用和功能”（或“控制面板”中较旧的“添加/删除程序”）中。

![图 6.45 同步后，稍等片刻，Office 将根据你的规范进行安装。](images/c06f045.jpg)

[**图 6.45**](#c06.xhtml#figureanchor6-45) 同步后，稍等片刻，Office 将根据你的规范进行安装。

然而，我在设置报告（基本或高级）中未注意到任何通过 MDM 安装 Office 的迹象。也许这将在未来的 Windows MDM 报告更新中出现，但我真的不清楚。

但是，你可以看到安装留下的一些线索。一处去向是终结点的注册表（以管理员身份），查看 `HKLM\Software\Microsoft\OfficeCSP\` 并检查其中的任何内容。这是我的样子：

![](images/c06uf015.jpg)

在我的示例中，我有两个带有 GUID 的项，在这些项中有一些值。

我在此高亮显示的项显示了三件事：

### Default（默认）

如果你查看内部，将看到安装软件时使用的所有参数，如发布渠道、版本、用于 `RemoveMSI` 的标志等。复制粘贴在此以便你了解我的意思，如下所示：

```
<Configuration><Add Channel="FirstReleaseDeferred" ForceUpgrade="TRUE"
 OfficeClientEdition="64"><Product ID="O365ProPlusRetail">
<ExcludeApp ID="Access" /><ExcludeApp ID="Groove" />
<ExcludeApp ID="InfoPath" /><ExcludeApp ID="Lync" />
<ExcludeApp ID="OneNote" /><ExcludeApp ID="Outlook" />
<ExcludeApp ID="PowerPoint" /><ExcludeApp ID="Publisher" />
<ExcludeApp ID="SharePointDesigner" /><Language ID="MatchOS" />
</Product></Add><Display Level="None" AcceptEULA="TRUE" />
<RemoveMSI All="TRUE" /><Property Name="SharedComputerLicensing" Value="1" />
<LastExecuteTime>1/1/2019 3:50:15 AM</LastExecuteTime></Configuration>
```

### Status（状态）

我的状态是 0。这通常意味着“良好”或无错误。

### FinalStatus（最终状态）

我的最终状态是 70，大家都知道这意味着“成功”。

等等。你是说你不知道错误代码 70 意味着成功？

好吧。我也不知道。但我查看了 Office CSP，代码就在那里！其他错误和状态代码也可以在该页面找到，如果你想知道为什么事情失败或未按预期安装，这非常有用。

该参考页面位于 `https://docs.microsoft.com/en-us/windows/client-management/mdm/office-csp`。

## Office 部署工具和 Office 策略配置工具

Office 配置正走向云端。

分两部分：

*   创建 XML 以操作 Office 配置的方式
*   可能设置策略设置的方式

首先我们来谈谈创建 Office XML 配置文件。现在工具在线上，位于 `https://config.office.com/`，你无需下载部署工具，然后把 XML 文件折腾半天。你可以从头开始进行自定义，或导入现有文件，完成后导出这些自定义项。你可以在此处查看 Office 自定义工具。

![](images/c06uf016.jpg)

截至目前，此工具仅能配置 Office 2019，因为只有 Office 2019 支持传递 XML 文件。对于搭配 Intune 的 Office 365，目前无法做到这一点——“目前”是关键词。

你所需的配置 Office 的大多数 UI 已经在 Microsoft Intune 中。它不是*所有*花哨功能，但包含相当多。对于剩余的怪癖，你应该（很快）能够使用此工具制作 Office XML，然后将 XML 文件传递给 Intune。

第二个云端 Office 工具是 Office 客户端策略服务，简称 OCPS。OCPS 适用于加入域和未加入域的计算机，无论是否有 MDM。基本上，这是一种为你控制的任何 Office 集中创建和管理 Office 策略的方式。要访问 OCPS，你的 Azure 租户需要 Office 365 专业增强版，并且必须使用全局管理员、安全管理员或桌面分析管理员凭据登录。（如果你在没有 Office 365 专业增强版订阅的情况下尝试此操作，将收到一个无差别错误消息。）

OCPS 位于 `https://config.office.com/officesettings`。当你到达那里时，你可以选择一个 Azure AD 组（如图所示），然后选择一些要配置的策略。

![](images/c06uf017.jpg)

现在，你控制范围内任何地方运行 Office 365 的计算机只需“回访”并检查策略（使用 Office 本身检查更新的相同机制）。它将每 90 分钟检查一次。端口和 URL 记录在 `https://docs.microsoft.com/en-us/office365/enterprise/urls-and-ip-address-ranges`（只需查找“Office 策略管理”）。

另请注意，如果 OCPS 与组策略发生冲突，则 OCPS 胜出。

请注意，目前 OCPS 中并非包含所有设置，仅包含用户端项目，且仅限具有基本值的用户端项目。

OCPS 仅适用于 Office 365，不适用于 Office 2019 等批量许可版本的 Office。对于这些版本的 Office，你仍需使用 Office 自定义工具和 XML 文件。

最后，如果你想了解更多关于以传统方式部署 Office 2019（相对于通过 Windows Intune 部署 Office 365）的信息，以下是资源：

*   **YouTube：** What's new in Microsoft Office 2019 for IT deployment - BRK3260
*   `https://docs.microsoft.com/en-us/deployoffice/office2019/deploy`
*   `https://config.office.com/`

如果你想了解更多关于 Office 客户端策略服务的信息（附带一个不错的视频），请查看：

`https://techcommunity.microsoft.com/t5/Office-365-Blog/Announcing-the-new-cloud-based-policy-management-service-for/ba-p/310405`

官方文档位于：

`https://docs.microsoft.com/en-us/deployoffice/overview-office-client-policy-service`

## 使用 MDM 部署 Win32 应用

每年 Microsoft 都会针对 Intune 发布重大公告。在 2018 年 Ignite 大会上，Microsoft 的重大公告是能够使用 Intune 部署 .EXE 和复杂的 MSI，Microsoft 统称之为 Win32 应用程序。

