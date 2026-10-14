# Discussion Questions

+   1. Have you or someone you know been the victim of any kind of theft (either personal possessions or identity theft)? How did you or this other person respond? What course of action was taken to remedy the situation? How long did it take for this incident to be resolved?
+   2. What do you think should happen to Equifax as a result of this breach? Should consumers have the option/right to have their data deleted by a company at any time upon request? Should the government step in and become the clearinghouse for consumer credit reporting in an effort to provide more robust security?
+   3. The article mentions Equifax’s use of a centralized structure for storing data, which resulted in a very appealing target for hackers. Can you think of other companies/contexts in which a centralized structure is used? Do you think this should be avoided in light of the Equifax breach?
+   4. Equifax employees made the mistake of tweeting out a URL for a site that was not actually associated with the company’s response efforts. How can you verify that a site is legitimate?

are frustrated for many reasons, including the risk of fraud and the fact that they have no power over their own PII (i.e., the credit agencies collect data about everyone and there is no choice to “opt out” of having these companies store data about you).

Equifax made matters worse with a number of blunders in the way it handled the breach. For example, shortly after reporting the breach, the company created a support site for people to check whether their data had been compromised, but the site it created was external to its corporate domain (i.e., not related to its main website). This enabled cyber criminals to exploit unwary individuals by creating a variety of false websites with similar URLs. To make this point, a web developer created a fake site that was subsequently referenced by a few Equifax employees. Incredibly, they erroneously tweeted out a link to the fraudulent site—multiple times!63 One estimate reported that almost 200 fake sites had been created by phishers within a day of the support site being created.64

# Security Technology

# Going Phishing

Phishing scams are used by criminals to fraudulently extract confidential information from users. These scams are creative, complex, and well organized. Criminals, typically located outside the United States, use a compromised server to host a fake website that gathers and automatically transmits information harvested from users. The following example shows how a typical phishing scam works.

# The Scam

A phishing scam was sent to one of the authors (Randy.Boyle@utah.edu) at 1:09 AM located in Salt Lake City, Utah. The “To” line read “info@helpdesk.org,” not the author’s e-mail address. The e-mail address listed for the sender of the e-mail was from a county health care administrator in Scottsville, Kentucky. The scam indicated that the user’s mailbox was over its limit and they needed to log in and “validate” their quota.

This phishing scam may or may not have originated from the e-mail server in Kentucky. However, it is likely that the e-mail server for the county health care organization was compromised. A trace of the e-mail showed that it came from a nearby e-mail server in Frankfort, Kentucky. However, the e-mail address could have been spoofed and the e-mails could have come from an entirely different e-mail server. Without more information from the administrators of those systems, it’s difficult to say for sure.

The phishing scam itself was running within a website for a company in Jamestown, North Dakota, that makes tombstones. Yes, tombstones. The server associated with this IP address had several ports open, including 21 (FTP), 53 (DNS), 80 (HTTP), 143 (IMAP), 443 (HTTPS), 587 (Sendmail), and 3306 (MySQL). Some of these services were likely being used legitimately by the tombstone company and others may have been initiated by the scammers.

The website that was compromised was being hosted by a hosting company in Tampa, Florida. The administrator for that hosting company was e-mailed by the author within 10 minutes of getting the phishing scam. They were told that one of their machines was hosting an illegal phishing scam within a legitimate website. They never responded, and the phishing scam remained up for several hours (or more).

# Scam Part 2

A week later, the same phishing scam was again sent. The “To” line read “admin@helpdesk.org.” The sender’s e-mail address was actually an e-mail address of a professor of clinical surgery (oncology) at a large university in the western United States.