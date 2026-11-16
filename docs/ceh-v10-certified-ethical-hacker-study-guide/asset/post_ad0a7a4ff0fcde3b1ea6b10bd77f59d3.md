
to be open before have been identified again. You will also notice that nmap scanned two different systems. This is another way nmap can be told to scan systems rather than ranges or network blocks. If you provide multiple systems on the command line, nmap will perform the same scan on each of the systems specified.

## Operating System Scan with Nmap

```
$ nmap -O 192.168.86.32 192.168.86.30
Starting Nmap 7.70 ( https://nmap.org ) at 2018-07-15 20:54 MDT
Nmap scan report for billthecat.lan (192.168.86.32)
Host is up (0.0039s latency).
Not shown: 995 closed ports
PORT STATE SERVICE
22/tcp open ssh
88/tcp open kerberos-sec
445/tcp open microsoft-ds
548/tcp open afp
5900/tcp open vnc
MAC Address: AC:87:A3:36:D6:AA (Apple)
OS details: Apple Mac OS X 10.7.0 (Lion) - 10.12 (Sierra) or iOS 4.1 - 9.3.3 (Darwin 10.0.0 - 16.4.0)
Network Distance: 1 hop
```

```
Nmap scan report for 192.168.86.30
Host is up (0.0040s latency).
Not shown: 997 closed ports
PORT STATE SERVICE
22/tcp open ssh
111/tcp open rpcbind
3128/tcp open squid-http
MAC Address: 70:4D:7B:61:52:6B (Asustek Computer)
Device type: general purpose
Running: Linux 3.X|4.X
OS CPE: cpe:/o:linux:linux_kernel:3 cpe:/o:linux:linux_kernel:4
OS details: Linux 3.2 - 4.9
Network Distance: 1 hop
```

```
OS detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 2 IP addresses (2 hosts up) scanned in 9.07 seconds
```

One thing to keep in mind when you do an operating system scan is that nmap relies on fingerprints, and unlike people, the same fingerprint can match multiple operating systems. As long as nothing in the network stack has changed, you will find that multiple versions of a commercial operating system will match the same fingerprint. You can see this is the case with Apple Mac OS X, now known as macOS. There are several versions that match the same fingerprint, including some versions of iOS. The version running on the target does fall into the range indicated by nmap. One other thing to keep in mind is that nmap tracks the operating system. The operating system is really the kernel—the piece of software that manages the hardware, manages memory, and manages processes. All the other stuff that helps the user interact with the operating system to do user-useful things is in the operating environment, to help draw distinctions. In the case of Linux, the same kernel may be used across multiple distributions, but since the only thing being identified is the kernel, there is no way to know what distribution. Nmap can't tell you Ubuntu versus CentOS, for example. It only knows the version of the Linux kernel you are running.

## Scripting

We've seen a lot of the functionality that nmap has. Even with all of that functionality, we can go beyond. Nmap includes a scripting engine, which allows you, as an nmap user, to extend the functionality in any way that you would like. It's not entirely about extending the functionality yourself, though. The scripting engine is there, but it's not completely up to you to determine what you want to do with it. There are hundreds of scripts available with the latest version of nmap, and the number continues to grow. They are grouped into categories, which currently are auth, broadcast, brute, default, discovery, dos, exploit, external, fuzzer, intrusive, malware, safe, version, and vuln. You can have nmap run all the scripts from a particular category. The following code is nmap being asked to run all the scripts in the discovery category.

## Nmap Discovery Scripts

```
$ nmap -sS --script=discovery 192.168.86.0/24
Starting Nmap 7.70 ( https://nmap.org ) at 2018-07-21 13:28 MDT
Pre-scan script results:
| broadcast-igmp-discovery:
| 192.168.86.22
| Interface: eth0
| Version: 2
| Group: 224.0.0.251
| Description: mDNS (rfc6762)
| 192.168.86.28
| Interface: eth0
| Version: 2
| Group: 224.0.0.251
| Description: mDNS (rfc6762)
| 192.168.86.32
| Interface: eth0
| Version: 2
| Group: 224.0.0.251
| Description: mDNS (rfc6762)
| 192.168.86.47
| Interface: eth0
| Version: 2
| Group: 224.0.0.251
| Description: mDNS (rfc6762)
```

