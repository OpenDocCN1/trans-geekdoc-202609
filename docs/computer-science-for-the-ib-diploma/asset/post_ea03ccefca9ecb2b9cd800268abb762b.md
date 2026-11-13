
For an office environment, it is usually preferential for the storage of a file server to be present within the file, folder and disk structure of the local computer operating system as a mounted drive letter (Windows) or folder (macOS). To do this, protocols such as Server Message Block (SMB), Network File System (NFS) or Apple Filing Protocol (AFP) are more commonly used.

- Scalability: File servers are typically scaled through adding drives to provide additional storage, and upgrading the speed of the network interface cards when they are shared between many client devices.

- Reliability: RAID (redundant array of independent disks) is a technology that allows for combining multiple physical disk drives into one logical unit. This can be used to pool the storage together to create one larger drive (for example two 1 TB drives pooled together to present as if they were a 2 TB drive), or to provide backup redundancy in the case of one drive failing. RAID also allows for a hybrid approach to mix both functions together.

- Security: Access permissions need to be carefully managed to protect against unauthorized access or alteration of data. These access permissions can typically be set at a file or folder level, and can have either read-only permission or read-write permission.

## Mail server

The mail server stores emails for local users on a network, and exchanges them with other mail servers when users send an email. Commonly used protocols include the SMTP (Simple Mail Transfer Protocol) and POP3 (Post Office Protocol).

- Scalability: Mail servers need to handle large volumes of emails and attachments efficiently. Many companies contract out their mail systems to third-party providers to help manage the demand.

- Reliability: As a critical help system, email servers typically employ such mechanisms as queues and redundant systems to help maintain reliability.

- Security: Strong security systems for email are essential, given the frequency with which email is used as an attack vector for spam, phishing, pharming, malware attachments and other security threats. Best practice now involves the use of email authentication protocols such as SPF (Sender Policy Framework) and DomainKeys Identified Mail (DKIM). SPF allows domain name owners to specify which email servers are authorized to send emails on their behalf. DKIM allows domain name owners to sign their emails digitally with a cryptographic signature that can be checked by the recipient to ensure the email has not been tampered with en route.

![](img/7f4ba44df9c5a19373dcc3ecd776c43a_140_0.png)

## Proxy server

In the business and commercial world of contracts, a proxy is a person you authorize to act on your behalf.

In that vein, a proxy server is traditionally used as the client device on your behalf to browse the greater internet. Its caching functionality is useful as it means it can remember content for you from different addresses and return that request immediately without having to generate additional external traffic. Organizations such as schools and offices may use a proxy server for requests coming from their internal network to reduce costs. As the request being received by a server appears to have originated from the proxy and not the actual client, students may also use proxy servers installed on computers at home as a means of getting around school network filters.

Proxy servers can also be configured to act on behalf of the server rather than just client devices. This arrangement is known as a “reverse proxy”. This arrangement is typically used to help distribute the load of incoming requests among a range of servers, and also to cache the common responses given to save calculation and processing load on the servers themselves.

- Scalability: Reverse proxy configurations can dramatically improve the scalability of a web server to handle significantly more traffic than would otherwise be the case.

- Reliability: When used to balance loads, a proxy server provides fault tolerance capacity.

- Security: A proxy server provides an additional layer of security by shielding internal client devices from direct exposure to the internet.

## Web server

A web server hosts web pages and related content, and serves them to client devices across the internet. The web pages can either be static documents (such as HTML) or dynamically produced at runtime from programming code, in which case the web server sends the request to the application in the style of a reverse proxy, and then sends the reply back to the original client.

Nginx is a popular open source web server.

- Scalability: Modern web servers are quite efficient but, when demand for their services is high, the load is typically distributed across multiple servers, with a reverse proxy server acting as the public interface.

- Reliability: If the web server fails, then all websites it is hosting also fail. As web-based applications become critical infrastructure for some organizations, the importance of reliable web server software grows.

- Security: A web server needs to be secured against attacks such as distributed denial of service. Additionally, modern web servers provide encryption and authentication through SSL to run HTTPS, rather than just HTTP traffic, for a safer browsing experience. Let’s Encrypt (https://letsencrypt.org) provides a free service for obtaining the SSL certificates needed to offer HTTPS browsing through a web server.

## A2.2.3 Networking models

![](img/7f4ba44df9c5a19373dcc3ecd776c43a_141_0.png)

### Client-server

The client-server model is where devices take on the role of either being the client that requests a network service, or the server that provides a network service.

### Benefits:

- Centralized control: It is easier to manage and update systems from a central point.

- Scalability: It is easier to add a more powerful server (for example with increased processing, memory or storage) if it is a central system.

- Efficiency: A server can be optimized for a specific task.

- Security: It is much easier to manage security risks if everything is run from a central point.

### Drawbacks:

- Single point of failure: If the server goes down, all services attached to it fail.

- Single point of risk: If the security of the server is compromised, all data and services managed by the central point are also exposed and vulnerable.

- Cost: Creating a central point to manage all the requests means a significant investment in expensive hardware and software to cope with that demand.

### Real-world applications:

- Web browsing: Clients (browsers) request web pages from servers.

- Email: Email servers manage the sending and receiving of emails to and from client applications.

- Online banking: Central servers handle transactions, authentication and data storage, offering high security and reliability.

![](img/7f4ba44df9c5a19373dcc3ecd776c43a_142_0.png)

### Peer-to-peer

In the peer-to-peer model, there is no server that co-ordinates the network services; each device is both a client and a server, and communicates with all other peers. The provision of network services is distributed across the devices.

The challenge with peer-to-peer is co-ordination, since there is no obvious “authoritative” source to query where to find certain services.

### Benefits:

- Decentralization: There is no single point of failure or risk.

- Cost effective: There is no need to spend money on expensive hardware or software, as the load is shared among all the clients themselves.

- Scalability: As the size of the network grows, so too does the scale of services it can provide. Each additional peer also adds additional capacity.

- Direct sharing: Services can be provided directly from one computer to another, reducing bottlenecks.

### Drawbacks:

- Co-ordination: Maintaining settings, security patches and synchronization of data across multiple nodes on the network can be very challenging.

- Reliability: Since services are being provided by peers, which are just client devices on the network, if someone turns their device off, then it is no longer providing whatever services it was supplying to the network. Availability of systems and resources on the network can vary without much notice.

## Common mistake

### Networking models

Don't oversimplify the distinction between client–server and peer-to-peer models. Understand the nuances involved that might make one more suitable than the other for specific scenarios. Failing to consider scalability and maintenance aspects can lead to incomplete understandings.
