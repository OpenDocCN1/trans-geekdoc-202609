There is a variant of the mbox format called MMDF, where each message is surrounded by lines containing four ctrl-As (^^A^^A^^A), without any blank line separating each message.

As the number of your e-mail messages stored in your mailbox grows, a single text file model becomes way too inefficient to access and manage. Also, no two clients can access the same mailbox concurrently: one may lose its lock on the mailbox when another attempts to access it. To avoid this file-locking problem, every e-mail message needs to be stored as a separate file. The MH mailbox format consists of directories and each message is stored in a separate file. Most NNTP servers use a similar format to MH to manage news articles.

IMAP lets you create a hierarchy of multiple mailboxes in much the same way you manipulate file directories. Formats of the mailbox hierarchy vary depending on server implementations, but the simplest form is a mail file system format. In this format, each mailbox can be mapped to a directory or file. INBOX is always a directory.

Note that UW-IMAP server eventually appends messages to a single mbox format mailbox, whereas Cyrus server maintains every message as a separate file in a mailbox directory. Courier-IMAP server is unique in that it supports Qmail's Maildir mailbox format. With UW-IMAP, no two clients can access the same mailbox concurrently: that is, one may lose its lock on the mailbox if the other attempts to access it at the same time. Cyrus and Courier-IMAP servers don't suffer from this file-locking problem.

# # Example IMAP Session

An IMAP session is comprised of four distinct states. Since it supports multiple mailboxes, you need to select one to work with before you can access messages in it:

+   Non-authenticated state: the client is connected to the server

+   Authenticated state: the client is successfully authenticated

+   Selected state: a mailbox has been successfully selected

+   Logout state: the client issued the LOGOUT command or the server closed the connection

Let us now telnet to our localhost running an IMAP server:

```
# telnet localhost imap
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
* OK [CAPABILITY IMAP4 IMAP4REV1 LOGIN-REFERRALS AUTH=LOGIN] localhost IMAP4rev1
2000.287 at Tue, 30 Jan 2001 16:15:07 +0900 (KST)
```

The server greets you with an untagged response (note the asterisk at the start of the response).

You need to login if you want to do anything meaningful with the server. The LOGIN command is used with two arguments: your account name, also considered your mailbox name, and password. Remember that you need to prepend a tag string to each command:

```
WCK001 LOGIN wankyu 12345
* CAPABILITY IMAP4 IMAP4REV1 NAMESPACE IDLE MAILBOX-REFERRALS SCAN SORT THREAD=REFERENCES THREAD=ORDEREDSUBJECT MULTIAPPEND
WCK001 OK LOGIN completed
```