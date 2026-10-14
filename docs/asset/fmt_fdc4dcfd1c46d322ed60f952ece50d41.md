
在查看 PHP 的 `mail()` 函数——`mail(to, subject, body[, headers])`——时，你可以看到其中一个参数直接进入邮件正文，其余参数则出现在邮件头中。要向*你的地址*发送垃圾邮件（如第 11 章示例所示），用户只需在表单的评论部分输入垃圾邮件内容。这已经够糟糕了，但要同时向*其他人*发送垃圾邮件，用户只需在邮件头中添加 `Bcc: poorsap@example.org`，并跟上某种行终止符（如换行符或回车符）。按示例原样操作，这仅意味着在联系表单的 *from* 值中输入：`me@example.com\nBcc:poorsap@example.org`。

你可能认为保护所有进入邮件头的内容就足够安全了，但由于邮件只是一个文档，正文中的恶意输入也会影响邮件头。

可以针对该联系表单采取几种预防技术。首先，使用正则表达式验证邮箱地址，相关内容见第 13 章“Perl 兼容正则表达式”，或稍后讨论的 Filter 扩展。其次，既然你知道作恶者必须输入什么才能发送垃圾邮件（表 13.1），就在表单值中监视那些字符和字符串。如果某值包含列表中的任何内容，请勿在发送的邮件中使用该值（表 13.1 中最后四个值都是创建换行的不同方式）。

### 表 13.1. 垃圾邮件线索

在下一个示例中（基于第 11 章的邮件脚本修改），我将定义一个函数，清除所提供数据中所有潜在危险字符。同时将用到两个新的 PHP 函数：`str_replace()` 和 `array_map()`。两者将在后续步骤中详细解释。

---

### 安全方法

理解安全最重要的概念是：它不是二元状态。不要认为网站或脚本要么*安全*要么*不安全*。安全不是你开关的开关；它是一个你可以上下移动的刻度。编程时，要思考如何让网站*更安全*，以及你做了什么让它*降低安全性*。同时请记住，提高安全性通常以便利性（对你这位程序员和最终用户皆是如此）和性能为代价。增强安全性通常意味着更多代码、更多检查和更多服务器资源。开发 Web 应用时，目标是达到针对特定情况适当的安全级别。然后，为了谨慎起见，最好在安全方面稍微“过度”一点。

---

### 防止垃圾邮件

**1.** 在文本编辑器或 IDE 中打开 `email.php`（脚本 11.1）。

为完成垃圾邮件净化，需修改邮件脚本。

**2.** 检查表单提交后，开始定义函数（脚本 13.1）：

```php
function spam_scrubber($value) {
```

该函数接受一个参数：字符串。通常我会在脚本顶部或单独文件中定义函数，但为简化操作，将在提交处理代码块内定义。

**3.** 创建一个列表，包含合法联系表单提交中不应出现的极其恶劣内容：

```php
$very_bad = array('to:', 'cc:', 'bcc:', 'content-type:', 'mime-version:', 'multipart-mixed:', 'content-transfer-encoding:');
```

诚实的联系表单提交中不应出现这些字符串（用户在评论中合法使用 `to:` 的可能性虽存但极低）。若存在此类字符串，即为垃圾邮件尝试。为便于检测，将它们放入数组以便循环遍历（步骤 4）。步骤 4 中的比较不区分大小写，因此所有危险字符串均以小写形式编写。

**4.** 循环遍历数组。若发现极其恶劣内容，返回空字符串：

```php
foreach ($very_bad as $v) {
    if (stripos($value, $v) !== false) return '';
}
```

脚本 13.1. 此版本脚本现可安全发送邮件，无需担心垃圾邮件。任何有问题的字符都会被 `spam_scrubber()` 函数捕获。

