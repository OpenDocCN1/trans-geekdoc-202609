

例如，如果 Apache 安装在默认目录中，请键入以下行来启动 Apache：

```
/usr/local/apache2/bin/apachectl start
```

## 启动 Apache

apachectl 脚本启动 Apache 服务器。然后服务器在后台运行，监听 HTTP 请求。默认情况下，编译的 Apache 服务器名为 httpd，并存储在与 apachectl 脚本相同的目录中，尽管您在安装 Apache 时可以更改名称和位置。apachectl 脚本充当编译后服务器（称为 httpd）的接口。

您可以直接运行 httpd 服务器，但最好将 apachectl 用作接口。apachectl 脚本管理并检查 httpd 命令所需的数据。使用 apachectl 脚本通过以下命令启动 Apache：

```
/usr/local/apache2/bin/apachectl start
```

apachectl 脚本包含运行 httpd 的一行。默认情况下，apachectl 在默认位置（/usr/local/apache/bin 或 /usr/local/apache2/bin）中查找 httpd。如果您在非标准位置安装了 Apache，可能需要编辑 apachectl 以使用正确的路径。打开 apachectl，然后搜索以下行：

```
HTTPD='/usr/local/apache2/bin/httpd'
```

将路径更改为安装 httpd 的位置。例如，新行可能是此行：

```
HTTPD='/usr/mystuff/bin/httpd'
```

启动 Apache 后，可以通过查看计算机上的进程来检查 Apache 是否正在运行。键入以下命令以查看正在运行的进程：

```
ps -A
```

如果 Apache 正在运行，显示的进程列表将包含一些 httpd 进程。

## 使用 Apache 启动选项

您可以使用多个选项来启动 Apache 服务器。例如，您可能希望使用名称不同的配置文件。您可能希望将配置文件命名为 myhttpd.conf，而不是 httpd.conf。您可以指示 Apache 在启动时查找不同的文件，方法如下：

```
/usr/local/apache2/bin/httpd -f conf/myhttpd.conf
```

如果在启动 Apache 时要使用 httpd 的任何选项，请将选项添加到 apachectl 文件中，方法如下：

```
HTTPD='/usr/local/apache2/bin/httpd -f conf/myhttpd.conf'
```

表 2-2 显示了 httpd 可用的一些选项。

| 选项 | 告诉 Apache ... |
|---|---|
| -d serverroot | 使用 serverroot 作为搜索 Apache 文件的主目录。默认值为 /usr/local/apache 或 /usr/local/apache2。 |
| -f path/filename | 使用 path/filename 作为配置文件。路径相对于 serverroot。默认值为 conf/httpd.conf。 |
| -k action | 向 Apache 发出启动、停止或重启的信号。apachectl 中用于启动 httpd 的命令是 httpd -k start。 |
| -C directive | 在读取配置文件之前处理指令。可以使用任何指令。指令在 Book II, Chapter 3 中讨论。 |
| -c directive | 在读取配置文件之后处理指令。可以使用任何指令。指令在 Book II, Chapter 3 中讨论。 |
| -D | 设置配置参数。有关详细信息，请参见 Book II, Chapter 3。 |
| -e | 设置错误报告的级别。有关可能级别的描述，请参见 Book II, Chapter 3。 |
| -E file | 将错误消息发送到 file。 |
| -h | 显示可能选项列表，然后退出。 |
| -l | 显示编译到服务器中的模块列表，然后退出。 |
| -L | 显示可用指令列表，然后退出。 |
| -S | 显示配置文件中的设置，然后退出。 |
| -t | 仅运行语法测试。如果在配置文件中未发现错误，则返回 "Syntax OK"。 |
| -v | 显示 Apache 版本，然后退出。 |
| -V | 显示 Apache 版本和构建参数，然后退出。 |
| -X | 以调试模式运行 Apache。 |

表 2-2 中的某些选项仅显示信息，不启动 httpd 服务器。这些选项不适合添加到 apachectl 脚本中。您应该直接运行这些命令。例如，您可以使用以下命令查看已安装的 Apache 版本：

```
/usr/local/apache2/bin/httpd -v
```

或者，您可以使用以下命令查看编译到 Apache 中的模块：

```
/usr/local/apache2/bin/httpd -l
```

## 重启 Apache

每当更改配置文件时，新指令会在下次启动 Apache 时生效。如果在进行更改时 Apache 已关闭，可以如前文“启动 Apache”中所述启动 Apache。但是，如果 Apache 正在运行，则不能使用 start 来重启它。使用 start 会导致错误消息，指出 Apache 已经在运行。当 Apache 当前正在运行时，可以使用以下命令重启 Apache：

