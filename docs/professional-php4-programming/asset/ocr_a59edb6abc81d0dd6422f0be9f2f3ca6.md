+   NNTP-Posting-Host
+   The name of the host used to post the article. It is automatically added by the server. For example, news.whatever.com.

Other optional headers that are heavily used include:

+   Reply-To
+   The e-mail address to which any replies to the article should be sent. In its absence, all e-mail replies are sent to the address in the From header.

+   References
+   A list of message IDs, separated by whitespace, of previous articles to which the current article is a follow-up. The header plays a key role in creating a threaded list of messages belonging to a newsgroup. For example, References: <95kvcb$qcn$3@toye.p.sourceforge.net> <390F4E9C.80D6BBCB@whatever.net>.

+   Approved
+   The e-mail addresses of those in charge of approving the article for posting in a moderated newsgroup.

+   Lines
+   The number of lines in the body of the article.

+   Organization
+   The name of the author's organization.

We're not going to cover all the details on a news article here. Only a few headers are needed to post an article to a newsgroup. Others are either informational ones or control messages for the news server. For a complete discussion, refer to RFC 1036.

Without further ado, let's see how we can create an NNTP class that helps you post an article to a selected newsgroup.

# Creating an NNTP Class

The NNTP class we'll be creating is basically the same in appearance as the SMTP class built earlier, but we need new versions of the buildHeaders() and talk() methods. We can do without some of the e-mail headers but a couple of new headers need to be added. The new talk() method parses NNTP server response codes. We can extend the My_Smtp_Mime_Mail class to create My_Nntp class.

# Properties

```
<?php
// my_nntp_class.php

include("./my_smtp_mime_mail_class.php");

class My_Nntp extends My_Smtp_Mime_Mail
{
```