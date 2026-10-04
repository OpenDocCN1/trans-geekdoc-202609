# Chapter 10

```
</tr>
<tr>
<td valign="top">Message:</td>
<td>
<textarea cols="60" rows="10" name="message">
>Enter your message here</</textarea>
</td>
</tr>
<tr>
<td></td>
<td>
<input type="submit" value="Send">
<input type="reset" value="Reset the form">
</td>
</tr>
</table>
</form>
<body>
</html>
```

+   2. Save the page as postcard.php. Note that postcard.php doesn't actually have any PHP code in it. It simply collects the required data in an HTML form. Give it a .php extension in case you decide to add PHP code to it later (and you will).
3. Start a new document and enter the following code:

```
<html>
<head>
<title>Mail Sent!</title>
</head>
<body>
<?php
$to = $_POST['to'];
$from = $_POST['from'];
$subject = $_POST['subject'];
$message = $_POST['message'];
$headers = "From:" . $from . "\r\n";
$mailsent = mail($to, $subject, $message, $headers);
if ($mailsent) {
echo "Congrats! The following message has been sent:<br>";
echo "<b>To:</b>" . $to . "<br>";
echo "<b>From:</b>" . $from . "<br>";
echo "<b>Subject:</b>" . $subject . "<br>";
echo "<b>Message:</b>" . $message . "<br>";
} else {
echo "there was an error...";
}
?>
</body>
</html>
```

288