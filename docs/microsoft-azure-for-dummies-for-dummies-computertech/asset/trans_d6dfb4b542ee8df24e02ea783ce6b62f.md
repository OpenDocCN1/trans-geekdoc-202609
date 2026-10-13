
您在此处只需提供相应的 Azure 订阅、资源组名称和区域。截至撰写本文时，Azure Arc 仅在选定区域可用。对此不必感到惊讶；Microsoft 会逐步推出预览功能，目标是到正式发布日期时产品在所有区域均可用。

4. **单击“创建”以提交部署。**

此操作应只需几秒钟即可完成。

### 将 Windows Server 系统添加到 Arc

您可以将基于 Windows 的服务器添加到 Arc 环境中。根据 Arc 文档，该服务支持运行 Windows Server 2012 R2 及更高版本的系统。

您无需 VPN 或 ExpressRoute 连接即可将服务器添加到 Azure。要让本地系统可由 Azure 管理，您只需安装一个代理。

请遵循以下步骤将 Windows Server 系统接入 Arc。当然，只有当您有可用的本地服务器时，才能执行这些步骤：

1. **在 Azure 门户中，搜索 `azure arc`。**

搜索结果包括 Azure Arc 和 Machines - Azure Arc（计算机 - Azure Arc）条目。

2. **单击第一个图标以查看完整产品。**

3. **在 Arc 欢迎页上，单击“管理服务器”。**

随即出现“Machines - Azure Arc”边栏选项卡。

![Remember](images/remember.png)截至撰写本文时，Kubernetes 和数据平台产品尚不可用。

4. **在“Machines - Azure Arc”边栏选项卡上，单击“添加”。**

随即出现“选择方法”边栏选项卡。

