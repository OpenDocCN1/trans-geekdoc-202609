
```text
[INF] Enumerating subdomains for m4lwhere.org
webshell.m4lwhere.org
notes.m4lwhere.org
magento.m4lwhere.org
[INF] Found 3 subdomains for m4lwhere.org in 10 seconds 338 milliseconds
```

Subfinder’s power comes from not only its speed but how it can be piped into other tools. When using the **-silent** switch, the output is only the found subdomains. This can be paired with other tools from ProjectDiscovery tools and will be explored further in this book as well.

```text
$ subfinder -d m4lwhere.org -silent
notes.m4lwhere.org
magento.m4lwhere.org
webshell.m4lwhere.org
```

## *Certificate Transparency Logs*

The Certificate Transparency Logs are a set of hostnames and certificates that are required to be published by a Certificate Authority (CA) upon issuance of a certificate. This is to ensure that the digital certificate ecosystem is open, accessible, and trustworthy for the Internet at large – a byproduct of this allows us to enumerate additional subdomains. The **amass** and **subfinder** tools use these logs to help find more hostnames, however, manual analysis can reveal new and interesting subdomains.

Several websites can be used, one of this author’s favorites is the **crt.sh** website ([https://crt.sh](https://crt.sh)). The Censys website ([https://censys.io](https://censys.io)) is another wonderful resource as well.

It’s not unusual to add additional **Matching Identities** that have an internal domain scheme, such as **.local** for the certificate. Many organizations leverage DMZ hosts which share both an internal and external hostname – reviewing the certificate transparency logs can help us uncover this intelligence. For the certificate, many organizations leverage DMZ hosts which share both an internal and external hostname – reviewing the certificate transparency logs can help us uncover this intelligence.

![](img/181571ad74cba0e6a2f38fcd2658651e_69_0.png)

**FIGURE 3.4**  Reviewing the certificate transparency logs at crt.sh to help enumerate new subdomains.

DNS is a key tool in modern networks today. Large organizations will have a very large DNS footprint, especially within developer-heavy organizations. These types of companies will likely allow certain subdomains to be automatically registered and updated within DNS, such as **qa.m4lwhere.org**, where developers can register their test machines underneath. QA and Testing machines almost always are less secure and can likely leak credentials for plunder.

## Port Scanning

Port scanning is a technique where we attempt to identify which ports may be providing services to the Internet. Many times, organizations unintentionally expand their attack surface by opening certain ports without knowledge or proper authorization. Port scanning is a common technique used in enterprise network hacking and exploit attempts, but it is also very common for web services to be hosted on ports other than 80 and 443. For this reason, we will explore further in depth about port scanning and identify where web services may be served on non-default ports.

Generally, these web ports other than 80 and 443 indicate a potential for less secure or even completely vulnerable web services which could be used to compromise the underlying host. For example, a developer who creates a web application designed for public consumption may establish the application on port 443 and redirect traffic from port 80 to 443. However, this developer also created a debugging version of this web application hosted on port 65001 – surely nobody would consider connecting to a website on port 65001 right?

In our arbitrary example, let’s believe that our naïve developer decided to record all logged-in users and their session management information for easy troubleshooting. While there is certainly convenience to troubleshooting legitimate session management problems, leaving this data available to any connected individual (logged in or not) can easily allow session hijacking vulnerabilities. Imagine leaving the PIN code to open your garage door to your house available for anyone to read! Now that we have an idea of a scenario, let’s put our skills to work and identify what activity is occurring on our target.

**Masscan** and **nmap** are the two most ubiquitous tools for port scanning. Think of **masscan** as a tool used to scan as many ports as possible as quickly as possible, while **nmap** is a precise tool to determine the service running on that port. For our workflow, we will scan a large number of ports with **masscan**, and then re-scan the responding ports with **nmap** to determine what service may be running.

### *Masscan*

Let’s begin by scanning all possible TCP ports (up to 65,535) with **masscan**. Since we’ve completed a DNS check, we can easily import the list of IP addresses using the **-iL** switch (think “in List” to help remember it). We’re going to use the tee command as well to display the **masscan** activity to our terminal while simultaneously saving it to a file for later use.

```bash
$ sudo masscan -p 0-65535 --rate 1500 34.226.31.104 | tee masscan_out.txt
Starting masscan 1.3.2 (http://bit.ly/14GZzCT) at 2023-05-01 10:46:49 GMT
Initiating SYN Stealth Scan
Scanning 1 hosts [65536 ports/host]
Discovered open port 80/tcp on 34.226.31.104
Discovered open port 443/tcp on 34.226.31.104
```

With the list of responding ports, we can carve them out and provide them to **nmap** in a functional manner. For the example above, it was simple enough to see only two responding ports. However, in examples of dozens or hundreds of hosts, there can easily be thousands of open ports which is much more difficult to manage. The GNU tool **awk** makes this easy, allowing us to create a comma-delimited list of known open ports to place into **nmap**. Syntax to accomplish this, assuming an output of the **masscan** activity using tee, is below.

```bash
$ cat masscan_out.txt | awk '{print $4}' | awk -F/ '{print $1}' | sort | uniq | tr '\n' ','
```

This awk command creates a list of ports found, sorts them, and then returns only the unique ports within the list. Finally, the tr command translates the newlines (“\n”) into a single line of comma-separated port numbers, easy and ready to provide into a **nmap** command. From this set of unique ports, we can pass them into **nmap** to ensure we’re only probing ports that are within known open ports.

To narrow down the responding hosts, we can perform a similar activity, just changing out the location where awk is carving information. Our information will simply be the last item for each line, which is represented with the character `$NF` in awk. This can be passed into another file to reference for further commands. A command to carve out this information is below:

```bash
$ cat masscan_out.txt | awk '{print $NF}' | sort | uniq > responding_hosts.txt
34.226.31.104
```

### Nmap

Now with our known list of responding ports, we can scan with **nmap** to perform service detection. Leveraging **masscan** first helps us reduce the number of scanning probes required by **nmap** and speeds up the enumeration process. To scan with **nmap**, we are going to take the list of ports returned and place them into our command. The following command is designed to take a close look at the types of services available on the open ports (the **-sV** switch for service Versions), run some common enumeration scripts (the **-sC** switch for Scripts), then place the output of the scan into a set of files labeled **service_scans** (the **-oA** switch for output All types).

```text
sudo nmap -iL responding_hosts.txt -p 80,443 -sV -sC -oA service_scans
Starting Nmap 7.93 ( https://nmap.org ) at 2023-05-01 06:54 EDT
Nmap scan report for ec2-34-226-31-104.compute-1.amazonaws.com
(34.226.31.104)
Host is up (0.023s latency).

PORT    STATE SERVICE  VERSION
80/tcp  open  http     Apache httpd 2.4.41
|_http-title: Did not follow redirect to https://logonportal.ml/
|_http-server-header: Apache/2.4.41 (Ubuntu)
443/tcp open  ssl/http Apache httpd 2.4.41 ((Ubuntu))
|_http-title: m4lwhere.org Intel
|_http-server-header: Apache/2.4.41 (Ubuntu)
| ssl-cert: Subject: commonName=m4lwhere.org
| Subject Alternative Name: DNS:m4lwhere.org
| Not valid before: 2023-03-17T16:33:41
|_Not valid after: 2023-06-15T16:33:40
|_ssl-date: TLS randomness does not represent time
Service Info: Host: logonportal.ml

Service detection performed. Please report any incorrect results at
https://nmap.org/submit/.
Nmap done: 1 IP address (1 host up) scanned in 19.53 seconds
```

Looking closer at our output, what do we see? Another website was either hosted here or intended to redirect to a completely different website! This **logonportal.ml** was not found in any of the initial enumeration, it was only identified during these scans. Paying close attention to the tool output can lead us down new paths with additional information that could be seemingly impossible to find before.

### Forced Browsing

Forced browsing is a technique used to discover additional endpoints and directories on a webpage that are either not listed, sensitive, or forgotten. This commonly results in finding sensitive information, credentials, or API keys that can be leveraged to attack the application or the organization. Many developers take a “security through obscurity” approach to systems as well, which can allow certain vulnerabilities to persist.
