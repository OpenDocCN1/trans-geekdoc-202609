```
[+] Hosts found in search engines:
----------------------------------------------------------------------------
Total hosts: 8
[-] Resolving hostnames IPs...
agupubs.onlinelibrary.wiley.com : 65.156.1.101
authorservices.wiley.com : 216.137.41.119
booksupport.wiley.com : 208.215.179.132
eu.wiley.com : 216.137.41.74
hub.wiley.com : 204.93.79.243
newsroom.wiley.com : 204.8.173.169
onlinelibrary.wiley.com : 65.156.1.101
www.wiley.com : 216.137.41.21
```

Google is not the only source that can be used with theHarvester. Another source that can be used, that may not be considered a lot, is a Pretty Good Privacy (PGP) key server. PGP relies on public keys to be available in publicly available key servers. Without these, the public key has to be shared manually by anyone who wants to get an encrypted message from someone else. Because these keys have to be available to be used, they are stored and searchable on web servers. Since they are associated with email addresses, you can search for email addresses on the key server. This may not always be successful. People who have been around for a long time may be more likely to have PGP keys. As an example, you can see the run results of theHarvester against one of my own domains. Since some of my email addresses have been around for more than 20 years, and since I've generally had a habit of rebuilding machines without storing off encryption keys, I have a few PGP keys.

Interestingly, theHarvester wasn't able to locate any of my PGP keys. This leads us to other places to look for PGP keys. One of the older public key servers is hosted at the Massachusetts Institute of Technology (MIT). If you go to https://pgp.mit.edu, you can provide a search term, including a domain name. Searching using theHarvester didn't turn up any entries for wiley.com. Doing the same search at https://pgp.key-server.io (MIT's site was unresponsive for this search) resulted in a handful of results. However, because of the way the search in the database was conducted, the term wiley.com resulted in a number of people whose first name was Wiley, while the domain name their email address was in ended in .com.

Using the MIT site to search for my own keys, I turned up all the keys I have loaded into the key servers over the years. This is a way to look up information about individual people if you need to, since theHarvester requires that you provide a domain name. In my case, you can see the output from the search in Figure 4.3. My primary email address has three different keys associated with it. As I said, I had a habit of rebuilding or moving to different machines without ever storing my private key. This meant, if I wanted to do any PGP encrypted email, I had to regenerate a key and re-upload. Since the key signature is different, it doesn't overwrite the other key. It's possible, after all, I could have a few legitimate keys that are all used on different systems.