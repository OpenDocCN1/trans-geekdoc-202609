

```
herong> \php\php PassingObjectAsArguments.php

Test on updating object identified by variable content:
   a: Large
   b: Large
   z: Large
Test on updating variable content:
   a: Medidum
   b: Large
   z: Large
```

输出结果证实了我之前的理解。

还要注意：

*   `return` 语句仅支持按值传递模式。无法返回变量的引用。
*   PHP 不再支持调用时按引用传递。`$x = f(&$a)` 不再有效。
*   只有变量可以在调用语句中按引用传递。如果 `f()` 声明为 `f(&$aa)`，则不允许 `$x = f("Hello")`。

# PHP 教程 - Herong 的教程示例

## 将 PHP 与 Apache Web 服务器集成

本章提供了在 Windows 系统上安装 Apache Web 服务器的教程笔记。主题包括下载和安装 Apache 2.4.12 二进制分发版；配置 Apache 将 PHP 作为 CGI 脚本运行以及使用 Apache PHP 加载模块；在 Apache 服务器上测试 PHP 脚本。

> [下载适用于 Windows 的 Apache 2.4.37 二进制版](#part0093.xhtml)
>
> [在 Windows 系统上安装 Apache 2.4.37](#part0094.xhtml)
>
> [将 HTML 文档发布为网页](#part0095.xhtml)
>
> [启动和停止 Apache 服务器](#part0096.xhtml)
>
> [为 PHP CGI 脚本配置 Apache](#part0097.xhtml)
>
> [将 PHP 脚本发布为网页](#part0098.xhtml)
>
> [php-cgi.exe 权限错误](#part0099.xhtml)
>
> [配置 Apache PHP 加载模块](#part0100.xhtml)

### 要点

*   Apache HTTP Server 是互联网上最常用的开源 Web 服务器。它在 Windows 系统上非常易于安装和设置。
*   在 Windows 上安装 Apache Web 服务器非常简单。你只需下载分发 ZIP 文件并解压即可。
*   你应该选择 Apache VC15 和 64 位构建版本，以匹配之前安装的 PHP 引擎构建版本，从而避免任何兼容性问题。
*   将 Apache Web 服务器与 PHP 引擎集成以使用 `php-cgi.exe` 运行 PHP 脚本，需要在 Apache 配置文件中进行多项更改。
*   使用 Apache PHP 加载模块将 PHP 脚本作为网页运行，效率更高且更安全。

# PHP 教程 - Herong 的教程示例

## 将 PHP 与 Apache Web 服务器集成

### 下载适用于 Windows 的 Apache 2.4.37 二进制版

本节介绍如何下载适用于 Windows 的 Apache 2.4.37 二进制分发版。你应该选择 VC15 和 64 位构建版本，以匹配 PHP 引擎的构建版本。

为了将 PHP 脚本作为网页提供服务，你需要有一个正在运行并与 PHP 引擎集成的 Web 服务器。目前最流行的 Web 服务器是 Apache (HTTP Server)。以下是我下载适用于 Windows 的 Apache 2.4.37 二进制分发版的步骤：

1.  访问 Apache Lounge 网站 [apachelounge.com/](https://www.apachelounge.com/)。
2.  点击左侧菜单中的“Downloads”。你将看到下载页面。
3.  点击左侧菜单中的“VC15”，因为我下载并安装了 PHP VC15 (Visual C++ v15) 构建版本。
4.  在 Apache 2.4.37 Win64 标题下选择 `httpd-2.4.37-win64-VC15.zip` 开始下载，因为我下载并安装了 PHP 64 位构建版本。
5.  将下载的文件 `httpd-2.4.37-win64-VC15.zip`（17,764,403 字节）保存在临时目录中。

你应该选择 VC15 和 64 位构建版本，以匹配之前安装的 PHP 引擎构建版本。

# PHP 教程 - Herong 的教程示例

## 将 PHP 与 Apache Web 服务器集成

### 在 Windows 系统上安装 Apache 2.4.37

本节介绍如何在 Windows 系统上安装 Apache 2.4.37 二进制分发版。服务器根目录设置需要更改以匹配安装目录。

下载 Apache HTTP Server 2.4.37 后，我继续在 Windows 系统上安装它：

1.  解压 `httpd-2.4.37-win64-VC15.zip`。你将看到一个名为 `.\\Apache24` 的子目录。
2.  复制并重命名 `.\\Apache24` 子目录为 `\\apache`。
3.  在文本编辑器中打开 `\\apache\\conf\\httpd.conf`，通过注释掉原始设置并复制一行新设置，将服务器根目录更改为匹配我的安装目录：

```
# Define SRVROOT "c:/Apache24"
Define SRVROOT "c:/apache"
```

4.  通过运行以下命令启动 Apache Web 服务器：

```
herong> \apache\bin\httpd
```

5.  使用 Web 浏览器打开 `http://localhost`。你应该会看到 Apache 服务器默认主页显示：

```
It works!
```

恭喜，Apache Web 服务器已安装并正常工作！

# PHP 教程 - Herong 的教程示例

## 将 PHP 与 Apache Web 服务器集成

### 将 HTML 文档发布为网页

本节介绍如何在 Apache HTTP 服务器上发布 HTML 文档。

Apache 服务器运行后，我准备好将 HTML 文档发布为静态网页。以下是一个使用文本编辑器创建的简单 HTML 文档 `hello.html`：

```
<html>
<body>
Hello world!
</body>
</html>
```

要将此 HTML 文档发布为网页，我将其复制到 Apache 文档目录 `\\apache\\htdocs`：

```
herong> copy hello.html \apache\htdocs
```

然后我在 `http://localhost/hello.html` 查看该页面，正确显示了页面内容。

```
Hello world!
```

# PHP 教程 - Herong 的教程示例

## 将 PHP 与 Apache Web 服务器集成

### 启动和停止 Apache 服务器

本节介绍如何使用启动和停止脚本来启动和停止 Apache 服务器。Windows 任务管理器也可用于停止 Apache 服务器。

1.  启动和停止 Apache 服务器的常规方法是使用 ApacheMonitor 程序，运行以下命令：

```
herong> \apache\bin\ApacheMonitor.exe
```

2.  查看任务栏区域。你将看到一个 Apache 监视器图标出现。
3.  点击 Apache 监视器图标。你将看到 3 个子菜单项：Start、Stop 和 Restart。你可以随时使用它们来启动和停止 Apache 服务器。
4.  判断 Apache 服务器是否正在运行的另一种方法是使用 Windows 任务管理器。运行 Windows 任务管理器，然后点击“进程”选项卡。如果你看到 `httpd.exe` 列为正在运行的进程，则知道你的 Apache 服务器正在运行。
5.  当然，Windows 任务管理器也可用于停止 Apache 服务器。在 Windows 任务管理器的“进程”选项卡上选择 `httpd.exe`，然后点击“结束进程”按钮。在警告消息上点击“是”以终止 `httpd.exe`。如果看到多个 `httpd.exe` 实例，请重复该过程。

# PHP 教程 - Herong 的教程示例

## 将 PHP 与 Apache Web 服务器集成

### 为 PHP CGI 脚本配置 Apache

本节介绍如何配置 Apache 服务器以支持 PHP CGI 脚本。

在我的 Windows 系统上同时安装了 PHP 引擎和 Apache Web 服务器后，我继续配置 Apache 服务器以支持 PHP CGI 脚本：

1.  在文本编辑器中打开 Apache 配置文件 `\\apache\\conf\\httpd.conf`
2.  首先我必须定义一个 CGI 脚本目录别名，将 Apache 文档目录映射到 `php-cgi.exe` 所在的真实目录。转到 `alias_module` 部分并添加一行：

```
<IfModule alias_module>
...
   ScriptAlias /cgi-bin-php/ "/local/php/"
</IfModule>
```

3.  然后我需要为此目录添加一个访问控制部分：

```
<Directory "/local/php/">
     AllowOverride None
     Options None
     Require all granted
</Directory>
```

4.  接下来，我必须定义一个新的 MIME 类型以支持 `.php` 文件扩展名。转到 `mime_module` 部分并添加一行：

```
<IfModule mime_module>
...
    AddType application/x-httpd-php .php
</IfModule>
```

5.  最后一个设置是告诉 Apache 使用位于目录别名 `/cgi-bin-php/` 中的 `php-cgi.exe` 来提供新的 MIME 类型：在 LoadModule 部分下方的根级别，定义一个“Action”条目：

