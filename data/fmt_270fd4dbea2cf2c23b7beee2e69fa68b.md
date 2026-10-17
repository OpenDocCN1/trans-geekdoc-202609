
```php
$uploader->addFilter('Rename', array('target' => $no_spaces, $info['tmp_name']));
```

**14** 最后的更改是获取错误信息的代码。修改为：

```php
$messages = implode('. ', $uploader->getMessages());
```

由于 `foreach` 循环分别处理每个文件，`$messages` 必须变成数组。否则，每次循环运行时它会被覆盖。然而，`getMessages()` 方法输出一个数组。为了避免处理多维数组的需求，`getMessages()` 的输出通过 `implode()` 转换为字符串。`getMessages()` 生成的每条消息都以大写字母开头，因此 `implode()` 的第一个参数加上句点和空格来分隔每条消息。

此更改需要在两个位置进行：在紧随 `receive()` 调用之后的条件语句中，以及第一个使用 `isValid()` 方法的条件语句中（见步骤 10）。

**15** 保存 `process_upload.php`、`upload_test_multi.php` 并测试多文件上传表单。它的功能与之前完全相同，只是现在可以同时上传一个、两个或三个文件。

单文件上传的功能意味着该脚本同样适用于原始只有一个文件域的上传表单。

您可以将您的代码与 `lesson09/completed/scripts` 中的 `process_upload_06.php` 进行比较。

### Customizing error messages

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

![Image](img/fig09_21.jpg)

**Table 9.2** (`##ch09.html#ch09tab2`) 列出了常见的错误代码，可用于创建自定义消息。

**Table 9.2. Common File Validation Error Codes**

![Image](img/t0333-01.jpg)

该代码位于 `lesson09/completed/scripts` 中的 `process_upload_07.php`。脚本已大量注释，帮助您理解其工作原理。

### 发送带附件的电子邮件

现在您知道如何上传文件，将附件添加到在线表单发送的电子邮件就很简单。要发送带附件的电子邮件，您需要先将文件上传到服务器。然后使用 PHP 函数 `file_get_contents()` 获取文件内容，并将其传递给 `Zend_Mail` 的 `createAttachment()` 方法。除非您想修改默认的编码（base64）和 disposition（inline），否则就完成了。

附件的潜在问题（除了恶意软件）是，如果您不在服务器的文件系统中保存上传文件，它们会被丢弃。用户如果在提交表单时出现错误，就需要重新上传文件，这很烦人。另一方面，您也不希望在文件系统中堆积已经作为附件发送的文件。

解决方案是使用会话变量为文件名前缀，暂时存储文件。这样在表单重新提交时可以正确检索文件。发送邮件后，您可以删除文件，保持临时上传目录整洁。

本课结束前，您将适配本课的文件上传脚本，并将其与 Lesson 8 的反馈表单合并，使用户能够从您的网站发送附件。

#### 适配文件上传脚本

当将文件作为附件上传时，脚本可以简化。例如，您不必担心覆盖现有文件，因为附件会使用唯一前缀暂时存储，并在发送后从文件系统中删除。

**1.** 创建一个新的 PHP 页面并保存为 `get_attachments.php`，放在 `lesson09/workfiles/scripts`。

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

如果 `$_SESSION['att_id']` 不存在，则通过构建基于当前时间戳的字符串创建它，形如 `att1273166609-`，用于在每个文件名前加前缀。

表达当前日期和时间为过去约 40 年中的秒数可能看起来很奇怪。尽管时间戳对人类来说难以理解，但 PHP 函数使用它们来快速简便地进行日期计算，避免了不同长度月份和闰年带来的复杂性。1970 年 1 月 1 日被称为 Unix 纪元，这种日期和时间的表示方式通常被称为 Unix 时间戳。

`$_SESSION['attachments']` 也初始化为一个空数组。

**5.** 在你刚刚创建的条件语句内部，实例化一个文件传输对象并设置上传目标和验证类：

```php
$uploader = new Zend_File_Transfer_Adapter_Http();
$uploader->setDestination($destination);
$uploader->setOptions(array('ignoreNoFile' => TRUE));
$uploader->addValidator('Size', FALSE, $max_size);
$uploader->addValidator('ExcludeExtension', FALSE, $not_allowed);
```

这与主上传脚本中的代码基本相同。它使用 `ExcludeExtension` 而不是 `MimeType` 验证类。

**6.** 剩余的代码也在条件语句内部，代码如下（高亮行在下面代码列表中解释）：

```php
$files = $uploader->getFileInfo();
foreach($files as $file => $info) {
  if ($uploader->isUploaded($file)) {
    $filename = $uploader->getFileName($file, FALSE);
    if (!$uploader->isValid($file)) {
      $messages[] = "$filename exceeds $max_size or is not an acceptable type";
    } else {
      $attachment = $_SESSION['att_id'] . str_replace(' ', '_', $filename);
      $uploader->addFilter('Rename', array('target' => $attachment), $file);
      $success = $uploader->receive($file);
      if (!$success) {
        $messages[] = "$filename could not be attached";
      } else {
        $messages[] = "$filename attached";
      }
    }
  }
}
```

这与你之前构建的文件上传脚本遵循类似的模式，只是更短更简单。如果文件验证失败，会使用 `$filename` 和 `$max_size` 创建一条消息。

在主 `else` 块内部，会在第一次加载页面时显示文件字段，提交后若表单有错误则隐藏这些字段并显示附件提示信息。

