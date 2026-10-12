
![](img/Figure-10.8.jpg)

**图 10.8：** 原生库

任何 `原始设备制造商` (`OEM`) 均可对其进行定制。库模块通常包含以下项目：

*   **媒体框架：** 该框架基于 PacketVideo OpenCore 平台构建，支持常见的音频、视频和静态帧格式以及编解码器插件。StageFright 漏洞是通过利用媒体框架 (`libStageFright`) 的缺陷发现的，该缺陷让攻击者能够通过一项自动播放通过 MMS 或其他方式接收的视频文件的功能，获得对 Android 设备的完全远程访问权限。

*   **Surface Manager (界面管理器)：** 支持显示子系统，并渲染许多应用程序的 2D 和 3D 图形图层。

*   **Freetype：** 用于渲染位图和文本。

*   **OpenGL ES：** OpenGL 是一个跨平台图形 API，为 3D 图形处理器定义了软件接口。

*   **安全套接字层** (`SSL`)**：** 基于 OpenSSL (`www.openssl.org`)。

*   **SQLite：** 应用程序框架 API 使这个轻量级关系数据库引擎可供任何应用程序使用。

*   **WebKit：** 这是一个基于 WebKit 浏览器 (`www.webkit.org`) 的浏览器引擎，支持页面渲染、完整的 CSS、JavaScript、DOM 和 AJAX，以及单栏和自适应视图渲染。

*   **SGL** (即 **可伸缩图形库** 的缩写)：** 用于 2D 图形库。

*   **libc：** 源自 BSD 的标准 C 系统库，用于基于嵌入式 Linux 的设备。

### 应用程序框架

应用程序框架为开发者提供了创建更复杂应用或工具所需的工具。该框架用于管理应用程序的完整开发生命周期。

例如，正在开发需要通知功能应用的开发者，无需编写一行代码；只需调用 `Notification Manager` (通知管理器) API 即可。操作 Android 智能手机所需的大多数 API 都由该框架提供。

*图 10.9* 展示了 Android 平台当前可用的框架列表：

![](img/Figure-10.9.jpg)

**图 10.9：** 应用程序框架

该框架中的关键服务如下：

*   **Activity Manager (活动管理器)：** 活动管理器管理应用的完整生命周期，还负责处理活动的多种状态，以确保使用不同进程的应用平稳运行，我们将在下一节深入探讨。

*   **Content Providers (内容提供者)：** 该组件使应用程序能够与其他应用共享和发布数据。内容提供者负责封装数据、定义数据安全性和控制数据结构。例如，当用户对应用的所有输入都被结构化并保存在 SQLite 数据库中时。

*   **Resource Manager (资源管理器)：** 资源管理器管理对所有未在应用中编码的嵌入式资源的访问，例如图形、本地化字符串和其他布局文件。

*   **Notifications Manager (通知管理器)：** 为移动用户提供通知并显示警报。

*   **View System (视图系统)：** 视图系统监管多种视图、事件分发以及其他重要的按钮和列表。

*   **Package Manager (包管理器)：** 控制设备上安装的所有应用程序包。

*   **Telephony Manager (电话管理器)：** 为设备提供电话服务，如状态和用户信息。

*   **Location Manager (位置管理器)：** 提供关于位置变化的位置服务，允许应用接收更新。

*   **Window Manager (窗口管理器)：** 监管向用户显示的屏幕组织，并在应用程序生成并在显示窗口上适当分层时，为界面提供决策能力。

### 应用层

这是 Android 技术栈的第一层，绝大多数用户通过应用程序与手机进行交互。如 *图 10.10* 所示，设备上通常有两类应用程序：

![](img/Figure-10.10.jpg)

**图 10.10：** 应用层

现在，让我们探讨它们的区别。

### 原生 Android 应用或系统应用

系统应用是由制造商预置在手机中并随手机提供的应用程序。电子邮件客户端、短信程序、电话、日历、地图、拨号器、浏览器、联系人及其他应用均默认加载。这些应用通常无法从设备中移除，且位于 `/system` 文件夹中。

### 用户安装的应用或自定义应用

用户可以通过各种分发网络（包括 Google Play 和 Amazon Store）下载并安装这些应用程序。这些应用位于 Android 文件系统的 `/data/data/` 子目录中。在接下来的章节中，我们将详细介绍安全功能的具体细节。

## Android 渗透测试环境搭建

对于任何形式的安全评估，建立一个结构良好的测试环境至关重要。建议从零环境开始，假设你的电脑上没有安装任何东西。建立 Android 应用渗透测试基础设施的硬件和软件要求如下。

本书重点介绍在 Windows 上搭建环境，但你也可以自由尝试 Linux 和其他操作系统。

*   **硬件和操作系统要求：**

    *   运行 Windows 7 (64 位) 的工作站/笔记本电脑

