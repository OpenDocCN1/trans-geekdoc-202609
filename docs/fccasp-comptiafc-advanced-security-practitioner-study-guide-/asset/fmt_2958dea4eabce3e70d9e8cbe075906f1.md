
# Securing DNS and Directory Services

Before service is enabled on any DNS server, it should be secured. Some of the most popular DNS server software, such as the Internet Systems Consortium's BIND, has suffered from a high number of vulnerabilities in the past that have allowed attackers to gain access to and tamper with DNS servers. Alternatives to BIND such as Unbound are available, and you should consider them if your infrastructure permits. DNS is one of the services that you should secure as there are many ways the attacker can target DNS. One such attack is DNS cache poisoning. This type of attack sends fake entries to a DNS server to corrupt the information stored there. DNS can also be susceptible to denial-of-service (DoS) attacks and unauthorized zone transfers. DNS uses UDP port 53 for DNS queries and TCP port 53 for zone transfers. Securing the zone transfer process is an important security control.

## Securing Zone Transfers

The DNS database consists of one or more zone files. Each zone is a collection of structured resource records. Common record types include the Start of Authority (SOA) record, the A record, the CNAME record, the NS record, the PTR record, and the MX record. There is only one SOA record in each zone database file. It describes the zone name space. The A record is the most common, as it contains IP addresses and names of specific hosts. The CNAME record is an alias. The NS record lists the IP addresses of other nameservers. The PTR record is used for reverse lookups. An MX record is a mail exchange record. This record has the IP address of the server where email should be delivered.

Securing zone transfers begins by making sure that your DNS servers are not set to allow zone transfers. If your host has both external and internal DNS servers, then the security administrator should also close TCP port 53. Internal DNS servers should be configured to talk to only the root servers. If attackers can access DNS information, they can get a virtual map of the network. Understanding the importance of securing zone transfers is essential for both the CASP exam and your work as a security professional. [Exercise 2.6](#c02.xhtml#c02-ex-06) will show you how to check your DNS server for proper configuration.

## Start of Authority

The Start of Authority (SOA) details which DNS server is your primary nameserver, your contact information, when secondary nameservers get updated, and the default time-to-live (TTL) values for your DNS records. The SOA defines general parameters for the DNS zone. One important issue for the CASP is the TTL setting. The TTL gives important information about DNS cache poisoning. The longer the TTL, the less frequently the resource record is read and the lower the possibility it may be poisoned. [Exercise 2.7](#c02.xhtml#c02-ex-07) shows you how to force a zone transfer.

## Secure DNS

The integrity and availability of DNS are critical for the health of the Internet. One common approach to securing DNS is to manage two DNS servers, one internal and one external. Another approach is using DNS Security Extensions (DNSSEC). DNSSEC is a real consideration, since one of the big issues with running two DNS servers is that the external DNS server that provides information to external hosts remains vulnerable to attack. This is because DNS servers have no mechanism of trust. A DNS client cannot normally determine whether a DNS reply is valid.

With DNSSEC, the DNS server provides a signature and digitally signs every response. For DNSSEC to function properly, authentication keys have to be distributed before use. Otherwise, DNSSEC is of little use if the client has no means to validate the authentication. DNSSEC only authenticates the DNS server and not the content. Even if the DNS server is configured for DNSSEC, situations can arise where the server may sign the results for a domain that it is impersonating. You can read more about DNSSEC at `www.dnssec.net`.

## Transaction Signature

Dynamic DNS (DDNS) enables a DNS server to update resource records for clients automatically if their hostnames or IP addresses change. When you are using DDNS, the mechanism used to authenticate updates to a DDNS is known as Transaction Signature (TSIG). TSIG was designed with cryptographic controls and uses shared secret keys and one-way hashing.

When the DNS client and DNS server exchange a set of DNS messages to establish a secure session, the update message sent by the DNS client contains a TSIG record used to validate the DNS client. TSIG is used to provide a means of authenticating updates to a DDNS database.

Although TSIG does offer some level of security, vulnerabilities have been discovered. For example, if an attacker crafts a response without the proper key, a buffer overflow could occur. An attacker who completes this task may potentially crash the server or gain root access to the shell.

## Fast Flux DNS

Another security threat connected with DNS is fast flux DNS. This is a technique that can be implemented with varying levels of sophistication. It is generally incorporated by today's more advanced botnets in order to hide their command and control (C&C) servers. There are two types of fast flux DNS: single flux and double flux. Single flux is a simple method of registering and deregistering DNS A records and is simple to detect and prevent, since it generally works on a single domain. Double flux, however, will frequently use an infected machine, often referred to as a `bot` or a `zombie`, as a proxy server, thereby shielding the C&C server from any prying eyes. In fact, there may be many levels of proxies, making it very difficult to locate these C&C servers. This also makes it difficult to block the IP addresses of these machines using conventional methods. These proxies may frequently register DNS names with a very short TTL value, which should appear suspicious to the registrar where the domains are being registered; however, this registration is often performed in countries that do not enforce laws against cyber crime. Knowledge of these countries and careful monitoring of logs as well as automated detection rules can be paramount to discovery of this type of threat.

## Lightweight Directory Access Protocol

Originally, Lightweight Directory Access Protocol (LDAP) was created to be a lightweight alternative protocol for accessing X.500 directory services. X.500 is a series of computer networking standards covering electronic directory services. X.500 was developed to support the requirements of X.400 email exchange and name lookup.

LDAP uses the same object data format as X.500, where each object is made up of attributes that are indexed and referenced by a distinguished name. Each object has a unique name designed to fit into a global namespace that helps determine the relationship of the object and allows for the object to be referenced uniquely.

Security issues with LDAP include the fact that no data encryption method was available in LDAP versions 1 and 2. Security is negotiated during the connection phase when the client and server begin communications. Options include no authentication or basic authentication. This is the same mechanism that is used in other protocols, such as HTTP.

This process requires the client to identify itself by means of a password that may be sent in the clear or by means of Base64 encoding. The problem with Base64 encoding is that it is weak and easy to decode. One solution to this problem is the Simple Authentication and Security Layer (SASL). SASL has been added to LDAPv3 to include additional authentication mechanisms.

## Secure Directory Services
