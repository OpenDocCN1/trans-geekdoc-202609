# E-mailing with PHP

3. Save the text file as firstmail.php and load it in your browser. You should see a blank page and should receive an e-mail shortly at the address entered as the first parameter.

Pretty cool, huh? That's all there is to it!

# How It Works

The Mail() function automatically sends an e-mail, using the following format:

```
Mail(to, subject, message, other_parameters)
```

The headers and other_parameters are optional. If you want to send a message to multiple recipients, their addresses must be separated with a comma in the to parameter:

```
Mail(*first@-mail.com, second@mail.com, "Hi", "Whazzup??")
```

We will cover the headers parameter soon. The other_parameters are beyond the scope of this book, but if you want more information about the mail() function, point your browser to www.php.net/manual/en/function.mail.php.

You may have noticed receiving this e-mail that there was no From (or, your service provider may have automatically put in a bogus address. Ours says "Nobody". In the next example, you will see how to add a "From" parameter to your e-mail, and you'll collect information from the user before sending the e-mail. Let's get in it!

# Try It Out Collecting Data and Sending an E-mail

You are going to create Web pages, postcard.php and pc_sendmail.php. The file postcard.php will collect the data you are going to send. The file pc_sendmail.php will actually send the message, using the data you enter.

+   1. Start up your favorite text/PHP/HTML editor, and enter the following code:

```
<html>
<head>
<title>Enter E-mail Data</title>
</head>
<body>
<form name="theform" method="post" action="sendmail.php">
<table>
<tr>
<td>To:</td>
<td><input type="text" name="to" size="50"></td>
</tr>
<tr>
<td>From:</td>
<td><input type="text" name="from" size="50"></td>
</tr>
<tr>
<td>Subject:</td>
<td><input type="text" name="subject" size="50"></td>
</tr>
</table>
```