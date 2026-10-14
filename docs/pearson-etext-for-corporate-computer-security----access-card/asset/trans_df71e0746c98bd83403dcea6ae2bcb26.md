
**图 7-7：Windows Server 2019 用户界面**

![](img/073342643701cc54eb7875c41ab92ef2_354_0.png)

漏洞补丁的安装非常简单且通常是自动的。它们包括服务器软件防火墙、加密数据以及许多其他安全增强功能的能力。

这些保护措施并不完美。安全漏洞需要每月进行修补。其他操作系统也存在同样的问题。

### Windows Server 用户界面

Windows Server 的所有最新版本都具有与 Windows 客户端版本界面类似的用户界面。这使得学习 Windows Server 相对容易。如图 7-7 所示，Windows Server 2019 配备了许多在 Windows 客户端版本中也能找到的相同应用程序。它附带 Internet Explorer 和文件资源管理器，并且具有一个 *开始* 菜单，其中大多数选项对桌面用户来说都很熟悉。您甚至可以在 Windows Server 上运行标准客户端软件。

### 开始 → 管理工具

如图 7-7 所示，Windows Server 将大多数管理工具放在 *开始* 菜单上的 **管理工具** 选项中。这使得系统管理员更容易猜到所需工具的位置。

### Windows Server 管理器

Windows Server 的日常管理可以通过 Windows Server 管理器完成。新的角色、功能和服务可以通过服务器管理器添加。它还会向管理员发出有关潜在性能问题和意外事件的通知。管理员可以在一个窗口中查看所有潜在问题并直接修复，而无需逐个打开每个应用程序。

### Microsoft 管理控制台 (MMC)

Windows Server 中的大多数管理工具都采用相同的通用格式，称为 **Microsoft 管理控制台 (MMC)**。图 7-8 显示了重要 MMC *计算机管理* 的组织结构。

**图 7-8：计算机管理 Microsoft Management Console (MMC)**

![](img/073342643701cc54eb7875c41ab92ef2_355_0.png)

- 首先，有图标栏。当用户在两个下部窗格之一中选择一个对象时，图标指定管理员可以对所选对象执行的操作。其中最重要的选项是 *操作*，它特定于所选对象。
- 其次，在左下窗格中有一个管理应用程序的树状结构（**树形窗格**）。
- 第三，树形窗格上的各个应用程序称为 **快接件**，因为它们可以轻松地从树列表中添加或删除。这允许系统管理员轻松地根据特定需求定制 MMC。在图中，快接件 *服务* 被选中。
- 第四，在右下窗格中，有所选工具（服务）的子对象。在这种情况下，选择了 Windows Defender 防火墙服务。

所有 MMC 都有相同的通用组织结构，包括图标栏、树形窗格和子对象窗格。管理员对所选对象可以执行的操作通过单击操作图标显示。这种一致的用户界面使得学习如何使用新的 MMC 和新的快接件变得相对容易。

## 测试你的理解

- **3a.** 微软的服务器操作系统的名称是什么？
- **3b.** 该操作系统的最新版本提供哪些安全保护？
- **3c.** 为什么 Microsoft Windows Server 易于学习？
- **3d.** 为什么服务器管理员会喜欢使用 Windows Server 管理器？
- **3e.** MMC 是什么？（不要只是拼写出缩写。）
- **3f.** 图标栏图标作用于哪个对象？
- **3g.** 树形窗格中有什么？
- **3h.** 子对象窗格中的项目指的是什么？
- **3i.** 快接件是什么？
- **3j.** 为什么它们被称为“快接件”？
- **3k.** MMC 的标准化布局有什么好处？
- **3l.** 系统管理员如何访问大多数管理工具 MMC？
- **3m.** 选择操作会做什么？

## UNIX（包括 Linux）服务器

UNIX 是大型服务器上流行的操作系统。它也用于一些个人电脑。UNIX 创建于多年以前。这段悠久的历史赋予了它广泛的功能和高可靠性。然而，在某些情况下，其基本架构非常陈旧这一事实在某些限制和与用户交互的陈旧模式中显现出来。

### 多个版本

很难广泛谈论 UNIX 安全，因为 UNIX 不是像 Windows 那样的单一操作系统。相反，存在许多不同的 UNIX 版本。包括 IBM、Sun 和 Hewlett-Packard 在内的主要厂商都有自己的商业 UNIX 版本。公司购买的不仅仅是 UNIX；它购买的是 UNIX 的特定版本。

> 公司购买的不仅仅是 UNIX；它购买的是 UNIX 的特定版本。

这些不同的 UNIX 版本倾向于在 **内核** 层面（操作系统的核心部分）互操作。内核兼容性使它们能够运行大多数相同的应用程序。图 7-10 显示了 Unix 终端的示例。

然而，内核只是操作系统的一部分。不同版本的 UNIX 通常具有不同的管理工具，包括安全工具。如果公司使用不同类型的 UNIX，这会使 UNIX 管理变得困难。

![](img/073342643701cc54eb7875c41ab92ef2_356_0.png)

**图 7-9：UNIX 操作系统（学习图）**

**图 7-10：Unix 终端**

```text
boyler@DESKTOP-5514P26:/$ ls -l
total 112
drwxr-xr-x 1 root root 512 Aug 14 17:17 bin
drwxr-xr-x 1 root root 512 May 21 08:42 boot
drwxr-xr-x 1 root root 512 Aug 14 18:06 dev
drwxr-xr-x 1 root root 512 Aug 14 17:17 etc
drwxr-xr-x 1 root root 512 Aug 14 17:17 home
-rwxr-xr-x 1 root root 112600 Dec 31 1969 init
drwxr-xr-x 1 root root 512 May 21 08:41 lib
drwxr-xr-x 1 root root 512 May 21 08:39 lib64
drwxr-xr-x 1 root root 512 May 21 08:39 media
drwxr-xr-x 1 root root 512 Aug 14 17:17 mnt
drwxr-xr-x 1 root root 512 May 21 08:39 opt
dr-xr-xr-x 9 root root 0 Aug 14 18:06 proc
drwx------ 1 root root 512 May 21 08:42 root
drwxr-xr-x 1 root root 512 Aug 14 18:06 run
drwxr-xr-x 1 root root 512 May 21 08:42 sbin
drwxr-xr-x 1 root root 512 Mar 21 03:55 snap
drwxr-xr-x 1 root root 512 May 21 08:39 srv
dr-xr-xr-x 12 root root 0 Aug 14 18:06 sys
drwxrwxrwt 1 root root 512 Aug 14 17:24 tmp
drwxr-xr-x 1 root root 512 May 21 08:39 usr
drwxr-xr-x 1 root root 512 May 21 08:42 var
boyler@DESKTOP-5514P26:/$
```

来源：© 1995–2019 The Open Group

### Linux

对于 PC 上的 UNIX，情况甚至更加混乱。PC 上最流行的 UNIX 版本是 **Linux**。然而，Linux 只是操作系统内核。Linux 厂商实际提供的是将该内核与其他软件结合的发行版。许多软件来自开源 GNU 项目。对于大多数功能，GNU 提供了几种替代程序。因此，Linux 发行版往往差异较大，尤其是在管理和安全方面。

> Linux 是在普通 PC 上运行的 UNIX 版本。实际上，Linux 只是操作系统的内核。实际的 Linux 包是发行版，包含内核和许多其他程序——主要是来自 GNU 项目的通用程序。

Linux 很受欢迎，因为它是免费的，尽管“免费”需要谨慎对待。首先，一些 Linux 厂商会收取使用其 Linux 版本的费用，无论他们是否称之为销售价格。即便如此，Linux 的购买价格远低于商业服务器操作系统，并且一份 Linux 副本可以在多台服务器上安装而无需额外费用。Microsoft Windows Server 或服务器厂商创建的 UNIX 版本绝非如此。

然而，购买价格只是总拥有成本（TCO）的一个因素。许多公司发现 Linux 的管理成本相当高，尤其是在使用来自多个 Linux 厂商的许多发行版时。

存在许多不同的 Linux 发行版这一事实使得加固 Linux 系统变得困难。一些更流行的 Linux 发行版包括但不限于 Mint、Ubuntu、Debian、Manjaro 等。重要的是为你使用的 UNIX 发行版的特定版本建立良好的安全基线。

尽管 Linux 最初是为个人电脑创建的，但现在许多大型服务器都在运行 Linux。服务器采购通常是集中的，因此企业服务器上的 Linux 发行版种类可以得到控制。

### UNIX 桌面环境

即使在 UNIX 的特定版本中，操作系统软件也可能附带几种替代桌面环境。其中一些界面将是类似于 Microsoft Windows 界面的图形用户界面。在 Linux 上，有几种流行的桌面环境
