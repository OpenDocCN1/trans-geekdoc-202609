An SPF pass doesn’t mean that the email isn’t malicious. Many malicious emails pass SPF checks. It simply means that the email claimed a particular 5321 email address domain and SPF verified that it was or wasn’t sent by an email server/service authorized for that domain.

Figure 7-9 shows an SPF check failure on a real-world phishing email.

![](bbox=[0.153, 0.296, 0.892, 0.622])

# FIGURE 7-9 An SPF check failure on a real-world phishing email.

In Figure 7-9, you can see “spf=fail” on the first line of the header excerpt. The phishing email was trying to claim that its 5321 email domain was accountprotection.microsoft.com and it was not. Further, the email header indicates the email was really sent from the sim-networks.net domain instead.

SPF failures aren’t always malicious. It can also be because the sender did not set up their SPF DNS records correctly. In fact, this is quite common. Still, if you suspect an email is a phishing email because of other reasons, failing an SPF check is