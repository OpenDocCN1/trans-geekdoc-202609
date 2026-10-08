```
$message .= " at ";
$message .= date("H:i");

$rn = mail($to,$subject,$message);
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

PHP is particularly good at processing and manipulating strings and dates. Whatever you need to do with a string (count the number of characters, convert it to upper or lower case,