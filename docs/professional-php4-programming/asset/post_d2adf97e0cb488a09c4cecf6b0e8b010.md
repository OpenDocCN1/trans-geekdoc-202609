

```php
$this->buildErrorMsg($this->ERR_STR_CANT_CREATE_MAILBOX,
    $this->new_mailbox);
    return false;
}
if (!@imap_createmailbox($this->stream, "{$this->host}
    $this->new_mailbox")) {
    $this->buildErrorMsg($this->ERR_STR_CANT_CREATE_MAILBOX,
        imap_last_error());
    return false;
}
return true;
}
```

## renameMailbox()

This method renames a mailbox using the values in the $old_mailbox and $new_mailbox properties:

```php
function renameMailbox()
{
    if ($this->protocol == 'nntp' || $this->protocol == 'pop3' ||
        $this->new_mailbox == 'INBOX') {
        $this->buildErrorMsg($this->ERR_STR_CANT_RENAME_MAILBOX,
            $this->new_mailbox);
        return false;
    }
    if (!@imap_renamemailbox($this->stream, "{$this->host}
        $this->old_mailbox", "({$this->host})$this->new_mailbox")) {
        $this->buildErrorMsg($this->ERR_STR_CANT_RENAME_MAILBOX,
            imap_last_error());
        return false;
    }
    return true;
}
```

## deleteMailbox()

This method deletes a mailbox using the value in the $del_mailbox property:

```php
function deleteMailbox()
{
    if ($this->protocol == 'nntp' || $this->protocol == 'pop3' ||
        $this->del_mailbox == 'INBOX') {
        $this->buildErrorMsg($this->ERR_STR_CANT_DELETE_MAILBOX,
            $this->del_mailbox);
        return false;
    }
    if (!@imap_deletemailbox($this->stream, "{$this->host}
        $this->del_mailbox")) {
        $this->buildErrorMsg($this->ERR_STR_CANT_DELETE_MAILBOX,
            imap_last_error());
        return false;
    }
    return true;
}
```

## Manipulating Messages

IMAP maintains status information on a message with a number of flags indicating each status. Deleting a message with IMAP, for example, is setting a \Deleted flag to it. Actual deletion occurs when you close the stream to the mailbox. You can delete a message (or mark it for deletion to be exact), by calling either imap_delete() or imap_setflag_full().

### imap_delete()

```c
int imap_delete(int stream, int msg_no [, int flags])
```

This function marks a given message for deletion. It returns true on success. The flags argument can be FT_UID to tell the function to treat the msg_no argument as a UID. To actually delete a message marked for deletion, you need to explicitly call the imap_expunge() function or imap_close() with the optional argument CL_EXPUNGE.

### imap_expunge()

```c
int imap_expunge(int stream)
```

The function wipes out all messages marked for deletion. The following code snippet deletes the message numbered 10:

```php
if (!imap_delete($stream, 10)) echo("Error deleting the message!");
else imap_expunge($stream); // same as imap_close($stream, CL_EXPUNGE)
```

Marking a message for deletion can also be achieved by calling the imap_setflag_full() function used to set one or more flags to a message.

### imap_setflag_full()

```c
string imap_setflag_full(int stream, string msg_set, string flag, int flags)
```

The function sets one or more flags to a specified message. The msg_set string argument can be in any of the following formats:

- A single digit: 5
- A comma separated string of message sequence numbers with no whitespace: 1,2,3,4
- A colon separated range of message sequence: 2:10
- A combination of the above: 1,2,5:10
- "*" wildcard: 1: * for all of the messages starting from message number 1

Note that you need to escape a flag to be set: "\\Deleted" for example. Multiple flags can be set by separating them with whitespace: "\\Seen \\Answered \\Flagged", for example.

If you pass ST_UID for the fifth optional flags argument, the msg_set argument is treated as containing UIDs. Recall that a set of message numbers can be specified as a range.

The following function call causes every message numbered 10 or above to be "\\Seen" and "\\Flagged":

```php
imap_setflag_full($stream, "10:*", '\\Seen \\Flagged');
```

If you change your mind after marking a message for deletion with the imap_delete() function, you can either call imap_undelete() or imap_clearflag_full() to clear the message of the "\\Deleted" flag.

### imap_undelete()

```c
int imap_undelete(int stream, int msg_no)
```

Clears the message of the "\\Deleted" flag. imap_clearflag_full() can also be used for the purpose.

### imap_clearflag_full()

```c
string imap_clearflag_full(int stream, string msg_set,
string flag, int flags)
```

