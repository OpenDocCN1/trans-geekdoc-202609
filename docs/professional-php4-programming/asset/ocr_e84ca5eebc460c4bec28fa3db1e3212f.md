If the user is replying to an e-mail message, remove the original message and set header values accordingly:

```
if ($mode == 'reply') {
    $msg = $this->getMsg('', '');
    if (!$msg) $mail_to = $email;
    else {
        $mail_date = $msg["date"];
        $mail_to = $msg["raw_from"];
        $mail_cc = $msg["raw_cc"];
        $mail_subject = "Re: " . $msg["subject"];
        $mail_body = "--- Original Message($mail_date) ---\r\n" .
            eregi_replace("<br>", "\r\n", $msg["body"]);
    }
}
```

The user wants to forward the current e-mail message. Retain the From header and prepend a string "Fwd:" to the Subject header:

```
} else if ($mode == 'forward') {
    $msg = $this->getMsg('', '');
    if (!$msg) return false;
    $mail_from = $msg["raw_from"];
    $mail_date = $msg["date"];
    $mail_subject = "Fwd: " . $msg["subject"];
    $mail_reply_to = $mail_from;
    $mail_body = "--- Original Message($mail_date) ---\r\n" .
        eregi_replace("<br>", "\r\n", $msg["body"]);
}
```

The user wants to post a news article, switch the $is_news flag on:

```
} else if ($mode == 'article') {
    $mail_to = $this->mailbox;
    $is_news = true;
}
```

In case the user replies to a news article, we also need to set the References header. Obtain the original References header value and add the current article's Message-ID header:

```
} else if ($mode == 'followup') {
    $mail_to = $this->mailbox;
    $msg = $this->getMsg('', '', $y;
    $mail_references = $msg["references"] . " "
        . $msg["message_id"];
    $mail_subject = "Re: " . $msg["subject"];
    $is_news = true;
}
```

```
$ret_str = "<form name=\"MAIL_FORM\" action=\"$PHP_SELF\"
method=\"POST\" enctype=\"MULTIPART/FORM-DATA\">\n";
$ret_str .= "<input type=\"HIDDEN\" value=\"mail\"
name=\"action\">\n";
$ret_str .= "<input type=\"HIDDEN\" value=\"$mode\"\\
```