
# Abyss Web Server PHP 配置

## 配置 PHP 解释器

Abyss Web Server 必须配置为识别 PHP 脚本，并在遇到它们时使用 PHP 解释器。这在 Abyss 控制台中通过将文件扩展名 `".php"` 关联为 PHP 脚本，并指定系统上 PHP 引擎的位置来解释它们来实现：

![image](images/1b.jpg)在浏览器地址栏输入 `http://localhost:9999` 以启动 Abyss Web Server 控制台，然后单击 **配置** 按钮 – 以打开配置页面

![image](images/2b.jpg)单击 ![image](images/pg14_2.jpg)**脚本参数** 图标 – 以打开脚本参数编辑页面

![image](images/3b.jpg)确保已选中 **启用脚本执行** 复选框，然后在解释器表中单击 **添加** 按钮 – 以打开解释器-添加页面

![image](images/4b.jpg)将 **接口** 参数设置为“FastCGI (Local - Pipes)”

![image](images/5b.jpg)将 **解释器** 参数设置为系统上 `php-cgi.exe` 文件的 PHP 路径位置

![image](images/6b.jpg)将 **关联扩展** 参数设置为“`php`”，因此您的配置应如下所示：

![image](images/pg14_3.jpg)

![image](images/pg14_1.jpg)

