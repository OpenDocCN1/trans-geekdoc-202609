
## References

[1] Warrell, H and Wright, R (2019) Balfour Beatty sacked from MI6 refurbishment contract, *Financial Times*, 27 December, [`www.ft.com/content/81d4ac8c-28d9-11ea-9a4f-963f0ec7e134`](http://www.ft.com/content/81d4ac8c-28d9-11ea-9a4f-963f0ec7e134) (archived at [`https://perma.cc/234D-3JJT`](https://perma.cc/234D-3JJT))

[2] Ritschel, C (2019) Mother releases video of hacker talking to eight-year-old child through Ring camera, *Independent*, 12 December, [`www.independent.co.uk/news/world/americas/ring-camera-video-hack-security-mississippi-child-a9244326.html`](http://www.independent.co.uk/news/world/americas/ring-camera-video-hack-security-mississippi-child-a9244326.html) (archived at [`https://perma.cc/64Z5-QJ62`](https://perma.cc/64Z5-QJ62))

[3] Kellon, L (2018) MiSafes' child-tracking smartwatches are 'easy to hack', BBC News, 15 November, [`www.bbc.co.uk/news/technology-46195189`](http://www.bbc.co.uk/news/technology-46195189) (archived at [`https://perma.cc/PN89-X9U5`](https://perma.cc/PN89-X9U5))

[4] Anderson, N (2006) Steal David Beckham's car with a laptop, Ars Technica, 5 April, [`https://arstechnica.com/uncategorized/2006/05/6750-2`](https://arstechnica.com/uncategorized/2006/05/6750-2)/ (archived at [`https://perma.cc/4D4R-M2D8`](https://perma.cc/4D4R-M2D8))

[5] Greenberg, A (2015) Hackers remotely kill a Jeep on the highway – with me in it, Wired, 21 July, [`www.wired.com/2015/07/hackers-remotely-kill-jeep-highway`](http://www.wired.com/2015/07/hackers-remotely-kill-jeep-highway) (archived at [`https://perma.cc/WRP9-WGLH`](https://perma.cc/WRP9-WGLH))

[6] FBI (2016) Motor vehicles increasingly vulnerable to remote exploits, FBI Public Service Announcement, 17 March, [`www.ic3.gov/media/2016/160317.aspx`](http://www.ic3.gov/media/2016/160317.aspx) (archived at [`https://perma.cc/49CK-BAZB`](https://perma.cc/49CK-BAZB))

[7] DEFCON Conference (2019) Jmaxxz – your car is my car (online video), [`www.youtube.com/watch?v=w8SG2V3n4-U`](http://www.youtube.com/watch?v=w8SG2V3n4-U) (archived at [`https://perma.cc/3QHB-JXUU`](https://perma.cc/3QHB-JXUU))

[08](#04_toc01.xhtml#fm_toc_078)

There is no one security solution that will protect an organization. As we have seen, security relies on a layered set of defences in conjunction with monitoring and testing of those defences to ensure that they maintain required levels of defence, detection and response. The first step in establishing a security programme is understanding the information assets you have and what value they represent for the organization, its clients or customers, and those who might seek to access and abuse the information. Cataloguing the assets and performing risk assessments (as covered in [Chapter 2](#09_chapter02.xhtml#ch02_sec_001)) is a fundamental part of establishing what level of security to ascribe to which systems and assets, and therefore which controls to put in place. Using a framework (such as the National Institute of Standards and Technology (NIST) Cybersecurity Framework or ISO 27001) will help many organizations with the process of categorizing information assets, conducting risk assessments and determining appropriate controls (as we will discuss in [Chapter 12](#23_chapter12.xhtml#ch12_sec_001)). In this chapter, we are going to look at the common security controls and practices that organizations use to better protect themselves.

## [Firewalls](#04_toc01.xhtml#fm_toc_079)

Firewalls are commonly regarded as the first line of defence in cyber security, a gateway that is intended to protect an internal, secured network from threats that exist on the open internet. A firewall sits on the network, as hardware and/or software, and monitors traffic that is coming in and going out. Using a set of rules, it determines traffic that is authorized or expected to come into the network and where it can go. The rules revolve around the data source, destination and ports. A simple analogy would be to imagine a security desk in a shared building as the firewall; the security desk decides who can be allowed in and where they are able to go within the building, depending on who they are and how trusted they are.

## [Anti-virus software](#04_toc01.xhtml#fm_toc_080)

Anti-virus software can also be understood as anti-malware. It traditionally works by detecting and removing computer viruses and malicious software, running in the background of systems and searching for signatures of known malware (if you imagine that each piece of malware has a fingerprint, it is searching for the fingerprint). A key limitation of this, of course, is that it can only detect and remove known malware; it uses a database of known malware signatures and so, when a new threat emerges, its signature will not be in the database. Due to this limitation, anti-virus protections have evolved to monitor the system and pick up on unusual behaviour: when the system does something that is unusual, the anti-virus is triggered. Advances in machine learning have been incorporated in anti-virus, enabling the systems to learn from new data, behaviours and signatures.

## [Network segmentation](#04_toc01.xhtml#fm_toc_081)

Network segmentation is a very important element in an organization's defences, based on the understanding that organizations must not only try to protect against being attacked, but also put in place damage limitation for if (or when) they are breached. Network segmentation means that if one part of an organization or its network is compromised, this compromise can be contained and not infect the whole. This also allows for logical segmentation of an organization, so that different departments have different segments. It works in conjunction with what is called the 'least privilege' principle – that users can only access the minimum that they need in order to do their work – meaning that access to information can be structured more easily on a need to know basis. It also allows for better monitoring and auditing of access to information. This is superior to a flat network, in which nothing is segmented and people can move around the network more freely, accessing information that perhaps should not be available to them.

## [Policies and procedures](#04_toc01.xhtml#fm_toc_083)

Organizations use policies and procedures to capture and communicate expectations, responsibilities and commitments regarding cyber security. They may not be exciting, but they are important as a way of ensuring that the organization has communicated what is expected of people – for example, acceptable use of the internet, password management, what to do if there has been an incident, and who is responsible for cyber security. Some policies are legally required or required for compliance purposes, and they should also be in place to provide legal protection for employees and for the organization. Unfortunately, policies are often neglected or ignored. In 2019, research from ClubCISO found that 53 per cent of senior information security leaders who took part in the survey stated that they believed their policies are ineffective, dormant or don't affect day-to-day behaviours.^([2](#18_chapter08.xhtml#ch08_en2)) For policies to be effective and useful, it is important they are kept up to date, that they are written in jargon-free and concise language, that people know where to find them in the organization (for example, that they are easy to navigate to on the intranet) and that relevant information is easy to find within them.

## [Logging](#04_toc01.xhtml#fm_toc_084)
