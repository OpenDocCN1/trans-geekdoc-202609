
$my_random_value, but shorter is always best as there's less chance of making a typing mistake when you refer to the same variable later on.

Line 6 checks to see whether $r is equal to 7. If it is, everything between the 2 curly brackets gets executed. If it's not, everything between the curly brackets gets ignored.

Note two important points about the code in line 6. First, the if command is almost unique in PHP, in that it doesn't (indeed, mustn't) end with a semicolon. Second, when you're comparing something, you use 2 "equals" signs rather than just one. So, $x = 99 will set the variable $x to 99. But to check whether $x is equal to 99 we say if ($x == 99). Note, too, how the value to check for has to go inside rounded brackets.

Incidentally, if you leave PHP mode and then re-enter it within the same file, no information is lost. So, for example, the following:

```html
<html>
<?php
$name = "Fred";
?>
Your name is
<?php echo $name; ?>
</html>
```

Will display the message Your name is Fred.

## Sending Email with PHP

With server-side programming you can do just about anything, and that includes sending email. Try this little PHP program, by changing the contents of demo.php to the following and then surfing to the demo.php page:

```php
<?php
$to = "robert@the-web-book.com";
$subject = "Hello";
$message = "This is my Web server, sending me email on ";
$message .= date("D");
$message .= " at ";
$message .= date("H:i");

$rn = mail($to, $subject, $message);
echo "Return code from mail was " . $rn;
exit();
?>
```

You should see a message which says "Return code from mail was 1". To understand why, and what this program does, let's examine it in detail.

The first line of code creates a new variable called $to, which is set to the "to" address of the email we're going to be sending. In this case, I'm sending the message to myself. If you want to try this example, please use your own email address rather than mine!

The next line sets the subject of the message in a similar way, and then we create $message, which is the text of the actual message we'll be sending.

But what about $message .= date("D");? Are we setting $message to something else entirely? No. Take a closer look and you'll see we're using .= rather than = on its own. The .= symbol means that PHP should add the new text to the end of what's in that variable already. But what text to add? In this case we're using the date() function and specifying "D" as what's known as the argument. The date() function returns lots of time- and date-related information, such as the current day, date, hour, minute, second, year, and so on. There are dozens of possible things that it can return, each symbolized by their own letter (and these are case-sensitive, by the way, so d is not the same as D).

In this case, D returns the current day of the week as a 3-letter abbreviation. So, this line is adding a 3-letter version of today's day onto the end of the $message string which we created in the line above. Thus, if today happens to be Friday, $message will now be "This is my Web server, sending me email on Fri".

The next line adds " at " to the $message string. So now it contains "This is my Web server, sending me email on Fri at ".

Finally we add the current time to the end of the message that we'll be emailing. We use the date() function again, with H and i. H returns the current hour in 24-hour clock format, and i returns the number of minutes. Anything that isn't a letter, within the bracketed part of the date() function, gets returned as-is. So if the time happened to be 9pm, date("H:i") would return 21:00.

PHP is particularly good at processing and manipulating strings and dates. Whatever you need to do with a string (count the number of characters, convert it to upper or lower case, remove the last 4 characters, etc etc), PHP has a function to do it. As for dates, there are even functions which will, if you supply a date and a latitude/longitude location, tell you the time of the sunrise or sunset.

Right, back to our program. Next, we use the mail() command to send the message. It’s as simple as specifying, in the correct order, the "to" address, the "from" address, and the text of the message to be sent. But note the $m = bit at the start, though. The mail() function returns a value to indicate whether the message was successfully sent to the mail server for delivery. We capture this into the $m variable, and display it in the next line.

Finally, the exit() statement ends the PHP program. You don’t need to use this if it’s unambiguous, as it is here. The program is clearly going to end, as there’s no more PHP code left to run. But that won’t always be the case, as we’ll see later.

By surfing to the demo.php page, the program runs and the mail gets sent. The value of 1 for $m means that the mail message was successfully sent to the web server’s outgoing mail system. It does NOT mean that the message was successfully sent to the recipient’s inbox. Unfortunately there’s no way of knowing that.

A few minutes later, the following arrives in my inbox:

![](img/50e1558b8202f19b96c1cc386ea5ec66_220_0.png)

Here’s the message. It has the correct subject, and the text of the message is there too. But there are a couple of things to notice.

First, the message appears to come from thewebbo@host368.hostmonster.com. That’s not particularly friendly. There’s an optional extra item that you can include in the mail() function to specify the address that the message appears to come from, though I haven’t bothered with it here. In theory you can set the "from:" address to be whatever you like. But in practice, most web servers won’t send mail that appears to have come from anywhere outside of the domain name that the server is based on. So in this case I could send mail that appears to come from `robert@the-web-book.com` but not `robert@microsoft.com`. This rule is imposed to help prevent web hosts from having their servers used by spammers.

It's important that you do set a `from:` address when sending mail. Because that's where the reply will be sent when the recipient hits their `reply` button. I'd much rather the replies came to a real mailbox at `robert@the-web-book.com` rather than something which I wouldn't even know how to log into if I wanted.

There's one other discrepancy too. See how the text of the message says that it was sent on Fri at 14.15. But look in the upper window and, according to my Outlook email program, the message was received at 21.15. The message appeared in my inbox within seconds of me surfing to the demo.php page, so why does it appear to have taken 7 hours? You will recall that PHP is a server-side language. So when you use the `date()` function to find out the time, it looks up the time on the server. Compare this to the client-side Javascript, which finds out the time on the visitor's own PC. The hostmonster web server is in the US, where it's 2.15pm. I'm in the UK, 7 hours ahead, where it's 9.15pm, so that's why the discrepancy arises. And it's well worth knowing about, because it can lead to problems if you create a web application that needs to know the correct (whatever that means, in this global market) time.

## Passing Information to PHP

There are various ways of passing information to a PHP program, and we'll cover many of them in the database-related chapters that follow, and when we come to talk about HTML forms later on. But here's a fun example for now, which illustrates a couple of important points about PHP.

Open PSPad, delete the contents of demo.php and replace it with the following:

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

Surf to the demo.php page and you'll see a message that says `Hello, how are you today`.

Now surf to the page again, but use the following URL. Substitute the-web-book.com for whatever your domain is called. And you can change Robert to your own name if you wish, too:

```
http://www.the-web-book.com/demo.php?name=Robert
```

Note the question mark at the end of the URL, followed by name=Robert. You’ve probably seen URLs like this before, and you might have wondered what they meant. Now you’re going to find out.

The question mark in a URL allows you to surf to a server-side program (in this case one called demo.php) and also to pass information to the program. In this case, we have created a variable called name with a value of Robert. The PHP program can, if it wishes, retrieve the contents of that variable.

Along with the question mark, the other symbol that you use for passing information to PHP programs via the URL is the ampersand (&) sign. This is used when you want to pass more than one variable. For example:

```
http://www.the-web-book.com/demo.php?firstname=Robert&surname=Smith
```

Here, we’re passing 2 variables called firstname and surname. Note how only the first variable is preceded by a question mark. Any subsequent variables must be preceded by an ampersand.

Back to our demo.php program. Assuming you entered a name of Robert on the URL, you’ll see the following in your web browser:

![](img/50e1558b8202f19b96c1cc386ea5ec66_222_0.png)
