```
```
echo "Message could not be sent..."\;
}
?>
</body>
</html>
```
```

# # Sending attachments with email

To send an email with mixed content requires to set **Content-type** header to **multipart/mixed**. Then text and attachment sections can be specified within **boundaries**.

A boundary is started with two hyphens followed by a unique number which can not appear in the message part of the email. A PHP function **md5()** is used to create a 32 digit hexadecimal number to create unique number. A final boundary denoting the email's final section must also end with two hyphens.

Attached files should be encoded with the **base64_encode()** function for safer transmission and are best split into chunks with the **chunk_split()** function. This adds `\r\n` inside the file at regular intervals, normally every 76 characters.

Following is the example which will send a file **/tmp/test.txt** as an attachment. you can code your program to receive an uploaded file and send it.

```
```
<html>
<head>
<title>Sending attachment using PHP</title>
</head>
<body>
<?php
$to = "xyz@somedomain.com"\;
$subject = "This is subject"\;
$message = "This is test message."\;
# Open a file
$file = fopen( "/tmp/test.txt", "r" )\;
if( $file == false )
{
   echo "Error in opening file"\;
   exit()\;
}
# Read the file into a variable
$size = filesize("/tmp/test.txt")\;
$content = fread( $file, $size)\;
```
```