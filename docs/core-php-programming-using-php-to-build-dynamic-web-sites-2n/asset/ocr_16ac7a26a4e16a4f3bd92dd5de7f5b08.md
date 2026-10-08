# Core PHP Programming

The imap_mail function is an alternative to the mail function. The difference is the arguments for specific headers.

# string imap_mail_compose(array envelope, array body)

The imap_mail_compose function returns a MIME message given arrays describing the envelope and body. The envelope argument may contain the following elements: bcc, cc, date, from, message_id, reply_to, return_path, to. The body argument may contain the following elements: bytes, contents.data, encoding, id, md5, subtype, type.

# boolean imap_mail_copy(integer stream, string list, string mailbox, integer flags)

The imap_mail_copy function copies messages into another mailbox. The list of messages can be a list of messages or a range. The optional flags argument is a bitfield that may be set with CP_UID, which specifies that the list contains UIDs, or CP_MOVE, which instructs the function to delete the original messages after copying. This last functionality may be accomplished with the imap_mail_move function.

```
<?
$mailbox = imap_open("{mail.server.com}INBOX", "leon", "password");
imap_mail_copy($mailbox, "OLD", "17");
imap_close($mailbox);

```

# boolean imap_mail_move(integer stream, string list, string mailbox)

The imap_mail_move function moves messages from the current mailbox to a new mailbox. The list of messages can be a list of messages or a range.

```
<?
$mailbox = imap_open("{mail.server.com}INBOX", "leon", "password");
imap_mail_move($mailbox, "OLD", "17");
imap_close($mailbox);

```

IT-SC book 475