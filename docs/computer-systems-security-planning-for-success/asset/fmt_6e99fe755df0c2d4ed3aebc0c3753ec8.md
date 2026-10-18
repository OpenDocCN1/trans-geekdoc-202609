
# 5.8. Review Questions

What can MAC address spoofing allow an attacker to do? What steps can be taken to mitigate this risk?

What is the difference between horizontal and vertical privilege escalation? Give an example of each.

What is XSS and how can it be used in an attack?

# 6. Security Solutions

To help combat security breaches, many different vendors offer security solutions. These may be hardware or software designed to help mitigate a security threat. Security solutions may be created in-house, created custom by a third party, or outsourced and offered as a service. When evaluating solutions it is important to have a plan and understand the features and possible pitfalls of that product.

## 6.1. False Positives / Negatives

When a security solution detects a threat, but no threat exists, that is a `false positive`. Depending on the complexity of the solution it may utilize a set of rules, indicators of compromise, or possibly even artificial intelligence to trigger its warning system. In the case of a solution that creates a lot of false positives, it can be tiring for a team to go through each alert. Eventually teams are conditioned to ignore the alerts, making the security solution useless.

The key to lowering the false positive rate of a system is to better tune the rule set used to trigger the warnings. A security team may spend time determining a baseline of events and looking for abnormalities that correspond to actual attacks. This information can then be used to build a better detection system.

### Webroot Antivirus

