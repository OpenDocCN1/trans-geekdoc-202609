
included a list of fairly well known file types. If you're not sure about the MIME type for a specific type of file can always save yourself an email with the file. Then inspect the source code for the content type.

```php
$allowed_type = array("application/msword",
"application/vnd.openxmlformats-officocument.wordprocessingml.document",
"application/vnd.ms-excel",
"image/gif",
"image/jpeg",
"application/pdf",
"image/png",
"text/plain",
"application/zip");
```

Once you identify that the file type is allowed it needs to be base64 encoded the mail program can design the file correctly. The way to do this is to open the file and read the binary contents. After the file is opened you can store the content into the $data variable. Then close the file. The last step is to base64 encode the file and chunk_split into manageable sizes. If you ever looked at the raw text of a base64 encoded file, it can be quite long.

```php
if(in_array($type,$allowed_type)) {
		$file = fopen($tmp_name,'rb');
		$data = fread($file,filesize($tmp_name));
		fclose($file);
		$data = chunk_split(base64_encode($data));
	} else {
```

If the user uploaded a file type that's not allowed you should show a message and exit the script before the email is sent. Keep in mind: you won't actually be uploading and moving the file to a permanent location on the server. The nice thing about this method is that as soon as the script is done the files are automatically deleted from the server. The temp folder does not store these files long.

```php
{
		echo "file type not allowed: " . $type;
		exit();
	}
}
```

Now that we've verified and encoded the attachment we can create a boundary with the attachment. It's very similar to the boundary for the message except attachments are base64 encoded. Use the $_FILES variables we created at this section of code for type and name to assemble the required boundary information. Again, this PART MUST BE EXACT, without CRLF. If you are off by a single space, extra or missing CRLF, the attachment won't work. Although PHP may be forgiving, formatting is not. The code for the closing boundary to indicate the location in the message. It has two dashes "-" at the end of the line.

```php
$message = "--{$mime_boundary}\n\nContent-Type: {$type};\n\nname="{$name}"\n\nContent-Disposition: attachment;\n\nfilename="{$filename}"\n\nContent-Transfer-Encoding: base64\n\n\n";

$message .= "--{$mime_boundary}--\n";
```

As long as there haven't been any errors so far it is time to send the email. Since we've loaded everything into variables we just need to specify the mail function and test if the message is sent or not. Keep in mind that even if the function does not return an error it doesn't mean that the message didn't end up in the spam folder or didn't encounter some other error that prevented it from getting through. I encourage you to test your system thoroughly, including randomly testing your live system to ensure that everything is working as expected. I can't tell you how many times I've run across companies that claimed that the mail wasn't getting through to find out that they changed something on their firewall, network, or upgraded/changed their email server and didn't consider testing all the affected systems until they encountered a critical problem.

```php
if (mail($to, $subject, $message, $headers)) {
    echo "Your mail was sent"; exit();
} else {
    echo "There was an error sending your mail"; exit();
}
```

The final part of the web page is the form. The form comes at the end of the code rather than at top of the page. You want your PHP code to run after the submit button is clicked and the information is posted back to the same page. This enables you to capture any missing fields and validate all the data before the email is sent.

The form is very straightforward. I chose to place the Alert variable at the top of the page. Remember, we created the Alert variable to display a message to the user if they didn't fill in all the fields.

I think like this basic method is that you can include as many file fields as want. The code will work if the user uses zero or more fields. If you don't need to upload files you simply remove the file fields from the form and all the code as is.

The only item I didn't include in this lesson is the use of Google reCAPTCHA that was covered in another lesson. If you don't need to prevent bots from sending you amounts of bogus email you can implement Google's reCAPTCHA to the submit button.

There are a couple of things I'd like to point out regarding this form, which may seem obvious, many people forget that you can limit spam from getting into your system. First, the length of the email is 64 characters. The filter is only good for 64 characters. Don't let the users enter anything. When was the last time you saw an email longer than 64 characters? The same goes for the subject. They don't need to write a book. A couple of words will do fine. Finally, remember that some applications may have problems with lines that are longer than 78 characters. I set the text area column width for the message to 78 characters. This is important as we use wordwrap in the code to match the RFC2822 standard. However, it's nice for the user to get a visual feedback on the screen of

```php
<?php echo $alert; ?>
<form action="<?php echo $_SERVER['REQUEST_METHOD']; ?>" method="post" enctype="multipart/form-data">
<p>From-email: <input name="email" type="text" size="60" maxlength="64"></p>
<p>Subject: <input name="subject" type="text" size="60" maxlength="64"></p>
<p>Message: <textarea name="message" rows="4"></textarea></p>
<p>File 1: <input type="file" name="file1"></p>
<p>File 2: <input type="file" name="file2"></p>
<input type="submit" name="Submit" value="Submit"></p>
</form>
</body>
```

There is a, bullet proof PHP Mail message to prevent bots and spammers from utilizing email injection techniques to take over your email server. We learned how to assemble the boundary, message, and attachments. Using the $_FILES superglobal we created a form with visual feedback. The best part is that each page passes its fields and data to the next page. Only on a couple of lines of PHP code inside the form. The entire process takes a couple of minutes.
