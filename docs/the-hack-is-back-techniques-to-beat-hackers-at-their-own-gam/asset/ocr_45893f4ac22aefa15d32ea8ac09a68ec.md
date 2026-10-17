```
;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 512
;; QUESTION SECTION:
;m41where.org.                    IN      ANY

;; ANSWER SECTION:
m41where.org.            900     IN      NS      ns1.hover.com.
m41where.org.            900     IN      MX      10
mx.hover.com.cust.hostedemail.com.
m41where.org.            900     IN      TXT     "abuseipdb-
verification=ExJNGjL1"
m41where.org.            900     IN      A       34.226.31.104
m41where.org.            900     IN      SOA     ns1.hover.com.
dnsmaster.hover.com. 1577806130 10800 3600 604800 900
m41where.org.            900     IN      NS      ns2.hover.com.

;; Query time: 720 msec
;; SERVER: 8.8.8.8#53(8.8.8.8) (TCP)
;; WHEN: Wed Jul 06 11:52:00 EDT 2022
;; MSG SIZE  rcvd: 238
```

What we see is that there are several records published for this site. Additionally, there is a TXT record for AbuseIPDB, a website used to record attacks across the Internet. This is an example of a small piece of seemingly benign information; however, we could potentially leverage this information. Imagine a scenario where we craft a phishing email posing to be AbuseIPDB, we could notify the target that their honeypots are breaking the new terms of service on the platform – certainly, an interesting email that will spark curiosity in the target. Always be on the lookout for ways to convert information into intelligence about the target.

The output from the DNS records shows that there are several different IP addresses returned. It is important to keep in mind that not all of these IPs may be owned by the target but may simply be SaaS (Software as a Service, think of things like Office 365) based or owned by a 3rd party. Directly evaluating the security of SaaS application providers is strictly out of scope, however, authentication attempts are allowed. We must make sure that we properly stay within scoping when analyzing an environment.

From our perspective as hackers, we want to enumerate as many possible hosts and hostnames as we can. This will be correlated with the IPs they resolve to, as well as potential information within open-source resources to gather even more information. The following tools are used to help us gather as many potential hostnames and subdomains as possible to use further down our reconnaissance chain.

# DNS Dumpster

Tools such as DNSDumpster make quick and easy work of finding and analyzing DNS records. Simply placing the domain in the search bar reveals the active DNS records and what they resolve. Many organizations have no idea what items they have in their DNS records and unintentionally leak sensitive information or assets.