
In this chapter, we described the different components of an ATM and the role that each plays while dispensing money. We explored the different types of malware that affect these teller machines, dissecting their inner workings. Finally we presented countermeasures to try to mitigate the risk of this threat, which has led to the theft of millions of dollars from banks worldwide.

## For Further Reading

- ATM Security Guidelines https://www.pcisecuritystandards.org/pdfs/PCI_ATM_Security_Guidelines_Ir
- ATM Software Security Best Practices Guide https://www.atmia.com/files/Best%20Practices/ATMIA%20Best%20Practices%20
- XFS middleware https://en.wikipedia.org/wiki/CEN/XFS

## References

- 1. “CWA 13449 - XFS Interface Specification Release 2.0,” European Committee for Standardization, https://www.cen.eu/work/areas/ICT/eBusiness/Pages/CWA13449.aspx.
- 2. OpenXFS Repository, freexfs, https://code.google.com/archive/p/freexfs/.
- 3. Daniel Regalado, “RIPPER ATM Malware and the 12 Million Baht Jackpot,” FireEye, August 26, 2016, https://www.fireeye.com/blog/threat-research/2016/08/ripper_atm_malwarea.html.
- 4. Infostealer.PanDeBono, Symantec, June 26, 2014, https://www.symantec.com/security_response/writeup.jsp?docid=2014-042323-5548-99&tabid=2; Infostealer.Neabolsa, Symantec, April 23, 2014, https://www.symantec.com/security_response/writeup.jsp?docid=2014-042214-1330-99&tabid=2.
- 5. Brian Krebs, “Tracking a Bluetooth Skimmer Gang in Mexico,” Krebs on Security, September 15, 2015, https://krebsonsecurity.com/2015/09/tracking-a-bluetooth-skimmer-gang-in-mexico/.
- 6. Daniel Regalado, “SUCEFUL: Next Generation ATM Malware,” FireEye, September 11, 2015, https://www.fireeye.com/blog/threat-research/2015/09/suceful_next_genera.html.

## CHAPTER 21

## Deception: Next-Generation Honeypots

This chapter covers the topic of deception for defensive purposes. The chapter first covers deception in conflict from a historical perspective and then moves into the use of deception for protection of information systems using honeypots. The chapter provides many hands-on examples and explores the latest in deception and honeypot technologies.

In this chapter, we cover the following topics:

- Brief history of deception
- Honeypots as a form of deception
- Open source honeypots
- Commercial options

### Brief History of Deception

Deception is as old as conflict. In fact, earlier than 800 BCE, Sun Tzu, in his book The Art of War, said, “All warfare is based on deception.”¹ A notable example of using deception in war includes Operation Bodyguard during WWII, when Allied forces used deception to feint attacks and make the Germans think the attacks were coming from another direction.² Several fake airfields and a small army of Hollywood set builders created inflatable tanks and planes and buildings. All of this effort was successful in deceiving the Germans and caused them to hold a portion of their forces in reserve on D-Day.

As far as using deception to protect information systems, Fred Cohen is considered by many to be the grandfather of deception and derivative concepts such as honeypots. Cohen is also known as the person who first published the term computer virus, in 1984,³ by citing Len Adleman, who coined the term. Later, Cohen wrote the seminal work, “A Note on the Role of Deception in Information Protection,” in 1998.⁴ Although Cohen gave credit to others before him, such as Bill Cheswick and researchers at AT&T, it was Cohen and his associates who created the Deception Toolkit, which served as one of the first real honeypots.⁵

If Fred Cohen is the grandfather of modern deception technologies and honeypots, then Lance Spitzner should be considered the father of those technologies. Spitzner, in 1999, with little more than a computer connected to the Internet from his spare bedroom,⁶ inspired a generation of enthusiasts and founded the honeynet.org group,⁷ which continues to contribute to the field of deception technologies to this day. The honeynet.org group defined and built many levels and types of honeypots, many of which were the precursors of what we have today. We stand on the shoulders of these giants as we present some of the latest technologies in this chapter.

### Honeypots as a Form of Deception

