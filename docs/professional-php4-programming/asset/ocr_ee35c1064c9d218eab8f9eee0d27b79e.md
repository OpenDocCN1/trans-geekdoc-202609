The $download_action argument contains a link to use when downloading a body part while $mail_action holds a link to a mail composition form:

```
if (!$this->msg_uid) {
    $this->buildErrorMsg($this->ERR_STR_MSG_UID_INVALID,
        imap_last_error()));
    return false;
}

$msg_no = imap_msgno($this->stream, $this->msg_uid);
```

Get an object containing a summary of the header block:

```
$headers = @imap_header($this->stream, $msg_no);
if (!$headers) {
    $this->buildErrorMsg($this->ERR_STR_MSG_NO_INVALID,
        imap_last_error()));
    return false;
}
```

Format the Date header value:

```
$arr["date"] = gmstrftime("%b %d %Y %H:%M:%S", strtotime
    ($headers->date));
```

Make e-mail addresses clickable retaining their original format in another array element:

```
$arr["raw_from"] = $this->decodeHeader($headers->fromaddress);
$arr["raw_cc"] = $this->decodeHeader($headers->ccaddress);
$arr["from"] = $this->makeAddress($headers->from,
    "mail_action&msg_uid=$this->msg_uid&mailbox=$this->mailbox");
$arr["cc"] = $this->makeAddress($headers->cc,
    "mail_action&msg_uid=$this->msg_uid&mailbox=$this->mailbox");
```

Try decoding the Subject header:

```
$arr["subject"] = $this->decodeHeader($headers->subject);
if (empty($arr["subject"])) $arr["subject"] = $this->STR_NO_SUBJECT;
```

We also need the Message-ID and References header values for news articles:

```
$arr["message_id"] = $headers->message_id;
$arr["references"] = $headers->references;
```

Get an object containing meta data on the message:

```
$struct = @imap_fetchstructure($this->stream,
    $this->msg_uid, FT_UID);
```