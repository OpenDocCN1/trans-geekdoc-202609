
# OS Fingerprinting

OS fingerprinting or OS banner grabbing is a technique used to identify the OS being used on a remote host. There are several ways through which OS fingerprinting can be performed.

## TCP/IP Implementation

The configuration of certain parameters in the protocols such as `TCP` and `IP` are left up to the implementation and unfortunately different OSs have their trademark implementations. An analysis of these configurations in the packets received from a target host can help the intruder in identifying the OS running on that host. In [Table 3.1](#08_Chapter03.xhtml#tab3_1), a list of initial TTL values and Window sizes used by different OSs is provided. The scanning techniques we have discussed in [Section 3.1](#08_Chapter03.xhtml#sch3_1), can be used to capture the response of the target and then the values of the two fields can be compared to identify the type of the OS. Other parameters and flags such as TCP initial sequence number and IP identification numbers can also be used to reveal the OS.

**Table 3.1** Commonly Used TCP/IP Parameters by Different Operating Systems

| OPERATING SYSTEM | IP INITIAL TTL | TCP WINDOW SIZE |
|---|---|---|
| Linux (kernel 2.4 and 2.6) | 64 | 5840 |
| Google's customized Linux | 64 | 5720 |
| FreeBSD | 64 | 65535 |
| Windows XP | 128 | 65535 |
| Windows 7, Vista, and Server 2008 | 128 | 8192 |
| Cisco Router (IOS 12.4) | 255 | 4128 |

Furthermore, we have stated during our discussion on the network scanning that certain implementations of the `TCP` respond in a different way when an unusual protocol operation is observed. For example, the `TCP RST` segment in response to Xmas and null scan is only possible in the case of Berkeley Software Distribution (BSD) implementation. Similarly, the ICMP echo scanning is applicable to the BSD implementation as only these OS respond sent to the ICMP echo requests sent to the broadcast addresses.

## Application Layer Protocols

`HTTP`, `SMTP`, and other application layer protocols in their message banners include the information about the OS and thus reveal the identity. The `server` and `user agent` header fields in the `HTTP` are prime examples of such banner grabbing.

## 3.2.2 Windows Platform

There are several protocols, application programming interfaces (APIs), and tools specifically used on Windows platform to maliciously attack a Windows system such as Network Basic Input and Output system (NetBIOS) and PsTools.

### NetBIOS Enumeration

NetBIOS is an API used on Windows platform to access LAN resources. The `nbtstat` command provided in the Windows reveals important information about the remote machines on the LAN and shared resources.

### PsTools

This resource kit has several command-line tools that help to administer Windows systems. They can be also used by the intruders to collect the information about the remote and local systems.

### Microsoft Authentication

Microsoft LAN Manager (LM) and Microsoft Windows NT LAN Manager are proprietary protocols used by Microsoft products to perform challenge/response authentication. These protocols store passwords in the form of hashes calculated through a sequence of steps that divides the 14-character long password into two halves and process them separately to create an 8-byte hash for each part. The earlier version LM has an interesting flaw that if the password is less than or just about seven characters in length, then the second part of the hash is always `0xAAD3B435B51404EE`. This can easily reveal to the intruder that the actual password length was seven characters or less.

### NTFS Stream Manipulation

The NTFS file system on Windows platform has two data streams associated with each file stored on an NTFS volume. The first stream stores the security descriptor, while the second stream stores the data within the file. Alternate data stream (ADS) is another type of named data stream that can be present within each NTFS file. It is any kind of data that can be attached to the file but is actually not in the file. The master file table of the partition maintains a list of all the data streams associated with a file and their physical location; ADS is attached to the file through the file table.

The purpose of ADS in Windows is to provide a hidden stream that contains metadata for the file such as attributes, word count, author name, and access and modification time of the files. However, ADS can be used to fork data into existing files without changing or altering their functionality, size, or display to file-browsing utilities. Thus, ADSs provide attackers with a method of hiding malicious code or programs on a compromised system and allow them to be executed without being detected.

## 3.2.3 UNIX/Linux Platform

### Enumeration

The `finger` command is used for enumerating the users on the remote machine. It provides information such as user's home directory, login time, idle times, office location, and the last time they received or read mail. Similarly, there are other commands such as `rpcinfo` and `showmount` that can be used to reveal the administrative stuff.

## References

*   [1.](#08_Chapter03.xhtml#rfn1) Fielding, R., Gettys, J., Mogul, J., Frystyk, H., Masinter, L., Leach, P., and T. Berners-Lee, "Hypertext Transfer Protocol – HTTP/1.1", RFC 2616, DOI 10.17487/RFC2616, June 1999, [http://www.rfc-editor.org/](http://www.rfc-editor.org/) info/rfc2616.
*   [2.](#08_Chapter03.xhtml#rfn2) Postel, J., Transmission Control Protocol, STD 7, RFC 793, DOI 10.17487/RFC0793, September 1981, [http://www.rfc-editor.org/info/](http://www.rfc-editor.org/info/) rfc793.
*   [3.](#08_Chapter03.xhtml#rfn3) Postel, J., User Datagram Protocol, STD 6, RFC 768, DOI 10.17487/RFC0768, August 1980, [http://www.rfc-editor.org/info/rfc768](http://www.rfc-editor.org/info/rfc768).
*   [4.](#08_Chapter03.xhtml#rfn4) Postel, J., Internet Control Message Protocol, STD 5, RFC 792, DOI 10.17487/RFC0792, September 1981, [http://www.rfc-editor.org/info/](http://www.rfc-editor.org/info/) rfc792.
*   [5.](#08_Chapter03.xhtml#rfn5) Klensin, J., Ed., Simple Mail Transfer Protocol, RFC 2821, DOI 10.17487/RFC2821, April 2001, [http://www.rfc-editor.org/info/](http://www.rfc-editor.org/info/) rfc2821.
*   [6.](#08_Chapter03.xhtml#rfn6) Bhushan, A., File Transfer Protocol, RFC 114, DOI 10.17487/RFC0114, April 1971, [http://www.rfc-editor.org/info/rfc114](http://www.rfc-editor.org/info/rfc114).
*   [7.](#08_Chapter03.xhtml#rfn7) Droms, R., Dynamic Host Configuration Protocol, RFC 2131, DOI 10.17487/RFC2131, March 1997, [http://www.rfc-editor.org/info/](http://www.rfc-editor.org/info/) rfc2131.
*   [8.](#08_Chapter03.xhtml#rfn8) Plummer, D., Ethernet Address Resolution Protocol: Or Converting Network Protocol Addresses to 48.bit Ethernet Address for Transmission on Ethernet Hardware, STD 37, RFC 826, DOI 10.17487/RFC0826, November 1982, [http://www.rfc-editor.org/info/rfc826](http://www.rfc-editor.org/info/rfc826).

# 4 Malware

**MOHSEN MOHAMED**
