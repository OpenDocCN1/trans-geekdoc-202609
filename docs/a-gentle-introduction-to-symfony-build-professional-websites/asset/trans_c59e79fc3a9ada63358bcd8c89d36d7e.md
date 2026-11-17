

## PHP 配置

由于 PHP 配置在不同操作系统之间，甚至在不同 Linux 发行版之间可能差异很大，你需要检查你的 PHP 配置是否满足 symfony 的最低要求。

首先，使用 phpinfo() 内置函数或在命令行运行 php -v，确保已安装至少 PHP 5.2.4。请注意，在某些配置下，你可能安装了两个不同的 PHP 版本：一个用于命令行，另一个用于 Web。

然后，从以下 URL 下载 symfony 配置检查脚本：

```
Listing 3-2
http://sf-to.org/1.4/check.php
```

将脚本保存到当前 Web 根目录下的某个位置。

从命令行启动配置检查脚本：

```
Listing 3-3
$ php check_configuration.php
```

如果 PHP 配置有问题，命令的输出会给出修复什么以及如何修复的提示。

你还应该从浏览器执行检查器并修复它可能发现的问题。这是因为 PHP 对这两个环境可以有不同的独立 php.ini 配置文件，设置也不同。

之后别忘了从 Web 根目录中删除该文件。

如果你的目标是尝试 symfony 几个小时，可以按照本章末尾的描述安装 symfony 沙箱。如果你想引导一个真实世界项目，或想了解更多关于 symfony 的内容，请继续阅读。

## Symfony 安装

### 初始化项目目录

在安装 symfony 之前，你首先需要创建一个目录来存放与项目相关的所有文件：

```
Listing 3-4
$ mkdir -p /home/sfproject
$ cd /home/sfproject
```

或者在 Windows 上：

```
c:\> mkdir c:\dev\sfproject
c:\> cd c:\dev\sfproject
```

建议 Windows 用户在不包含空格的路径下运行 symfony 并设置新项目。避免使用“文档和设置”目录，包括“我的文档”下的任何位置。

如果你在 Web 根目录下创建 symfony 项目目录，则不需要配置 Web 服务器。当然，对于生产环境，我们强烈建议你按照 Web 服务器配置部分的说明配置 Web 服务器。

### 选择 Symfony 版本

现在，你需要安装 symfony。由于 symfony 框架有几个稳定版本，你需要通过阅读 symfony 网站上的安装页面20来选择要安装的版本。

### 选择 Symfony 安装位置

你可以在机器上全局安装 symfony，或者将其嵌入到每个项目中。后者是推荐的方法，因为项目之间将完全独立，升级本地安装的 symfony 不会意外地破坏某些项目。这也意味着你可以使用不同版本的 symfony 进行项目开发，并按需逐个升级。

作为最佳实践，许多人将 symfony 框架文件安装在 lib/vendor 项目目录中。因此，首先创建此目录：

```
$ mkdir -p lib/vendor
```

### 安装 Symfony

### 从存档安装

安装 symfony 的最简单方法是从 symfony 网站下载你选择的版本的存档。转到你刚刚选择的版本的安装页面，例如 symfony 1.421。

在“源码下载”部分，你将找到 .tgz 或 .zip 格式的存档。下载存档，将其放在新创建的 lib/vendor/ 目录下，解压缩，并将目录重命名为 symfony：

```
$ cd lib/vendor
$ tar zxpf symfony-1.4.0.tgz
$ mv symfony-1.4.0 symfony
$ rm symfony-1.4.0.tgz
```

在 Windows 上，可以使用资源管理器解压 zip 文件。将目录重命名为 symfony 后，应该会出现类似于 c:\dev\sfproject\lib\vendor\symfony 的目录结构。

20. http://www.symfony-project.org/installation
21. http://www.symfony-project.org/installation/1.4

### 从 Subversion 安装（推荐）

