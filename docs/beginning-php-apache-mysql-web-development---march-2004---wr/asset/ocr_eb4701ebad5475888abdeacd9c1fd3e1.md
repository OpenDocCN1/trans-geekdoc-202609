# E-mailing with PHP

```
$headers = "* . $from . "\r\n";
```

The mail() returns a value of True if it is successful and False if it fails. You will use this function to make your application more user-friendly;

```
$mailsent = mail($to, $subject, $message, $headers);
if ($mailsent) {
    echo "Congrats! The following message has been sent: <br><br>";
    echo "<b>To:</b> $to<br><br>";
    echo "<b>Subject:</b> $subject<br><br>";
    echo "<b>Message:</b> $message<br><br>";
    echo $message;
} else {
    echo "There was an error...";
}
```

Of course, you can modify this to handle errors more elegantly. Use the knowledge you acquired in Chapter 8 to do so.

You have created your first PHP e-mail application. Congratulations! (Call your mother! She'll be proud.) You'll probably soon get tired of ugly, plain text e-mails. I'm sure you're chafing at the bit to create colorful, formatted e-mails, right? How else are you going to enable users to send some pretty postcards? Okay, let's do something about that!

# Dressing Up Your E-mails with HTML

Because you are creating a postcard application, sending plain-text e-mails just won't do. You want to dress them up a bit, and make them look professional, yet attractive. So, let's add a bit of HTML to your e-mail code to dress it up!

> Try It Out Sending HTML Code in an E-mail

First, let's try a little experiment. This step isn't vital, but it will help illustrate a later point about headers.

+   1. Go to Step 5 of the previous "Try It Out" section and send another e-mail. This time, put some HTML in the message. An example would be:

<h3>Hello World!</h3><br>Prepare for our arrival.<br><br><b>We are starving!!!</b></n
2. When you have entered all relevant data in the form, click the Send button, and check your e-mail. It should look something like the e-mail shown in Figure 10-4.

291