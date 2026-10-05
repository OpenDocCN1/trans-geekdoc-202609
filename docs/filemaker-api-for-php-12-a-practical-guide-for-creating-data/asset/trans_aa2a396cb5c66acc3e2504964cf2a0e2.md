
包含了一个相当常见的文件类型列表。如果你不确定特定文件类型的 MIME 类型，可以始终通过发送该文件给自己来节省邮件。然后检查源代码中的 `content type`。

```php
$allowed_type = array("application/msword",
"application/vnd.openxmlformats-officocument.wordprocessingml.document",
"application/vnd.ms-excel",
"image/gif",
"image/jpeg",
"application/pdf",
"image/png",
"text/plain",
"application/zip");
```

一旦你确定该文件类型是允许的，就需要对其进行 base64 编码，以便邮件程序能够正确处理文件。此此的方法是打开文件并读取二进制内容。打开文件后，你可以将内容存储到 $data 变量中。然后关闭文件。最后一步是对文件进行 base64 编码并使用 `chunk_split` 分分为易于管理的大小。如果你查看过 base64 编码文件的原始文本，你会发现它可能非常长。

```php
if(in_array($type,$allowed_type)) {
		$file = fopen($tmp_name,'rb');
		$data = fread($file,filesize($tmp_name));
		fclose($file);
		$data = chunk_split(base64_encode($data));
	} else {
```

如果用户上传了不允许的文件类型，你应该在发送邮件之前显示消息并退出脚本。请记住：你并不会真正上传并将文件移动到服务器的永久位置。这种方法的巧妙之处在于，一旦脚本运行结束，文件将自动从服务器上删除。临时文件夹不会长时间存储这些文件。

```php
{
		echo "file type not allowed: " . $type;
		exit();
	}
}
```

现在我们已经验证并编码了附件，可以为附件创建一个边界（boundary）了。这与消息的边界非常相似，不同之处附件是经过 base64 编码的。使用我们在代码此部分创建的 `$_FILES` 变量来获取类型和名称，用以组装所需的边界信息。再次强调，这部分**必须完全准确**，不能包含 CRLF。如果你多或少了一个空格，或者多了一个 CRLF，附件将无法工作。尽管 PHP 可能会很宽容，但格式要求不会。结束边界的代码用于指示其在消息中的位置。它在行尾有两个破折线 "-"。

```php
$message = "--{$mime_boundary}\n\nContent-Type: {$type};\n\nname="{$name}"\n\nContent-Disposition: attachment;\n\nfilename="{$filename}"\n\nContent-Transfer-Encoding: base64\n\n\n";

$message .= "--{$mime_boundary}--\n";
```

只要到目前还没有出现任何错误，就是时候发送邮件了。由于我们已经将所有内容加载到变量中，只需要指定 `mail` 函数并测试消息是否发送。请记住，即使该函数没有返回错误，也不意味着消息没有进入垃圾箱，或没有遇到其他阻止其送达的错误。我鼓励你彻底测试你的系统，包括对线上系统进行随机测试，以确保一切运行都符合预期。我无法告诉你遇到过多少公司，他们声称邮件无法发出去，结果发现是因为他们更改了防火墙、网络，或者升级/更改了邮件服务器，而在遇到关键问题之前，他们没有考虑到测试所有受影响的系统。

```php
if (mail($to, $subject, $message, $headers)) {
    echo "Your mail was sent"; exit();
} else {
    echo "There was an error sending your mail"; exit();
}
```

网页的最后部分是表单。表单位于代码的末尾，而不是页面顶部。你希望你的 PHP 代码在点击提交按钮且信息回传到同一页面之后运行。这允许你在发送邮件之前捕获任何缺失的字段并对所有数据进行验证。

表单非常直观。我选择将 `Alert` 变量放在页面顶部。记住，我们创建 `Alert` 是为了在用户没有填写所有字段时向他们显示消息。

我认为这种基础方法的优点是，你可以包含你所需要的任何数量的文件字段。如果用户使用了零个或多个字段，代码都可以运行。如果你不需要上传文件，只需从表单中删除文件字段，其他代码保持不变。

本节课程中没有包含的唯一项目是 Google reCAPTCHA 的使用，那在另一节课程中介绍过。如果你不需要防止机器人向你发送大量垃圾邮件，可以在提交按钮上实现 Google 的 reCAPTCHA。

关于这个表单，我想指出几点，虽然它们看起来显而易见，但很多人忘记了你可以限制垃圾邮件进入你的系统。首先，邮件的长度为 64 个字符。过滤器只对 64 个字符有效。不要让用户输入任何内容。你上一次看到超过 64 个字符的邮件是什么时候了？主题也是如此。他们不需要写一本书。几个词就可以了。最后，记住，某些应用程序对于长度超过 78 个字符的行可能会出现问题。我将消息的文本区域列宽设置为 78 个字符。这非常重要，因为我们在代码中使用 `wordwrap` 来匹配 RFC2822 标准。然而，让用户在屏幕上获得视觉反馈是很好的，例如：

```php
<?php echo $alert; ?>
<form action="<?php echo $_SERVER['REQUEST_METHOD']; ?>" method="post" enctype="multipart/form-data">
<p>From-email: <input name="email" type="text" size="60" maxlength="64"></p>
<p>Subject: <input name="subject" type="text" size="60" maxlength="64"></p>
<p>Message: <textarea name="message" rows="4"></textarea></p>
<p>File 1: <input type="file" name="file1"></p>
<p>File 2: <input type="file" name="file2"></p>
<input type="submit" name="Submit" value="Submit"></p>
</form>
</body>
```

这里有一个防弹的 PHP 邮件消息，可以防止机器人和垃圾邮件发送者利用邮件注入技术接管你的邮件服务器。我们学习了如何组装边界、消息和附件。使用我们创建的 `$_FILES` 全局变量，我们创建了一个带有视觉反馈的表单。最好的部分是每个页面都将其字段和数据传递给下一个页面。只需表单内部的几行 PHP 代码。整个过程只需要几分钟。

