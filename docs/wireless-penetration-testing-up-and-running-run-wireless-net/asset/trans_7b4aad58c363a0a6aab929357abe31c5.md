
*   内置对 Google Cloud Platform 的支持，可实现与 Firebase Cloud Messaging（早期称为 *Google Cloud Messaging*）和 Google App Engine 的集成。
*   Lint 工具，用于捕获性能、实用性、版本兼容性及其他问题。
*   多预览 API。
*   Wear OS 配对助手。

在下载和安装 Android Studio 之前，必须满足以下先决条件。

*   操作系统版本——Microsoft Windows 8/10（64 位）。
*   x86\_64 CPU 架构 第二代 Intel Core 或更高版本，或支持 Windows 的 AMD CPU。
*   随机存取存储器 (RAM)——最低 8 GB RAM 或更多。
*   可用磁盘空间——最低 8 GB，用于 IDE + Android SDK + Android 模拟器。
*   最低要求 JDK 版本——Java Development Kit (JDK) 8。
*   最低屏幕分辨率——1280 \* 800 分辨率。

# Android Studio 的下载与安装

要下载并安装 Android Studio，请遵循以下步骤：

1.  要下载 Android Studio，请在 Web 浏览器中访问 Android Studio 官方网站（**[https://developer.android.com/studio/](https://developer.android.com/studio/)**）。
2.  单击 `Download Android Studio` 选项，如 *[图 10.11](#c10.xhtml#fig10_11)* 所示：
    ![](images/Figure-10.11.jpg)
    **图 10.11：** 从网站下载 Android Studio
3.  下载完成后，双击 `Android Studio-ide.exe` 文件。
4.  屏幕上将出现 `Android Studio Setup`，单击 `Next` 继续，如 *[图 10.12](#c10.xhtml#fig10_12)* 所示：
    ![](images/Figure-10.12.jpg)
    **图 10.12：** Android Studio 安装向导\_1
5.  选择要安装的组件，然后单击 `Next` 按钮，如 *[图 10.13](#c10.xhtml#fig10_13)* 所示：
    ![](images/Figure-10.13.jpg)
    **图 10.13：** Android Studio 安装向导\_2
6.  现在，浏览选择要安装 Android Studio 的位置，然后单击 `Next` 继续，如 *[图 10.14](#c10.xhtml#fig10_14)* 所示：
    ![](images/Figure-10.14.jpg)
    **图 10.14：** Android Studio 安装向导\_3
7.  为 `Android Studio` 快捷方式选择一个“开始”菜单文件夹，然后单击 `Install` 按钮继续，如 *[图 10.15](#c10.xhtml#fig10_15)* 所示：
    ![](images/Figure-10.15.jpg)
    **图 10.15：** Android Studio 安装向导\_4
8.  安装成功完成后，单击 `Next` 按钮，如 *[图 10.16](#c10.xhtml#fig10_16)* 所示：
    ![](images/Figure-10.16.jpg)
    **图 10.16：** Android Studio 安装向导\_5
9.  单击 `Finish` 按钮继续，如 *[图 10.17](#c10.xhtml#fig10_17)* 所示：
    ![](images/Figure-10.17.jpg)
    **图 10.17：** Android Studio 安装向导\_6
10. 现在，你的 Android Studio 欢迎屏幕将出现在屏幕上，如 *[图 10.18](#c10.xhtml#fig10_18)* 所示：
    ![](images/Figure-10.18.jpg)
    **图 10.18：** Android Studio 安装向导\_7

# Android SDK

Android SDK 允许开发者为 Android 平台创建、测试和调试应用。它包含开发 Android 应用所需的所有软件库、API、模拟器系统映像、文档和其他资源。我们已经随 Android Studio 一起安装了 Android SDK，因此掌握如何充分利用 SDK 的内置功能至关重要。本节概述了我们将在渗透测试演练中用于攻击 Android 应用的一些关键工具。

# Android Debug Bridge

这就是我们在本章 *Android Architecture* 部分讨论的内容。它是一个简单而强大的命令行工具，将用于与 Android 设备进行交互和操作。要在物理设备上通过 ADB 连接，必须启用 USB 调试。在运行 Android v9 的 Galaxy Note 10 上，你可以通过进入 `Settings` | `Developer` settings 来访问此选项，如 *[图 10.19](#c10.xhtml#fig10_19)* 所示。

如果不可见开发者选项，是因为它们被禁用了；你可以通过点按 Build number 字段来启用它们，该字段可通过进入 `Settings` | `About Phone` | `Software information` | `Build number` 找到。你总共应该点按七次。

请参阅 *[图 10.19](#c10.xhtml#fig10_19)*：

![](images/Figure-10.19.jpg)

**图 10.19：** Android 调试桥

以下是测试过程中将用到的一系列 ADB 命令。

# 连接设备

设备连接到工作站后，使用 `adb devices` 命令查看设备是否已使用正确的设备驱动程序正确设置。此命令显示连接到工作站的所有设备列表。请参阅 *[图 10.20](#c10.xhtml#fig10_20)*：

![](images/Figure-10.20.jpg)

**图 10.20：** ADB devices 命令\_1

当你在未加载移动设备驱动程序的情况下运行此命令时，将获得一个空列表，如 *[图 10.21](#c10.xhtml#fig10_21)* 所示：

![](images/Figure-10.21.jpg)

**图 10.21：** ADB devices 命令\_2

在这种情况下，你可能需要从设备制造商的网站下载并安装设备驱动程序。

# 获取设备访问权限

正如本章 *Android Architecture* 部分详述的那样，Android 基于 Linux 内核。你可以使用 ADB 连接到 Shell 并在移动设备上执行命令。如果启用了 `Allow USB Debugging` 选项，则可以在已获取 Root 权限或未获取 Root 权限的设备上使用 `adb shell` 命令，如以下命令行输出所示。你将获得一个带有一些限制的标准 Shell。你可能需要通过输入 `su` 进入 Root 模式，这允许你运行大多数 Linux 命令。请参阅 *[图 10.22](#c10.xhtml#fig10_22)*：

![](images/Figure-10.22.jpg)

**图 10.22：** ADB shell 命令

如果工作站连接了多台设备，你可能需要使用不同的参数。请参阅 *[图 10.23](#c10.xhtml#fig10_23)*：

![](images/Figure-10.23.jpg)

**图 10.23：** ADB devices 和 shell 命令

*   `-s` 连接到指定设备
*   `-d` 仅连接到 USB 设备
*   `-e` 仅连接到模拟器

# 向设备安装应用

在评估过程中，将 Android 应用安装到硬件设备或模拟器上是基本前提。你可以使用 `adb install` 命令；这需要要安装的 APK 文件，如 *[图 10.24](#c10.xhtml#fig10_24)* 所示：

![](images/Figure-10.24.jpg)

**图 10.24：** ADB install 命令

# 从设备提取文件

为了检查安装和卸载期间存储了什么数据，我们必须确保没有留下可能被恶意应用或用户利用的敏感信息。因此，我们提取文件以进行离线检查，从而访问任何敏感数据。这可以通过使用 `adb pull` 命令并指定设备上的文件位置来完成。我们在 *[图 10.25](#c10.xhtml#fig10_25)* 中抓取了已获取 Root 权限设备上安装的所有应用：

![](images/Figure-10.25.jpg)

**图 10.25：** ADB pull 命令

# 向设备存储文件

大多数情况下，我们可能想要将本地文件从桌面复制到 Android 设备。语法是 `adb push` 本地文件 远程位置，其中远程位置是文件应存储的位置。例如，以下命令行输出显示将 `pushme.JPG` 文件从本地工作站移动到设备的 `/sdcard/` 文件夹，如 *[图 10.26](#c10.xhtml#fig10_26)* 所示：

![](images/Figure-10.26.jpg)

**图 10.26：** ADB 命令

# 停止服务