Clears the message of the specified flag(s). If given ST_UID for the fourth argument, the function treats the msg_set argument as containing UIDs.

The following two function calls achieve exactly the same goal of undeleting message number 10 marked for deletion:

```php
imap_undelete($stream, 10);
```

Or:

```php
imap_clearflag_full($stream, 10, "\\Deleted");
```

Most MUAs provide a "Deleted" or "Trash" mailbox instead of actually removing messages. We can mimic this feature by moving a message to ‘mailbox containing all the deleted messages when the user requests for its deletion. If the current mailbox is the one holding deleted messages, that’s when we wipe them out for good. imap_mail_move() and imap_mail_copy() can come in handy for this purpose.

### imap_mail_move() and imap_mail_copy()

```c
int imap_mail_move(int stream, string msg_set, string mailbox [, int flags])
```

The imap_mail_move() function moves messages given as a range to a specified mailbox. The flags argument can be CP_UID to tell the function to treat the msg_set argument as having UIDs. The function returns true on success and false on error.

A moved message will be still there unless you call imap_expunge() or imap_close() with the CL_EXPUNGE option. In fact, you don't need to call imap_mail_move() at all – imap_mail_copy() includes the same feature:

```c
int imap_mail_copy(int stream, string msg_set, string mailbox [, int flags])
```

The function also returns true on success or false on error. It copies a given range of messages to a specified mailbox. If you set the flags argument to CP_MOVE, it marks copied messages in the source mailbox for deletion. The following two function calls are functionally equivalent:

```php
imap_mail_move($stream, "5:10", "{mail.whatever.com}work");
imap_mail_copy($stream, "5:10", "{mail.whatever.com}work", CP_MOVE);
```

The last function we'll be looking at is imap_append() which lets you append an e-mail message to a mailbox.

### imap_append()

```c
int imap_append (int stream, string mbox, string msg [, string flags])
```

The function appends a given string containing an e-mail message to a specified mailbox, returning true on success or false on error. The flags string can be specified to set one or more flags to the appended message.

The function is useful when you want to implement the "Sent" or "Deleted" mailbox feature. A sent message can be deposited to a "Sent" mailbox of your choice using this function.

## Manipulating Messages Using Webmail Class

Let's teach our Webmail class how to manipulate messages by updating the previous Webmail class.

### New Properties

We just throw in a bunch of custom error messages again:

```php
//webmail_class_final.php

var $ERR_STR_CANT_DELETE_MESSAGE = "Can't delete the message!";
var $ERR_STR_CANT_UNDELETE_MESSAGE = "Can't undelete the message!";
var $ERR_STR_CANT_COPY_MESSAGE = "Can't copy the message!";
var $ERR_STR_CANT_MOVE_MESSAGE = "Can't move the message!";
var $ERR_STR_CANT_SET_FLAGS = "Can't set the flags!";
var $ERR_STR_CANT_UNSET_FLAGS = "Can't unset the flags!";
```

### appendMail()

This method appends a given e-mail message to a specified mailbox:

```php
function appendMail($mail_str, $mailbox)
{
    if (!imap_append($this->stream,
        "\\{$this->host}mailbox", $mail_str)) {
        $this->buildErrorMsg(imap_last_error());
        return false;
    } else return true;
}
```

### deleteMailMsg()

This method marks a given range of messages for deletion. Note that we don't use the `imap_delete()` function since we would have to call it multiple times to delete several messages:

```php
function deleteMailMsg($msg_set)
{
    if (!@imap_setflag_full($this->stream,
        $msg_set, "\\Deleted", ST_UID)) {
        $this->buildErrorMsg($this->ERR_STR_CANT_DELETE_MESSAGE,
            imap_last_error());
        return false;
    }
    return true;
}
```

### undeleteMailMsg()

Clears the given range of messages of the "\\Deleted" flag:

```php
function undeleteMailMsg($msg_set)
{
    if (!@imap_clearflag_full($this->stream, $msg_set,
        "\\Deleted", ST_UID)) {
        $this->buildErrorMsg($this->ERR_STR_CANT_UNDELETE_MESSAGE,
            imap_last_error());
        return false;
    }
    return true;
}
```

### copyMailMsg()

Copies a given range of messages to a new mailbox:

```php
function copyMailMsg($msg_set)
{
    if (!@imap_mail_copy($this->stream, $msg_set, "{$this->server}{$this->new_mailbox}", CP_UID)) {
        $this->buildErrorMsg($this->ERR_STR_CANT_COPY_MESSAGE,
            imap_last_error());
        return false;
    }
    return true;
}
```

