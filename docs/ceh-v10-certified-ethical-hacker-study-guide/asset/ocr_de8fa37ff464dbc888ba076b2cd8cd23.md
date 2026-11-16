# # Zone Transfer Using dig _(continued)_

```
;; Query time: 20 msec
;; SERVER: 192.168.86.51#53(192.168.86.51)
;; WHEN: Thu Jul 05 10:15:27 MDT 2018
;; XFR size: 9 records (messages 1, bytes 243)
```

# ## Brute Force

As zone transfers are generally disallowed, you may have to rely on less elegant solutions to gather information about your target. Fortunately, there are some tools that may be of help here. One is dnsrecon, which can be used to extract some of the common resource records in DNS. Additionally, it can be used to identify hostnames as a result of repeated requests based on a wordlist provided to the program. In the following code, dnsrecon is used to do a brute force scan. The wordlist provided has a number of possible hostnames. These hostnames are prepended to the provided domain name and then the resulting FQDN is checked. You can see a portion of the results from the scan.

# ## Using dnsrecon to Acquire Hostnames

```
$ dnsrecon -d wiley.com -D /usr/share/wordlists/dnsmap.txt -t brt
[*] Performing host and subdomain brute force against wiley.com
[*]     A act.wiley.com 209.172.193.49
[*]     A adc.wiley.com 192.168.5.1
[*]     A ags.wiley.com 209.172.193.49
[*]     A api.wiley.com 209.172.192.180
[*]     A bcs.wiley.com 209.172.193.216
[*]     CNAME bpa.wiley.com internal-bpa-private-app-prod-elb-405571586
.us-east-1.elb.amazonaws.com
[*]     A internal-bpa-private-app-prod-elb-405571586.us-east-1.elb.amazonaws
.com 10.223.11.111
[*]     A internal-bpa-private-app-prod-elb-405571586.us-east-1.elb.amazonaws
.com 10.223.199.133
[*]     A bpm.wiley.com 10.6.1.241
[*]     A bps.wiley.com 10.6.2.91
[*]     A cct.wiley.com 209.172.194.98
[*]     CNAME cec.wiley.com d1hsh8hpdo3jj3.cloudfront.net
```

In some cases, looking up an IP address results in an alias. In the output, these show up as canonical name (CNAME) responses. The CNAME refers to another hostname, and that hostname is then resolved until there is an IP address. There can be multiple layers of CNAMEs that need to be resolved. Some of these IP addresses are private, but some others are public IP addresses. These IP addresses could be chased down.