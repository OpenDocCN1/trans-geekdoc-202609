
该脚本的起始方式与之前相似。它从查询字符串或表单提交中获取提供的成员 ID，然后通过调用 `Member::get()` 在数据库中查找该成员。如果找不到该成员，将显示错误并退出脚本。否则，该成员将存储在 `$member` 变量中。

# 第三部分：在实践中使用 PHP

接下来，脚本会决定调用哪个函数。如果点击了“保存”（Save）按钮，将调用 `deleteMember()` 来更新数据库中的成员记录。如果点击了“删除成员”（Delete Member），将调用 `deleteMember()` 从数据库中移除该成员。否则，调用 `displayForm()` 显示成员详情并访问记录。脚本会传递获取到的 `$member` 对象以便进行显示。

`displayForm()` 的工作方式与在本章早期创建的 `register.php` 脚本中的对应部分类似。它首先获取属于查询成员的 `logEntry` 对象，并将它们存储在 `$logEntries` 数组中。在显示页面头部后，该函数会在页面顶部输出任何错误信息。

接下来，`displayForm()` 从查询字符串或表单提交中获取 `start` 和 `order` 参数，并将它们存储在 `$start` 和 `$order` 中。然后显示表单。表单包含三个字段：

```html
<input type="hidden" name="memberId" id="memberId" value="<?php echo $member->id; ?>">
<input type="hidden" name="start" id="start" value="<?php echo $start; ?>">
<input type="hidden" name="order" id="order" value="<?php echo $order; ?>">
```

`memberId` 用于跟踪正在被查看或编辑的成员 ID，而 `start` 和 `order` 则从成员列表页传递各自的值，以便管理员在查看或编辑成员后能够返回到成员列表的相同位置。

表单的其余部分工作方式与 `register.php` 相同。每个字段都使用 `Member::getValue()`、`setChecked()` 和 `setSelected()` 从成员对象获取数据并显示。表单底部包含一个“保存更改”（Save Changes）按钮和一个“删除成员”（Delete Member）按钮。表单之后，以与 `old_member.php` 脚本相同的方式显示访问日志详情。

表单底部的返回链接工作方式与 `register.php` 略有不同。由于你不知道管理员提交表单的次数，无法像 `register.php` 那样使用 JavaScript 函数调回成员列表页。因此，而是构造指向 `view_members.php` 的新链接，将 `$start` 和 `$order` 值作为起始和查询字符串参数传递，以便管理员返回成员列表的相同位置。

`saveMember()` 检查表单是否提交了数据，如果是，则更新数据库中的成员记录。它的工作方式类似于 `register.php` 中的 `processForm()`。它会创建一个包含表单过滤后值的 `New Member` 对象。如果缺少任何字段，或者用户名或邮箱已被其他成员使用，则会生成错误信息并通过调用 `displayForm()` 重新显示表单。

如果一切顺利，将通过调用 `$member->update()` 更新成员记录，并通过调用 `displaySuccess()` 显示成功消息。注意，根据 `Member::update()` 方法的设计，管理员可以留空密码字段以保留成员现有密码。

`deleteMember()` 简单地创建一个包含表单 `memberId` 隐藏字段中存储 ID 的新 `Member` 对象，然后调用 `object::delete()` 方法从成员表中删除成员记录。它还调用了静态方法 `logEntry::deleteAllMember()` 并传递成员 ID，以便删除该成员相关的任何日志记录。

最后，`displaySuccess()` 函数通知管理员更新或删除操作成功，并提供一个返回到管理员离开处成员列表的链接。通过将表单提交中的 `start` 和 `order` 参数传递到查询字符串来实现。

# 测试成员

你已经构建了成员管理器，现在是测试它了。导航到 `view_members.php`，选择你想要编辑的成员并更改某些细节。点击“保存”，并通过再次查看成员列表来验证更改已更新到数据库。你也可以尝试删除一个成员，并验证他们已从表中移除，且他们的日志记录也已被删除。

## 15 使用 PEAR 让你的工作变得更容易

一旦你开始创建几个 PHP Web 应用程序，你会发现你的脚本经常需要重复执行相同的任务。例如，许多应用程序需要登录/注销机制，而大多数 Web 应用程序在某个时刻需要显示并处理 HTML 表单。

如果你是以模块化的方式编写应用程序（即使用类和函数将它们拆分为特定的功能块），你应该会发现可以在不同的应用程序之间复用这些类或函数。例如，你在第 13 和第 14 章中开发的 `Member` 类可以轻松地用于任何 Web 应用程序注册、存储和检索成员。

代码复用非常重要，因为可以节省你数小时的时间。然而，与其自己编写，不如复用别人的？这样你甚至不需要自己写代码！这就是 PEAR 的由来——PHP 扩展与应用库（PHP Extension and Application Repository），它是一个高质量开源代码包的集合，你可以自由下载并将其用于自己的应用程序中。

使用 PEAR 软件包时，请确保检查其许可协议（license）。某些许可允许你以任何方式使用该包；例如，你可以将代码包含在作为产品销售的应用程序中。其他许可的限制则较多。

每个软件包都是为了实现特定目标而单独维护的类或类集。目前已有超过 500 个软件包可用，涵盖了从数据库访问、身份验证、文件处理、日期格式化、网络甚至甚至预测的所有领域。你可以在 http://pear.php.net/packages/pear.php 浏览完整列表。许多包可以独立运行，但一个包通常需要一个或多个其他包来完成工作。这些其他包被称为主包的依赖（dependencies）。

在开始任何新项目之前，检查 PEAR 仓库查看是否有可以集成到你的应用程序中的包是一个好主意。你可能会发现一半的工作已经由别人为你做好了，节省了大量时间。

## 第三部分：PHP 实战

在本章中，你将仔细研究 PEAR，并学习如何安装和卸载 PEAR 软件包。你将通过编写它们使用的简单脚本来探索一些用的包。在本章结束时，你将编写出能够实现以下内容的应用程序：

- 检测浏览器
- 使用纯 PHP 代码生成 HTML 表格
- 创建、验证和处理 Web 表单

在每个情况下，你都使用 PEAR 软件包来完成大部分困难性工作，让你能够专注于应用程序的逻辑。到本章结束时，你应该应该对 PEAR 软件包的力量以及通用的复用代码有良好的理解。

## 安装 PEAR 软件包

要使用 PEAR 软件包，你需要将其安装在与 PHP 安装在同一个 Web 服务器上，这样你的 PHP 脚本才能访问它。安装 PEAR 软件包非常简单，这得益于 PHP 安装附带的 PEAR 软件包管理器。然而，首要工作是找到你需要安装的包的名称。你可以通过以下一种或多种方式实现：

- 你可以在 http://pear.php.net/packages.php 按类别浏览包。
- 你可以在 http://pear.php.net/search.php 搜索包名和描述。
- 你可以在 http://pear.php.net/package-stats.php 查看按流行程度（下载量最多在前）排序的完整列表。

一旦你找到了想要安装的包，就可以运行 PEAR 软件包管理器进行安装了。不过，先测试包管理器是否可用且正常运行是一个好主意。如果你的 PHP 安装在 Ubuntu 或 Mac OS X 上，PEAR 软件包管理器已经安装并可用。在 Windows 上，你可能需要手动设置包管理器。

## 在 Ubuntu 上测试 PEAR 软件包管理器

要在 Ubuntu 上测试 PEAR 软件包管理器，只需打开终端（应用程序 ➜ 终端）并输入：

```pear
pear
```

然后按回车。你会看到出现了一个命令列表，如下：

```
$ pear
Commands:
build Build an Extension From C Source
bundle Unpacks a Perl Package
channel-add Add a Channel
channel-alias Specify an alias to a channel name
channel-delete Remove a Channel From the List
channel-discover Initialize a Channel from its server
channel-info Retrieve Information on a Channel
```

### 第 15 章：使用 PEAR 让你的工作变得更容易

```
channel-update Update an Existing Channel
clear-cache Clear Web Services Cache
config-create Create a Default configuration file
config-get Show One Setting
config-help Information About Setting
config-set Change Setting
config-show Show All Settings
convert Convert package.xml 1.0 to package.xml 2.0 format
cvsdiff Run a "cvs diff" for all files in a package
cvestag Set CVS Release Tag
download Download Package
dload-all Downloads each available package from the default channel
info Display information about a package
install Install Package
list List Installed Packages In The Default Channel
list-channels List All Packages
list-files List Files In Installed Package
list-upgrades List Available Upgrades
login Connects and authenticates to remote server
logout Logs from the remote server
makerperl Builds an RPM spec file from a PEAR package
package Build Package
package-dependencies Show package dependencies
package-validate Validate Package Consistency
pickle Information About Remote Packages
remote-list List Remote Packages
run-scripts Post-Install Scripts bundled with the package
run-tests Run Regression Tests
search Search package database
shell-test Shell Script Test
sign Sign package distribution file
uninstall Un-Install Package
update-channels Update the Channel List
upgrade Upgrade Package
upgrade-all Upgrade All Packages
```

用法：`pear [options] command [command-options] <parameters>`
输入 "pear help options" 列出所有选项。
输入 "pear help shortcuts" 列出所有命令快捷键。
输入 "pear help <command>" 获取指定命令的帮助。$

这些都是你可以给 PEAR 软件包管理器的命令。例如，向系统安装新包，以及卸载包。

## 使用 Mac OS 和 MAMP 测试 PEAR

如果你在 Mac OS X 上使用 MAMP，过程是类似的，但你应该确保运行的是与 MAMP 兼容的 PEAR 管理器版本，而不是 Mac OS X 默认的。首先打开终端窗口（应用程序 ⇨ 终端）并切换到你 MAMP 安装的 PHP 二进制文件夹。

```
cd /Applications/MAMP/bin/php5/bin/
```

## 第三部分：在实践中使用 PHP

你现在可以通过输入运行 PEAR 软件包管理器：

```
pear
```

并按回车键。与 Ubuntu 一样，你会看到命令列表。

## 在 Windows 上使用 WampServer 安装并测试 PEAR

如果你在 Windows 上运行 WampServer，你首先需要使用 PEAR 软件包管理器。为此，请打开命令提示符（开始 ⇨ 所有程序 ⇨ 命令提示符）并切换到 WampServer 的 PHP 文件夹——例如：

```
cd C:\wamp\bin\php\php5.2
```

编写时还没有 PHP 5.3  WampServer，因此本部分的路径包含 php5.2 文件夹。如果你的 WampServer 带有 PHP 5.3，请将路径改为 php5.3 而不是 php5.2。

在该文件夹中，你应该有一个名为 `go-pear.bat` 的文件。输入其名称并按回车运行此批文件：

```
go-pear.bat
```

批文件将询问你关于配置 PEAR 的问题。通常只需按回车接受默认值。批程序将安装并设置 PEAR，显示类似所示的消息：

```
C:\wamp\bin\php\php5.2.6>go-pear.bat
```