5. **在“选择方法”边栏选项卡上，单击“使用交互式脚本添加计算机”部分中的“生成脚本”按钮（请参阅[图 13-12](#c13.xhtml#c13-fig-0012)）。**

界面可能已*更改*，您看到的内容可能与[图 13-12](#c13.xhtml#c13-fig-0012) 不同；这是 Azure 不断发展的生态系统的本性。

单击此按钮后，将出现“生成脚本”边栏选项卡。

![Tip](images/tip.png)请阅读附近的边栏“[大规模添加服务器](#c13.xhtml#c13-fea-0002)”，了解有关其他 Arc 服务器接入方法的更多信息。

6. **在“生成脚本”边栏选项卡上，完成“基本信息”选项卡。**

选择您的订阅、资源组和区域；然后选择本地计算机的操作系统（Windows 或 Linux）。

![FIGURE 13-12: Choosing a server onboarding method for Arc.](images/9781119612148-fg1312.png)

[图 13-12：](#c13.xhtml#rc13-fig-0012) 为 Arc 选择服务器接入方法。

7. **单击“查看 + 生成”。**

随即出现“查看 + 生成”选项卡。

对于 Windows 计算机，您将看到以下脚本（如果 Microsoft 在本书出版后更新了代码，您可能会看到类似的脚本）：

```
# Download the package
Invoke-WebRequest -Uri https://aka.ms/AzureConnectedMachineAgent -OutFile AzureConnectedMachineAgent.msi
# Install the package
msiexec /i AzureConnectedMachineAgent.msi /l*v installationlog.txt /qn | Out-String
# Run connect command
& "$env:ProgramFiles\AzureConnectedMachineAgent\azcmagent.exe" connect --resource-group "AzureArc" --tenant-id "133f6972-44a7-4037-8eea-1d9afd1ebfc8" --location "westus2" --subscription-id "2fbf906e-1101-4bc0-b64f-adc44e462fff"
```

Azure 门户会根据您在部署过程中之前指定的环境详细信息，动态填充此 PowerShell 代码。

PowerShell 将完成以下三项任务：以 Microsoft Installer (`.msi`) 格式下载 Azure Connected Machine Agent，使用内置于 Windows 的 `msiexec` 命令行实用程序在您的系统上安装代理，并将本地系统链接到您的 Azure 订阅（总体上）和 Arc（特别是）。

8. **单击“下载”。**

9. **将接入脚本复制到目标系统。**

您直接在系统上运行该脚本。

10. **在目标系统上，通过打开“开始”、键入 `powershell`、右键单击 PowerShell 图标，并从快捷菜单中选择“以管理员身份运行”，启动一个提升权限的 PowerShell 控制台。**

随即出现一个管理员 PowerShell 控制台。

11. **暂时将脚本执行策略设置为 Bypass。**

出于安全原因，Windows 默认不运行所有 PowerShell 脚本。为确保您可以运行 Arc 接入脚本，请键入并运行以下命令：

```
Set-ExecutionPolicy -ExecutionPolicy Bypass -Scope Process -Force
```

此代码会在当前 PowerShell 会话期间放宽系统的脚本执行策略。

12. **运行脚本。**

您只需键入脚本文件的完整或限定路径。例如，如果您使用 `cd` 命令将命令提示符位置设置为与脚本文件相同的目录，则可以键入以下内容来运行脚本：

```
.\OnboardingScript.ps1
```

![Technical stuff](images/technicalstuff.png)在 Windows 和 Linux 系统上，指定*点斜杠*语法会指示计算机从当前工作目录运行脚本。

Arc for Servers 接入脚本会暂停并要求您向 Azure 进行身份验证。[图 13-13](#c13.xhtml#c13-fig-0013) 显示了设备登录过程。

![FIGURE 13-13: Onboarding a Windows Server system to Arc.](images/9781119612148-fg1313.png)

[图 13-13：](#c13.xhtml#rc13-fig-0013) 将 Windows Server 系统接入 Arc。

### 将 Linux 系统添加到 Arc

截至撰写本文时，Arc for Servers 仅支持 Ubuntu 16.04 和 18.04。请遵循以下步骤将 Linux 系统接入 Arc：

1. **在 Azure 门户中，搜索 `azure arc`。**

2. **在搜索结果中，选择“Machines - Azure Arc”图标。**

3. **在“Machines - Azure Arc”边栏选项卡上，单击“添加”。**

随即出现“选择方法”边栏选项卡。

4. **在“选择方法”边栏选项卡上，单击“生成脚本”。**

随即出现“生成脚本”边栏选项卡的“基本信息”选项卡。

5. **填写“基本信息”选项卡。**

请务必选择 Linux 作为目标操作系统。

6. **单击“查看 + 生成”，然后单击“下载”。**

以下代码是 `OnboardingScript.sh` Linux 接入脚本，它使用 Bash shell 语法而非 PowerShell 语法：

```
# Download the installation package
wget https://aka.ms/azcmagent -O ~/install_linux_azcmagent.sh
# Install the hybrid agent
bash ~/install_linux_azcmagent.sh
# Run connect command
azcmagent connect --resource-group "AzureArc" --tenant-id "133f6972-44a7-4037-8eea-1d9afd1ebfc8" --location "westus2" --subscription-id "2fbf906e-1101-4bc0-b64f-adc44e462fff"
```

Linux 代码执行以下三项操作：下载 Connected Machine Agent、安装它，然后将本地系统链接到您的 Arc 环境。

7. **将 `OnboardingScript.sh` 脚本传输到目标系统，并运行它以完成接入过程。**

在 Linux 系统上打开终端，浏览到复制 `OnboardingScript.sh` 脚本的目录，然后执行它。例如，如果您的终端命令提示符位于与脚本相同的目录中，请键入并运行以下 Bash 命令：

```
sudo sh ./OnboardingScript.sh
```

您需要在单独的浏览器窗口中输入一次性代码，以向 Azure 进行身份验证。

8. **代理安装完成后，返回 Azure 门户，并刷新“Machines - Azure Arc”边栏选项卡。**

正如您在[图 13-14](#c13.xhtml#c13-fig-0014) 中所见，您的 Arc 环境现在有两个托管的本地 VM。

![FIGURE 13-14: Viewing onboarded local VMs in the Azure portal.](images/9781119612148-fg1314.png)

[图 13-14：](#c13.xhtml#rc13-fig-0014) 在 Azure 门户中查看已接入的本地 VM。

### 使用 Arc 管理本地系统

现在是时候回答“使用 Arc for Servers 接入计算机后我能做什么？”这个问题了。截至撰写本文时，Arc for Servers 支持对已接入系统执行以下管理操作：

* 基于角色的访问控制 (RBAC)
* Azure Monitor
* 分类标记
* Azure Policy

#### 实施 Azure Policy
