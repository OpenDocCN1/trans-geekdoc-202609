Here's a sample MIME e-mail with a binary file attached:

```
Return-Path: <yonsuk@whoelse.com>
Received: from whoelse.com (IDENT:yonsuk@whoelse.com[192.168.0.2])
        by mail.whatever.com (8.9.3/8.9.3) with SMTP id VAA30663
        for wankyu; Mon, 29 Jan 2001 15:21:59 +0900
Date: Mon, 29 Jan 2001 15:21:50 +0900
From: Yonsuk Song <yonsuk@whoelse.com>
To: wankyu@whatever.com
Subject: My Picture!
Message-Id: <200101291215.VAA30663@whatever.com>
MIME-Version: 1.0
Content-Type: multipart/mixed; boundary="01fedcb871d3f012e43680250ba5ca3f"

This is a multi-part message in MIME format.

--01fedcb871d3f012e43680250ba5ca3f
Content-Type: text/plain; charset=us-ascii

Here goes my picture. Send me yours!

Yours faithfully,
Yonsuk Song

--01fedcb871d3f012e43680250ba5ca3f
Content-Type: image/gif; name="yonsuk.gif"
Content-Transfer-Encoding: base64

R0lGODlhZACWAQf/AP///oPKs1paWq2trbW1td7e3ufn5+/v7/f3987Gxufe
3r21tbWtrZSMjPfWtlatrWNKSQvjY95jWq05Mb0xKc4xIc4QANaUjNZaSr0x
.......
g7+Uy88Q7MgHOc81833oayb6b6DHG3p+fvSnX/lvsHTIH44Aylc++5e/fv1l
3v0jr/7x28fFZ0ICADs=
--01fedcb871d3f012e43680250ba5ca3f--
```

The header fields in bold typeface are MIME-specific. It is essential to have a firm grasp of these headers if you want to put MIME into your arsenal of knowledge.

# # MIME Header Fields

A MIME e-mail message may contain more than one body part; the textual message body you usually see in your e-mail client and encoded image data attached to the message, for example.

In some contexts, the header block is also considered a body part. For example, a function may see your e-mail message as a whole and the header block is interpreted as the body part 0 with the textual message body given the part number 1, the first attached file number 2, and so on. Another function may deal only with the body block, in which case, the textual data is given the part number 0.

MIME header fields are specified the same way as the others previously seen. They may appear in the header block or just before a body part starts. If a MIME header appears in a body part, it only covers that part. You may think of those showing up in the header block as having a global scope and the rest appearing before body parts a local scope.