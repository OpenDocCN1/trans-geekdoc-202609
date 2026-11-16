A server response code consists of three digits and the rest is a comment string that follows it. We're giving enough room (1024 bytes) to read in the whole response:

```
if (eregi("^([0-9]{3}) (.* )", $server_response, $match)) {
    $this->response_code = $match[1];
    $this->response_msg = $match[2];
    return true;
}
$this->response_msg = $server_response;
return false;
}
```

# talk()

The talk() method is the primary workhorse of the class implementing an SMTP session to send an e-mail message. It takes an SMTP command and an optional data string that contains either the SMTP command's argument or e-mail data:

```
function talk($cmd, $arg='')
{
}
```

Check to see if the connection is still alive:

```
if (!$this->socket) {
    $this->ERROR_MSG = $this->ERR_SMTP_NOT_CONNECTED;
    return false;
}
```

Send the given SMTP command and get the server response:

```
switch ($cmd) {
}
```

First, send the HELO command:

```
case "HELO":
    if (empty($arg)) {
        $this->ERROR_MSG = $this->ERR_HELO_WITHOUT_ARG;
        return false;
    }
    $smtp_cmd = "HELO $arg\r\n";
    fwrite($this->socket, $smtp_cmd);
    if (!$this->getResponse()) {
        $this->ERROR_MSG = $this->ERR_UNKNOWN_RESPONSE_FROM_SERVER . ":". $this->response_msg;
        return false;
    }
}
```

If the server response code starts with 250, the command was successful:

```
if ($this->response_code != 250) {
    $this->ERROR_MSG = $this->ERR_HELO_FAILED . " ".
    $this->response_code . " " . $this->response_msg;
    return false;
}
break;
```