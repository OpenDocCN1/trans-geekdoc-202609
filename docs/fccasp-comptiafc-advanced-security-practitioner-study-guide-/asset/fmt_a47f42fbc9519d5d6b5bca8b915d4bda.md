
# Appendix B

## Answers to Review Questions

### Chapter 1: Cryptographic Tools and Techniques

1.  **B.** Symmetric encryption offers privacy as a feature but suffers from problems with key distribution and key management.

2.  **C.** The MD algorithms are a series of cryptographic algorithms that were developed by Ron Rivest. `MD5` processes a variable-size input and produces a fixed 128-bit output.

3.  **B.** A digital signature is a hash value that has been encrypted with the private key of the sender. It is used for authentication and integrity.

4.  **C.** The easiest way to check whether the lost key has been flagged by the system is to use the `Online Certificate Status Protocol` to check the certificate and verify if it is valid.

5.  **D.** A `CRL` lists revoked certificates.

6.  **A.** Wildcard certificates allow the purchaser to secure an unlimited number of subdomain certificates on a domain name.

7.  **D.** Symmetric encryption does not provide for easy key exchange.

8.  **C.** Most authentication systems make use of a one-way encryption process known as hashing. One of the strengths of a hash is that it cannot be easily reversed.

9.  **D.** Caesar's cipher is known as `ROT3` cipher, because you move forward by three characters to encrypt and back by three characters to decrypt.

10. **B.** Asymmetric encryption offers easy key exchange and key management. However, it requires a much larger key to have the same strength as symmetric encryption.

11. **D.** Both `SSL` and `TLS` are examples of hybrid encryption. These services use both symmetric and asymmetric algorithms.

12. **B.** While `DES`, `Blowfish`, and `Twofish` are all examples of symmetric encryption, `RSA` is not.

13. **D.** `IDEA` is a symmetric encryption standard that is similar to `DES` and was invented in Switzerland.

14. **B.** `BitLocker` is an example of an application that can provide full disk encryption.

15. **A.** Comparing the hash of a program to that on the developer's website is an easy way to verify the integrity of an application.

16. **D.** When two different messages result in the same output, it's called a collision. Collisions can be a problem with hashing programs that output shorter hashes, such as 128 bits. That is why many programs that rely on a hash use 256-bit or 512-bit outputs. Larger hashes are less likely to suffer from collision.

17. **D.** The web of trust is easy to set up and has little or no cost. Users can distribute keys directly by attaching them to the bottom of their email messages.

18. **B.** Hybrid encryption combines symmetric and asymmetric encryption. The process works by using an asymmetric process to exchange a symmetric key.

19. **B.** There are many ways that cryptographic solutions can be applied. `DES ECB` is an example of block encryption. `DES` works with 64-bit blocks of data.

20. **A.** `Hardware Security Modules (HSMs)` are physical devices that are used to securely store cryptographic keys and are widely used in high-security systems and hard devices such as ATMs.

### Chapter 2: Comprehensive Security Solutions

1.  **B.** `TACACS+` has added functionality and has extended attribute control and accounting processes. `TACACS+` also separates the authentication and authorization process into three processes.

2.  **A.** `XTACACS` is proprietary to Cisco.

3.  **D.** A single-tier packet filter design has one packet-filtering router installed between the trusted and untrusted network.

4.  **C.** Broadcast MAC addresses appear as `FF FF FF FF FF FF`.

5.  **B.** An address of `224.3.9.5` is class D, or multicast, traffic.

6.  **B.** `DNS` uses `UDP` port 53 for DNS queries and `TCP` port 53 for zone transfers.

7.  **B.** Port 123 is used by `NTP`.

8.  **B.** `Kerberos` offers Windows users faster connections, mutual authentication, delegated authentication, simplified trust management, and interoperability.

9.  **B.** `LDAPS` provides for security by using `SSL`.

10. **C.** `DNSSEC` does not protect against domain kiting.

11. **D.** The `SOA` record holds zone replication `TTL` information.

