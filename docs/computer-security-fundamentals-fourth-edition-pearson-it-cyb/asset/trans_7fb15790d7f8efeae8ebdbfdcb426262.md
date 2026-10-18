...[/content].

- Ensure no line is omitted, no duplication of original text.

We need to translate the whole given content.

Let's parse the content.

It starts with:

[content]

A rootkit may consist of utilities that also do the following:

- Monitor traffic and keystrokes
- Create a backdoor into the system for the hacker's use
- Alter log files
- Attack other machines on the network
- Alter existing system tools to circumvent detection

The presence of a rootkit on a network was first documented in the early 1990s. At that time, the Sun and Linux operating systems were the primary targets for hackers looking to install rootkits. Today, rootkits are available for a number of operating systems and are increasingly difficult to detect on any network.

## Malicious Web-Based Code

Malicious web-based code, also known as web-based mobile code, simply refers to code that is portable to all operating systems or platforms, such as HTTP, Java, and so on. The “malicious” part implies that it is a virus, worm, Trojan horse, or some other form of malware. Simply put, the malicious code does not care what the operating system may be or what browser is in use. It infects them all blindly.

Where does this code come from, and how it is spread? The first generation of the Internet was mostly indexed text files. However, as the Internet has grown into a graphical, multimedia user experience, programmers have created scripting languages and new application technologies to enable a more interactive experience. Programs written with scripting languages run the gamut from useful to poorly crafted to outright dangerous.

Technologies such as Java and ActiveX enable buggy or untrustworthy programs to move to and execute on user workstations. (Other technologies that can enable malicious code are executables, JavaScript, VBScript, and plug‑ins.) The Web increases the mobility of code without differentiating between program quality, integrity, or reliability. Using available tools, it is quite simple to “drag and drop” code into documents that are subsequently placed on web servers and made available to employees throughout the organization or individuals across the Internet. If this code is maliciously programmed or just improperly tested, it can cause serious damage.

Not surprisingly, hackers have used these very useful tools to steal, alter, and erase data files as well as gain unauthorized access to corporate networks. A malicious code attack can penetrate corporate networks and systems from a variety of access points, including websites, HTML content in email messages, or corporate intranets.

Today, with billions of Internet users, new malicious code attacks can spread through corporations almost instantly. The majority of damage caused by malicious code happens in the first hours after a first‑strike attack occurs—before there is time for countermeasures. The costs of network downtime or theft of IP make malicious code a top priority.

## Logic Bombs

A logic bomb is a type of malware that executes its malicious purpose when a specific criterion is met. The most common factor is date/time. For example, a logic bomb might delete files on a certain date/time. For example, in June 2006, Roger Duronio, a system administrator for UBS, was charged with using a logic bomb to damage the company's computer network. His plan was to drive the company stock down due to damage from the logic bomb, so he was charged with securities fraud. Duronio was later convicted and sentenced to 8 years and 1 month in prison and ordered to pay $3.1 million restitution to UBS. This case illustrates this problem is not new.

In 2017 Mittesh Das of Atlanta Georgia was found guilty of transmitting malicious code with the intent of causing damage to a U.S. Army computer. Mr. Das created a logic bomb that would delete files in U.S. Army Reserve payroll systems after his company lost the contract. The incident actually occurred in 2014. He was sentenced to 2 years in prison followed by 3 years of probation.

Nimesh Patel is alleged to have created a logic bomb to attack his former employer's servers in 2016. He is alleged to have logged on to the network after his employment ended, and uploaded malware. The software was designed to delete financial data from the Oracle database.

Another example occurred at the mortgage company Fannie Mae. On October 29, 2008, a logic bomb was discovered in the company’s systems. While this is an older example, it is an important one in the history of logic bombs. This logic bomb had been planted by a former contractor, Rajendra­inh Makwana, who had been terminated. The bomb was set to activate on January 31, 2009, and completely wipe all of the company’s servers. Makwana was indicted in a Maryland court on January 27, 2009, for unauthorized computer access. On December 17, 2010, he was convicted and sentenced to 41 months in prison, followed by 3 years of probation. Makwana planted the logic bomb between the time he was terminated and the time the network administrators cancelled his network access. This illustrates the importance of ensuring that the accounts of former employees are deactivated immediately when their employment is terminated—whether it is an involuntary termination, a retirement, or a voluntary quit.

## Spam

Spam, which most people are familiar with, is unwanted and unsolicited email that is sent out to multiple parties. Often it is used for marketing purposes, but it can be used for much more malicious goals. For example, spam is a common vehicle for spreading viruses and worms. Spam is also used to send emails enticing recipients to visit phishing websites in order to steal their identities. At best, spam is an annoyance, and at worst, it is a vehicle for spyware, viruses, worms, and phishing attacks.

## Advanced Persistent Threats

Advanced persistent threats ([APTs](#)) is a relatively new term for a continuous process of attacking. It can involve hacking, social engineering, malware, or combinations of attacks. The issue is that the attack must be relatively sophisticated, thus the term advanced, and it must be ongoing, thus the term persistent.

The security firm Mandiant tracked several APTs over a period of 7 years, all originating in China—specifically, Shanghai and the Pudong region. These APTs were simply named APT1, APT2, and so on.

The attacks were linked to the UNIT 61398 of China’s military. The Chinese government regards this unit’s activities as classified, but it appears that offensive cyber warfare is one of its tasks. Just one of the APTs from this group compromised 141 companies in 20 different industries. APT1 was able to maintain access to victim networks for an average of 365 days, and in one case for 1764 days. APT1 is responsible for stealing 6.5TB of information from a single organization over a 10-month time frame. We will discuss the Chinese attack in more detail in **Chapter 12**, “Cyber Terrorism and Information Warfare.”

## Detecting and Eliminating Viruses and Spyware

Once you understand the nature of malware, and just how devastating it can be, the next logical topic is to detect and remove malware.

## Antivirus Software

In this chapter and throughout this book, we have discussed the need for running virus-scanning software. This section provides some details on how virus scanners work and information on the major virus-scanning software packages. This information should help you better understand how a virus scanner might protect your system and help you make intelligent decisions regarding the purchase and deployment of an antivirus solution.

A virus scanner can work in one of two ways. The first is to look for a signature (or pattern) that matches a known virus. It is therefore important to keep your virus software updated so that you have the most recent list of signatures with which to work.

The other way in which a virus scanner might check a given PC is to look at the behavior of an executable. If a program behaves in a way consistent with virus activity, the virus scanner may flag it as a virus. Such activity could include the following:

- Attempting to copy itself
- Attempting to access the address book of the system’s email program
- Attempting to change Registry settings in Windows

