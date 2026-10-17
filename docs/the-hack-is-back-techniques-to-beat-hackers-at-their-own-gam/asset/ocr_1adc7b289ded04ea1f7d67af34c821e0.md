This data is also accessible through the **Domain Hunter**<sup>10</sup> python tool, which identifies the reputation of expired domains as well. This can quickly help us identify domains with a previously clean reputation, allowing us to stay below the radar with detection tools. Additional benefits of this tool include searching for keywords and filtering based on Alexa’s top domains.

The **domainhunter.py** script does require an active **expireddomains.net** account, this can be quickly set up on the website. Additionally, the domains that are found can be run against known malware domain lists as well, revealing if the domains are previously established as malicious. This gives us information to choose an effective domain for us to register and utilize.

DNS is an effective tool for us to identify hosts and use within the reconnaissance stage, but we must also understand that the same information can be used against our attack infrastructure as well. Understanding how passive DNS attribution and historical records can be used to identify our systems is important. Choosing existing domains that have expired also gives us flexibility in how our attack can be launched and potentially bypass detection tools.

# TARGET DETECTION

Other ways we can obfuscate and protect our infrastructure are through various methods of target detection and selective payload delivery. If we know to expect a certain IP range or ASN, we can tune our systems to only deliver the payload to them, while delivering a benign result to anyone else. We can pair this with a specific HTTP header, User Agent, or even a specific TCP source port to ensure that we are responding to our intended target only.

It is exceptionally common for organizations to run an online tool such as **VirusTotal** or **urlscan.io** to check if a link or file is malicious. IT Help Desks or system administrators will use these tools to determine if a particular object should be considered malicious or not. However, these tools and checks suffer from systems that intelligently and selectively determine their victims.

![](bbox=[0.166, 0.521, 0.837, 0.837])

**FIGURE 4.25**  Serving a default splash page to any CIDR we’re not looking for and providing the payload for the intended victim CIDRs.

There are many ways for us to check this. With PHP, we can look through the `$_SERVER['REMOTE_ADDR']` value as it is received. This value presents the IP address of the