12. **D.** Version 3 is more secure than previous versions of `SNMP` and offers encryption.

13. **D.** `TFTP` uses port 69 by default.

14. **D.** `UDP` is composed of four fields: source, destination, length, and checksum.

15. **B.** The `CNAME` record is an alias.

16. **A.** `TSIG` is used as a means of authenticating updates to a Dynamic `DNS` database.

17. **A.** Cisco has several ways to incorporate `VLAN` traffic into trunking, such as the IEEE's implementation of `802.1Q` and Cisco's `ISL`.

18. **D.** `IPv6` has many improvements over `IPv4`; one of these is that the address space moves from 32 bits to 128 bits.

19. **A.** `WS_Security` is an extension to `SOAP` and is designed to provide added security.

20. **D.** `SPIT` is “Spam over Internet Telephony” and is not considered a component of `VoIP`.

### Chapter 3: Securing Virtualized, Distributed, and Shared Computing

1.  **C.** A trunking port is one that is designed to share traffic from multiple `VLANs`.

2.  **D.** Although cloud computing offers many benefits, privacy is not one of them.

## Suggestions for Further Exploration of Security Topics

This last section provides some direction for further exploration. The concept behind these labs is twofold. First, these labs were designed to introduce various concepts touched on throughout the Study Guide. At the same time, they were designed to provide the home-based lab environment that can assist you with your goal of obtaining CASP status while increasing your technical abilities in areas where you may feel weaker. This is especially important since security in general is a very broad topic, even more so when a professional is required to have a firm grasp of the practical application side as well as the theory.

You should now have a strong foundation in multiple virtual environments that you can use for further study. You have the `NETinVM` environment with both `OpenSUSE` and several `Debian 5` machines so you can learn more about Linux networking. You have the bootable `Kali DVD` with hundreds of great hacking tools to explore. You have `VMware`, where you can create and work with an unlimited number of virtual machines. Security is a moving target—keep learning and be safe.

### Recommended links for further exploration:

*   SANS Using `OSSEC HIDS` with `NETinVM`: `www.sans.org/reading_room/whitepapers/detection/ossec-netinvm_33473`
*   FreeNAS Network Attached Storage How-to guide: `www.howtoforge.com/network_attached_storage_with_freenas`
*   `AsteriskNOW` Communications Server: `www.asterisk.org`
*   Project Artillery – Advanced HoneyPot with `IPS`: `www.trustedsec.com/downloads/artillery/`
*   `Kali Linux` – Penetration Testing Toolkit: `www.kali.org/`
*   Introduction to `Wireshark` video by IronGeek: `www.irongeek.com/i.php?page=videos/wireshark-sniffer-1`
*   `VMware` Virtual Appliances (pre-packaged applications): `http://solutionexchange.vmware.com/store/category_groups/19`
*   `Squid` proxy server in a `VM`: `www.thedailyadmin.com/2009/04/how-to-install-virtual-machine-with.html`
*   `Nexpose Community Edition` Vulnerability Management: `www.rapid7.com/products/nexpose-community-edition.jsp`
*   `OWASP WebGoat` (Vulnerable Test Web Server): `www.owasp.org/index.php/Category:OWASP_WebGoat_Project`
*   `McAfee` Tools including `Hacme Bank v2.0`: `www.mcafee.com/us/downloads/free-tools/index.aspx`
*   `Hacme Bank` Documentation: `http://www.mcafee.com/us/resources/white-papers/foundstone/wp-hacme-bank-v2-user-guide.pdf`
*   `Suricata IDS/IPS`, similar to `Snort`: `www.openinfosecfoundation.org/`
*   Social engineering resources: `www.social-engineer.org/`

## Lab Exercises

### Exercise 28

Enter `http.request.uri matches “ethereal ”` in the filter toolbar. Observe the results, focusing on why you have filtered out all traffic with the exception of one single `GET` request.

### Exercise 29

Take some time to play with various sample captures and `Wireshark` display filters, focusing on protocols that you are unfamiliar with and of course those specifically referenced on the exam objectives.
