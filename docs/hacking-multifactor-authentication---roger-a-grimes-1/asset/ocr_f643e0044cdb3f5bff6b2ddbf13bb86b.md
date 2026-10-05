# 156 Hacking Multifactor Authentication

```
EMAIL: johnny.do@mitnicksecurity.com
PASSWORD: knowbe4rocks

###
###
TOKEN COOKIE: document.cookie = "li1_at=AQEDASYYnMEC0GtoAABAYy5k6AAAAAFUIJsXo4AgXeGoeH
EH4XXp646BYJ1LCHqFVM4kME2ZmtqtgdagayYIPhDccXHHBM; expires=2020-05-04 03:18:11"
###
###
```

Figure 6.4: Kevin Mitnick getting around a common MFA solution involving a popular website and stealing the access control cookie token

In summary, here's what Kevin did in his demo:

+   1. Kevin set up lookalike/sound-alike website that was really an evil proxy.
2. Using an email containing a fraudulent URL, which tricked the "victim" into visiting the evil proxy website.
3. Victim typed in credentials, which were proxied, now pretending to be the legitimate customer, posted to legitimate website.
4. website sent back legitimate session token, which Kevin stole and replayed to take over victim's session.

> Kevin used Evilginx (breakdev.org/evilginx-advanced-phishing-with-two-factor-authentication-bypass). It's a great network session hijacking tool. But there are dozens of hacking tools you can use to accomplish the thing.

This is just one example out of the dozens, if not hundreds, of ways to network session hijacking, even if Kevin originally demo this attack in May 2018, reviewers thought his attack was due to a flaw in the website (i.e., LinkedIn) or to a flaw in the MFA solution. They wanted to know when Microsoft (LinkedIn's parent company) was going to fix its website or when Kevin was going to file the CVE (Common Vulnerabilities and Exposures) notifying the world of his brand-new tactic.

Kevin and I laughed because we both knew that it was another great example of Kevin's demos, that he had been done for decades, and it wasn't due to a flaw in the site or the MFA solution. The actual hack was just due to the inherent disconnect between the successful authentication and the resulting access control token and an end-user. There were no bugs. This was one of many unfortunate "as-designed" issues. And these aren't just theoretical attacks. They occur all the time in real life.