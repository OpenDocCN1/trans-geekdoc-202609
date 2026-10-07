# Chapter 3 ■ Manual Network Exploration

```
global options: +cmd
;; Got answer:
;; --HEADER<< opcode: QUERY, status: NOERROR, id: 127771
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1
```

```
; OPT PSEUDECTION:
; EDNS version: 0, flags; udp: 4096
; QUESTION SECTION:
; cyper.org
		IN		A

;; ANSWER SECTION:
cyper.org		3155		IN		A		162.210.102.59
```

| TOTAL RESULTS |
| 28 |
| TOP COUNTRIES |
| Uzbekistan | 14 |
| Pakistan | 12 |
| Guatemala | 2 |
| TOP SERVICES |
| SMTP | 2 |
| POP3 + SSL | 2 |
| IMAP + SSL | 2 |
| HTTPS | 2 |
| IMAP | 2 |

Figure 3.8

Now let's check Shodan for any hits based on that IP (also referred to as a reverse DNS lookup). There are no subdomains in this output; instead we are provided with a significant amount of metadata from this IP, including other associated domains.

We will discuss reverse DNS (RDNS) lookups in greater detail in Part II of this book (website information gathering)—specifically when looking at domain names. As the name implies, a reverse DNS lookup takes an IP address and returns all domains associated with that IP.