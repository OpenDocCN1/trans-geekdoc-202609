
This collection of firewall management best practices should serve as a starting point for the development of an effective firewall deployment. Other valid and useful guidelines deserve consideration, so do not assume this list of recommendations, or any list from any source, is exhaustive. There are always new lessons to learn and new challenges to face, as well as new wisdom to obtain.

### Security Measures in Addition to a Firewall

A firewall is an essential part of any security infrastructure. Every host needs a firewall. A traditional network needs border firewalls. Firewalls are concentrations of security, and they are easily recognizable embodiments of an organization’s security policy. However, a firewall on its own is an incomplete security solution.

A complete security solution requires many more components (**FIGURE 13-1**) than just a firewall. Proper understanding of the organization’s essential processes, threats, and goals will guide you toward the creation an effective security plan. Without a proper risk assessment, however, recommendations for safeguards and countermeasures are just guesses.

![FIGURE 13-1 Firewalls: Only part of the security puzzle.](Images/9781284183658_CH13_FIGF01.png)

**FIGURE 13-1** Firewalls: Only part of the security puzzle.

Several common elements characterize most properly designed security systems. These include:

*   Multifactor authentication
*   Anti-malware scanning
*   Full hard drive encryption
*   Communications encryption
*   Detailed logging and auditing of events
*   Intrusion detection systems and intrusion prevention systems (IDSs/IPSs)
*   Network segmentation and traffic management
*   Private IP addresses and network address translation (NAT) proxies
*   VPNs for remote access
*   Network access control (NAC)

Although these are often excellent security components, all are not necessarily applicable and required in every environment. Addressing your environment’s specific risks is always more preferable than deploying a security product just because it seems like a good idea.

### Mitigating Firewall Threats and Exploits

Firewalls are one of the most important components of a complete security solution. However, firewalls are not without issues, threats, and concerns. Exploits will cause a firewall to fail. Remember that a firewall is software that sometimes includes dedicated hardware and a host OS. Simply calling it a firewall does not eliminate this concern.

Ultimately, firewalls are software code written by human beings. In either a host firewall or an appliance firewall, the logic and controlling mechanisms are software. Software code is designed and written by people. And whenever people are involved, mistakes or oversights are possible. Any software product is prone to flaws and errors in programming.

Coding errors are not as common in firewall products as in operating systems (OSs) or other forms of software. But do not think that errors do not occur. Most firewall programmers and vendors take extra care to thoroughly test every line of code to exacting quality control and security standards. Standard industry practice requires considerable pilot testing of firewall code before release into the commercial environment.

In spite of these precautions, firewalls have been released to market with software coding errors later discovered and exploited. Hackers are constantly using scanning, testing, and probing tools to discover exploitable weaknesses. When a vulnerability appears, hackers take advantage of the flaw. Some firewall exploits have caused firewalls to freeze or crash, while others have given the hacker the ability to read or adjust filtering rules. In most cases, vendors quickly release updates and patches to correct these problems. When selecting a firewall, check the version and patching history. Firewall products with lots of patches might not be as reliable in the future as a product with fewer patches.

How long does the vendor typically take to release a patch once a flaw or exploit for the product becomes public knowledge? The longer the vendor takes to release a fix, the longer you will be left insecure, waiting for the update. Although termed “zero-day exploits,” once it is found, a hacker can utilize the vulnerability until patched.

When the firewall vendor becomes aware of an exploit, it quickly develops and releases a patch. An effective security- and patch-management system will enable you to quickly test and update the firewalls that protect your production environment. A delay in the release of a patch or its application keeps the window of opportunity wide open for hackers to compromise your environment.

A good policy is to avoid the first generation or first release of a firewall product. Version 1.0 is likely to include more programming errors than later releases. If the first version of a product seems better than any other product available, thoroughly test the product or wait at least six months after its initial release before deployment. This gives other people—good and bad—a reasonable time to find flaws, test exploits, and trigger release updates by the vendor.

After you have installed a firewall, always install every available patch and update from the vendor. Always test updates first—no exceptions—but then get those installed as quickly as your testing process will allow. Install only full and final releases of a firewall patch. Never deploy alpha, beta, pre-release, release candidate, or test-build patches on a production firewall.

Another potential concern of firewall security is the filtering used. Each form of firewall filtering or traffic management is vulnerable in some way. The easiest is basic packet filtering.

Basic packet filtering uses a simple and static rule set. Numerous allow- and deny-explicit exceptions compromise the rule set’s final deny-all rule. Rules can filter by the IP address and port number of the source and/or destination, as well as the protocol in use. A firewall testing and probing technique known as firewalking can potentially discover some or all of the rules on a static packet-filtering firewall.

Overlapping can cause the full or partial overwriting of datagram components, creating new datagrams out of parts of previous datagrams (**FIGURE 13-2**). An overrun can create excessively large datagrams. These and other forms of fragmentation attacks cause denial of service (DoS) or attempt to confuse intrusion detection or firewall filtering.

![FIGURE 13-2 Fragmentation and overlapping.](Images/9781284183658_CH13_FIGF02.png)

**FIGURE 13-2** Fragmentation and overlapping.

Fragmentation is a supported function of IP packets. Packets fragment when they encounter network segments that support a smaller maximum transmission unit (MTU). When packets reassemble, the fragments usually return the data to its original configuration. However, overlapping attacks can abuse the fragmentation offset value in the IP header, causing reassembly overlap. Reassembly overlap can create new payloads or headers. For example, if a payload of “EVIL PAYS BLUE LOAD” fragments into “EVIL PAYS BLUE” and “LOAD,” an overlap reassembly could result in the creation of “EVIL PAYLOAD.”

Protections against fragmentation attacks include using modern IDS detection and firewall-filtering features, as well as performing sender fragmentation. Sender fragmentation queries the network route to determine the smallest maximum transmission unit (MTU) or datagram size. Then the sender pre-fragments the data to ensure that no fragmentation needs to occur en route.