[In 2017 a popular antivirus service created a bad rule that identified certain Windows operating system files as threats.](https://www.nbcnews.com/tech/tech-news/popular-antivirus-program-mistakenly-ids-windows-threat-creating-chaos-n750521) The antivirus solution quarantined these files, which were critical for the operation of the machine. The result was a machine that was unusable.

For 13 minutes, Webroot distributed this rule to its antivirus software shutting down operations on an untold number of machines. Fortunately Webroot was able to quickly identify the problem and send out an update which would have allowed the machines to automatically fix the problem. Unfortunately their infrastructure for distributing the update quickly became overloaded.

When a security solution fails to identify a threat, this is known as a `false negative`. While no solution can ever be 100% effective, false negatives can undermine confidence in a product. False negatives may be resolved by a skilled SOC team, closely monitoring what is happening. It is also possible to address false negatives through `Layered Security` a concept that we will cover next.

## 6.2. Layered Security

![](images/layers.svg "fig:")

Given that a single security solution is never 100% effective it makes sense to approach security in layers and use multiple systems. There is often a lot of overlap between solutions and while that may seem inefficient in other fields, in cybersecurity we consider it a benefit. By using multiple solutions, sometimes referred to as multi-layered security or defense in depth, you can build a more robust protection against breaches.

Let’s take a look at an example to see how layered security can help mitigate the effects of a real-world attack. Assume an SOC is supporting a web application on self-hosted machines. A malicious actor wishes to exfiltrate data from the web application. They begin by testing to see if SQL several different SQL injection attacks yield any results.

A well designed web application should sanitize its inputs and may prevent the queries from making it to the database. Similarly an alert team may notice a sudden uptick in SQL queries, far beyond the usual baseline for the application. An IDS (Intrusion Detection System) may flag the queries as known SQL injection attacks. Assuming the attack makes it past the application, team, and the IDS, it is possible that the database user is configured according to the principle of least privilege and the queries will not be executed due to a lack of permissions.

As you can see, any one of these layers may be fail, but by having multiple layers the chance of an attack occurring is greatly diminished.

## 6.3. Network Solutions

Many products are available for handling network traffic. They are typically marketed as either stand-alone devices, software to install on internal devices, or a subscription service that routes traffic through an external appliance. In the age of cloud computing network security as a service is becoming increasingly popular.

### 6.3.1. Firewall

A firewall is a service/software/device that blocks unwanted traffic and permits wanted traffic. Typically a firewall is a barrier between and private network and the Internet.

Software like [nftables](https://wiki.nftables.org/wiki-nftables/index.php/Main_Page) can be used to build a firewall on a Linux router for many interior clients. Interior clients may also run host-based firewalls such as [Windows Defender Firewall](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security). Finally hardware solutions for plug-in firewall devices are available from many vendors including Palo Alto and Cisco. Any combination of these solutions may be used.

Firewalls typically employ rules regarding which packets can come in and how to handle them. For example a firewall may have a rule to `ALLOW` packets from exterior hosts connecting on port 22. This would allow SSH connections. Likewise a firewall may have a rule to track internal to external connection requests and perform network address translation (NAT). On an IPv4 network it is common to have a firewall also perform NAT.

Next-Gen Firewalls (NGFW) perform the same functions of a standard firewall, but also employ an integrated intrusion prevention system (IPS) to mitigate threats. The firewall is a perfect place to perform these actions as it can easily close of connections. NGFW often tout artificial intelligence threat monitoring and automatic threat intelligence updating (typically updating attack signatures). A NGFW can also easily be built on a Linux device by making use of [an IPS](https://www.snort.org/) in conjunction with a netfilter firewall.

Network infrastructure may also make use of a special space `outside` of a firewall called the Demilitarized Zone (DMZ). Servers that need to be directly connected to the Internet are often put in the DMZ so they don’t have a deal with restrictive firewall rules. These servers may be used to detect malicious activity, monitor incoming traffic, or to handle basic requests such as serving static web pages.

The largest firewall in the world is the Chinese Great Firewall, started in 1998 as a way to prevent outside influence in China. It is a system used to block IPs, hijack DNS queries, throttle traffic, and perform MitM decryption. The Great Firewall is made of proxies and firewalls performing packet-inspection and content filtering. VPNs are often employed within China to circumvent the great firewall and the great firewall is continually updated to attempt to detect and shut down this traffic.

### 6.3.2. Proxy

![](images/tls-proxy.svg "fig:")

A proxy typically sits between the users and an external network. Proxies and receive and send requests on behalf of a user, allowing for full control over the traffic going out and coming back in.

Proxies can be used for caching, access control, URL filtering, content scanning, and even packet inspection. Proxy solutions may be explicit or transparent and are offered by many companies including McAfee, Fortigate, Netsparker, and Palo Alto. A typical application of a proxy would be to filter explicit content on a school district network.

Proxies can also be broken into `forward` and `reverse` configurations. A forward proxy passes requests from a private or internal network to the internet. Forward proxies can speed up local requests through caching and validate that the request should be performed. Forward proxies are interoperable with standard firewalls and network address translation (NAT).

Reverse proxies take requests from an external source and pass it to an internal service. This helps prevent clients from having direct access to internal services. Reverse proxies can utilize caching and validate requests as well. A reverse proxy can also be configured to work with a firewall. Whereas it used to be common practice to place a server in a demilitarized zone (DMZ) outside of a firewall, it is now far more common to employ a reverse proxy to reach that server.

### 6.3.3. Load Balancer

A common application for reverse proxies is to act as a load balancer for traffic. Load balancers distribute work, in the form of external client requests, among the internal resources, typically servers.

For example, if a company has four servers supporting a web application, they may employ a reverse proxy load balancer that takes requests from clients and passes that request to one of the four internal servers. Different metrics are used to determine how the servers are utilized including least used (round robin), weighted, least amount of active connections. Load balancers optimize bandwidth and increase availability.

### 6.3.4. VPN

A virtual private network (VPN) is used to encrypt internet traffic between two networks or a client and a network. VPNs have become standard procedure for linking remote offices or connecting remote workers. Given the growth of working from home, almost all users have become familiar with what a VPN is and what it does.

Site-to-site VPNs are typically used for linking offices together. This kind of VPN is on permanently. An example would be linking two college campuses: NJIT Newark and NJIT Jersey City. In this scenario users on either campus expect to be able to connect securely to services on the opposite campus at all times. The traffic is encrypted and carried over the Internet.

Remote access VPNs are used by individuals connecting in to a secure network. This kind of VPN is usually stated through a application such as Cisco AnyConnect. When the application is running the user is able to securely access internal resources as if they were at the office.

Many vendors offer VPN products including Cisco, Citrix, Fortinet, Palo Alto, and Checkpoint. Many open source options also exist for building VPNs including [OpenVPN](https://openvpn.net/), [WireGuard](https://www.wireguard.com/), and [IPsec](https://linuxhint.com/how-to-implement-ipsec-in-linux/).

### 6.3.5. TAP

Sometimes it is necessary for a network or security engineer to monitor what is happening on a particular network segment. In this case a network terminal access point (TAP) can be employed. A TAP creates a copy of network traffic and forwards it to a particular port on a switch or router.

## 6.4. EDR

Endpoint Detection and Response (EDR) is used to secure endpoints: servers, workstations, desktops, mobile devices, etc. EDR is typically implemented as a host-based incident prevention system (HBIPS), software that runs on the endpoint to monitor and collect data.

These systems will usually watch for indicators of compromise, scan for malware, and can even quarantine or shutdown the endpoint as needed. Company hardware is a significant investment for any business and an EDR makes sure that investment is protected. Many systems exist for EDR including FireEye, SEP, and CrowdStrike.

## 6.5. Data Loss Prevention

Data loss prevention (DLP) solutions aim to stop the exfiltration of sensitive data. This could be personally identifying information (PI), medical records, social security numbers (SSNs), credit card numbers, etc. Typically DLP either functions on the endpoint and server, data at rest, or on the network, data in motion.

Network DLP solutions may monitor emails or web traffic for sensitive strings, such as SSNs. When an SSN is detecting in an email, the email is quarantined and an alert is sent. Server and endpoint DLP solutions may periodically scan the system to see if sensitive strings are stored on the system. If it is a system that shouldn’t have access to sensitive data an alert is sent. DLP on an endpoint may also limit tasks like USB usage or bulk data transmitting.

## 6.6. IDS/IPS

Intrusion Detection Systems and Intrusion Prevention Systems are systems that monitor network traffic to detect/prevent attacks. These systems may look for known exploits, such as SQL injection patterns, in the traffic and trigger an alert when detected. An intrusion `prevention` system will take it one step further and actually shut down the connection or kill the offending process.

These systems employ exploit signatures or IDs that are indicators of compromise (IoCs), anomalies, or strange behaviors. The power of an IDS/IPS often comes from how up-to-date it’s signature database is. There are many solutions in the category including Splunk, QRadar, CrowdStrike, and SolarWinds.

## 6.7. Email Solutions

The original protocols used to send/receive email were simple and not designed for the challenges we face today. SPAM and phishing emails are unfortunately common and can be addressed with email client add-ons that scan for viruses or use patterns to identify phishing emails. Many of these tools are already built into Google’s GMail or Microsofts Exchange.

Another large challenge is verifying the sender of an email. Currently three common methods exist: Sender Policy Framework (SPF), DomainKeys Identified Mail (DKIM), and Domain-base Message Authentication, Reporting, and Conformance (DMARC).

SPF utilizes TXT records on a DNS domain to verify the IP of a sender. When inbound mail is received, the SPF information for the domain of the sender is retrieved, giving an allowed list of IPs. For example, NJIT’s SPF record currently looks like this:

```
v=spf1 ip4:128.235.251.0/24 ip4:128.235.209.0/24 ip4:66.207.100.96/27 ip4:66.207.98.32/27 ip4:205.139.104.0/22 ip4:206.79.6.0/24 ip4:209.235.101.208/28 ip4:216.185.73.96/27 ip4:69.196.241.0/28 ip4:69.196.242.128/28 ip4:46.183.242.192/28 ip4:202.38.144.192/28 ip4:69.196.236.208/28 ip4:103.225.232.128/28 ip4:37.216.222.128/28 ip4:64.125.200.96/28 ip4:74.217.49.0/25 ip4:69.25.227.128/25 ip4:52.45.50.190 ip4:198.187.196.100 include:_netblock.njit.edu include:spf.sparkmail.org ~all
```

It is important to note that not all of these IPs belong to NJIT. Some may be groups that send emails on NJIT’s behalf like mass mailers, web applications, etc. When properly configured SPF prevents an attacker from impersonating emails from a domain.

DKIM utilizes public and private key cryptography to ensure that an email originated from a particular SMTP server. Public keys for a domain are advertised through a TXT DNS record for a particular domain. Private keys are used by the SMTP server for that domain to sign the emails being sent. A receiving SMTP server can then verify that the message originated from a valid SMTP server for that domain. Private keys can also be distributed to SMTP servers that send emails on behalf of the domain.

DMARC applies policies to the SPF and DKIM validations. DMARC answers questions like, "What should I do if a message is from a valid SPF IP but doesn’t have a valid DKIM signature?" or "What should I do with a message that looks like SPAM but has a valid DKIM signature?" DMARC puts many of the tools used to verify email together in a layered approach to determine whether to pass, quarantine, or block an email.

## 6.8. SIEM

![](images/seim.svg "fig:")

Security and Information Event management is a system for real-time monitoring of security information. Typically a SIEM system presents a dashboard showing events and has the ability to generate reports or create tickets. It may be separate device, software on an internal device, or even a third party service. Some examples of popular SIEMs are QRadar, Splunk, and Azure Sentinel.

## 6.9. Lab: Exploiting log4j

In this lab we will examine the log4j vulnerability, [CVE-2021-44228](https://nvd.nist.gov/vuln/detail/CVE-2021-44228). This vulnerability takes advantage of a flaw in a common logging library used by many Java applications, including Apache, neo4j, Steam, iCloud, and Minecraft. Any attacker that can cause a message to be logged can use the Java Naming and Directory Interface (JNDI) and cause the target to reach out to another server, LDAP in our example, and load a remote Java class file. This file can contain any code that the attacker wishes to inject into the server process.

This lab uses a Docker Compose configuration to simulate a network with an attacker and a target. The target runs a [known-vulnerable, example application](https://github.com/leonjza/log4jpwn) written by leonjza. This example application logs the `User-Agent` header, request path, and a query string parameter of a request as seen below:
