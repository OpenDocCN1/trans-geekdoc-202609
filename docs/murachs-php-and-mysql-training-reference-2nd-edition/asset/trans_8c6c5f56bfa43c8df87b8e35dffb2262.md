
## 如何启动和停止 Apache 和 MySQL 服务器

完成基本安装后，您可以通过第 C-3 图第 2 部分所述的方法启动和停止 Apache 和 MySQL 服务器来进行测试。

启动 Apache 服务器后，您可以通过启动网页浏览器并导航到以下目录来测试它：

```text
http://localhost/xampp
```

如果此 URL 显示网页，则表示您已成功安装并启动了 Apache 服务器。

## 如何更改 htdocs 目录的所有权

第 C-3 图第 2 部分还向您展示了如何更改 htdocs 目录的所有权，使其归属于您的用户账户。我们建议这样做，因为它使使用本书的应用程序和练习变得容易得多。

## XAMPP 默认安装位置

```
/opt/lampp
```

## XAMPP 控制面板

![](img/b7dd5fec6684a99ab526c7fe8e21e7de_870_0.png)

## 如何启动和停止 Apache 和 MySQL 服务器

- 1. 打开终端并通过输入以下命令切换到 /opt/lampp 目录：
- `cd /opt/lampp`
- 2. 启动 XAMPP 管理器。对于 Linux 的 64 位版本，您可以输入以下命令：
- `sudo ./manager-linux-x64.run`
- 对于 Linux 的 32 位版本，您可以输入以下命令：
- `sudo ./manager-linux-x86.run`
- 3. 在提示时输入 root 密码。
- 4. 单击“管理服务器”按钮。
- 5. 使用“启动”和“停止”按钮启动或停止相应的服务器。

## 可用于测试 Apache 服务器的 URL

```
http://localhost/xampp
```

## 如何更改 htdocs 目录的所有权

- 1. 打开终端并切换到 /opt/lampp 目录。
- 2. 输入以下命令，将 your_username 替换为您的 Linux 登录名：
- `sudo chown your_username htdocs`
- 3. 如有必要，输入 root 密码。

## 注释

- - 在 Linux 上启动 Apache 和 MySQL 后，它们在重新启动计算机时可能会停止。在这种情况下，您可能需要在进行任何 PHP 开发之前重新启动 Apache 和 MySQL。

Figure C-3    如何安装 XAMPP（第 2 部分，共 2 部分）

## 如何配置 phpMyAdmin

XAMPP 包含一个用于处理 MySQL 的基于 Web 的工具，名为 phpMyAdmin。默认情况下，phpMyAdmin 会将其配置文件中存储 MySQL root 用户的用户名和密码，该文件是纯文本文件。由于这不安全，因此通常被认为是一种良好的做法来修改这些默认设置。

我们建议将 phpMyAdmin 的身份验证类型从“config”更改为“cookie”，如第 C-4 图所示。当您使用“cookie”身份验证类型时，phpMyAdmin 不会在其配置文件中存储任何用户名或密码。相反，它在启动时会提示用户输入用户名和密码，并将用户名和密码存储在用户浏览器中的 cookie 中。

修改 phpMyAdmin 的配置文件后，您可以使用本图中的第二个过程来确保 MySQL 服务器正常工作，并确保 phpMyAdmin 已正确配置。

## phpMyAdmin 配置文件的默认位置

```
/opt/lampp/phpmyadmin/config.inc.php
```

## 如何为 phpMyAdmin 配置身份验证

- 1. 打开终端并切换到 `/opt/lampp/phpmyadmin` 目录。
- 2. 通过输入以下命令打开 `config.inc.php` 文件进行编辑：
- ```bash
sudo gedit config.inc.php
```
- 3. 将“blowfish_secret”选项设置为最多 46 个字符的随机字符串。这指定了 cookie 的加密密钥。
- 4. 将“auth_type”选项的值设置为“cookie”。
- 5. 将“user”和“password”选项设置为空字符串。
- 6. 保存您的更改。

## 默认设置

```php
$cfg['blowfish_secret'] = 'xampp'; /* YOU SHOULD CHANGE THIS FOR A MORE
SECURE COOKIE AUTH! */

/* Authentication type and info */
$cfg['Servers'][$i]['auth_type']      = 'config';
$cfg['Servers'][$i]['user']           = 'root';
$cfg['Servers'][$i]['password']       = '';
```

## phpMyAdmin 已为身份验证配置后的设置

```php
$cfg['blowfish_secret'] = 'd2k0vc93ms28si29';

/* Authentication type and info */
$cfg['Servers'][$i]['auth_type']      = 'cookie';
$cfg['Servers'][$i]['user']           = '';
$cfg['Servers'][$i]['password']       = '';
```

## 如何使用 phpMyAdmin 测试 MySQL 服务器

