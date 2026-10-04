# E-mailing with PHP

```
$html_msg = "&lt;/td&gt;tr&lt;td&gt;"
$html_msg = "$fname has sent you a postcard.body&Enjoy!";
$html_msg = "&lt;/td&gt;tr&lt;align=\"center\&gt;"
$html_msg = "&lt;img src=\$postcard border=0\&gt;"
$html_msg = "&lt;/td&gt;tr&lt;align=\"center\&gt;"
$html_msg = "$messagebody";
$html_msg = "&lt;/td&gt;tr&lt;/center&gt;"
$temp=gettimeday();
$msgid=(int)$temp['sec'];
$msgid = md5(time()) - $msgid;
$conn = mysql_connect(\$server,"joeser","yourpass\n$sql_select = "INSERT into (validator, to_e_mail, toname, from_e_mail, fromname, bc_e_mail, subject, postcard, message) VALUES (\$msgid,\$to,\$toname,\$from_e_mail,\$fromname,\$bc_e_mail,\$subject,\$postcard,\$messagebody)";
$query = mysql_query($sql, $conn,mysql_error));
$confirmation = "Please confirm your postcard;";
$confirmation = "Mail from " . $fname". \n\n"
$confirmation = "Please click on the link below to confirm that\nyou would like to send this postcard;\n\n"
$confirmation = "$html_msg. \n\n"
$confirmation = "&lt;a href='http://localhost/wrox/confirmmail.php&gt;\$msgid&gt;Click here to confirm/" . $fname . " \n\n"
$confirmation = "Please visit the following URL to confirm your\npostcard;\n\n"
$confirmation = "http://localhost/wrox/confirmmail.php"
$ids = "$msgid";\n\n"
$message = "A Multipart Message in MIME format\n\n"
$message = "--$boundary\n\n"
$message = "Content-Type: text/html; charset=iso-8859-1\n\n"
$message = "Content-Type-Encoding: 7bit\n\n"
$message = "$confirmation. \n\n"
$message = "--$boundary\n\n"
$message = "Content-Type: text/plain;charset=iso-8859-1\n\n"
$message = "Content-Type-Encoding: 7bit\n\n"
$message = "$text. \n\n"
$message = "--$boundary--\n"
$text = "mail(\$fname, $confirmationsubject, $message, $headers);
if ($msalent)
necho "Here is the postcard you wish to send.<br>";
echo "A confirmation e-mail has been sent to you.<br>";
echo "Open your e-mail and click on the link to confirm that you would\nlike to send this postcard to $toname.<br>";
echo "<Subject>" . $subject . "<br>";
echo "<Message>" . $message . "<br>";
echo $html_msg;
elelse (
necho "There was an error sending the e-mail.";
)
?>
</body>
</html>
```