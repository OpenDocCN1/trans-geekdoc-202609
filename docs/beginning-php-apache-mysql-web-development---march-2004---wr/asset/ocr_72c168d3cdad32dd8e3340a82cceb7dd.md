# Chapter 10

What follows is pretty standard stuff; did you prefer in pc_sendmail.php. Here's a quick review: To create a multipart message, use the Content-type of multipart/alternative, and a boundary that contains unique alphanumeric text to designate the MIME and text portions of the e-mail.

```
$boundary = =MP_Bound_xycc948x=";
$headers = "MIME-Version: 1.0\r\n";n$headers = "Content-type: multipart/alternative; boundary=\$boundary\r\n";nif ($cc == "") {
	$headers = "CC: " $cc\r\n";
}
if (!$bcc == "") {
	$headers = "BCC: " $bcc\r\n";
}
$headers .= "From: " $from\r\n";n
$html = "<center>";
$html .= "<table width="500" border=0 cellpadding="4*>";
$html .= "<tr><td>Greeting, $toname!</td></tr>";n$html .= "<tr><td></td></tr>";n$html .= "<tr><td align="center\">$fromname has sent you a postcard today.<br>Enjoy!</td></tr>";n$html .= "<tr><td></td></tr>";n$html .= "<tr><td align="center\"><img src="$postcard" border="0"></td></tr>";n$html .= "<tr><td></td></tr>";n$html .= "<tr><td>$messagebody </td></td></tr>";
$html .= "<tr><td></td></tr>";
$html .= "</table></center>";
```

```
$message = "This is a Multipart Message in MIME format";
$message .= "-$boundary\";
$message .= "Content-type: text/html; charset=iso-8859-1\r\n";
$message .= "Content-Transfer-Encoding: 7bit\r\n";
$message .= "$html\r\n";
$message .= "-$boundary\";
$message .= "Content-type: text/plain; charset=iso-8859-1\r\n";
$message .= "Content-Transfer-Encoding: 7bit\r\n";
$message .= "$messagebody\r\n";
$message .= "-$boundary-";
$sailsent = mail($to, $subject, $message, $headers);
?>
```

Until now, nothing has been sent to the browser. That is a good thing. For example, if you had received any errors, and wanted to use the header() function to redirect the user to a different page, it works only if text has already been sent to the browser. The lesson is: Don't put <html> (and other tags) inside the code until you are ready to send text to the user's browser.

```
<html>
<head>
<title>Postcard Sent!</title>
</head>
<body>
<?php
if ($sailsent) {
	echo "Congrats! The following message has been sent: <br><br";
	echo "To:$to<br>";
```

314