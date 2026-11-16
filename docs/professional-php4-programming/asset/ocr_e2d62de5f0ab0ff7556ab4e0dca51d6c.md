Specify the remote NNTP server and the port number it listens on:

```
var $nntp_host = '';
var $nntp_port = 119;
```

We also need a placeholder for the newsgroup(s) the article should be posted to. Multiple newsgroups are separated by a comma:

```
var $newsgroups = '';
```

The References header placeholder:

```
var $references = '';
```

Additional custom error message strings:

```
var $ERR_NNTP_HOST_NOT_SET = 'NNTP host not set!';
var $ERR_NNTP_CONNECTION_FAILED = 'Failed to connect to the specified
NNTP host!}';
var $ERR_NNTP_NOT_CONNECTED = 'Establish a connection to an NNTP server
first!!'};

var $ERR_EMPTY_FROM = "Empty From header!";
var $ERR_EMPTY_NEWSGROUPS = "No newsgroup(s) specified!";

var $ERR_GROUP_WITHOUT_ARG = 'GROUP command needs an argument!}';
var $ERR_POST_WITHOUT_ARG = 'POST command with empty article content!}';

var $ERR_UNKNOWN_RESPONSE_FROM_SERVER = 'Unknown response from the
server!'}';
var $ERR_POSTING_NOT_ALLOWED = "Posting not allowed on this server!";
var $ERR_GROUP_POSTING_NOT_ALLOWED = "Posting not allowed on this
newsgroup!}';
var $ERR_GROUP_FAILED = 'GROUP command failed!}';
var $ERR_NO_SUCH_GROUP = 'No such group!}';
var $ERR_POST_FAILED = 'POST command failed!}';
var $ERR_QUIT_FAILED = 'QUIT command failed!}';

```

# connect()

This method establishes a connection to your NNTP server setting the $socket property. Note that you should have permissions to connect to the server. Most NNTP servers authenticate accesses by checking your IP address to determine whether you're coming from a valid domain. The method also tests to see if posting is allowed on the specified news server. The response code 201 means posting is not allowed, in which case it returns false after setting the internal error message property to that effect:

```
function connect()
{
    if (empty($this->nntp_host)) {
        $this->ERROR_MSG = $this->ERR_NNTP_HOST_NOT_SET;
        return false;
    }
```