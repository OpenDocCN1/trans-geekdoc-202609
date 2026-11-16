

## 服务器消息块

你会遇到的最常见的远程过程调用实现是 Windows 网络中使用的那一种。SMB 协议在考虑其所有不同用途和所有不同运行方式时比较复杂。你可能最熟悉 SMB 作为用于跨网络共享文件的协议。虽然这肯定是 SMB 的一种用途，但不是唯一一种，即使考虑文件共享，也远不止是在网络上传输文件内容。

SMB 是一个应用层协议，可以在较低层的不同协议之上运行。首先，它可以直接在 TCP 之上运行，无需任何其他会话层协议。如果系统直接在 TCP 上运行 SMB，你会发现 TCP 端口 445 是开放的。SMB 也可以在 NetBIOS 等会话协议之上运行，NetBIOS 是由 IBM 开发的应用程序编程接口 (API)，旨在将输入/输出 (I/O) 功能从本地系统扩展到网络。如果你看到 UDP 端口 137 和 138 开放，你就会知道你发现了在 NetBIOS 之上运行的 SMB。但是，如果你发现 TCP 端口 137 和 139 开放，你就会发现 SMB 在 TCP 上的 NetBIOS 之上运行。请记住，在这种情况下，NetBIOS 用于名称服务。

那么，SMB 到底有什么用呢？SMB 用于 Windows 系统之间的通信——文件共享、网络管理、系统管理。这可能意味着管理系统名称，以确保没有冲突。这样的管理要求系统向本地网络宣布自身。SMB 还必须支持身份验证，以免系统对整个网络完全开放。这意味着 SMB 了解用户和组。它还了解共享，即暴露给网络的目录。系统必须能够向询问的系统提供它们正在导出到网络的共享列表。这允许用户在身份验证后获取共享列表并访问想要的共享。

当然，身份验证并非总是必要。SMB 支持一种称为空身份验证的机制。这意味着有些函数不需要用户名和密码。系统可以使用空身份验证请求网络中其他系统的信息，这意味着未传递任何凭据。这种空身份验证可以让我们收集关于系统的大量信息。

我们可以使用几种不同的工具来枚举 Windows 系统上的信息。实际上，这不仅限于 Windows 系统，尽管在其他系统上实现 SMB 的目的是与 Windows 系统互操作。Samba 是一个可以安装在类 Unix 操作系统上的软件包，提供 SMB 以及 NetBIOS 命名服务。Samba 使用两个独立的进程。一个是 smbd，处理 SMB，还有一个是 nmbd，处理与 Windows 系统互操作的命名方面。这意味着，即使我们希望从 Windows 系统枚举信息，也可以收集类 Unix 系统的信息。

起步的首要方法是使用内置工具。内置工具在 Windows 系统上尤其常见，但也有类 Unix 的实用程序。我们还将查看一些可用于收集信息的 nmap 插件。Metasploit 毫不奇怪地拥有多个用于扫描 SMB 系统的模块。还有其他一些实用程序可供使用，我们将了解其中一些。

## 内置实用程序

如果你在 Windows 系统上，有许多可用的工具可以使用 SMB 收集信息。Linux 上也有类似工具。关于内置工具需要注意的是，你需要处于同一广播域才能使用它们。NetBIOS 最初是为局域网开发的，而不是内置广域网概念的。因此，一些函数之所以有效，是因为系统依赖向网络广播信息。这意味着，在这些工具生效之前，你需要在本地网络上有存在。

可以通过使用 nbstat 程序来收集 NetBIOS 统计信息。这允许你收集有关本地网络的数据。在以下示例中，你可以看到使用 nbstat 获取远程系统数据的方法。使用 nbstat -a 会显示所提供主机名的名称表。如果我们只知道远程系统的 IP 地址，可以改用 nbstat -A。你会看到我们得到不同的信息片段。你会在左侧看到名称列表，后跟一个代码。该代码指示名称存在的上下文，后跟每个名称的状态。

### nbstat 输出

```
C:\Users\kilroy
> nbstat -a billthecat

Local Area Connection:
Node IpAddress: [192.168.86.50] Scope Id: []

NetBIOS Remote Machine Name Table

Name                   Type       Status
------------------------------------------------
BILLTHECAT             <00>       UNIQUE     Registered
BILLTHECAT             <20>       UNIQUE     Registered
WORKGROUP              <00>       GROUP      Registered

MAC Address = AC-87-A3-36-D6-AA
```

