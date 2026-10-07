
# Chapter 3 Manual Network Exploration 59

```
[-] Searching in Google..
[-] Searching in Bing..
[-] Searching in Ask..
[-] Searching in Netcraft..
[-] Searching in DNSstumpter..
[-] Searching in Virustotal..
[-] Searching in ThreatCrowd..
[-] Searching in SSL Certificates..
[-] Searching in PassiveDNS..
[-] Total Unique Subdomains Found: 5
```

This initial query resulted in several hundred subdomains returned from pepsi.com. Let's try the same command with our second:

```
root@CSINT: python sublist3.py -d cypher.org

www.cypher.org
office.cypher.org
seek.cypher.org
storm.cypher.org
zone.cypher.org
```
[-] Total Unique Subdomains Found: 5

Now we've seen a handful of GUI and command-line tools that we can use to get lists of subdomains using more conventional methods. Let's take this process further and try brute forcing.

## Enumall

Enumall is a script created by Jason Haddix to perform exhaustive subdomain discovery with a single command. Enumall is designed to do everything you've seen in this chapter with the recon-ng engine to:

- Enumerate subdomains
- Search Google, Bing, Yahoo, and Netcraft
- Resolve all active addresses to IP addresses
- Output everything to a nice and neat CSV

Before running the script, you should be aware of these parameters:

- -a: Use altdns to create a permutation of words based on seed list
- -p: The seed list we want to feed to altdns
- -w: The custom wordlist to use with recon-ng while bruteforcing

> NOTE Using the altdns options might be overkill on the level of testing you want to perform. This will create millions of possible permutations and take a very long time to complete (+ hours). Using the standard dictionary -w will probably be enough in most cases. If not, you can also try different dictionaries. Let’s run our script against pepsi.com:

```
root@OSINT: python enumall.py pepsi.com -a ../altdns/words.txt -w /SecLists/sortedcombined-knock-dns-fierce.txt
```
[*] 78 total (51 new) hosts found. 16 records added to '/opt/recon/domain/pepsi.com.csv'.

```
root@OSINT: python enumall.py cypher.org -a ../altdns/words.txt -w /SecLists/sortedcombined-knock-dns-fierce.txt
```
[*] 5 total (5 new) hosts found. 6 records added to '/opt/recon/domain/cypher.org.csv'.

## Results

Table 1.1 shows the results from the different tools we used.

Table 1.1: Subdomain search results

| TOOL USED | PEPSI.COM | CYPHER.ORG |
|---|---|---|
| DNSDumpster | 19 | 1 |
| Hacker Target | 31 | 5 |
| Shodan | 28 | 0 |
| Censys | 42 | 0 |
| Fierce | 6 | 4 |
| Sublist3r | 56 | 5 |
| Enumall/Recon-ng | 78 | 5 |

If you take anything away from this chapter it should be that not every tool is perfect, and each tool will often give you different (or varying) results. You should always use tools in your arsenal. Scripts Enumall are great because they will use multiple tools to give you the most possible results.

## Phishing Domains and Typosquatting

Typosquatting is a technique of registering fake names that look similar to the original/legitimate domain name. It is really just a fancy way of saying it is a misspelled URL. Attackers will take advantage of the fact that people make spelling errors when they type, and will register fake domain names with the intent of harvesting credentials, distributing malware, or doing something malicious. Attackers will often use misspelled domains in phishing emails as a quick way to get someone to click a link.

> NOTE Homoglyphs are also very popular now in phishing attacks. Homoglyphs are characters (or glyphs) that appear very similar. These often include characters from other alphabets that look very similar to the original. For example, looking at pepsi.com and pep.com, can you tell the difference right away? “i” is different.

Searching for phishing/typosquatted domains is typically useful for one of two reasons. Either 1) you want to include a list of potential phishing domains for a customer on an external pen-test report (which you should always do); or 2) you have been hired to socially engineer the customer and find a way to trick users into giving you their credentials.

