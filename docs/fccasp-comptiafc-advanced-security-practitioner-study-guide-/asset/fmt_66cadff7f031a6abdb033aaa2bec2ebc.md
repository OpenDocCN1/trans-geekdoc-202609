
Many of these threats have been around for a while, but that doesn't mean they should be ignored. Old exploits are constantly made new again as attackers find ways to recycle exploits.

### Emergent Threats and Issues

If one thing is constant, it's that attackers constantly look for new methods of attack. Since the year 2000, there has been a host of emergent threats. Emergent threats are those that are becoming more prominent and were not seen in the past. These threats include the following:

1.  **Botnets** A collection of zombies that are controlled by a hacker; these bots or zombies may be used to send spam, install Trojans, attempt pump-and-dump stock manipulation, or even launch DDoS attacks. An end user can become infected by visiting a malicious site, clicking on the wrong email attachment, or even following a link in a social networking site. What most botnets have in common is that they are designed to make money. For example, in April 2011 the Coreflood botnet that was being used by computer criminals to loot victims' bank accounts was shut down by a U.S. court order. The botnet had been used to steal thousands of dollars from unsuspecting victims. You can read more about this at `http://arstechnica.com/tech-policy/news/2011/04/fbi-vs-coreflood-botnet-round-one-goes-to-the-feds.ars`. An example of the command and control structure of botnets is shown in [Figure 8.7](#c08.xhtml#c08-fig-0007).

2.  **Scareware** These are several classes of software often with limited or no benefit that are sold to consumers by certain unethical marketing practices. Scareware has been growing for a few years, and it has spread to the Mac. Scareware is designed to frighten you into buying fake or malicious software.

**SMiShing** A form of criminal activity that uses a cell phone's SMS (Short Message Service) and social engineering techniques to send fake SMS messages designed to trick users to click on bogus links.

**Smartphone Attacks** Cell phones are growing as a target. Smart phones are much more powerful than just a few years ago and today, they are just very small, powerful computers. Although some have sounded the alarm for cell phone viruses, worms, and bots for a number of years, these threats have yet to make themselves seen in a major way. Several factors have contributed to the slower than expected advancement of this category of malware. These factors include lack of bandwidth, a fragmented market, and a much shorter life cycle for cell phones than for a computer.

The factors that worked against the spread of these types of malware are changing. More smart phone providers are moving from just providing voice to also providing increasing amounts of data. Platforms such as the iPhone have captured a large portion of the smartphone market. It is important to remember that many threats evolve in an incremental manner. Yesterday's proof of concept may become tomorrow's mainstream attack. There have even been examples of bad applications found in the Apple Store and for some of the Android applications. Some of these were used to track users whereas others were designed to record user activity. For those who decide to go outside the security perimeter of the vendor, such as those who jail-break their phones, other risks are present. Jailbreaking is the process of removing the limitations imposed by smartphone vendors to control the operating system and what programs can be loaded.

**Search Engine Poisoning** Search engine poisoning or black hat search engine optimization is a technique by which attackers ensure that their sites appear high in the return lists of queries so that users are redirected to infected sites.

**Crimeware Kits** Crimeware kits are complete attack tool kits that have everything needed for the wannabe criminal who lacks the technical expertise to launch phishing and malicious attacks. These kits consist of a builder that enables a user to create malware capable of web injections. It's not uncommon for a basic kit to cost about $1,000 or more. You can think of the basic kit in much the same way as if you purchased Windows 8.1 Starter; if you would like more features, you can move up to Windows 8.1 Ultimate. Crimeware kits work in much the same way. For an additional fee, you can buy Explorer or Firefox Form Grabber, encryption plug-ins, or even a remote keylogger. These kits come with user manuals, administration panels, and serial numbers used to validate the kit.

**Clickjacking** This online threat is increasing and works by hiding the true purpose of a link or button. If a hacker can trick you into clicking on an innocent-looking link, the victim actually executes something completely different, often resulting in the remote execution of arbitrary code.

![FIGURE 8.7 Botnet command and control structure](images/c08f007.jpg)

[**FIGURE 8.7**](#c08.xhtml#c08-fig-anc-0007) Botnet command and control structure

### Mitigating Controls and Remediation for Zero-Day Attacks

Before discussing ways to counter zero-day attacks, let's begin with the definition of what a zero-day attack is. A `zero-day attack` is one that the vendor does not yet know about or hasn't been fixed. Zero-day exploits are usually circulated in the hacker underground. Even when software companies become aware of them, a patch to fix the vulnerability may not be immediately available. Consider the attacks against Google known as Aurora. After the attacks, when the source code was made public, it was about a week before Microsoft could create a patch and release it.

Finding ways to counter zero-day attacks is an interesting topic because by definition, you can't defend against a specific attack that you don't know about beforehand. However, you can implement some best practices and techniques that layer in security controls to improve the overall security posture of the organization. Seven lessons for surviving zero-day attacks can be found here: `www.informationweek.com/news/security/attacks/231601692`. Here are some of the other technologies and techniques you should use:

*   Security training and awareness so that users practice safe computing
*   IDS/IPS to scan traffic at the edge of the network and also internally
*   Firewalls to filter ingress and egress traffic with default setting to “deny all”
*   SIEM to scan for anomalous events and investigate their source
*   Incident response procedures and practices to respond to events and determine if they are incidents that should be investigated
*   Implementation of a patch management plan that can be used to keep systems patched
*   Physical security practices that limit access to those who need access and provide multiple layers of physical controls
*   Operational security practices that dictate good hiring, personnel, and termination practices
*   The deployment of encryption for sensitive data while in transit and while at rest
*   Up-to-date antivirus that can scan for malware in different ways, such as signature scanning, heuristic scanning, integrity checking, and activity blocking

### Research Security Implications of New Business Tools

New business tools such as Web 2.0 technologies have changed the way companies operate and market themselves. Although these tools can help your business grow and allow for greater collaboration, you need to research the security implications of new technologies.

#### Social Media/Networking
