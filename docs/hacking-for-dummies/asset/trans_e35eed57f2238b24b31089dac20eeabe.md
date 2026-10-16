
A ping sweep of all your network subnets and hosts is a good way to find out which hosts are alive and kicking on the network. A `ping sweep` involves pinging a range of addresses using Internet Control Message Protocol (ICMP) packets. [Figure 9-1](#c09.xhtml#c09-fig-0001) shows the command and the results of using Nmap to perform a ping sweep of a class C subnet range.

![ FIGURE 9-1:  Performing a ping sweep of an entire class C network with Nmap.](images/9781119485476-fg0901.png)

[FIGURE 9-1:](#c09.xhtml#rc09-fig-0001) Performing a ping sweep of an entire class C network with Nmap.

Dozens of Nmap command-line options exist, which can be overwhelming when you want only a basic scan. Nonetheless, you can enter `nmap` on the command line to see all the options available.

You can use the following command-line options for an Nmap ping sweep:

* `-sP` tells Nmap to perform a ping scan.

* `-n` tells Nmap not to perform name resolution.

* `-T 4` tells Nmap to perform an aggressive (faster) scan.

* `192.168.1.1-254` tells Nmap to scan the entire 192.168.1.0 subnet.

#### Using port scanning tools

Most port scanners operate in three steps:

1. The port scanner sends TCP SYN requests to the host or range of hosts you set it to scan.

    Some port scanners perform ping sweeps to determine which hosts are available before starting the TCP port scans.

    ![warning](images/warning.png)Most port scanners scan only TCP ports by default. Don’t forget about UDP ports, which you can scan with a UDP port scanner, such as Nmap.

2. The port scanner waits for replies from the available hosts.

3. The port scanner probes these available hosts for up to 65,534 possible TCP and UDP ports (based on which ports you tell it to scan) to see which ones have available services on them.

The port scans provide the following information about the live hosts on your network:

* Hosts that are active and reachable through the network.

* Network addresses of the hosts found.

* Services or applications that the hosts *may be* running.

After performing a generic sweep of the network, you can dig deeper into specific hosts you find.

#### NMAP

After you have a general idea of what hosts are available and what ports are open, you can perform fancier scans to verify that the ports are actually open and not returning false positives. Nmap allows you to run the following additional scans:

* **Connect:** This basic TCP scan looks for any open TCP ports on the host. You can use this scan to see what’s running and determine whether IPSes, firewalls, or other logging devices are logging the connections.

* **UDP scan:** This basic UDP scan looks for any open UDP ports on the host. You can use this scan to see what’s running and determine whether IPSes, firewalls, or other logging devices are logging the connections.

* **SYN Stealth:** This scan creates a half-open TCP connection with the host, possibly evading IPS systems and logging. This scan is a good one for testing IPSes, firewalls, and other logging devices.

* **FIN Stealth, Xmas Tree, and Null:** These scans let you mix things up a bit by sending strangely formed packets to your network hosts so that you can see how they respond. These scans change the flags in the TCP headers of each packet, which allows you to test how each host handles them to point out weak TCP/IP implementations as well as patches that may need to be applied.

![warning](images/warning.png)Be careful when performing these scans. You can create your own DoS attack and potentially crash applications or entire systems. Unfortunately, if you have a host with a weak TCP/IP stack (the software that controls TCP/IP communications on your hosts), there’s no good way to prevent your scan from creating a DoS attack. A good way to help reduce the chances of such an attack is to use the slow Nmap timing options — Paranoid, Sneaky, or Polite — when running your scans.

[Figure 9-2](#c09.xhtml#c09-fig-0002) shows the NMapWin Scan tab, where you can select the Scan Mode options (Connect, UDP Scan, and so on). If you’re a command-line fan, you see the command-line parameters displayed in the bottom-left corner of the NMapWin screen. This display helps when you know what you want to do and the command-line help isn’t enough.

![ FIGURE 9-2:  In-depth port-scanning options in NMapWin.](images/9781119485476-fg0902.png)

[FIGURE 9-2:](#rc09-fig-0002) In-depth port-scanning options in NMapWin.

![tip](images/tip.png)If you connect to a single port (as opposed to several at one time) without making too much noise, you may be able to evade your firewall or IPS. This scan is a good test of your network security controls, so look at your logs to see what they saw during this process.

#### NETSCANTOOLS PRO

NetScanTools Pro (`https://www.netscantools.com`) is a nice all-in-one commercial tool for gathering general network information, such as the number of unique IP addresses, NetBIOS names, and MAC addresses. It also has a neat feature that allows you to fingerprint the operating systems of various hosts. [Figure 9-3](#c09.xhtml#c09-fig-0003) shows the OS Fingerprinting results while scanning a wireless network access point.

![ FIGURE 9-3:  NetScanTools Pro OS Fingerprinting tool.](images/9781119485476-fg0903.png)

[FIGURE 9-3:](#rc09-fig-0003) NetScanTools Pro OS Fingerprinting tool.

#### Countermeasures against ping sweeping and port scanning

Enable only the traffic you need to access internal hosts — preferably as far as possible from the hosts you’re trying to protect — and deny everything else. This guideline goes for standard ports, such as TCP 80 for HTTP and ICMP for ping requests.

Configure firewalls to look for potentially malicious behavior over time (such as the number of packets received in a certain period), and have rules in place to cut off attacks if a certain threshold is reached, such as 10 scanned ports in 10 seconds or 100 consecutive ping (ICMP) requests.

Most firewalls and IPSes can detect such scanning and cut it off in real time.

![warning](images/warning.png)You *can* break applications on your network when restricting network traffic, so make sure that you analyze what’s going on and understand how applications and protocols are working before you disable any type of network traffic.

### Scanning SNMP

Simple Network Management Protocol (SNMP) is built into virtually every network device. Network management programs (such as HP OpenView and LANDesk) use SNMP for remote network host management. Unfortunately, SNMP also presents security vulnerabilities.

#### Vulnerabilities

The problem is that most network hosts run SNMP enabled with the default read/write community strings of public/private. The majority of network devices that I come across have SNMP enabled and don’t even need it.

If SNMP is compromised, a hacker may be able to gather such network information as ARP tables, usernames, and TCP connections to attack your systems further. If SNMP shows up in port scans, you can bet that a malicious attacker will try to compromise the system.

Here are some utilities for SNMP enumeration:

* The commercial tools NetScanTools Pro and Essential NetTools.

* Free Windows GUI-based Getif.

* Free Windows text-based SNMPUTIL ([`www.wtcs.org/snmp4tpc/FILES/Tools/SNMPUTIL/SNMPUTIL.zip`](http://www.wtcs.org/snmp4tpc/FILES/Tools/SNMPUTIL/SNMPUTIL.zip)).

You can use Getif to enumerate systems with SNMP enabled, as shown in [Figure 9-4](#c09.xhtml#c09-fig-0004).

![ FIGURE 9-4:  General SNMP information gathered by Getif.](images/9781119485476-fg0904.png)

[FIGURE 9-4:](#rc09-fig-0004) General SNMP information gathered by Getif.
