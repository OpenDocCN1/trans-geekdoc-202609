# 60 Part I Network Exploration

The script uses a combination of wordlists to create different subdomain combinations to try during the brutorce attempt. Before running the script, you should be aware of these specific parameters:

+   - -a: Use alt-dns to create a permutation of words based on a seed list
- -p: The seed list that we want to feed to alt-dns
- -w: The custom wordlist to use with recon-ng while bruteforce

> NOTE Using the alt-dns options might be overkill on the level of testing you want to perform. This will create millions of possible permutations to test and will take a very long time to complete (12+ hours). Using the standard brute force dictionary -w will probably be enough in most cases. If not, you can also try different dictionaries.

Let’s run our script against peppsi.com:

```
root@OSINT: python enumall.py peppsi.com -a -p ../altdns/words.txt -w \
/SecLists/sortedcombined-knock-dnsrecon-fierce-reconn.txt
```

# SUMMARY

+   [*] 78 total (51 new) hosts found.\[*] 167 records added to '/opt/recon/domain/peppsi.com.csv'.

```
root@OSINT: python enumall.py cypher.org -a -p ../altdns/words.txt -w \
/SecLists/sortedcombined-knock-dnsrecon-fierce-reconn.txt
```

+   [*] 5 total (5 new) hosts found.\[*] 6 records added to '/opt/recon/domain/cypher.org.csv'.

# Results

Table 1.1 shows the results from the different tools we used.

Table 1.1:Subdomain search results

| TOOL USED | PEPSI.COM | CYPHER.ORG |
|---|---||
| DNSDumpster | 19 | 1 |
| Hacker Target | 31 | 5 |
| Shodan | 28 | 0 |