关于 Abyss Web Server 配置的进一步指导可在网上获得，网址为 **[aprelium.com/abyssws/start.html](http://www.aprelium.com/abyssws/start.html)**

![image](images/forget.jpg)

为澄清本书中的代码示例，PHP 语言的组件以 **蓝色** 显示，程序员指定的名称以 **红色** 显示，数值和字符串数据以 **黑色** 显示，注释以 **绿色** 显示。

![image](images/forget.jpg)

`localhost` 域名是 `127.0.0.1` 域名 IP 地址的别名 – 因此 Abyss Web Server 控制台也可以另行寻址为 `http://127.0.0.1:9999`。

![image](images/7b.jpg)单击 **确定** 按钮以验证您的新配置

![image](images/8b.jpg)单击随后出现的 **重启** 按钮，以应用您对 Abyss 配置所做的更改

![image](images/pg15_1.jpg)

![image](images/snake.jpg)

## 测试配置

文档只有在使用 HTTP 协议由 Web 服务器提供服务时才能由 PHP 引擎解释。您不能直接在浏览器中打开 PHP 文件。始终使用位置 `http://localhost/` 来提供本书中的示例。

Abyss Web Server 现在应该在您的系统上运行，已正确配置为识别具有 `.php` 文件扩展名的文档应由 PHP 引擎解释。现在可以通过创建简单的 PHP 脚本来测试配置，以便 Abyss 为您的 Web 浏览器提供服务：

![image](images/1b.jpg)打开一个纯文本编辑器并准确输入下面的脚本

`<?php phpinfo() ;  ?>`

![image](images/commonb.jpg)

`phpinfo.php`

![image](images/2b.jpg)将脚本另存为 `phpinfo.php`，保存在 Abyss 文档路径目录中，通常位于 `C:\\Abyss Web Server\\htdocs`

![image](images/3b.jpg)在 Web 浏览器的地址栏中准确输入位置 `http://localhost/phpinfo.php`，以查看 Abyss 提供包含您的 PHP 版本信息的网页

![image](images/pg15_2.jpg)

![image](images/snake.jpg)

PHP 脚本区分大小写，因此您必须仅使用小写字符复制所列脚本。

## 嵌入 PHP 脚本代码

![image](images/pg16_1.jpg)

PHP 脚本可以嵌入 HTML 文档中 – 意味着 PHP 和 HTML 代码可以愉快地共存于同一文件中。所有嵌入的 PHP 代码必须包含在 `<?php` 和 `?>` 标签内，以便 PHP 引擎能够轻松识别并解释。通常，PHP 代码会将内容写入 HTML 文档的 body 部分，然后发送到 Web 浏览器：

![image](images/1b.jpg)启动纯文本编辑器并创建此有效的简易 HTML 文档，其中 body 部分为空

```
<!DOCTYPE HTML>
<html lang=“en”>
<head>
<meta charset=”UTF-8”>
<title>Getting Started In PHP</title>
</head>
<body>
</body>
</html>
```

![image](images/commonb.jpg)

`hello.php`

![image](images/2b.jpg)在 body 部分插入标签以包含 PHP 代码

```
<?php
?>
```

![image](images/3b.jpg)接下来，在 PHP 标签之间插入描述性注释和一行代码以将内容写入 body 部分

```
\# Write the traditional greeting.
echo ‘<h1>Hello World!</h1>’ ;
```

![image](images/pg16_2.jpg)

![image](images/hot.jpg)

请注意，描述性注释仅出于信息目的而包含在 PHP 标签之间。

![image](images/4b.jpg)将文档另存为 `hello.php`，保存在 Abyss Web 服务器的 `/htdocs` 文件夹中

![image](images/5b.jpg)现在，在 Web 浏览器的地址栏中输入位置 `http://localhost/hello.php` – 以查看 Abyss 提供包含由嵌入式 PHP 代码编写的内容的网页

![image](images/pg17_1.jpg)

![image](images/6b.jpg)使用 Web 浏览器的工具检查页面的源代码 – 以查看 PHP 已将内容写入 body 部分，包括 HTML `<h1> </h1>` 标签

![image](images/pg17_2.jpg)

![image](images/forget.jpg)

请注意，PHP `echo` 指令会原样写入 **‘ ‘** 单引号对中包含的全部内容。本书中的示例演示了嵌入式 PHP 脚本，但不会重复列出 HTML 代码。

## 按规则脚本编写

![image](images/pg18_1.jpg)

### 标签规则

当 PHP 引擎从 Web 服务器接收输入时，它会从上到下读取输入，此过程称为“解析”。在解析过程中，PHP 引擎（又名解析器）会查找开始和结束的 `<?php` 和 `?>` 标签，并理解这些标签之间的内容是它必须解释的脚本代码。 `<?php` 和 `?>` 标签之外的所有内容都将被完全忽略，这允许 PHP 文件具有混合内容，并允许 PHP 代码嵌入 HTML 中，如下所示：

```
<p>Ignored by PHP and displayed by the browser</p>
<?php echo ‘Script code that will be parsed’ ; ?>
<p>Also ignored by PHP and displayed by the browser</p>
```

因此，为了使此功能正常工作，当嵌入 HTML 文件时，确保所有 PHP 脚本代码都包含在开始和结束的 `<?php` 和 `?>` 标签之间非常重要。

![image](images/hot.jpg)

通常，您的嵌入式 PHP 代码始终会在脚本周围具有开始和结束的 `<?php` 和 `?>` 标签。

此规则的唯一例外是当 PHP 脚本写入纯 PHP 文件中时，该文件仅包含代码。在这种情况下，最好省略结束 `?>` 标签，如下所示：

```
<?php echo ‘Print this First’ ;
echo ‘Print this Last’ ;
```

如果您的 PHP 脚本代码仅打算将单个文本字符串插入 HTML 文档中，则您可以选择使用 PHP 短 echo `<?=` 和 `?>` 标签：

`<?= ‘Hello!’ ; ?>` 等同于 `<?php echo ‘Hello!’ ; ?>`

高级 PHP 脚本代码也可以仅在满足测试条件时插入文本，如下所示：

```
<?php if ( $expression \== true ) : ?>
Insert this text only if the expression is true.
<?php else : ?>
Otherwise insert this text.
<?php endif ; ?>
```

![image](images/forget.jpg)

条件测试将在本书后面完全解释并演示，见 [第 3 章。](#chapter03.xhtml)

### 语句规则

PHP 语言中的每个语句都必须以 `;` 分号字符结尾 – 就像英语中的每个句子都必须以 `.` 句号字符结尾一样。分号被解析器识别为标记它必须解释的单个指令的结束。因此，包含两个语句的 PHP 代码块可能如下所示：

`<?php echo ‘First statement’ ; echo ‘Second statement’ ; ?>`

然而，PHP 代码块的结束 `?>` 标签会自动隐含一个分号，因此您可以选择省略 PHP 块最后一个语句的终止分号，如下所示：