- 1. 使用第 C-3 图所述的 XAMPP 控制面板启动 Apache 和 MySQL 服务器。
- 2. 启动 Chrome 并输入此 URL：
- ```text
http://localhost/phpmyadmin/
```
- 这应该启动 phpMyAdmin 并提示您输入用户名和密码。如果没有，请单击“注销”链接以进入登录页面。
- 3. 通过指定用户名为“root”并输入 root 用户的密码以 root 用户身份登录。默认情况下，root 用户没有密码，因此您无需输入任何内容。当您成功以 root 用户身份登录时，phpMyAdmin 应显示其主页。此时，MySQL 服务器和 phpMyAdmin 都正常工作。

Figure C-4    如何配置 phpMyAdmin

## 如何安装 NetBeans

我们建议您使用本书的 PHP 版 NetBeans IDE，因为它使您更容易输入、编辑和运行构成 Web 应用程序的各种文件。此外，我们建议您将 XDebug 调试器配置为与 NetBeans 一起使用，因为它使调试 PHP 应用程序变得更容易。

## 如何安装 NetBeans

第 C-5 图显示了如何安装 PHP 版 NetBeans IDE。由于这与大多数安装程序的工作方式类似，您不应该对该过程有任何困难。如果遇到任何问题，您可以查看 NetBeans 网站上提供的文档并参考故障排除提示。

请注意，NetBeans 需要 Java 才能运行。但是，Ubuntu 默认未安装 Java。因此，在 Ubuntu 上尝试安装 NetBeans 可能会失败，因为 NetBeans 找不到 Java。如果失败，您可以按照本图中的过程在 Ubuntu 上安装 Java。Fedora 默认随 Java 一起安装，因此在 Fedora 上安装应该可以正常工作。

## NetBeans 网站

[NetBeans 官网](http://netbeans.org)

## 安装 Java 的命令（仅限 Ubuntu）

- 1. 打开终端并输入以下命令：

```
sudo apt-get install default-jre
```

## 如何安装 NetBeans

- 1. 前往 NetBeans 网站。
- 2. 下载支持 PHP 的 NetBeans IDE 的安装程序（.sh）文件。该文件应位于 HTML5 和 PHP 标题下，名称类似于 `netbeans-8.0.1-php-linux.sh`。
- 3. 打开终端并切换到 Downloads 目录。
- 4. 使文件可执行。为此，您可以输入：
- 5. 运行文件。为此，输入：
- 6. 按照 NetBeans 设置向导中的说明进行操作。

```
chmod u+x netbeans-8.0.1-php-linux.sh
```

通常，如果有必要，请将此处显示的文件名替换为您系统上的文件名。

```
sudo ./netbeans-8.0.1-php-linux.sh
```

Figure C-5 — 如何安装 NetBeans

## 如何构建和配置 xDebug

我们建议您使用 NetBeans 使用 xDebug 调试器，因为它使调试 PHP 应用程序变得更容易。xDebug 的源代码包含在 XAMPP 安装中。但是，要使其与 NetBeans 一起工作，您必须构建 xDebug 源代码并配置 xDebug 以与 NetBeans 一起工作。

在构建 xDebug 之前，您需要安装一些构建工具，包括 C 编译器和 autoconf 工具。为此，请打开终端并输入与您的 Linux 发行版相对应的第 C-6 图中显示的命令。

安装构建工具后，您可以使用图中第二部分所示的过程构建和配置 xDebug。完成后，xDebug 调试器应按第 6 章所述工作。

## 如何在 Ubuntu 上安装构建工具

```bash
sudo apt-get install build-essential
sudo apt-get install autoconf
```

## 如何在 Fedora 上安装构建工具

```bash
sudo yum install gcc autoconf
```

## 扩展目录的默认位置

```
/opt/lampp/lib/
```

## PHP 初始化文件的默认位置

```
/opt/lampp/etc/php.ini
```

## 如何构建和配置 xDebug

- 1. 打开终端并切换到 /opt/lampp 目录。
- 2. 构建 xDebug 文件。为此，输入：
- ```bash
sudo bin/pecl install xdebug
```
- 这应该构建 xDebug。完成后，命令行提示符应返回。
- 3. 切换到 /opt/lampp/lib/php/extensions 目录并找到 xdebug.so 文件。它通常存储在名称很长的目录中，例如 no-debug-non-zts-20121212。请注意目录的名称，因为它在您的系统上可能略有不同。
- 4. 返回 /opt/lampp 目录。
- 5. 打开 php.ini 文件进行编辑。为此，输入：
- ```bash
sudo gedit etc/php.ini
```
- 6. 滚动到此文件的末尾并添加以下行：
- ```ini
[xdebug]
zend_extension = /opt/lampp/lib/php/extensions/no-debug-non-zts-20121212/xdebug.so
xdebug.remote_enable=on
xdebug.remote_host=localhost
xdebug.remote_handler=dbgp
xdebug.remote_port=9000
```
- 7. 保存您的更改。
- 8. 停止并重新启动 Apache。

## 说明

- - 对于本书，我们建议您将 NetBeans 与 xDebug 一起用作主要开发工具。
- - 有关安装 NetBeans 的更多信息，您可以参考 NetBeans 网站上提供的文档。
- - 有关安装 xDebug 的更多信息，您可以在互联网上搜索“Linux xDebug”。

Figure C-6    如何构建和配置 xDebug
