
# Hacking

**Hacking** originally meant tinkering or modifying systems to learn and explore. However, the term has come to refer to malicious and possibly criminal intrusion into and manipulation of computers. In either case, a malicious or criminal hacker is a serious threat. Every network administrator should be concerned about hacking.

Some important aspects of security stem from understanding the techniques, methods, and motivations of hackers. Once you learn to think like a hacker, you may be able to anticipate future attacks. This enables you to devise new defenses before a hacker can successfully **breach** your organization’s network.

So how do hackers think? Hackers think along the lines of manipulation or change. They look into the rules to create new ways of bending, breaking, or changing them. Many successful security breaches have been little more than slight variations or violations of network communication rules.

Hackers look for easy targets or overlooked vulnerabilities. Hackers seek out targets that provide them the most gain, often financial rewards. Hackers turn things over, inside out, and in the wrong direction. Hackers attempt to perform tasks in different orders, with incorrect values, outside the boundaries, and with a purpose to cause a reaction. Hackers learn from and exploit mistakes, especially mistakes of the network security professionals who fail to properly protect an organization’s assets.

![Image](images/pg8.jpg)

**FIGURE 1-2**

The seven domains of a typical IT infrastructure.

Why is thinking like a hacker critically important? A sixth century Chinese military strategist and philosopher, Sun Tzu, in his famous military text *The Art of War*, stated: “If you know the enemy and know yourself you need not fear the results of a hundred battles.” Once you understand how hackers think, the tools they use, their exploits, and the attack techniques they employ, you can create effective defenses to protect against them.

You’ve often heard that “the best defense is a good offense.” While this statement may have merit elsewhere, most network security administrators do not have the luxury—or legal right—to attack hackers. Instead, you need to turn this strategic phrase around: The best offense is a good defense. While network security administrators cannot legally or ethically attack hackers, they are fully empowered to defend networks and assets against hacker onslaughts.

## Seven Domains of a Typical IT Infrastructure

Hackers look for any and every opportunity to exploit a target. No aspect of an IT infrastructure is without **risk,** nor is it immune to the scrutiny of a hacker. When thinking like a hacker, analyze every one of the seven **domains** of a typical IT infrastructure ([Figure 1-2](#07_chapter01.xhtml#fig1-2)) for potential vulnerabilities and weaknesses. Be thorough. A hacker needs only one crack in the protections to begin chipping away at the defenses. You need to find every possible breach point to secure it and harden the network.

The seven domains of a typical IT infrastructure are:

![Image](images/bull1.jpg) **User Domain**—This domain refers to actual users, whether they are employees, consultants, contractors, or other third-party users. Any user who accesses and uses the organization’s IT infrastructure must review and sign an acceptable use policy (`AUP`) prior to being granted access to the organization’s IT resources and infrastructure.

![Image](images/bull1.jpg) **Workstation Domain**—This domain refers to the end user’s desktop devices such as a desktop computer, laptop, `VoIP` telephone, or other endpoint device. Workstation devices typically require security countermeasures such as antivirus, anti-spyware, and vulnerability software patch management to maintain the integrity of the device.

![Image](images/bull1.jpg) **LAN Domain**—This domain refers to the physical and logical **local area network (LAN)** technologies (i.e., 100Mbps/1000Mbps switched Ethernet, 802.11 family of wireless LAN technologies) used to support workstation connectivity to the organization’s network infrastructure.

![Image](images/bull1.jpg) **LAN-to-WAN Domain**—This domain refers to the organization’s internetworking and interconnectivity point between the LAN and the WAN network infrastructures. Routers, firewalls, **demilitarized zones (DMZ)**, and **intrusion detection systems (IDS)** and **intrusion prevention systems (IPS)** are commonly used as security monitoring devices in this domain.

![Image](images/bull.jpg) **Remote Access Domain**—This domain refers to the authorized and authenticated remote access procedures for users to remotely access the organization’s IT infrastructure, systems, and data. Remote access solutions typically involve `SSL-128` bit encrypted remote browser access or encrypted `VPN` tunnels for secure remote communications.

![Image](images/bull1.jpg) **WAN Domain**—Organizations with remote locations require a **wide area network (WAN)** to interconnect them. Organizations typically outsource WAN connectivity from service providers for end-to-end connectivity and bandwidth. This domain typically includes routers, circuits, switches, firewalls, and equivalent gear at remote locations, sometimes under a managed service offering by the service provider.

![Image](images/bull1.jpg) **System/Application Domain**—This domain refers to the hardware, operating system software, database software, client/server applications, and data that is typically housed in the organization’s data center and/or computer rooms.

The first step is recognizing that the potential for compromise exists throughout an organization. The next step is to comprehend the goals of network security.

## Goals of Network Security

Network **security goals** vary from organization to organization. Often, however, they include a few common mandates:

![Image](images/bull1.jpg) Ensure the confidentiality of resources

![Image](images/bull1.jpg) Protect the integrity of data

![Image](images/bull1.jpg) Maintain availability of the IT infrastructure

![Image](images/bull1.jpg) Ensure the privacy of personally identifiable data

![Image](images/bull1.jpg) Enforce access control

![Image](images/bull1.jpg) Monitor the IT environment for violations of policy

![Image](images/bull1.jpg) Support **business tasks** and the overall mission of the organization

Whatever your organization’s security goals are, to accomplish them, you need to write down those goals and develop a thorough plan to execute them. Without a written plan, security will be haphazard at best and will likely fail to protect your assets. With a written plan, network security is on the path to success. Once you define your security goals, these goals will become your organization’s roadmap for securing the entire IT infrastructure.

## How Can You Measure the Success of Network Security?

An organization measures the security of its network by how well its stated security goals are accomplished and its security standards maintained. In essence, this becomes the organization’s baseline definition for information systems security. For example, if private information on the network does not leak to outsiders, then your efforts to maintain confidentiality were successful. Or, if employees are able to complete their work on time and on budget, then your efforts to provide system integrity protection were successful.

If violations take place that compromise your assets or prevent the accomplishment of a security goal, however, then network security was less than successful. But let’s face it, security is never perfect. In fact, even with well-designed and executed security, accidents, mistakes, and even intentional harmful exploits will dog your best efforts. The perfect security components do not exist. All of them have weaknesses, limitations, **backdoors**, work-arounds, programming bugs, or some other exploitable element.
