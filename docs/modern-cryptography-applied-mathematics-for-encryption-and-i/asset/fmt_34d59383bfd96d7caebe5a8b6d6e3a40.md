
![image](Images/image00484.jpeg) The actual malware code (which is encrypted)

![image](Images/image00484.jpeg) A module to perform encryption/decryption

![image](Images/image00484.jpeg) A key

Cryptoviral extortion, or ransomware, is another application of cryptovirology. `Ransomware` is malware that, once it has infected the target machine, encrypts sensitive files on that machine. The machine user is then sent a ransom message, demanding money for the attacker to decrypt the files. The One_Half virus, first reported in 2007, would encrypt certain files but did not demand ransom.^([8](#part0026.xhtml#ch15note8a)) The PGPCoder, or GPCode (Virus.Win32.Gpcode.ag), used a 660-bit version of RSA to encrypt certain files. It then asked for a ransom. If the ransom was paid, the victim was sent a key to decrypt the files.

The infamous CryptoLocker is one of the most widely known examples of a cryptovirus that was first discovered in 2013. CryptoLocker used asymmetric encryption to lock the user’s files. Several varieties of the virus have been detected, including CryptoWall, which was first found in August 2014.^([9](#part0026.xhtml#ch15note9a)) It looked and behaved much like CryptoLocker, but in addition to encrypting sensitive files, it would communicate with a command and control server, and even take a screenshot of the infected machine. In March 2015, a variation of CryptoWall was discovered, which is bundled with the spyware TSPY_FAREIT.YOI and actually steals credentials from the infected system in addition to holding files for ransom.^([10](#part0026.xhtml#ch15note10a))

**Note**

The viruses mentioned here are just a sample of viruses that use encryption. The purpose of this chapter is not to educate you on viruses, but the line between viruses and cryptography is becoming blurred. As you have seen, cryptography can be used with malware to create both new forms of malware (ransomware) and enhanced viruses (armored viruses).

##### Weaponized Malware

Moving forward, we should expect to see more examples of malware-based attacks and state-sponsored malware espionage, as indicated in the “Worldwide Threat Assessment of the US Intelligence Community” report.^([11](#part0026.xhtml#ch15note11a)) Several nations have either already been discovered to have been engaged in such activities or are strongly suspected of being engaged in such activities. Most analysts believe that the Stuxnet and Flame viruses were designed for the express purpose of cyber-espionage and/or sabotage of the Iranian government.^([12](#part0026.xhtml#ch15note12a))

###### Stuxnet Virus

As the first example of cyber-warfare via malware infections, consider the Stuxnet virus. Stuxnet first spread via infected thumb drives; however, after it infected a machine, it would spread over the entire network and even over the Internet. The Stuxnet virus then searched for a connection to a specific type of programmable logic controller (PLC), specifically the Siemens STEP 7 software. Once Stuxnet discovered that PLC, the virus would load its own copy of a specific dynamic link library (DLL) to monitor the PLC and then alter the PLC’s functionality. It was meant to target only centrifuge controllers involved in Iran’s uranium enrichment program.^([13](#part0026.xhtml#ch15note13a)) Clearly this was meant to be a targeted attack, but it spread beyond the intended targets. Although many reported no significant damage from Stuxnet, outside the Iranian reactors, it was detected on numerous machines. Although the Stuxnet targeting was clearly inadequate, its design was classic virus design. Stuxnet has three modules: a worm that executes routines related to the attack, a link file that executes the propagated copies of the worm, and a rootkit responsible for hiding files and processes, with the goal of making it more difficult to detect the presence of Stuxnet.

**Note**

It is not the purpose of this chapter to explore the intricacies of Stuxnet. Rather Stuxnet is introduced as both an example of state-sponsored malware attacks and at least an attempt to target such attacks.

###### Flame Virus

The Flame virus was first discovered in May 2012 in Iran.^([14](#part0026.xhtml#ch15note14a)) It was spyware that recorded keyboard activity and network traffic; it took screenshots and was even reported to record Skype conversations. It would also turn the infected computer into a Bluetooth beacon that attempted to download information from nearby Bluetooth-enabled devices.

Kaspersky Labs reported that the Flame file contained an MD5 hash that appeared only on machines in the Middle East. This indicated the possibility that the virus authors intended to target the malware attack to a specific geographical region. The Flame virus also appears to have had a kill function that would allow someone controlling it to send a signal directing it to delete all traces of itself. These two items indicate an attempt to target the malware, though like Stuxnet, the outcome of that targeting was less than optimal.

##### Cyber-Warfare

Cyber-warfare may seem like a topic far removed from cryptography. Although a complete discussion of cyber-warfare is beyond the scope of this text, it is appropriate to introduce the topic briefly. As you have already seen, weaponized malware is an element of cyber-warfare, and cryptovirology certainly has a role to play.

Let’s begin by defining cyber-warfare. According to the Rand Corporation, “Cyber warfare involves the actions by a nation-state or international organization to attack and attempt to damage another nation’s computers or information networks through, for example, computer viruses or denial-of-service attacks.”^([15](#part0026.xhtml#ch15note15a)) Cyber-warfare is not just a topic for science fiction. Here are a few real-world incidents:

![image](Images/image00484.jpeg) In 2008, Central Command (CENTCOM) was infected with spyware. CENTCOM is the U.S. Army entity that is responsible for command and control throughout the Middle East and Central Asia. This means that during the conflicts in Iraq and Afghanistan, spyware was infecting a critical military system for at least a certain period of time.

![image](Images/image00484.jpeg) In 2009, drone video feed was compromised. In Afghanistan, an unknown attacker was able to tap into the video feed of a U.S. drone and watch the video feed.

![image](Images/image00484.jpeg) On December 4, 2010, a group calling itself the Pakistan Cyber Army hacked the web site of India’s top investigating agency, the Central Bureau of Investigation (CBI).

![image](Images/image00484.jpeg) In December 2009, hackers broke into computer systems and stole secret defense plans of the United States and South Korea. Authorities speculated that North Korea was responsible. The information stolen included a summary of plans for military operations by South Korean and U.S. troops in case of war with North Korea, though the attacks were traced back to a Chinese IP address.

![image](Images/image00484.jpeg) The security firm Mandiant tracked several advanced persistent threats (APTs) over a period of seven years, all originating in China, specifically Shanghai and the Pudong region. These APTs were named APT1, APT2, and so on. The attacks were linked to the UNIT 61398 of the Chinese military. The Chinese government regards this unit’s activities as classified, but it appears that offensive cyber-warfare is one of its tasks. Just one of the APTs from this group compromised 141 companies in 20 different industries. APT1 was able to maintain access to victim networks for an average of 365 days, and in one case for 1764 days. APT1 is responsible for stealing 6.5 terabytes of information from a single organization over a 10-month timeframe.
