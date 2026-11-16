For example, the following timestamp:

Sun, 28 Jan 2001 23:18:09 +0900

indicates the following:

+   - [ ] The MTA's local time is 23:18:09
+   - [ ] Its time zone is +0900, that is, nine hours east of UTC (Universal Time Coordinated)
+   - [ ] The actual time is 28 Jan 2001 14:18:09 in UTC, that is, nine hours minus the MTA's local time

The day of the week can be omitted.

# From

The sender's e-mail address is contained in the From field. The field may hold multiple addresses separated by a comma, but usually contains a single sender.

An e-mail address is actually its holder's mailbox followed by an @ symbol and his hostname: for example wankyu@whatever.com. Here, "wankyu" is the name of the mailbox and it resides on the host whatever.com.

What if you want to add your real name to your e-mail address? An e-mail address may take additional information in the following form:

+   - [ ] Wankyu Choi <wankyu@whatever.com>
+   - [ ] "Choi, Wankyu" <wankyu@whatever.com>
+   - [ ] wankyu@whatever.com (Da Man)

Notice the angled brackets used to delimit the e-mail address in the first and second formats. Most MUAs use such additional information to show senders' real names in message lists and make address books. Additional information in the third address is delimited by parentheses. More address formats are available but rarely used.

You don't have to worry about parsing these address formats. PHP offers functions to do just that.

# To

The To field contains the identity of the primary recipient(s) of the e-mail message. It can be omitted if, and only if, the Bcc header field is specified.

A comma separates multiple recipients. Most MUAs use a semicolon for designating multiple recipients, so you may be accustomed to it. Make sure you use a comma when creating an e-mail script within PHP or convert every instance of a semicolon into a comma.

# Bcc

The Bcc header field can be omitted if, and only if, the To header field is present.

Bcc stands for Blind Carbon Copy and holds a comma-separated list of other recipients getting a copy of the same e-mail message. It works much the same as the Cc field we'll be looking at shortly, but is intended not to show up in other recipients' header blocks. In other words, none of the recipients getting a copy of the e-mail will know that other people have been sent the same message.