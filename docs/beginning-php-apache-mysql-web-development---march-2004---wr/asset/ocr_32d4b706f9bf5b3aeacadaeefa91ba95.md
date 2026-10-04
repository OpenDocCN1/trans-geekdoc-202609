```
<td>From:</td>
<td>
<input type="text" name="from" size="50">
</td>
</tr>
<tr>
<td>CC:</td>
<td>
<input type="text" name="cc" size="50">
</td>
</tr>
<tr>
<td>Bcc:</td>
<td><input type="text" name="bcc" size="50"></td>
</tr>
<tr>
<td>Subject:</td>
<td><input type="text" name="subject" size="50"></td>
</tr>
<tr>
<td align="top">Message:</td>
<td>
<textarea cols="60" rows="10" name="message">
Enter your message here</textarea>
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
</body>
</html>
```

+   3. Edit your copy of pc_sendmail.php in your favorite text editor. Back up pc_sendmail.php before making changes if you want to keep the old version.

+   4. Make the following changes to pc_sendmail.php. Modifications are shown in bold:

```
<html>
<head>
<title>Multipart Sent!</title>
</head>
<body>
<?php
$to = $_POST[\*to"];
$cc = $_POST[\*cc"];
$bcc = $_POST[\*bcc"];
$from = $_POST[\*from"];
```