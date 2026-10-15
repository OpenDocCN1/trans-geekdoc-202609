
A major breach of customer records when a perpetrator was able to gain access to an Amazon Web Services server (that stored Capital One data) by exploiting a misconfigured web application firewall.⁴

The growing use of Internet of Things (IoT) devices is also increasing the attack surface. Although these smart devices offer many benefits and capabilities, they are known to have weaker security protections and are not easily patchable or updatable.⁵ Hackers were able to steal customer data of a casino by exploiting a security vulnerability in the smart sensor used to remotely monitor the casino’s aquarium.⁶ In the healthcare industry, there is a heavy use of IoT devices for a variety of purposes such as tracking hospital bed occupancy, remotely monitoring patients, providing device malfunction alerts, and timely administration of medication.⁷ A recent research report finds that a majority (82%) of healthcare organizations experienced IoT-focused attacks within a one-year period. The breach consequences ranged from stolen health records to disruption of service, compromised end-user safety, and reputational damage.⁸

Today's mobile devices, such as smart phones, are another attractive target for cybercriminals. With organizations allowing employees to use their personal device for work, breaking into such devices will net not only personally identifiable information (PII) but also confidential business data. Such devices are extremely vulnerable and provide a pathway for malware to reach an organization’s cloud or on-premise networks. According to a recent cybersecurity report that polled IT professionals, 59% did not use a mobile threat defense solution to protect employee devices. No wonder hackers are able to successfully compromise these devices in different ways, such as launching phishing and man-in-the-middle (MITM) attacks and installing rogue applications. Lost or stolen devices that have not been appropriately configured for security and remote wipe-outs are prime sources of data breach.⁹

Thus, with increasing digitization and transformation of business processes and models, a highly mobile work environment, greater dependency on cloud-based services, infusion of wearable and IoT devices, and a high level of interorganizational connectivity, hardware and software attack surfaces are growing exponentially. The coronavirus pandemic that began early in 2020 is further fueling the explosion of attack surfaces by compelling remote work. In their rush to embrace extreme digitization, many organizations are sacrificing their cybersecurity postures and temporarily allowing employees to access critical systems and data via insecure devices and networks. Use of social media platforms for confidential and crisis communications and storing work data in low-security storage locations are further exacerbating the security vulnerability problem.¹⁰

## 2.2 The Human Vulnerability Factor

A widely reported 2019 survey found that 99% of cyberattacks are focused on exploiting human vulnerabilities by targeting people instead of computer systems and infrastructure.¹¹ Cybercriminals are continuously refining their social engineering techniques to lead unsuspecting people to commit acts such as downloading and installing malicious email attachments, clicking on fraudulent website links, and unknowingly handing over personal information and login credentials. Some of the most significant data breaches were carried out after stealing login credentials from human actors.

The Yahoo breach that compromised three billion user accounts and cost the company $117.5 million in settlement fines was caused by a spear-phishing attack. One of the Yahoo employees unsuspectingly clicked on an email sent by a Latvian hacker, and this led to the installation of a malicious code. This malware allowed the perpetrators to set up a backdoor opening to a Yahoo server and steal user information.¹²

Similar to Yahoo, eBay suffered a data breach when three of its corporate employees fell for a spear-phishing campaign. Using the access credentials of those employees, attackers were able to break into the company servers and steal personally identifiable information (PII) such as names, emails, physical addresses, phone numbers, and birth dates.¹³

A record-breaking fine of 183M pounds was imposed on British Airways when it was found negligent in protecting customer data. This breach was triggered when humans—British Airways customers—were tricked into completing travel reservations on a rogue site that resembled a legitimate British Airways portal.¹⁴

The following vignette provides a telling account of how susceptible humans are to innovative social engineering techniques.

### Hacking into ParentCo’s Systems

Mike was an ex-hacker who had started his own company that performed legal hacking. Legal hacking is where companies pay someone to attempt to break into their computer systems. Mike sat down with Dave, the CEO of a large corporation called ParentCo, and told him that ParentCo was very much at risk of having its data compromised. He explained to Dave how much money it could potentially cost ParentCo. “One global company suffered a large breach and spent over 100 million on investigating the incident,” Mike told him. “Subsequently they suffered a multibillion-dollar loss in market capitalization because investors lost confidence in them.”

