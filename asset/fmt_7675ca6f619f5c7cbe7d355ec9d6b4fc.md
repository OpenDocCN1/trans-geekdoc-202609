
```
bin/safe_mysqld --user=mysql &
```

18. **要测试 MySQL 是否正常运行，请键入**

```
bin/mysqladmin --version
```

你应该会看到 MySQL 服务器的版本号。

## 从源代码安装

在决定从源代码文件安装 MySQL 之前，请检查你的操作系统是否有二进制文件。MySQL 二进制文件是预编译的、可直接安装的 MySQL 安装包。MySQL 二进制文件非常方便且可靠。

你可以通过下载源代码文件、编译源代码文件并安装编译后的程序来安装 MySQL。这个过程听起来非常技术化且令人生畏，但实际上并非如此。在开始安装过程之前，请完整阅读以下步骤。

要从源代码安装 MySQL，请按照以下步骤操作：

- 1. **将你的 Web 浏览器指向 `www.mysql.com`，即 MySQL 主页。**

- 2. **单击生产版本号链接。**

查看屏幕右侧标记为“MySQL 产品”的列表。在“数据库服务器”标题下查找相应部分。在撰写本文时，生产版本为 4.0.17。

- 3. **滚动到屏幕底部，找到“源代码下载”标题。**

此部分列出了几个下载项。

- 4. **找到 tar 包版本，并点击其旁边的下载链接。**

此时会打开一个对话框。

- 5. **选择保存文件的选项。**

此时会打开一个窗口，让你选择文件的保存位置。

- 6. **导航到你要安装 MySQL 的位置，然后点击“保存”。**

标准位置是 `/usr/local`。如果可能，最好使用标准位置。

- 7. **下载完成后，切换到下载目录——例如，`cd /usr/local`。**

你会看到一个名为 `mysql-` 的文件，后面跟着版本号和 `.tar.gz.`——例如 `mysql-4.0.17.tar.gz`。这个文件是一个 *tar 包*。

- 8. **使用以下命令为 MySQL 创建用于运行的用户和组 ID：**

```bash
groupadd mysql
useradd -g mysql mysql
```

这些命令的语法在不同版本的 Unix 上可能略有不同，或者它们可能被称为 `adduser` 和 `addgroup`。

*注意：* 你必须使用一个有权添加用户和组的账户。

- 9. **通过键入以下内容解压 tar 包**

```bash
gunzip -c filename | tar -xvf -
```

例如：

```bash
gunzip -c mysql-3.23.44.tar.gz | tar -xvf -
```

你会看到一个名为 `mysql-version` 的新目录——例如 `mysql-4.0.15`。

你必须使用一个被允许在 `/usr/local` 中创建文件的账户。

- 10. **切换到新目录。**

例如，键入 `cd mysql-4.0.17`。

- 11. **请键入以下内容：**

```bash
./configure --prefix=/usr/local/mysql
```

你会看到几行输出。输出会告诉你 `configure` 何时完成。这可能需要一些时间。

- 12. **键入 `make`。**

你会看到许多行输出。输出会告诉你 `make` 何时完成。`make` 可能会运行一段时间。

- 13. **键入 `make install`。**

`make install` 会很快完成。

*注意：* 你可能需要以 `root` 身份运行此命令。

- 14. **请键入以下内容：**

```bash
scripts/mysql_install_db
```

此命令会运行一个脚本，用于初始化你的 MySQL 数据库。

- 15. **确保你的 MySQL 目录的所有权和组成员身份正确。使用以下命令设置所有权：**

```
chown -R root /usr/local/mysql
chown -R mysql /usr/local/mysql/data
chgrp -R mysql /usr/local/mysql
```

这些命令使 `root` 成为除 `data` 之外所有 MySQL 目录的所有者，并使 `mysql` 成为 `data` 目录的所有者。所有 MySQL 目录都属于组 `mysql`。

- 16. **通过将文件 `mysql.server` 从 `/usr/local/mysql/support-files` 复制到系统启动文件所在的位置，将计算机设置为在启动时自动启动 MySQL。**

17. 要测试MySQL，你可以手动启动服务器，无需重启计算机，输入以下命令：

