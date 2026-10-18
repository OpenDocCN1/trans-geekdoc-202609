

## 将您的 VM 连接到虚拟网络

默认情况下，新 VM 连接到 `host-only network`，这意味着您只能从主机计算机访问它们。要将您的 VM 相互连接并连接到互联网，我们将创建一个 `virtual network`。将您的 Windows 和 Kali 机器连接到虚拟网络，就像将它们连接到同一个 Wi-Fi 网络一样。

1. 在 VirtualBox 中，转到 `File`▶`Preferences`（或 Mac 上的 `VirtualBox`▶`Preferences`）。

2. 转到 `Network` 选项卡，然后单击绿色的 Add 图标（带有加号的那个）以创建新的虚拟网络。

3. 一个新网络（名称类似于 `NatNetwork`）应该出现在列表中。确保网络名称旁边 Active 列下的复选框已被选中。

4. 选择该网络，然后单击 Settings 图标（带有黄色齿轮的那个）。

5. 在 Network Name 框中输入 `PublicNAT`，并通过输入 `10.0.9.0/24` 更改 Network CIDR 文本框，以设置 VM 的 IP 地址。

6. 保持 Supports DHCP 复选框被选中，并单击两次 `OK` 以完成网络的创建。

我们的下一个任务是将您的 VM 连接到您创建的 PublicNAT 网络。

### 连接您的 Kali VM

我们将首先将您的 Kali VM 连接到网络并测试连接。

1. 在 Oracle VM VirtualBox Manager 中，单击您的 Kali VM，然后单击 `Settings`。

2. 选择 `Network` 选项卡，并从 Attached to: 下拉列表中选择 `NAT Network`。在 Name: 下拉列表中，选择 `PublicNAT`。然后单击 `OK` 以保存更改。

3. 启动 Kali VM，并像之前一样使用用户名 `kali` 和密码 `kali` 登录。

