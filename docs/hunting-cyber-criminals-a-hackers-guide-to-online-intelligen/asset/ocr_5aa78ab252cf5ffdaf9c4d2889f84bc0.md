# Chapter 3 Manual Network Exploration 57

We can already see that the results between the two services are very different. This is mainly due to the size of the two organizations, but is a reminder that different tools will yield different results.

# Fierce

Fierce is a DNS enumeration tool that helps locate noncontiguous IP space and hostnames against specified domains.
It's really meant as a precursor to NMAP since already requires you to know what IP space you are looking for.
A tool doesn't need to have 100 options to be great. Fierce is meant for DNS enumeration and it simply does what it says it will. The options include:

+   - dns-server: Specifies DNS servers to use
- domain: Domain to test
- subdomain-file: Use subdomains specified in this file (one per line)
- range: Scan an internal IP range, cidr notation
- delay: Time to wait between lookups

To keep things simple, let's run Fierce against our two example domains. We can also output the results to a text file using the Linux output command.
The result of the fierce scan shows six unique subdomain/host entries:

```
fierce --pepsi.com > output.txt
```

```
159.127.187.12 e.pepsi.com
182.214.229.99 promo.pepsi.com
182.214.229.99 secure.pepsi.com
161.147.125.72 shop.pepsi.com
159.127.185.121 signup.pepsi.com
209.143.254.67 stage.pepsi.com
```

```
Subnets (may want to probe using nmap or unicast):
159.127.185.0-255 : 1 hostnames found.
159.127.187.0-255 : 1 hostnames found.
161.147.125.0-255 : 1 hostnames found.
182.214.229.0-255 : 2 hostnames found.
209.143.254.0-255 : 1 hostnames found.
```

Now let's try with our other domain:

```
root@OSINT: fierce --dns cypher.org --threads 5 --file dns.txt
```