```
/usr/local/apache2/bin/apachectl restart
```

虽然 restart 命令通常有效，但有时可能无效。如果重启 Apache 后新设置似乎未生效，请尝试停止 Apache，然后重新启动它。有时这可以解决问题。

## 停止 Apache

要停止 Apache，请使用以下命令：

```
/usr/local/apache2/bin/apachectl stop
```

您可以使用以下命令检查计算机上运行的进程，以确认 Apache 已停止：

```
ps -A
```

ps 的输出不应包含任何 httpd 进程。

## Apache 故障排除

偶尔，在安装 Apache 时可能会遇到问题。本节介绍可能遇到的问题以及如何处理这些问题。

如果您尝试了一切但仍无法使 Apache 工作，可以在 Apache 用户支持列表中寻求帮助。列表中的许多 Apache 用户将帮助您解决问题。要订阅列表，请向 users-subscribe@httpd.apache.org 发送一封空电子邮件。此外，列表档案可用（marc.theaimsgroup.com/?l=apache-httpd-users），因此您也可以搜索过去的消息以找到所需答案。查找问题信息的另一种方法是在 www.google.com 中搜索错误消息的文本或一些描述性词语。如果是常见问题，您可能会找到一些相关信息。

## 编译 Apache 时的问题

如果在运行 configure、make 或 make install 命令时遇到问题，将显示一条指出问题所在的错误消息。在大多数情况下，问题是安装脚本找不到所需的软件。要么您的计算机上未安装该软件，要么该软件未安装在脚本预期查找的位置。有时，计算机上安装的软件是旧版本，需要升级。仔细阅读错误消息，并根据需要安装/升级软件。

如果消息不清楚，可以尝试在 Apache 讨论列表中提问，或在 Google 中搜索该消息。

## 启动 Apache 时的问题

启动 Apache 时，它会读取配置文件以获取所需信息。安装 Apache 时，会创建此文件。通常，可以使用安装时写入文件中的信息启动 Apache。但是，如果 Apache 无法正确启动，配置文件可能存在问题。配置文件在 Book II, Chapter 3 中有详细讨论。

除非在安装时另行指定，否则配置文件位于 /usr/local/apache2/conf/httpd.conf。您可以在安装 Apache 的目录中键入以下行，以检查 Apache 正在查找配置文件的位置：

```
bin/httpd -V
```

输出是设置列表。设置 SERVER_CONFIG_FILE 显示 Apache 正在查找其配置文件的位置。确保该文件存在。

如果在尝试启动 Apache 时收到权限被拒绝错误，可能存在权限问题。用于启动 Apache 的帐户可能没有所需的权限。例如，该帐户可能没有运行 httpd 或打开配置文件的权限。您可能需要使用权限更大的帐户来启动 Apache。通常使用 root 帐户启动 Apache。

Apache 监听配置文件中指定的端口上的请求。如果服务器已在使用该端口，您会看到错误消息。您可以通过编辑配置文件更改服务器正在监听的端口。查找以下行：

```
Listen 80
```

然后将 80 更改为另一个端口号，例如 8080。

## 运行多个 Apache 服务器

您可能希望运行多个 Apache 服务器。例如，您可能希望一个 Apache 服务器用于生产 Web 站点，另一个用于测试环境。或者，您可能希望运行多个版本的 Apache 来测试差异。运行多个 Apache 服务器不是问题。

将每个 Apache 服务器安装在不同的目录中。也就是说，使用 configure 命令的 --prefix 选项指定不同的主 Apache 目录。这会在两个不同的目录中构建两个不同的 Apache 服务器。

您可以启动和停止每个服务器，一次仅运行一个以进行测试。或者，您可以同时运行两个服务器。可以有一个服务器监听单个端口（例如端口 80），另一个服务器监听不同的端口。您可以通过编辑配置文件（例如 conf/httpd.conf）并更改以下行中的端口号来告诉 Apache 监听哪个端口：

```
Listen 80
```

每个 Apache 服务器还需要读取自己的配置文件。默认情况下，配置文件作为 conf/httpd.conf 安装。如果在不同的目录中安装两个服务器，每个服务器都在读取自己的配置文件，例如 /usr/local/apacheA/conf/httpd.conf 和 /usr/local/apacheB/conf/httpd.conf。确保不要更改配置文件的位置，以免两个服务器读取同一个配置文件。

