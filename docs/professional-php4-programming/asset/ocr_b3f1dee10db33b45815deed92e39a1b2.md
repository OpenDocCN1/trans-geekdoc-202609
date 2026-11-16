The viewMsg() method is supposed to be called after you send e-mail. It initializes the $headers property and rebuilds the header block:

```
$this->headers = array();

$this->buildHeaders();

$this->headers[] = "From: $this->from";
$this->headers[] = "To: $this->to";
$this->headers[] = "Subject: $this->subject";

$msg = implode("\r\n", $this->headers);
$msg .= "\r\n\r\n";
$msg .= $this->body;

return $msg;
}
```

# send()

The send() method calls checkFields() to validate headers and e-mail addresses used, and then, buildHeaders() to construct additional headers. Finally, it calls the mail() function to pass the message to the local MTA (or a remote SMTP server if PHP is configured to use one). It returns true on success, and false upon error:

```
function send()
{
    if (!$this->checkFields()) return true;

    $this->buildHeaders();

    if (mail($this->to, stripslashes(trim($this->subject)),
        stripslashes($this->body), implode("\r\n", $this->headers)))
        return true;
    else {
        $this->ERROR_MSG = $this->ERR_SEND_MAIL_FAILURE;
        return false;
    }
}
```

# errorMsg()

It is always a good practice to include an error reporting method in your class instead of echoing out error messages directly. If you want to change the way errors are reported, for example, you have only one place to look into: the errorMsg() method in this case. The method returns $ERROR_MSG, or $STR_NO_ERROR if $ERROR_MSG is empty indicating that no reportable error has occurred:

```
function errorMsg()
{
    if (empty($this->ERROR_MSG)) return $this->STR_NO_ERROR;
        return $this->ERROR_MSG;
}

?>
```