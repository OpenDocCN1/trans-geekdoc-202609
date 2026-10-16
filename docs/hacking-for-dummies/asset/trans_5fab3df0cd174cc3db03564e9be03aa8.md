
![remember](images/remember.png)Whatever you do, whatever tool you choose, and whatever procedures work best in your environment, keep your systems patched! This rule goes for operating systems; web servers; databases; mobile applications; and even firmware on your network firewalls, routers, and switches. Especially important are third-party software patches from vendors such as Oracle (Java) and Adobe (Reader, Flash, and so on). These patches are overlooked more than most, yet they create considerable risks that go unaddressed.

Patching is avoidable but inevitable. The only way to eliminate the need for patches is to develop secure software in the first place, but that’s not going to happen any time soon, if ever. Software is too complex to be perfect. A large portion of security incidents can be prevented by some good patching practices, so you simply have no reason not to have a solid patch-management process in place.

### Patch management

If you can’t keep up with the deluge of security patches for all your systems, don’t despair; you can still get a handle on the problem. Here are my basic tenets for applying patches to keep your systems secure:

*   Make sure that all the people and departments involved in applying patches on your organization’s systems are on the same page and follow the same procedures.

*   Have formal documented procedures in place for these critical processes: 

    *   Obtaining patch alerts from your vendors, including third-party patches

    *   Assessing which patches affect your systems

    *   Determining when to apply patches

*   Make a policy and have procedures in place for testing patches *before* you apply them to your production servers. Testing patches after you apply them isn’t as big a deal on workstations, but servers are a different story. Many patches have undocumented features and subsequent unintended side effects, which I’ve experienced. An untested patch is an invitation to system termination.

### Patch automation

The following sections describe the various patch deployment tools you can use to lessen the burden of keeping up with patches.

#### Commercial tools

I recommend a robust patch-automation application, especially if these factors are involved:

*   A large network.

*   A network with multiple operating systems (Windows, Linux, Mac OS, and so on).

*   A lot of third-party software applications, such as Adobe and Java.

*   More than a few dozen computers.

![tip](images/tip.png)Check out these patch-automation solutions:

*   Ecora Patch Manager ([`www.ecora.com/ecora/products/patchmanager.asp`](http://www.ecora.com/ecora/products/patchmanager.asp))

*   GFI LanGuard ([`www.gfi.com/products-and-solutions/network-security-solutions/gfi-languard`](http://www.gfi.com/products-and-solutions/network-security-solutions/gfi-languard))

*   PDQ Deploy ([`https://www.pdq.com/pdq-deploy`](https://www.pdq.com/pdq-deploy))

#### Free tools

Use one of these free tools to help with automated patching:

*   Windows Server Update Services ([`https://technet.microsoft.com/en-us/library/cc539281.aspx`](https://technet.microsoft.com/en-us/library/cc539281.aspx) or System Center Configuration Manager ([`https://www.microsoft.com/en-us/cloud-platform/system-center-configuration-manager`](https://www.microsoft.com/en-us/cloud-platform/system-center-configuration-manager))).

*   Windows Update, which is built into Microsoft Windows operating systems.

*   Microsoft Baseline Security Analyzer ([`https://www.microsoft.com/en-us/download/details.aspx?id=7558`](https://www.microsoft.com/en-us/download/details.aspx?id=7558)).

*   The built-in patching tools for Linux-based systems (such as Yellowdog Updater, Modified \[yum\], and YaST Online Update).

## Hardening Your Systems

In addition to patching your systems, you have to make sure that your systems are *hardened* (locked down) against the security vulnerabilities that patches can’t fix. I’ve found that many people stop with patching, thinking that their systems are secure, but that’s just not the case. Throughout the years, I’ve seen network administrators ignore recommended hardening practices from such organizations as the National Institute of Standards and Technology Computer Security Resource Center ([`http://csrc.nist.gov/publications/PubsSPs.html`](http://csrc.nist.gov/publications/PubsSPs.html)) and the Center for Internet Security ([`www.cisecurity.org`](http://www.cisecurity.org)), leaving many security holes wide open. I believe, however, that hardening systems against malicious attack isn’t foolproof either. Because every system and every organization’s needs are different, there’s no one-size-fits-all solution, so you have to strike a balance without relying on any option too much.

![remember](images/remember.png)After you apply patches, it’s a good idea to rescan your systems for vulnerabilities to confirm that the patches took.

This book presents hardening countermeasures that you can implement for your network, computers, and even physical systems and people. I find that these countermeasures work best.

Implementing at least basic security practices is critical. Whether you’re installing a firewall on the network or requiring users to have strong passwords via a Windows Active Directory domain GPO, you *must* address the basics if you want any modicum of security. Beyond patching, if you follow the countermeasures I document, add the other well-known security practices for network systems (routers, servers, workstations, and so on) that are freely available on the Internet, and perform ongoing security tests, you can rest assured that you’re doing your best to keep your organization’s information secure.

## Assessing Your Security Infrastructure

Reviewing your overall security infrastructure in the following ways can add oomph to your systems:

*   **Look at how your overall network is designed.** Consider organizational issues, such as whether policies are in place, maintained, or even taken seriously. Physical issues count as well. Determine whether members of management have buy-in on information security and compliance, or whether they simply shrug the measure off as an unnecessary expense or barrier to conducting business.

*   **Map your network by using the information you gather from the security tests in this book.** Updating existing documentation is a major necessity. Outline IP addresses, running services, and whatever else you discover. Draw your network diagram. Network design and security issues are a whole lot easier to assess when you can work with them visually. Although I prefer to use a technical drawing program such as Microsoft Visio or Cheops-ng ([`http://cheops-ng.sourceforge.net`](http://cheops-ng.sourceforge.net)) to create network diagrams, such a tool isn’t necessary. You can draw your map on a whiteboard, as many people do, which is just fine.

    ![remember](images/remember.png)Be sure to update your diagrams when your network changes or once every year or so.

*   **Think about your approach to correcting vulnerabilities and increasing your organization’s overall security.** Are you focusing all your efforts on the perimeter and not on a layered security approach? Think about how most convenience stores and banks are protected. Security cameras focus on the cash registers, teller computers, and surrounding areas — not just on the parking lot or entrances. Look at security from a defense in-depth perspective. Make sure that several layers of security are in place in case one measure fails so that the attacker must go through other barriers to carry out a successful attack.
