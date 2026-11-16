

安装向导目前不会自动配置 Apache 的 httpd.conf 文件，因此你可能会看到关于此事的对话框。别担心，我们将在接下来介绍如何配置 Apache 以使用 PHP。

安装完成后，你会看到一个声明安装成功的对话框和一个“确定”按钮。单击“确定”，我们将继续配置 Apache。

## 将 Apache 配置为使用 PHP

由于 Windows 线程下第三方软件不稳定，我们将在 Windows 下配置 Apache 以 CGI 方式使用 PHP。即使你计划采用 ISAPI 模块路线，也应遵循这些说明，先进行 CGI 配置并确保一切正常。在其他所有部分都正常工作后，再切换到 ISAPI 模块用法会容易得多。你需要在 ISAPI 下进行大量压力测试，以确保你的 Web 服务器稳定。

首先，确保 Apache 未运行。在 PHP 目录（默认 C:\php\）中，你应该找到名为 php4ts.dll 的文件。Windows 9x/ME 用户应将其复制到 C:\Windows\System\，而 Windows NT/2000 用户应将其复制到 C:\WinNT\System32\。

找到 httpd.conf 文件，默认位于 C:\Program Files\Apache Group\Apache\conf\。在编辑该文件前，先制作备份副本。

使用文本编辑器打开此文件。使用“查找”菜单项搜索 ScriptAlias 部分。它通常位于 <IfModule mod_alias.c> 和 </IfModule> 之间。可能存在多个 ScriptAlias 部分，且 IfModule 行之间可能隔着大量文本。在 ScriptAlias 部分，添加以下行：

```
ScriptAlias /php/ "C:/php/"
```

这告诉 Apache 在哪里查找各种 PHP 文件，并创建一个别名，以便稍后在 httpd.conf 中引用该目录。如果你将 PHP 安装在非默认位置，则需要更改上面的路径。不要在 httpd.conf 中使用 Windows \，而要使用 /。

如果似乎没有现有的 ScriptAlias 部分，请在与你的 DocumentRoot 对应的 <Directory...> 行后面直接添加上面的行。Apache 安装说明中对这些内容提供了更多说明。

其次，查找 httpd.conf 的 AddType 部分。那里应该已经有一些 PHP4.x 行。你可以取消注释（删除开头的 # 字符），也可以在上述注释下方键入一行：

```
AddType application/x-httpd-php .php
```

这告诉 Apache，以 .php 结尾的文件应被视为 MIME 类型 application/x-httpd-php。就像 GIF 文件的 MIME 类型是 image/gif，JPEG 文件是 image/jpg 一样。如果似乎没有 AddType 部分，请将此行放在如上所述的 <Directory...> 部分内。

最后，查找 httpd.conf 的 Action 部分。这通常包含一些示例 Format: 行。在 Action 部分中添加以下行：

```
Action application/x-httpd-php "/php/php.exe"
```

这告诉 Apache，MIME 类型为 application/x-httpd-php（即我们通过上面的 AddType 定义的类型）的文件，应由位于我们上面输入的 ScriptAlias "/php/" 所定义目录中的名为 php.exe 的文件来处理。

同样，如果你的 httpd.conf 中似乎没有 Action 部分，只需像上面一样将此行添加到 Directory 部分内。检查你添加的行是否有拼写错误。虽然这些行分布在 httpd.conf 文件中以按命令进行组织，但这三行协同工作，告诉 Apache 如何处理 PHP 文件。

你可能希望修改那第二行，以便将以 .php3（你可能发现的旧脚本）或甚至 .htm 和 .html 结尾的文件传递给 PHP。强制所有 HTML 文件通过 PHP 处理不会显著降低响应时间。此外，包含旧扩展名将允许你在现有 HTML 文件的各种位置添加 PHP 功能，而无需重新链接到你的网站。它还允许使用用户习惯的 .htm 或 .html，而不是 .php。

你的 AddType 行最终可能如下所示：

```
AddType application/x-httpd-php .php .htm .html .php3
```

文件扩展名的顺序无关紧要，你可以添加任意多个合理的扩展名。例如，通常将 .mp3 文件传递给 PHP 处理并没有多大意义。事实上，这可能会破坏你的 MP3 URL，因为 PHP 会添加一些默认头信息。

在对所有更改进行审核后，保存 httpd.conf 文件并重启 Apache。

## 可能出错的情况？

如果 Apache 此时无法启动，请检查你添加的三行是否有拼写错误。另外，请确保：

- ScriptAlias 行中你的 PHP 安装目录正确。
- 该路径中使用了 / 而不是 \\。
- AddType 和 Action 行上的 MIME 类型 application/x-httpd-php 相同。复制并粘贴这两行，以确保它们完全一致。
- php.exe 实际上位于正确的目录中。
- 已将 php4ts.dll 复制到你的 Windows 系统目录。

