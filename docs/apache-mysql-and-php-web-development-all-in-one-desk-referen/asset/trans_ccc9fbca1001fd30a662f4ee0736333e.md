

您会看到一个名为 httpd- 的文件，后面跟着版本号和 tar.gz。此文件称为 tarball。

请确保您使用的账户有权写入 /usr/src，例如 root。

### 6. 验证下载的文件，确保其未被篡改。

要验证文件，请执行以下步骤：

- i. 从 www.apache.org/dist/httpd/ 下载两个文件：KEYS 和一个与源版本号相同、文件名以 .asc 结尾的文件。
- ii. 输入以下任一行，具体取决于您计算机上安装的 PGP 版本：
  - pgp <KEYS>
  - gpg --import KEYS
- iii. 输入以下任一行，使用正确的版本号：
  - pgp httpd-2.0.47.tar.gz.asc
  - gpg --verify httpd-2.0.47.tar.gz.asc

您应该会看到类似下面的内容：
Good signature from user "Sander Striker"

这就是您要找的内容。可能会显示多条消息，但前面那条是重要的。您还可能会看到一条消息，指出密钥与密钥签名者之间的关系无法验证。这没关系。

如果您没有收到签名良好的消息，则该文件可能已被篡改且可能很危险。在这种情况下，请从第 1 步开始重复该过程，并选择不同的镜像进行下载。

### 7. 解压 tarball。

解压版本 2.0.45 的 tarball 的命令如下：

```
gunzip -c httpd-2.0.45.tar.gz | tar -xf -
```

将创建一个名为 httpd-2.0.45 的新目录，其中包含若干子目录，内含您刚刚从 tarball 中解压的所有文件。

### 8. 切换到解压 tarball 时创建的新目录。

例如，您可以使用类似以下的命令：

```
cd httpd-2.0.45
```

### 9. 输入以下内容：

```
./install-bindist.sh
```

如果要将 Apache 安装在默认位置（/usr/local/apache2）以外的位置，可以按如下方式指定不同的安装位置：

```
./install-bindist.sh /usr/mine/apache2
```

### 10. 启动 Apache Web 服务器。

有关详细信息，请参见本章后面的“启动 Apache”部分。

### 11. 在浏览器中输入您网站的 URL（例如 www.mysite.com 或 localhost）以测试 Apache。

如果一切顺利，您会看到 Apache 消息，告诉您 Apache 正在运行。如果您没有看到此消息，则说明有问题，您应该阅读本章后面的“排除 Apache 故障”部分。

## 安装选项

在使用源文件安装 Apache 的第 11 步中（请参见“从源文件安装 Apache”），您可以在 configure 命令中使用安装选项来更改 Apache 的安装方式。本节描述了您可以使用的不同安装选项。

### 设置路径

如果您不使用 configure 命令中的选项来更改位置，Apache 将安装在默认位置。主 Apache 目录的默认路径为 Apache 1.3 的 /usr/local/apache 和 Apache 2 的 /usr/local/apache2。要更改安装 Apache 文件的位置，请使用以下三种安装选项之一：

- prefix=PREFIX: 将主 Apache 目录设置为 PREFIX。默认位置为 Apache 1.3 的 /usr/local/apache 和 Apache 2 的 /usr/local/apache2。

- exec-prefix=EPREFIX: 将安装体系结构相关文件的目录设置为 EPREFIX。体系结构相关文件是特定于操作系统的文件（例如 Apache 服务器二进制文件），与在每个操作系统上都相同的文件（例如配置文件 httpd.conf，它是每个操作系统上相同的文本文件）相对。默认情况下，EPREFIX 为 PREFIX。

- enable-layout=LAYOUT: 使用名为 config.layout 的文件中名为 LAYOUT 的布局来指定文件的安装位置。

要使用选项，请将其包含在 configure 命令中，前面加上两个连字符 (--)，如下所示：

```
./configure --prefix=/usr/apache --exec-prefix=/usr/apache
```

您可以使用布局文件来指定所有文件的安装位置。名为 config.layout 的布局文件包含几个示例布局，您可以使用这些布局。您还可以编辑现有布局之一或添加自己的布局。文件中包含了标准 Apache 布局（当您不更改任何内容时使用），如下所示：

