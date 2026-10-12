
Each of these design models is simple to understand. A point-to-point network connects two nodes, and transmissions between them can only be received by the endpoints. Point-to-multipoint networks like `Wi-Fi` have many nodes receiving the information sent by a node. Broadcast designs send out information on many nodes and typically do not care about receiving a response. `GPS` and radio are both examples of broadcast models.

## Attacks Against Wireless Networks

One of the first things you need to consider when designing a secure network is how it could be attacked. Attackers may pose as legitimate wireless networks, add their own wireless devices to your network, interfere with the network, use protocol flaws or attacks, or take other steps to attack your network.

### Rogue Access Points and Evil Twins

The Security+ exam considers a few of the many ways that networks can be attacked. The first of these attacks that you need to know about is the `evil twin` attack. An evil twin is a malicious fake access point that is set up to appear to be a legitimate, trusted network. [Figure 13.2](#c13.xhtml#c13-fig-0002) shows an evil twin attack where the client wireless device has opted for the evil twin access point (AP) instead of the legitimate access point. The attacker may have used a more powerful AP, placed the evil twin closer to the target, or used another technique to make the AP more likely to be the one the target will associate with.

![FIGURE 13.2 Evil twin pretending to be a legitimate access point](images/c13f002.png)

[**FIGURE 13.2**](#c13.xhtml#R_c13-fig-0002) Evil twin pretending to be a legitimate access point

Once a client connects to the evil twin, the attacker will typically provide Internet connectivity so that the victim does not realize that something has gone wrong. The attacker will then capture all of the victim's network traffic and look for sensitive data, passwords, or other information that they can use. Presenting false versions of websites, particularly login screens, can provide attackers who have successfully implemented an evil twin with a quick way to capture credentials.

Evil twins aren't the only type of undesirable access point that you may find on your network. `Rogue access points` are APs added to your network either intentionally or unintentionally. Once they are connected to your network, they can offer a point of entry to attackers or other unwanted users. Since many devices have built-in wireless connectivity and may show up as an accessible network, it is important to monitor your network and facilities for rogue access points.

Most modern enterprise wireless controller systems have built-in functionality that allows them to detect new access points in areas where they are deployed. In addition, wireless intrusion detection systems or features can continuously scan for unknown access points and then determine if they are connected to your network by combining wireless network testing with wired network logs and traffic information. This helps separate out devices like mobile phones set up as hotspots and devices that may advertise a setup Wi-Fi network from devices that are plugged into your network and that may thus create a real threat.

### Bluetooth Attacks

You need to be familiar with two types of Bluetooth attacks for the Security+ exam: `bluejacking` and `bluesnarfing`. Bluejacking simply sends unsolicited messages to Bluetooth-enabled devices. Bluesnarfing is unauthorized access to a Bluetooth device, typically aimed at gathering information like contact lists or other details the device contains. Unfortunately, there aren't many security steps that can be put in place for most Bluetooth devices.

Many simply require pairing using an easily guessed code (often `0000`), and then proceed to establish a long-term key that is used to secure their communications. Unfortunately, that long-term key is used to generate session keys when combined with other public factors, thus making attacks against them possible.

Despite years of use of Bluetooth in everything from mobile devices to medical devices, wearables, and cars, the security model for Bluetooth has not significantly improved. Therefore, your best option to secure Bluetooth devices is to turn off Bluetooth if it is not absolutely needed and to leave it off except when in use. In addition, if devices allow a pairing code to be set, change it from the default pairing code and install all patches for Bluetooth devices. Unfortunately, this will leave many vulnerable devices, particularly those that are embedded or no longer supported by the software or hardware manufacturer.

### RF and Protocol Attacks

Attackers who want to conduct evil twin attacks, or who want systems to disconnect from a wireless network for any reason, have two primary options to help with that goal: disassociation attacks and jamming.

`Disassociation` describes what happens when a device disconnects from an access point. Many wireless attacks work better if the target system can be forced to disassociate from the access point that it is using when the attack starts. That will cause the system to attempt to reconnect, providing an attacker with a window of opportunity to set up a more powerful evil twin or to capture information as the system tries to reconnect.

The best way for attackers to force a system to disassociate is typically to send a de-authentication frame, a specific wireless protocol element that can be sent to the access point by spoofing the victim's wireless MAC address. When the AP receives it, it will disassociate the device, requiring it to then reconnect to continue. Since management frames for networks that are using `WPA2` are often not encrypted, this type of attack is relatively easy to conduct. `WPA3`, however, requires protected management frames and will prevent this type of deauthentication attack from working.

Another means of attacking radio frequency networks like `Wi-Fi` and Bluetooth is to jam them. `Jamming` will block all the traffic in the range or frequency it is conducted against. Since jamming is essentially wireless interference, jamming may not always be intentional—in fact, running into devices that are sending out signals in the same frequency range as Wi-Fi devices isn't uncommon.

A final type of attack against Wi-Fi networks is an `initialization vector (IV)` attack. The original implementation of wireless security was `WEP` (Wired Equivalent Privacy). WEP used a 24-bit initialization vector, which could be reverse-engineered once enough traffic from a network was captured. After the traffic was analyzed, the initialization vector used to generate an `RC4` key stream could be derived, and all traffic sent on the network could be decrypted. Fortunately, IV attacks are no longer a concern for modern networks. Both `WPA2` and `WPA3` do not use weak initialization vectors like this, making the IV attack historical knowledge.

## Designing a Network

Designing your Wi-Fi network for usability, performance, and security requires careful wireless access point (WAP) placement as well as configuration. Tuning and placement are critical, because wireless access points have a limited number of channels to operate within, and multiple wireless access points using the same channel within range of each other can decrease the performance and overall usability of the network. At the same time, organizations typically don't want to extend signal to places where they don't intend their network to reach. That means your design may need to include AP placement options that limit how far wireless signal extends beyond your buildings or corporate premises.