显示的代码来自 NetBIOS，你可以查找代码以确定名称关联到什么。使用 SMB 的系统可以存在于多个上下文中。你看到的是一个既是工作站又是文件服务器的系统。这意味着该系统上已启用文件共享。不过，该系统在网络上也充当工作站或客户端。区分功能很重要，因为这样每个系统才能知道可以向其他每个系统提出什么类型的问题。从技术术语来说，每组功能都有关联的过程。我们不能调用不存在的过程，因此在远程系统上调用过程以启动操作之前，我们必须知道有哪些过程可用。nbstat -a 基本上提供了这些信息。

到目前为止我们看到的只是询问网络上主机名关联的所有功能（名称）。这是一个单独的系统。如果我们想查看所有正在通信的 SMB/NetBIOS 主机名，需要请求其他内容。我们仍然可以使用 nbstat，只是在命令行中传递不同的参数。我们要查找的是已解析的名称。当没有用于名称查找的集中式数据库时，此列表可以来自广播消息——系统在上线时宣布其名称和存在，之后会定期宣布。它也可以来自 Windows Internet Name Server (WINS)，后者是企业网络中系统名称的中央存储库。Windows 服务器将具有 WINS 功能，因此系统向 WINS 注册，所有名称都可以被解析。

### 使用 nbstat 列出已解析的名称

```
C:\Users\kilroy
> nbstat -r

NetBIOS Names Resolution and Registration Statistics
-----------------------------------------------
Resolved By Broadcast    = 47
Resolved By Name Server  = 0

Registered By Broadcast  = 8
Registered By Name Server = 0

NetBIOS Names Resolved By Broadcast
-----------------------------------------------
YA9PISTACHIO       <00>
BILLTHECAT         <00>
YAZPISTACHIO       <00>
YAZPISTACHIO <00>
LOLAGRAINOLA <00>
LOLAGRAINOLA <00>
YAZPISTACHIO <00>
YAZPISTACHIO <00>
```

nbstat 还提供其他功能，但它们更多与本地系统功能相关，对枚举来说相关性较低。虽然 nbstat 功能丰富，但如前所述，它仅适用于 Windows 系统。如果你不运行 Windows，可以使用其他工具。如果你有 Linux 系统并安装了 Samba 软件包（它提供允许 Linux 使用 SMB 进行通信的服务），可以使用 nmblookup 工具。这可用于查找网络上的名称。它可以用于查询 WINS，也可以查找那些仅广播其信息的系统的名称。例如，要获取有关系统 billthecat 的详细信息，如我们之前所做的，你会使用 nmblookup -S -R billthecat，如你在这里看到的那样。

### 用于枚举的 nmblookup

```
kilroy@savagewood$ nmblookup -S -B 192.168.86.255 billthecat
Can't load /etc/samba/smb.conf - run testparm to debug it
querying billthecat on 192.168.86.255
192.168.86.32 billthecat<00>
Looking up status of 192.168.86.32
	BILLTHECAT <00> -      H <ACTIVE>
	BILLTHECAT <20> -      H <ACTIVE>
	WORKGROUP  <00> - <GROUP> H <ACTIVE>
MAC Address = AC-87-A3-36-D6-AA
```

使用 -B 告诉 nmblookup 使用提供的广播地址，即本地网络上的广播地址。要使用 WINS，可以使用 -R 对名称进行递归查找。标志 -S 告诉 nmblookup 获取节点状态，而不仅仅是名称状态。这个标志为我们提供了其他用途。与之前一样，我们可以看到我们有一个工作站 (<00>) 和一个文件服务器 (<20>)。你还将从此输出中看到，与之前一样，该系统属于工作组 WORKGROUP。工作组用于临时 Windows 网络，其中没有域控制器来管理所有系统。

## Nmap 脚本

Nmap 对我们继续很有用，尽管我们已经超越了端口扫描阶段。在这里，我们希望使用提供的脚本收集更多信息。在撰写本文时，最新版 Kali Linux 的 nmap 实现中包含 33 个与 SMB 相关的脚本。接下来，你可以看到来自输出的一部分

