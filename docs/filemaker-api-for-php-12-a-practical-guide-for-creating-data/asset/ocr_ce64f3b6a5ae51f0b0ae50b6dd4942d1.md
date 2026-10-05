```
$to = "tduelformulationspro.com";
$subject = filter_var($_POST['subject'], FILTER_SANITIZE_STRING);
$message = filter_var($_POST['message'], FILTER_SANITIZE_STRING);
$message = wordrap(\$message, 78);
$message = str_replace("\", "\n", $message);
$headers = "From: $from";
$headers .= "\nReply-To: $reply_to";
$headers .= "\nCc: tduel@formulationspro.com";
$headers .= "\nBcc: tduelformulationspro.com";
$headers .= "\nX-Mailer: $mailer" . " .php" . phpversion();
```

```
Return-Path: <mailer@example.com>
Delivered To: junemail@formulationspro.com
Received from: localhost [127.0.0.1]
by formation.com (with SMTP) ID 1LAB4KA7625
from junemail@formulationspro.com, Mon, 25 Apr 2011 11:54:32 -0700 (PT)
X-From: <junemail@formulationspro.local>
X-To: <tduel@formulationspro.com>
X-To-Blocked: blocked
X-Queue-ID: 6S5E9A6c
X-Spam-Yes: YES
X-Spam-Score: 6.92
X-Spam-Status: YES(6.942:ALL_TRUSTED=-1.8,n=967,BAYS=5.5,MESSAGE_HEADER_TYPE=SPAM_RATIO=2.109)
Received from: localhost (127.0.0.1) (omtaid, new-port 1824)
by formation.com with OpenSMTP for <tduel@formulationspro.com>
Mon, 25 Apr 2011 11:54:31 -0700 (PT)
Received from mail.local (unknown [192.168.1.1])
by formation.com (with SMTP) ID 0D654A76E2
from tduel@formulationspro.com
Received from localhost (Postfix, from user 70)
id 3D615A5E8D3, Mon, 25 Apr 2011 11:54:30 -0700 (PT)
Subject: tduel@formulationspro.com
Reply-To: tduel@formulationspro.com
Cc: tduel@formulationspro.com
X-Mailers: PHP/5.3.0-PHPIME/1.0
```

Figure 7-14 Cc and Bcc addresses are marked as sent but not from an unauthenticated Mail function.

I encourage you to send yourself an email with the message and attachments to see what the repetitive code looks like. Open the source code and the attachment code. This will give you a clear idea of what we have attached. The headers are built, so we can include the message section of each email. Each message (and attachments) must be separated by a boundary with a unique string. We can create the boundary using a md5 hash of the current message. The message section of the file will be sent as text and encoded in 7-bit format. You must have two lines of feeds before the actual attachment or the email will not display correctly.

```
$boundary = "++Multipart_Boundary_" . md5(time(""));";
$headers = "Content-Type: multipart/mixed; boundary=$boundary";
$boundary = "--$boundary\n";
$message = "This is a multi-message email in MIME format.\n--$boundary\n\nContent-Type: text/plain; charset=ISO-8859-1\n\nContent-Transfer-Encoding: 7bit\n\nMessage: \\n--$boundary--";
```

Before you include the attachments you check the total size of your server settings. By default the php.input value for max_filesize is 2MB. Not very much, considering most mail servers are set to allow 20MB+ by default days. One thing to keep in mind is by the time your code gets to this points, the file size is already uploaded to the server in the temp directory. Therefore, the only reason why you want to validate the file size is to check the size of the files you are coming in. When you change the server settings the check size of the files will however work while they are trying to upload a 1 GB file. You can also change the settings using the following PHP code, where the file size is specified as M for Mb. For those of you using a hosted server you probably won't be able to change the php.ini settings, so you'll have to temporarily change them using your script. Check with your host for more information