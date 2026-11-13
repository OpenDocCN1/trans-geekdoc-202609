

<?
 $enc_passwd = "206bfaa5da7422d2f497239dcf8b96f3";
```

Now let's start by defining what to do when someone logs out (signified by a logout parameter). First, we set the session variable to incomplete, send the user to a generic page (here, index.php), and exit:

```
session_start();
if ($_REQUEST["logout"]) {
    $_SESSION["auth"] = "incomplete";
    header("Location: index.php");
    exit(0);
}
```

If the user is logging in, she'll do it through a pwd parameter. To see if the password is correct, we MD5-hash the parameter and compare the hash against the encrypted password. If everything checks out, we validate the session variable and send the user to a home page. You may not need to do this redirection depending on how your site sends form parameters. However, the danger is always that you may be trying to change something that requires a login, and then you log in, but as you are logging in, you lose the original parameters that you were trying to work with. It's safer to send new logins to some sort of home page.

```
if ($_REQUEST["pwd"]) {
    if (md5($_REQUEST["pwd"]) == $enc_passwd) {
        $_SESSION["auth"] = "completed";
        header("Location: index.php");
        exit(0);
    }
}
```

If we've gotten to this point, we know that we're not logging in or out, so all we have to do is check to see if the user is already logged in. Remember that this is in the $_SESSION["auth"] variable, so we check that. If the user is not logged in, we give the user the opportunity to log in by printing a login form, and then exit. You could also do this by redirecting the user to a special login page if you want to make it look better, but it's important that you always exit after redirecting or printing the form. Past this point you don't want to let PHP do anything that a logged-in user is able to do!

```
$authed = $_SESSION["auth"];
if ($authed != "completed") {
    ?><html><head></head><body>
    <form method="post">
    Enter password: <input type="password" name="pwd" />
    </form>
    </body></html><?php
    exit(0);
}
?>
```

To use this script, call it login.php and require it at the beginning of any script that should have authentication. When a client first encounters the page, the script prints a login form and exits before giving any other code a chance to run.

To set a new password for the script, run this script to generate the new password's hash, and then set the $enc_passwd string to the output:

```
<?php
print md5("newpassword");
?>
```

Remember that this is a very simple login system. You can augment it by adding the session timeout code from the preceding section, but if you find yourself asking for more features, you probably want to start from a fully tested login system. There are several free systems available on the Internet—they're definitely worth checking out.

## 9

## WORKING WITH EMAIL

![](img/19183d2b75bf6b509317c631c0e7b817_134_0.png)

You won't need to manipulate much email in PHP, but one thing that you will need to do is send confirmation messages to users and administrators about account settings, orders, and so on. The easiest way to send email in PHP is with the mail() function. If your mail server is set up correctly, and you need only to send messages to yourself, then this is probably the only function you'll ever need.

Here's a simple script to illustrate how mail() works. Replace user@example.com with a working email address:

```
if (mail('user@example.com', 'PHP email test', 'It worked!')) {
    echo "Mail sent.";
} else {
    echo "Mail delivery failed.";
}
```

If this script says *Mail sent.* when run, check the target email to verify that it actually did work. The subject should be *PHP email test* and the body should be *It worked!*

The `mail()` function, like any other system that sends email, is susceptible to problems in the mail-delivery system. You may need to fix your mail server's configuration to get things working. However, because there is so much junk in email now, a malformed or irregular mail header may cause a remote server to reject your email without telling you. In addition, when you send attachments or add HTML text, you have to do a lot more work. The next section shows you how overcome these problems with PHPMailer.

### 64: Using PHPMailer to Send Mail

PHPMailer is an open source email package that supports attachments, multiple recipients, SMTP authentication, and a large number of other features. It's well tested and relatively easy to use and upgrade. You need only include the core PHPMailer file as a part of your script, and you're ready to go.

### Installing PHPMailer

Just follow these steps to install PHPMailer:

- 1. Download the core PHPMailer files from http://phpmailer.sourceforge.net/.
- 2. Create a directory called *phpmailer* on your server to store the core PHPMailer files.
- 3. Extract the PHPMailer files into the phpmailer directory.
- 4. Determine your mail transport method. PHPMailer has three different methods to send email: `mail`, `sendmail`, and `smtp`. The default is `mail`, which uses the PHP `mail()` function discussed in the preceding section. It's the easiest to configure, assuming that your webserver's mail is configured correctly. If this method doesn't work, you have two remaining options:
  - a. You can provide PHPMailer with an SMTP server to talk to. SMTP stands for Simple Mail Transfer Protocol, the most common protocol for transporting email messages. To configure PHPMailer for SMTP, you need the SMTP server hostname. If the server requires SMTP authentication (as most do), you need a username and password for that server. Your ISP will be able to tell you the details about its SMTP server settings.
  - b. If your webserver uses `sendmail` or a package with a `sendmail`-compatible binary (such as Postfix) you can configure PHPMailer to use this to send mail. You need to know the `sendmail` binary location where the core `sendmail` executable resides. It's usually `/usr/sbin/sendmail` or `/usr/lib/sendmail`.
- 5. Adjust the PHPMailer default settings by editing the class.phpmailer.php file. You'll want to change the settings in the Public Variables section at the top of the file. The most important settings are as follows:
  - var $Mailer = "mail"; The method PHPMailer uses to send email. Set this to mail, sendmail, or smtp, as determined in step 4.
  - var $From = "root@localhost"; The default origin email address.
  - var $FromName = "Root User"; The default name associated with the default email address.
  - var $Host = ""; The SMTP server you want to use when using SMTP to connect. Check with your ISP for details. You can list multiple SMTP servers separated by semicolons (;) in case the first SMTP server is down or rejects the email.
  - var $SMTPAuth = false; If your SMTP server requires authentication to send emails, set this to true. If you set this, you must also set the following two variables.
  - var $Username = ""; When using SMTP authentication, the username on the SMTP server.
  - var $Password = ""; The password associated with $Username, if necessary.
  - var $Helo = ""; The name of your webserver, such as www.example.com.

After changing any necessary configuration variables, you're ready to see a simple script that sends a test message.

### Using the Script

Make sure the class.phpmailer.php file is in your include path, and try this script:

```
<?php
include_once("class.phpmailer.php");
$mail = new PHPMailer();
$mail->ClearAddresses();
$mail->AddAddress('theferrett@theferrett.com', 'The Ferrett');
$mail->From = 'you@example.com';
$mail->FromName = 'Your Name';
$mail->Subject = 'Test Message Subject';
$mail->Body = 'This is the test message body.';
if ($mail->Send()) {
    echo "Message sent.";
} else {
    echo $mail->ErrorInfo;
}
?>
```

PHPMailer has an object-oriented interface. You need to create an object ($mail in the preceding example) and then set some attributes and call some methods to set up the message. When you've finished, use the object's Send() method to send the message. This method returns true if PHPMailer was able to hand the message to its delivery agent. If there was a problem at this stage, you'll find the details in the ErrorInfo variable.

Here is an overview of the methods and attributes used in the example:

```
$mail->AddAddress(email_address, real_name)
```

Add a recipient for the current message. email_address is the address of the recipient, and real_name is the real name of the recipient (or, at least, what you'd rather call the recipient).

```
$mail->ClearAddresses()
```

This line clears the current recipient address list. Because the AddAddress() method doesn't remove previous addresses, you run the risk of sending a message to someone many times if you send messages in a loop using a single PHPMailer object. Therefore, you should get into the habit of clearing the recipient list before you do anything with a message or after you call the Send() method.

```
$mail->isHTML = true|false
```

If this attribute is set to true, PHPMailer uses HTML instead of plaintext. You can embed pretty pictures with HTML, but not all mail clients want to support HTML. See the following attribute if this is a problem.

```
$mail->AltBody = text
```

If you set the isHTML attribute to true, you can set the AltBody attribute to a text-only equivalent of the message body.

### Adding Attachments

If you want to attach files to messages, use this method:

```
$mail->AddAttachment(path, name, encoding, type)
```

The parameters are as follows:

| Parameter | Description |
|-----------|-------------|
| path | The full pathname of the file that you want to attach. |
| name | The new name for the attached file. For example, if the file is called 011100.jpg on your system, but you want it to be called product_sample.jpg, set this parameter to product_sample.jpg. This parameter is |

