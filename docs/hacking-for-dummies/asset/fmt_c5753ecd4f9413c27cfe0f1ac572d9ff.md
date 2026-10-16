
Even in large companies, or if you’re using a cloud-based email service such as G Suite or Office 365, there’s likely no reason why thousands of inbound email deliveries should be necessary within a short period.

![warning](images/warning.png)Email servers can be programmed to deliver emails to a service for automated functions, such as `create this e-commerce order when a message from this account is received`. If DoS protection isn’t built into the system, an attacker can crash both the server and the application that receives these messages, potentially creating e-commerce liabilities and losses. This type of attack can happen more easily on e-commerce websites when CAPTCHA (short for Completely Automated Public Turing test to tell Computers and Humans Apart) isn’t used on forms. This can be problematic when you’re performing web vulnerability scans against web forms that are tied to email addresses on the back end. It’s not unusual for this situation to generate thousands, if not millions, of emails. It pays to be prepared and to let those involved know that the risk exists. I cover web application security in [Chapter 15](#c15.xhtml).

#### Automated email security controls

You can implement the following countermeasures as an additional layer of security for your email systems:

*   **Tarpitting:** `Tarpitting` detects inbound messages destined for unknown users. If your email server supports tarpitting, it can help prevent spam or DoS attacks against your server. If a predefined threshold is exceeded — say, more than 100 messages in one minute — the tarpitting function effectively shuns traffic from the sending IP address for a given period.

*   **Email firewalls:** Email firewalls and content-filtering applications from vendors such as Symantec and Barracuda Networks can go a long way toward preventing various email attacks. These tools protect practically every aspect of an email system.

*   **Perimeter protection:** Although not email-specific, many firewall and intrusion prevention systems can detect various email attacks and shut off the attacker in real time, which can come in handy during an attack.

*   **CAPTCHA:** Using CAPTCHA on web-based email forms can help minimize the impact of automated attacks and lessen your chances of email flooding and DoS, even when you’re performing seemingly benign web vulnerability scans. These benefits really come in handy when you test your websites and applications, as I discuss in [Chapter 15](#c15.xhtml).

### Banners

When hacking an email server, a hacker’s first order of business is performing a basic banner grab to see whether he can discover what email server software is running. This test is one of the most critical tests to find out what the world knows about your SMTP, POP3, and IMAP servers.

#### Gathering information

[Figure 14-2](#c14.xhtml#c14-fig-0002) shows the banner displayed on an email server when a basic Telnet connection is made on port 25 (SMTP). To do this, at a command prompt, simply enter **`telnet *ip or_hostname_of_your_server* 25`**. This command opens a Telnet session on TCP port 25.

![ FIGURE 14-2:  An SMTP banner showing server-version information.](images/9781119485476-fg1402.png)

[FIGURE 14-2:](#c14.xhtml#rc14-fig-0002)  An SMTP banner showing server-version information.

The email software type and server version are often very obvious and give hackers some ideas about possible attacks, especially if they search a vulnerability database for known vulnerabilities in that software version. [Figure 14-3](#c14.xhtml#c14-fig-0003) shows the same email server with its SMTP banner changed from the default (okay, the previous one was, too) to disguise such information as the email server’s version number.

![ FIGURE 14-3:  An SMTP banner that disguises the version information.](images/9781119485476-fg1403.png)

[FIGURE 14-3:](#c14.xhtml#rc14-fig-0003)  An SMTP banner that disguises the version information.

![tip](images/tip.png)You can gather information on POP3 and IMAP email services by Telnetting to port 110 (POP3) or port 143 (IMAP).

![warning](images/warning.png)If you change your default SMTP banner, don’t think that no one can figure out the version. General vulnerability scanners can often detect the version of your email server. One Linux-based tool called `smtpscan` ([`www.freshports.org/security/smtpscan`](http://www.freshports.org/security/smtpscan)) determines email server version information based on how the server responds to malformed SMTP requests. [Figure 14-4](#c14.xhtml#c14-fig-0004) shows the results from smtpscan against the same server shown in [Figure 14-3](#c14.xhtml#c14-fig-0003). The smtpscan tool detected the product and version number of the email server.

![ FIGURE 14-4:  smtpscan gathers version info even when the SMTP banner is disguised.](images/9781119485476-fg1404.png)

[FIGURE 14-4:](#c14.xhtml#rc14-fig-0004)  smtpscan gathers version info even when the SMTP banner is disguised.

#### Countermeasures against banner attacks

There isn’t a 100 percent secure way to disguise banner information. I suggest these banner security tips for your SMTP, POP3, and IMAP servers:

*   Change your default banners to conceal the details.

*   Make sure that you’re always running the latest software patches.

*   Harden your server as much as possible by using well-known best practices from such resources as the Center for Internet Security ([`https://www.cisecurity.org`](https://www.cisecurity.org)) and NIST ([`https://csrc.nist.gov`](https://csrc.nist.gov)).

### SMTP attacks

Some attacks exploit weaknesses in SMTP. This email communication protocol, which is more than three decades old, was designed for functionality, not security.

#### Account enumeration

A clever way that attackers can verify whether email accounts exist on a server is to Telnet to the server on port 25 and run the `VRFY` command. The `VRFY` (short for *verify*) command makes a server check whether a specific user ID exists. Spammers often automate this method to perform a directory harvest attack (DHA), which is a way of gleaning valid email addresses from a server or domain so that hackers know whom to send spam, phishing, or malware-infected messages to.

#### ATTACKS USING ACCOUNT ENUMERATION

[Figure 14-5](#c14.xhtml#c14-fig-0005) shows how easy it is to verify an email address on a server with the `VRFY` command enabled. Scripting this attack can test thousands of email address combinations.

![ FIGURE 14-5:  Using VRFY to verify that an email address exists.](images/9781119485476-fg1405.png)

[FIGURE 14-5:](#c14.xhtml#rc14-fig-0005)  Using VRFY to verify that an email address exists.

The SMTP command `EXPN` (short for *expand*) might allow attackers to verify what mailing lists exist on a server. You can Telnet to your email server on port 25 and try `EXPN` on your system if you know of any mailing lists that exist. [Figure 14-6](#c14.xhtml#c14-fig-0006) shows how the result might look. Scripting this attack and testing thousands of mailing-list combinations are simple.

![ FIGURE 14-6:  Using EXPN to verify that a mailing list exists.](images/9781119485476-fg1406.png)

[FIGURE 14-6:](#c14.xhtml#rc14-fig-0006)  Using EXPN to verify that a mailing list exists.

![warning](images/warning.png)You might get bogus information from your server when performing these two tests. Some SMTP servers (such as Microsoft Exchange) don't support the `VRFY` and `EXPN` commands, and some email firewalls ignore them or return false information.

Another way to automate the process somewhat is to use the EmailVerify program in TamoSoft's Essential NetTools ([`https://www.tamos.com/products/nettools`](https://www.tamos.com/products/nettools)). As shown in [Figure 14-7](#c14.xhtml#c14-fig-0007), you enter an email address and click Start; EmailVerify connects to the server and pretends to send an email.
