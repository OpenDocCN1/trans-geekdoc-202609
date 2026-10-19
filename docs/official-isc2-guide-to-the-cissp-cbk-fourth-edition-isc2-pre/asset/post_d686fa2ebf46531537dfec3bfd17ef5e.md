
of an overall access control lifecycle.

Crimeware, mainly financially driven attacks using automated attack toolkits, is a common problem faced by nearly every industry, and Verizon found crimeware associated with more than 12,000 security incidents and 50 data breaches in 2013. The Zeus and SpyEye Trojan families spread quickly by organized cybercriminal networks that use spam messages and malicious links to trick people into downloading the dangerous malware. The malware is designed to steal account credentials and drain bank accounts. Many infections happen by simply visiting an attack website or downloading a malicious file. Security architects need to deploy browser security patches and apply updates to browser plug-ins. Java should be disabled or uninstalled if it is not needed. In addition, the use of at least two-factor authentication would thwart many attacks that use stolen credentials.

Distributed denial-of-service attacks, designed to cripple the network or bring down websites and Web applications, are being carried out by attackers that are compromising servers in public and private cloud data centers to increase the bandwidth of their attacks. Verizon analyzed more than 1,100 total security incidents in 2013. Security architects should have a plan in place and consider the use of an Internet service provider DDoS mitigation service and also consider isolating IP address spaces not in active use.

There were more than 7,200 security incidents that do not fit into a common incident pattern, according to the Verizon report. Nearly all of these attacks were external and were browser-based threats, using a combination of hacking, phishing, and malware. Three-quarters of all incidents involved compromised Web servers, and they usually represented mass attacks, in which hundreds of servers are hijacked to host malware for drive-by attacks or phishing sites.

The security architects should use a variety of resources and data points to gather a picture of the threats facing their networks. Resources such as the Verizon Data Breach Investigations Report are valuable because they present findings across a large variety of industries and architectures. Some additional resources that the security architect may find helpful in this regard are listed below:

- The Secunia Vulnerability Review 2014: http://secunia.com/?action=fetch&filename=secunia_vulnerability_review_2014.pdf
- The Symantec Internet Security Threat Report 2014: http://www.symantec.com/content/en/us/enterprise/other_resources/b-istr_main_report_v19_21291018.en-us.pdf
- The Sophos Security Threat Report 2014: http://www.sophos.com/en-us/medialibrary/PDFs/other/sophos-security-threat-report-2014.pdf
- The Cisco 2014 Annual Security Report: https://www.cisco.com/web/offer/gist_ty2_asset/Cisco_2014_ASR.pdf
- PricewaterhouseCoopers the Global State of Information Security Survey 2014: http://www.pwc.com/gx/en/consulting-services/information-security-survey/index.jhtml
- Trustwave’s 2014 Security Pressures Report: http://www2.trustwave.com/rs/trustwave/images/2014%20Trustwave%20Security%20Pr
- Websense 2014 Threat Report: http://www.websense.com/assets/reports/report-2014-threat-report-en.pdf

## Systems

Poorly designed systems are ripe for attack. The security architects must familiarize themselves with well-known attacks and vulnerabilities in their industry and the types of systems they work with. They should also possess an understanding of what kinds of threats and capabilities exist concerning the organization’s mission and system. Countless attacks exist; however, some of the most challenging in terms of secure architecture are emanations, state attacks, and covert channels.

### Emanations

System emanations are unintentional electrical, mechanical, optical, or acoustical energy signals that contain information or metadata about the information being processed, stored, or transmitted in a system.[40] One of the earliest public descriptions released by the U.S. National Security Agency describes it as:

