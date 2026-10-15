
与以前的外部脚本不同，process_comments.php 有关闭的 PHP 标签。这是因为 try 和 catch 块没有包裹在条件语句中。如果没有关闭标签，Dreamweaver 会将 PHP 代码视为 DOCTYPE 声明之上的文本，导致设计视图出现问题。

**3.** 将 comments.php 保存后，在“相关文件”工具栏中添加 process_comments.php。点击工具栏中的 process_comments.php 即可在分屏视图中进行编辑。

### ![Image](graphics/tip.jpg)**TIP:**

在分屏视图中编辑相关文件可以让网页在设计视图中保持可见，加快实时预览的测试速度。如果你更喜欢在单独标签页中编辑文件，Dreamweaver 会保持两个版本同步。分屏视图中看到的相关文件与单独标签页中的文件完全相同，不会出现混淆。选择最适合你的工作流程。

**4.** `Zend_Service_ReCaptcha` 对象负责显示 reCAPTCHA 小部件并验证答案，因此必须在只在表单已提交时才运行的条件语句之前实例化它。在 try 块的开头使用你自己的公钥和私钥添加下面高亮的代码：

try {  

**  $public\_key = 'Your\_reCAPTCHA\_public\_key';**    

**  $private\_key = 'Your\_reCAPTCHA\_private\_key';**    

**  $recaptcha = new `Zend_Service_ReCaptcha`($public_key, $private_key);**  

  if (isset($_POST['send'])) {

显示小部件的代码稍后会在 comments.php 中添加。

**5** 验证答案属于验证脚本。在“验证用户输入”注释之后新增一行，并在此行中插入代码：

// validate the user input  

**$result = $recaptcha->verify($_POST['recaptcha_challenge_field'], $_POST['recaptcha_response_field']);**  

if (!$result->isValid()) {  

  $errors['recaptcha'] = 'Try again';**  

}  

$val = new `Zend_Validate_Alnum` (TRUE);

原始挑战和用户的输入都通过 `$_POST` 数组传输。`verify()` 方法检查这两个值是否相同。

**6.** 保存 process_comments.php，然后切换到 comments.php 的源代码视图。

`Zend_Service_ReCaptcha` 为 reCAPTCHA 小部件生成全部 HTML 和 CSS，因此需要直接插入表单内部，且不要添加任何格式。comments.php 中的表单元素位于段落中，所以 reCAPTCHA 小部件的显示代码必须放在包含评论文本框的段落和提交按钮之间，如下图第 44 行所示：

![image](graphics/fig08_12.jpg)

尽管 `$recaptcha` 在另一页面定义，但 Dreamweaver 会因为 process_comments.php 是关联文件而为它生成代码提示。

**7.** 保存 comments.php，确保已连接 Internet，然后点击实时预览。你应该在页面 258（本课第一页）的截图中看到已添加到反馈表单的 reCAPTCHA 挑战。

**8.** 点击实时代码视图，检查页面上新加入的大量 HTML 和 JavaScript。`Zend_Service_ReCaptcha` 对象会在页面 `<head>` 中添加自己的 `<style>` 块。

reCAPTCHA 小部件大约在第 144 行，位于带有 `recaptcha_widget_div` ID 的 `<div>` 中。使用该 ID 在 CSS 中进行调整，以修改 `<div>` 周围的边距。`users_wider.css` 中的样式将小部件的边距与段落相同：

form p, `#recaptcha_widget_div` {  

  margin:0 0 10px 205px;  

}

**9** 保持所有字段空白，在实时预览中按住 Ctrl/Cmd 并点击“发送评论”。文档窗口顶部会出现“缺少响应字段”的提示，但输入框旁不会出现错误信息。

这是因为 `Zend_Service_ReCaptcha` 抛出了异常。当这种情况发生时，try 块被放弃，仅执行 catch 块。提示“缺少响应字段”是异常生成的信息。

**10** 为了防止在 reCAPTCHA 挑战为空时抛出异常，需要在 process_comments.php 中修改代码如下：

**if (empty($_POST['recaptcha_response_field'])) {**  

  $errors['recaptcha'] = 'reCAPTCHA field is required';    

} else {**  

  $result = $recaptcha->verify($_POST['recaptcha_challenge_field'], $_POST['recaptcha_response_field']);  

  if (!$result->isValid()) {  

    $errors['recaptcha'] = 'Try again';  

  }  

}

这里使用 `empty()` 检查 reCAPTCHA 字段。如果未填写，则向 `$errors` 数组添加提示信息。验证代码被包装在 `else` 块中，仅在字段非空时执行。

**11** 保存 process_comments.php，再次在不填写字段的情况下测试表单。脚本不再抛出异常，错误信息会显示在每个表单字段旁边。

**12** 为了显示 `$errors['recaptcha']` 消息，需要修改显示 reCAPTCHA 小部件的代码：

<?php **if (isset($errors['recaptcha'])) {**  

  echo "<p><span>{$errors['recaptcha']}</span></p>";  

}**  

echo $recaptcha->getHtml(); ?>

从技术上讲，`<span>` 是多余的，但这里加入它是为了让错误信息的样式与其他信息保持一致。字符串使用双引号包裹，以便显示 `$errors['recaptcha']` 的值，而数组元素需要用大括号包裹（参见“使用数组变量的引号”，[第 3 课](#ch03.html#ch03)）。

#### 通过电子邮件发送反馈

只有在验证没有错误时才发送电子邮件。因此，构建消息并发送邮件的代码应位于验证脚本末尾的条件语句内部。

**1.** 在 process_comments.php 中找到下面的条件语句（大约在第 30–32 行）：

if (!$errors) {  

// create and send the email  

}

所有邮件处理代码应放在这段花括号之间。

**2.** 包含邮件连接脚本，并创建 `Zend_Mail` 对象：

require_once('mail_connector.php');  

$mail = new `Zend_Mail`('UTF-8');

将 UTF-8 传递给 `Zend_Mail` 构造函数，确保重音或非字母字符正确显示。

**3.** 使用前文“使用 `Zend_Mail`”以及 [表 8.1](#ch08.html#ch08tab1) 中描述的方法设置收件人地址、`From` 头部和主题。使用你自己的电子邮件地址在 `addTo()` 和 `setFrom()` 方法中：

$mail->addTo('me@example.com', 'David Powers');  

$mail->setFrom('another@example.com', 'Zend Mail Test');  

$mail->setSubject('Comments from feedback form');

### ![Image](graphics/caution.jpg)**CAUTION!**

如果可能，为 addTo() 和 setFrom() 使用不同的电子邮件地址。两者都应是真实的电子邮件地址。setFrom() 使用与邮件连接器脚本中用户名和密码关联的电子邮件地址。使用不同的地址可能导致服务器在转发时拒绝邮件。`Zend_Mail` 在将消息交给服务器后并不知道其后续情况，因此你无法得知邮件最终是否送达。

**4.** 由于用户的电子邮件地址已被验证，你可以安全地使用它设置 `Reply-To` 头部：

$mail->setReplyTo($_POST['email'], $_POST['name']);
