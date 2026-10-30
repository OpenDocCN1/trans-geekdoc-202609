+   7. Attempt standard attacks including:
+     a. Try to connect to computers’ shares.
+     b. Try to crack passwords on key machines.
+     c. Try to telnet or ssh to printers.
+     d. Attempt default passwords on any servers, printers, switches or routers, and wireless access points.

Of course, you must test all items indicated by any standard you are using. For example, PCI requires all external communication of credit card data to be encrypted. I suggest you test all internal and external data communication.

# Optional Items

+   1. Send employees anonymous phishing email that will do something harmless such as redirect them to a page admonishing them not to click on links or a harmless malware attachment that just has a voice or popup telling them not to download attachments.
+   2. Attempt social engineering via phone or in person.
+   3. A penetration test is not a vulnerability scan, but can include vulnerability scanning (as already shown in this document). In the same way, a penetration test is not an audit, but can sometimes include elements of an audit. With that in mind, you may wish to check the following items:
+      a. Password policies
+         i. Lockout policy
+         ii. Minimum requirements
+         iii. How often passwords are changed
+         iv. Check to ensure default passwords are not used on any systems
+      b. Are there any unauthorized devices or software anywhere on the network?
+      c. Are there still accounts active for employees no longer with the organization?

This outline is a basic outline for a rather small network. Feel free to expand it and add to it as you see fit. This should be considered the bare minimum of a pen test.

# Related Standards

There are other standards that are not actually penetration testing standards, but are closely related. These are security standards that can be used to guide your penetration testing. For example, earlier in this chapter I mentioned OWASP as a web security standard. Testing against some standard is preferable to simply performing ad hoc tests of whatever issues occur to you.