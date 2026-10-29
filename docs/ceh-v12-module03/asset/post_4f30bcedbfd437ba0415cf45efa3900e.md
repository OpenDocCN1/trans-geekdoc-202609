
Attackers can use various tools to perform OS discovery on the target machine, including Wireshark, Nmap, Unicornscan, and Nmap Script Engine. Attackers can also adopt the IPv6 fingerprinting method to grab the target OS details.

## OS Discovery using Wireshark

Source: https://www.wireshark.org

To identify the target OS, sniff/capture the response generated from the target machine to the request-originated machine using packet-sniffing tools such as Wireshark, etc., and observe the TTL and TCP window size fields in the first captured TCP packet. By comparing these values with those in the above table, you can determine the target OS that has generated the response.

![](img/198108450322f24970ade227cbf24f47_80_0.png)

Figure 3.76: Wireshark screenshot showing TTL value (Possible OS is Windows)

![](img/198108450322f24970ade227cbf24f47_81_0.png)

## Possible OS is Linux

Figure 3.77: Wireshark screenshot showing TTL value (Possible OS is Linux)

![](img/198108450322f24970ade227cbf24f47_82_0.png)

## OS Discovery using Nmap and Unicornscan

## OS Discovery using Nmap

Source: https://nmap.org

To exploit the target, it is highly essential to identify the OS running on the target machine. Attackers can employ various tools to acquire the OS details of the target. Nmap is one of the effective tools for performing OS discovery activities. In Zenmap, the -O option is used to perform OS discovery, which displays the OS details of the target machine.

![](img/198108450322f24970ade227cbf24f47_83_0.png)

```
nmap -O 10.10.1.11
```

MAC Address: 00:15:5D:01:80:00 (Microsoft)
Device type: general purpose
Running: Microsoft Windows 10
OS CPE: cpe:/o:microsoft:windows_10:1703
OS details: Microsoft Windows 10 1703

Figure 3.78: OS Discovery using Zenmap

## OS Discovery using Unicornscan

Source: https://sourceforge.net

In Unicornscan, the OS of the target machine can be identified by observing the TTL values in the acquired scan result. To perform Unicornscan, the syntax `#unicornscan <target IP address>` is used. As shown in the screenshot, the `ttl` value acquired after the scan is 128; hence, the OS is possibly Microsoft Windows.

![](img/198108450322f24970ade227cbf24f47_84_0.png)

Figure 3.79: OS Discovery using Unicornscan

## OS Discovery using Nmap Script Engine

- Nmap script engine (NSE) can be used to automate a wide variety of networking tasks by allowing the users to write and share scripts
- Attackers use various scripts in the Nmap Script Engine to perform OS discovery on the target machine
- For example, in Nmap, smb-os-discovery is an inbuilt script that can be used for collecting OS information on the target machine through the SMB protocol
- In Zenmap, the -sC option or --script option is used to activate the NSE scripts

![](img/198108450322f24970ade227cbf24f47_85_0.png)

## OS Discovery using Nmap Script Engine

Source: https://nmap.org

Nmap Scripting Engine (NSE) in Nmap can be used to automate a wide variety of networking tasks by allowing users to write and share scripts. These scripts can be executed in parallel with the same efficiency and speed as Nmap. Attackers can also use various scripts in the Nmap Script Engine for performing OS discovery on the target machine. For example, in Nmap, smb-os-discovery is an inbuilt script used for collecting OS information on the target machine through the SMB protocol.

In Zenmap, NSE can be generally activated using the -sC option. If the custom scripts are to be specified, then attackers can use the --script option. The NSE results will be displayed with both the Nmap normal and XML outputs.

```
[root@parrot] /home/attacker
# nmap --script smb-os-discovery.nse 10.10.1.22
Starting Nmap 7.92 ( https://nmap.org ) at 2022-03-25 00:36 EDT
Nmap scan report for 10.10.1.22
Host is up (0.0094s latency).
Not shown: 983 filtered tcp ports (no-response)
PORT      STATE SERVICE
53/tcp    open  domain
80/tcp    open  http
88/tcp    open  kerberos-sec
135/tcp   open  msrpc
139/tcp   open  netbios-ssn
389/tcp   open  ldap
445/tcp   open  microsoft-ds
464/tcp   open  kpasswd5
593/tcp   open  http-rpc-epmap
636/tcp   open  ldaps
1801/tcp  open  msmq
2103/tcp  open  zephyr-clt
2105/tcp  open  eklogin
2107/tcp  open  msmq-mgmt
3268/tcp  open  globalcatLDAP
3269/tcp  open  globalcatLDAPssl
3389/tcp  open  ms-wbt-server
MAC Address: 00:15:5D:01:80:02 (Microsoft)

Host script results:
| smb-os-discovery:
|   OS: Windows Server 2022 Standard 20348 (Windows Server 2022 Standard 6.3)
|   Computer name: Server2022
```

