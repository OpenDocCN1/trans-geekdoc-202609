In addition, mail priority is not standardized in RFC 822. This can be recognized by the X- prefix of X-Priority. It is therefore at the discretion of the email program whether and how this mail header is interpreted. The following values for X-Priority seem to have become generally accepted:

+   - Low
+   - Normal
+   - High

Other entries, such as very high or very low, are only supported by specific email clients.

> **Tip**
> 
> You can also use the From:sender@xy.zzz header under Windows to overwrite the php.ini sendmail_from setting in Windows. In Unix/Linux, this is a convenient way to set the mail sender.

# 16.2.2 MIME Mails

So far, so good—and so simple. For emails that are sent from web applications (e.g., from contact forms), what has been written so far is usually sufficient. However, marketers in particular want emails to be colorful. And in fact, it is possible to enhance emails with HTML formatting and file attachments.

But one thing should be made clear right away: It is relatively time-consuming to create this type of mail. Most of the work can be saved by using external libraries. Nevertheless, we will demonstrate the basics, as this will show you what is and is not possible with dynamically generated emails.

> **Note**
> 
> At www.mhonarc.org/~ehhood/MIME/, there is a good overview of the various MIME standards, which are now filed under RFCs 2045 to 2049. MIME stands for Multipurpose Internet Mail Extensions and describes the structure of emails along with special formats and file attachments.

Composing a MIME mail requires two precautions:

+   - Setting special headers
+   - Special construction of the mail text

Let's start with the headers. The Content-Type entry determines the type of the content.² Various MIME types can be selected here:

2 Similar to the Content-type entry (with a small t) in the HTTP header.