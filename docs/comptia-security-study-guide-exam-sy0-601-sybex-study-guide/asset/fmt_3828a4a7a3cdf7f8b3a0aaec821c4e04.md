
There are many other options for IP scanning tools, ranging from simple options that use `netcat` to test for open ports to complete tools like the Angry IP Scanner and the Spiceworks IP Scanner. Many others also exist and may be in use in organizations you may work with. They all operate on similar principles: they attempt to connect systems, and then connect to each port on each IP address or system that they are configured to scan and report back what they find.

### Data Transfer and General-Purpose Tools

`netcat` is often called a network Swiss army knife because it can be used for many purposes. It is also a very small program, meaning that it can be easily transferred to systems where a tool like `netcat` might be useful. `netcat` can be used for purposes as simple as banner grabbing to determine what a service is. It can provide a local or remote shell, allow raw connections to services, transfer files, and allow you to interact with web servers.

Connecting to a service with `netcat` is as simple as this:

```
nc [hostname] [port]
```

Commands like SMTP or HTTP can then be directly issued.

`netcat` can act as both a listener and a client, allowing shells or file transfers to be performed. Using `netcat` for file transfer involves first setting up a listener:

```
nc -lvp [port] > /home/example/file.txt
```

Then downloading it using `netcat` is simple:

```
nc [listener IP] [port] < /file/location/for/download/file.txt
```

`netcat`'s wide variety of uses mean that it can be used for many purposes. You can even port scan with `netcat`!

The `curl` utility is found on Linux systems and is used to transfer data via URLs. That means it is frequently used to manually perform HTTP commands like HTTP `get` or to fetch HTTP headers. It can also be used for file transfer via FTP, FTPS, and SFTP, and for general purposes for a wide variety of protocols that use a URL. A sample `curl` command to retrieve a page using an HTTP `get` can be performed using this:

```
curl --request GET https://www.example.com
```

The final general tool in this category is `hping`, a tool used to assemble and analyze TCP/IP packets. Penetration testers and security analysts sometimes need to build a custom packet to test for an issue or a vulnerability, or to see if a firewall will respond properly. Analysis using `hping` can also provide information like OS fingerprinting or help guess at how long a system has been online based on packet details. It is available for both Linux and Windows, making it a useful tool in a variety of circumstances.

### OSINT and Data Gathering Tools

`theHarvester` is an open source intelligence gathering tool that can retrieve information like email accounts, domains, usernames, and other details using LinkedIn; search engines like Google, Bing, and Baidu; PGP servers; and other sources. `theHarvester` can be run from a command line and provided with a domain or URL and a search engine to use. [Figure 12.8](#c12.xhtml#c12-fig-0207) shows the results for our publisher, Wiley (the parent company of Sybex). A Google search provides a list of hosts, using LinkedIn would return the names of employees, and other search engines may supply additional data.

![FIGURE 12.8 theHarvester output for wiley.com](images/c12f008.png)

[**FIGURE 12.8**](#c12.xhtml#R_c12-fig-0207) `theHarvester` output for `wiley.com`

Another way to gather intelligence is to use `scanless`, a port scanner that uses third-party scanners to gather information. The `scanless` tool leverages port scanners like viewdns, yougetsignal, and spiderip. `scanless` then uses those tools to run a port scan without exposing the system that you are running from as the source of the scans. The basic command line is simple and will return port scan data much like an `nmap` scan, with output depending on the scanning tool you have selected:

```
scanless -s [chosen scanning site] -t target
```

It is important to note that `scanless` will run from outside of an organization, rather than inside, and that results will therefore look different than if you ran the scan from a workstation within trust or security boundaries.

The next tool in this list is `Sn1per`, an automated scanning tool that combines multiple tools for penetration testers, including reconnaissance via WhoIs, DNS, and ping; port scanning and enumeration; Metasploit and `nmap` automation; and brute-forcing to attempt to automatically gain access to targets. Whereas `theHarvester` focuses on open source intelligence, `Sn1per` is intended to perform automated penetration testing.

The final tool for information gathering in the Security+ exam outline is `DNSEnum`. This tool is used to find DNS servers and entries for a domain and can be directed to query a specific DNS server or default to the DNS server the system it is running on relies on. [Figure 12.9](#c12.xhtml#c12-fig-0008) shows a `dnsenum` command for `wiley.com`. Note that you can see the primary name servers, the host address for `wiley.com`, and the MX servers that rely on FireEye's cloud service to filter email. As would normally be expected from a properly secured DNS server, both of the primary name servers declined to allow `DNSEnum` to perform a zone transfer as well.

Information gathering tools like these can help network administrators and security professionals check the configuration of their own networks, as well as help penetration testers (or attackers) gather information about their targets. As a security professional, you should be aware of the tools and the types of information they provide so that you can pick the right tool to gather the information you need.

### Packet Capture and Replay

The ability to capture and analyze network traffic is important for security professionals who need to identify attacks, perform passive reconnaissance, and document their own actions on a network during a penetration test. Many Linux and Unix systems have `tcpdump`, a command-line packet capture tool available by default. It can capture packets using a variety of filtering and output options. Since network traffic can be high volume, capturing to a file is often a good idea with `tcpdump`. A typical `tcpdump` command line that captures TCP port 80 traffic from the primary network interface for a Linux system to a PCAP file looks like this:

```
tcpdump -w capture.pcap -i eth0 tcp port 80
```

![FIGURE 12.9 DNSEnum output for wiley.com](images/c12f009.png)

[**FIGURE 12.9**](#c12.xhtml#R_c12-fig-0008) `DNSEnum` output for `wiley.com`

You can also capture packets by source and destination IP, read from a file, and perform other operations that can be useful for security practitioners. [Figure 12.10](#c12.xhtml#c12-fig-0888) shows an example of the traffic captured during an `nmap` port scan of a system using `tcpdump`. Note that `nmap` randomizes the ports in a scan to avoid scanning them in a linear fashion but that a capture file like this allows you to quickly notice that the system is receiving a series of connections that quickly test ports and then end without continuing traffic.

![FIGURE 12.10 tcpdump of a segment of nmap port scanning](images/c12f010.png)

[**FIGURE 12.10**](#c12.xhtml#R_c12-fig-0888) `tcpdump` of a segment of `nmap` port scanning

This figure shows that the traffic is sent from `10.0.2.15` to `10.0.2.4`, and you can see the various tested ports including `21`, `22`, `135` and `445`. The `nmap` starts with an ARP request to get information about `10.0.2.4`.
