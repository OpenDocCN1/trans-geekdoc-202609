
The community benefits as a whole as a result of this. If a security intelligence organization anywhere in the world encounters a previously unseen threat, there is now information on it. While that organization may have been compromised, the information gathered and shared will allow all other organizations to better protect themselves from it. There are various security intelligence clouds out there that all revolve around the same concepts, but they must first author the security intelligence. Once the intelligence is created, the cloud must distribute it to the participants. Finally, each member must consume the intelligence and apply it in a way that makes sense. In the following chapter, I'll go over the various aspects of security intelligence.

# Chapter 18

# Authoring the intelligence

# ![How The Right Authoring Tools Affect Training? - IntelligentHQ](image.026.jpeg)

First, let's talk about who created the intelligence. To author any intelligence about the current threats, information must first be provided. Telemetry sharing is a very powerful way for the security intelligence cloud to discover what is happening in real-time to an organization's networks. Telemetry sharing occurs when the devices themselves upload the data that they have seen to a larger network or cloud for further analysis. Continue with the previous chapter's example of a global organization that encountered a previously unseen threat. Let's call that organization Sunshine Store. When a threat affects Sunshine Store, their devices now have valuable information about that threat. If they participate in threat telemetry sharing, this information is shared with the rest of the security intelligence cloud. This is done automatically from the device to the cloud and does not require any manual intervention from the security engineer. Every other organization in the security intelligence cloud is also sharing critical information about cloud threats. All of the sharing provides valuable context about the threat that could not have come from a single source. Perhaps the threat occurs at the same time of day for each organization, or perhaps the threat is limited to a specific country or industry. Better inferences can be made by having a larger sample pool contribute data to the cloud.

A cloud will then perform various tasks on the information, such as normalizing it and analyzing it to find patterns. The intelligence clouds can determine various factors such as the type of threat, the frequency with which the attack occurs, the surface area within the organization that the threat used to gain access to, the severity of the impact, and many more metrics. As previously stated, when the cloud analyses threats, it determines whether there are targeted industries, targeted nations, or other patterns. As more information about the threat becomes available, the security intelligence cloud can devise various countermeasures. The security intelligence cloud can now generate different signatures and content updates for all of the cloud's products.

The organization's email security devices will participate in the security intelligence cloud, and an update will be issued to that email secure device for it to block the threat. For example, if another company decided to join the threat intelligence cloud, such as Cisco Talos, they would provide the email security appliance with the most recent updates to block threats identified as using email as the attack medium. This is the same as an intrusion prevention system. An update would be created around all threats that can be stopped using an IPS, or Intrusion Prevention System. As a result, any IPS that install that update will block this new threat. Cisco Talos would receive an update on the company's next-generation intrusion prevention system. This leads us to the sharing and consumption of security intelligence. Now that the security intelligence cloud has created various updates and signatures for the threats that it has encountered, it is time to share them with the rest of the security intelligence community.

This is typically accomplished through the use of content update pushes, and organizations such as Cisco Talos have content updates every 3-5 minutes. Once the update has been downloaded, each device must now install it, and once the content has been installed, each device is now ready to block the latest threat. Similarly, a new threat has affected organizations within the security intelligence cloud, including Sunshine Store. Because another company was participating in the cloud, as soon as the threat was analyzed, the appropriate mitigations were discovered and the updates were created, pushed, and installed. This new company is now safe from this new threat. What makes this so beneficial is that it occurs without any manual intervention from the security engineer.

They no longer need to conduct this research on their own, figure out how to stop it, and then manually apply their changes. Speaking of research, I'd like to point out that security intelligence information sharing does not only refer to the automatic updates that devices receive. It is an entire ecosystem that enables security professionals to understand the threats as well. While it is great that network security devices can be automatically configured to stop new threats, it would be a disservice if administrators were unaware of the threats and mitigations that were being implemented. Having a better understanding of the most recent security threats will only benefit you as a security engineer. The more you are aware of the various types of threats and the actual methods they use to infiltrate networks and cause havoc, the better you will be able to understand the big picture.

# Chapter 19

# ARP Poisoning

# ![ARP spoofing attacks - CCNA Security 210-260 Certification Guide \[Book\]](image.027.png)

When it comes to a Man in the Middle attack, it can take many forms, but the most common is known as ARP poisoning.

To understand ARP poisoning, you must first understand how ARP, also known as Address Resolution Protocol, works.

ARP converts IP addresses to MAC addresses, also known as physical addresses, of all networking devices connected to a specific network device. The command on a Windows machine is `arp –a`, but the same command can be used on other operating systems as well.

To launch Command Prompt on a Windows operating system, click the Start button, type Command Prompt, and press Enter. After that, simply type `arp` and press enter to see all options related to the `arp` command.

After you've done that, you'll notice the following variations;

• `Arp – a` > This command displays the current ARP entries connected to the network that the computer is aware of, listing both the IP and MAC addresses of those devices.

• `Arp – d` > This command removes the ARP entry for the host you specify.

• `Arp – s` > This command will assist you in adding hosts and assigning them an IP address.

• `Arp – v` > This command displays the current ARP entries in verbose mode, as well as all invalid entries and the loopback interface.

These are some of the basic variations and options available when it comes to ARP, but it is not necessary to be aware of all available options.

To return to ARP poisoning, once connected, computers and networking devices on the same network learn each other's Mac Addresses. They will create an ARP table once they have learned each other's MAC addresses, and they will use that table to locate each other on the same network in the future.

This is how ARP assists computers and networking devices in easily discovering each other on the network; however, hackers would take advantage of ARP tables by introducing themselves on the network with bogus MAC addresses, fooling computers into thinking they were the new Router. As a result, the real ARP table would be tainted with bogus entries.
