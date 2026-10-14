
-   即使某人擦除了历史记录，仍然可以恢复。Windows 会在一个名为 `index.dat` 的文件中存储大量信息（如网址、搜索查询和最近打开的文件）。大多数取证工具都能从电脑中提取大量证据。OSForensics 提供了多种选项。其中之一是 **Recent Activity**，如 [Figure 14.7](#ch14.xhtml#ch14fig07) 所示。

![Figure 14.7 OSForensics Recent Activity Option.](Images/14fig07.jpg)

**Figure 14.7** OSForensics Recent Activity Option.

从这张屏幕中，你可以找到所有浏览器活动、已安装的程序、已连接的 USB 设备以及更多内容。

### 在系统日志中查找证据

无论你使用的是什么操作系统，操作系统都有日志。这些日志在任何取证调查中都可能至关重要，你应该将它们提取出来。

#### Windows 日志

我们从 Windows 7/8/10 开始。在这些 Windows 版本中，你可以通过点击桌面左下角的 **Start** 按钮，然后打开 **Control Panel**。接着点击 **Administrative Tools** 并选择 **Event Viewer**。下面是你会检查的日志（虽然并非所有版本都包含全部）：

> **Note**  
> 使用这些工具时必须打开日志记录；否则日志中将没有任何内容。

-   **Security log**：从取证角度来看，这可能是最重要的日志。它记录了成功和失败的登录事件。

-   **Application log**：包含各种应用程序或程序记录的事件。许多应用程序会在此日志中记录错误。

-   **System log**：记录由 Windows 系统组件产生的事件，例如驱动程序失败。与其他日志相比，这个日志在取证视角上兴趣较低。

-   **ForwardedEvents log**：用于存储从远程计算机收集的事件。只有在配置了事件转发时，该日志才会包含数据。

-   **Applications and Services logs**：用于记录单个应用程序或组件的事件，而不是可能影响整个系统的事件。

Windows 服务器具有类似的日志。但 Windows 系统有一个额外的潜在问题：攻击者可能在离开系统前清除日志。也有工具可以擦除日志。还可以在攻击前关闭日志，攻击后再重新打开。一个例子是 `auditpol.exe`。`auditpol \\ipaddress /disable` 用于关闭日志，`auditpol \\ipaddress /enable` 则用于重新开启。还有诸如 **WinZapper** 之类的工具，可以选择性地从 Windows 事件日志中删除特定项。

#### Linux 日志

显然，Linux 也有可供检查的日志。具体哪些日志存在取决于 Linux 发行版以及运行的服务（如 MySQL）。下面是一些常见的日志文件：

-   **/var/log/faillog**：记录失败的用户登录。在追踪破解尝试时非常重要。

-   **/var/log/kern.log**：操作系统内核的消息日志。大多数计算机犯罪调查与此关系不大。

-   **/var/log/lpr.log**：打印机日志，可提供机器打印记录，对企业间谍案有用。

-   **/var/log/mail.\***：邮件服务器日志，在计算机犯罪调查中非常有价值，邮件也可能是非计算机犯罪（如欺诈）的组成部分。

-   **/var/log/mysql.\***：记录 MySQL 数据库服务器的活动，通常对计算机犯罪调查兴趣不大。

-   **/var/log/apache2/\***：如果机器运行 Apache Web 服务器，此日志显示相关活动，对追踪对 Web 服务器的入侵尝试很有帮助。

-   **/var/log/lighttpd/\***：如果机器运行 Lighttpd Web 服务器，此日志显示相关活动，同样对追踪入侵尝试有用。

-   **/var/log/apport.log**：记录应用程序崩溃，有时能揭示入侵尝试或病毒/间谍软件的存在。

-   **/var/log/user.log**：记录用户活动，对刑事调查非常重要。

### 恢复已删除文件

事实是，犯罪分子经常尝试销毁证据，计算机犯罪也是如此：他们可能会删除文件。不过，你可以使用多种工具来恢复这些文件，尤其是在 Windows 上。DiskDigger 是一款免费工具，可用于恢复 Windows 文件，使用非常简便。虽然还有更强大的工具，但它的免费和易用性使其非常适合学习取证的学生。下面我们演示它的基本操作。需要注意的是，前面提到的所有取证工具都能帮助你恢复已删除文件。还需注意，网络上有大量文件恢复工具可供选择，DiskDigger 仅作为示例。

在第一个界面（如 [Figure 14.8](#ch14.xhtml#ch14fig08) 所示），你需要选择要恢复文件的驱动器/分区。

![Figure 14.8 Adding a new scan.](Images/14fig08.jpg)

**Figure 14.8** Adding a new scan.

随后，你在下一屏选择想要执行的扫描深度。如 [Figure 14.9](#ch14.xhtml#ch14fig09) 所示。扫描深度越深，耗时越长。

![Figure 14.9 Selecting the depth of scan.](Images/14fig09.jpg)

**Figure 14.9** Selecting the depth of scan.

然后，你会得到已恢复文件的列表，如 [Figure 14.10](#ch14.xhtml#ch14fig10) 所示。

![Figure 14.10 Recovered files.](Images/14fig10.jpg)

**Figure 14.10** Recovered files.

你可以看到文件名以及文件头。如果需要，还可以选择恢复文件。显然，DiskDigger 可能只恢复文件的碎片，但这在取证中已经足够。

> **Note**  
> 除了已删除文件外，还必须检查 **slack space**（空闲空间）。文件保存时，即使只使用了部分集群，整个集群仍被分配。例如，若集群大小为 10 个扇区，而文件仅占 3 个扇区，操作系统仍视全部 10 个扇区为已用。剩余的 7 个扇区即为 slack space，可能被用来隐藏数据。

OSForensics 也支持搜索并恢复已删除文件，如 [Figure 14.11](#ch14.xhtml#ch14fig11) 所示。

![Figure 14.11 OSForensics Deleted File Search Option.](Images/14fig11.jpg)

**Figure 14.11** OSForensics Deleted File Search Option.

### 操作系统实用程序

操作系统内置了许多实用程序，可用于获取取证数据。鉴于 Windows 是使用最广泛的操作系统，我们将重点放在 Windows 命令行下的实用程序上。但值得注意的是，进行取证工作的关键是熟悉目标操作系统。你也应注意，许多命令在系统正常运行时最有用，以便在攻击进行中捕获攻击痕迹。

#### `net sessions`

`net sessions` 命令列出当前连接到该计算机的活动会话。如果你怀疑攻击正在进行，这将非常重要。如果没有活动会话，工具会报告如 [Figure 14.12](#ch14.xhtml#ch14fig12) 所示。

![Figure 14.12 net sessions.](Images/14fig12.jpg)

