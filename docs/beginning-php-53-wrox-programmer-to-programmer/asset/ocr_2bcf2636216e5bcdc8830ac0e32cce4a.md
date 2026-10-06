# Chapter 16: PHP and the Outside World

![](bbox=[0.193, 0.093, 0.881, 0.545])

Server and script details

```
[HTTP_HOST] = localhost
[HTTP_USER_AGENT] = Mozilla/5.0 (X11; Linux i686_64; Gecko/20100208 Firefox/3.0.1)
[HTTP_CONTENT_TYPE] = application/xml
[HTTP_ACCEPT_LANGUAGE] = en-US;en=0.9;q=0.8
[HTTP_ACCEPT_ENCODING] = gzip, deflate
[HTTP_ACCEPT_CHARSET] = ISO-8859-1,utf-8;q=0.5;q=0.7
[HTTP_CONNECTION] = keep-alive
[HTTP_REFERER] = http://localhost/
[PATH] = /usr/local/bin:/bin
[SERVER_SOFTWARE] = Apache/2.2.23 (Ubuntu)
PHP/5.2.4-ubuntu5.5 with Subin-Patch Server at Localhost Port 80

[SERVER_VERSION] = Apache/2.2.23 (Ubuntu)
[SERVER_NAME] = Localhost
[SERVER_PORT] = 80
[REMOTE_ADDR] = 127.0.0.1
[DOCUMENT_ROOT] = /var/www/
[REMOTE_USER] = localhost
[REMOTE_PATH] = /server_info.php
[REQUEST_METHOD] = GET
[REQUEST_PROTOCOL] = HTTP/1.1
[QUERY_STRING] =
[REQUEST_URI] = /server_info.php
[PHP_SELF] = server_info.php
[PHP_SELF_TIME] = 12318893
[args] = Array
{
[argc] => 0
```

Figure 16-3

# Send Email

Many Web applications have a need to send email messages. For example, a contact form script typically processes a form submitted by a visitor and emails the form information to the Webmaster. Other scenarios include "tell friend" functions, as well as member registration and "forgotten password" functions that email information to members.

PHP includes built-in support for creating and sending email messages, which makes it very easy to send from within your PHP scripts.

To send an email message in PHP, you use the mail() function. On Unix servers such as Linux and Mac OS X, PHP uses the operating system's built-in mail transfer agent (MTA) to send the email. (Common MTAs include sendmail, postfix, and exim.) On Non-Unix servers such as Windows, PHP talks directly to an SMTP server (either on the server or on another machine).

497