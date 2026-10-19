Open mail relays are a principal tool for the distribution of spam because they allow an attacker to hide his or her identity. A number of blacklists for open mail relay servers exist that can be used for blacklisting open mail relays; i.e., a legitimate mail server would not accept any email from this host because it has a high likelihood of being spam. Although using blacklists as one indicator in spam filtering has its merits, it is risky to use them as an exclusive indicator. Generally, they are run by private organizations and individuals according to their own rules, they are able to change their policies on a whim, they can vanish overnight for any reason, and they can rarely be held accountable for the way they operate their lists.

![](bbox=[0.01, 0.27, 0.99, 0.62])

1 An SMTP exchange is normally initiated by a client opening an SMTP session to a local SMTP server.

2 The SMTP server (A) performs an MX lookup to determine the receiving mail host for the destination domain (B), and initiates a mail transfer, adding itself as a receiving host in the mail message header.

3 SMTP Gateway B receives and processes the mail as appropriate (performing content scanning and filtering, etc). B then opens a connection to SMTP C.

4 SMTP C receives the mail into a local mailbox, which is ultimately polled-retrieved by the appropriate mail client.

Figure 4.35 – Representative SMTP exchange
(From Young, S. and Aitel, D., Hacker’s Handbook: The Strategy behind Breaking into and Defending Networks, Auerbach Publications, Boca Raton, FL, 2004. With permission.)

# Spam

Spam benefits from the low cost of email, as opposed to phone calls or letters. It can be sent in massive amounts with little additional cost and a low risk of retribution. Over the years, sending spam has become a professional and highly profitable business. This means that spammers are highly organized and structured. In general, spam is not