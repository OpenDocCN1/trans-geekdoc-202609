
# 5.5.6. XML Injection

XML stands for extensible markup language, and it is often used to transfer messages. XML can be an important part of a web systems infrastructure and as such if unsanitized user inputs are allowed to generate XML the is used in the system many things can go wrong. Using XML injection an attacker may be able to retrieve secret files or create admin accounts. XML injection can be mitigated by input validation or possibly disabling the resolution of external entities in the framework being used.

# 5.5.7. LDAP Injection

Finally, Lightweight Directory Access Protocol (LDAP) is often used to store information about users. As such, it can be found behind many web applications. LDAP also supports complex queries in a similar fashion to SQL. An unsantized user input can lead to a LDAP query with unexpected results.

# 5.5.8. Directory Traversal

A poorly designed web server may be subject to a directory traversal attack. Recall that web servers are designed to serve static content from a particular directory, `/var/www` for example. Now suppose that an attacker submitted a GET request for `http://www.example.com/../../etc/shadow`. It is possible that the web server may actually go up two directories and serve that file.

This can be addressed with file permissions, access controls, and filtering incoming requests. It is important to note that there is more than one way to specify a path in an HTTP request, including using URL encoding, so all possible malicious inputs must be sanitized.

# 5.5.9. URL Hijacking/Typosquating

An unfortunately common, broad-based attack is to buy a domain with a similar name to a very popular domain. When users mistype the popular domain they end up at the malicious actor’s website. For example, imagine if someone registered `gooogle.com` (note the three o’s). They could gain a lot of traffic from people who mistyped `google`.

These sites could be used for ad revenue, phishing credentials, or even possibly to distribute malware. A mitigation that several browsers implement is to keep a list of malicious websites and warn users before they visit them.

# 5.5.10. Domain Hijacking

Domain names expire after a certain period of time and the registrant may forget to renew. In these rare occasions an attacker may actually gain control of a popular domain name, `google.com` for example, and route traffic to their site. The malicious activities are the same as for typosquating, but the attacker does not need to rely on the users making a mistake.

It is also possible to hijack a domain by logging into the domain registration system using stolen/compromised credentials. In this scenario an attacker could still modify a record to point to their server, but wouldn’t have to rely on the company forgetting to renew.

# 5.5.11. Zone Transfer Attacks

On the subject of the domain name system, zone transfer attacks may leak sensitive information about domains. DNS is a distributed system by design and is used for resolving domain names into IP addresses. Due to the distributed nature of the system, protocols were built in for having a single domain served by multiple servers. These servers pass information to each other using a DNS zone transfer.

Typically these communications should be internal as they may leak valuable information regarding the zone. Unfortunately an improperly configured DNS server may advertise its zone transfers publicly. In such a situation an attacker can use the leaked information in the recon phase of an attack.

# 5.5.12. Clickjacking

A website may be designed in such a way that the interface is confusing to the user and they inadvertently click on an advertisement or malicious link. This is common practice on low integrity websites such as streaming sites, torrent trackers, and adult websites. It is often complicated by a poor ad screening or even purposefully making ads that look similar to the content.

# 5.6. Outcomes

# 5.6.1. Remote Code Execution (RCE)

One of the most dangerous outcomes of an attack is Remote or Arbitrary Code Execution. RCE gives the attacker the ability to execute any instructions they want on the compromised machine. Often the attacker will start a shell with administrative privileges so they can do whatever they want. Imagine SSHing into a remote Linux machine and elevating your privileges to root. This is essentially the type of power that can result from RCE. Attackers may also use the RCE to attack the availability of a computing resource by causing a program to terminate. In this situation the RCE is being used as part of a denial of service (DoS) attack.

# 5.6.2. Privilege Escalation

There is no elevator to root, you have to use an exploit.

~ Anonymous

Privilege escalation involves gaining access to protected resources through unintended means. An example would be CVE-2021-4034, a local privilege escalation vulnerability recently discovered in the Linux `pkexec` command. `pkexec` runs with elevated privileges and does not safely parse command line arguments. As such it can be exploited to give a regular user a root shell. This would be an example of local, vertical privilege escalation.

