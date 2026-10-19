
18. Hong, K. S., Chi, Y. P., Chao, L. R., & Tang, J. H. (2003). An integrated system theory of information security management. Information Management & Computer Security, 11(5), 243-248.

19. Akter, S., & Wamba, S. F. (2016). Big data analytics in E-commerce: a systematic review and agenda for future research. Electronic Markets, 26(2), 173-194.

20. Flanagin, A. J., Metzger, M. J., Pure, R., Markov, A., & Hartsell, E. (2014). Mitigating risk in ecommerce transactions: perceptions of information credibility and the role of user-generated ratings in product quality and purchase intention. Electronic Commerce Research, 14(1), 1-23.

21. Jang-Jaccard, J., & Nepal, S. (2014). A survey of emerging threats in cybersecurity. Journal of Computer and System Sciences, 80(5), 973-993.

## CHAPTER

## Cyberwar is Coming

T. MANIKANDAN¹, B. BALAMURUGAN², C. SENTHILKUMAR¹, R. RAJESH ALIAS HARINARAYAN³, R. RAJA SUBRAMANIAN³

¹ APCSE, CSE Department, Thiagarajar College of Engineering, Madurai, Tamil Nadu, India

² PCSE, Galgotias University, Uttar Pradesh, India

³ Research Scholar, CSE Department, Thiagarajar College of Engineering, Madurai, Tamil Nadu, India

Email: tmcse@tce.edu

## Abstract

“War” is the most dangerous game played by humans when their resources are under threat, which has then continuously evolved throughout history due to greed. After the huge losses incurred in the world wars, humanity was restored with diplomacy. War is initiated when emotions like fear and greed encroach upon the minds of people in a society. Basically, fear is triggered due to the lack of resources necessary for living a peaceful life, and questions begin to arise in the minds of people as to what would happen if these resources were to be threatened by those of a faster-growing society with more money and arms which might be used to enslave their own society. Greed happens after a nation reaches a stable state and wants to become. Armed warfare in today’s world has been reduced due to diplomatic efforts, but the fear of reduced resources and greed for money are still visible, and the resources are now becoming digital all over the world with the development of technologies like 5G, the internet of things, smartphones, smarter cities, etc., but so are cyberattacks with ransomware such as WannaCry, NotPetya, BadRabbit, etc. With everything connected to the Internet, it has become a battlefield connected to the civilians of all nations, placing them on the battlefield unknowingly. This connectivity is a bigger threat as it can cause massive devastation in rising digital economies and in everyone and everything, even our brains, which, along with the internet’s ever-encroaching war on people’s emotions, is evidence that a war is coming-a cyber war!

Keywords: Cyberwar, ransomware

In 1988, an experiment conducted by Robert Tappan Morris from Cornell University to determine the size of the Internet led to the creation of the first worm distributed over the Internet. The worm was released from MIT as an experiment. Once downloaded into a system, the worm infected the system by slowing it down. The actual intention of determining internet gauge changed to a virus affecting system because of its nature, the Morris worm [3] spread over the systems. The worm is more likely to be run in the same system many times, slowing it down every time and finally making it unusable. Hence, self-replicating worms are more harmful even today. The unintended results of the graduate student’s experiment was responsible for about $10 million of damage, as stated by the U.S. Government Accountability Office.

The worm was tracked down by Clifford Stoll, whose survey noted that the Morris worm infected about two thousand computers in just fifteen hours. He also stated that the disinfection took about two days. Colleagues of Morris stated that the survey was cooked up. Robert Morris was sentenced to three years probation and fined $10,500 plus the cost of his supervision. The Morris worm was actually the impetus for security personnel to concentrate on Internet security

With the slow relief from the accidental worm of Morris in the Internet, there entered an intentional injection of a worm named Michelangelo [4] in 1991. The attacker was Roger Riordan, an anti-virus expert from Australia. Although the impact of the Michelangelo virus was expected to be great, in reality only a few thousand computers were found to be infected by it. Yet another boot sector virus, it actually did little harm to the systems.

Michelangelo has been considered one of the threatening viruses of the 1990s mainly because of its media hype. The Michelangelo virus works by infecting the first 17 sectors of every track in the infected hard disk on March 6th of each year. As seen so far, boot sector viruses seem to be more threatening. A boot sector virus affects the master boot sector (MBR), which runs every time the computer starts. The MBR controls the boot sequence and also determines the partition in which the computer boots into. Once the virus can successfully infect the MBR, then the computer boot will fail and the contents inside the memory will be lost. Boot sector viruses are hard to remove; hence, the better solution is to prevent them by appropriate verification of external drives for viruses before being injected into the system. Good anti-virus software does the job.

