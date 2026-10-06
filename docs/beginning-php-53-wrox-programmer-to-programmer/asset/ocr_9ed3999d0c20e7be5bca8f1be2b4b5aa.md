# Part III: Using PHP Practice

How about if you're running on a Windows server? In that case you're in luck. Because PHP doesn't use an MTA and instead connects directly to an SMTP server, you can easily set the return path via a .php ini setting sendmail_from:

```
ini_set("sendmail_from", "bob@example.com");
mail("Jim Smith <jim@example.com>", "Hello", $message,"From: Bob Jones <bob@example.com>", $message);
```

# Sending HTML Emails

Your message body doesn't have to be plain text; you can send an HTML web page as well and more attractively. This allows you to format your message however you need to bear in mind that not all email applications display HTML emails in the same way (or at all)

To send an HTML email body, you may need to do two things:

+   1. Create the HTML markup for your message body.
2. Send the message using the mail() function, passing in additional MIME headers to indicate that the message body is in HTML format.

MIME stands for Multipurpose Mail Extensions, and it's an extension to the standard email protocols that follow, among other things, messages to contain multiple text and non-text attachments. MIME is also used in other protocols; in fact you've already seen the Content-Type: MIME header in the "Working with HTTP" section earlier in the chapter.

First, create your HTML message body. At the time of writing, most email applications only understand a subset of the HTML standard, so it's best to make your markup as simple as possible. CSS support is particularly bad, so you may need to eschew CSS in favor of table-based layouts.

You can find out about creating HTML emails, as well as download free email templates, at http://www.mailchimp.com/resources/templates/. Another useful site is the Email Standards Project (http://www.email-standards.org/) that tracks the state of Web standards support across various email applications.

Here's a simple HTML email message:

```
$message = <<END_HTML
<html>
<body>
<h1 style="color: #AA3333;">Thank You</h1>
<p>Thank you for contacting us <a href="http://www.example.com/">The Widget Company</a></a>. We'll be in touch shortly.</p>
</body>
</html>
END_HTML;
```