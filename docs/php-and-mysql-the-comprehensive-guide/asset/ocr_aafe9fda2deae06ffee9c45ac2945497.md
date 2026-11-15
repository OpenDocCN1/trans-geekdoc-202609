+   - **smtp_port**
+   Port of the SMTP server (if it is not the default port 25); only necessary under Windows!

+   - **sendmail_from**
+   Sender of the emails sent. Only necessary under Windows!

+   - **sendmail_path**
+   Path for sendmail including parameters (e.g., sendmail -t). Only necessary under Unix/Linux!

+   - **mail.force_extra_parameters**
+   Additional parameters that must always be sent to the email program.

+   - **mail.add_x_header**
+   Specifies whether the name and UID of the PHP script should be added to the mail via the header.

+   - **mail.mixed_lf_and_crlf**
+   Mixed line endings (only necessary for exotic mail servers).

+   - **mail.log**
+   Log for all calls to mail().

> **Tip**
> The extra mail parameters can also be set programmatically. The configuration setting in `php.ini` is mainly of interest to hosts who want to prevent the user from passing parameters directly to the mailer.

The standard versions of `php.ini` delivered with PHP are different for Unix/Linux and Windows; the configuration parameters that are not relevant for the respective system are commented out. Here you can see possible values for a Unix/Linux installation:

```
sendmail_path = "/var/qmail/bin/qmail-inject"
```

And here is a possible Windows configuration:

```
SMTP = localhost
smtp_port = 25
sendmail_from = "webapp@xy.zzz"
```

> **Note**
> For reasons of clarity, we have omitted most of the error corrections in this chapter. However, especially when sending emails, you should always check whether they have been sent successfully—at least to the mail server. Of course, you cannot determine whether the recipient has received the email because your mail server forwards the email to the recipient's mail server, and this server is outside your control.