在主 `else` 块中，会移除文件名中的空格并添加前缀，生成类似 `att1273166609-bryce1.jpg` 的文件名。修改后的文件名存储在 `$attachment` 中，而原始文件名保留在 `$filename` 中。

`Rename` 过滤器使用 `$attachment`（例如 `att1273166609-bryce1.jpg`），而 `$_SESSION['attachments']` 使用 `$filename` 以保留原始文件名，以便在电子邮件中使用。

你可以将你的代码与 `get_attachments.php` 在 `lesson09/completed/scripts` 中进行比较。

#### 适配邮件处理脚本

对 Lesson 8 中的邮件处理脚本进行以下修改：

**1.** 复制 `lesson09/start/scripts/process_attachments.php`，保存到本课程的 `workfiles/scripts` 文件夹中。或者，你可以使用上一课的 `process_comments.php`。

**2.** 在 `process_attachments.php` 中，使用 `require_once()` 包含 `get_attachments.php`。代码应放在最后的验证语句和检查错误的条件语句之间（大约第 30 行）：

```php
if (!$val->isValid($_POST['comments'])) {
$errors['comments'] = 'Required';
}
require_once('get_attachments.php');
if (!$errors) {
```

这确保即使表单出错，附件也会被保存。

**3** 将附件附加代码放在发送邮件之前（大约第 48 行）。完整代码块如下：

```php
$mail->setBodyHtml($html, 'UTF-8');
if (isset($_SESSION['attachments']) && !empty($_SESSION['attachments'])) {
  foreach($_SESSION['attachments'] as $attached) {
    $current_file = $destination . '/' . $_SESSION['att_id'] . $attached;
    $contents = file_get_contents($current_file);
    $att = $mail->createAttachment($contents);
    $att->filename = $attached;
    unlink($current_file);
  }
  unset($_SESSION['attachments']);
  unset($_SESSION['att_id']);
}
$success = $mail->send();
```

这段代码被包装在判断 `$_SESSION['attachments']` 是否存在且不为空的条件语句中，确保只有在有附件需要发送时才执行。

在条件语句内部，`foreach` 循环会处理 `$_SESSION['attachments']` 中存储的文件名，将每个文件名赋值给临时变量 `$attached`。每次循环中，`$attached` 保存当前文件的原始文件名。要从上传文件夹获取文件内容，需要使用完整路径，包括用于存储文件的前缀。具体做法如下：

```php
$current_file = $destination . '/' . $_SESSION['att_id'] . $attached;
```

`$destination` 是上传文件夹，随后是一个正斜杠。`$_SESSION['att_id']` 是基于时间的前缀，`$attached` 是原始文件名。组合起来会得到类似 `C:/upload_test/att1273166609-bryce1.jpg` 的完整路径。

完整文件路径会传递给 `file_get_contents()`，这是一条核心 PHP 函数，适用于文本和二进制文件，能安全获取文件内容。

文件内容被存储在 `$contents` 中，然后传递给 `Zend_Mail` 对象的 `createAttachment()` 方法。该方法最多接受五个参数，但第一个参数（附件内容）是必需的。其余四个参数用于设置附件的 MIME 类型、 disposition、编码和文件名。如果不指定，`Zend_Mail` 会使用默认值，这在大多数情况下都很好。但使用默认文件名会导致收件人收到名为 `att1273166609-bryce1.jpg` 的附件，而不是原始文件名。

ZF 的面向对象方法的优势在于可以在构造函数之外独立设置属性。与一次性传递五个参数给 `createAttachment()` 相比，这里先将附件赋值给变量 `$att`，然后通过 `$att->filename = $attached;` 设置文件名。

`foreach` 循环的最后一行使用另一个核心 PHP 函数 `unlink()` 删除上传文件夹中的文件。

循环结束后，所有附件已附加到邮件对象，随后使用 `unset()` 释放 `$_SESSION['attachments']` 和 `$_SESSION['att_id']`，以便用户可以重新使用在线表单。

你可以将你的代码与 `process_attachments.php` 在 `lesson09/completed/scripts` 中进行比较。

#### 适配反馈表单

最后，需要调整反馈表单，使其在页面首次加载时显示附件字段，提交后若表单有错误则隐藏这些字段并显示附件提示信息。

**1.** 复制 `send_attachments.php` 从 `lesson09/start` 到你的 `workfiles` 文件夹。该文件与 `comments.php`（Lesson 8）相同，但在评论文本区和 reCAPTCHA 小部件之间增加了三个文件上传字段。

**2.** 在设计视图中，点击位于评论文本区旁边的 PHP 盾形图标（指示显示错误信息的服务器行为位置）右侧。打开分屏视图，确保光标位于 `</span>` 和 `</p>` 标签之间。在设计视图中保持焦点，按回车键插入一个新段落。

**3.** 在新段落中输入 **Attachments do not need to be uploaded again.** 你的页面应如下所示：

![Image](img/fig09_22.jpg)

**4** 如果表单包含错误提交，需要显示这段文字，并伴随 `get_attachments.php` 生成的任何消息。为了避免混淆，最好隐藏文件字段。将段落和文件字段包裹在条件语句中：

```php
<?php if (isset($_SESSION['att_id'])) { ?>
<p>Attachments do not need to be uploaded again.</p>
<?php } ?>
```

```php
<?php if (isset($messages)) { ?>
<ul>
```
