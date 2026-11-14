
# Armitage 渗透测试教程

## 启动终端并检查 IP

![](rsrcKM.jpg)你保存、关闭窗口，然后从开始菜单输入命令 `cmd` 以启动终端。终端启动后，输入命令 `ipconfig`，这将显示受害者 IP 的相关信息。

## 启动 Armitage 并执行深度扫描

![](rsrcKN.jpg)返回 Kali Linux 虚拟机将启动 `armitage` 工具。如图所示，选择 `Intense Scan`（深度扫描）项，这将允许你扫描连接到网络的所有设备。此扫描将使用集成在 `Armitage` 中的 `Nmap` 工具完成。

## 设置 IP 范围

![](rsrcKP.jpg)将出现下图，其中将设置要搜索的 IP 地址范围。在本例中，范围从 `192.168.1.100` 到 `192.168.1.200`。

## 扫描受害者设备

![](rsrcKR.jpg)扫描完成后，将显示所有连接到网络的设备，在某些情况下，也会显示连接设备的操作系统。 ![](rsrcKS.jpg)转到受害者的设备（本例中为 Windows），用鼠标右键点击可选择 `Scan`（扫描）项，这将分析该操作系统的所有服务和开放端口。

## 扫描服务并识别端口 445

![](rsrcKT.jpg)扫描完成后，你移动到下方菜单中的 `Service`（服务）项，在那里你可以扫描受害者机器的所有开放端口。将要使用的端口是 `445`，它指的是 `SAMBA` 服务。 ![](rsrcKU.jpg)在顶部侧边菜单中，你必须依次打开 `exploit`、`windows` 最后是 `smb`。

## 利用 SMB 漏洞

![](rsrcKV.jpg)![](rsrcKW.jpg)![](rsrcKX.jpg)与 `SAMBA` 服务相关的攻击类型如图所示。你需要双击它，将出现一个进一步的配置窗口，你只需勾选 `use a reverse connection`（使用反向连接）标志并点击 `launch`（启动）。

## 获取 Shell 访问权限

![](rsrcKY.jpg)片刻后，系统将以红色显示。点击它可以选择 `Shell1` 和 `Interact`（交互），这将使你获得受害者系统的 Shell 访问权限。 ![](rsrcKZ.jpg)![](rsrcKZ.jpg)下图显示的是受控主机的 Shell。

# OpenVAS 漏洞分析

## 概述

**OpenVAS** 是一个复杂的程序，由一个服务器组成，多个客户端可连接到该服务器以执行漏洞分析。在前面的示例中已分析了两个与渗透测试相关的工具。其基础是两个守护进程，一个管理器 (`openvasmd`) 和一个扫描器 (`openvassd`)，可以远程连接到它们以执行管理操作（例如证书创建）以及扫描主机或受害者网络。要连接并指示分析，可以使用 `Greenbone Security Desktop`，或在启动适当的 Web 封装器（如 `Greenbone Security Assistant`）后使用 Web 界面。该工具非常易于使用，我们将使用 `Parrot` 操作系统（一种类似于 `Kali Linux` 的安全系统）来安装它。选择该操作系统是因为它提供了安装命令，使一切变得非常简单直观。为了生成 PDF 报告，需要先执行一些初步操作，以便系统能够处理此类文件。你必须打开终端并输入以下命令：

```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install texlive-latex-base
sudo apt-get install texlive-latex-extra
```

## 初始设置

在虚拟机上下载并安装 `Parrot` 后，只需启动它。如图所示，打开 OpenVas 条目并点击 `openvas initial setup`。 ![](rsrcM0.jpg)将出现一个类似于下图的屏幕，我们需要在其中输入密码；通常默认密码是 `toor`，但如果它进入桌面，将会有一个包含要使用密码的文本文件。

输入密码后，你必须等待安装完成，这将花费相当长的时间。

安装完成后，我们必须复制包括分隔符 (`-`) 在内的所有代码，这将是访问程序的密码 (`1d7a51b76993-4b6d-9ed9-b1ed09fb427a`)。复制并保存此密码至关重要。要完成安装，请再次输入用户密码（在本例中为默认密码，即 `toor`）。 ![](rsrcM1.jpg)密码稍后将被更改。

## 订阅源更新与验证

在启动 OpenVas 之前，你必须重复之前的操作，即转到 OpenVas 项并点击 `feed update`，这将更新用于搜索漏洞的数据库。同样在这种情况下，你需要耐心等待，因为这将花费很长时间。 ![](rsrcM0.jpg)完成此步骤后，你可以通过点击 `openvas check setup` 来检查一切是否正常。如果有任何问题，只需启动终端，以 root 身份登录（使用 `sudo su` 命令，输入管理员密码）并输入 `openvasmd -rebuild`。此操作至关重要，因为否则扫描程序可能会出现问题，分析结果可能始终为阴性，这意味着将无法检测到漏洞。 ![](rsrcM2.jpg)

## 启动 OpenVAS 并访问 Web 界面

现在你可以通过再次搜索 OpenVas 并在上述菜单中点击 `openvas start` 来启动 OpenVas。右键点击链接 (`https://127.0.0.1:9392`) 即可连接到图形界面页面。

![](rsrcM3.jpg)如图所示，浏览器中将打开一个安全警报。