Dave didn’t think that Mike would be able to break into ParentCo’s systems because they had the latest updates on their servers, the best firewalls in place, and layers of security that made it hard for hackers to break through. Since Mike would only charge him if he successfully broke into the system, Dave signed a contract allowing Mike to attempt to break into ParentCo’s computer system.

The next day, Mike came to Dave with several sheets of paper. They contained employee social security numbers, customer and employee bank account numbers, and additionally, sensitive corporate information. Dave was floored. “How did you do this?” he asked Mike.

Mike proceeded to explain that earlier the same day, dressed in blue coveralls, he had walked up to the secretary (who had seen him twice before), flashed an ID card and said, “Hello, I’m Mike with AT&T, and we are upgrading the lines coming to your building. I’m afraid we cut something that we weren’t supposed to, and I need access to the server room in order to make sure that you guys don’t lose connectivity.” Mike showed Dave the card. It was the ID card from the building that Mike worked at; it had his picture but didn’t say anything about AT&T.

Knowing that everyone would be upset if the lines got shut down, the secretary led him to the server room, typed in the security code in the door lock, and opened the door. “Let me know if there is anything you need. We definitely don’t need our telephones to cut off,” she said, as she turned to walk to her desk, leaving Mike alone in the server room.

After a few minutes, Mike had walked back out to the secretary, “Looks like we may be ok, but I need to check one more thing. I need your username and password to check that the MAC addresses and TCP protocols haven’t been affected.”

“Sure thing,” said the secretary, and she jotted her information down for him on a sticky note. Thirty minutes later, Mike was in Dave’s office with a stack of documents containing sensitive information, printed out using one of the ParentCo’s printers. Mike was able to effectively hack ParentCo’s computers using a non-technical method of intrusion in less than an hour. On top of that, Dave’s company didn’t even use AT&T as a provider.

“So, we’ve got a problem,” said Dave as he signed a check over to Mike. “How do we fix it?”

## 2.3 Growing Attack Vectors

The term *attack vectors* refers to methods used by hackers to break into systems and networks and steal sensitive data. These techniques are constantly evolving, and it is a challenge for organizations to keep up with the hacking community and secure their infrastructure from new forms of attacks. Before discussing the delivery channels, let's first review the different types of malware.

### 2.3.1 Malware Types

Malicious code, or malware, is used by cybercriminals to steal information and identities, disrupt operations, execute fraudulent transactions, and more. Some common forms of malware are viruses, worms, Trojans, ransomware, spyware, and adware.15

**Viruses** usually appear as executable files (.exe) and are capable of corrupting and deleting files, altering the way a computer operates, and shutting down devices and networks. True to their biological namesakes, viruses infect clean files and can spread uncontrollably.

**Computer worms** can self-replicate and inflict the same types of damage as viruses. However, unlike viruses, worms are standalone software, and do not require the help of a human or a host program to propagate. Worms exploit a vulnerability to enter the targeted system and then uses file-transport or information-transport features to travel and spread. Often different social engineering techniques (i.e., methods of exploiting perceived trust to elicit sensitive information such as login credentials) are used to trick users to execute computer worm files.

Similar to the large wooden horse left outside the gates of the besieged ancient city of Troy—once the Trojans had hauled the apparent gift inside, enemy soldiers emerged and won the battle for control of the city—the **Trojan** malicious code is often sent as a seemingly legitimate email attachment or as part of a free program download. When the unsuspecting victim clicks on the attachment or downloads the free software, the malware gets transferred to the user's device. If detected, the victim will see a message as depicted in Figure 1. If it stays undetected, the transmitted code can self-execute as timed and cause damage. Some Trojan viruses create a “backdoor” access to the victim's computer, thereby enabling the attacker to access and download confidential files, modify or delete data, and cause other forms of damage. Others have triggered Distributed Denial of Service (DDoS) attacks that flood the network devices with traffic and disrupt operations. Then there is the Trojan banker code that is designed to steal financial account information from user
