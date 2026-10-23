# 30. PHPMailer

PHPMailer is a email creation and transport class for PHP, supporting SMTP and other email delivery methods.

# Ex:PHPMailer

```
```php
// Install PHPMailer via Composer
composer require phpmailer/phpmailer

// Example PHP code to send an email using PHPMailer
require 'vendor/autoload.php';
$mail = new PHPMailer\PHPMailer\PHPMailer();
$mail->isSMTP();
$mail->Host = 'smtp.example.com';
$mail->SMTPAuth = true;
$mail->Username = 'your_email@example.com';
$mail->Password = 'your_password';
$mail->SMTPSecure = 'tls';
$mail->Port = 587;
$mail->setFrom('from@example.com', 'Mailer');
$mail->addAddress('recipient@example.com', 'Recipient Name');
$mail->Subject = 'Here is the subject';
$mail->Body = 'This is the HTML message body **in bold!**';
$mail->AltBody = 'This is the body in plain text for non-HTML mail clients';
if(!$mail->send()) {
    echo 'Message could not be sent.';
    echo 'Mailer Error: ' . $mail->ErrorInfo;
}
```
```