```
<Layout Apache>
prefix: /usr/local/apache2
exec_prefix: ${prefix}
bindir: ${exec_prefix}/bin
sbindir: ${exec_prefix}/bin
libdir: ${exec_prefix}/lib
libexecdir: ${exec_prefix}/modules
mandir: ${prefix}/man
sysconfdir: ${prefix}/conf
datadir: ${prefix}
installbuilddir: ${datadir}/build
errordir: ${datadir}/error
iconsdir: ${datadir}/icons
htdocsdir: ${datadir}/htdocs
manualdir: ${datadir}/manual
cgidir: ${datadir}/cgi-bin
includedir: ${prefix}/include
localstatedir: ${prefix}
runtimedir: ${localstatedir}/logs
logfiledir: ${localstatedir}/logs
proxycachedir: ${localstatedir}/proxy
</Layout>
```

布局由起始布局行和结束布局行括起来，如下所示：

```
<Layout Apache>
</Layout>
```

在此示例中，Apache 是布局的名称。如果要使用此布局，请在 configure 命令中使用以下选项：

```
./configure --enable-layout=Apache
```

布局随后指定各种文件类型的目录路径，如下所示：

```
prefix: main Apache directory
exec_prefix: architecture dependent files
bindir: user executable binary files
sbindir: system executable binary files
libdir: libraries
libexecdir: architecture dependent libraries
mandir: man pages
sysconfdir: configuration files
datadir: read-only data files
installbuilddir: datafiles used in the build
errordir: error files
iconsdir: image files containing icons
htdocsdir: Web page files
manualdir: HTML manual files
cgidir: CGI programs
includedir: include files
localstatedir: writeable data files
runtimedir: runtime data files
logfiledir: log files
proxycachedir: proxy cache files
```

您可以通过更改目录名来编辑此布局。例如，布局为 CGI 目录指定了以下路径：

```
cgidir:   ${datadir}/cgi-bin
```

您可以通过按如下方式编辑该行来更改此路径：

```
cgidir:   ${datadir}/mycgi-bin
```

该文件包含其他几个可供使用的布局。目前，布局有 GNU、Mac OS X Server、Darwin、Red Hat、opt、beos、SuSE、BSD、Solaris、OpenBSD 和 Debian。如果您愿意，也可以编辑这些布局中的任何一个，或添加自己的新布局。

### 设置环境变量

一种安装选项设置在构建过程中使用的环境变量（“从源文件安装 Apache”中的步骤 9 和 12）。您可以在发出 configure 命令之前单独设置环境变量。或者，您可以在与 configure 命令相同的行上设置变量，如下所示：

```
CC="gcc" ./configure
```

configure 命令为 make 命令做准备，创建一个名为 makefile 的文件。然后 make 命令启动构建过程，该过程基于 makefile 中包含的说明查找某些环境变量。如果您有使用 C 的经验，可能对 make 和 makefile 比较熟悉。如果没有，您可能不需要设置这些环境变量。您可以在 GNU 网站 www.gnu.org 上阅读更多关于 make 的信息。表 2-1 显示了您可能想要设置的环境变量。

| 选项 | 要求 Apache ... |
| --- | --- |
| CC="COMP" | 在构建（make 命令）时使用 COMP 作为 C 编译器的名称。 |
| CPPFLAGS="FLAGS" | 使用 FLAGS 作为 C 编译器的杂项选项。 |
| CFLAGS="FLAGS" | 使用 FLAGS 作为 C 编译器的调试和优化选项。 |
| LDFLAGS="FLAGS" | 在构建期间将 FLAGS 传递给链接器。 |
| LIBS="LOCATIONS" | 在构建期间将库 LOCATIONS 传递给链接器。 |
| INCLUDES="DIRS" | 在构建期间使用 DIRS 作为搜索头文件的目录。 |
| TARGET="NAME" | 将编译后的文件命名为 NAME。默认值为 httpd。 |

### 启用模块

在使用模块之前必须先启用模块。安装 Apache 时，许多模块默认处于启用状态。其他模块必须在安装期间使用安装选项启用。有关使用模块的信息，请参见第 II 册第 4 章。

## 启动和停止 Apache

有一个名为 apachectl 的脚本可用于控制服务器。默认情况下，该脚本存储在 Apache 安装目录下的名为 bin 的子目录中。某些 Linux 发行版可能将其放在另一个目录中。

该脚本需要一个关键字。最常见的关键字是 start、stop 和 restart。通用语法如下：

```
path/apachectl keyword
```

