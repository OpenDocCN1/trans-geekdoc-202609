
![](img/b2a7c1cdb4938c3b37d6925de0425ae9_397_0.png)

FIGURE 11-13 Defaced New York Times webpage.

Source: zdnet.com

> Backdoor programs are typically more dangerous than computer viruses. This is because intruders can use them to take control of a computer and potentially gain network access. These programs are also commonly referred to as Trojan horses because they pretend to do something other than what they actually do. Backdoor programs typically arrive as attachments to emails with innocent-looking filenames.

included a payload that installed a backdoor Trojan. This Trojan allowed remote access to an infected IIS server, which attackers could use to deface the front page of the web server. You can minimize the risk of this type of attack by ensuring that you install current software versions and security patches.

## A Brief History of Malicious Code Threats

In the early days of computing, malware spread from computer to computer via diskettes that were handed off from person to person. This manual transmission method was called sneaker-net. With sneaker-net, a virus could take months to spread across the globe. In contrast, today’s viral infections spread via networks and can cross the globe in a matter of seconds. As the virus-writing community evolved, more and more sophisticated viruses began to emerge. Some could spread via email, mobile code, or macros, and others could spread in multiple ways.

### 1970s and Early 1980s: Academic Research and UNIX

The idea of self-replicating computer programs has been around for decades. This idea has appeared in literature, scientific papers, and even experiments since the early 1970s.

Researchers made early attempts to perform routine maintenance tasks on large networks using self-distributing code (worms), but the technology did not become widespread or well known.

A key event in hostile code development was the research performed by Dr. Fred Cohen in 1983. Cohen's paper, “Computer Viruses—Theory and Experiments,” published in 1984, defined the computer virus and described experiments he and others performed to prove the viability of viral code. Cohen published this work before anyone observed the first computer viruses.

The Internet during this period was a network that primarily connected university computers to one another. This network was vulnerable to programs that could propagate using existing communications protocols. A university student named Robert Morris—who unleashed the first major malware incident, the Morris Worm, in November 1988—demonstrated this idea. This UNIX-based worm overwhelmed almost all computers on the Internet, causing a great deal of media interest and many headlines.

### 1980s: Early PC Viruses

The first personal computers (PCs) hit the market in the early 1980s. Their popularity grew fast. By the late 1980s, the PC was an indispensable and affordable business technology for many companies. This rapid growth also brought computer technology closer to a larger number of individuals.

The PC operating system was disk-based (DOS), and most software and data files migrated between PCs via floppy diskettes. Two primary types of malicious virus code emerged to exploit this fact: boot sector viruses, which attacked the operating system components located on disks and in memory, and file infector viruses, which attacked the executable files themselves.

Brain (a boot sector virus), Lehigh, and Jerusalem (a file infector) are examples of the earliest viruses. They propagated primarily via floppy disks and downloads from popular computer bulletin board (BBS) archives. Another early virus, Elk Cloner, which targeted the Apple II computer, also spread by floppy disks.

### 1990s: Early LAN Viruses

Local area networks (LANs) began to appear in business environments by the early 1990s. This development gave the traditional file viruses a fertile environment to propagate. Very few people understood the virus problem at this time, and finding a virus was a rare event. Interested users collected the samples they found and freely distributed those, giving rise to notorious virus exchange bulletin boards. Some viruses did cause damage, and business users started to become aware of the problem. The boot sector virus Form5 became the most widespread virus during this period. Another well-known virus of this era was Dark Avenger, also known as Eddie6. It was a very destructive virus.

By the end of the decade, local area networks had become a key infrastructure in most companies. At the same time, the use of the Internet for communications—particularly email and data file transfer—became widespread. Traditional boot sector and file infector viruses began to diminish in frequency as storage technology advanced with the introduction of CD-ROMs.

### Mid-1990s: Smart Applications and the Internet

The popularity of email, combined with the ease of attaching files, gave rise to the extremely widespread distribution of malicious code using the same techniques demonstrated years earlier by Morris: email worms. These programs locate email address files within a user’s system and then generate multiple copies of themselves, often disguised as innocent-looking file attachments. The well-known email worms named Melissa and Loveletter are examples. Although many of these earlier programs relied on users to activate the code by opening attachments, newer forms of worms have exploited various security weaknesses in the increasing numbers of always-on computers and servers. For example, Code Red exploited vulnerabilities in Microsoft web servers (IIS) and had exceptional replication speed.

The Internet provides an environment from which individuals and groups can extend their activities beyond functional and geographic boundaries. During the mid-1990s, hacking (or cracking) became a growing business security concern. Using automated tools and more structured approaches, these individuals and groups have continued to evolve. The inherent resiliency of Internet communications protocols became a way to disrupt normal operations and gave rise to DoS attacks against popular websites.

New forms of malicious code evolved in the 1990s, including Trojan programs like Back Orifice and AIDS. More resilient and stealthy variants of virus code also evolved, including polymorphic versions like Tequila. In addition, new programming languages designed for portability and functionality presented new opportunities to develop additional forms of malicious code. StrangeBrew was the first virus to infect Java files. Though harmless, the virus modified CLASS files to contain a copy of itself.

With the introduction of advanced programming features into popular application software, the rise of other forms of malicious code appeared to infect document files. The first macro virus, WM/Concept7, was discovered in August 1995. It spread through the transmission of a simple document file.

### 2000 to Present

As personal and corporate Internet connectivity has continued to increase in this new century, authors of popular browser technologies have added numerous companion tools or plugins. These tools use specialized scripting codes that can automate common functions. They comprise a generation of active content code that exposes additional opportunities to attackers.

The number of computers and devices now connected to the Internet, especially popular server platforms running Windows and other widely distributed software, has created new vulnerabilities. The replication speed of Internet worms coupled with today’s high-speed computers, as well as increasing interactive probing for vulnerabilities by hostile groups, mandate continuous improvement, monitoring, and testing of IT security by organizations and user communities.

The W32/Nimda worm, taking advantage of backdoors left behind by the Code Red II worm, is the first to propagate itself via several methods, including email, network shares, and an infected website. The worm spreads from client to web server by scanning for backdoors. The Klezworm infects executables by creating a hidden copy of the original host file and then overwriting the original file with itself.
