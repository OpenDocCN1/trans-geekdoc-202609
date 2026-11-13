

```
display_errors = On
log_errors = Off
```

你可以使用 error_log 指令指定替代文件名，如下例所示：

```
error_log = /tmp/php_log
```

## 配置 PHP 扩展

某些 PHP 扩展拥有可在 php.ini 中配置的指令，用于调整该扩展的行为。

为了配置文件的清晰度，使用小节标题来区分扩展特定的设置。例如，所有影响 MySQL 扩展的设置都位于 php.ini 中以 [MySQL] 开头的小节中。每个指令名称还带有一个前缀，指示它所属的扩展（例如，mysql.connect_timeout 或 session.cookie_path）。

你可以在每个扩展的在线手册页面中找到扩展特定配置指令的文档。

## 配置系统安全性

本课程未涵盖的 php.ini 中的某些指令，尤其是 safe_mode 指令及其相关设置，涉及服务器安全性。这些配置选项允许你限制 Web 服务器上的某些功能类型，你将在第 24 课“PHP 安全性”中了解它们。

## 可加载模块

PHP 允许你在运行时加载某些扩展。这意味着你可以在不需要从源代码重新编译的情况下扩展 PHP 的功能。

### 按需加载扩展

你使用 dl 函数来动态加载扩展模块。在编译 PHP 时，你使用 --with-EXTENSION=shared 开关将扩展构建为动态可加载对象。例如，运行以下 configure 语句会导致 PHP 被编译为带有链接的 MySQL 支持，但 socket 支持作为可加载扩展：

```
./configure --with-mysql --with-sockets=shared
```

传递给 dl 的参数是扩展的文件名。在 sockets 扩展的情况下，在 Linux/Unix 上它被称为 sockets.so，而在 Windows 系统上则称为 php_sockets.dll。

**可加载扩展** dl 函数是否可用由 php.ini 中的 enable_dl 指令控制。你可能会发现，在共享 Web 托管服务上，你无法使用此功能。

要检查扩展是否已加载到 PHP 中，你使用 extension_loaded 函数。给定一个扩展名称参数，该函数根据该扩展的存在与否返回 true 或 false。请注意，PHP 无法判断扩展是通过 dl 加载的还是编译在内的。

### 启动时加载模块

如果你拥有作为可加载模块的扩展，并且希望它们在不需要在每个脚本中运行 dl 的情况下加载到 PHP 中，你可以使用 php.ini 中的 extension 指令来提供在启动时要加载的扩展列表。

每个扩展单独一行，并且以这种方式可以加载的扩展数量没有限制。php.ini 中的以下行确保在 Linux/Unix 服务器上自动加载 sockets 和 imap 扩展：

```
extension=imap.so
extension=sockets.so
```

在 Windows Web 服务器上，配置行需要如下所示，以反映两个平台之间文件名的差异：

```
extension=php_imap.dll
extension=php_sockets.dll
```

## 摘要

在本课中，你学习了如何在运行时配置 PHP。在下一课中，你将学习 PHP 的安全模式以及如何最大限度地减少对网站的安全威胁。

## 第 24 课。PHP 安全性

PHP 无疑是一种非常强大的服务器端脚本语言，但权力越大，责任越大。在本课中，你将学习如何使用 PHP 的安全模式，确保 PHP 的某些潜在危险功能被锁定。

## 安全模式

PHP 的安全模式试图在共享环境中提供一定程度的基本安全性，在该环境中，多个用户帐户存在于启用 PHP 的 Web 服务器上。

当 Web 服务器以安全模式运行 PHP 时，某些函数被完全禁用，而其他函数则以有限功能可用。

### 安全模式强制的限制

尝试访问文件系统的函数在安全模式下功能受限。Web 服务器进程为所有 Web 空间帐户以相同的用户 ID 运行，并且必须具有适当的读取或写入权限才能访问文件。这是底层操作系统的要求，与 PHP 本身无关。

当启用安全模式并尝试读取或写入本地文件时，PHP 检查脚本的文件所有权是否与目标文件相同。如果所有者不同，则禁止该操作。

**写权限** 虽然安全模式实施了防止你通过 PHP 打开其他用户文件的措施，但操作系统的文件权限仍可能在较低级别允许对这些文件的读取甚至写入访问。请注意，具有 Web 服务器 shell 访问权限的用户能够读取 Web 服务器可访问的任何文件，并写入具有全局写入权限的任何文件。

以下核心文件系统函数受此规则限制：

- chdir
- chgrp
- chown
- copy
- fopen
- highlight_file
- include
- link
- mkdir
- move_uploaded_file
- parse_ini_file
- rmdir
- rename
- require
- show_source
- symlink
- touch
- unlink

属于 PHP 扩展且也访问文件系统的函数同样受到影响。

**可加载模块** `dl` 函数在安全模式下被禁用，无论扩展文件的所有者是谁。扩展必须在启动时加载到 PHP 中，使用 php.ini 中的 `extension` 指令。

执行主机程序的函数被禁用，除非它们在 `safe_mode_exec_dir` 指令给定的目录中运行，你将在下一节中了解它。即使允许执行，命令的参数也会自动传递给 `escapeshellcmd` 函数。

受此规则影响的程序执行函数如下：

- exec
- shell_exec
- passthru
- system
- popen

此外，反引号运算符 (`) 被禁用。

`putenv` 函数在安全模式下运行时无效，尽管不会产生错误。同样，其他尝试更改 PHP 环境的函数，例如 `set_time_limit` 和 `set_include_path`，会被忽略。

## 启用安全模式

你通过在 php.ini 中使用 `safe_mode` 指令来打开或关闭安全模式。要在共享 Web 服务器上为所有用户激活安全模式，请使用以下指令：

```
safe_mode = On
```

如你在上一节中所学，访问文件系统的函数会对文件所有者进行检查。默认情况下，检查是针对文件所有者的用户 ID 执行的，但你可以通过打开 `safe_mode_gid` 指令将其放宽为检查所有者的组 ID (GID)。

如果系统上有共享库文件，你可以使用 `safe_mode_include_dir` 指令来获取位置列表，当遇到 `include` 或 `require` 语句时，不会对这些位置执行 UID/GID 检查。

**包含目录** 如果你想在 `safe_mode_include_dir` 指令中列出多个位置，可以在 Linux/Unix 上使用冒号分隔，在 Windows 系统上使用分号分隔，就像使用 `include_path` 设置一样。

要允许任何用户在安全模式下包含 `/usr/local/include/php` 中的文件，你将使用以下指令：

```
safe_mode_include_dir = /usr/local/include/php
```

要提供系统可从中执行的位置，你使用 `safe_mode_exec_dir` 指令。

要允许在安全模式下执行 `/usr/local/php-bin` 中的程序，你将使用以下指令：

```
safe_mode_exec_dir = /usr/local/php-bin
```

**可执行文件** 与其允许从 `/usr/bin` 或其他系统位置执行所有程序，不如创建一个新目录，并仅将选定的二进制文件复制或链接到其中。

要允许设置某些环境变量，你使用 `safe_mode_allowed_env_vars` 指令。给定的值是一个前缀，默认情况下仅允许更改以 `PHP_` 开头的环境变量。如果给出多个值，列表应使用逗号分隔。

以下指令还允许更改时区环境变量 `TZ`：

```
safe_mode_allowed_env_vars = PHP_, TZ
```

