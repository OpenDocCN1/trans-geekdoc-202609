Since we've seen all the SQL code involved in this time and again, I'll leave the details up to you. As usual, the SitePoint.com Forum (www.sitepointforums.com) community is there to offer a helping hand if you need it!

# Email in PHP

Email is a powerful force on the Internet. Whether you want to provide a weekly "what's new" newsletter to your users, or a way for them to retrieve a lost or forgotten password, email is the way to go. PHP makes working with email very easy, letting you send messages using a single call to the mail function.

Before you can send email using the mail function, you have to first set up PHP's email-related options. Here are the relevant lines of an out-of-the-box php.ini file under Windows:

```
[mail function]
SMTP =
sendmail_from = me@localhost.com
;sendmail_path =
```

Depending on whether you use the Windows or UNIX version, PHP will send mail through an SMTP server or the local sendmail system, respectively. The process we'd use to set up either of these systems is beyond the scope of this book, and there's plenty of information out there to help you with either. If you're running on Windows, however, chances that your ISP has already provided an SMTP server for your use. It's the same server you set your email program to use when you send messages. Set the SMTP setting to the hostname/IP address of that server.

sendmail_from should be set to the default email address from which you would like emails sent by PHP to be from. If you administer this server, then you should probably put your email address here.

Finally, sendmail_path under UNIX should be uncommented (i.e. remove the semicolon from the start of the line) and set to the path and filename of the sendmail program on your system. Under Linux, this will usually be /usr/sbin/sendmail.

With these settings set and your Web server restarted, PHP should be decked out with full email capabilities. Now, to send an email in PHP couldn't be easier:

```
mail("to-address@somewhere.com", "Message subject", "This is the body of the message.");
```

Mailing to multiple recipients can be accomplished if you simply separate each address with commas: