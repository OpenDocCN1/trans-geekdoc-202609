

## 第4步：发送消息

```php
// 1. Set the SMTP headers
$headers = array();
$headers['From'] = 'sample.user@example.com';
$headers['To'] = 'john.doe@example.com, jane.doe@example.com';
$headers['Cc'] = 'fsmith@example.org';
$headers['Bcc'] = 'jsmith@example.net';
$headers['Subject'] = 'How to use PEAR Mail';

// 2. Set the recipient list
$recipients = 'john.doe@example.com, jane.doe@example.com, ';
$recipients .= 'fsmith@example.org, jsmith@example.net';

// 3. Set the text for the body of the message
$body = "The Murach PHP and MySQL book has a chapter on\n";
$body .= "how to use the PEAR Mail package to send email.";

// 4. Send the message
$result = $mailer->send($recipients, $headers, $body);

// 5. Check the result and display an error if one exists
if (PEAR::isError($result)) {
    $error = 'Error sending email: ' . $result->getMessage();
    echo htmlspecialchars($error);
}
```

## 如何在消息正文中使用 HTML 格式

```php
// 1. Set the Content-type header
$headers['Content-type'] = 'text/html';

// 2. Use HTML tags to format the body of the message.
$body = '<p>The Murach PHP and MySQL book has a chapter on how to use
        the <a href="http://pear.php.net/Mail/">PEAR Mail package</a>
        to send email.</p>';
```

## 说明

- mailer 对象的 send 方法发送电子邮件。它接受三个参数：(1) 以逗号分隔的收件人列表，(2) 标头数组，(3) 消息正文文本。如果此方法遇到错误，它将返回 PEAR_Error 对象。
- PEAR 类的静态 isError 方法检查指定对象是否为 PEAR_Error 对象。如果是，则可以使用该对象的 getMessage 方法获取错误消息。
- 默认情况下，消息正文文本必须是纯文本，且不能包含附件。但是，如果将 Content-type 标头设置为“text/html”，则可以使用 HTML 标签来格式化文本。
- 若要创建包含内联图像和附件的电子邮件，可以使用 PEAR Mail_Mime 包。有关该包的更多信息，可访问此 URL：
  http://pear.php.net/package/Mail_Mime/

图22-3    如何使用 PEAR Mail 包发送电子邮件（第2部分，共2部分）

## 用于发送电子邮件的辅助函数

图22-4展示了名为 send_email 的辅助函数的代码，你可以使用它来更轻松地创建和发送电子邮件。此函数验证传递给它的电子邮件地址，连接到 SMTP 服务器，并发送电子邮件。

此文件中的代码首先加载两个文件。第一个文件（Mail.php）是 PEAR Mail 包。第二个文件（RFC822.php）是另一个 PHP 文件。它提供了一个名为 parseAddressList 的方法，用于验证电子邮件地址列表，其中每个电子邮件地址可能采用以下格式：

```text
Full Name <username@example.com>
```

该方法由本图第2部分中的 valid_email 函数使用。

send_email 函数接受五个参数。其中，前四个参数是必需的：From 地址、To 地址、主题行和电子邮件正文。但是，第五个参数是可选的。该参数指定电子邮件的正文是否使用 HTML 标签进行格式化。默认情况下，此参数设置为 FALSE，因此消息正文不会使用 HTML 标签进行格式化。

该函数首先检查 From 地址和 To 地址是否有效。为此，它使用第2部分中的 valid_email 函数。如果某个电子邮件地址无效，此代码将抛出一个包含相应错误消息的 Exception 对象。

验证电子邮件地址后，此函数设置 SMTP 服务器的参数。使用此代码时，需要修改 $smtp 数组元素，以匹配你自己的 SMTP 服务器的值。如果不更改这些值，代码将无法正常工作。

设置参数后，将使用 Mail::factory 方法创建 mailer 对象。然后，使用 PEAR::isError 方法检查此方法是否返回 PEAR_Error 对象。如果是，此代码将抛出一个异常，指示代码无法创建 mailer 对象。