After a decade of Michelangelo’s hype, in January 2003, a huge computer worm threatening the internet world by causing a denial-of-service attack was discovered. The attack requires prerequisite knowledge of the loophole in ancient Microsoft SQL. IP address spoofing over a particular UDP port can cause buffer overflow and destruct normal service of the SQL server [5]. David Litchfield from Microsoft conducted a proof of concept and fixed the issue of this SQL Slammer attack. The issue was submitted to the Microsoft Security Response Center and a patch was developed to counter it. In the next Black Hat, Microsoft released the patch and requested every SQL user to add the patch for security. The POC was studied by researcher Michael Bacarella and released publicly during Black Hat. The attacker implemented it and released it over the Internet. About 75,000 servers that were not patched were affected in just 10 minutes. It was thought that the victims did not report the virus attack because it resulted from their mistake of not adding the patch.

After the era of using viruses to threaten and demolish computers passed, the era of destroying targeted computer sources using viruses evolved. The product was named Stuxnet [6], which has the capability of attacking the programmable logic controller (PLC) of industrial control systems. The PLC is responsible for making logical decisions by monitoring input and producing appropriate output in an automated machine. Stuxnet was born in 2009 at Kaspersky Lab. Stuxnet attacks systems running Windows, which actually

is not a kind of PLC. As PLC is a proprietary machine-language-based device, the virus initially captures the system running the PLC. Then it infects Siemens SIMATIC WinCC¹, a supervisory control and data acquisition (SCADA) and human-machine interface (HMI) system. As these program the PLC, infecting them destroys the proper programming of PLC. This results in an improper automation process by PLC, disrupting the industrial process on a large scale. Stuxnet initially spreads in three systems, each of which has the capability of infecting another three and so on.

Stuxnet has a record of causing substantial damage to Iran’s nuclear program. The worm can be wiped out by a suitable anti-virus program.

Once Stuxnet reached its supremacy, a so-called extended version of Stuxnet was developed, not with the same notion of destroying industrial control systems, but with the aim of gaining information from and deleting recent information in those systems [7]. The attack was created by Unit 8200 of the Israeli Intelligence Corps in 2009. The unit captures sensitive information that is encrypted and transferred as signals.

The worm creates a file, with a prefix ~DQ, in the infected system. Hence, the model is named Duqu. Duqu also targeted the Iran nuclear program, but with the goal of gathering sensitive information, instead of demolishing it. Unlike Stuxnet, the worm is very difficult to predict because of its passive nature. This behavior let it prevail in Kaspersky Lab for a long time without being detected. Once the threat was discovered in 2010, the worm program codes were kept and added in antivirus software.

The recent attackers started concentrating on espionage rather than sabotage. The result was the development of a modular computer worm named Flame [7] in 2012. The worm, also known as Skywiper, has the ability to wipe away the contents in the infected system. Kaspersky Lab² and CrySyS Lab³ called it the most tedious malware they had ever seen. The wiper acquires the system in a similar way as its ancestors, Stuxnet and Duqu, by affecting the rootkit functionality. Flame is capable of spreading over a LAN or via a USB stick. It can capture user activities by recording audio and capturing screenshots, keystrokes and network traffic. Skype conversations also find a place on the list. The collected data and other files can be sent to the control server for analysis by attackers. The worm targeted sources in Iran, Syria and Israel. Kaspersky entered into a program with its competitors as yet another precaution against the espionage worm.

### 5.2 Ransomware Attacks

Ransomware continues to be the most threatening form of modern cybercrime [8]. Ransomware acquires data from an entire computer through email attachments, drive-by downloads, malicious pdfs and exploit kits, and then openly blackmails the owners by asking them to pay to restore the computer to its original state. The malware may be locker, where the entire system is locked and not able to be used, or it may be crypto, where some dedicated, sensitive files are locked and access is denied. The lock or access denial is released only after the demand is met for mammoth amounts of bitcoins to be transferred to the hackers as a fine, owing to the innocence of the owner. Also, ransomware makes no assertions that the key will decrypt the lock on files or the system even after the fine is

¹ https://w3.siemens.com/
² https://www.kaspersky.com/
³ https://www.crysis.hu/
