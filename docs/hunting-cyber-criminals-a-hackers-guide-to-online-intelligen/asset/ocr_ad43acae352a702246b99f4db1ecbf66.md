# Chapter 3 ■ Manual Network Exploration 47

```
;; ANSWER SECTION:
apple.com.      1100 IN A      17.172.224.47
apple.com.      1100 IN A      17.142.160.59
apple.com.      1100 IN A      17.178.96.59
```

```
;; Query time: 1 msec
;; SERVER: 8.8.8.8#53(8.8.8.8)
;; WHEN: Mon Dec 10 09:02:24 UTC 2018
;; MSG SIZE rcvd: 86
```

# ARIN Search

Having one IP address is great, but we would like to know more about the target's IP space. The American Registry of Internet Numbers (ARIN) manages the distribution of IPv4 and IPv6 addresses. Many large organizations will register entire ranges, their IP space will be easily searchable. ARIN provides a free search to quickly identify these IP ranges.

The WHOIS protocol (which will be discussed in Chapter 9) is used to query databases containing all sorts of publicly available information on resources, including domain names and IP addresses. The WHOIS protocol is used to query a wide network of WHOIS servers for any information on the domains behind the billions of websites around the world (collectively known as WHOIS data).

WhoisSearch looks at data specifically within the ARIN's registration data. This can be a good first step when performing a black box assessment and all you have to go on is a company name. Figure 3.1 shows an example ARIN search window.

![](bbox=[0.186, 0.622, 0.549, 0.658])

Figure 3.1. "Google" in the WhoisRWS search gives us a few different network ranges we can add to our searches, as shown in Figure 3.2.

NOTE This is a great first step for me because you will get lucky and find that an IP address (even an even IP block) is owned by a particular owner. When you're looking for server or database attribution, it's rare that this happens, but I've been lucky a few times. There was one data leak in particular I want to mention. A Chinese telecom company had over 3 TB of data leaking, including customer names, email addresses, mobile numbers, and debit card numbers. Luckily, they owned their entire netblock, so attribution was fairly simple. It doesn't always happen this way, but it's worth trying first.