创建 mailer 对象后，此代码创建一个名为 $recipients 的数组。此数组存储电子邮件所有收件人的地址。对于此函数，此数组仅包含一个收件人，即 To 地址。不过，如有必要，你可以创建此函数的增强版本，以支持多个 To、Cc 或 Bcc 地址。

创建收件人列表后，此代码设置 HTTP 标头。在这里，代码检查 $is_body_html 参数，以确定是否设置 Content-type 标头。如果此参数设置为 TRUE，此代码会将 Content-type 标头设置为“text/html”。这表示正文使用 HTML 标签进行格式化。否则，此代码会将 Content-type 标头保留为默认值“text/plain”。

设置标头后，此代码通过调用 mailer 对象的 send 方法发送电子邮件。为此，此代码将收件人数组、标头数组和消息正文传递给 send 方法，并将返回值存储在名为 $result 的变量中。然后，如果 $result 变量是一个错误，此代码将抛出一个异常。如果不是，则不执行任何操作，因为没有错误表示电子邮件已成功发送。

## message.php 文件

```php
<?php
require_once 'Mail.php';
require_once 'Mail/RFC822.php';

function send_email($to, $from, $subject, $body, $is_body_html = false) {
    if (! valid_email($to)) {
        throw new Exception('This To address is invalid: ' .
            htmlspecialchars($to));
    }
    if (! valid_email($from)) {
        throw new Exception('This From address is invalid: ' .
            htmlspecialchars($from));
    }

    $smtp = array();
    // **** You must change the following to match your
    // **** SMTP server and account information.
    $smtp['host'] = 'ssl://smtp.gmail.com';
    $smtp['port'] = 465;
    $smtp['auth'] = true;
    $smtp['username'] = 'example@gmail.com';
    $smtp['password'] = 'supersecret';

    $mailer = Mail::factory('smtp', $smtp);
    if (PEAR::isError($mailer)) {
        throw new Exception('Could not create mailer.');
    }

    // Add the email address to the list of all recipients
    $recipients = array();
    $recipients[] = $to;

    // Set the headers
    $headers = array();
    $headers['From'] = $from;
    $headers['To'] = $to;
    $headers['Subject'] = $subject;
    if ($is_body_html) {
        $headers['Content-type'] = 'text/html';
    }

    // Send the email
    $result = $mailer->send($recipients, $headers, $body);

    // Check the result and throw an error if one exists
    if (PEAR::isError($result)) {
        throw new Exception('Error sending email: ' .
            htmlspecialchars($result->getMessage()) );
    }
}
```

第2部分中的 valid_email 函数使用由 PEAR Mail 包提供的 parseAddressList 方法来解析以下形式的电子邮件地址：

```text
Full Name <username@example.com>
```

此方法接受一个地址或地址列表，并返回一个电子邮件对象数组，每个地址对应一个对象。

如果 parseAddressList 方法返回 PEAR_Error 对象，则 valid_email 函数返回 FALSE。否则，从第一个电子邮件地址对象中复制电子邮件地址部分，并存储在 $email 变量中。然后，此代码使用 filter_var 函数检查存储在该变量中的电子邮件地址是否有效。如果无效，此代码返回 FALSE。否则，返回 TRUE。如果 filter_var 函数无法让你对验证过程进行足够的控制，你可以按照第15章的描述，使用正则表达式来验证电子邮件地址。

## message.php 文件

```php
function valid_email($email) {
    $emailobjects = Mail_RFC822::parseAddressList($email);
    if (PEAR::isError($emailobjects)) { return false; }

    $emailobject = $emailobjects[0];
    $email = $emailobject->mailbox . '@' . $emailobject->host;

    if (filter_var($email, FILTER_VALIDATE_EMAIL) === false) {
        return false;
    } else {
        return true;
    }
}
?>
```

图22-4    用于发送电子邮件的辅助函数（第2部分，共2部分）

