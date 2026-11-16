Setting the $auto_expunge property to true causes the imap_close() function call to expunge any messages marked for deletion:

```
var $auto_expunge = true;
```

We need a whole new set of custom messages. Note the $ERR_ARGS_DELIMITER property is used to delimit an error message and a following argument:

```
var $ERR_ARGS_DELIMITER = " ";
var $ERROR_MSG = '';

var $ERR_STR_CONNECTION_FAILED = 'Connection failed!';
var $ERR_STR_PROTOCOL_NOT_SUPPORTED = 'Protocol not supported!'';
var $ERR_STR_CLOSE_FAILED = 'Error closing the stream!'';
var $ERR_STR_MAILBOX_NOT_AVAILABLE = 'Mailbox not available!'';
var $ERR_STR_OVERRIDE_START = "Override start() method!";
```

# init()

The init() method initializes the class setting internal properties to given arguments:

```
function init($host, $protocol='imap', $port=143,
	$userid='', $userpassword='')
{
	$this->host = $host;
	$this->protocol = $protocol;
	$this->port = $port;
	$this->userid = $userid;
	$this->userpassword = $userpassword;
}
```

The $mailbox property value is fetched from the global namespace:

```
$this->mailbox = $GLOBALS["mailbox"];
```

If the specified protocol is not an element of the $supported_protocols array, it is deemed invalid:

```
if (!in_array($this->protocol, $this->supported_protocols)) {
	$this->buildErrorMsg($this->ERR_STR_PROTOCOL_NOT_SUPPORTED,
		$this->protocol);
	return false;
}
```

If the NNTP protocol is to be used and the mailbox property is empty, an IMAP stream should be opened without selecting a mailbox by setting the fourth argument of the imap_open() function to OP_HALFOPEN. If the $mailbox property has a value, however, it is used as a newsgroup name:

```
if ($this->protocol == 'nntp' && empty($this->mailbox)) {
	$mode = OP_HALFOPEN;
} else $mode = false;
```