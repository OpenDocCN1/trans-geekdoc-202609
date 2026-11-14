

可以通过 Apache 安装程序创建的“开始”菜单条目访问这些命令的快捷方式。如果将 Apache 安装为服务，可以使用 Windows 服务界面启动或停止 Apache：在控制面板中，选择“管理工具”，然后单击“服务”图标。

## Apache 控制脚本

尽管可以在 Linux/UNIX 上使用 httpd 二进制文件来控制 Apache，但建议使用 apachectl 工具。apachectl 支持程序将常见功能封装在易于使用的脚本中。要使用 apachectl，请键入以下内容：

```
# /usr/local/apache2/bin/apachectl command
```

在此语法中，*command* 可以是 stop、start、restart 或 graceful。你也可以编辑 apachectl 脚本的内容以添加额外的命令行选项。某些操作系统发行版提供用于控制 Apache 的其他脚本；请查看随发行版提供的文档。

## 首次启动 Apache

在启动 Apache 之前，应验证 Apache 配置文件 `httpd.conf` 中是否存在所需的最小信息集。以下各部分介绍了配置 Apache 并启动服务器所需的基本信息。

## 检查配置文件

可以使用喜欢的文本编辑器编辑 Apache `httpd.conf` 文件。在 Linux/UNIX 和 Mac OS X 上，这可能指的是 `vi` 或 `emacs`。在 Windows 上，可以使用“记事本”或“写字板”。必须记住以纯文本格式保存配置文件，这是 Apache 唯一能理解的格式。

要首次启动 Apache，可能只需更改两个参数：服务器名称以及监听的地址和端口。服务器名称是 Apache 在需要引用自身时会使用的名称（例如，重定向请求时）。Apache 通常可以从计算机的 IP 地址推断出服务器名称，但并非总是如此。如果服务器没有有效的 DNS（域名服务）条目，可能需要指定计算机的某个 IP 地址。如果服务器未连接到网络（你可能希望在独立计算机上测试 Apache），可以使用值 127.0.0.1，即回环地址。默认端口值为 80。如果计算机上已在端口 80 运行服务器，或没有管理员权限，则可能需要更改此值——在 Linux/UNIX 和 Mac OS X 系统中，只有 root 用户可以绑定到特权端口（即端口号低于 1024 的端口）。

可以使用 Listen 指令更改监听地址和端口值。Listen 指令接受端口号，或 IP 地址和端口（两者之间用冒号分隔）。如果仅指定端口，Apache 将在计算机上所有可用 IP 地址的该端口上监听。如果提供其他 IP 地址，Apache 将仅监听该地址和端口组合。例如，Listen 80 告诉 Apache 在端口 80 上监听所有 IP 地址的请求。Listen 10.0.0.1:443 告诉 Apache 仅监听 10.0.0.1 的端口 443。

ServerName 指令允许你定义服务器在任何自引用 URL 中将报告的名称。该指令接受 DNS 名称和可选端口（两者之间用冒号分隔）。确保 ServerName 具有有效值。否则，服务器将无法正常工作；例如，它会发出错误的重定向。

在 Linux/UNIX 和 Mac OS X 平台上，可以使用 User 和 Group 指令来指定服务器以哪个用户 ID 和组 ID 运行。nobody 用户是大多数平台的不错选择。但是，HP-UX 平台上存在此用户 ID 的问题，因此必须创建并使用不同的用户 ID，例如 www。

## 启动 Apache

要在 Linux/UNIX 上启动 Apache，请切换到包含 apachectl 脚本的目录并执行以下命令：

```
# /usr/local/apache2/bin/apachectl start
```

Mac OS X 用户可以在提示符下键入以下内容：

```
# /usr/sbin/httpd
```

要在 Windows 上手动启动 Apache，请在“开始”菜单的“Apache HTTP Server 2.2”程序组的“控制 Apache 服务器”部分中，单击“控制台中启动 Apache”链接。如果将 Apache 安装为服务，则必须改为启动 Apache 服务。

如果一切正常，可以使用浏览器访问 Apache。将显示默认安装页面，如图 3.4 所示。如果无法启动 Web 服务器，或出现错误页面，请参阅以下的“疑难解答”部分。确保正在访问 Listen 指令中指定的端口之一——通常是端口 80 或 8080。

![](img/be3c5789b9e58d6dc55dc804718f15b4_61_0.png)

图 3.4 Apache 默认安装页面。

## 疑难解答

以下小节介绍首次启动 Apache 时可能遇到的几个常见问题。

### 已存在的 Web 服务器

如果计算机上已有服务器在运行，并且正在监听相同的 IP 地址和端口组合，Apache 将无法成功启动。错误日志文件中会出现一条条目，指示 Apache 无法绑定到端口：

```
[crit] (48)Address already in use: make_sock: could not bind..[alert] no listening sockets available, shutting down
```

要解决此问题，需要停止运行中的服务器，或更改 Apache 配置以在不同端口上监听。

### 没有绑定端口的权限

如果没有管理员权限且尝试绑定到特权端口（0 到 1024 之间），将收到错误：

```
[crit] (13)Permission denied: make_sock: could not bind to address 10.0.0.2:80 [alert] no listening sockets available, shutting down
```

要解决此问题，必须在启动 Apache 之前以管理员身份登录，或更改端口号（8080 是常用的非特权端口）。

### 访问被拒绝

如果没有权限读取配置文件或写入日志文件，可能无法启动 Apache。将收到类似于以下的错误：

```
(13)Permission denied: httpd: could not open error log file
```

如果构建和安装 Apache 的用户与尝试运行它的用户不同，可能会出现此问题。

### 组设置错误

可以配置 Apache 在特定用户名和组下运行。Apache 为运行服务器的用户名和组提供默认值。有时默认值无效，你会收到包含 setgid: unable to set group id 的错误。

要在 Linux/UNIX 和 Mac OS X 上解决此问题，必须将配置文件中 Group 指令的值更改为有效值。检查 /etc/groups 文件以查看现有组。

## 安装和配置 PHP

在三个与安装相关的章节的最后一章中，你将获取、安装和配置 PHP，并对 Apache 安装进行一些基本更改。

### PHP 的当前版本和未来版本

本章中的安装说明指的是 PHP 版本 5.2.5，这是该软件的当前版本。

> 注意：如果已在生产环境中使用 PHP 4.x.x，或希望继续使用 4.x.x 开发树，请访问 PHP 手册中的“安装和配置”部分：http://www.php.net/install。
> 
> 由于 PHP 5 已使用超过三年，且 PHP 6 可能会在 2009 年投入生产使用，PHP 4 的状态官方已为“生命周期结束”——这意味着 PHP 组自 2007 年 12 月 31 日以来未对 PHP 4 进行任何更新。有关更多信息，请访问：http://www.php.net/archive/2007.php#2007-07-13-1。
> 
> 本工具包中的代码假设使用 PHP 5 而不是 PHP 4；在某些情况下，两个版本之间的代码没有区别，但你应该熟悉两个版本之间的差异，以便做出相应调整。