*   **移动设备和操作系统要求：**

    *   Google Nexus 5 或运行 Android 5.0 或更高版本的其他设备 (已 Root)

*   **软件要求：**

    *   Python

    *   Java Development Kit (1.8)

*   **其他要求：**

    *   适用于移动设备的兼容 USB 数据线

    *   网络 Wi-Fi 设备（可使用任何具有网络共享功能的智能手机充当 Wi-Fi 路由器）

为什么测试环境需要一台已 Root 的手机？

原因很简单：为了能够在设备上编辑和安装任何工具，并运行来自非典型应用商店的未签名软件。已 Root 的手机将拥有完整的文件系统访问权限。给移动设备 Root 不在本书范围内。

## Android Studio 和 SDK

用于开发 Android 应用的官方 `集成开发环境` (`IDE`) 是 Android Studio，由 Google 支持。2019 年 5 月 7 日，Kotlin 取代 Java 成为开发 Android 应用的首选语言。但 Java 仍在被用于开发 Android 应用。Android Studio Dolphin|2021.3.1 具有以下功能。

*   基于 Gradle 的构建支持。

*   UI 组件可通过布局编辑器中的拖放功能创建。

*   通用的 Android 设计和组件可通过基于模板的向导创建。

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

### Android Studio 的下载与安装

要下载并安装 Android Studio，请遵循以下步骤：

