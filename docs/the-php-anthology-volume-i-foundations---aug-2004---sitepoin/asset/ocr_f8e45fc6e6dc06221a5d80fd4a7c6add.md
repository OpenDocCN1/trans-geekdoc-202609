mand prompt, and are using sendmail on the server to handle email. Phew! It’s a long list of requirements, I know, but this fairly common configuration greatly simplifies matters.

First things first. You’ll need to place a file called .forward in your home directory. Use a text editor to write the following to the file (all on one line):

```
you@yoursite.com
"|/home/yourUserName/phpmailer/mailhandler.php"
```

This tells the mail system on the server that any email headed for you@yoursite.com not only needs to be delivered to that address, but must also be sent to the PHP script at /home/yourUserName/phpmailer/mailhandler.php.

Now, within the PHP script mailhandler.php, you can process incoming email in any way you like. As this PHP script is intended to be run automatically by the mail system—not your Web server—the first line of the file must point to the location of the standalone PHP program on your server (commonly /usr/bin/php). Here’s a possible script that detects incoming email from a particular address and sends a second notification email in response:

```
#!/usr/bin/php
<?php
// Read the email from the stdin file
$fp = fopen('php://stdin', 'r');
$email = fread ($fp, filesize('php://stdin'));
fclose($fp);

// Break the email up by linefeeds
$email = explode("\n", $email);

// Initialize vars
$numLines = count($email);
for ($i = 0; $i < $numLines; $i++) {
    // Watch out for the From header
    if (preg_match("/^From: (.*)/", $email[$i], $matches)) {
        $from = $matches[1];
        break;
    }
}

// Forward the message to the hotline email
if (strstr($from, 'vip@example.com')) {
    mail('you@yourdomain.com', 'Urgent Message!',
```