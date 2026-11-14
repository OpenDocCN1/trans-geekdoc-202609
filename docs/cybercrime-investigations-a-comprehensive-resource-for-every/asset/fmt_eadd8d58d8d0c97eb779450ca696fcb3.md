
IP addresses traditionally use the `IPv4` format, which uses four sets of numbers separated by periods. The entire address is stored in four bytes, and each byte can store a number from 0 to 255. These four numbers are displayed with decimals in between, allowing for IP addresses ranging from `0.0.0.0` to `255.255.255.255`.

In establishing the `IPv4` protocol, some IP address ranges were reserved exclusively for private use. Any address within these ranges cannot be a public IP, but is reserved for private companies and individuals to use in their local internal or home networks. When a local network is established, the administrator decides what IP addresses within the private ranges to use. You don’t need permission from anyone, and different companies and individuals can use the same private IP addresses in their respective private networks.

The private IP address ranges are:

- `10.0.0.0` to `10.255.255.255`
- `172.16.0.0` to `172.31.255.255`
- `192.168.0.0` to `192.168.255.255` (most home networks are in this range)

IP addresses are a common clue regarding network and Internet activity, and investigators should be knowledgeable about whether an IP address is private or public. If it is a private IP address, you look within its local network to identify the device, including by looking at the routing tables. If it is a public IP address, you need to look to see what ISP is assigned that IP address. There are a number of reputable and free online services to look up IP addresses.

Thanks to network address translation (`NAT`), a public IP address is often shared by more than one device. If a cybercrime investigator learns that a public IP address was used to commit a crime, investigation may reveal that the public IP address was shared by many computers on the local area network. The investigator would then examine local network records showing which device (and which private IP address) was used to commit the crime. Other investigation avenues would also be followed to identify the specific computer and user involved.

The Internet is outgrowing `IPv4`, as there are too many people and devices needing an IP address. A new addressing system, called `IPv6`, was developed to allow for more addresses. `IPv6` is a 16-byte system, allowing millions of additional address combinations to be generated. The `IPv6` addresses are written in hexadecimal form, separated by colons, and might look something like this:

```
2001:4860:4860:0000:0000:0000:0000:8888
```

Because `IPv6` addresses are so much longer, there are some conventions for shortening how they are written where the value of certain bytes is zero (`0000`). One way to do this is simply to delete the four zeroes, resulting in two back-to-back colons (`::`).

Thus, the above address could be shortened to this:

```
2001:4860:4860::8888
```

Investigators may encounter both `IPv4` and `IPv6` addresses when looking at records of Internet activity.

### 3.5.3 TCP versus UDP

While IP addresses are the addressing system on the Internet that allow computers to find one another, computers still need a common language to talk to each other. In network speak, that language is known as a protocol, and there are two main protocols for Internet communication – Transmission Control Protocol (`TCP`) and User Datagram Protocol (`UDP`). `TCP` is a controlled form of communication that reliably delivers data exactly as it is sent and checks regularly to make sure nothing is missing or got misrouted through the Internet as the packets were separated and then reassembled. `TCP` is used for many of the Internet’s core functions, such as email and websites. `TCP`’s accurate process takes time, however, and slows down the transfer of data.

`UDP`, on the other hand, is faster but less accurate. It is used for transferring large amounts of data quickly, such as for streaming music or video, or for multi-player video games. `UDP` does not check to ensure all the data is received exactly as sent, because that level of precision is not needed for these purposes. A small loss or error in packet delivery will not have a noticeable effect upon your movie viewing, but waiting for 100% packet delivery would be a noticeable interruption.

### 3.5.4 Domain Name System (DNS)

As we mentioned, computers communicate with one another on the Internet by specifying both a destination and origination IP address. For computers, IP addresses are easy to remember, but for us humans, IP addresses are inconvenient. Imagine if you had to remember an `IPv4` address to go to a website? You would have to type something like `72.167.241.180` into your web browser address bar to visit it. But thanks to the domain name system (`DNS`), we do not have to do that. Instead, we can type the domain name of our website (such as `cybercrimeinvestigationsbook.com` or `cnn.com`) into the address bar. The domain name system will look up that domain name in a database and direct the computer to the IP address where the website is hosted.

To rent a domain name, you first have to go to a domain name registrar and check to see if the domain name is available. If it is available, you can rent it for a chosen period of time. The domain name includes a specific top-level domain suffix (such as `.com`, `.org`, or `.net`). `CNN.com`, for example, is a completely different domain name from `CNN.net`. When renting (registering) a domain name, you are asked to provide contact information. This registration information might be made public, but domain registrars usually offer the option of keeping it private for an extra fee.

Cybercriminals may register domain names that sound similar to legitimate businesses or services to trick unsuspecting users (such as domain names similar to the websites of banks and credit card companies). They also can manipulate the domain name system to misdirect website traffic to the wrong website server, so that a user trying to reach a legitimate company’s website is directed to the criminals’ fake website instead. There are many open source tools to investigate domain name registration. In a law enforcement investigation, subpoenas to domain name registrars and website hosting companies for customer registration and usage details also can yield helpful information.

### 3.5.5 Website Hosting

After a domain name is registered (rented), the registrant may decide to host a website at that domain. Web hosting services – which are companies that provide server space for the websites of many customers – make this easy. The domain name system (`DNS`) is notified that the website’s domain is hosted at the particular IP address of the server, so that website visitors can be routed there. Using a hosting service is not required; anyone could host a website from his or her personal or business computer.

Often, multiple websites will share the same IP address – a practice known as shared website hosting. This sharing system is for websites that do not have a lot of traffic, allowing the data for many websites to share the IP address and server. Some websites need a dedicated IP address because the amount of traffic they receive requires the entire capacity of a server and the IP address’ entire bandwidth. Some websites even use multiple IP addresses and multiple servers to handle the volume of their business. A global website like `Google.com` or `CNN.com` will need multiple IP addresses and servers all over the world, so that users are routed to an IP address and server closer to them. Sophisticated load balancing may take place when some servers or regions are overloaded – or attacked – so that extra traffic can be transferred to other sites.
