
The WannaCry virus had an odd feature: It had a built-in kill switch. If a particular URL was registered, that would kill WannaCry. A man named Marcus Hutchins accidentally discovered the kill switch and stopped WannaCry. Hutchins was initially hailed as a hero, but he was later arrested by the FBI (not in connection with WannaCry) for developing and selling banking Trojan malware.

##### Petya

Petya was first discovered in 2016 but continued to spread all the way into 2018. It targeted Windows machines, infecting the boot sector and encrypting the hard drive’s file system. It then demanded payment in bitcoin. This is an excellent example of a virus combining multiple features. The virus’s name comes from the 1995 James Bond movie *Golden Eye*, in which Petya is one of the Soviet weapons satellites.

##### Shamoon

The Shamoon virus was first discovered in 2012, and a variant resurged in 2017. Shamoon acts as spyware but deletes files after it has uploaded them to the attacker. The virus attacked Saudi Aramco workstations, and a group named Cutting Sword of Justice claimed responsibility for the attack.

##### Rombertik

Rombertik wreaked havoc in 2015. This malware uses the browser to read user credentials to websites. It is most often sent as an attachment to an email. Perhaps even worse, in some situations Rombertik will either overwrite the master boot record on the hard drive, making the machine unbootable, or begin encrypting files in the user’s home directory.

##### Gameover ZeuS

Gameover ZeuS is a virus that creates a peer-to-peer botnet. Essentially, it establishes encrypted communication between infected computers and the command and control computer, allowing the attacker to control the various infected computers. (A command and control computer is the computer used in a botnet to control the other computers. These are the central nodes from which a botnet will be managed.) In 2014 the U.S. Department of Justice was able to temporarily shut down communication with the command and control computers; then in 2015 the FBI announced a reward of $3 million for information leading to the capture of Evgeniy Bogachev for his alleged involvement with Gameover ZeuS.

##### CryptoLocker and CryptoWall

One of the most widely known examples of ransomware is the infamous CryptoLocker, first discovered in 2013. CryptoLocker utilized asymmetric encryption to lock the user’s files. Several varieties of CryptoLocker have been detected.

CryptoWall is a variant of CryptoLocker first found in August 2014. It looked and behaved much like CryptoLocker. In addition to encrypting sensitive files, however, it would communicate with a command and control server and even take a screenshot of the infected machine. By March 2015 a variation of CryptoWall had been discovered bundled with the spyware TSPY\_FAREIT.YOI; this variant actually steals credentials from the infected system in addition to holding files for ransom.

##### Atlanta’s Ransomware Attack

The city of Atlanta, Georgia, was hit with ransomware in March 2018. Many of the city’s systems were impacted, including utilities, courts, and other essential systems. Two Iranian hackers, Faramarz Savandi and Mohammed Mansouri, were indicted for the attack. This attack is noteworthy for several reasons. The first is that it used the SamSam ransomware, which gets access to systems not through phishing but rather via brute-force password guessing. The second issue is that Atlanta had previously been criticized for failing to spend adequately on security. An audit just 2 months before the attack had found 1500 to 2000 vulnerabilities.

##### FakeAV

While the FakeAV virus has been around for several years, it is well worth studying. This virus, which first appeared in July 2012, affected Windows systems ranging from Windows 95 to Windows 10 and Windows Server 2016. It was a fake antivirus (thus the name FakeAV) that would pop up fake virus warnings. This was not the first such fake antivirus malware, but it is a successful example of the type.

##### MacDefender

The MacDefender virus is very interesting for multiple reasons. First, it specifically targets Mac computers. Most experts for a long time agreed that Apple products remained relatively virus free simply because their products did not have enough market share to attract the attention of virus writers. Many suspected that if Apple garnered a greater market share, it would also begin to experience more virus attacks, and this has proven to be true.

The MacDefender virus was first seen in the early months of 2011, and variations are still seen today. It is embedded in some web pages, and when a user visits those web pages, she is given a fake virus scan that tells her she has a virus, and it needs to be fixed. The “fix” is actually downloading a virus. The point of the virus is to get end users to purchase the MacDefender “antivirus” product. This is the second reason this case is noteworthy. Fake antivirus attacks, also known as *scareware*, have been becoming increasingly common.

##### Kedi RAT

In September 2017 the Kedi RAT (Remote Access Trojan) virus was spreading through phishing emails. Once on an infected system, it would steal data, and then it would exfiltrate that data by emailing it via a Gmail account. It specifically attempted to identify personal and/or financial data on the infected system to sell.

##### The Sobig Virus

Sobig, which was first found in 2003, is not a recent virus, but it is an excellent virus to study because it received a lot of media attention and caused a lot of harm when it hit. This virus used a multimodal approach to spreading—that is, it used more than one mechanism to spread and infect new machines. It would copy itself to any shared drives on your network and would email itself out to everyone in your address book. Sobig was therefore particularly virulent, which is also why it is important to study.

FYI: Virulent Virus

The term *virulent* means essentially the same thing in reference to a computer virus as it does in relationship to a biological virus: It is a measure of how rapidly the infection spreads and how easily it infects new targets.

In the case of Sobig, if one person on a network was unfortunate enough to open an email containing the virus, not only would his machine be infected, but so would every shared drive on that network to which this person had access. However, Sobig, like most other email-distributed virus attacks, had telltale signs in the email subject or title that could be used to identify the email as one infected by a virus. The email would have some enticing title such as “here is the sample” or “the document” to encourage you to be curious enough to open the attached file. The virus would then copy itself into the Windows System directory.

This particular virus spread so far and infected so many networks that the multiple copying of the virus alone was enough to bring some networks to a standstill. This virus did not destroy files or damage the system, but it generated a great deal of traffic that bogged down the networks it infected. The virus itself was of moderate sophistication. Once it was out, however, many variants began to spring up, further complicating the situation. One of the effects of some variants of Sobig was to download a file from the Internet that would then cause printing problems. Some network printers would just start printing junk. The Sobig.E variant would even write to the Windows Registry, causing itself to be in the computer startup. These complex characteristics indicate that the creator knew how to access the Windows Registry, access shared drives, alter the Windows startup, and access Outlook.
