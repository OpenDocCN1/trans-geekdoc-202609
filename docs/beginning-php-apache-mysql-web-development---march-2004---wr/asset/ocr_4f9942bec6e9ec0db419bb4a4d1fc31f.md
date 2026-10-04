```
$headers = "Content-type: text/html; charset=iso-8859-1\r\n";
$headers .= "Content-Transfer-Encoding: 7bit\r\n";
$headers .= "From: " . $from . "\r\n";
$mail = mail($to, $subject, $message, $headers);
if ($mail) {
  echo "Congrats! The following message has been sent:<br>";
  echo "<To:$to<br>";
  echo "<From:$from<br>";
  echo "<Subject:$subject<br>";
  echo "<Message:$message<br>";
  echo $message;
} else {
  echo 'There was an error...';
}
?>
n</body>
</html>
```

3. Save the file.

4. Load postcard.php in your browser and fill in the fields with appropriate information. Be sure to include some HTML in the message field, such as:

<h3>Hello World!</h3><br>Prepare for our arrival.<br><br>We are starving!!</p>

5. Click the Send button, and open your e mail client to see the new message, which will look something like Figure 10-5.

![](bbox=[0.263, 0.51, 0.846, 0.807])

Figure 10-5