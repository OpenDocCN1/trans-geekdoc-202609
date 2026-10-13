
# PHP `mail()` 函数与垃圾邮件防范

在查看 PHP 的 `mail()` 函数——`mail(to, subject, body[, headers])`——时，你可以看到其中一个参数直接进入邮件正文，其余参数则出现在邮件头中。要向*你的地址*发送垃圾邮件（如[第 11 章](#ch11.html#ch11)示例所示），用户只需在表单的评论部分输入垃圾邮件内容 ![Image](graphics/graycircle-a.jpg)。这已经够糟糕了，但要同时向*其他人*发送垃圾邮件，用户只需在邮件头中添加 `Bcc: poorsap@example.org`，并跟上某种行终止符（如换行符或回车符）。按示例原样操作，这仅意味着在联系表单的 *from* 值中输入：`me@example.com\nBcc:poorsap@example.org`。

你可能认为保护所有进入邮件头的内容就足够安全了，但由于邮件只是一个文档，正文中的恶意输入也会影响邮件头。

可以针对该联系表单采取几种预防技术。首先，使用正则表达式验证邮箱地址，相关内容见[第 13 章](#ch13.html#ch13)“Perl 兼容正则表达式”，或稍后讨论的 Filter 扩展。其次，既然你知道作恶者必须输入什么才能发送垃圾邮件（**[表 13.1](#ch13.html#ch13table01)**），就在表单值中监视那些字符和字符串。如果某值包含列表中的任何内容，请勿在发送的邮件中使用该值（**表 13.1** 中最后四个值都是创建换行的不同方式）。

**表 13.1. 垃圾邮件线索**

![Image](graphics/13tab01.jpg)

在下一个示例中（基于[第 11 章](#ch11.html#ch11)的邮件脚本修改），我将定义一个函数，清除所提供数据中所有潜在危险字符。同时将用到两个新的 PHP 函数：`str_replace()` 和 `array_map()`。两者将在后续步骤中详细解释。

---

## 安全方法

理解安全最重要的概念是：它不是二元状态。不要认为网站或脚本要么*安全*要么*不安全*。安全不是你开关的开关；它是一个你可以上下移动的刻度。编程时，要思考如何让网站*更安全*，以及你做了什么让它*降低安全性*。同时请记住，提高安全性通常以便利性（对你这位程序员和最终用户皆是如此）和性能为代价。增强安全性通常意味着更多代码、更多检查和更多服务器资源。开发 Web 应用时，目标是达到针对特定情况适当的安全级别。然后，为了谨慎起见，最好在安全方面稍微“过度”一点。

---

## 防止垃圾邮件

**1.** 在文本编辑器或 IDE 中打开 `email.php`（**[脚本 11.1](#ch11.html#ch11ex01)**）。

为完成垃圾邮件净化，需修改邮件脚本。

**2.** 检查表单提交后，开始定义函数（**[脚本 13.1](#ch13.html#ch13ex01)**）：

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

**脚本 13.1.** 此版本脚本现可安全发送邮件，无需担心垃圾邮件。任何有问题的字符都会被 `spam_scrubber()` 函数捕获。

---

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