```html
1   <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML
2       1.0 Transitional//EN" "http://www.w3.org/
3       TR/xhtml1/DTD/xhtml1-transitional.dtd">
4   <html xmlns="http://www.w3.org/1999/
5       xhtml" xml:lang="en" lang="en">
6   <head>
7       <meta http-equiv="Content-Type"
8           content="text/html; charset=utf-8" />
9       <title>Contact Me</title>
10  </head>
11  <body>
12  <h1>Contact Me</h1>
13  <?php # Script 13.1 - email.php #2
14  // This version now scrubs dangerous
15      strings from the submitted input.
16
17  // Check for form submission:
18  if ($_SERVER['REQUEST_METHOD'] == 'POST') {
19
20      /* The function takes one argument: a
21          string.
22       * The function returns a clean
23          version of the string.
24       * The clean version may be either an
25          empty string or
26       * just the removal of all newline
27          characters.
28       */
29      function spam_scrubber($value) {
30
31          // List of very bad values:
32          $very_bad = array('to:',
33              'cc:', 'bcc:', 'content-type:',
34              'mime-version:', 'multipart-mixed:',
35              'content-transfer-encoding:');
36
37          // If any of the very bad strings
38          are in
39          // the submitted value, return an
40          empty string:
41          foreach ($very_bad as $v) {
42              if (stripos($value, $v) !==
43                  false) return '';
44          }
45
46          // Replace any newline characters
47          with spaces:
48          $value = str_replace(array("\r",
49              "\n", "%0a", "%0d"), ' ', $value);
50
51          // Return the value:
52          return trim($value);
53
54      } // End of spam_scrubber()
55          function.
56
57      // Clean the form data:
58      $scrubbed = array_map
59          ('spam_scrubber', $_POST);
60
61      // Minimal form validation:
62      if (!empty($scrubbed['name']) &&
63          !empty($scrubbed['email']) &&
64          !empty($scrubbed['comments']) ) {
65
66          // Create the body:
67          $body = "Name: {$scrubbed
68              ['name']}\n\nComments:
69              {$scrubbed['comments']}";
70
71          // Make it no longer than 70
72          characters long:
73          $body = wordwrap($body, 70);
74
75          // Send the email:
76          mail('your_email@example.com',
77              'Contact Form Submission', $body,
78              "From: {$scrubbed['email']}");
79
80          // Print a message:
81          echo '<p><em>Thank you for
82              contacting me. I will reply some
83              day.</em></p>';
84
85          // Clear $_POST (so that the form's
86              not sticky):
87          $_POST = array();
88
89      } else {
90          echo '<p style="font-weight: bold;
91              color: #C00">Please fill out the
92              form completely.</p>';
93      }
94
95  } // End of main isset() IF.
96
97  // Create the HTML form:
98  ?>
99  <p>Please fill out this form to contact me.</p>
100 <form action="email.php" method="post">
101     <p>Name: <input type="text" name="name" size="30" maxlength="60" value="<?php if
102         (isset($scrubbed['name'])) echo $scrubbed['name']; ?>" /></p>
103     <p>Email Address: <input type="text" name="email" size="30" maxlength="80"
```

```php
value="<?php if (isset($scrubbed['email'])) echo $scrubbed['email']; ?>" /></p>

72      <p>Comments: <textarea name="comments" rows="5" cols="30"><?php if
      (isset($scrubbed['comments'])) echo $scrubbed['comments']; ?></textarea></p>

73      <p><input type="submit" name="submit" value="Send!" /></p>

74  </form>

75  </body>

76  </html>
```

`foreach` 循环将逐个访问 `$very_bad` 数组中的每一项，并将每一项赋值给 `$v`。在循环内部，`stripos()` 函数将检查该项是否存在于作为 `$value` 提供给该函数的字符串中。`stripos()` 函数执行不区分大小写的搜索（因此它会匹配 `bcc:`、`Bcc:`、`bCC:` 等）。如果在 haystack 中找到 needle（例如，在 `$value` 中查找 `$v` 的出现），该函数返回布尔值 `TRUE`。因此，条件语句表示如果该函数的结果不等于 `FALSE`（即在 `$value` 中未找到 `$v`），则返回空字符串。

