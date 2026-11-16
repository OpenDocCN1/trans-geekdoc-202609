We start with the request labeled A. This goes to the name resolver, labeled Caching DNS. The caching DNS server checks its cache and sees that it has no IP address stored, so it begins something called a recursive name query or recursive name resolution. It’s called recursive because it will end up with multiple requests that keep getting narrower until we end up with what we want. The caching server will need to start with the TLD. It will have a hints file, indicating the IP addresses for the root name servers. For our example, the caching server will need to identify the server to use for the .com TLD. Once it has identified the server it needs to send a request to, request B goes out, asking the root server for the IP address of the name server for the domain.com domain.

The root server has the name server details for all of the domains that fall under the TLD it is responsible for. The root server will reply to our caching server with the IP address for the name server for domain.com. When we did the whois lookups earlier, at the very end of a whois lookup on a domain will be the name servers for that domain, since the name servers are stored with the domain. This, though, is why what we are doing is called a recursive query. We can’t just ask the root server for the IP address of the hostname, so we have to ask it for a pointer to who to ask next.

Request C is the DNS request asking the name server for domain.com about labs.domain.com. Since labs.domain.com is separate from domain.com, what our caching server gets back is another name server. This means one more request. We are now at the point where the FQDN is being asked for. Request D goes out asking for the IP address of www.labs.domain.com. The authoritative server, which is the one we are asking because it has the authoritative information about that domain, responds with the IP address. It may actually respond with multiple IP addresses, but for our purposes, we’re going to just say it comes back with a single IP. Once the caching server has the IP, it sends the response back to our system, which can then issue request E, which isn’t a DNS request but a connection request to the web server.

Now that you have a handle on the process we are going through to get IP addresses back from DNS servers, we can start looking at tools we can use to get those addresses.

# Using Host

Perhaps the easiest tool to use is host. This is a program that you will find on most Unix-like systems, including Linux systems. It has no Windows analog, unfortunately. If you don’t have it installed by default, you can probably get it installed. Using it is very straightforward. You just pass the hostname you want the IP address for to host and you will get a response. You can see an example of that in the following code.

# DNS Lookup Using host

```
$ host www.sybex.com
www.sybex.com has address 208.215.179.132
$ host www.sybex.com 4.2.2.1
Using domain server:
Name: 4.2.2.1
Address: 4.2.2.1#53
```