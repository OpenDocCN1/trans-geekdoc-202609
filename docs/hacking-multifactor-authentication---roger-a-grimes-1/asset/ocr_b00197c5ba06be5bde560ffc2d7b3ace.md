# Chapter 18 DNS Hijacking 393

Since 1994, most of the major routers on the Internet used BGP. It's the way the Internet’s work. Each Participating BGP router is assigned a unique autonomous system number (ASN). BGP routers send and receive traffic from other BGP routers, and most of the Internet depends on BGP routers and their BGP routing tables. You can learn more about BGP here: en.wikipedia.org/wiki/Border_Gateway_Protocol.

Unfortunately, when BGP was created and released, it didn't have a lot of security or integrity checks built into it. Essentially, any errant BGP router administrator who updates their BGP routing table in the wrong way can cause huge routing issues with the Internet. Sometimes these mistakes are indistinguishable from intentional hijacking.

Starting in 2013, BGP "mistakes" have sent large percentages of domestic traffic through other countries, often engaged in a cold war with the other country. The first article I remember reading about it: arstechnica.com/information-technology/2013/11/repeated-attacks-hijack-huge-chunks-of-internet-traffic-researchers-warn-. Then I’ve read dozens of articles about your country’s routers, which happened to send some country’s Internet traffic through another country:

+   - asatimes.com/2018/10/beware-china-may-be-reading-your-email
- arstechnica.com/information-technology/2018/11/strange-snafu-misroutes-domestic-internet-traffic-through-china-telcom
- asatimes.com/2018/10/beware-china-may-be-reading-your-email
- zdnet.com/article/russian-telco-hijacks-internet-traffic-for-google-aws-cloudflare-and-others

There’s a white paper on cases of BGP hijacks: scholarscommons.us.edu/cgi/content.cgi?article=1050&context=mca.
When a BGP hijacking happens, any unencrypted traffic routed through the hijacked network points can be captured and read. If the data is encrypted, an attacker can at the very least read source and destination IP addresses and determine relationships. If the attackers get fake, trusted digital certificates, as is often the case with regular phishers, they may be able to read and edit other web traffic. And like DNS hijacking, DNS hijacking

I hope this has convinced you of the importance of namespaces in our computer security and how their malicious manipulation can easily bypass MFA.

# Defenses Against Namespace Hijacking Attacks

This section examines developers and users defenses against namespace hijacking attacks.