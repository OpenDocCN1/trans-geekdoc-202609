# FIGURE 12.16 A simple email

![](bbox=[0.275, 0.075, 0.86, 0.37])

Simply including (X)HTML elements in the message body is not the end of the story however. To make this work we also need to include some additional header information, like this:

```
$headers = "MIME-Version: 1.0\r\n";
$headers .= "Content-type: text/html; charset=iso-8859-1\r\n";
```

MIME stands for multipurpose Internet mail extensions. MIME extends the format of Internet mail to allow more sophisticated non-text-based e-mail messages. The e-mail client needs to know what version of MIME we are using so the MIME header defines the MIME version. The Content-type header is a mandatory header which specifies the format of the message body (in this case text and html) and the character set being used. The following script illustrates an example of a script creating an (X)HTML email message:

```
<?php
// File: example12-24.php

$strEmail = "simon.stobart@sunderland.ac.uk";
$strSubject = "Sales Figures";
$strMessage = "
<html>
<head>
<style type='text/css'>
body {background-color: white}
tr {color: white;
    background-color: blue}
h1 {color: black}
</style>
</head>

<body>
<div align="center">
```