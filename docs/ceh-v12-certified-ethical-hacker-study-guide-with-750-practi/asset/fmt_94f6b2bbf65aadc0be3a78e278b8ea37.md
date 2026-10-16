
The root server has the name server details for all the domains that fall under the TLD it is responsible for. The root server will reply to our caching server with the IP address for the name server for `domain.com`. When we did the `whois` lookups earlier, at the end of a `whois` lookup on a domain will be the name servers for that domain, since the name servers are stored with the domain. This, though, is why what we are doing is called a *recursive query*. We can't just ask the root server for the IP address of the hostname, so we have to ask it for a pointer to who to ask next.

Request C is the DNS request asking the authoritative name server for `domain.com` about `labs.domain.com`. Since `labs.domain.com` is separate from `domain.com`, what our caching server gets back is another name server. This means one more request. We are now at the point where the FQDN is being asked for. Request D goes out asking for the IP address of `www.labs.domain.com`. The authoritative server, which is the one we are asking because it has the authoritative information about that domain, responds with the IP address. It may actually respond with multiple IP addresses, but for our purposes, we're going to just say it comes back with a single IP. Once the caching server has the IP, it sends the response back to our system, which can then issue request E, which isn't a DNS request but a connection request to the web server.

While DNS stores mappings between FQDNs and IP addresses, those are not the only data mappings that are stored. Some of the different record types you can and may want to look up include:

*   A: An A record is an address record and it converts an FQDN to an IP address.

*   AAAA: An AAAA record converts an FQDN to an IPv6 address.

*   MX: Every domain has a mail exchanger record, used to indicate the host that email should be sent to for that domain.

*   NS: The name server records are the FQDNs and IP addresses of the authoritative name servers for that domain.

*   SOA: The start of authority record holds information about the zone, including the serial number, indicating when zone information has changed last.

*   CNAME: A canonical name is an alias for an FQDN. This maps one hostname to another hostname or FQDN. The CNAME may refer to specifically a hostname since the domain name may already be assumed if it's in the same domain.

*   PTR: A pointer from an IP address to an FQDN. Unlike an A record, this is not necessary, but it is considered useful. An FQDN always has to map to an IP address but an IP address does not have to map to a hostname. Often multiple FQDNs may map to a single IP address.

There are other records, some of which relate to email security to indicate signing keys to verify messages from a trusted email server. Another record is the TXT record, used to store text entries that don't have specific purposes but can be used for a variety of purposes. Now that you have a handle on the process we are going through to get IP addresses back from DNS servers and some of the information we can collect, we can start looking at tools we can use to get those addresses.

#### Using *host*

Perhaps the easiest tool to use is `host`. This is a program that you will find on most Unix‑like systems, including Linux systems. It has no Windows analog, unfortunately. If you don't have it installed by default, you can probably get it installed. Using it is very straightforward. You just pass the hostname you want the IP address for to `host` and you will get a response. You can see an example of that in the following code.

**DNS Lookup Using `host`**

```
$ host www.sybex.com
www.sybex.com has address 208.215.179.132
$ host www.sybex.com 4.2.2.1
Using domain server:
Name: 4.2.2.1
Address: 4.2.2.1 # 53
Aliases:
 
www.sybex.com has address 208.215.179.132
$ host 208.215.179.132
132.179.215.208.in-addr.arpa domain name pointer motorfluctuations.net.
132.179.215.208.in-addr.arpa domain name pointer managementencyclopedia.org.
132.179.215.208.in-addr.arpa domain name pointer smdashboard.wiley.com.
132.179.215.208.in-addr.arpa domain name pointer elansguides.com.
132.179.215.208.in-addr.arpa domain name pointer currentprotocols.net.
132.179.215.208.in-addr.arpa domain name pointer geographyencyclopedia.com.
132.179.215.208.in-addr.arpa domain name pointer separationsnow.info.
132.179.215.208.in-addr.arpa domain name pointer jcsm-journal.com.
132.179.215.208.in-addr.arpa domain name pointer literature-compass.com.
```

In addition to just a straightforward lookup of an IP address, we can use a different server than the one that is defined as our resolver. You can see in the second request, I added an IP address to the command line. This IP address is a caching server that is available for anyone to use. It was created by BBN Planet in the 1990s and, alongside similar services by Google and Cloudflare, can be used by anyone on the Internet. Since it is also a caching server that is open for anyone to use, we can issue requests to it and it will go through the same process described earlier, just as if it were our own caching server.

You can also see from the example, where it says `host 208.215.179.132`, that you can look up an FQDN from an IP address. DNS servers may store mappings from FQDNs or hostnames to IP addresses, allowing something called a *reverse lookup*. This means that we have an IP address, and we want the hostname that's associated with it. As you can see, often an IP address will have several hostnames associated with it. This may be the case where a web server is hosting virtual servers—meaning the web server can determine what content to serve up based on the hostname in the request. The request for this IP address resulted in 197 responses, but they have been truncated for space.

#### Using *nslookup*

Another tool that can be used is `nslookup`. This can be used just like the program `host`, meaning you could just run `nslookup` `www.sybex.com` and get a response. An advantage to `nslookup`, however, is that you can issue many requests without having to keep running `nslookup`. When you run `nslookup` without any parameters, you will be placed into an `nslookup` shell, where you are interacting with the program, issuing requests. In the following code, you can see an exchange in `nslookup`. We are ultimately looking for the same information as we got earlier using `host`, but we are going about it in a different manner.

**Using `nslookup` for Name Resolution**

```
$ nslookup
> set type=ns
> sybex.com
Server:        192.168.86.1
Address:    192.168.86.1#53
  
 
```

**Non‑authoritative answer:**

```
 sybex.com    nameserver = jws-edcp.wiley.com.
 sybex.com    nameserver = ns.wiley.co.uk.
 sybex.com    nameserver = ns2.wiley.co.uk.
 sybex.com    nameserver = sg-ns01.wiley.com.
 sybex.com    nameserver = bri-ns01.wiley.com.
 sybex.com    nameserver = ns.wileypub.com.
  
 Authoritative answers can be found from:
 > set type=A
 > server ns.wileypub.com.
 Default server: ns.wileypub.com.
 Address: 12.165.240.53#53
 > www.sybex.com
 Server:        ns.wileypub.com.
 Address:    12.165.240.53#53
  
 Name:    www.sybex.com
 Address: 208.215.179.132
 
```

Instead of just looking up the IP address from the FQDN, I used resource records to start. DNS supports multiple resource records, though the most common is the address (A) record. When you see `set type=ns`, I'm telling `nslookup` to issue subsequent requests asking for name server (NS) records. This will tell us the authoritative name servers for the given domain. Once I had the list of NSs, I was able to set the server I was asking to one of the NSs. What this means is that instead of going to my caching server, `nslookup` is going to issue a DNS request directly to the authoritative server, which wouldn't have to do any recursive search since it has the information being requested.

#### Using *dig*
