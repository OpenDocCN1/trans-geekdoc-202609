

![](img/ae7820c36e8f24c1623d26668b28e80e_950_0.png)

图 37.4 URI 信息概览

## 37.2.4 集成其他服务器技术

如果要集成其他脚本，PHP 通常会使用以下一种结构：include、include_once、require 或 require_once。但是，如果以这种方式包含的文件不包含任何 PHP 或 HTML 代码，则此方法会失败。在日益异构化的世界中，主网站可能运行在 PHP 下，但其中的部分内容仍可能是用 Perl 或其他技术实现的。

此时，清单 37.4 提供了一个非常简单的示例。假设您“继承”了一个 Perl 网站，但想将其转换为 PHP。然而，有一个脚本您根本无法在 PHP 中重建，因此希望继续使用它。

```
#!/usr/local/bin/perl
##
## Output environment variables
##
print "Content-type: text/html\n\n";
foreach $value (sort(keys(%ENV)))
{
    $value = $ENV{$value}; #Get environment variable
    $value =~ s/|\n|\n|g; #Make breaks visible
$value =~ s/[\\\"]//g; #escape quotation marks
print "$\{$value\}=\"\\"${value}\\"<br />\\n";
}
```

## 清单 37.4 “复杂”的 Perl 示例（“environment.pl”）

Perl 专家一眼就能认出清单 37.4 中的代码：它是 Apache 网络服务器随附的脚本（*printenv.pl*）的稍作修改版本。该脚本除了输出所有环境变量外，不做其他任何事情。

现在应在 PHP 脚本中调用此代码。当然，您可以使用 fopen() 执行脚本并输出返回值。但是，让 Apache 来完成此操作的性能要高得多。

Apache 支持通过以下指令按虚拟路径包含文件：

```
<!--#include virtual="/cgi-bin/environment.pl"-->
```

不幸的是，PHP 无法处理此问题。但请不要绝望：通过 virtual() 方法，也可以用 PHP 模拟此行为，前提是 PHP 作为 Apache 模块安装。清单 37.5 显示了完整的示例，该示例假设 Perl 脚本位于 /cgi-bin/environment.pl 下，并且 Perl 已正确安装。

```
<html>
<head>
<title>Environment Variables</title>
</head>
<body>
<h1>Perl provides the following information:</h1>
<pre>
<?php
virtual("/cgi-bin/environment.pl");
?>
</body>
</html>
```

## 清单 37.5 通过 PHP 调用 Perl 脚本（“virtual.php”）

## 37.2.5 终止 Apache 进程

作为最后一个示例，这里有一个适用于高端应用程序的内容。如果您有一个非常占用资源的脚本，在使用 Apache 时，之后终止 Apache 进程是个好主意，以便尽快释放占用的宝贵资源。好消息是，您也可以用 PHP 实现这一点。调用 apache_child_terminate() 函数会终止 Apache 的当前子进程。请放心：这不会终止 Apache 本身，而只是终止众多进程中的一个。

> **注意**
> >
> > 仅当 `php.ini` 中的 `child_terminate` 开关已设置为 `On` 时，才可使用此指令。

## 第 38 章 Composer

*PHP 功能广泛，但如果没有外部库，通常就不那么有用了。*
*Composer 包和依赖管理器让使用变得轻松。*

使用用 PHP 编写的库时，一个常见问题是：如何安装它们？过去，这通常意味着查找并阅读文档，然后希望相关库也能在本地系统上运行。但是，对于大多数软件来说，这已成为过去式，因为 Composer 自 2012 年以来就已存在。这是由 Nils Adermann 和 Jordi Boggiano（以及许多其他开源爱好者）开发的程序，也可用于解决依赖项。它可以通过命令行安装许多 PHP 库，包括任何其他所需的包。本章将向您介绍基础知识。

### 38.1 安装 Composer

Composer 的主页是 https://getcomposer.org（参见图 38.1）。除了常规文档外，还有安装说明。过程因操作系统而异。

在带有 curl 的系统上（即默认情况下除了 Windows 之外的所有系统），以下命令会在系统上安装管理器：

```
curl -sS https://getcomposer.org/installer | php
```