A honeypot may be simply defined as a system that has no legitimate purpose other than to be attacked and thereby give alerts of such activity. As has already been discussed, honeypots have been used for deception for many years. One of the problems with early honeypot technologies was the lack of the ability to scale. It often took an experienced security expert to deploy and monitor the technology, which was a full-time job in some environments, even just to monitor a few honeypots. In today’s corporate environments, the older honeypot technology is simply too labor intensive to deploy effectively. However, what was old is new again! With the advent of greater virtual technologies, container technologies such as Docker, and analytic tools such as the Elasticsearch, Logstash, Kibana (ELK) stack, what was once a full-time challenge has turned into a valuable asset of any organization’s cyberdefense, which may be managed part time. As we will demonstrate in this chapter, modern honeypots are easy to deploy and manage, at scale. Even industry analysts have noted that modern deception technologies should be deployed in order to supplement the other enterprise security technologies.⁸ Honeypot technology will not replace other layers of technology, but once an attacker is inside a network, it may be your best shot at catching them.

The main reason to deploy honeypots as a form of deception is to delay, disrupt, and distract the attacker in order to detect and stop them. The key attribute of honeypot technology is its low false-positive nature. By the very definition we used, honeypots should not be touched by anyone but an attacker. Therefore, when a connection is made to a honeypot, there is either a misconfigured server that needs attention, a curious user who needs attention, or an attacker who needs attention. There are no other options; therefore, honeypot technology is about as false-positive proof as you can get. In today’s high-false-positive environment, the ability to deploy a low or no false-positive technology should get your attention.

We'll take a closer look at the following types of honeypot technologies:

- High-interaction honeypots
- Low-interaction honeypots
- Medium-interaction honeypots
- Honeyclients
- Honeytokens

### High-Interaction Honeypots

High-interaction honeypots are most often real systems that are instrumented to monitor and catch an attacker in a near real-time manner. The problem, of course, with high-interaction honeypots is that real systems may be rooted and then used by the attacker to further their attack on the hosting network or other networks. Therefore, high-interaction honeypots are risky and often avoided.

### Low-Interaction Honeypots

Low-interaction honeypots are at the other end of the spectrum; they are simulated services that run in some sort of emulated environment, whereby the service is simulating realistic responses. However, there is often a limit to that simulation. For example, the commands of the Telnet service may be emulated using Python or another scripting language, but not all of the commands work. If an attacker attempts to download a file with wget, for example, perhaps the command appears to work but the file is not provided to the attacker; instead, it is provided to the defender for further analysis. There are other practical limits as well in that it might not be feasible to emulate all the commands of Telnet. Therefore, if an attacker tries one of those commands and it fails, the deception could be over. We will take a look at some popular low-interaction honeypots in the coming sections and labs.

### Medium-Interaction Honeypots

Medium-interaction honeypots were purposely listed after the other two, as they are a newer concept of deeply emulating services. This includes fully reproducing complex operating system processes, such as the SMB network protocol, to a degree that an attacker can run real exploits against the seemingly vulnerable service and in some cases even return a shell. This is a marked improvement over low-interaction honeypots, which would normally fail on those types of attacks. Some medium-interaction honeypots actually proxy the commands to the real operating system to achieve this level of deception.⁹¹⁰ Another form of medium-interaction honeypot would be a canary service, running on a real system, whose purpose is to alert the defender to attacker behavior.

### Honeyclients

Honeyclients are the other side of the honeypot coin. Whereas honeypots are generally services, soliciting a connection and request from an attacker, honeyclients are client applications, seeking to make connections to potentially compromised systems and extract binaries and potential malware for the purpose of analysis and defensive use of that knowledge elsewhere in the enterprise. There are web-based honeyclients and other forms of honeyclients available as well.¹¹

### Honeytokens

Honeytokens are any form of bait that falls outside the traditional server/client model. A common form of honeytokens is a file that contains fake data that is attractive to the attacker. When used by the attacker, this file alerts the defender to their presence. For example, imagine a file called passwords.txt that sits in the root directory of a user on a honeypot system. The file contains fake accounts and fake passwords that do not exist. However, the attacker does not know that when they try to use those accounts, and an alert is fired off in the enterprise’s Security Information Event Management (SIEM) system, notifying the defender to the attack. A great open source resource for generating and tracking honeytokens is canarytokens.org.¹² Another great open source project providing
