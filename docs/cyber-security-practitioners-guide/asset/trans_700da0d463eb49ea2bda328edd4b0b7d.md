
进入`/path/to/xxx`目录，找到`xxx.json`。

在表达式`cvar = avar + bvar`中，加法运算符（`+`）将`avar`与`bvar`相加，得到它们的和`cvar`

在`List.of(arg0, arg1, arg2)`中，`List`接口的工厂方法`of()`接受一系列的元素，返回包含它们的只读列表。

之后我们这样调用`cmd`命令：`cmd arg0 arg1 arg2`。

```
if (condVar > someVal) {console.log("xxx")}
```

### 1.3.1.*Exfiltration using DNS aka DNS tunnelling*

DNS as a protocol is often allowed outbound even though DNS queries on a network should be resolved by internal DNS servers. Although DNS queries use UDP for speed the communication is 2-way in that a DNS response is expected. The DNS protocol only allows packets of 512 bytes, so to transfer any amount of data many queries need to be sent in the form of multiple packets to the same parent domain.

A DNS query will always find its way to the authoritative DNS server for the domain queried, see [Fig. 1.1](#chapter1.xhtml#fig1.1). The endpoint of the attack is therefore a server acting as an authoritative DNS server. DNS tunnelling is therefore a covert way of exfiltrating data and several toolkits are available with which to do this. To encode the communication, Base32/Base64 Binary encoding or Hex encoding is often used. The responses can either be CNAME (limited to 63 characters) or TXT (limited to 220 characters). EDNS can also be used to increase the payload.

![image](images/fig1.1.jpg)

**Fig. 1.1.**Outbound DNS request followed by response.

### 1.3.2.**DNS tunnelling tools**

There are several tools available to effect DNS tunnelling. They are:

•`DeNiSe` — This is a Python script for DNS tunnelling.

•`Dns2tcp` — This exfiltrates data to an authoritative DNS server using UDP port 53.

•`Dnscat2` (`Dnscat`, 2018) — This tool is specifically designed with Command and Control attacks in mind and is available as Windows and Linux binaries.

•`Iodine` — Iodine is a more recent tool that has client and server components. A VPN tunnel is effectively set up between the client and server using a different IP range to the physical IP addresses (Iodine, 2014).

•`Meterpreter DNS Tunnel` (`K-Max`, 2018) — Uses Kali as the attacking tool and a small payload on the compromised workstation.

Improvements to these existing tools are discussed by Revelli and Leidecker (2009).

Using varied name server queries and varied TXT responses, various tools have been developed, which has led to the development of NSTX (Name Server Transfer Protocol), another technique for exploiting DNS.

The tools `Iodine` and `DNScat2`, which are available for DNS tunnelling, require local administrative rights to install, and `DNScat2` is detected by Sophos and AVG. Because having administrative rights on a workstation is not possible on a secured network, these tools are theoretically not a threat; however, this does not mean that the vulnerability is removed, as a new method using PowerShell could still work. A recent example of a DNS exfiltration tool is `DNSExfiltrator` (`DNSExfiltrator`, 2018), which has a JavaScript client that could be triggered by a cross-site script or rogue link.

### 1.3.3.*DNS tunnelling detection*

According to Zimba and Chishimba (2017) one of the greatest challenges in detecting DNS tunnelling is that most firewalls and IDS devices do not inspect DNS traffic. Mehmet and Ince (2016) highlight that if a workstation’s configured DNS servers cannot resolve external DNS, DNScat2 can be configured to exfiltrate data using any DNS cache server that a workstation can communicate with.

DNS tunnels can be detected based on the entropy of requested hostnames (Butler and Grady, 2011). The number of DNS queries of a hostname for a given domain could also be an indicator.

Logging of DNS requests is therefore important as this provides evidence of DNS exfiltration and of the location where data is being exfiltrated to. An examination of the ownership of a domain name may provide some evidence of the attacker’s identity should they have been careless enough not to use fake details. The obvious arguments against DNS logging are the sheer size of the logs that would be produced, and that these logs would need to be archived and managed.

Although DNS tunnelling might look complicated it is much safer an option for an attacker as DNS requests are less likely to be logged compared with HTTP/HTTPS requests which would be logged by a web proxy or outgoing SMTP email, which in turn would be logged by an email gateway.

DNS tunnelling is interesting in that although DNS is a layer 7 protocol, the object of DNS tunneling is to establish TCP communication (which would be layer 3 — the network layer) over DNS.

Netflow’s FlowPro Defender is a tool that can be used to detect DNS tunnelling (Scott, 2016).

DNS logging allows one the opportunity of detecting requests to dynamic DNS hosts. Evidence of DNS tunnelling will be found in DNS Cache server logs. The requests will make use of the maximum DNS packet size which is 253 characters, with a maximum of 63 characters per label. This is defined in RFC1035 (Mockapetris, 1987) as x.y.z where y.z is a parent domain and x is (255 — length (y.z) – 63 – 63 – 63) characters (Dooley and Rooney, 2017).

DNS URLs over 52 characters are not normal, so in simple terms the first sign of something not being right is a long DNS frame (Guy, 2009). The next giveaway is the entropy of the first label. If a label is the first label of a DNS tunnel, it would be expected to be encoded with base32 giving a higher entropy (Butler and Grady, 2011).

DNSSEC may prevent DNS cache servers from DNS poisoning. However, as DNS exfiltration techniques use valid DNS packets, DNSSEC does little to prevent DNS tunneling. The reason for this is that DNSSEC is designed as a mechanism for a browser to check with a domain registrar that DNS records being returned by DNS Cache servers are consistent with the registrar’s signature for those records. In other words, a rogue domain used for DNS exfiltration could still be protected by DNSSEC.

### 1.3.4.*Malware using DNS tunnelling*

A new trend is malware using DNS to send C&C commands (Khandelwal, 2017). DNSMessenger is an example of a Remote Access Trojan (RAT) that uses DNS queries to launch malicious PowerShell commands on compromised computers. Examples have been detected in sophisticated attacks launched from a VBA macro embedded in a Word document, which is used to execute a PowerShell script (Brumaghin and Grady, 2017). DNSMessenger is fileless as it does not write files to the targeted system, but uses DNS TXT messages to fetch PowerShell commands stored remotely as DNS TXT records (Khandelwal, 2017). The method modifies the Windows Management Instrumentation (WMI) database to maintain persistence after reboots.

### 1.4.The Threat Posed by Web Storage and Web Exfiltration

Web-based exfiltration methods can either be covert or overt. Data can be transferred in the background using the web-based protocols HTTP or HTTPS, which use an organisation’s proxy server, or by a rogue employee to a web storage account such as Dropbox, OneDrive, SpiderOak, etc. Microsoft OneDrive, Dropbox and SpiderOak are all examples of commonly used web storage accounts. Dropbox can be used with or without an agent, however, in order to use the agent, further TCP ports must be configured on a firewall, so using Dropbox in this mode would not be possible on a secure network. The OneDrive App is often installed with Microsoft Office and the App works quite happily over a web proxy. SpiderOak provides encrypted web storage and so is an example of a business system that could be exploited by an attacker who would be able to conceal the data stolen.
