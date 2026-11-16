
Set both the sequence number and UID of the message:

```
$msg = @imap_header($this->stream, $msg_no);
$arr[$i]["no"] = $msg_no = $msgs[$i];
$arr[$i]["uid"] = $msg_uid = imap_uid($this->stream, $msg_no);
```

Has the message been read?

```
if ($msg->Unseen == 'U' || $msg->Recent == 'R') {
    $arr[$i]["unseen"] = true;
} else {
    $arr[$i]["unseen"] = false;
}
```

The Date header value is too long to fit in a table cell. Trim it. The strtotime() function returns a UNIX timestamp given a date string:

```
$arr[$i]["date"] = gmstrftime("%b %d %Y",
    strtotime($msg->date));
```

Fetch meta data for the current message:

```
$struct = @imap_fetchstructure($this->stream, $msg_no);
```

The first element in the parts property of the returned object is the message's textual body. If it contains more than one element, that means the message has attachment(s), in which case, an ampersand (@) is prepended to its subject:

```
$num_parts = count($struct->parts) - 1;
if ($num_parts > 0) $msg_prefix = "@";
else $msg_prefix = '';
```

Decode MIME headers if necessary. The decodeHeader() method returns a decoded header value if it contains a non-ASCII value:

```
if (empty($msg->subject)) {
    $arr[$i]["subject"] = $this
        ->buildUrl("read_action&msg_uid=$msg_uid&mailbox="
        .$this->mailbox,$this->STR_NO_SUBJECT);
} else {
    $msg_subject = $this->decodeHeader($msg->subject);
    $arr[$i]["subject"] = $this->
        buildUrl("read_action&msg_uid=$msg_uid&mailbox="
        .$this->mailbox, "$msg_prefix$msg_subject");
}
```

The makeAddress() method takes an array of objects containing e-mail address properties and converts each e-mail address into a link using the second argument as a reference:

```
if (empty($msg->from)) {
    $arr[$i]["from"] = $this->STR_NO_FROM;
} else {
    $arr[$i]["from"] = $this->makeAddress($msg->from,
        "Mail_action&msg_uid=$msg_uid&mailbox=$this->mailbox");
}
}
return $arr;
}
```

The getMsg() method is used to read a message or article. We'll build this method in the next section.

### makeAddress()

The makeAddress() function returns a string of e-mail addresses with each address separated by a comma. If given the $action argument, it converts each address into a link using the argument:

```
function makeAddress($emails, $action)
{
    if (!is_array($emails)) return;
    foreach ($emails as $email) {
```

The From header may also contain encoded text:

```
$personal = $this->decodeHeader($email->personal);
$address = $email->mailbox . "@" . $email->host;
if (!empty($personal)) {
    $arr[] = $this->buildUrl("$action&email=$address",
        $personal);
} else {
    $arr[] = $this->buildUrl("$action&email=$address",
        $address);
}
}
return implode(',', $arr);
}
```

### decodeHeader()

The decodeHeader() method returns a decoded header value:

```
function decodeHeader($arg)
{
    $dec_array = imap_mime_header_decode($arg);
```

Only the text property of the returned object is used:

```
foreach ($dec_array as $obj) $arr[] = $obj->text;

if (count($arr) >0) return implode('', $arr);
else return $arg;
}
```

### buildUrl()

The buildUrl() method is a utility returning a URL calling the current script. For example the $onclick argument is used to provide JavaScript functionality:

```
function buildUrl($options, $link, $onclick='')
{
    global $PHP_SELF;

    if (!empty($onclick)) $onclick = " OnClick=\"$onclick\"";
    return "<a href=\"$PHP_SELF?$options\"$onclick>$link</a>" ;
}
```

## Testing the Webmail Class

You can now instantiate the Webmail class and connect to either a mail or news server and list messages or articles. The following script connects to news.php.net and lists articles posted on the php.test newsgroup. It takes a while for the server to come up:

```
<?php
// webmail_class_test2.php

include "./webmail_class_ver2.php";
class My_Webmail extends Webmail
{
    function start()
    {
        $msgs = $this->getMsgList('readMsg', 'mailForm');
        if (!$msgs) return false;
        $ret_str = '';
        foreach ($msgs as $msg)
            $ret_str .= $msg["subject"] . " - " . $msg["from"] . "<br>";
        return $ret_str;
    }
}

$host = "news.php.net";
$protocol = "nntp";
$port = 119;
$userid = "";
$userpassword = "";
$mailbox = 'php.test';

$wmail = new My_Webmail();

if (!$wmail->init($host, $protocol, $port, $userid, $userpassword)) {
    echo($wmail->errorMsg());
}
$list = $wmail->start();

if (!$list) {
    echo($wmail->errorMsg());
} else echo($list);

$wmail->end();
?>
```

