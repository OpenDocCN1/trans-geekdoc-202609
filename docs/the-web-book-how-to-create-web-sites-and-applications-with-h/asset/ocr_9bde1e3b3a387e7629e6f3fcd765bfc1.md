remove the last 4 characters, etc etc), PHP has a function to do it. As for dates, there are even functions which will, if you supply a date and a latitude/longitude location, tell you the time of the sunrise or sunset.

Right, back to our program. Next, we use the mail() command to send the message. It’s as simple as specifying, in the correct order, the "to" address, the "from" address, and the text of the message to be sent. But note the $m = bit at the start, though. The mail() function returns a value to indicate whether the message was successfully sent to the mail server for delivery. We capture this into the $m variable, and display it in the next line.

Finally, the exit() statement ends the PHP program. You don’t need to use this if it’s unambiguous, as it is here. The program is clearly going to end, as there’s no more PHP code left to run. But that won’t always be the case, as we’ll see later.

By surfing to the demo.php page, the program runs and the mail gets sent. The value of 1 for $m means that the mail message was successfully sent to the web server’s outgoing mail system. It does NOT mean that the message was successfully sent to the recipient’s inbox. Unfortunately there’s no way of knowing that.

A few minutes later, the following arrives in my inbox:

![](bbox=[0.12, 0.52, 0.88, 0.7])

Here’s the message. It has the correct subject, and the text of the message is there too. But there are a couple of things to notice.

First, the message appears to come from thewebbo@host368.hostmonster.com. That’s not particularly friendly. There’s an optional extra item that you can include in the mail() function to specify the address that the message appears to come from, though I haven’t bothered with it here. In theory you can set the "from:" address to be whatever you like. But in practice, most web servers won’t send mail that appears to have come from anywhere outside of the domain name that the server is based on. So in this case I could send mail that