```
bin/mysqld_safe --user=mysql &
```

18. 要测试MySQL是否运行正常，输入：

```
bin/mysqladmin --version
```

你应该能看到MySQL服务器的版本号。

## 在Mac上

你可以使用Mac OS X 10.2（Jaguar）PKG二进制包下载MySQL。如果你的操作系统是OS X 10.1或更早版本，则无法使用此包。你需要下载一个tarball并按照上一节所述从源代码安装MySQL。

- 1. 将Web浏览器指向MySQL主页 `www.mysql.com`。

- 2. 点击生产版本号链接。

查看屏幕右侧标记为“MySQL Products”的列表。查找“Database Server”标题下的部分。在撰写本文时，生产版本为4.0.17。

- 3. 向下滚动屏幕，找到标题为“Mac OS Package Installer Downloads”的部分。

此部分列出几个下载项。

- 4. 找到标准版本，然后点击旁边的下载链接。

将打开一个对话框。

- 5. 选择保存文件的选项。

将打开一个框，让你选择文件的保存位置。

- 6. 导航到要安装MySQL的位置，然后点击“保存”。

标准位置是 `/usr/local`。如果可能，最好使用标准位置。

- 7. 下载完成后，切换到下载目录——例如 `/usr/local`。

你会看到一个名为 `mysql-standard` 的包，后面跟着版本号和 `dmg`，例如 `mysql-standard-4.0.17.dmg`。如果下载的文件没有扩展名 `.dmg`，请将文件名更改为 `.dmg` 扩展名。

- 8. **创建一个名为`mysql`的用户和组，供MySQL运行。** 在大多数较新的Mac版本中，此用户和组已经存在。

- 9. **通过在Finder中双击其图标来挂载磁盘镜像。**

- 10. **双击包图标以安装MySQL PKG。**

包安装程序将运行并安装该包。它将MySQL安装到目录 `/usr/local/mysql` 后跟版本号的目录中。它还会安装一个符号链接 `/usr/local/mysql/` 指向MySQL安装的目录。它还会通过运行脚本 `mysql_install_db` 初始化数据库，该脚本会创建一个名为`root`的MySQL账户。

- 11. **你可能需要更改mysql目录的所有者。**

MySQL安装的目录（例如 `/usr/local/mysql-4.0.17`）应归`root`所有。数据目录（例如 `/usr/local/mysql-4.0.17/data`）应归 `mysql` 账户所有。两个目录都应属于 `mysql` 组。如果用户和组不正确，请使用以下命令更改它们：

```
sudo chown -R root /usr/local/mysql-4.0.17
sudo chown -R mysql /usr/local/mysql-4.0.17/data
sudo chown -R root /usr/local/mysql-4.0.17/bin
```

- 12. **使用以下命令启动MySQL服务器：**

```
cd /usr/local/mysql
sudo ./bin/mysqld_safe
if necessary, enter your password
Press Ctrl-Z
bg
Press Ctrl-D or type exit
```

**这会手动启动服务器**，这意味着每次重启计算机时都必须手动启动MySQL服务器。要让服务器在每次计算机启动时自动启动，你需要安装MySQL启动项，它包含在安装磁盘镜像中单独的安装包中。要安装启动项，请双击 `MySQLStartupItem.pkg` 图标。

要停止MySQL服务器，请切换到MySQL安装目录下的 `bin` 子目录，然后输入

```
mysqladmin -u root -p shutdown
```

`-p` 使 `mysqladmin` 提示你输入密码。如果账户不需要密码，则不要包含 `-p`。

![](img/d82df0828cfbc6d6be1e9a991861f3b7_412_0.png)

## 配置MySQL

MySQL在启动时会读取配置文件。如果你使用默认设置或安装程序，可能不需要在配置文件中添加任何内容。但是，如果你将MySQL安装在非标准位置，或者希望将数据库存储在其他位置而不是默认位置，则可能需要编辑配置文件。

该文件名为 `my.ini` 或 `my.cnf`。如果你使用Windows，它位于系统目录（如WINNT）中；在Linux/Unix/Mac上，它位于 `/etc` 中。该文件看起来类似于以下内容：

