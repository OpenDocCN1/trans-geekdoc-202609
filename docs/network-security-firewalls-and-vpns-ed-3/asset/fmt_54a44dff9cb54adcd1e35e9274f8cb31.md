
# Hosting a Web Server in a DMZ

Hosting a web server in a DMZ is a more secure solution. However, if compromised, a DMZ web server gives the hacker a weapons platform just outside of the private network’s front door. Co-location is placing a web server host directly on an ISP network within a facility. Hosting is leasing access to space on an existing web server owned and managed by the hosting entity. These last two options are the most secure; if the web server or site is compromised, the hacker gains no location benefit to breach the private network.

## Network and Resource Availability Threats

To be successful, many exploits and attacks require special access on a private network. Some exploits will function against an Internet-facing web server, but such a server might not directly connect to a private network. If a hacker is unable to find an exploitable vulnerability that gains access or control over the targeted systems, a fallback or final resort option is to launch availability attacks.

An availability attack aims at preventing legitimate access or use of resources to delay or interrupt business. Generally, this is known as a denial of service attack.

### Denial of Service (DoS)

A [denial of service (DoS) attack](#30_glossary.xhtml#gloss125) interrupts the normal patterns of traffic, communication, and response. A DoS attack interferes with timely processing and reply to legitimate requests for resources. A DoS attack can be of two primary forms: flaw exploitation or traffic generation.

![FIGURE 2-12 Denial of service flooding attack against a client.](Images/9781284183658_CH02_FIGF12.png)

**FIGURE 2-12** Denial of service flooding attack against a client.

Flaw exploitation DoS attacks take advantage of a programming bug, flaw, or convention. The DoS exploit results in the system freezing, crashing, rebooting, or failing to respond to external communications. You can mitigate flaw exploitation DoS attacks through the application of a patch and the use of an `IDS` or `IPS` system. Once you apply a patch, the DoS will no longer be effective. [Flaw exploitation attacks](#30_glossary.xhtml#gloss185) are usually specific to a software version.

Traffic generation DoS attacks flood a target with traffic ([**FIGURE 2-12**](#11_chapter02_16.xhtml#fig2-12)). The traffic consumes available bandwidth and processing, preventing legitimate communications. No patches exist to mitigate traffic generation DoS attacks. Instead, traffic filtering is the only effective response. [Upstream filtering](#30_glossary.xhtml#gloss528), however, is more effective than edge device filtering.

Upstream filtering occurs when a parent network, usually the ISP, provides filtering for traffic before it enters the child network to which individual and business customers connect. Edge device filtering will prevent malicious traffic from entering the private network, but it will not prevent a successful DoS. Only upstream filtering will reduce or eliminate the DoS traffic and allow legitimate communications to continue.

### Distributed Denial of Service (DDoS)

[Distributed denial of service (DDoS) attacks](#30_glossary.xhtml#gloss140) advance DoS attacks through massive distributed processing and sourcing. The foundations of a DDoS attack are [agents](#30_glossary.xhtml#gloss9), [bots](#30_glossary.xhtml#gloss52), or [zombies](#30_glossary.xhtml#gloss560), which are malicious code implanted on victim systems across the Internet. These mobile agents may create their own peer-network interaction or connect into a public communication medium, such as an [Internet relay chat (IRC)](#30_glossary.xhtml#gloss257) channel. The resultant network is known as a [botnet](#30_glossary.xhtml#gloss53), [zombie army](#30_glossary.xhtml#gloss561), or [zombie array](#30_glossary.xhtml#gloss562).

The hacker remotely controls the botnet and directs it to perform various malicious activities—including flooding attacks—against selected targets. Generally, the main targets of the botnet are known as primary victims, while the compromised systems hosting the botnet’s agents are known as secondary victims. This form of DoS is distributed because the bots are disseminated across numerous secondary victims, and the resulting attacks originate from a plethora of source vectors.

A hacker distributes the bots, agents, or zombies to many secondary victims located throughout the Internet. The bots then connect to some form of communication server, commonly a chat service like IRC, where each can receive instructions from the hacker. Once the hacker sends attack instructions, the bots launch attacks against the primary target ([**FIGURE 2-13**](#11_chapter02_16.xhtml#fig2-13)).

![FIGURE 2-13 Distributed denial of service flooding attack against a primary target.](Images/9781284183658_CH02_FIGF13.png)

**FIGURE 2-13** Distributed denial of service flooding attack against a primary target.

A botnet can perform a wide range of malicious actions including flooding, spamming, eavesdropping, intercepting, `MitM`, session hijacking, spoofing, packet manipulating, malware distributing, phishing site hosting, password stealing, encryption cracking, and more.

Several botnets, such as Storm and Conficker, have appeared in the last decade; these two worms had an estimated secondary victim base of 75 to 100 million systems.

Defenses against DDoS focus on either avoiding becoming a secondary victim or protecting against primary victim onslaughts. To avoid becoming a secondary victim, measures include current antivirus and anti-malware scanning, user behavior modification, firewall filtering, and `IDS/IPS` solutions. Protection against primary victim onslaughts includes firewall filtering, honeypots, `IDS/IPS` solutions, and DDoS mitigators. A [DDoS mitigator](#30_glossary.xhtml#gloss114) is a purpose-built appliance that inspects traffic entering a network; it blocks attacks while allowing legitimate traffic to flow. Hybrid solutions are available that combine on-premises appliances with a cloud-scrubbing service to filter traffic.

## Hacker Tools

Hacker tools include a wide variety of software: from mundane native OS utilities, to commercial applications, to custom-coded exploits. Generally, any software put to a malicious or unauthorized (according to company security policy) use is a hacking tool. Hacking tools perform hacking activities. All of the exploit concepts mentioned in this chapter are possible through a wide variety of hacking tools and utilities.

No master list of hacker tools exists to search for or block access to protect IT systems. Just about every legitimate program can be put to some illicit task. To defend generally against hacker tools, consider using a whitelist restriction system.

A whitelist restriction system incorporates a list of software executables authorized for use. A user can launch any application on the list, but all executables not on the list can be blocked from running. A whitelist cannot focus only on authorized filenames; this process also uses a hash value to prevent a hacker from easily bypassing the limitation through simple file renaming. In addition to whitelisting, you can reduce the threat of hacking tools by limiting Internet downloads and file exchanges, controlling use of portable storage devices (especially those used on external systems), filtering email attachments, installing `IDS/IPS` solutions, and providing user education.

## Social Engineering

[Social engineering](#30_glossary.xhtml#gloss467) is the art of manipulating and exploiting human nature by getting people to perform tasks or release information that violates security. Social engineering is an exploit that can almost always be performed against a target organization due to the presence of humans. Humans are the primary targets of social engineering.
