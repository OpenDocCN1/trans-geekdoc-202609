# Chapter 5 Automated Tools for Network Discovery 111

[recon-ng] [OSINT] > show domains

| rowid | domain | module |
|---|---|--|
| 1 | www.uberpeople.net | user_defined |
| 2 | www.dualxcrypt.com | user_defined |

[*]2 rows returned
[recon-ng] [OSINT] >

# Searching for Modules

You have two ways to search for modules. The previously described method of typing use and pressing the Tab key will show you all available modules. If you would rather not look through the entire list, you can type search and a string. Let's say what is available for resolving domain names:

```
[recon-ng] [OSINT] > search resolve
[*] Searching for 'resolve'...

---
```

```
Recon
recon/hosts-hosts/resolve
recon/hosts-hosts/reverse_resolve
recon/netblocks-hosts/reverse_resolve
```

Before initiating any of scans on a target, it is good practice to get into the habit of earning as much information as you can look for the target. Doing so may turn up interesting results in a different (and unexpected) module.

Since we don't know much about DualCrypt, we might turn up some interesting results if we look for the company name in addition to the domain name. To add a company name, we follow the same process using the command add companiesname description:

```
[recon-ng] [OSINT] > add companies DualCrypt na
```

# Using Modules

Since we know the domain, we can start our investigation by performing a simple resolve search. A resolve search is a short way of saying we will be performing a DNS resolution search, using the hosts-hosts/resolve nameservers.

Let's say using the hosts-hosts/resolve module:

```
[recon-ng] [OSINT] > use recon/hosts-hosts/resolve
```