如果你的项目使用 Subversion，使用 svn:externals 属性将 symfony 嵌入到 lib/vendor/ 目录中的项目中会更好：

```
$ svn pe svn:externals lib/vendor/
```

如果一切顺利，此命令将运行你喜欢的编辑器，让你有机会配置外部 Subversion 来源。

> 在 Windows 上，你可以使用 TortoiseSVN22 等工具，无需使用控制台即可完成所有操作。

如果你比较保守，可以将项目绑定到特定版本（Subversion 标签）：

```
symfony http://svn.symfony-project.com/tags/RELEASE_1_4_0
```

每当有新版本发布（如 symfony 博客23所宣布），你都需要将 URL 更改为新版本。

如果你想走前沿路线，请使用 1.4 分支：

```
symfony http://svn.symfony-project.com/branches/1.4/
```

使用分支意味着，每次运行 svn update 时，你的项目都会自动获得错误修复。

### 安装验证

symfony 安装完成后，使用 symfony 命令行显示 symfony 版本来检查一切是否正常（注意大写 V）：

```
$ cd ../..
$ php lib/vendor/symfony/data/bin/symfony -V
```

在 Windows 上：

```
c:\> cd ../..
c:\> php lib\vendor\symfony\data\bin\symfony -V
```

创建项目后（见下文），运行此命令还会显示 symfony 安装目录的路径，该路径存储在 config/ProjectConfiguration.class.php 中。

如果检查时 symfony 的路径是绝对路径（默认情况下不应该是，如果你按照以下说明操作），请将其更改为如下形式，以便更具可移植性：

```
// config/ProjectConfiguration.class.php
require_once dirname(__FILE__).'./../lib/vendor/symfony/lib/autoload/sfCoreAutoload.class.php';
```

这样，你就可以将项目目录移动到机器上的任何位置或另一台机器，它都能正常工作。

22. http://tortoisesvn.net/
23. http://www.symfony-project.org/blog/

如果你对这个命令行工具能为你做什么感到好奇，请输入 symfony 以列出可用的选项和任务：

```
$ php lib/vendor/symfony/data/bin/symfony
```

在 Windows 上：

```
c:\> php lib\vendor\symfony\data\bin\symfony
```

symfony 命令行是开发者的好帮手。它提供了许多实用程序，可提高你在日常活动（如清除缓存、生成代码等）中的工作效率。

## 项目设置

在 symfony 中，共享相同数据模型的 **应用程序** 被分组到 **项目** 中。对于大多数项目，你会有两个不同的应用程序：前端和后端。

### 创建项目

从 sfproject/ 目录运行 symfony generate:project 任务以实际创建 symfony 项目：

```
$ php lib/vendor/symfony/data/bin/symfony generate:project PROJECT_NAME
```

在 Windows 上：

```
c:\> php lib\vendor\symfony\data\bin\symfony generate:project PROJECT_NAME
```

generate:project 任务生成 symfony 项目所需的默认目录和文件结构。

> 为什么 symfony 会生成这么多文件？使用全栈框架的主要好处之一是标准化你的开发。得益于 symfony 默认的文件和目录结构，任何具备一些 symfony 知识的开发者都可以接手任何 symfony 项目的维护工作。几分钟内，他就能深入代码，修复错误并添加新功能。

generate:project 任务还在项目根目录中创建了一个 symfony 快捷方式，以减少运行任务时需要输入的字符数。

因此，从现在开始，不再使用 symfony 程序的完全限定路径，而可以使用 symfony 快捷方式。

### 配置数据库

symfony 框架开箱即用支持所有 PDO24支持的数据库（MySQL、PostgreSQL、SQLite、Oracle、MSSQL 等）。在 PDO 之上，symfony 包含两个 ORM 工具：Propel 和 Doctrine。

创建新项目时，Doctrine 默认启用。配置 Doctrine 使用的数据库就像使用 configure:database 任务一样简单：

24. http://www.php.net/PDO

