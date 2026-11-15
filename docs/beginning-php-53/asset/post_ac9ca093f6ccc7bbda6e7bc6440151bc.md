

| Variable | Description |
| :--- | :--- |
| `$_SERVER["DOCUMENT_ROOT"]` | The absolute path to the document root folder of the Web site (for example: /home/matt/mysite/htdocs) |
| `$_SERVER["HTTP_REFERER"]` | The referring URL, as sent by the browser in the Referer HTTP header. (See the “Working with HTTP” section in this chapter for more details) |
| `$_SERVER["HTTP_USER_AGENT"]` | The visitor’s browser information, such as name and version. (A nicer way to access this information is to use the PEAR Net_UserAgent_Detect package, as described in Chapter 15) |
| `$_SERVER["HTTPS"]` | true if the script was accessed via HTTPS; false if accessed via HTTP |
| `$_SERVER["PATH_INFO"]` | Any extra info appended onto the URL. For example, if the script is accessed via the URL http://www.example.com/myscript.php/extra/info) then $_SERVER["PATH_INFO"] contains /extra/info. (Not supported on all servers) |
| `$_SERVER["PHP_SELF"]` | The URL of the currently running script, relative to the Web site’s document root. For example: /about/index.php |
| `$_SERVER["QUERY_STRING"]` | The query string in the URL of the request, if present (this is the string that appears after the ‘?’ in the URL) |
| `$_SERVER["REMOTE_ADDR"]` | The IP address of the visitor’s computer (or proxy server if the visitor is using one) |
| `$_SERVER["REMOTE_HOST"]` | The hostname of the visitor’s computer (or proxy server if the visitor is using one). Because this involves making a DNS lookup it can have a performance hit on the server, so many Web server applications disable this option by default. However, you can use gethostbyaddr() to manually retrieve the hostname from the IP address as follows: echo gethostbyaddr( $_SERVER["REMOTE_ADDR"] ) |
| `$_SERVER["REQUEST_METHOD"]` | The request method used to access the script (such as GET, POST, or HEAD) |
| `$_SERVER["REQUEST_URI"]` | The full URL of the currently running script, relative to the Web site’s document root, and including any query string (for example: /about/index.php?page=3) |
| `$_SERVER["SCRIPT_FILENAME"]` | The absolute path to the running script (for example: /home/matt/mysite/htdocs/myscript.php) |
| `$_SERVER["SCRIPT_NAME"]` | The URL of the currently running script, relative to the Web site’s document root. For example: /about/index.php. Note that this is subtly different to $_SERVER['PHP_SELF']. Whereas $_SERVER["PHP_SELF"] includes any extra path information (as stored in $_SERVER ["PATH_INFO"]), $_SERVER["SCRIPT_NAME"] discards such information |

As with all external input, it’s unwise to trust the contents of $_SERVER variables. Most of them can be manipulated by your visitors in one way or another. Make sure you check, filter, or encode the values as appropriate.