4. 一旦 Kali VM 桌面出现，单击屏幕左上角面板中的黑色方块图标打开命令行 Terminal 程序，如 [Figure 3-4](#c03.xhtml#figure3-4) 中圈出的所示。

5. 键入命令 `ip addr` 并按 `ENTER` 以查看 VM 网络连接的信息。

    ![Figure 3-4: Checking the Kali VM’s IP address](image_fi/502000c03/f03004.png)

    Figure 3-4: Checking the Kali VM’s IP address

6. 您应该在 `eth0:` 部分下看到以 `10.0.9` 开头的 IP 地址，如 [Figure 3-4](#c03.xhtml#figure3-4) 中圈出的那个。

当 Kali 显示以 10.0.9 开头的 IP 地址时，它已连接到 PublicNAT 网络。如果您看不到类似 10.0.9.*x* 的地址，请转到 `Machine`▶`Reset` 以重新启动 Kali VM。当 VM 重新启动后，在终端中再次运行 `ip addr` 命令。如果您仍然看不到 10.0.9.*x* IP 地址，请返回并检查 VirtualBox Manager 中的 Kali VM 网络设置。

### 连接您的 Windows VM

将您的 Windows VM 连接到 PublicNAT 网络的工作几乎与连接 Kali VM 完全相同。

1. 转到 VirtualBox Manager，选择您的 Windows VM，然后单击 `Settings`。

2. 单击 `Network` 选项卡，从 Attached to: 下拉列表中选择 `NAT Network`，并从 Name: 下拉列表中选择 `PublicNAT`。单击 `OK` 应用这些设置。

3. 启动您的 Windows VM，并像之前一样使用默认密码 (`Passw0rd!`) 登录。

4. 当 VM 加载后，单击 Windows 搜索栏（位于 [Figure 3-5](#c03.xhtml#figure3-5) 的左下角），键入 `CMD`，并按 `ENTER` 打开 Windows 命令提示符，它类似于 Kali Linux Terminal 程序。

5. 输入命令 `ipconfig` 以检查 VM 的网络设置。

6. 您应该看到 10.0.9.*x* 范围内的 IP 地址，如 [Figure 3-5](#c03.xhtml#figure3-5) 中的 `10.0.9.5` 地址。

    如果您的地址以 10.0.9 开头，您已成功将 Windows VM 连接到 PublicNAT 网络。如果不是，请转到 `Machine`▶`Reset` 以重新启动 Windows VM。再次尝试 `ipconfig` 命令。如果您仍然看不到 10.0.9.*x* IP 地址，请返回并检查 VirtualBox Manager 中的 VM 网络设置。

    ![Figure 3-5: Checking your Windows VM’s network settings](image_fi/502000c03/f03005.png)

    Figure 3-5: Checking your Windows VM’s network settings

7. 最后，尝试测试您网络的互联网连接。在您的 Windows VM 中，打开 Microsoft Edge 网络浏览器并访问任何网址，例如 [https://www.nostarch.com/go-hck-yourself/](https://www.nostarch.com/go-hck-yourself/)。

如果您无法访问任何网站，请再次执行前面的步骤，并尝试关闭并重新启动 Windows VM。

## 更新您的 VM 操作系统

现在您的虚拟机已连接到互联网，我们可以更新它们的操作系统，以确保它们可以访问最新功能。经常更新计算机的操作系统始终是个好主意，可以通过启用自动更新或至少每月检查一次更新来实现。更新操作系统可以保护您免受病毒、黑客和其他在线威胁。这是您可以做的最重要的事情之一，以抵御最新的网络攻击。

### 更新 Kali Linux

按照以下说明更新 Kali Linux：

1. 启动 Kali VM 并再次打开终端命令行应用程序。

2. 在终端提示符下，输入以下命令以查找需要更新的软件：

    ```
    kali@kali:~$ sudo apt update
    ```

3. 第一次使用 `sudo` 时，Kali 会要求您输入密码。这个命令（“superuser do”的缩写）允许您以管理员（或 `superuser`）权限运行命令。将 `kali` 作为密码输入并按 `ENTER`。

4. 现在使用此命令执行更新：

    ```
    kali@kali:~$ sudo apt upgrade
    ```

5. 您可能需要按 `Y` 来确认某些更新。随着各种软件包的更新，它们将在终端窗口中列出，后跟消息 `Done`。

6. 当 `apt` 完成 Kali 的更新后，关闭机器并保存机器状态。

### 更新 Windows

接下来，我们将更新您的 Windows VM。

1. 启动 Windows VM，在 Windows 搜索栏中键入 `updates`，并从选项列表中选择 `Check for updates`。

2. 如果 Windows 有可用更新，您应该会看到 Install now 或 Restart now 按钮。单击按钮安装更新。您可能需要重新启动 VM，就像您有时需要为真实计算机的更新重新启动一样。

3. 在 Windows VM 完成更新后，关闭它并保存机器状态。

## 要点

在本章中，您设置了 VirtualBox 虚拟化软件并创建了两台虚拟机，这些软件充当您实际计算机内的计算机。其中一台 VM 运行 Kali Linux，将充当您的攻击计算机，而另一台运行 Windows，将充当您的目标计算机。您还创建了一个名为 PublicNAT 的虚拟网络，以将两台 VM 连接到互联网并相互连接。然后，您对 Kali 和 Windows VM 应用了更新。

您现在已经设置了一个功能齐全的虚拟黑客实验室。做得好！有了您的两台 VM 和虚拟网络，您就可以安全且合乎道德地尝试不同的黑客攻击，而不会影响您的物理计算机。在下一章中，我们将开始利用您的实验室进行一些侦察，看看仅使用搜索引擎和社交媒体就能找到什么样的信息。

# 4

在线侦察与自卫

![](image_fi/book_art/chapterart.png)

大多数黑客攻击的第一步是 `reconnaissance`，或 `recon`。在军事行动中，侦察涉及勘察敌方领土或观察目标。在黑客世界中，攻击者在线执行侦察。他们使用常规搜索引擎（如 Google）、社交媒体平台和专业工具收集有关公司、网络和个人的信息。然后，他们使用这些信息来计划黑客攻击的下一阶段。