Figure 3.80: OS Discovery using Nmap Script Engine

## OS Discovery using IPv6 Fingerprinting

IPv6 Fingerprinting can be used to identify the OS running on the target machine

IPv6 fingerprinting has the same functionality as that of IPv4

The difference between IPv6 and IPv4 fingerprinting is that the IPv6 uses several additional advanced probes specific to IPv6 along with a separate OS detection engine that is specialized for IPv6

In Zenmap, the -6 option and -O option are used to perform OS discovery using the IPv6 fingerprinting method

```
Syntax: # nmap -6 -O <target>
```

## OS Discovery using IPv6 Fingerprinting

Source: https://nmap.org

IPv6 Fingerprinting is another technique used to identify the OS running on the target machine. It has the same functionality as IPv4, such as sending probes, waiting and collecting the responses, and matching them with the database of fingerprints. The difference between IPv6 and IPv4 fingerprinting is that IPv6 uses several additional advanced IPv6-specific probes along with a separate IPv6-specific OS detection engine. Nmap sends nearly 18 probes in the following order to identify the target OS using the IPv6 fingerprinting method.

- Sequence generation (S1–S6)
- ICMPv6 echo (IE1)
- ICMPv6 echo (IE2)
- Node Information Query (NI)
- Neighbor Solicitation (NS)
- UDP (U1)
- TCP explicit congestion notification (TECN)
- TCP (T2–T7)

In Zenmap, the -6 option along with -O option is used to perform OS discovery using the IPv6 fingerprinting method.

```
Syntax: # nmap -6 -O <target>
```

## LO#06: Demonstrate Various Techniques for Scanning Beyond IDS and Firewall

![](img/198108450322f24970ade227cbf24f47_88_0.png)

## Scanning Beyond IDS and Firewall

Intrusion detection systems (IDS) and firewalls are security mechanisms intended to prevent an attacker from accessing a network. However, even IDS and firewalls have some security limitations. Attackers try to launch attacks to exploit these limitations. This section highlights various IDS/firewall evasion techniques such as packet fragmentation, source routing, IP address spoofing, etc.

## IDS/Firewall Evasion Techniques

Though firewalls and IDSs can prevent malicious traffic (packets) from entering a network, attackers can manage to send intended packets to the target by evading an IDS or firewall through the following techniques:

- 1. Packet Fragmentation
- 2. Source Routing
- 3. Source Port Manipulation
- 4. IP Address Decoy
- 5. IP Address Spoofing
- 6. MAC Address Spoofing
- 7. Creating Custom Packets
- 8. Randomizing Host Order and Sending Bad Checksums
- 9. Proxy Servers
- 10. Anonymizers

## IDS/Firewall Evasion Techniques

Although firewalls and IDS can prevent malicious traffic (packets) from entering a network, attackers can send intended packets to the target that evade the IDS/firewall by implementing the following techniques:

- Packet Fragmentation
- Source Routing
- Source Port Manipulation
- IP Address Decoy
- IP Address Spoofing
- MAC Address Spoofing
- Creating Custom Packets
- Randomizing Host Order
- Sending Bad Checksums
- Proxy Servers
- Anonymizers

## Packet Fragmentation

- Packet fragmentation refers to the **splitting of a probe packet into several smaller packets** (fragments) while sending it to a network
- It is not a new scanning method but a **modification** of the previous techniques
- The **TCP header** is split into several packets so that the packet filters are not able to detect what the packets are intended to do

## SYN/FIN Scanning Using IP Fragments

![](img/198108450322f24970ade227cbf24f47_90_0.png)

![](img/198108450322f24970ade227cbf24f47_90_1.png)

## Packet Fragmentation

Packet fragmentation refers to the splitting of a probe packet into several smaller packets (fragments) while sending it to a network. When these packets reach a host, the IDS and firewalls behind the host generally queue all of them and process them one by one. However, since this method of processing involves greater CPU and network resource consumption, the configuration of most IDS cause them to skip fragmented packets during port scans.

Therefore, attackers use packet fragmentation tools such as Nmap and fragroute to split the probe packet into smaller packets that circumvent the port-scanning techniques employed by IDS. Once these fragments reach the destined host, they are reassembled to form a single packet.

## SYN/FIN Scanning Using IP Fragments

SYN/FIN scanning using IP fragments is not a new scanning method but a modification of previous techniques. This process of scanning was developed to avoid false positives generated by other scans because of a packet filtering device on the target system. The TCP header splits into several packets to evade the packet filter. For any transmission, every TCP header must have the source and destination port for the initial packet (8-octet, 64-bit). The initialized flags in the next packet allow the remote host to reassemble the packets upon receipt via an Internet protocol module that detects the fragmented data packets using field-equivalent values of the source, destination, protocol, and identification.