```ini
[mysqld]
basedir=D:/mysql4
datadir=D:/mysql4/data
#port=3306
```

`basedir` 行告诉MySQL服务器MySQL的安装位置。`datadir` 行告诉服务器数据库所在的位置。最后一行开头的 `#` 使该行失效。你可以删除 `#` 并更改端口号，以告诉服务器在不同的端口上侦听数据库查询。

很受欢迎，所以许多RPM启用了对它的支持，但这不是你能控制的。此外，RPM通常会启用所有最流行的选项，因此RPM可能会启用你不需要的选项。因此，最简单、最高效的PHP安装方式可能是从源代码安装。如果你熟悉RPM，可以自行查找RPM并安装。RPM是可用的。不过，我这里提供的是源代码安装步骤，而不是RPM安装。

## 安装之前

在开始安装PHP之前，请检查以下各项：

✓ **Apache模块`mod_so`已安装。** 通常它是安装好的。要显示所有模块的列表，请输入以下命令：

```
httpd -l
```

命令生效前，你可能需要先进入`httpd`所在的目录。输出通常显示一长串模块列表。对于PHP，你只需要关心`mod_so`。如果`mod_so`没有加载，必须使用 `enable-module=so` 选项重新安装Apache。

✓ **已安装`apxs`实用程序。** `apxs`在安装Apache时安装。你应该能找到名为`apxs`的文件。如果Apache是从Linux上的RPM安装的，可能没有安装`apxs`。有些Apache的RPM由两个RPM组成：一个用于基本的Apache服务器，一个用于Apache开发工具。可能还需要安装包含开发工具的RPM，它会安装`apxs`。

✓ **Apache版本较新。** 有关Apache版本的信息，请参阅附录C。

要检查版本，请输入以下命令：

```
httpd --v
```

命令生效前，你可能需要先进入`httpd`所在的目录。

## 安装

要在Unix/Linux上使用Apache Web服务器安装PHP，请按照以下步骤操作：

- 1. 将Web浏览器指向PHP主页 `www.php.net`。

- 2. 点击 Downloads（下载）。

- 3. 点击最新版本的PHP源代码，在撰写本文时为5.0.0版。

你将要下载的文件包含许多压缩到一个文件中的文件——即tarball。

将打开一个对话框。

- 4. **选择保存文件的选项。**

将打开一个对话框，让你选择文件的保存位置。

- 5. **导航到要保存源代码的位置（例如 `/usr/src`），然后点击“保存”。**

- 6. **下载完成后，切换到下载目录（例如 `cd ~/usr/src`）。**

你会看到一个名为 `php-` 后跟版本名和 `tar.gz` 的文件。

- 7. **解压tarball。PHP 5.0.0版的命令是**

```
gunzip -c php-5.0.0.tar.gz | tar -xf -
```

将创建一个名为 `php-5.0.0` 的新目录，其中包含几个子目录。

- 8. **切换到解压tarball时创建的新目录。例如：**

```
cd php-5.0.0
```

- 9. **输入`configure`命令。**

使用下面两个`configure`命令之一：

```
./configure --with-mysql=DIR --with-apxs
./configure --with-mysqli=DIR --with-apxs
```

如果你使用的是MySQL 4.0或更早版本，请使用`mysql`；如果你使用的是MySQL 4.1或更高版本，请使用`mysqli`。`DIR`是相应的MySQL目录路径。使用 `with-mysql` 时，请使用mysql安装目录的路径，例如：

```
--with-mysql=/usr/local/mysql
```

使用 `with-mysqli` 时，请使用名为 `mysql_config` 的文件的路径。

如果你使用Apache 2，请使用 `with-apxs2` 选项。（有关使用Apache 2的信息，请参阅附录C。）

你会看到许多输出行。请等待`configure`命令执行完成。这可能需要几分钟。如果`configure`命令失败，它会提供一条信息性消息。通常，问题是缺少软件。你会看到一条错误消息，指出无法找到`xyz`软件，或者需要`xyz 5.6`版但找到的是`xyz 4.2`版。你需要安装或更新PHP所需的软件。

![](img/d82df0828cfbc6d6be1e9a991861f3b7_417_0.png)

如果`apxs`实用程序未安装在预期位置，你会看到一条错误消息，指出找不到`apxs`。如果收到此消息，请检查`apxs`的安装位置（`find / -name apxs`），并将路径包含在`configure`的 `with-apxs` 选项中。

```text
command: --with-apxs=/usr/sbin/apxs or /usr/local/apache/bin/apxs. If you're using Apache 2, the option is --with-apxs2=/usr/sbin/apxs.
```

10. **输入** `make`.

你将看到许多行输出。等待其完成。这可能需要几分钟。

11. **输入** `make install`.

## 在 Mac OS X 上

自 PHP 4.3 发布以来，你可以在 Mac OS X 上像在 Unix/Linux 上一样轻松安装 PHP。你通过下载源文件、编译源文件并安装编译后的程序来安装 PHP。这个过程并不像看起来那么技术性且令人生畏。我在接下来的几个部分中提供了逐步说明。在开始安装程序之前，请通读所有步骤，以确保你能清楚地理解全部内容并且已准备好所有东西，这样在安装过程中就不会中途停止。

### 安装前

如果你想在你的网站上使用 PHP 与 Apache 配合使用，则必须安装 Apache。大多数 Mac OS X 系统已预装 Apache。有关 Apache 的更多信息，请参阅附录 C。

开始安装 PHP 之前，请检查以下内容：

- **Apache 版本较新：** 有关 Apache 版本的讨论，请参阅附录 C。要检查版本，请在命令行中输入以下内容：

  ```text
  httpd -v
  ```

  你可能需要在 `httpd` 所在的目录中才能使命令生效。

  ![](img/d82df0828cfbc6d6be1e9a991861f3b7_418_0.png)

  截至本文撰写时，PHP 与 Apache 2 仍被视为实验性。对于生产网站的使用，使用 Apache 1.3 可能比 Apache 2 更好。有关 Apache 版本的讨论，请参阅附录 C。通过在 `www.php.net/manual/en/install.apache2.php` 检查 PHP 网站，了解 PHP 与 Apache 2 的状态更新。

- **Apache 模块 `mod_so` 已安装。** 通常是这样。要显示所有模块的列表，请输入以下内容：

  ```text
  httpd -l
  ```

  你可能需要在 `httpd` 所在的目录中才能使命令生效。输出通常显示很长的模块列表。对于 PHP，你只需关心 `mod_so`。如果 `mod_so` 未加载，则必须重新安装 Apache。

- ✓ **已安装 apxs 实用程序。** `apxs` 通常在安装 Apache 时安装。要确定它是否已安装在你的计算机上，你应该查找名为 `apxs` 的文件，通常位于 `/usr/sbin/apxs` 目录。如果能找到该文件，则表示已安装 `apxs`；如果找不到，则未安装。

- ✓ **已安装开发者工具 CD 上的文件。** 该 CD 是 Mac OS X 主发行版的补充。如果找不到该 CD，你可以从 Apple Developer Connection 网站 `developer.apple.com/tools/macosxtools.html` 下载工具。

### 安装

要在 Mac 上安装 PHP，请按照以下步骤操作：

1. **将你的 Web 浏览器指向 `www.php.net`，这是 PHP 主页。**

2. **点击 下载。**

3. **点击最新的 PHP 源代码版本，截至本文撰写时为 5.0.0 版本。**

   一个对话框打开。

4. **选择保存文件的选项。**

   一个对话框打开，让你选择文件保存位置。

5. **导航到你想要保存源代码的位置（例如，`/usr/src`），然后点击 保存。**

6. **下载后，切换到下载目录（例如，`cd /usr/src`）。**

   你会看到一个名为 `php-5.0.0.tar.gz` 的文件。该文件包含压缩成一个文件中的多个文件。该文件可能已被 StuffIt Expander 自动解包，因此你会看到 `php-5.0.0` 目录。如果是这样，请跳到第 8 步。

7. **解包 tarball。**

   解包 PHP 5.0.0 版本 tarball 的命令是
