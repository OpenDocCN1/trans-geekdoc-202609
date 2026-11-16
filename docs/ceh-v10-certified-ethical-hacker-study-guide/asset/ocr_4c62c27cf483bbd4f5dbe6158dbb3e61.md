that script. The name of the script, smb-os-discovery, is shown in the output. This is a Windows system that has been set up for sharing. You’ll see that nmap has identified it very specifically, down to the service pack that has been installed. Interestingly, there are several other systems on the network where SMB-based sharing is enabled, but none of them get identified. The big difference between those and this one is that those systems only have port 445 open while this one also has ports 135 and 139 open.

# smb-os-discovery Scan Output

```
Nmap scan report for stevedallas.lan (192.168.86.50)
Host is up (0.00058s latency).

PORT    STATE SERVICE
135/tcp open  msrpc
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds
MAC Address: 46:5E:C8:0A:B7:D1 (Unknown)

Host script results:
| smb-os-discovery:
|   OS: Windows 7 Professional 7601 Service Pack 1 (Windows 7 Professional 6.1)
|   OS CPE: cpe:/o:microsoft:windows_7::sp1:professional
|   Computer name: stevedallas
|   NetBIOS computer name: STEVEDALLAS\x00
|   Workgroup: WORKGROUP\x00
|_  System time: 2018-08-17T20:30:27-06:00
```

There are several important pieces of information we can use nmap to look for. There are enumeration scripts for users, groups, services, processes, and shares. Some of these require authentication before the remote system will give anything up. Microsoft began disabling null session authentication in Windows Server 2008 R2 and Windows 7. Any operating system after that will require authentication before accessing the interprocess communication needed to extract the information requested. However, the setting can be disabled, and you never know when you will run across very outdated or misconfigured systems. You can see the failure of the share enumeration script in nmap here. The listing shows that even though authentication was required, it still attempted common share names.

# Enumerating Shares with Nmap

```
Nmap scan report for stevedallas.lan (192.168.86.50)
Host is up (0.00040s latency).

PORT    STATE SERVICE
135/tcp open  msrpc
```