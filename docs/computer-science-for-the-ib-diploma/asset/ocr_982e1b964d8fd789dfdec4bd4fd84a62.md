device connects to the network. If the DNS server that receives the request does not know the answer to the query, it asks its DNS server, and so on up the chain until a server can provide a response. The DNS server then typically caches that response for a while in case it receives the same query.

On Windows computers, the nslookup terminal command allows you to execute DNS queries, and on macOS machines use the host command. In Python, there is a built-in dns.resolver module that you can use.

```
Python
import dnspython as dns
import dns.resolver
domain = "www.example.com"
try:
    resolver = dns.resolver.Resolver()
    answer = resolver.resolve(domain, "A")
    for record in answer:
        print(record.to_text())
except dns.resolver.NXDOMAIN:
    print(f"The domain {domain} does not exist.")
except dns.resolver.Timeout:
    print(f"The DNS lookup for {domain} timed out.")
except dns.resolver.NoAnswer:
    print(f"No answer found for {domain}.")
except Exception as e:
    print(f"An error occurred: {e}")
```

+   **Scalability:** DNS uses a distributed database and caching. This system allows for the global domain name system to manage with ease the billions of requests made per day.

+   **Reliability:** DNS is a mission-critical system for the internet. Any downtime, particularly from the upstream servers, can affect many thousands or millions of client devices. With that in mind, the system is built with a lot of redundancy in place, where each server typically has at least three alternatives to query.

+   **Security:** Given the global importance of DNS, it is frequently the subject of malicious behaviour. The key domain name servers around the world require extremely robust security systems including firewalls, intrusion detection systems and other countermeasures.

# **Dynamic Host Configuration Protocol (DHCP)**

As previously discussed in Section A21.4, DHCP is responsible for assigning IP addresses and network settings to devices that request them on the network.

# **File server**

A file server provides a centralized location to store, access and manage files. There are several commonly used approaches for this.

FTP (file transfer protocol) or SFTP (secure FTP) are protocols that are commonly used for accessing remote systems for the transfer of files. FTP usually involves opening dedicated FTP transfer utility software to perform the task.