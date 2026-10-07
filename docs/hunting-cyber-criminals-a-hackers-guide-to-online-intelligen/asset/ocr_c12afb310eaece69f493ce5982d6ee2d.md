# Chapter 4 Looking for Network Activity (Advanced NMAP Techniques) 69

Most scans only focus on TCP ports. Several services and ports use UDP to communicate and are often missed. Our previous scans (-s, -sX, etc.) will not find UDP ports. To find these ports and services, we need to include the -SU switch.

+   - scanflags: This will tell Nmap which types to use. When running an NMAP scan, you have to define this setting. Some types include null scan, FIN scan, and Xmas scan. --scanflags allows you to set multiple scan types.

+   - Settings worth trying are PSH, FINSH, and SYNFIN. PSH will try to get a response by manipulating the PSH flag of a TCP header. FINSH will try the same tactic but will also try manipulating the FIN flags. SYNFIN will try manipulating the FIN flags and will also try to get a response using the SYN/ACK method.

Let's run a full scan of pepsi.com:

```
root@OSINT: nmap -v -p - -U pepsi.com --scanflags PSH
```

The results of this scan were not ideal. All parts are coming back as/ filtered:

```
Nmap 7.70 ( https://nmap.org ) at 2018-12-11 01:03 CST
Initiating Ping Scan at 01:03
Scanning pepsi.com (18.214.229.99) [4 ports]
Completed Ping Scan at 01:03, 0.06s elapsed (1 hosts)
Initiating Parallel DNS resolution of 1 host. at 01:03
Completed Parallel DNS resolution of 1 host. at 01:03, 0.00s elapsed
Initiating Xmas Scan at 01:03
Scanning pepsi.com (18.214.229.99) [65535 ports]
Xmas Scan Timing: About 18.48m done; ETC: 01:06 (02:17 remaining)
Stats: 00:39 elapsed, 0 hosts (1 up), undergoing Xmas Scan
Xmas Scan Timing: About 25.85m done; ETC: 01:06 (01:52 remaining)
Xmas Scan Timing: About 53.74m done; ETC: 01:06 (00:59 remaining)
Completed Xmas Scan at 01:05, 117.00s elapsed (65535 total ports)
Initiating UDP Scan at 01:05
Scanning pepsi.com (18.214.229.99) [65535 ports]
Stats: 02:17 elapsed; 0 hosts (1 up), undergoing UDP Scan
UDP Scan Timing: About 11.73m done; ETC: 01:08 (02:30 remaining)
UDP Scan Timing: About 35.76m done; ETC: 01:08 (01:31 remaining)
UDP Scan Timing: About 57.06m done; ETC: 01:07 (00:40 remaining)
Completed UDP Scan at 01:07, 108.80s elapsed (65535 total ports)
map scan report for pepsi.com (18.214.229.99)
Host is up (0.058s latency).
drdrecord for 18.214.229.99: ec2-18-214-229-99.compute-1.amazonaws.com
All 131070 ports on pepsi.com (18.214.229.99) are open|filtered
```