> “Any time a machine is used to process classified information electrically, the various switches, contacts, relays, and other components in that machine may emit radio frequency or acoustic energy. These emissions, like tiny radio broadcasts may radiate through free space for considerable distances—a half mile or more in some cases.
>
> Or they may be induced on nearby conductors like signal lines, power lines, telephone lines, or water pipes and be conducted along those paths for some distance—and here we may be talking of a mile or more.
>
> When these emissions can be intercepted and recorded, it is frequently possible to analyze them and recover the intelligence that was being processed by the source equipment. The phenomenon affects not only cipher machines, but any information-processing equipment—teletypewriters, duplicating equipment, intercoms, facsimile, computers—you name it. But it has special significance for crypto-machines because it may reveal not only the plaintexts of individual messages being processed but also that carefully guarded information about the internal machine processes. Thus, conceivably, the machine could be radiating information which could lead to the reconstruction of our daily changing keying variables—and from a Comsec viewpoint, that is absolutely the worst thing that can happen to us. This problem of compromising radiation we have given the cover name TEMPEST.” [41]

Governments, intelligence organizations, and militaries have spent years and countless resources researching emanations. Their research has focused on how to capture them and use or protect against them. TEMPEST is a set of standards designed to shield buildings and equipment to protect them against eavesdropping and passive emanations gathering attempts. One of the more common approaches was the “Red/Black” separation of equipment.

The Red/Black separation requirements meant installing physical security controls such as shielding between normal unclassified (non-sensitive) circuits and equipment and the classified ones. Once it was implemented and certified, the operators must ensure the smallest of changes to the controls were reported because something as small as moving a component a few millimeters can invalidate the installation.

While this may initially seem to apply only to the counter intelligence situations, the prudent security architect will understand today’s competitive market place and the possibility of industrial espionage and the criminal element. As the price of emanations monitoring capability goes down, the incentive to use it by dishonest individuals to steal intellectual property and other assets increases. For example, a research paper by Dmitri Asonov and Rakesh Agrawal describes an emanation attack on an automatic teller machine (ATM).[42] Asonov and Agrawal proposed that the sound (audible emanation) from the ATM pad was different for each key pressed. They studied the keypad and determined they could “listen in” at distances of 15 meters and greater. As a result, they were able to determine about 79% of the key presses accurately. This means an attacker would be able to determine the banking PIN of a person, at a distance, without installing any additional equipment on the ATM. Many security architecture frameworks would miss this vulnerability. A security architect designing banking systems with ATMs would need to take this vulnerability into account and possibly specify the keypad be made of a different material or determine a way to muffle or distort the sound.

### State Attacks

example, an Internet browser may be considered a thin client.

From a security perspective, the advantage of this type of architecture is that it focuses the design and implementation of security services in a single, centralized environment. This can make it easier to design, implement, and verify security services as well as maintain them. Because patches and updates only need to be patched in a central location, most security vulnerabilities can be dealt with quickly and efficiently. At the same time, unpatched vulnerabilities will be inherited across the entire system. This makes any vulnerability much more pervasive and dangerous than in other computing platforms. It also requires very careful control of privileged and non-privileged subjects operating at the same time to ensure that one cannot interfere or leak information to the other.

## Middleware

Middleware is a connectivity software that enables multiple processes running on one or more machines to interact. These services are collections of distributed software that are present between the application running on the OS and the network services, which reside on a network node. The main purpose of middleware services is to help solve many application connectivity and interoperability problems.

In essence, middleware is a distributed software layer that hides the intricacies and heterogeneous distributed environment consisting of numerous network technologies, computer architectures, OS, and programming languages. Some of the services provided are directory services, transaction tracking, data replication, and time synchronization, services that improve the distributed environment. Some examples are workflow, messaging applications, Internet news channels, and customer ordering through delivery.

In recent years, considerable attention has been placed on middleware as a foundation for Service Oriented Architectures (SOA).[43] Organizations are recognizing that continued reliance on legacy systems impedes business imperatives such as growth, speed to market, business, and IT alignment. Moreover, upgrading to newer technologies is an expensive proposition, especially in a struggling economy. With these challenges in mind, organizations are migrating to a more usable and efficient IT architecture, which enables their customers to more closely interact with the company through Internet-based Web applications. In a SOA, disparate entities make their resources available to an entire population in a standardized way. In other words, SOA is a model for distributed computing, wherein applications call other applications over the network. Functionality is distributed over the network, utilizing the ability to find the functionality and the ability to connect to it.
