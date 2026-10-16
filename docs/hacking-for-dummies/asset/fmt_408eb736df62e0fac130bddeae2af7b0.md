
![ FIGURE 14-7:  Using EmailVerify to verify an email address.](images/9781119485476-fg1407.png)

[FIGURE 14-7:](#c14.xhtml#rc14-fig-0007)  Using EmailVerify to verify an email address.

Yet another way to capture valid email addresses is to use theHarvester ([`https://github.com/laramies/theHarvester`](https://github.com/laramies/theHarvester)) to glean addresses via Google and other search engines. As I outline in [Chapter 9](#c09.xhtml), you can download Kali Linux from [`www.kali.org`](http://www.kali.org) to burn the ISO image to CD or boot the image directly through VMware or VirtualBox. In the Kali Linux interface, choose Applications ⇒ Information Gathering ⇒ SMTP Analysis ⇒ smtp-user-enum, and enter **smtp-user-enum –M VRFY –u *<user name you want to confirm>* -t server IP/hostname**, as shown in [Figure 14-8](#c14.xhtml#c14-fig-0008).

![ FIGURE 14-8:  Using smtp-user-enum to glean email addresses.](images/9781119485476-fg1408.png)

[FIGURE 14-8:](#c14.xhtml#rc14-fig-0008)  Using smtp-user-enum to glean email addresses.

You can customize smtp-user-enum queries as well using, for example, `EXPN` in place of `VRFY` and `–U` and a list of user names in a file to query more than one user. Simply enter **smtp-user-enum** for all the search options.

#### COUNTERMEASURES AGAINST ACCOUNT ENUMERATION

If you're running Exchange, account enumeration won’t be an issue. If you’re not running Exchange, the best way to prevent this type of email account enumeration depends on whether you need to enable the `VRFY` and `EXPN` commands, as follows: 

*   Disable `VRFY` and `EXPN` unless you need your remote systems to gather user and mailing-list information from your server.

*   If you need `VRFY` and `EXPN` functionality, check your email server or email firewall documentation for the ability to limit these commands to specific hosts on your network or the Internet.

Finally, work with your marketing team and web developers to ensure that company email addresses aren't posted on your organization’s website or on social media websites. Also educate your users about not doing this.

#### Relay

SMTP relay lets users send emails through external servers. Open email relays aren’t the problem they used to be, but you still need to check for them. Spammers and criminal hackers can use an email server to send spam or malware through email under the guise of the unsuspecting open-relay owner.

![tip](images/tip.png)Be sure to test for open relay from both outside and inside your network. If you test your internal systems, you may get false positives because outbound email relaying may be configured and necessary for your internal email clients to send messages to the outside world. If a client system is compromised, however, that situation could be just what the bad guys need to use your systems to launch an outbound spam or malware attack.

#### AUTOMATIC TESTING

Here are a couple of easy ways to test your server for SMTP relay:

*   **Vulnerability scanners:** Many vulnerability scanners, such as Nexpose and QualysGuard, can find open email relay vulnerabilities.

*   **Windows-based tools:** One example is NetScanTools Pro ([`www.netscantools.com`](http://www.netscantools.com)). You can run an SMTP Relay check on your email server with NetScanTools Pro, as shown in [Figure 14-9](#c14.xhtml#c14-fig-0009).

    ![warning](images/warning.png)Although some SMTP servers accept inbound relay connections and make relay appear to work, this situation isn’t always the case, because the initial connection may be allowed, but the filtering actually takes place behind the scenes. Check whether the email made it through by checking the account to which you sent the test relay message.

![ FIGURE 14-9:  Using NetScanTools Pro SMTP Server Tests to check for an open email relay.](images/9781119485476-fg1409.png)

[FIGURE 14-9:](#c14.xhtml#rc14-fig-0009)  Using NetScanTools Pro SMTP Server Tests to check for an open email relay.

In NetScanTools Pro, enter values for the SMTP mail server name and Your Sending Domain Name. Inside Test Message Settings, enter the Recipient Email Address and Sender’s Email Address. If the test is successful, NetScanTools Pro opens a window that says `Message Sent Successfully`.

You can also view the results in the main SMTP Server Tests window and generate a formal report by clicking View Results in a Web Browser and then clicking View Relay Test Results.

#### MANUAL TESTING

You can test your server for SMTP relay manually by Telnetting to the email server on port 25. Follow these steps:

1.  **Telnet to your server on port 25.**

    You can do this in two ways:

    *   Use your favorite graphical telnet application, such as PuTTY ([`https://www.chiark.greenend.org.uk/~sgtatham/putty`](https://www.chiark.greenend.org.uk/~sgtatham/putty)).

    *   Enter the following command at a Windows or Linux command prompt:  

        `telnet mailserver_address 25`

    You should see the SMTP welcome banner when the connection is made.

2.  **Enter a command to tell the server “Hi, I'm connecting from this domain.”**

    ![technicalstuff](images/technicalstuff.png)After each command in these steps, you should receive a different-numbered message, such as `999 OK`. You can ignore these messages.

3.  **Enter a command to tell the server your email address.**

    An example is:

    `mail from:yourname@yourdomain.com`

    You can use any email address in place of `yourname@yourdomain.com`.

4.  **Enter a command to tell the server who to send the email to.**

    An example is:

    `rcpt to:yourname@yourdomain.com`

    Again, any email address will suffice.

5.  **Enter a command to tell the server that the message body is to follow.**

    An example is:

    `data`

6.  **Enter the following text as the body of the message:**  

    `A relay test!`

7.  **End the command with a period on a line by itself.**

    ![tip](images/tip.png)You can enter **?** or **help** at the first Telnet prompt to see a list of all the supported commands and, depending on the server, get help on the use of the commands.

    The final period marks the end of the message. After you enter this final period, your message will be sent if relaying is allowed.

8.  **Check for relaying on your server:** 

    *   Look for a message similar to `Relay not allowed` coming back from the server.

        If you get a message similar to this one, SMTP relaying isn't allowed on your server or is being filtered because many servers block messages that appear to originate from the outside yet come from the inside.

        ![tip](images/tip.png)You may get this message after you enter the `rcpt to:` command.

    *   If you don’t receive a message from your server, check your Inbox for the relayed email.

        If you receive the test email that you sent, SMTP relaying is enabled on your server and probably needs to be disabled. The last thing you want is to let spammers or other attackers make it look like you’re sending tons of spam or, worse, to be blacklisted by one or more blacklist providers. Ending up on a blacklist can disrupt email sending and receiving, which isn’t good for business!

#### COUNTERMEASURES AGAINST SMTP RELAY ATTACKS

You can implement the following countermeasures on your email server to disable or at least control SMTP relaying:

*   **Disable SMTP relay on your email server.** SMTP relay should be disabled by default, but it pays to check. If you don’t know whether you need SMTP relay, you probably don’t. You can enable SMTP relay for specific hosts on the server or within your firewall configuration.

*   **Enforce authentication if your email server supports it.** You may be able to require password authentication on an email address that matches the email server’s domain. Check your email server and client documentation for details on setting up this type of authentication.

#### Email header disclosures