因此，对于每一个危险字符串，首次在提交的值中发现它们中的任何一个时，该函数将返回空字符串并终止（函数一旦遇到 `return` 就会自动停止执行）。

**5. 将任何换行符替换为空格：**

```php
$value = str_replace(array("\r", "\n", "%0a", "%0d"), ' ', $value);
```

换行符由 `\r`、`\n`、`%0a` 和 `%0d` 表示，可能会也可能不会造成问题。发送垃圾邮件需要换行符（否则无法创建正确的标头），但如果用户在 textarea 框中输入时按下 Enter 或 Return 键，也会出现换行符。因此，任何找到的换行符都将被替换为空格。这意味着提交的值可能会丢失部分格式，但为了阻止垃圾邮件，这是合理的代价。

`str_replace()` 函数遍历第三个参数中的值，并将第一个参数中的字符出现替换为第二个参数中的字符。正如 PHP 手册所述：

```
mixed str_replace (mixed $search, mixed $replace, mixed $subject)
```

此函数非常灵活，因为它可以接受字符串或数组作为其三个参数（`mixed` 意味着它接受混合的参数类型）。因此，脚本中的这行代码将 `$value` 变量赋值为其原始值，并将任何换行符替换为单个空格。

此函数有一个不区分大小写的版本，但这里不需要，因为例如 `\r` 是回车符，但 `\R` 不是。

**6. 返回值并完成函数：**

```php
return trim($value);

} // End of spam_scrubber() function.
```

最后，该函数返回去除首尾空格后的值。请记住，只有在未发现任何非常危险的内容时，函数才会执行到这一点。

**7. 在函数定义后，调用 `spam_scrubber()` 函数：**

```php
$scrubbed = array_map('spam_scrubber', $_POST);
```

这种方法简洁而优美！`array_map()` 函数有两个必需参数。第一个是要调用的函数名。在本例中，是 `spam_scrubber`（不带括号，因为你提供的是函数的*名称*，而不是调用该函数）。第二个参数是一个数组。

`array_map()` 会将指定的函数应用于数组的每个元素，将每个元素的值发送给该函数调用。在本脚本中，`$_POST` 有四个元素——`name`、`email`、`comments` 和 `submit`，这意味着得益于 `array_map()`，`spam_scrubber()` 函数将被调用四次。执行这行代码后，`$scrubbed` 数组将包含四个元素：`$scrubbed['name']` 将包含 `$_POST['name']` 经 `spam_scrubber()` 处理后的值；`$scrubbed['email']` 将包含 `$_POST['email']` 经 `spam_scrubber()` 处理后的值；以此类推。

这一行代码获取整个潜在受污染的数据数组（`$_POST`），使用 `spam_scrubber()` 进行清理，并将结果赋值给新变量。该技术最重要的一点是：从现在开始，脚本必须使用干净的 `$scrubbed` 数组，而不是仍可能脏的 `$_POST`。

**8. 更改表单验证以使用这个新数组：**

```php
if (!empty($scrubbed['name']) && !empty($scrubbed['email']) && !empty($scrubbed['comments'])) {
```

这些元素中的每一个都可能有两个原因导致值为空。第一，用户将它们留空。第二，用户在字段中输入了其中一个坏字符串，这会被 `spam_scrubber()` 函数转换为空字符串。

电子邮件地址字段中存在 `cc:` 将阻止此提交通过电子邮件发送。

由于电子邮件地址中使用了非常危险的字符，被垃圾邮件防止函数转换为空字符串，因此邮件未发送。

**9. 更改 `$body` 变量的创建以使用干净的值：**

```php
$body = "Name: {$scrubbed['name']}\n\nComments: {$scrubbed['comments']}";
```

**10. 更改 `mail()` 函数的调用以使用干净的电子邮件地址：**

```php
mail('your_email@example.com', 'Contact Form Submission', $body, "From: {$scrubbed['email']}");
```

请记得在 `mail()` 调用中使用您自己的电子邮件地址，否则您永远收不到消息！

**11. 更改表单以使用 `$scrubbed` 版本的值：**

```html
```
