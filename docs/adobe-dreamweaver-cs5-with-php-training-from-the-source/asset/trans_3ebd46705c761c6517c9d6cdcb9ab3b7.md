
**13** `addFilter()` 方法在 `receive()` 上方的行上采用略有不同的文件引用。使用 PHP 为它分配的临时名称，可以从 `foreach` 循环创建的 `$info` 子数组中访问。修改代码如下：

```php
$uploader->addFilter('Rename', array('target' => $no_spaces, `$info\['tmp_name'\]`));
```

**14** 最后的更改是获取错误信息的代码。修改为：

```php
$messages = implode('. ', $uploader->getMessages());
```

由于 `foreach` 循环分别处理每个文件，`$messages` 必须变成数组。否则，每次循环运行时它会被覆盖。然而，`getMessages()` 方法输出一个数组。为了避免处理多维数组的需求，`getMessages()` 的输出通过 `implode()` 转换为字符串。`getMessages()` 生成的每条消息都以大写字母开头，因此 `implode()` 的第一个参数加上句点和空格来分隔每条消息。

此更改需要在两个位置进行：在紧随 `receive()` 调用之后的条件语句中，以及第一个使用 `isValid()` 方法的条件语句中（见步骤 10）。

**15** 保存 `process_upload.php`、`upload_test_multi.php` 并测试多文件上传表单。它的功能与之前完全相同，只是现在可以同时上传一个、两个或三个文件。

单文件上传的功能意味着该脚本同样适用于原始只有一个文件域的上传表单。

您可以将您的代码与 lesson09/completed/scripts 中的 `process_upload_06.php` 进行比较。

##### *Customizing error messages*

文件上传脚本基本完成。要将其适应您自己的网站，只需更改上传文件夹的目标并使用您自己的验证类。唯一的问题是 `getMessages()` 方法生成的一些错误消息措辞略显奇怪。该问题部分通过添加重命名文件的代码以及选择是否覆盖现有文件来部分解决。但如果选择了错误的 MIME 类型，仍会出现关于“错误”类型的消息。

根据您的编码技能和上传表单的目标受众，您需要投入多少努力来自定义错误消息。一个简单但相当粗糙的方法是，在文件验证失败时自行生成消息：

```php
if (!$uploader->isValid($file)) {  
    $messages[] = "Sorry, $filename doesn't match the requirements";  
} else {
```

问题在于这并未指示文件出错的具体原因。

更好的做法是使用 `getErrors()` 方法查找错误信息，然后在您认为有必要时自定义消息。`getErrors()` 方法返回一个错误代码数组。

错误代码为不正确的 MIME 类型时为 `fileMimeTypeFalse`。因此，要在上传了错误类型的文件时显示自定义错误消息，只需修改相同代码段：

```php
if (!$uploader->isValid($file)) {  
    $error_codes = $uploader->getErrors();  
    if (in_array('fileMimeTypeFalse', $error_codes)) {  
        $messages[] = "$filename is not an image";  
    } else {  
        $messages[] = implode('. ', $uploader->getMessages());  
    }  
} else {
```

如果文件验证失败，`getErrors()` 方法获取错误代码数组，而条件语句使用 `in_array()` 检查 `fileMimeTypeFalse` 是否在数组中。如果在，则向 `$messages` 添加自定义消息，报告文件不是图像。如果 `fileMimeTypeFalse` 不在 `$error_codes` 数组中，则表示其他问题，使用默认消息。

现在选择上传非图像文件会显示更友好的提示信息。

![Image](graphics/fig09_21.jpg)

**Table 9.2** (##ch09.html#ch09tab2) 列出了常见的错误代码，可用于创建自定义消息。

**Table 9.2. Common File Validation Error Codes**

![Image](graphics/t0333-01.jpg)

该代码位于 lesson09/completed/scripts 中的 `process_upload_07.php`。脚本已大量注释，帮助您理解其工作原理。

### 发送带附件的电子邮件

现在您知道如何上传文件，将附件添加到在线表单发送的电子邮件就很简单。要发送带附件的电子邮件，您需要先将文件上传到服务器。然后使用 PHP 函数 `file_get_contents()` 获取文件内容，并将其传递给 `Zend_Mail` 的 `createAttachment()` 方法。除非您想修改默认的编码（base64）和 disposition（inline），否则就完成了。

附件的潜在问题（除了恶意软件）是，如果您不在服务器的文件系统中保存上传文件，它们会被丢弃。用户如果在提交表单时出现错误，就需要重新上传文件，这很烦人。另一方面，您也不希望在文件系统中堆积已经作为附件发送的文件。

解决方案是使用会话变量为文件名前缀，暂时存储文件。这样在表单重新提交时可以正确检索文件。发送邮件后，您可以删除文件，保持临时上传目录整洁。

本课结束前，您将适配本课的文件上传脚本，并将其与 [Lesson 8](#ch08.html#ch08) 的反馈表单合并，使用户能够从您的网站发送附件。

#### 适配文件上传脚本

当将文件作为附件上传时，脚本可以简化。例如，您不必担心覆盖现有文件，因为附件会使用唯一前缀暂时存储，并在发送后从文件系统中删除。

**1.** 创建一个新的 PHP 页面并保存为 **get_attachments.php**，放在 lesson09/workfiles/scripts。

**2.** 删除默认的 HTML 代码，并添加一个开头 PHP 标签。

**3.** 该脚本使用会话变量，因此先添加 `session_start()`，随后定义一些基本设置：

```php
session_start();  
$destination = 'C:/upload_test';  
$max_size = '50kB';  
$not_allowed = 'exe,vbs,shs,pif,lnk,dll';
```

在此定义基本设置可以让后续修改更方便。如前，`$destination` 为上传目录；`$max_size` 设定每个附件的最大大小；`$not_allowed` 为被 `ExcludeExtension` 验证类拒绝的文件扩展名列表。

**4** 您不希望在附件已经存储在文件系统时运行上传脚本。因此，需要包含一个检查会话变量是否存在的条件语句。若变量不存在，说明是首次提交表单。添加以下代码：

```php
if (!isset($_SESSION['att_id'])) {  
    $_SESSION['att_id'] = 'att' . time() . '-';  
    $_SESSION['attachments'] = array();  
}
```

如果 `$_SESSION['att_id']` 不存在，则通过构建基于当前时间戳的字符串创建它，形如 att1273166609-，用于在每个文件名前加前缀。

