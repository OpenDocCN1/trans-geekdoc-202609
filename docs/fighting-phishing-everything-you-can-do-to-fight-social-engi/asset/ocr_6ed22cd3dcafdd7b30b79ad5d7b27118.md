use a VPN, make sure that you keep up on the patching on both sides, the server side and the client side. Many defenders have implemented VPNs only for an unpatched VPN component to end up being responsible for how hackers gained initial access.

# # Prevent Unauthorized External Domain Collaboration

More and more phishing attacks are coming from external domains using an organization’s internal collaboration app (e.g., Microsoft Teams, Slack, Skype, etc.). Make sure internal endpoints are prevented from accepting messaging from unauthorized external domains. How this is configured varies by application.

# # DMARC

As covered in Chapter 7, “DMARC, SPF, and DKIM,” every organization should have DMARC, SPF, and DKIM enabled on both sending and receiving. It prevents email senders from easily spoofing sending email domains. Make sure that all endpoints with email clients have DMARC (and SPF and DKIM) enabled somewhere in the receiving path (i.e., email server, gateway, client, etc.) so that all incoming emails are DMARC verified.

You can check to see if DMARC is enabled on the receiving path by opening up any received email (on an email client on the receiving path), revealing the email headers, and looking for the “dmarc=,” “spf=,” and “dkim=” statements (Figure 9-7 shows an example of this).

The appearance of any of those DMARC result outcomes indicates that DMARC is turned on somewhere in the pathway of the email being received. Make sure every email client has