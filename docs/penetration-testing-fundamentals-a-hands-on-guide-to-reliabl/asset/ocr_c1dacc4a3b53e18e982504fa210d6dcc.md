HP printers have a mechanism to send email to the printer. You can find the printer’s email address two different ways. The first way is to log into ePrintCenter.com and look on the printer’s page for the email address. The second way is to touch the ePrint button on the front panel and it will display all of the printer’s web services information. You should test this. And of course, find out if other devices have similar issues.

Of course, you must test all items indicated by any standard you are using. For example, PCI DSS requires all external communication of credit card data to be encrypted. I suggest you test all internal and external data communication.

# Optional Items

The following items are not always included in penetration tests, but you should consider them. We discussed a few of these earlier in this chapter.

+   1. Send employees anonymous phishing email that will do something harmless such as redirect them to a page admonishing them not to click on links, or a harmless malware attachment that just has a voice or popup telling them not to download attachments.
+   2. Attempt social engineering via phone or in person.
+   3. A penetration test is not a vulnerability scan, but can include vulnerability scanning (as already shown in this book). In the same way, a penetration test is not an audit, but can sometimes include elements of an audit. With that in mind, you may wish to check the following items:
+      a. Password policies
+         i. Lockout policy
+         ii. Minimum requirements
+         iii. How often passwords are changed
+      b. Are there any unauthorized devices or software anywhere on the network?
+      c. Are there still accounts active for employees no longer with the organization?

In general, you should feel free to add items to this outline, but not to take any away. When you are testing a system, issues may arise that were not foreseen in the pre-project activities. Also, your own experience will teach you new things to be alert for. There may be recent security issues in the news that were not an issue at the time this chapter was written. Keep in mind the penetration test described in this chapter is for a small network, and it should be considered the baseline or minimum for a successful penetration test. You should feel free to add to it and expand it.

# Report Outline

Now that you have completed your test, you should have a lot of screenshots from your tools, lots of notes, and a significant amount of data. While the focus should be on issues found, anything you tested