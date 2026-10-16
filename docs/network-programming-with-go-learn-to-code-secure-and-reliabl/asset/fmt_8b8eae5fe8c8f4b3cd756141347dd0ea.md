
domain names (like `*google.com*`) are easier for humans to understand and remember. If I gave you the IP address `172.217.6.14` to visit, you wouldn’t know who owned that IP address or what I was directing you to visit. But if **34** Chapter 2 I gave you *google.com* instead, you’d know exactly where I was sending you.

DNS allows you to remember a hostname instead of its IP address in the same way that your smartphone’s contact list frees you from having to memorize all those phone numbers.

All domains are children of a *top-level domain*, such as *.com*, *.net*, *.org*, and so on. Take *nostarch.com*, for instance. No Starch Press registered the *nostarch* domain on the *.com* top-level domain from a registrar with the authority from IANA to register *.com* domains. No Starch Press now has the exclusive authority to manage DNS records for *nostarch.com* and publish records on its DNS server. This includes the ability for No Starch Press to publish *subdomains*—a subdivision of a domain—under its domain. For example, *maps.google.com* is a subdomain of *google.com*. A longer example is *sub3.sub2.sub1.domain.com*, where *sub3* is a subdomain under *sub2.sub1.domain.com*, *sub2* is subdomain under *sub1.domain.com*, and *sub1* is a subdomain under *domain.com*.

If you enter https://nostarch.com in your web browser, your computer will consult its configured *domain name resolver*, a server that knows how to retrieve the answer to your query. The resolver will start by asking one of the 13 IANA-maintained root name servers for the IP address of *nostarch.com*.

The root name server will examine the top-level domain of the domain you requested and give your resolver the address of the *.com* name server.

Your resolver will then ask the *.com* name server for *nostarch.com*’s IP address, which will examine the domain portion and direct your resolver to ask No Starch Press’s name server. Finally, your resolver will ask No Starch Press’s name server and receive the IP address that corresponds to *nostarch.com*.

Your web browser will establish a connection to this IP address, retrieve the web page, and render it for you. This hierarchical journey of domain resolution allows you to zero in on a specific web server, and all you had to know was the domain name. No Starch Press is free to move its servers to a different ISP with new IP addresses, and yet you’ll still be able to visit its website by using *nostarch.com*.

***Domain Name Resource Records***

Domain name servers maintain *resource records* for the domains they serve.

Resource records contain domain-specific information, used to satisfy domain name queries, like IP addresses, mail server hostnames, mail-handling rules, and authentication tokens. There are many resource records, but this section focuses on only the most common ones: address records, start-of-authority records, name server records, canonical name records, mail exchange records, pointer records, and text records.

**N O T E** 

*For more details on types of resource records, see Wikipedia’s entry at* https://en.wikipedia.org/wiki/List_of_DNS_record_types *.*

Our exploration of each resource record will use a utility called *dig* to query domain name servers. This utility may be available on your operating system, but in case you don’t have dig installed, you can use the G Suite Toolbox Dig utility ( *https://toolbox.googleapps.com/apps/dig/*) in a web browser Resource Location and Traffic Routing **35** and receive similar output. All domain names you’ll see are *fully qualified*, which means they end in a period, displaying the domain’s entire hierarchy from the root zone. The *root zone* is the top DNS namespace.

Dig’s default output includes a bit of data relevant to your query but irrelevant to your study of its output. Therefore, I’ve elected to snip out header and footer information in dig’s output in each example to follow.

Also please be aware that the specific output in this book is a snapshot from when I executed each query. It may look different when you execute these commands.

**The Address Record**

The *Address (A) record* is the most common record you’ll query. An A record will resolve to one or more IPv4 addresses. When your computer asks its resolver to retrieve the IP address for *nostarch.com*, the resolver ultimately asks the domain name server for the *nostarch.com* Address (A) resource record. Listing 2-1 shows the question and answer sections when you query for the *google.com* A record.

$ **`dig google.com. a`**

*\-- snip --*

1 ;QUESTION

2 google.com. 3IN 4A

5 ;ANSWER

6 google.com. 7299 IN A 8172.217.4.46

*\-- snip --*

*Listing 2-1: DNS answer of the* google .com *A resource record*

Each section in a DNS reply begins with a header 1, prefixed with a semicolon to indicate that the line is a comment rather than code to be processed. Within the question section, you ask the domain name server for the domain name *google.com* 2 with the class IN 3, which indicates that this record is internet related. You also use A to ask for the A record 4 specifically.

In the Answer section 5, the domain name server resolves the *google.com* A record to six IPv4 addresses. The first field of each returned line is the domain name 6 you queried. The second field is the TTL value 7 for the record. The *TTL value* tells domain name resolvers how long to cache or remember the record, and it lets you know how long you have until the cached record expires. When you request a DNS record, the domain name resolver will first check its cache. If the answer is in its cache, it will simply return the cached answer instead of asking the domain name server for the answer. This improves domain name resolution performance for records that are unlikely to change frequently. In this example, the record will expire in 299 seconds. The last field is the IPv4 address 8. Your web browser could use any one of the six IPv4 addresses to establish a connection to *google.com*.

The AAAA resource record is the IPv6 equivalent of the A record.

**36** Chapter 2

**The Start of Authority Record**

The *Start of Authority (SOA) record* contains authoritative and administrative details about the domain, as shown in Listing 2-2. All domains must have an SOA record.

$ **`dig google.com. soa`**

*\-- snip --*

;QUESTION

google.com. IN SOA

;ANSWER

google.com. 59 IN SOA 1ns1.google.com. 2dns-admin.google.com. 3248440550 900 900 1800 60

*\-- snip --*

*Listing 2-2: DNS answer of the* google .com *SOA resource record*

The first four fields of an SOA record are the same as those found in an A record. The SOA record also includes the primary name server 1, the administrator’s email address 2, and fields 3 used by secondary name servers outside the scope of this book. Domain name servers primarily consume SOA records. However, the email address is useful if you wish to contact the domain’s administrator.

**N O T E** 

*The administrator’s email address is encoded as a name, with the at sign (@) replaced by a period.*

**The Name Server Record**

The *Name Server (NS) record* returns the authoritative name servers for the domain name. *Authoritative name servers* are the name servers able to provide answers for the domain name. NS records will include the primary name server from the SOA record and any secondary name servers answering DNS queries for the domain. Listing 2-3 is an example of the NS records for *google.com*.

$ **`dig google.com. ns`**

*\-- snip --*

;QUESTION

google.com. IN NS

;ANSWER

google.com. 21599 IN NS 1ns1.google.com.

google.com. 21599 IN NS ns2.google.com.

google.com. 21599 IN NS ns3.google.com.

google.com. 21599 IN NS ns4.google.com.

*\-- snip --*

*Listing 2-3: DNS answer of the* google .com *NS resource records*

Like the CNAME record, discussed next, the NS record will return a fully qualified domain name 1, not an IP address.
