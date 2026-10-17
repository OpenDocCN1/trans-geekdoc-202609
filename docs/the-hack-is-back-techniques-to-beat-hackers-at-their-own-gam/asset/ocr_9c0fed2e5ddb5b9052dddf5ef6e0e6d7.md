To narrow down the responding hosts, we can perform a similar activity, just changing out the location where awk is carving information. Our information will simply be the last item for each line, which is represented with the character `$NF` in awk. This can be passed into another file to reference for further commands. A command to carve out this information is below:

```
```bash
$ cat masscan_out.txt | awk '{print $NF}' | sort | uniq > responding_hosts.txt
34.226.31.104
```
```

# Nmap

Now with our known list of responding ports, we can scan with **nmap** to perform service detection. Leveraging **masscan** first helps us reduce the number of scanning probes required by **nmap** and speeds up the enumeration process. To scan with **nmap**, we are going to take the list of ports returned and place them into our command. The following command is designed to take a close look at the types of services available on the open ports (the **-sV** switch for service Versions), run some common enumeration scripts (the **-sC** switch for Scripts), then place the output of the scan into a set of files labeled **service_scans** (the **-oA** switch for output All types).

```
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
```

Looking closer at our output, what do we see? Another website was either hosted here or intended to redirect to a completely different website! This **logonportal.ml** was not found in any of the initial enumeration, it was only identified during these scans. Paying close attention to the tool output can lead us down new paths with additional information that could be seemingly impossible to find before.

# Forced Browsing

Forced browsing is a technique used to discover additional endpoints and directories on a webpage that are either not listed, sensitive, or forgotten. This commonly results in finding sensitive information, credentials, or API keys that can be leveraged to attack the application or the organization. Many developers take a “security through obscurity” approach to systems as well, which can allow certain vulnerabilities to persist.