如果你已仔细检查了以上所有内容，并停止/重启了 Apache 但仍无法工作，请查看“安装 Apache”部分下的“可能出错的情况？”部分。特别是，检查错误日志和 MS DOS 控制台窗口中的错误。

如果一切都无效，尝试将 php4ts.dll 复制到与 php.exe 相同的目录中。理应，Windows 应该能够在系统目录中找到它并加载，但如果不行，PHP 很可能可以在它与 php.exe 位于同一目录时找到它。

## 测试 PHP 安装

在你的 `httpd.conf` 文件中，有一个名为 `DocumentRoot` 的设置。还有一个与 `DocumentRoot` 设置具有相同路径的 `<Directory ...>` 设置。如果你未更改它们，并且使用默认设置安装，它们可能设置为 `C:\Program Files\Apache Group\Apache\htdocs\`。

`DocumentRoot` 是你的 Web 服务器主页所在的位置。那里已有一个名为 `index.html` 的文件，用于处理对你网站的任何请求。

在该目录中创建一个名为 `phpinfo.php` 的文本文件，并在其中放入以下单行文本：

```
<?php
phpinfo();
?>
```

将该文件保存在你的 `DocumentRoot` 中。使用 Web 浏览器访问 `http://localhost/phpinfo.php`。

如果你已正确安装 PHP，应该会看到详细说明你的 PHP 安装属性的以下页面：

![](img/9cf7789dba9b16ef3f8576d5aea89186_54_0.png)

### 可能出错的情况？

如果你看到 404 文档未找到或类似错误，可能是你没有将 `phpinfo.php` 保存在正确的目录中，或者拼写了错误的文件名，或者 URL 输入错误。如果你看到 500 内部服务器错误，可能是 `httpd.conf` 中有拼写错误。

如果你更改了 `DocumentRoot`，请确保相应的 `<Directory...>` 设置已更改为完全相同的目录。如果它们不匹配，Apache 将无法工作。如上文 *安装 Apache* 部分中 *可能出错的情况？* 所讨论，检查 Apache 错误日志。

如果你看不到任何内容，尝试使用浏览器的“查看源文件”菜单项。如果它显示 `<?php phpinfo(); ?>`，则表示 Apache 正在提供网页，但未正确配置为先将其交给 PHP 处理。因此，你添加到 `httpd.conf` 中的三个 `ScriptAlias`/`AddType`/`Action` 行之一一定有误。或者你忘记停止并重启 Apache。Apache 仅在启动时读取一次 `httpd.conf`。你必须重启 Apache，对 `httpd.conf` 的更改才能生效。

如果你看不到任何内容且“查看源文件”菜单项不可用，请检查 Apache 错误日志并检查 `httpd.conf` 设置。可能某些配置错误足以导致 Apache 崩溃。

如果一切都无效，尝试通过在 `httpd.conf` 中添加的三行前面插入 # 符号将其注释掉，然后重启 Apache。如果 Apache 此时能正常工作但 PHP 不行，至少你知道问题出在这三行中，或者你的 PHP 安装本身有问题。

如果你在 `httpd.conf` 中输入的内容未发现任何问题，请独立于浏览器测试 PHP 本身是否正常工作：

打开一个 MS DOS 控制台窗口，将目录更改为 C:\php\ 或 PHP 安装的任何位置。然后键入：

```
php C:\Program Files\Apache Group\Apache\htdocs\phpinfo.php
```

如果你的 `phpinfo.php` 文件位于其他目录，可能需要替换为不同的路径。

将调用 `php.exe`，因为你实际上是将 `phpinfo.php` 文件交给它来处理。PHP 应该执行该文件中的代码并返回 HTML。如果 PHP 显示 HTML 代码，则说明 `php.exe` 正常工作，且问题出在 Apache 调用 PHP 的方式上。再次检查你的 `httpd.conf` 设置。

如果 `php.exe` 单独能正常工作，Apache 在没有那三行调用 PHP 的情况下也能正常工作，但两者不能一起工作，那么你的错误一定出在那三行中。

## 安装后

安装 PHP 时，会随附安装一个名为 `php.ini` 的文件。你的 `phpinfo.php` 页面还应该说明 PHP 在哪里查找 `php.ini` 文件。为此 `php.ini` 文件制作备份副本，并确保 `phpinfo.php` 正在查找 `php.ini` 文件所在的位置。

如果到处都找不到 `php.ini` 文件，请查找 `php.ini-dist` 文件，并将其复制到 `phpinfo` 中列出的相应目录下的 `php.ini`。

使用文本编辑器打开 `php.ini` 文件，浏览其中的所有设置。你可能想对其中一些设置进行实验，也可能想在 http://php.net/ 上进行一些在线研究，以了解特定设置的作用。

首先，如果你不是经验丰富的程序员，建议将 `error_reporting` 提高一个档次到 `E_ALL`。找到“错误处理和日志记录”部分，并更改以下内容的行：

```
error_reporting = E_ALL & ~E_NOTICE ;show all errors, except for notices
```

