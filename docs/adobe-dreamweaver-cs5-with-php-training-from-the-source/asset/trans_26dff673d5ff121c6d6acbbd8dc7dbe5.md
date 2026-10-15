
表达当前日期和时间为过去约40年中的秒数可能看起来很奇怪。尽管时间戳对人类来说难以理解，但 PHP 函数使用它们来快速简便地进行日期计算，避免了不同长度月份和闰年带来的复杂性。1970 年 1 月 1 日被称为 Unix 纪元，这种日期和时间的表示方式通常被称为 Unix 时间戳。

`$_SESSION[‘attachments’]` 也初始化为一个空数组。

**5.** 在你刚刚创建的条件语句内部，实例化一个文件传输对象并设置上传目标和验证类：

``` 
$uploader = new Zend\_File\_Transfer\_Adapter\_Http();  
$uploader->setDestination($destination);  
$uploader->setOptions(array('ignoreNoFile' => TRUE));  
$uploader->addValidator('Size', FALSE, $max\_size);  
$uploader->addValidator('ExcludeExtension', FALSE, $not\_allowed);
``` 

这与主上传脚本中的代码基本相同。它使用 `ExcludeExtension` 而不是 `MimeType` 验证类。

**6.** 剩余的代码也在条件语句内部，代码如下（高亮行在下面代码列表中解释）：

``` 
$files = $uploader->getFileInfo();  
foreach($files as $file => $info) {  
  if ($uploader->isUploaded($file)) {  
    $filename = $uploader->getFileName($file, FALSE);  
    if (!$uploader->isValid($file)) {  
      $messages\[\] = "$filename exceeds $max\_size or is not an acceptable type";  
    } else {  
      $attachment = $_SESSION['att_id'] . str_replace(' ', '_', $filename);  
      $uploader->addFilter('Rename', array('target' => $attachment), $file);  
      $success = $uploader->receive($file);  
      if (!$success) {  
        $messages\[\] = "$filename could not be attached";  
      } else {  
        $messages\[\] = "$filename attached";  
      }  
    }  
  }  
}
``` 

这与你之前构建的文件上传脚本遵循类似的模式，只是更短更简单。如果文件验证失败，会使用 `$filename` 和 `$max_size` 创建一条消息。

在主 `else` 块内部，会在第一次加载页面时显示文件字段，提交后若表单有错误则隐藏这些字段并显示附件提示信息。

在主 `else` 块中，会移除文件名中的空格并添加前缀，生成类似 `att1273166609-bryce1.jpg` 的文件名。修改后的文件名存储在 `$attachment` 中，而原始文件名保留在 `$filename` 中。

`Rename` 过滤器使用 `$attachment`（例如 `att1273166609-bryce1.jpg`），而 `$_SESSION[‘attachments’]` 使用 `$filename` 以保留原始文件名，以便在电子邮件中使用。

你可以将你的代码与 `get_attachments.php` 在 lesson09/completed/scripts 中进行比较。

#### 适配邮件处理脚本

对 Lesson 8 中的邮件处理脚本进行以下修改：

**1.** 复制 `lesson09/start/scripts/process_attachments.php`，保存到本课程的 `workfiles/scripts` 文件夹中。或者，你可以使用上一课的 `process_comments.php`。

**2.** 在 `process_attachments.php` 中，使用 `require_once()` 包含 `get_attachments.php`。代码应放在最后的验证语句和检查错误的条件语句之间（大约第 30 行）：

``` 
if (!$val->isValid($_POST['comments'])) {  
$errors['comments'] = 'Required';  
}  

require_once('get_attachments.php');  

if (!$errors) {
```

这确保即使表单出错，附件也会被保存。

**3** 将附件附加代码放在发送邮件之前（大约第 48 行）。完整代码块如下：

``` 
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

这段代码被包装在判断 `$_SESSION[‘attachments’]` 是否存在且不为空的条件语句中，确保只有在有附件需要发送时才执行。

在条件语句内部，`foreach` 循环会处理 `$_SESSION[‘attachments’]` 中存储的文件名，将每个文件名赋值给临时变量 `$attached`。每次循环中，`$attached` 保存当前文件的原始文件名。要从上传文件夹获取文件内容，需要使用完整路径，包括用于存储文件的前缀。具体做法如下：

``` 
$current_file = $destination . '/' . $_SESSION['att_id'] . $attached;
``` 

`$destination` 是上传文件夹，随后是一个正斜杠。`$_SESSION[‘att_id’]` 是基于时间的前缀，`$attached` 是原始文件名。组合起来会得到类似 `C:/upload_test/att1273166609-bryce1.jpg` 的完整路径。

完整文件路径会传递给 `file_get_contents()`，这是一条核心 PHP 函数，适用于文本和二进制文件，能安全获取文件内容。

文件内容被存储在 `$contents` 中，然后传递给 `Zend_Mail` 对象的 `createAttachment()` 方法。该方法最多接受五个参数，但第一个参数（附件内容）是必需的。其余四个参数用于设置附件的 MIME 类型、 disposition、编码和文件名。如果不指定，`Zend_Mail` 会使用默认值，这在大多数情况下都很好。但使用默认文件名会导致收件人收到名为 `att1273166609-bryce1.jpg` 的附件，而不是原始文件名。

ZF 的面向对象方法的优势在于可以在构造函数之外独立设置属性。与一次性传递五个参数给 `createAttachment()` 相比，这里先将附件赋值给变量 `$att`，然后通过 `$att->filename = $attached;` 设置文件名。

`foreach` 循环的最后一行使用另一个核心 PHP 函数 `unlink()` 删除上传文件夹中的文件。

循环结束后，所有附件已附加到邮件对象，随后使用 `unset()` 释放 `$_SESSION[‘attachments’]` 和 `$_SESSION['att_id']`，以便用户可以重新使用在线表单。

你可以将你的代码与 `process_attachments.php` 在 lesson09/completed/scripts 中进行比较。

#### 适配反馈表单

最后，需要调整反馈表单，使其在页面首次加载时显示附件字段，提交后若表单有错误则隐藏这些字段并显示附件提示信息。

**1.** 复制 `send_attachments.php` 从 lesson09/start 到你的 workfiles 文件夹。该文件与 `comments.php`（Lesson 8）相同，但在评论文本区和 reCAPTCHA 小部件之间增加了三个文件上传字段。

**2.** 在设计视图中，点击位于评论文本区旁边的 PHP 盾形图标（指示显示错误信息的服务器行为位置）右侧。打开分屏视图，确保光标位于 `</span>` 和 `</p>` 标签之间。在设计视图中保持焦点，按回车键插入一个新段落。

**3.** 在新段落中输入 **Attachments do not need to be uploaded again.** 你的页面应如下所示：

![Image](graphics/fig09_22.jpg)