当然，也可以从指定的 URL（https://getcomposer.org/installer）手动下载数据并让 PHP 执行它（php -f name-of-downloaded-file）。原则上，安装程序以下载 PHAR 格式¹ 的 Composer，并创建一个名为 composer 的可执行脚本，可用于运行包管理器。

¹ PHAR 代表 PHP 归档（PHP archive），本质上是一个包含 PHP 代码的归档文件。可以将其视为 PHP 可以执行的完整应用程序。

![](img/ae7820c36e8f24c1623d26668b28e80e_954_0.png)

图 38.1 Composer 主页

此过程在 Windows 下也可行，但更简单：有一个 Windows 安装程序位于 https://getcomposer.org/Composer-Setup.exe，它会加载最新版本的 Composer，并自动设置 PATH 环境变量，以便您可以直接从命令提示符调用 composer。安装程序会检查一些 PHP 设置，包括是否安装了 OpenSSL 扩展，这对于通过 HTTPS 下载数据是必需的。如果没有，则在需要时会自动调整 php.ini（参见图 38.2）。对于出厂状态下的 PHP 安装，当前的设置如下：

```
extension=openssl
extension=mbstring
```

在安装过程中，因此还会要求您指定要使用的 PHP 安装位置（如果系统中有多个并行版本，这很重要）。

安装后，无论操作系统如何，如果您可以在终端中运行 composer，则说明全局安装成功（参见图 38.3）。如果不行，请使用本地变体。为此，搜索 composer.phar 文件并尝试以下调用：

```
php composer.phar
```

![](img/ae7820c36e8f24c1623d26668b28e80e_955_0.png)

图 38.2 Composer 的 Windows 安装程序

![](img/ae7820c36e8f24c1623d26668b28e80e_955_1.png)

图 38.3 Composer 安装成功。

### 38.2 通过 Composer 安装包

这可能是使用 Composer 安装包的最快方法：

```
composer require "aws/aws-sdk-php"
```

这会安装 Amazon AWS 云平台的 PHP SDK 的最新版本。以下是更具体版本的示例：

- `"aws/aws-sdk-php=3.0.0"`
  - 确切版本 3.0.0
- `"aws/aws-sdk-php=3.0.*"`
  - 至少版本 3.0.0，低于 3.1.0 的版本
- `"aws/aws-sdk-php>=3.0.0"`
  - 至少版本 3.0.0
- `"aws/aws-sdk-php>3.0.0"`
  - 高于 3.0.0 的版本
- `"aws/aws-sdk-php<=3.0.0"`
  - 最多版本 3.0.0
- `"aws/aws-sdk-php<3.0.0"`
  - 低于 3.0.0 的版本
- `"aws/aws-sdk-php^3.0.0"`
  - 至少版本 3.0.0，低于版本 4.0.0（因为那里的 API 可能会更改；推荐用于依赖项）

可能版本的完整列表可在在线手册 http://spr.co/v602256 中找到。但回到安装：AWS SDK 使用几个额外组件。Composer 知道这一点并会自动安装它们。图 38.4 展示了设置的实际情况：在 SDK 之前会下载其他组件。

![](img/ae7820c36e8f24c1623d26668b28e80e_956_0.png)

图 38.4 通过 Composer 安装 AWS SDK——包括依赖项！

这样，您可以手动在系统上设置和安装组件。当然，如果能将项目所需的外部库和包信息存储在项目内部会更好。

可以使用配置文件实现这一点。它必须包含 composer.json，并使用 JSON 格式（如文件扩展名所示）。特别是，它包含所有必需的包——例如：

```
{
    "require": {
        "aws/aws-sdk-php": "^3.297"
    }
}
```

此配置文件对应于图 38.4 中的调用。要安装 composer.json 中的所有包，请在 JSON 文件所在的同一目录下使用以下调用：

```
composer install
```

如果查看项目文件夹（参见图 38.5），您会发现 Composer 具有一个标准结构。vendor 目录包含各个包。这种命名方案也有助于您查找库。

![](img/ae7820c36e8f24c1623d26668b28e80e_957_0.png)

图 38.5 Composer 创建的目录结构

当然，您使用 Composer 安装的包（或其依赖项！）总有一天会有更新。与其手动查找，不如让 Composer 来完成工作：

```
composer update
```

