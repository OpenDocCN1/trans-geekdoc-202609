

# XAMPP Windows 安装指南

## 下载选项
- **[7zip](https://sourceforge.net/projects/xampp/files/XAMPP%20Windows/7.0.8/xampp-portable-win32-7.0.8-0-VC14.7z/download)**：适合带宽较低的纯粹主义者（XAMPP 7zip 压缩包）。

## 如何安装以及将 PHP/HTML 文件放在哪里？

### 方法 1：使用提供的安装程序安装
1. 双击下载的 `.exe` 文件执行 XAMPP 服务器安装程序。

### 方法 2：从 ZIP 压缩包安装
1. 将 zip 压缩包解压到您选择的文件夹中。
2. XAMPP 将解压到所选目标目录下的 `\xampp` 子目录中。
3. 现在启动文件 `setup_xampp.bat` 以将 XAMPP 配置调整为您的系统。

> **注意：** 如果您选择根目录 `C:\` 作为目标，则不得启动 `setup_xampp.bat`。

## 安装后
使用 **“XAMPP 控制面板”** 执行其他任务，如启动/停止 Apache、MySQL、FileZilla 和 Mercury，或将这些安装为服务。

## 文件处理
安装过程非常简单。完成后，您可以将要在服务器上托管的 HTML/PHP 文件添加到 `XAMPP\root\htdocs\` 中。然后启动服务器并在浏览器中打开 `http://localhost/file.php` 以查看页面。

> **注意：** Windows 中默认的 XAMPP 根目录是 `C:\xampp\htdocs`。

在您喜爱的 Web 浏览器中输入以下 URL 之一：
- `http://localhost`
- `http://127.0.0.1`

现在您应该能看到 XAMPP 启动页面。

---

# 附录 B：在 Linux/Unix 环境中安装

## 第 B.1 节：使用 APT 通过命令行安装 PHP 7

```bash
sudo add-apt-repository ppa:ondrej/php
```

> **注意：** 这将仅安装 PHP。如果您希望向 Web 提供 PHP 文件，还需要安装 Web 服务器，例如 [Apache](http://www.apache.org/)、[Nginx](https://www.nginx.com/)，或使用 [PHP 内置 Web 服务器](http://php.net/manual/en/features.commandline.webserver.php)（PHP 5.4+ 版本）。

如果您使用的是 16.04 以下版本的 Ubuntu 但仍想使用 PHP 7，可以通过以下方式添加 [Ondrej 的 PPA 仓库](https://launchpad.net/~ondrej/+archive/ubuntu/php/)：

确保您所有的 [软件仓库](https://en.wikipedia.org/wiki/Software_repository) 都是最新的：

```bash
sudo apt-get update
```

更新系统仓库后，安装 PHP：

```bash
sudo apt-get install php7.0
```

让我们通过检查 PHP 版本来测试安装：

```bash
php -v
```

这应该输出类似如下内容（您的输出会略有不同）：

```
PHP 7.0.8-0ubuntu0.16.04.1 (cli) ( NTS )
Copyright (c) 1997-2016 The PHP Group
Zend Engine v3.0.0, Copyright (c) 1998-2016 Zend Technologies
    with Zend OPcache v7.0.8-0ubuntu0.16.04.1, Copyright (c) 1999-2016, by Zend Technologies
    with Xdebug v2.4.0, Copyright (c) 2002-2016, by Derick Rethans
```

您现在已经具备了从命令行运行 PHP 的能力。

## 第 B.2 节：在企业级 Linux 发行版中安装（CentOS、Scientific Linux 等）

在基于企业级 Linux 的操作系统中使用 `yum` 命令管理软件包：

```bash
yum install php
```

这将安装包含一些常用功能的最小化 PHP。如果您需要额外的模块，则需要单独安装。您同样可以使用 `yum` 来搜索这些软件包：

```bash
yum search php-
```

**示例输出：**
```
php-bcmath.x86_64 : 用于 PHP 应用程序使用 bcmath 库的模块
php-cli.x86_64    : PHP 的命令行界面
php-common.x86_64 : PHP 的通用文件
php-dba.x86_64    : 用于 PHP 应用程序的数据库抽象层模块
php-devel.x86_64  : 构建 PHP 扩展所需的文件
php-embedded.x86_64 : 用于嵌入应用程序的 PHP 库
php-enchant.x86_64 : 人类语言和字符编码支持
php-gd.x86_64     : 用于 PHP 应用程序使用 gd 图形库的模块
php-imap.x86_64   : 用于使用 IMAP 的 PHP 应用程序的模块
```

安装 `gd` 库：

```bash
yum install php-gd
```

企业级 Linux 发行版在更新方面一向保守，通常不会更新到超出其发布时的版本。许多第三方仓库提供当前版本的 PHP：
- [IUS](https://ius.io/)
- [Remi Colette](http://www.remirepo.net/)
- [Webtatic](https://webtatic.com/)