The best tool I've found for sniffing typosquatting on domains is DNSTwist. Using DNSTwist is extremely straightforward and will generate a list of potential phishing domains and automatically check if they are registered and/or active. You can also use the following switches to enhance your results:

- -d: Use your own dictionary file
- -f: Output to file format (CSV, JSON)
- -r: Show only registered domains
- -w: Perform WHOIS lookup on domains
- -b: Grab banners from hosts
- -a: Show all DNS records

Let's run to show only registered domains and see the results:

```
root@OSINT: python dnattwist.py -r pepsi.com
```

Right off the top with minimal effort, we get 81 hits (the following results truncated): 936 variants.

| Addition | |
|---|---|
| Addition | psia.com | 185.82.122 ns:dynamhost.com MX:dynamhost.com |
| Addition | pepsib.com | 78.41.91 ns:ns1.torres.com |
| Addition | pepsid.com | 104.31.76.260:4700:30::681f:4cb NS:igor.ns.com |
| Addition | pepsie.com | 199.59.242.151 ns:ns1.bodis.com MX:mx76.m2bp.com |
| Addition | pepself.com | 184.168.221.50 ns:ns53.domaincontrol.com MX:mailstore.secureserver.net |
| Addition | pepsih.com | 66.63.171.125 ns:ns1.ehosting.com MX:mailpsi.com |
| Addition | pepij.com | 94.152.37.52 ns:ns1.key.com MX:pepsik.com NS:duns.com |
| Addition | pepsil.com | 184.168.221.50 ns:ns65.domaincontrol.com MX:mailstore.secureserver.net |
| Addition | pepsim.com | 69.172.201.153 ns:ns1.unigistry.link |
| Addition | pepsit.com | 162.255.119.196 ns:dns1.registrar.com |
| Addition | pepsix.com | 104.217.67.249 ns:v1.dns234.100 |
| Addition | pepsisy.com | 162.255.119.196 ns:dns1.registrar.com |
| Addition | pepmi.com | 206.220.201.245 ns:ns10.net MX:pepi.com.next10rcixm |
| Addition | pepsi.com | 21.6.243.144 ns:ns1311.awdns-35.06 MX:d1407a.ess.bacudanet |
| Addition | pepps.com | 213.1.249.100 ns:ns1.planet.com |
| Addition | ppsi.com | 208.91.197.128 ns:ns33.worldnic.com MX:| |
| Addition | epsi.com | 216.198.200.146 ns:ns23.domaincontrol.com MX:mail.epsi.com |

Repetition pepsi.com - 172.98.192.36 NS1:rentondoc.com
Repetition pepsi.com - 23.20.239.12 NS1:namebirthdns.com
Repetition pepsi.com - 50.63.202.54 NS0:ns01.domaincontrol.com MX:mailstore.secureserver.net

Replacement pemsi.com - 184.168.131.241 ns:ns53.domaincontrol.com MX:mailstore.secureserver.net
Replacement peosi.com - 192.185.188.86 ns:ns825.website.com MX:mail.peosi.com
Replacement pep9.com -
Replacement pep8.com -
Replacement pselsi.com - 64.118.87.10 NS1:ns1.myserver.com MX:pelsi.com
Replacement pepei.com - 72.52.179.174 NS1:nslogicic.com
Replacement pwpsi.com - 23.20.239.12 NS1:namebirthdns.com MX:pepsi.com
Replacement prpsi.com - NS1:ns1.microsoftoftline.com MX:pepsi.com.mail.protection.outlook.com
Replacement pepsu.com - 46.30.215.63 2ad2:2350:5:104:cfc0:0848 NS:ns01.com MX:mx1.pub.mailpod6-ch3.com
Replacement pepso.com - 50.63.202.54 ns:ns63.domaincontrol.com MX:mailstore.secureserver.net
Replacement pepjs.com - 192.232.223.72 ns:ns617.hostigator.com MX:pejs.com