Here's a sample run:

![](img/9cf7789dba9b16ef3f8576d5aea89186_430_0.png)

We can see a bunch of test articles posted on the php.test newsgroup. Now, let's read them.

## Retrieving Messages

After analyzing the structure of a message, you can extract any part of it by calling the imap_fetchbody() function.

### imap_fetchbody()

```
string imap_fetchbody(int stream, int msg_no, string part_no [, int flags])
```

With IMAP, you can fetch portions of the full message text. It is possible to fetch the message header or body block, a body part, or a body part header block with the imap_fetchbody() function.

The part_no string argument denotes exactly which portion of the message the function should fetch. An empty string will get you the whole message body text. Every body part is assigned a part number with the message header block given 0, message body 1, and so on. You may fetch the full text of each body part by specifying its part number. To fetch its header block or only its headers (HEADER), MIME headers (MIME), or text body (TEXT), you need to specify a part number using a period: 1.TEXT, for example.

Note that part number 1 matches the textual body of a given message. The first body of binary data can be fetched by setting the part number to 2. The part number 0 fetches the header block of the message:

> As of this writing, PHP imap_fetchbody() doesn't work reliably when given a part specification string such as "1.HEADER". Setting the part_no argument to the desired body part number will get you the body text.

Note that although you can fetch a body of encoded binary data with this function, the fetched body is not decoded in any way.

The fourth argument can be one or more of the following:

- FT_UID
  Treat the msg_no argument as UIDs.
- FT_PEEK
  Don't set the \Seen flag if not already set.
- FT_INTERNAL
  Do not convert a single newline character (\n) to a CRLF pair. Return the string as it is.

The imap_body() function returns both the header and body block as they are. It may be useful only for viewing a verbatim copy of a message:

```
string imap_body(int stream, int msg_no [, int flags])
```

The flags argument has the same meaning as that of the imap_fetchbody(). We'll be using the imap_fetchstructure() and imap_fetchbody() functions to analyze and read a message.

Each body part of a message may contain MIME encoded non-textual data, which should be decoded to be displayed or downloaded in its original state. We use imap_base64() and imap_qprint() for this purpose depending on the method of encoding applied to the part.

### imap_base64() and imap_binary()

```
string imap_base64(string var)
```

The function returns decoded data from base64-encoded text:

```
string imap_binary(string var)
```

The imap_binary() function does the opposite by returning binary encoded data:

### imap_qprint() and imap_8bit()

```
string imap_qprint(string var)
```

To decode quoted-printable encoded data, the imap_qprint() function is used:

```
string imap_8bit(string var)
```

The imap_8bit() function does the opposite by returning 8bit encoded data.

There are more encoding/decoding functions available. Refer to Appendix A (http://p2p.wrox.com/content/phpref/) or the PHP online manual for a complete list of encoding and decoding functions.

## Reading Messages Using Webmail Class

We'll add two additional methods for reading a message and downloading body parts: getMsg() and downloadAttachment(). A number of properties are also added.

### New Properties

The $msg_no and $msg_uid properties keep track of the message sequence number and UID respectively, while $part_no contains the number of the body part to work with. Recall that the first attachment is held as the second body part with the first being the textual body itself:

```
// webmail_class_ver3.php
class Webmail
{
    var $msg_no = 0;
    var $msg_uid = 0;
    var $part_no = 0;
}
```

The $filename property is used to let the browser know the name of the file it is to deal with. Feeding the value to the Content-Disposition header field causes the browser to use the given name instead of the name of the script when saving the data:

```
var $filename = '';
```

A couple of new custom message strings:

```
var $ERR_STR_MSG_NO_INVALID = 'Invalid Message Number!';
var $ERR_STR_MSG_UID_INVALID = 'Invalid Message UID!';
```

### init()

We need a few additional global variables corresponding to the newly defined properties:

```
function init()
{
    $this->msg_no = $GLOBALS["msg_no"];
    $this->msg_uid = $GLOBALS["msg_uid"];
    $this->filename = $GLOBALS["filename"];
    $this->part_no = $GLOBALS["part_no"];
}
```

### getMsg()

This method returns a string containing a summary of the header block followed by the message body. If the textual message body is encoded, it is decoded first. If attached files are found, it also adds links enabling the user to download them:

```
function getMsg($download_action, $mail_action)
{
```
