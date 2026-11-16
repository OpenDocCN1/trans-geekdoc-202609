

- 编写存储过程和函数的丰富环境远远超越了 MySQL 5 提供的有限环境，并支持 Perl 和甚至 PHP 本身等标准编程语言来编写存储过程，而不像 SQL Server 和 Oracle 使用的专有语言；而且，针对地理信息服务等更复杂功能的大量库使其远远优于许多其他企业级数据库服务的替代方案。

- 它方方面面都很出色。除了免费且符合标准之外，它还非常快速、非常稳定，并且设置和安装相当容易。它还得到了 PHP 的很好支持，考虑到本书的主题，这是一个巨大的加分项。

## 安装本身

既然您了解了背景，现在是时候开始安装了。以下假设您有一台可以正常工作的 UNIX 机器，已安装并准备就绪。

如果您还没有 UNIX 机器，并想找个好的起点，GNU/Linux 是面向 PC 硬件的理想基于 UNIX 的操作系统。只需确保在安装过程中选择安装所有开发实用程序，因为您需要它们来让 PHP 运行起来。

此安装假设您的 UNIX 机器已联网，分配了专用 IP 地址，并且可以从您的工作站 ping 通（您的工作站也可以从中 ping 通）。还假设您熟悉基本的 UNIX 命令和实用程序。

如果这一切看起来都没问题，那么您可以开始了。以 root 身份登录到您的 UNIX 机器（或使用 su 从普通用户帐户切换到 root），然后即可开始。

## 下载和安装 PostgreSQL

由于您的开发环境仅供自己使用，您不必担心将 PostgreSQL 放在单独的机器上。您可以使用同一台机器运行 Apache、PHP 和您的数据库，而不会产生真正的性能影响。

Mac OS X 用户很幸运，无需遵循本节。相反，请从 http://www.postgresql.org/download/macosx 下载向导驱动的安装程序，它几乎无需干预即可为您安装、配置并启动 PostgreSQL。

请确保从 www.postgresql.org 获取 PostgreSQL 的完整归档文件，并且下载的是源代码——而不是任何二进制文件。您将亲自编译它以获得最大速度和稳健性。下载的文件名看起来会像 postgresql-8.3.3.tar.gz 这样。要查找 URL，请访问 www.postgresql.org，单击 Downloads，并找到源代码的链接。

如果非要的话，可以使用 Lynx 或 FTP 下载文件，但作者更推荐使用 wget：

```
# wget ftp://ftp.postgresql.org/pub/latest/postgresql-8.3.3.tar.gz
```

下载完成后，以常规方式解压 PostgreSQL：

```
# tar -xzvf postgresql-8.3.3.tar.gz
```

这将创建一个名为 postgresql-8.3.3 的目录，其中包含 PostgreSQL 的源文件。进入该目录：

```
# cd postgresql-8.3.3
```

运行 configure 脚本以生成适合您特定 UNIX 环境的 Makefile：

```
# ./configure
```

运气好的话，您不会看到任何错误，并会看到一系列检查通过，最后一行读取如下或类似：

```
config.status: linking ./src/makefiles/Makefile.linux to src/Makefile.port
```

如果一切看起来都没问题，您可以通过键入以下内容来开始编译过程：

```
# make
```

PostgreSQL 编译可能需要相当长的时间，这时可以去喝杯咖啡。当您回来时，希望 PostgreSQL 已顺利编译完成，您可以按以下方式安装它：

```
# make install
```

严格来说，PostgreSQL 现在已安装，但仍需要进行一定量的配置。您必须创建守护进程将以其身份运行的用户帐户，为数据目录设置权限以便该用户拥有它，然后初始化数据目录。按照以下步骤设置数据库工作目录（所有数据都将存储在此）：

```
# adduser postgres
# mkdir /usr/local/pgsql/data
# chown postgres /usr/local/pgsql/data
# su - postgres
# /usr/local/pgsql/bin/initdb -D /usr/local/pgsql/data
```

您现在几乎可以启动 PostgreSQL 守护进程（服务器）了。最后一步：您必须告诉 PostgreSQL 允许从哪里接受连接。通常，这将只是来自同一服务器，或者在不得已的情况下，来自同一网络上的其他机器。

假设您的服务器 IP 地址在此示例中为 192.168.1.1，并且您只希望允许来自该 IP 地址的访问。使用您喜欢的编辑器编辑文件 /usr/local/pgsql/data/pg_hba.conf，将此行添加到文件的最底部：

