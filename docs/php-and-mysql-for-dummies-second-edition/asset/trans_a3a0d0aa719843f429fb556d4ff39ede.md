
此命令会安装 MySQL 软件包。它会设置你需要的 MySQL 账户和组名，并在 `/var/lib/mysql` 创建数据目录。它还会启动 MySQL 服务器，并在 `/etc/rc.d` 中创建适当的条目，以便 MySQL 在计算机启动时自动启动。

你需要使用一个拥有权限、能够成功运行 rpm 命令的账户，例如 root 账户。

- 10. **要测试 MySQL 是否正常运行，请键入以下内容：**

```
bin/mysqladmin --version
```

你应该会看到 MySQL 服务器的版本号。

## 从二进制文件安装

现成的、已编译的二进制文件可用于多种 Linux 和 Unix 发行版。如果这些发行版都不适用于你的 Linux/Unix 机器，你可以从源代码文件安装 MySQL，但只要有可能，最好使用二进制文件。在撰写本文时，MySQL 二进制文件可用于以下 Unix 发行版，但随时可能会提供更多版本：

- Solaris
- HP-UX
- AIX
- SCO
- SGI Irix
- Dec OSF
- QNX
- BSDi
- OpenBSD
- FreeBSD

要在 Linux 或 Unix 上安装二进制文件版本的 MySQL，请按照以下步骤操作：

- 1. **将你的 Web 浏览器指向 www.mysql.com，即 MySQL 主页。**
- 2. **单击 _生产_ 版本号链接。**

查看屏幕右侧标记为“MySQL 产品”的列表。在“数据库服务器”标题下查找相应部分。在撰写本文时，生产版本为 4.0.17。

- 3. **向下滚动屏幕，直到找到 Linux 或你的 Unix 版本对应的标题（例如 Solaris 下载）。**

此部分列出了该操作系统的几个下载项。

- 4. **找到适合你的操作系统版本的正确软件包。**

对于 Linux，你可能需要 Intel libc6 二进制版本。对于 Unix，请选择正确的 Unix 系统版本——例如 Solaris 9（SPARC，64 位）。

- 5. **单击适合你的操作系统的标准版本的下载链接。**

此时会打开一个对话框。

- 6. **选择保存文件的选项。**

此时会打开一个窗口，让你选择保存文件的位置。

- 7. **导航到你要安装 MySQL 的位置，然后点击“保存”。**

标准位置是 `/usr/local`；如果可能，最好使用此位置。

- 8. **下载完成后，切换到下载目录——例如，cd /usr/local。**

你会看到一个名为 `mysql-` 的文件，后面跟着版本号、操作系统名称和 `.tar.gz`——例如 `mysql-4.0.17-sun-solaris2.9-sparc-64bit.tar.gz`。这个文件是一个 tar 包。

- 9. **使用以下命令为 MySQL 创建用于运行的用户和组 ID：**

```bash
groupadd mysql
useradd -g mysql mysql
```

这些命令的语法在不同版本的 Unix 上可能略有不同，或者它们可能被称为 `adduser` 和 `addgroup`。

**注意：** 你必须使用一个有权添加用户和组的账户。

- 10. **通过键入以下内容解压 tar 包：**

```bash
gunzip -c filename | tar -xvf -
```

例如：

```bash
gunzip -c mysql-4.0.17-sun-solaris2.9-sparc-64bit.tar.gz | tar -xvf -
```

**注意：** 你必须使用一个被允许在 `/usr/local` 中创建文件的账户。

- 11. **创建一个指向新目录的链接，以便你可以用较短的名字来引用它，而不是使用当前难以输入的目录名。请键入以下内容：**

```
ln -s newdirectoryname mysql
```

例如：

```
ln -s mysql-4.0.17-sun-solaris2.9-sparc-64bit mysql
```

现在你可以将目录称为 mysql，而不必使用其长名称。

- 12. **通过键入 cd mysql 切换到新目录。**

你应该会看到几个子目录，包括 /bin 和 /scripts。

- 13. **将 bin 目录的路径（例如 /usr/local/mysql/bin）添加到系统路径中，以便任何需要访问 MySQL 的程序都可以访问 MySQL 程序。**

你应该通过编辑计算机启动时设置系统变量的文件来执行此操作。

- 14. **请键入以下内容：**

```
scripts/mysql_install_db
```

此命令会运行一个脚本，用于初始化你的 MySQL 数据库。

- 15. **确保你的 MySQL 目录的所有权和组成员身份正确。使用以下命令设置所有权：**

```
chown -R root /usr/local/mysql
chown -R mysql /usr/local/mysql/data
chgrp -R mysql /usr/local/mysql
```

这些命令使 root 成为除 data 之外所有 MySQL 目录的所有者，并使 mysql 成为 data 目录的所有者。所有 MySQL 目录都属于组 mysql。

- 16. **通过将文件 mysql.server 从 /usr/local/mysql/support-files 复制到系统启动文件所在的位置，将计算机设置为在启动时自动启动 MySQL。**

- 17. **要测试 MySQL，你可以通过键入以下内容手动启动服务器，而无需重启计算机：**

```
bin/safe_mysqld --user=mysql &
```

- 18. **要测试 MySQL 是否正常运行，请键入**

```
bin/mysqladmin --version
```

你应该会看到 MySQL 服务器的版本号。

## 从源代码安装

在决定从源代码文件安装 MySQL 之前，请检查你的操作系统是否有二进制文件。MySQL 二进制文件是预编译的、可直接安装的 MySQL 安装包。MySQL 二进制文件非常方便且可靠。

你可以通过下载源代码文件、编译源代码文件并安装编译后的程序来安装 MySQL。这个过程听起来非常技术化且令人生畏，但实际上并非如此。在开始安装过程之前，请完整阅读以下步骤。

要从源代码安装 MySQL，请按照以下步骤操作：

- 1. **将你的 Web 浏览器指向 www.mysql.com，即 MySQL 主页。**
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

- 7. **下载完成后，切换到下载目录——例如，cd /usr/local。**

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

你会看到一个名为 mysql-version 的新目录——例如 mysql-4.0.15。

你必须使用一个被允许在 /usr/local 中创建文件的账户。

- 10. **切换到新目录。**

例如，键入 cd mysql-4.0.17。

- 11. **请键入以下内容：**

```bash
./configure --prefix=/usr/local/mysql
```

你会看到几行输出。输出会告诉你 configure 何时完成。这可能需要一些时间。

- 12. **键入 make。**

你会看到许多行输出。输出会告诉你 make 何时完成。make 可能会运行一段时间。

- 13. **键入 make install。**

make install 会很快完成。

*注意：* 你可能需要以 root 身份运行此命令。

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

这些命令使 root 成为除 data 之外所有 MySQL 目录的所有者，并使 mysql 成为 data 目录的所有者。所有 MySQL 目录都属于组 mysql。

- 16. **通过将文件 mysql.server 从 /usr/local/mysql/support-files 复制到系统启动文件所在的位置，将计算机设置为在启动时自动启动 MySQL。**