Privilege escalation is typically broken into two categories: horizontal and vertical. Horizontal privilege escalation gives similar access to resources, ie. moving from one user account to another. Vertical privilege escalation gives higher level access, ie. moving from a user account to an admin account. The five main ways privilege escalation is achieved are credential exploitation, vulnerabilities/exploits, misconfigurations, malware, and social engineering.

# 5.6.3. Denial of Service (DoS)

A denial of service attack (Dos) attempts to keep a system from working by overwhelming it with requests. A distributed denial of service attack (DDoS) does the same thing by utilizing many different machines. Typically the attacking nodes for a DDoS attack are members of a botnet, machines that have been exploited previously and are under the attackers control.

DoS attacks can take many forms including:

SYN Floods : A malicious actor can send multiple SYN packets to initiate the TCP three-way handshake. SYN packets are easy to send, but may cause significant resources to be allocated on the server responding to them. Due to the asymettric nature of resource allocation this makes the use of SYN packets particularly suited to DoS attack. SYN cookies can be used to help prevent this kind of attack.

ICMP Floods : Often referred to as pinging, ICMP echo requests can be used to overwhelm a server. Especially when sent from multiple sources. The solution is typically to rate limit ICMP packets on the server.

Buffer Overflows/Exploits : Poorly designed software may fail when it receives unexpected data. This could be something as simple as sending more data than a buffer can hold, or setting the urgent pointer (URG) on a packet destined for port 139 of a Windows system.

Remote Shells

As you have hopefully experienced by completing the labs, Linux systems traditionally have a powerful shell system that uses text commands to control the OS. Through the shell you can create, read, update, or delete files, make network connections, configure kernel parameters, install packages, etc. In fact, all modern operating systems have shells that can be used to control them. On a Windows machine, having access to PowerShell running as an Administrator is all an attacker would need to have complete control over the system. Often the outcome of an attack is being able to interact with a shell remotely on the exploited machine.

In this scenario we say the victim is running a remote shell. Remote shells can run in the background on a victim machine listening on a port for an attacker to connect, but often the exploited machine may not actually have an external IP the attacker can use to connect. In these instances a reverse shell is used. A reverse shell reaches out from the victim to the attacker and establishes a connection from the inside. This is more compatible with the firewalls/NAT routers that sit between most devices and the Internet.

In either case having privileged shell access to a machine over a remote connection allows an attacker to basically do anything they want. To that end, many tools have sprung up to provide remote shell access. A machine may already have a remote shell tool installed, such as an SSH server. Barring that Netcat can be used with any executable to provide access to it over a network. `metasploit` (a very popular pentesting framework) comes with many payloads, most of which are shells of various types. Programs also exist to run shells over ICMP, Discord, IRC, or even DNS!

# 5.7. Lab: MitM with Scapy

In this lab we will use a fake SSH server, `sshesame`, and an interactive packet manipulation program, `scapy`, to disrupt an ongoing SSH session between victim and server, position ourself in the middle of the traffic, and capture the username and password victim is using.

| Name | IP Address |
|------|------------|
| server | 172.20.0.5 |
| victim | 172.20.0.6 |
| attacker | 172.20.0.7 |

For this lab our IP addresses are configured statically and are known to the attacker. It is also assumed that the attacker is on the local network. Lastly victim has been poorly configured to ignore changes to the host key. This is not entirely unreasonable as many users just ignore the warnings and clear out the `known_hosts` file when prompted anyway.

Start by downloading the `scapy.zip` file which contains the Docker Compose configuration we will be using. Uncompress it to a directory where you have write access. This lab will require us to use three terminal windows/tabs: one for the `docker-compose up` command which will show the output of everything running in the background, one for the victim which will show an SSH session with the server, and one for the attacker which we will use to make the attack.

Open three terminals and `cd` into the directory where you uncompressed the lab zip file in each of them. There should be a `docker-compose.yml` file and `server`, `victim`, and `attacker` directories in the directory you are in.

In the first terminal run the `docker-compose up` command to build the images and run the containers:

```
Listing 1. docker-compose up

PS C:\Users\rxt1077\it230\labs\scapy> docker-compose up
```