```
Host all all 192.168.1.1 255.255.255.255 trust
```

保存文件并退出编辑器。您现在可以使用以下语法启动 PostgreSQL：

```
# su - postgres
# /usr/local/pgsql/bin/postmaster -i -D /usr/local/pgsql/data &
```

第一行非常重要。postmaster 进程必须以新的 postgres 用户身份运行，而不是以 root 或您可能登录过的其他任何用户身份运行。启动时的 -i 指令也很重要，因为它告诉 PostgreSQL 允许 TCP/IP 连接——这是默认不允许的。

就这样。您可以再次以 postgres 用户身份按以下方式创建数据库：

```
# /usr/local/pgsql/bin/createdb databasename
```

现在您可以按以下方式使用 PostgreSQL 控制台操作它：

```
# /usr/local/pgsql/bin/psql databasename
```

最后，您可以按以下方式创建新用户：

```
# /usr/local/pgsql/bin/createuser username
```

这就结束了 PostgreSQL 安装的速成课程。根据您的操作系统和功能要求，此过程有许多变体。更高级的设置和所需库的更多细节在 PostgreSQL 文档中有所介绍。

## 安装各种支持库

在理想世界中，您现在可以继续安装 PHP 和 Apache。不幸的是，现实并非如此，您需要为 PHP 安装一些支持库。

PHP 6 大大减少了启动核心功能所需的外部库数量。主要的 GNU/Linux 发行版也在处理这些库的二进制分发方面变得好得多，而且，作者首次建议现在从二进制分发中安装所需的少数库。使用您喜欢的包管理器（例如 yum、apt-get 等）安装以下库：

- libicu
- libicu-devel

这两个库包含国际化组件的代码，这些组件提供了一些支持 PHP 6 新 Unicode 支持所需的软件基础设施。您需要的任何其他库（如果有的话）取决于您需要的确切功能。

安装 libicu 后，您就可以着手处理 PHP 和 Apache 本身了。

## 安装 PHP 和 Apache

PHP 和 Apache 必须同步安装，因此它们将在同一节中介绍。很快就会明白确切原因。

Mac OS X 用户再次可以在此步骤跳过，从 http://www.mamp.info/en/index.php 下载并安装 MAMP。它将使用简单的“向导”过程为您创建一个可用的 PHP 6 安装。完成后，您会发现可以在 http://localhost:8080 处找到 PHP 安装。

首先，从各自的网站下载 Apache 和 PHP 的最新版本——httpd.apache.org 和 www.php.net。

您将下载的两个文件名可能类似于 `httpd-2.2.9.tar.gz` 和 `php-6.0.0.tar.gz`。以常规方式解压缩它们。

```
# tar -xzvf httpd-2.2.9.tar.gz
# tar -xzvf php-6.0.0.tar.gz
```

第一步是对 Apache 进行初始配置。切换到 Apache 目录（可能是 `httpd-2.2.9`），使用默认参数运行 configure 脚本，然后编译并安装：

```
# ./configure
# make && make install
```

完成后，继续配置 PHP。切出 Apache 目录并进入 PHP 目录：

```
# cd ..
# cd php-6.0.0
```

与 PHP 早期版本的要求相比，您现在使用一个异常简单的 `configure` 语句来配置 PHP：

```
./configure --with-apxs2=/usr/local/apache/bin/apxs --with-pgsql --with-pdo-pgsql
```

请注意，如果您将 Apache 安装到不同的前缀，或使用了 `-enable-layout` 选项之一，则需要修改 `--with-apxs2` 指令以指向 `apxs` 可执行文件的安装位置。

配置可能需要几分钟，但假设您迄今为止都正确遵循了本附录，您不应该收到任何错误消息，一切都应该配置成功。

然后您可以构建 PHP：

```
# make
# make install
```

请注意，`make` 可能需要几分钟，具体取决于服务器的硬件和负载。`make install` 可能不会花太长时间。如果失败，您可能需要重新检查步骤。特别是，请确认上一节中提到的所有支持包都已正确配置。

PHP 编译和安装过程会在您的 Apache `modules` 目录中创建一个模块；现在您可以配置并安装 Apache 以使用该模块。您必须告诉 Apache 配置文件如何处理 `.php` 扩展名。修改文件 `/usr/local/apache/conf/httpd.conf`（同样，根据您的 configure 参数，此路径可能会有所不同，但这是默认值）并添加以下行：

```
AddType application/x-httpd-php .php
AddType application/x-httpd-php-source .phps
```