## Nmap Discovery Scripts (continued)

To use a script, you have to pass the --script= parameter followed by the name of the script you want to run. In addition to using the name of the script, you can indicate the category, as I did in the preceding code. On a Linux system, you will probably find all of the installed scripts in /usr/share/nmap/scripts. On a Windows system, you will find the scripts in the Program Files directory where nmap is installed. You'll notice that the file extension for these scripts is .nse for nmap scripting engine. Scripts are written in the Lua language, and each file can be opened and read, possibly to get details about the function of the script. If you'd rather use nmap to get information about the script, you can use --script-help, passing in the name of the script. As an example, let's say you want to get the details about http-waf-detect.nse. Here you can see how to call nmap to get help and the start of the response from nmap.

## Nmap Script Help

```
$ nmap --script-help=http-waf-detect.nse
Starting Nmap 7.70 ( https://nmap.org ) at 2018-07-21 13:42 MDT
http-waf-detect
Categories: discovery intrusive
https://nmap.org/nsedoc/scripts/http-waf-detect.html
Attempts to determine whether a web server is protected by an IPS (Intrusion Prevention System), IDS (Intrusion Detection System) or WAF (Web Application Firewall) by probing the web server with malicious payloads and detecting changes in the response code and body.
```

Another way of finding this information would be to just go to the script itself. When you are writing nmap scripts, there are variables that get set and one of those is the description. This is the variable that gets printed when script-help is called. Additionally, you'll notice there is a section on usage, indicating how the script should be called from nmap. You'll also notice the require statements at the top. This is where the functionality from the nmap scripting engine is pulled in. These modules are needed for the script to be called from nmap.

## Top of the http-waf-detect.nse File

```
local http = require "http"
local shortport = require "shortport"
local stdnse = require "stdnse"
local string = require "string"
local table = require "table"
```

```
description = [[
Attempts to determine whether a web server is protected by an IPS (Intrusion Prevention System), IDS (Intrusion Detection System) or WAF (Web Application Firewall) by probing the web server with malicious payloads and detecting changes in the response code and body.

To do this the script will send a "good" request and record the response,
afterwards it will match this response against new requests containing
malicious payloads. In theory, web applications shouldn't react to malicious
requests because we are storing the payloads in a variable that is not used by
the script/file and only WAF/IDS/IPS should react to it. If aggro mode is set,
the script will try all attack vectors (More noisy)
]]
```

```
--
-- @usage
-- nmap -p80 --script http-waf-detect <host>
-- nmap -p80 --script http-waf-detect --script-args="http-waf-detect.aggro,
http-waf-detect.uri=testphp.vulnweb.com/artists.php" www.modsecurity.org
--
-- @output
-- PORT STATE SERVICE
-- 80/tcp open http
-- |_http-waf-detect: IDS/IPS/WAF detected
```

In addition to calling individual scripts, you can have nmap select multiple scripts using wildcards. If, for example, you wanted to run all of the scripts related to the Server Message Block (SMB) protocol version 2, you could just indicate that the scripts you want to run are named smb2*. This means any script that starts with smb2 will get run. There are three that will get run if the SMB ports are found to be open. You can see calling the script and the results in the following code listing. You'll notice that the port scan identified port 445 as being open. This is the port used for the Common Internet File System (CIFS), which is an implementation of SMBv2. This is the port that triggered the running of the scripts, meaning that when nmap found the port to be open, it identified all the scripts that had registered that port and nmap ran those scripts.

## Nmap Using Wildcards

```
$ nmap -sS --script "smb2*" -T 4 192.168.86.32
Starting Nmap 7.70 ( https://nmap.org ) at 2018-07-21 15:32 MDT
```
