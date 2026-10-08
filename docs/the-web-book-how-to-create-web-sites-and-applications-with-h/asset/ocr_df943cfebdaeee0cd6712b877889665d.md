appears to come from `robert@the-web-book.com` but not `robert@microsoft.com`. This rule is imposed to help prevent web hosts from having their servers used by spammers.

It's important that you do set a `from:` address when sending mail. Because that's where the reply will be sent when the recipient hits their `reply` button. I'd much rather the replies came to a real mailbox at `robert@the-web-book.com` rather than something which I wouldn't even know how to log into if I wanted.

There's one other discrepancy too. See how the text of the message says that it was sent on Fri at 14.15. But look in the upper window and, according to my Outlook email program, the message was received at 21.15. The message appeared in my inbox within seconds of me surfing to the demo.php page, so why does it appear to have taken 7 hours? You will recall that PHP is a server-side language. So when you use the `date()` function to find out the time, it looks up the time on the server. Compare this to the client-side Javascript, which finds out the time on the visitor's own PC. The hostmonster web server is in the US, where it's 2.15pm. I'm in the UK, 7 hours ahead, where it's 9.15pm, so that's why the discrepancy arises. And it's well worth knowing about, because it can lead to problems if you create a web application that needs to know the correct (whatever that means, in this global market) time.

# ## Passing Information to PHP

There are various ways of passing information to a PHP program, and we'll cover many of them in the database-related chapters that follow, and when we come to talk about HTML forms later on. But here's a fun example for now, which illustrates a couple of important points about PHP.

Open PSPad, delete the contents of demo.php and replace it with the following:

```
```php
<?php
$person = $_GET["name"];
echo "<HTML>";
echo "Hello ";
echo $person;
echo ", how are you today?";
echo "</HTML>";
?>
```
```

Surf to the demo.php page and you'll see a message that says `Hello, how are you today`.