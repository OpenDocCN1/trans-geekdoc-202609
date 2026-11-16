As you can see in its greeting, the MTA we connected to can talk ESMTP, Extended Simple Mail Transfer Protocol, which extends the basic SMTP commands with additional ones. Since ESMTP commands are a superset of SMTP commands, all the commands we use to send e-mail talking directly to the server will still work.

When connected to an MTA, you issue the HELO command, with your domain name as its argument, to inform the server where you're coming from. It's an optional command, but when omitted, the MTA might attach a warning to the outgoing message that you were rude enough not to say hello to it. To tell the server who is sending the e-mail message, the MAIL FROM command is used followed by a colon, a whitespace, and the sender's e-mail address. The RCPT TO line designates who should get the e-mail. It is the DATA command that lets you compose a message, which is considered terminated by a period on a line by itself. The QUIT command ends the conversation with the server, and the connection drops.

A server response starts with three digits, called a response code, followed by a comment string. It is this response code you need to pay close attention to when parsing a server response. We'll get back to server response codes when we talk about sending e-mail using a remote SMTP server.

Now that you know how an e-mail message gets delivered and retrieved, let's see what it actually looks like.

# # E-Mail Unveiled

An e-mail message is nothing but a simple text file. No matter what it contains, it doesn't get beyond that. E-mail is a series of text lines terminated by a pair of CR/LF characters.

> UNIX uses a single linefeed character (\n) to end a text line whereas Windows uses both carriage return (\r) and linefeed (\n) to do the job. Therefore, it may be OK to use a single linefeed (\n) when composing an e-mail message within PHP on UNIX, but it may not be parsed correctly on Windows. For all practical purposes, stick to the standard: use both CR and LF (\r\n) when building a message.

To start with, let's refresh your memory of what a typical e-mail looks like:

```
Return-Path: <wankyu@whatever.com>
Received: from whatever.com (IDENT:wankyu@whatever.com[192.168.0.2])
 by mail.somewhere.com (8.9.3/8.9.3) with SMTP id WAA29446
 for yonsuk; Sun, 28 Jan 2001 23:18:09 +0900
Date: Sun, 28 Jan 2001 23:18:09 +0900
From: Wankyu Choi <wankyu@whatever.com>
To: yonsuk@whatever.com
Message-Id: <F890755DE93ED411@whatever.com>
Subject: Just a Note

Don't forget to bring your notebook tomorrow.
Have a nice read.
```