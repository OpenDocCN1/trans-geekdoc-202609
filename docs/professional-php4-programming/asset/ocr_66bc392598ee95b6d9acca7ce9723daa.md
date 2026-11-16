You use the FETCH command to read a message. Let's read the fifth message in INBOX using the FETCH command. It takes multiple arguments with the first one being the message number. The rest of the arguments may vary depending on what you want to do with the command:

```
WCK003 FETCH 5 BODY[1]
* 5 FETCH (BODY[1] {61}
Don't forget to bring your notebook tomorrow.
Sleep tight.
)
WCK003 OK FETCH completed
```

With the BODY argument you may specify which part of the message you wish to retrieve: BODY[0] for the headers, or BODY[1] for the message body, for example. Let's see what headers look like in this message:

```
WCK003 FETCH 5 BODY[0]
* 5 FETCH (BODY[0] {452}
Return-Path: <wankyu@whatever.com>
Received: from whatever.com (IDENT:wankyu@whatever.com[192.168.0.2])
    by mail.somewhere.com (8.9.3/8.9.3) with SMTP id WAA29446
    for yonsuk; Sun, 28 Jan 2001 23:18:09 +0900
Date: Sun, 28 Jan 2001 23:18:09 +0900
From: Wankyu Choi <wankyu@whatever.com>
To: yonsuk@whoelse.com
Message-Id: < F890755DE93ED411@ whatever.com>
Subject: Just a Note
)
WCK004 OK FETCH completed
```

You can even get a summary of the message structure with the BODYSTRUCTURE argument:

```
WCK005 FETCH 5 BODYSTRUCTURE
* 5 FETCH (BODYSTRUCTURE ("TEXT" "PLAIN" ("CHARSET" "US-ASCII") NIL NIL "7BIT" 61
2 NIL NIL NIL))
WCK005 OK FETCH completed
```

Flags are retrieved much the same way:

```
WCK006 FETCH 5 FLAGS
* 5 FETCH (FLAGS (\Seen))
WCK006 OK FETCH completed
```

Now you know the fifth message has been read (\Seen). You may combine these into a single command by surrounding arguments with parentheses:

```
WCK007 FETCH 5 (BODYSTRUCTURE FLAGS)
* 5 FETCH (BODYSTRUCTURE ("TEXT" "PLAIN" ("CHARSET" "US-ASCII") NIL NIL "7BIT" 61
2 NIL NIL NIL) FLAGS (\Seen))
WCK007 OK FETCH completed
```