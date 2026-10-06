
2. 点击“快速启动”（Quick Start），查看控制台已经发现并连接到你之前配置的本地 IPAM 服务器。这如图 5.5 所示。

# 图 5-4
服务器管理器中的 IPAM

![](img/41a83208e6906a3732620203b836cea7_218_0.png)

# 图 5-5
IPAM 管理

![](img/41a83208e6906a3732620203b836cea7_218_1.png)

3. 从“快速启动”菜单中点击“准备 IPAM 服务器”（Provision the IPAM server）以打开 IPAM 向导。

4. 快速阅读一遍“开始之前”（Before You Begin）对话框中的文本，点击“下一步”。
这将带你进入“配置数据库”（Configure Database）对话框，在其中你可以选择 Windows 内部数据库（Windows Internal Database）或 Microsoft SQL Server 作为你 IPAM 部署的数据库选项。在本例中，我们将保留默认的 Windows 内部数据库启用并点击“下一步”。

5. 在图 5.6 所示的“选择准备方法”（Select provisioning Method）对话框中，你需要从“手动”（Manual）或“基于组策略”（Group Policy Based）选项中进行选择。后者默认被选中，且这是推荐使用的选项。

在空字段中输入 GPO 名称前缀，然后点击“下一步”继续。

# 图 5.6
选择准备方法

![](img/41a83208e6906a3732620203b836cea7_219_0.png)

6. “摘要”（Summary）对话框向你展示了所选择的设置，在我们的示例中，它列出了将部署到你管理的 DHCP、DNS 和 NPS 服务器的 GPO。在点击“应用”之前，请注意！一旦点击“应用”，你将无法更改准备方法，如果你希望恢复到其他方法，将需要重新安装 IPAM。

当你对选择的准备方法满意时，点击“应用”。

7. 一旦 IPAM 准备配置成功完成，你可以点击“关闭”退出向导。

# 配置服务器发现

此时，你将看到信息已开始填充 IPAM 概览控制台，由于现在已选择了准备方法，你可以继续发现你的 DC、DNS 和 DHCP 服务器：

1. 从 IPAM 概览控制台，点击“开始”（Start）磁贴，然后点击“配置服务器发现”（Configure Server Discovery）。

在“配置服务器发现”框中，你应该能在“选择域”（Select Domains）下拉菜单下看到你的根域。

2. 点击“添加”（Add）按钮将此域列为发现你的 DC、DNS 和 DHCP 服务器的位置，如图 5.7 所示。

# 图 5-7
配置服务器发现

![](img/41a83208e6906a3732620203b836cea7_220_0.png)

3. 点击“确定”确认选择并返回 IPAM 概览控制台。

# 运行服务器发现

一旦你配置了想要管理服务器的域，就是时候让 IPAM 查找并审核它们了。完成此任务，你只需要点击 IPAM 概览控制台上“快速任务”（Quick Tasks）磁中的“启动服务器发现”（Start Server Discovery）选项。点击这将运行 `IPAMServerDiscovery` 任务，你可以从服务器管理器中点击信息标记以查看任务进的详情，如图 5.8 所示。

# 选择服务器进行管理

运行发现任务后，你可以选择通过 IPAM 管理你想要的哪些已发现服务器。要做到这一点，你首先需要从“快速启动”中点击“选择或添加服务器以管理并验证 IPAM 访问”（Select or Add Servers to Manage and Verify IPAM Access）选项。当你选择此选项时，你应该会在 IPv4 部分看到已发现的服务器，但你也会注意到它们的 IPAM 访问状态为“已阻止”（Blocked）或可管理状态为“未指定”（Unspecified），如图 5.9 所示。

# 第 5 章 IP 地址管理与 DHCP 故障转移

# 图 5.8
ServerDiscovery 任务详情

![](img/41a83208e6906a3732620203b836cea7_221_0.png)

# 图 5.9
被阻止的服务器

![](img/41a83208e6906a3732620203b836cea7_221_1.png)

不要慌；这是预期的默认行为，你需要使用 PowerShell 中的 `Invoke-IpamGpoProvisioning` 命令启动你创建的那些 GPO。要这样做，请执行以下步骤：

- 1. 从 IPAM 服务器确保你使用的是具有管理员权限的账户登录。
- 2. 使用“以管理员身份运行”选项打开 Windows PowerShell，以确保本地服务器上具有提升权限。
- 3. 现在使用以下命令并按回车（根据你自己的环境进行修改）：
  `Invoke-IpamGpoProvisioning -Domain Bigfirm.com -GpoPrefixName IPAMBF -DelegatedGouser administrator -IPServerFdn BF-IPAM1.bigfirm.com`
- 4. 你会被提示按 Y 确认选择，如图 5.10 所示。

# 图 5.10 调用 IPAM GPO

![](img/41a83208e6906a3732620203b836cea7_222_0.png)

该过程相对简单，一旦完成，你就可以通过 IPAM 控制台查看部署到你域的 GPO。你应该看到已部署的 GPO，如图 5.11 所示。

# 图 5.11
确认 GPO

![](img/41a83208e6906a3732620203b836cea7_222_1.png)

# 第 5 章 IP 地址管理与 DHCP 故障转移

- 6. 从 IPAM 控制台，通过各种视图管理某些 GPO。
- 7. 一旦 GPO 部署完成，返回“服务器清单”视图。
- 8. 从 IPAM 对话框，点击可管理性下拉菜单将其改为“已管理”。
- 9. 在发现完成后，右键点击你想要管理的服务器。
- 10. 一旦 GPO 部署完成，从右键菜单中选择“刷新”。
- 11. 在 IPv4 窗口中，你可以刷新服务器。
- 12. 一旦 IPAM 配置完成，点击“刷新”图标，如图 5.13 所示。

# 图 5.13
被阻止的服务器

![](img/41a83208e6906a3732620203b836cea7_224_0.png)

# 使用 IPAM

一旦你部署并配置了 IPAM，你就想知道如何使用它来管理 IP 地址。IPAM 控制台导航栏包含许多用于管理、监控和审核 IP 地址的的链接。这些选项如图 5.15 所示。在本节中，我们将通过各种视图讨论 IPAM 提供的某些功能场景。

图 5-15
IPAM 选项

| |
| --- |
| 概览 |
| 服务器清单 |
| IP 地址空间 |
| IP 块 |
| IP 地址清单 |
| IP 范围组 |
| 虚拟 IP 地址空间 |
| 监控与管理 |
| DNS 和 DHCP 服务器 |
| DHCP 范围 |
| DNS 区域监控 |
| 服务器组 |
| 事件目录 |
| 访问控制 |