The following simple script outputs all of the values in the $_SERVER superglobal array:

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
<title>Server and script details</title>
<link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>
<h1>Server and script details</h1>
<pre>
<?php print_r( $_SERVER ); ?>
</pre>
</body>
</html>
```

Figure 16-3 shows the output of the script running on a typical Apache Web server.

![](img/1ddec54918a4802eb9b4febec3d4e7f6_534_0.png)

Figure 16-3

## Sending Email

Many Web applications have a need to send email messages. For example, a contact form script typically processes a form submitted by a visitor and emails the form information to the Webmaster. Other common scenarios include “tell a friend” functions, as well as member registration and “forgotten password” functions that email information to members.

PHP includes built-in support for creating and sending email messages, which makes it very easy to send email from within your PHP scripts.

To send an email message in PHP, you use the mail() function. On Unix servers such as Linux and Mac OS X, PHP uses the operating system’s built-in mail transfer agent (MTA) to send the email. (Common MTAs include sendmail, postfix, and exim.) On non-Unix servers such as Windows, PHP talks directly to an SMTP mail server (either on the server or on another machine).

## Part III: Using PHP in Practice

At a minimum, mail() requires three arguments:

- A string containing the recipient’s email address (or a comma-separated list of email addresses if sending to multiple recipients)
- The email subject line, as a string
- The message body, as a string

mail() returns true if the mail was accepted for delivery by the mail server, or false if there was a problem. (Note that an email message might still eventually bounce, even if the mail server accepted it for delivery.)

For example, the following code sends a short email entitled “Hello”, with a message body of “Hi Jim, how are you?”, to jim@example.com:

```
mail( "jim@example.com", "Hello", "Hi Jim, how are you?" );
```

You can also include the recipient’s real name in the recipient string, provided you follow it with the recipient’s email address in angle brackets. For example:

```
mail( "Jim Smith <jim@example.com>", "Hello", "Hi Jim, how are you?" );
```

To send a multi-line message, pass in a string that contains newline characters. Here’s an example:

```
$message = "Hi Jim,
How are you?
";
```

```
mail( "Jim Smith <jim@example.com>", "Hello", $message );
```

Lines of text in an email message body should not exceed 70 characters in length. To ensure that your lines are of the correct length you can use PHP’s wordwrap() function:

```
$message = wordwrap( $message, 70 );
```

## Specifying the Sender Address and Adding Headers

By default, when running on a Unix server such as Linux or Mac OS X, mail() usually sends messages from the Web server’s username, such as “www” or “www-data”. (On Windows servers you need to specify a default “from” address with the sendmail_from option in the php.ini configuration file.) If you want to send your email from a different “from” address, you can specify the address in a fourth argument to mail(), as follows:

```
mail( "Jim Smith <jim@example.com>", "Hello", $message, "From: Bob Jones
<bob@example.com>" );
```

This fourth argument lets you specify additional headers to include in the mail message. In this case, just one header was added — the From: header — but you can add as many headers as you like. Just make sure you separate each header by both a carriage return (\r) and line feed (\n) character; this is required by the specification for Internet email messages:

```
$extraHeaders = "From: Bob Jones <bob@example.com>\r\n" .
    "Cc: Anna James <anna@example.com>\r\n" .
    "X-Priority: 1 (Highest)\r\n" .
    "X-Mailer: Matt's PHP Script";
mail( "Jim Smith <jim@example.com>", "Hello", $message, $extraHeaders );
```

This code sets four headers: From: (the message sender), Cc: (an additional carbon-copied recipient), X-Priority: (a value from 1 to 5 indicating the importance of the message), and X-Mailer: (a header specifying the software that sent the message).

RFC 2822 defines the format of email messages, including all the different headers you can use in a message. You can read it at: http://www.faqs.org/rfcs/rfc2822.

X-Priority: and X-Mailer: are known as experimental headers and are not officially part of RFC 2822 (though their usage is widespread).

## Controlling the Return Path Email Address

If your script is running on a Unix Web server, you can pass additional command-line arguments to the MTA as a fifth argument to mail(). Often this is used to add a -f command-line argument in order to set the so-called envelope sender or return path email address:

```
mail( "Jim Smith <jim@example.com>", "Hello", $message, "From: Bob Jones <bob@example.com>", "-f bob@example.com" );
```

Most email messages contain two “from” headers: the From: header and the Return-Path: header. The From: address is the one usually displayed when the email is viewed in a mail program, and the Return-Path: address is the one used to determine the “real” sender of the email for the purposes of sending back bounce messages, determining if the email might be spam, and so on.

Often the two headers contain the same email address. However, when sending mail via a Web script the Return-Path: header is usually set to the Web server’s username (for example, www@example.com). This can be a problem if you want to receive bounce messages (so you can determine if the email address you’re trying to contact no longer exists) and you don’t have access to the “www” mailbox on the server. By using the additional -f argument as just shown, you can set the Return-Path: address to be the same as the From: address (or you can set it to any email address where you can pick up email).

There’s one caveat with using -f. If the Web server user isn’t trusted by the MTA, the MTA adds a warning header to the email message similar to the following:

```
X-Authentication-Warning: www.example.com: user set sender to bob@example.com using -f
```

Though this isn’t usually shown to the recipient, it often results in the message being flagged as spam or otherwise treated as suspicious email. To tell the MTA to trust the Web server user you usually need to add the Web server username to the /etc/mail/trusted-users file on the server. (If you don’t have access to this file, ask your Web hosting provider for assistance.)

