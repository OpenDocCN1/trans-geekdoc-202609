
Secure Enclave 与主处理器隔离，它使用专用处理器和内存区域、安全引导 `ROM` 以及专用 `AES` 引擎。`AES` 硬件引擎在文件写入或读取时进行解密和加密，密钥材料不会暴露给应用处理器或操作系统。Apple 利用此机制实施多项安全防护，以防止硬件篡改，并保护生物识别认证数据及其加密。

首先要了解的是，Apple 通过为每台设备生成唯一的 `UID`（唯一标识符）根加密密钥来保护设备特定的机密，并通过在同类所有设备间共享的 `GID`（组标识符）来保护软件特定的机密。这些密钥用于确保对敏感硬件（如内部 `SSD` 存储或触摸传感器）的更改会导致加密数据变得不可访问。即使使用 `JTAG` 或其他调试接口，这些密钥也无法恢复。

![Images](img/note.jpg)

> **NOTE**
>
> `JTAG` 代表 Joint Test Action Group（联合测试行动组）。`JTAG` 接口是一种用于调试和连接电路板上嵌入式设备的硬件机制。`JTAG` 是 IEEE Std 1149.1 中认可的行业标准。你可以从 IEEE 数字图书馆了解更多关于该标准的信息：[`ieeexplore.ieee.org`](https://ieeexplore.ieee.org)。

### 移动操作系统概述

正如你所料，硬件的差异会导致操作系统的差异。这些差异将影响你使用的工具、查找信息的位置以及评估设备安全性的方式。为了理解这些差异，让我们深入了解 iOS 和 Android 操作系统。

#### iOS 操作系统安全

iOS 操作系统是专有的，iOS 及其变体仅在 Apple 移动设备（即 iPhone、iPad）上运行。iOS 基于 Darwin（[www.puredarwin.org](http://www.puredarwin.org)）。Apple 在操作系统中包含了许多安全措施。

例如，Apple 限制可用的服务和工具，并将整个操作系统分区作为只读加载到磁盘上，以保护操作系统内容。iOS 还通过 Execute Never（XN，不可执行）功能将内存位置标记为不可执行。内核会在允许应用程序访问可写且可执行的内存位置前，检查其是否具有 Apple 专用的动态代码签名权利。

大多数系统文件、资源和第三方应用程序作为非特权 `mobile` 用户运行。系统应用程序和守护进程使用经过数字签名的权利来执行特权操作。权利是允许应用程序在正常运行时参数之外进行认证的键值对。第三方应用程序通过声明的权利获得对用户信息、扩展或其他功能的访问权。如果用户授予应用程序访问权限，该授权会延伸至嵌入在应用程序中的扩展，但不延伸至由应用程序激活的扩展。

扩展是随应用打包的特殊签名可执行文件，为其他应用提供功能。这些扩展在应用安装期间被检测并映射以供使用。扩展是沙箱化的——它们在独立于应用程序的内存空间和容器中运行。扩展与激活它们的应用程序之间的通信，必须通过系统框架管理的进程间通信来处理。来自同一开发者的应用和扩展可以使用共享的 `App Group`，这将允许它们使用共享容器、偏好设置和钥匙串项目来共享内容。

此外，iOS 通过 Made for iPhone（MFI）计划验证经过审核的配件。当 MFI 设备通过 `Lightning`、`USB-C` 连接器或 `Bluetooth` 连接时，iOS 会使用来自配件的 Apple 提供证书，通过质询-响应协议对其进行验证。iDevice 中的自定义集成电路（IC）处理此交换。该 IC 确保只有经过批准的配件才能获得对设备的完全访问权限。如果不支持此认证，访问将仅限于一部分音频控制和功能。

#### Android 操作系统

##### Android 平台概述

Android 是由 Google 开发的基于 Linux 2.x 和 3.x 内核的开源移动操作系统（[`developer.android.com`](https://developer.android.com)）。Android 可运行在各种硬件上，如手机、电视、平板电脑和其他技术设备。图 7-1 描述了 Android 平台的主要组件。

![Images](img/F07-01.jpg)

**图 7-1** Android 平台

在移动 Android 设备上，用户在应用层进行交互。该层也是预装原生系统应用的所在地，如日历应用、相机和电子邮件。Android 应用程序使用 Java 或 Kotlin 进行开发。应用程序在虚拟机中运行其自己的进程（即 `ART` 的一个实例，即 Android Runtime 的缩写），就像它们是拥有独立主目录的独立用户账户一样。这提供了设备上所有其他正在运行的应用程序之间的隔离。Java 应用程序编程接口（`API`）框架向应用程序暴露 Android OS 的功能，以简化对应用程序数据和其他系统组件的访问。Android 应用程序的主要组件包括：

*   **活动** 用户可见的应用程序部分
*   **片段** 放置在活动中的一种行为
*   **意图** 用于在其他组件之间发送消息
*   **广播接收器** 允许应用程序接收来自其他应用的通知
*   **内容提供器** 一个 SQLite 数据库，以平面文件的形式存储数据
*   **服务** 用于启动意图、发送通知和处理数据

硬件抽象层（`HAL`）与设备的内置硬件组件进行交互。原生 C 和 C++ 库为使用原生代码开发的应用程序提供支持，例如 `HAL` 和 `ART`。内核为平台内的其他组件提供基础服务，如驱动程序、内存管理和显示功能。

![Images](img/note.jpg)

**注意** `ART` 是原始运行时 Dalvik 虚拟机（`DVM`）的继任者。Android 5.0（`API` 级别 21）或更高版本不再使用 `DVM`。

Android 分区位于设备的内部存储或外部存储上。下表描述了大多数 Android 操作系统上创建的常见分区。

![Images](img/f0221-01.jpg)

##### 移动应用程序概述

在本章中，我们将重点关注移动应用程序测试，因为这是知识面最广的领域。OWASP 移动安全项目旨在为移动应用程序的安全开发提供资源和指导。与 Web 应用程序一样，OWASP 提供了移动端十大风险，如图 7-2 所示。OWASP 还提供安全清单、测试指南以及其他关于测试和开发安全移动应用程序的信息。在此项目中，移动应用程序被分类为原生、Web、混合或渐进式 Web 应用程序。

![Images](img/F07-02.jpg)

**图 7-2** OWASP 移动端十大风险（2016）

原生应用程序可与操作系统紧密耦合，并直接访问摄像头、传感器和其他设备组件。要创建这些应用程序，开发人员使用针对操作系统专门定制的 SDK。对于 Android，这意味着使用 Java 或 Kotlin；对于 iOS，这意味着使用 Objective-C 或 Swift。由于原生应用与操作系统紧密耦合开发，除非使用特殊的开发工具进行移植，否则它们只能在单一操作系统上运行。

另一方面，Web 应用程序看起来像原生应用程序，但在设备的浏览器中像网页一样运行。这些通常用 HTML5 编写，并享有跨平台可移植性。然而，其功能依赖于与在线后端的通信。因此，这些通常可以使用我们在第 5 章中讨论的相同方法进行测试。

混合和渐进式应用程序则没那么简单。混合应用是 Web 和原生应用程序的结合。其组件使用 Web 到原生的抽象层来同时使用 Web 和原生功能。另一方面，渐进式 Web 应用像网页一样加载，但允许离线使用，并可根据平台访问有限的设备功能。这些通常具有本地组件，包括以 Web 应用程序清单形式存在的存储和应用程序配置。

![Images](img/note.jpg)

**注意** OWASP 移动应用安全清单（[`github.com/OWASP/owasp-mstg`](https://github.com/OWASP/owasp-mstg)）描述了移动渗透测试期间需评估的常见关注领域，而 OWASP 移动安全测试指南（`MSTG`，[`owasp.org/www-project-mobile-security-testing-guide/`](https://owasp.org/www-project-mobile-security-testing-guide/)）详细阐述了各种平台的内部机制，定义了移动应用程序安全测试的标准，并概述了针对移动设备执行各种测试活动的程序和工具。

每个平台实现自己的应用程序格式。为 Android 开发的应用程序存储在 Android 应用程序包（`APK`）中。由于 Android 应用程序基于 Java，`APK` 采用 Java 归档（`JAR`）格式，并包含一个清单文件（`AndroidManifest.xml`），该文件以二进制 XML 格式嵌入内容。iOS 应用程序存储在 iOS App Store 包（`IPA`）格式中。`IPA` 是一个 ZIP 压缩归档文件，包含运行应用程序所需的所有代码和资源。内置目录结构包括位于 `Payload` 文件夹内的 `Application.app`，其中包含所有应用程序代码和资源；存储在 `iTunesArtwork` 文件夹中的应用程序图标；包含开发者标识信息、捆绑包标识符和其他应用程序识别数据的 `iTunesMetadata.plist`；以及存储在以创建它们所用工具包命名的目录中的扩展包。

应用程序运行时，会被沙箱化，以防止其访问其他应用程序的数据或对设备进行更改。每个应用程序都有自己的容器，如果它需要访问设备数据或其他应用程序的数据，必须使用操作系统提供的服务。在 iOS 中，此容器包括：

*   **捆绑包容器** 一个只读的、已签名的容器，应用程序及其所有资源驻留于此
*   **数据容器** 通常包括 `Documents` 目录（用于用户创建和可访问的内容）；`Library` 目录（用于存储任何用户不可访问文件的顶级目录，通常包括一个 `Application Support` 子目录，用于存放应用运行所需但应对用户隐藏的文件）；以及一个 `tmp` 目录（用于非持久化文件）
*   **iCloud 容器** 用于云功能启用

要测试应用程序，您需要安装并运行它，或者需要一台已安装该应用的设备来进行观察。如前所述，移动应用程序通常是与其他 Web 服务和 API 交互的 Web 客户端。因此，您可以在移动领域使用许多我们在第 3 章和第 5 章中讨论的技术。例如，评估通信通道使用情况的最佳方法是拦截流量并进行网络分析。使用 OWASP ZAP 或 Burp Suite 检查和操纵 Web 流量，搜索弱加密或已弃用的加密算法，或使用 Postman 评估 API 滥用。在某些情况下，您需要绕过证书绑定才能观察流量。让我们深入了解。

![Images](img/note.jpg)

**注意** OWASP 的文章“证书和公钥绑定”解释了什么是证书绑定及其在移动平台背景下的工作原理：[`owasp.org/www-community/controls/Certificate_and_Public_Key_Pinning`](https://owasp.org/www-community/controls/Certificate_and_Public_Key_Pinning)

#### 测试 iOS

##### iOS 应用安全测试

OWASP 移动安全测试指南建议测试应用输入（包括 IPC、URL Scheme 和用户输入）、WebView 加载的内容、后端通信安全、本地数据存储保护，以及针对逆向/重打包的防御，以评估 iOS 应用的安全性。为此，你需要应用的副本或对已安装该应用的设备的访问权限。

Apple 使用代码签名来确保只有经过批准的应用程序才能在 iOS 上运行。代码可通过证书验证进行签名，这需要通过 Apple Developer Program（Apple 开发者计划）或 Apple Developer Enterprise Program（Apple 企业开发者计划）进行注册和身份验证。验证也通过代码签名验证完成，确保启动时链接的所有库都具有从 Apple 颁发的证书中提取的有效 Team ID。后者是一项保护措施，防止现有应用程序加载第三方代码。如果你拥有 Apple Developer 账户，你可以对 iOS 应用程序进行签名。请注意，如果你的行为被视为恶意，你的账户可能会被吊销，因此如果你计划进行任何安全研究，请使用与个人账户分开的账户。正如你从广泛的 iOS 安全控制中所想象的那样，在不越狱设备的情况下测试 iOS 应用程序是很困难的。

###### Cydia Impactor

Cydia Impactor 工具（[`www.cydiaimpactor.com`](http://www.cydiaimpactor.com)）是一个用于将 IPA 文件安装到 iDevice 的 GUI。例如，越狱工具被打包为 IPA，Impactor 工具用于将越狱工具传输到设备上进行安装。请按照以下步骤将应用安装到你的设备：

1.  在你的笔记本电脑上，下载适合你操作系统的最新 Cydia Impactor 安装文件。
2.  将移动设备连接到你的笔记本电脑。
3.  在你的笔记本电脑上，打开 Cydia Impactor 应用程序。如果 Cydia 识别出该设备，它将显示在顶部的下拉菜单框中。

    ![Images](img/I07-01.jpg)

4.  将适合你的设备和 iOS 版本的应用下载到你的笔记本电脑上。
5.  在你的笔记本电脑上，打开你常用的文件管理器 GUI，将应用程序文件拖拽到 Cydia Impactor 窗口中。系统将提示你输入 Apple ID 和密码以继续。出现提示时输入正确的电子邮件和密码，然后点击 OK 框继续。
6.  如果成功，Cydia Impactor 会将 IPA 安装到设备上，你将在移动设备桌面上看到该应用。

###### Cydia Package Manager

Cydia Package Manager 是“已越狱” iDevice 的应用商店。Jay Freeman (saurik) 是 Cydia 的最初创建者，通常在成功越狱后默认安装，例如 Yalu 和 Pangu 提供的越狱工具。Cydia 主屏幕提供对各项功能的访问，包括用户指南、可安装到设备的主题、用于实用软件包的仓库，以及从仓库搜索并安装你想要的软件包的能力。图 7-3 展示了 Cydia 主屏幕的外观示例。你可能想要从预配置的仓库中搜索并安装的一些基本工具包括 `Class Dump`、`Wget`、`OpenSSH` 和 `IPA Installer Console`。

![Images](img/F07-03.jpg)

**图 7-3** Cydia Package Manager

###### Frida 动态分析

Frida 是一个模块化框架，旨在评估移动应用的安全性。Frida 不仅是一个 iOS 测试工具。它也可用于 Android、Windows、Linux、macOS 和 QNX 的测试。Frida 有三种测试模式：注入模式，即你生成到正在运行的程序中，或测试运行着 `frida-server` 的设备；嵌入模式，它使用嵌入到你的应用中的共享库（`frida-gadget`）进行远程交互；以及预加载模式。Frida 包含许多用于测试的有用工具，包括一个名为 `Stalker` 的代码追踪引擎，用于追踪线程并捕获执行的函数和指令。但它不是调试器。例如，它不会在运行时修改代码或暂停执行。它也不是反汇编器。让我们看一个用例。

要安装 Frida，你的笔记本电脑上应安装 Python 3.x 和 PyPI。然后运行：

```
$ pip3 install frida-tools
```

假设你使用的是 macOS，你可以使用 Frida 12.7.12 或更高版本（github.com/frida/frida/releases/latest）以针对通过 USB 连接的 iOS 13 设备。使用 Cydia，前往 Manage | Sources | Edit | Add，并输入 `https://build.frida.re` 以添加 Frida 的仓库。现在你可以输入命令 `frida-ps` 列出所有已安装的应用。

```
$ frida-ps -Ua
```

![Images](img/I07-02.jpg)

它应该会提示你通过 USB 连接设备。连接后，你应该会看到越狱设备上所有正在运行的进程列表。现在你可以启动要测试的应用程序，并使用 `frida-trace` 连接到它。首先使用 `frida-discover` 查找要追踪的调用：

```
$ frida-discover -U MyApplication
```

![Images](img/I07-03.jpg)

一旦找到感兴趣的 API 进行跟踪，你可以使用 `frida-trace`：

```
$ frida-trace -U MyApplication -i "TargetFunction"
```

![Images](img/I07-04.jpg)

`-i` 标志告诉它挂钩 C 函数。对于 Objective-C 函数，你应该使用 `-m` 标志。你可以查看进程，追踪特定进程中的 API，或使用 `-l` 标志指定注入脚本将其注入到你的应用程序中。Frida 通过提供的工具（如 `frida-ps` 和 `frida-trace`）来处理这些；不过，你也可以编写自己的工具，或使用来自 Frida CodeShare（codeshare.frida.re/）等仓库的社区贡献代码。

![Images](img/note.jpg)

**注意** 要了解更多关于 Frida 的信息，包括其他用例、编写注入脚本的技巧以及关于 Frida API 的文档，请访问他们的文档宝库 [`frida.re/docs/home/`](https://frida.re/docs/home/)。

###### 使用 Objection 绕过 SSL Pinning
