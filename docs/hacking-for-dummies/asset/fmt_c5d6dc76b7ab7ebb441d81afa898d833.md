
Cain & Abel is a password-cracking tool that also has network analysis capabilities. You can also use a regular network analyzer, such as the commercial products Omnipeek ([`https://www.savvius.com`](https://www.savvius.com)) and CommView ([`https://www.tamos.com/products/commview`](https://www.tamos.com/products/commview)), as well as the free open-source program Wireshark ([`https://www.wireshark.org`](https://www.wireshark.org)). With a network analyzer, you can search for password traffic in various ways. To capture POP3 password traffic, for example, you can set up a filter and a trigger to search for the PASS command. When the network analyzer sees the PASS command in the packet, it captures that specific data.

Network analyzers require you to capture data on a hub segment of your network or via a monitor/mirror/span port on a switch. Otherwise, you can’t see anyone else’s data traversing the network — just yours. Check your switch’s user guide to see whether it has a monitor or mirror port and for instructions on how to configure it. You can connect your network analyzer to a hub on the public side of your firewall. You’ll capture only those packets that are entering or leaving your network — not internal traffic. I cover this type of network infrastructure hacking in detail in [Chapter 9](#c09.xhtml).

#### COUNTERMEASURES

Here are some good defenses against network analyzer attacks:

*   **Use switches on your network, not hubs.** Ethernet hubs are things of the past, but I still see them in use occasionally. If you must use hubs on network segments, a program like sniffdet ([`http://sniffdet.sourceforge.net`](http://sniffdet.sourceforge.net)) for Unix/Linux-based systems and PromiscDetect ([`http://ntsecurity.nu/toolbox/promiscdetect`](http://ntsecurity.nu/toolbox/promiscdetect)) for Windows can detect network cards in *promiscuous mode* (accepting all packets, whether they’re destined for the local machine or not). A network card in promiscuous mode signifies that a network analyzer may be running on the network.

*   **Make sure that unsupervised areas, such as an unoccupied lobby or training room, don’t have live network connections.** An Ethernet port is all someone needs to gain access to your internal network.

*   **Don’t let anyone without a business need gain physical access to your switches or to the network connection on the public side of your firewall.** With physical access, a hacker can connect to a switch monitor port or tap into the unswitched network segment outside the firewall and then capture packets.

![warning](images/warning.png)Switches don’t provide complete security because they’re vulnerable to ARP poisoning attacks, which I cover in [Chapter 9](#c09.xhtml).

#### Weak BIOS passwords

Most computer BIOS (basic input/output system) settings allow power-on passwords and/or setup passwords to protect the computer’s hardware settings that are stored in the CMOS chip. Here are some ways around these passwords:

*   You usually can reset these passwords by unplugging the CMOS battery or by changing a jumper on the motherboard.

*   Password-cracking utilities for BIOS passwords are available on the Internet and from computer manufacturers.

*   If gaining access to the hard drive is your ultimate goal, you can remove the hard drive from the computer and install it in another one, and you’re good to go. This technique is a great way to prove that BIOS/power-on passwords are *not* effective countermeasures for lost or stolen laptops.

![tip](images/tip.png)For a good list of default system passwords for various vendor equipment, check [`https://www.cirt.net/passwords`](https://www.cirt.net/passwords).

Tons of variables exist for hacking and hacking countermeasures depending on your hardware setup. If you plan to hack your own BIOS passwords, check for information in your user manual, or refer to the BIOS password-hacking guide I wrote at [`http://searchenterprisedesktop.techtarget.com/tutorial/BIOS-password-hacking`](http://searchenterprisedesktop.techtarget.com/tutorial/BIOS-password-hacking). If protecting the information on your hard drives is your ultimate goal, full (sometimes referred to as *whole*) disk is the best way to go. I cover mobile-related password cracking in depth in [Chapter 11](#c11.xhtml). The good news is that newer computers (within the past five years or so) use a new type of BIOS called unified extensible firmware interface (UEFI), which is much more resilient to boot-level system cracking attempts. Still, a weak password may be all it takes for the system to be exploited.

#### Weak passwords in limbo

Bad guys often exploit user accounts that have just been created or reset by a network administrator or help desk. New accounts may need to be created for new employees or even for security testing purposes. Accounts may need to be reset if users forget their passwords or if the accounts have been locked out because of failed attempts.

#### WEAKNESSES

Here are some reasons why user accounts can be vulnerable:

*   When user accounts are reset, they’re often assigned an easily cracked or widely-known password (such as the user’s name or the word *password*). The time between resetting the user account and changing the password is a prime opportunity for a break-in.

*   Many systems have default accounts or unused accounts with weak passwords or no passwords at all. These accounts are prime targets.

#### COUNTERMEASURES

The best defenses against attacks on passwords in limbo are solid help-desk policies and procedures that prevent weak passwords from being available at any given time during the new-account-generation and password-reset processes. Following are perhaps the best ways to overcome this vulnerability:

*   Require users to be on the phone with the help desk or to have a help-desk member perform the reset at the user’s desk.

*   Require that the user immediately log in and change the password.

*   If you need the ultimate in security, implement stronger authentication methods, such as challenge/response questions, smart cards, or digital certificates.

*   Automate password reset functionality via self-service tools on your network so that users can manage most of their password problems without help from others.

I cover mobile-related password cracking in [Chapter 11](#c11.xhtml) and website/application password cracking in [Chapter 15](#c15.xhtml).

### General Password Cracking Countermeasures

A password for one system usually equals passwords for many other systems because many people use the same (or at least similar) passwords on every system they use. For this reason, you may want to consider instructing users to create different passwords for different systems, especially on the systems that protect sensitive information. The only downside is that users have to keep multiple passwords and, therefore, may be tempted to write them down, which can negate any benefits.

 ![tip](images/tip.png)Strong passwords are important, but you need to balance security and convenience. You can’t expect users to memorize passwords that are insanely complex and must be changed every few weeks. But you can’t afford weak passwords or no passwords at all. Come up with a strong password policy and accompanying standard — preferably one that requires long, strong passphrases (combinations of words that are easy to remember yet next to impossible to crack) that have to be changed only once or twice a year.

### Storing passwords

If you have to choose between weak passwords that your users can memorize and strong passwords that your users must write down, I recommend having readers write down passwords and store the information securely. Train users to store their written passwords in a secure place — not on keyboards or in easily cracked password-protected computer files (such as spreadsheets). Users should store a written password in any of these locations:
