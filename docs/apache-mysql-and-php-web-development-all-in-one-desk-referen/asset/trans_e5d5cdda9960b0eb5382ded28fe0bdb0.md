

在决定安装哪个版本时，如果你计划使用某些模块，请查看这些模块的网站以确定其与 Apache 2 的兼容性。例如，通常可以通过在 www.google.com 中输入模块名称来查找模块的网站名称。如果模块兼容，请安装 Apache 2。

本书中的信息基于 Apache 2。其中大部分内容同样适用于 Apache 1.3。在某些地方，我会注明该信息仅适用于 Apache 2。

## Apache 2

目前，Apache 2 的当前版本是 2.0.47。此版本包含针对早期版本的错误修复，还修复了一个安全问题。请尽量安装最新的 Apache 版本。由于 Apache 2 发布频繁，请查看 Apache 网站 (httpd.apache.org) 以获取有关版本的最新信息。

## Apache 1.3

Apache 1.3 的当前版本是 1.3.28。此版本修复了一些安全问题。出于安全考虑，你应该安装此版本或更高版本。Apache 1.3 不再添加新功能，但仍在修复错误并处理安全问题。Apache 1.3 的新版本仍在继续发布，但频率不如 Apache 2 高。

## Upgrading from Apache 1.3 to Apache 2

如前所述，与 Apache 1.3 一起运行的模块无法与 Apache 2 一起运行。因此，如果你正在使用 Apache 1.3 运行模块，在升级 Apache 时需要升级模块。查看模块的网站并下载已重写为可与 Apache 2 一起运行的版本。

## Selecting the type of file to install

你可以下载并安装两种类型的 Apache 软件：

- 二进制文件——专为你的操作系统预编译的机器语言文件
- 你自己编译然后安装的源文件

### Binary files

大多数操作系统都可以安装二进制文件。二进制文件比源文件更容易安装，因为它们已经过编译。但是，某个版本的二进制文件通常比源文件发布得稍晚。因此，二进制文件可能不是最新版本。

二进制文件可从 Apache 网站获取。为你的操作系统选择合适的二进制文件。该网站为每个二进制文件提供一个 README 文件，其中包含有关二进制文件的信息，包括哪些模块已编译到二进制文件中。二进制文件、所有必要的支持文件（包括 README.bindist）和安装说明（在 INSTALL.bindist 文件中）被压缩并打包成一个文件——称为 tarball——供你下载。你解压该文件以访问所需的文件，然后将文件安装在适当的位置。

如果你熟悉 Linux RPM 文件，可能希望将 Linux 作为 RPM 安装。从你的 Linux 发行版网站下载 RPM 文件。也就是说，如果你运行的是 Red Hat Linux，请从 Red Hat 网站下载 RPM。

### Source files

从源文件安装 Apache 比从二进制文件安装更困难，但这样做可以让你按照所需的精确选项安装最新版本。

### Before installing Apache

在安装 Apache 之前，检查你的主机计算机是否满足以下要求：

- **磁盘空间：** 安装时可能需要高达 50MB 的磁盘空间。安装后 Apache 可能会使用 10MB，尽管具体用量取决于使用的选项和安装的模块。
- **C 编译器：** 你的计算机已安装符合 ANSI 标准的 C 编译器。GNU C (gcc) 是一个不错的选择。

### Installing Apache from Source Files

要从源文件安装 Apache，请执行以下步骤：

- 1. 将 Web 浏览器指向 httpd.apache.org，即 Apache 主页。
- 2. 在页面左侧的 Download 下点击 From a Mirror 链接。
- 3. 向下滚动到标记为 Mirror 的部分。

为你选择了特定的镜像站点。如果你不想使用此镜像站点，请选择另一个。或者，如果你不想从这个镜像站点下载时出现问题，请返回此页面并选择另一个。

- 4. 在同一页面上继续向下滚动，找到 Apache 2 或 Apache 1.3 的部分（取决于你想安装的版本）。找到并选中要下载的文件。

例如，目前 Linux 的最新版本是 httpd-2.0.47.tar.gz。

- 5. 点击最新版本进行下载。
- 6. 选择保存文件的选项。
- 7. 导航到要保存源代码的位置（例如，/usr/src）。然后点击 Save。
- 8. 下载完成后，切换到下载目录（例如，cd /usr/src）。

![](img/3f967ab8a8fddc723173059f56621648_83_0.png)

你会看到一个名为 httpd- 的文件，后面跟着版本名称和 tar.gz。这个文件被称为 tarball，因为它包含许多由名为 tar 的程序压缩到 tarball 文件中的文件。

请确保你使用的账户有权写入 /usr/src，例如 root。

- 9. 验证下载的文件，确保其未被篡改。要验证文件，请执行以下步骤：

- i. 从 www.apache.org/dist/httpd/ 下载两个文件：KEYS 和一个与源文件版本号相同、文件名以 .asc 结尾的文件。

- ii. 根据计算机上安装的 PGP 版本，键入以下其中一行：

```
pgp <KEYS
gpg --import KEYS
```

- iii. 键入以下其中一行，并使用正确的版本号。

```
pgp httpd-2.0.47.tar.gz.asc
gpg --verify httpd-2.0.47.tar.gz.asc
```

你应该会看到类似于以下内容的输出：

```
Good signature from user "Sander Striker"
```

这就是你要寻找的内容。可能会显示多条消息，但上述消息是重要的。你还可能会看到一条消息，说明密钥与密钥签名者之间的关系无法验证。这没关系。

如果你没有收到签名良好的消息，该文件可能已被篡改且可能有危险。在这种情况下，从步骤 1 开始重复该过程，并选择不同的镜像站点进行下载。

- 10. 解压 tarball。

解压 2.0.47 版本 tarball 的命令如下：

```
gunzip -c httpd-2.0.47.tar.gz | tar -xf -
```

将创建一个名为 httpd-2.0.47 的新目录，其中包含多个子目录，里面包含你刚刚从 tarball 解压的所有文件。

- 11. 切换到解压 tarball 时创建的新目录。

例如，你可以使用如下命令：

```
cd httpd-2.0.47
```

- 12. 键入 configure 命令。

configure 命令由 ./configure 后跟所有必要选项组成。如果你可以使用所有默认选项，可以如下使用 configure：

```
./configure
```

你可能想使用的一个重要安装选项是 prefix，它设置要安装 Apache 的不同位置。默认情况下，Apache 安装在 /usr/local/apache 或 /usr/local/apache2。你可以使用以下行更改安装位置：

```
./configure --prefix=/software/apache2
```

本章后面“安装选项”部分将讨论其他安装选项。你可以键入以下行查看所有可用选项的列表：

```
./configure --help
```

此脚本运行可能需要一段时间。运行时，它会显示输出。脚本完成后，会显示系统提示符。如果 configure 遇到问题，它会显示描述性错误消息。

- 13. 键入以下命令：

```
make
```

此命令构建 Apache 服务器。运行可能需要几分钟。运行时，它会显示消息，告诉你正在做什么。完成某个操作时可能会有偶尔的较长暂停。完成后，它会返回到系统提示符。如果出现问题，它会显示描述性错误消息。

- 14. 键入以下命令：

```
make install
```

此命令根据步骤 11 中使用的 configure 命令，将 Apache 软件安装到正确的位置。

- 15. 启动 Apache Web 服务器。

有关详细信息，请参见本章后面的“启动 Apache”部分。

- 16. 在浏览器中键入你的网站 URL（例如，www.mysite.com 或 localhost）以测试 Apache。

如果一切顺利，你会看到一条 Apache 消息，告诉你 Apache 已经正常工作。如果你看不到这条消息，说明出了问题，你应该阅读本章后面的“排查 Apache”部分。

### Installing Apache from Binaries

从二进制文件安装 Apache 与从源文件安装 Apache 类似。使用以下步骤从二进制文件安装 Apache：

- 1. 将 Web 浏览器指向 www.apache.org/dist/httpd/binaries/linux/。
- 2. 点击最新版本进行下载。

目前最新的二进制文件是 httpd-2.0.45-x86_64-unknown-linux-gnu.tar.gz。二进制版本通常比源版本稍旧一些。

- 3. 选择保存文件的选项。
- 4. 导航到要保存源代码的位置（例如，/usr/local/bindir）。然后点击 Save。
- 5. 下载完成后，切换到下载目录（例如，cd /usr/local/bindir）。

