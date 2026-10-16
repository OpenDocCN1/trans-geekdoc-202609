

## 2. 编写你的第一个PHP脚本

接下来，在终端窗口中，以超级用户身份运行以下命令，使用 apt 安装包管理器升级所有应用程序：

```
sudo apt upgrade
```

你需要输入 Y 或按 Enter 键以接受更改。此更新可能需要几分钟时间，因为包管理器将升级自 Ubuntu 20.04.3 LTS 发布以来所有已更新的程序包（图 2.7、2.8 和 2.9）。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_28_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_28_1.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_28_2.png)

### 安装并测试 Apache

在终端窗口中，以超级用户身份运行以下命令，使用 apt 安装包管理器安装 Apache：

```
sudo apt install apache2
```

你需要输入 Y 或按 Enter 键以接受更改（图 2.10）。

为确保 Apache 正在运行，请在终端窗口中作为超级用户运行以下命令。你应该会看到如图 2.11 所示的输出。

```
sudo systemctl status apache2
```

按 q 键退出 systemctl status 命令。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_29_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_29_1.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_29_2.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_29_3.png)

## 2. 编写你的第一个PHP脚本

确保 Apache 正在运行的最佳方法是打开一个 Web 浏览器并导航到 localhost。如果你看到如图 2.12 所示的网页，则可以确信你的 Apache 安装正在运行。

### 安装并测试 MySQL

在终端窗口中，以超级用户身份运行以下命令，使用 apt 安装包管理器安装 MySQL 服务器和客户端。

```
sudo apt install mysql-server mysql-client
```

你需要输入 Y 或按 Enter 键以接受更改（图 2.13）。

为确保 MySQL 正在运行，请在终端窗口中作为超级用户运行以下命令。

```
sudo systemctl status mysql
```

启动输出如图 2.14 所示。

按 q 键退出 systemctl status 命令。

### 安装、配置并测试 PHP

在撰写本文时，Ubuntu 20.04.3 LTS 的默认 PHP 版本为 7.4。本书中的所有代码都应能在 PHP 7.2 或更高版本上良好运行。

在终端窗口中，以超级用户身份运行以下命令，使用 apt 安装包管理器安装 PHP 及受支持的模块：

```
sudo apt install php php-mysql php-curl php-json php-cgi libapache2-mod-php
```

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_30_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_30_1.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_30_2.png)

### 设置开发环境

你需要输入 Y 或按 Enter 键以接受更改（图 2.15）。

通过在终端窗口中运行以下命令来验证 PHP 是否已安装：

```
php -v
```

你应该会看到如图 2.16 所示的输出。

默认情况下，PHP 安装时关闭了错误报告。这个默认设置是件好事，因为我们不希望向潜在的黑客暴露我们已部署网站上文件的位置或漏洞。由于我们正在创建开发环境，我们需要在出现 PHP 错误时能够得知。

我们的大部分 PHP 配置设置都位于 php.ini 文件中。我们将使用 Ubuntu 自带的 nano 编辑器来修改此文件，以显示我们的错误。

在终端窗口中，输入以下命令来编辑 php.ini 文件：

```
sudo nano /etc/php/7.4/apache2/php.ini
```

你需要使用 nano 中的 ^W“Where Is”命令（ctrl+W）搜索第二次出现的 display_errors，并将其从 Off 改为 On（图 2.17）。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_31_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_31_1.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_31_2.png)

## 2. 编写你的第一个PHP脚本

然后使用 ^O（Ctrl 加大写字母 O）“Write Out”命令（ctrl+O）写出更改。接下来，按回车键确认要写出的文件名。最后，使用 ^X 退出命令（ctrl+X）退出 nano。参见图 2.18。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_32_0.png)

在终端窗口中，输入以下命令以重启 Apache，使这些更改生效：

```bash
sudo systemctl restart apache2
```

### 安装数据库管理工具 Adminer

接下来，我们要安装一个基于 Web 的数据库管理工具。市面上有几个这样的工具，最流行的是 phpMyAdmin[1]。不过，我喜欢使用一个名为 Adminer 的工具，因为它包含在单个 PHP 文件中，运行速度更快，并且以更高的安全性著称。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_32_1.png)

打开浏览器并导航到 Adminer 下载页面[2]。从那里，选择最新的适用于 MySQL 的 Adminer 版本，如图 2.19 所示。

这样做会将 Adminer PHP 文件下载到你的“下载”文件夹中。

接下来，我们需要将此文件重命名为 index.php，并将其复制到我们的 html/ 文件夹中，Apache 会从这个文件夹提供网页服务。我们的 html/ 文件夹的根目录位于 /var/www/html。最好的方法是使用终端窗口。

在终端窗口中，输入以下命令 cd 到 /var/www/html 目录：

```bash
cd /var/www/html
```

命令的输出如图 2.20 所示。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_32_2.png)

[1] phpMyAdmin：https://www.phpmyadmin.net/

[2] Adminer 下载页面：https://www.adminer.org/#download

由于 root 用户拥有 html/ 目录，我们需要使用超级用户权限在此移动 Adminer PHP 文件。让我们首先创建一个名为 adminer 的新文件夹，并通过在终端窗口中输入以下命令切换到该文件夹（输出如图 2.21 所示）：

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_33_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_33_1.png)

```
sudo mkdir adminer
cd adminer
```

现在，让我们以超级用户身份输入以下命令（图 2.22），将下载的 PHP 文件从我们的“下载”目录移动到 adminer 目录，并将其重命名为 index.php：

```
sudo mv ~/Downloads/adminer-4.7.7-mysql-en.php index.php
```

### 创建一个测试数据库用户和数据库

默认情况下，我们不能使用 root 账户访问 MySQL 数据库。这一默认设置是一个可靠的安全约束。为了让我们能够使用 Adminer——或者说 PHP——访问我们的数据库，我们需要以 root 身份使用 MySQL 命令行界面（CLI）工具来创建一个数据库用户账户，并为该用户授予对某个数据库的访问权限。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_33_2.png)

在终端窗口中，输入以下命令进入 MySQL CLI：

```
sudo mysql
```

然后，在出现提示时输入你的密码，如图 2.23 所示。

## 2. 编写你的第一个PHP脚本

现在，让我们在 MySQL CLI 中输入以下命令（图 2.24）来创建一个名为 testdb 的测试数据库：

```
CREATE DATABASE testdb;
```

接下来，我们需要为数据库创建一个带密码的用户，因此输入以下命令：

```
CREATE USER 'testuser'@'localhost' IDENTIFIED BY 'testuser';
```

该命令应该如图 2.25 所示。

最后，我们需要为我们的 testuser 授予对 testdb 数据库的所有权限。输入以下命令（图 2.26）：

```
GRANT ALL PRIVILEGES ON testdb.*
TO 'testuser'@'localhost';
```

作为标准做法，最好也刷新数据库的权限。参见图 2.27。

```
FLUSH PRIVILEGES;
```

输入 quit 退出 MySQL CLI（图 2.28）。

为确保 Adminer 正常运行，请打开浏览器并导航到 http://localhost/adminer/。在用户名处输入 testuser，密码输入你在 MySQL CLI 中创建 testuser 账户时选择的密码（testuser），然后按图 2.29 所示登录。

如果你看到如图 2.30 所示的网页，则说明 Adminer 正常工作，MySQL 也已正确安装并运行。

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_34_0.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_34_1.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_34_2.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_34_3.png)

![](img/83a2e1d9463a10cf8d6f7fe54ee4b1c7_34_4.png)

