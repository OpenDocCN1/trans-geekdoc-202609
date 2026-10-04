# Chapter 10

Note the use of a PHP hash, md5(). This returns a 128-bit "fingerprint," or "hash," of the message passed to it. For example, the md5 hash of "Hello World" is b10a8db164e075410b5a799bc72e3fe5. It is designed as a one-way encryption of the data passed to it, so you cannot reverse it to

By passing in time, you can fairly be certain that the md5 hash will be a unique value, which you use as a unique ID for the data. It is not 100 percent guaranteed to be unique, but because it is generated based on the current time in seconds and 32 alphanumeric characters, you can be reasonably sure it will be unique.

If you are interested in finding more information about the md5 hash, visit RFC 1321: The MD5 Message-Digest Algorithm at http://www.faqs.org/rfc/rfc1321.

```
$conn = mysql_connect('yourserver', 'joeser', 'yourpass');
mysql_select_db('postcard', 'postcard');
$sql = "INSERT INTO content (validator, to_email, toname, from_e_mail,
fromname, bcc_email, cc_email, subject, postcard, message) VALUES
\$md5, \$!, \$toname, \$fromname,\n\$body, \$!, \$subject, \$postcard";
$query = mysql($sql, $conn) or die(mysql_error());
```

Next, to store the postcard data temporarily until it is validated. When the confirmation link in the e-mail is sent, it is posted to its intended recipient.

```
$confirmationsubject = "Please Confirm your postcard";
$confirmationmessage = "Hello " . $fromname . "\n\n";
$confirmationmessage .= "Please click on the link below to confirm that
You would like to send this to postcard:\n";
$confirmationmessage .= $html_msg . "\n";n$id=$md5="<a href="http://localhost/wrox/confirmation.php?id=\$md5">Click here to confirm to:</a>";
$textconfirm = "Hello " . $fromname . "\n\n";
$textconfirm .= "Please visit the following URL to confirm your
$textconfirm .= "<a href="http://localhost/wrox/confirmation.php?id=\$md5"></a>";
$message = "This is a Multiple Message in MIME format;\n";n$message .= "Content-Type: text/html; charset=iso-8859-1\n";
$message .= "Content-Transfer-Encoding: 7bit\n";
$message .= $confirmationmessage . "\n";n$message .= "-\$body-\n";n$message .= "Content-Type: text/plain; charset=iso-8859-1\n";n$message .= "Content-Transfer-Encoding: 7bit\n";n$message .= $textconfirm . "\n";n$message .= "-\$body-";
```

The variable $confirmationmessage is the HTML version of the confirmation e-mail. The variable $textconfirm is the plain text version. The variable $message is the entire message, coded to send both plain and HTML e-mails. Note where you insert the $confirmationmessage and $textconfirm variables in the multipart

312