1.  要下载 Android Studio，请在 Web 浏览器中访问 Android Studio 官方网站（**[`developer.android.com/studio/`](https://developer.android.com/studio/)**）。

2.  单击 `Download Android Studio` 选项，如 *图 10.11* 所示：

    ![](img/Figure-10.11.jpg)

    **图 10.11：** 从网站下载 Android Studio

3.  下载完成后，双击 `Android Studio-ide.exe` 文件。

4.  屏幕上将出现 `Android Studio Setup`，单击 `Next` 继续，如 *图 10.12* 所示：

    ![](img/Figure-10.12.jpg)

    **图 10.12：** Android Studio 安装向导\_1

5.  选择要安装的组件，然后单击 `Next` 按钮，如 *图 10.13* 所示：

    ![](img/Figure-10.13.jpg)

    **图 10.13：** Android Studio 安装向导\_2

6.  现在，浏览选择要安装 Android Studio 的位置，然后单击 `Next` 继续，如 *图 10.14* 所示：

    ![](img/Figure-10.14.jpg)

    **图 10.14：** Android Studio 安装向导\_3

7.  为 `Android Studio` 快捷方式选择一个“开始”菜单文件夹，然后单击 `Install` 按钮继续，如 *图 10.15* 所示：

    ![](img/Figure-10.15.jpg)

    **图 10.15：** Android Studio 安装向导\_4

8.  安装成功完成后，单击 `Next` 按钮，如 *图 10.16* 所示：

    ![](img/Figure-10.16.jpg)

    **图 10.16：** Android Studio 安装向导\_5

9.  单击 `Finish` 按钮继续，如 *图 10.17* 所示：

    ![](img/Figure-10.17.jpg)

    **图 10.17：** Android Studio 安装向导\_6

10. 现在，你的 Android Studio 欢迎屏幕将出现在屏幕上，如 *图 10.18* 所示：

    ![](img/Figure-10.18.jpg)

    **图 10.18：** Android Studio 安装向导\_7

### Android SDK

Android SDK 允许开发者为 Android 平台创建、测试和调试应用。它包含开发 Android 应用所需的所有软件库、API、模拟器系统映像、文档和其他资源。我们已经随 Android Studio 一起安装了 Android SDK，因此掌握如何充分利用 SDK 的内置功能至关重要。本节概述了我们将在渗透测试演练中用于攻击 Android 应用的一些关键工具。

### Android Debug Bridge

这就是我们在本章 *Android Architecture* 部分讨论的内容。它是一个简单而强大的命令行工具，将用于与 Android 设备进行交互和操作。要在物理设备上通过 ADB 连接，必须启用 USB 调试。在运行 Android v9 的 Galaxy Note 10 上，你可以通过进入 `Settings` | `Developer` settings 来访问此选项，如 *图 10.19* 所示。

如果不可见开发者选项，是因为它们被禁用了；你可以通过点按 Build number 字段来启用它们，该字段可通过进入 `Settings` | `About Phone` | `Software information` | `Build number` 找到。你总共应该点按七次。

请参阅 *图 10.19*：

![](img/Figure-10.19.jpg)

**图 10.19：** Android 调试桥

以下是测试过程中将用到的一系列 ADB 命令。

### 连接设备

设备连接到工作站后，使用 `adb devices` 命令查看设备是否已使用正确的设备驱动程序正确设置。此命令显示连接到工作站的所有设备列表。请参阅 *图 10.20*：

![](img/Figure-10.20.jpg)

**图 10.20：** ADB devices 命令\_1

当你在未加载移动设备驱动程序的情况下运行此命令时，将获得一个空列表，如 *图 10.21* 所示：

![](img/Figure-10.21.jpg)

**图 10.21：** ADB devices 命令\_2

在这种情况下，你可能需要从设备制造商的网站下载并安装设备驱动程序。

### 获取设备访问权限

正如本章 *Android Architecture* 部分详述的那样，Android 基于 Linux 内核。你可以使用 ADB 连接到 Shell 并在移动设备上执行命令。如果启用了 `Allow USB Debugging` 选项，则可以在已获取 Root 权限或未获取 Root 权限的设备上使用 `adb shell` 命令，如以下命令行输出所示。你将获得一个带有一些限制的标准 Shell。你可能需要通过输入 `su` 进入 Root 模式，这允许你运行大多数 Linux 命令。请参阅 *图 10.22*：

![](img/Figure-10.22.jpg)

**图 10.22：** ADB shell 命令

如果工作站连接了多台设备，你可能需要使用不同的参数。请参阅 *图 10.23*：

![](img/Figure-10.23.jpg)

**图 10.23：** ADB devices 和 shell 命令

*   `-s` 连接到指定设备

*   `-d` 仅连接到 USB 设备

*   `-e` 仅连接到模拟器

### 向设备安装应用

在评估过程中，将 Android 应用安装到硬件设备或模拟器上是基本前提。你可以使用 `adb install` 命令；这需要要安装的 APK 文件，如 *图 10.24* 所示：

![](img/Figure-10.24.jpg)

**图 10.24：** ADB install 命令

### 从设备提取文件

为了检查安装和卸载期间存储了什么数据，我们必须确保没有留下可能被恶意应用或用户利用的敏感信息。因此，我们提取文件以进行离线检查，从而访问任何敏感数据。这可以通过使用 `adb pull` 命令并指定设备上的文件位置来完成。我们在 *图 10.25* 中抓取了已获取 Root 权限设备上安装的所有应用：

![](img/Figure-10.25.jpg)

**图 10.25：** ADB pull 命令

### 向设备存储文件

大多数情况下，我们可能想要将本地文件从桌面复制到 Android 设备。语法是 `adb push` 本地文件 远程位置，其中远程位置是文件应存储的位置。例如，以下命令行输出显示将 `pushme.JPG` 文件从本地工作站移动到设备的 `/sdcard/` 文件夹，如 *图 10.26* 所示：

![](img/Figure-10.26.jpg)

**图 10.26：** ADB 命令

### 停止服务

在其他情况下，我们可能想要断开设备连接，此时必须重启 ADB 服务器。这可以通过 `ADB kill-server` 命令来完成，该命令将终止 ADB 连接，并在你提供新的 ADB 命令时重新启动它。

### 查看日志信息

通过 logcat，Android 提供了查看系统调试消息的良好视图；使用 `ADB logcat` 命令，如*图 10.27*所示。检查程序和系统在各种缓冲区中收集的多种类型的日志。在评估期间，此功能有可能成为数据泄露的来源：

![](img/Figure-10.27.jpg)

**图 10.27：** ADB logcat 命令

所有日志都以几种消息类型开头，可以总结如下：

*   `V`：详细

*   `D`：调试

*   `I`：信息

*   `W`：警告

*   `E`：错误

*   `F`：致命

*   `S`：静默

### 旁路加载应用

*旁路加载*通常指将 APK 格式的应用程序包安装到 Android 设备上。此类软件包通常从官方应用商店 Google Play 以外的网站下载。可以在 Android 智能手机上安装自定义 ROM，而 ADB 允许你旁路加载软件。运行 `ADB sideload package.zip`（相当于 `ADB push` 和 `install`）即可实现此目的。

### Monkeyrunner

Monkeyrunner 是一个 Android SDK 实用程序，允许开发人员创建或使用预先存在的应用来控制连接的设备模拟器。

例如，如果你运行 `ADB shell monkey 2`，它将注入事件 ID 2 并在没有用户界面的情况下启动应用程序。请参阅*图 10.28*：

![](img/Figure-10.28.jpg)

**图 10.28：** ADB shell monkey 命令

### Genymotion

Genymotion 是随 Android SDK 附带的 **Android 虚拟设备** (**AVD**) 管理器的替代品。本书的 Android 评估部分将全程使用它。只有在你创建了他们的云账户并按照 **[`www.genymotion.com/#!/download`](https://www.genymotion.com/#!/download)** 的步骤操作后，才能下载 Genymotion。有两种不同类型的许可证：

1.  **个人用途**：此版本的 Genymotion 运行模拟的可能性受到限制。

2.  **商业用途：** 此版本的 Genymotion 为开发人员提供了额外功能，包括网络调试、设计模拟和自动化。
