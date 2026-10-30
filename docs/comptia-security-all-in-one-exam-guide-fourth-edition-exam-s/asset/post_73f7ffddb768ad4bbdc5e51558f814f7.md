
10. An organization wanting to create a restricted-access, Internet-accessible resource for processing sensitive data might consider using:

- A. Software as a Service
- B. A private cloud
- C. A public cloud
- D. A community cloud

11. Your organization is setting up three new buildings on a local campus, all connecting to the same core router. You have only one available address space, 10.10.10.0, to handle the routing between those three new buildings. What subnet mask will you need to use to create separate subnets for each of those three buildings?

- A. 255.255.255.128
- B. 255.255.255.192
- C. 255.255.255.240
- D. 255.255.255.252

12. Your organization is considering migrating from QuickBooks 2009 to QuickBooks Online (a web-based solution). QuickBooks Online is an example of:

- A. PaaS
- B. SaaS
- C. IaaS
- D. QaaS

13. You need to set up a DMZ but want to keep the servers inside the DMZ on a private address space. You have plenty of public IP address space and just want to map each server's private address to a unique public address. What type of NAT would be most appropriate?

- A. Static NAT
- B. Full-cone NAT
- C. Port Address Translation
- D. Dynamic NAT

7. B. In virtualization, a snapshot is the state of a virtual machine at an exact point in time. The snapshot typically includes the state of a virtual machine’s storage devices as well.

8. A. Application delivery–only Platform as a Service (PaaS) offerings generally focus on security and scalability.

9. D. A company adopting an Infrastructure as a Service (IaaS) model would typically pay on a per-use basis. IaaS is a provision model where an organization outsources the equipment used by its operations as well as the housing, maintenance, and operation of that equipment.

10. B. An organization wanting to create a restricted-access, Internet-accessible resource for processing sensitive data might consider using a private cloud.

11. B. To create at least three subnetworks from the 10.10.10.0 address space, you will need to use a 255.255.255.192 subnet mask. This will give you four separate networks with 62 host addresses each.

12. B. QuickBooks Online is an example of a Software as a Service (SaaS) model. The software is accessed via a web browser and can be used by any computer with an Internet connection and a compatible browser.

13. A. Static NAT, often called one-to-one NAT, maps a single private address to a single public address.

14. B. The others in your meeting are arguing for defense in depth (or layered defense), which uses multiple security layers to provide more resistance to potential attacks. Attackers must successfully penetrate multiple layers of defenses before they can penetrate the network.

15. C. A community cloud shares the resources between several different organizations, but still reserves those resources for use by those organizations (that is, they are not public resources).

## SSID

The 802.11 protocol designers expected some security concerns and attempted to build provisions into the 802.11 protocol that would ensure adequate security. The 802.11 standard includes attempts at rudimentary authentication and confidentiality controls. Authentication is handled in its most basic form by the 802.11 access point (AP), forcing the clients to perform a handshake when attempting to “associate” to the AP. Association is the process required before the AP will allow the client to talk across the AP to the network.

The authentication function is known as the service set identifier (SSID). This unique 32-character identifier is attached to the header of the packet. Association occurs only if the client has all the correct parameters needed in the handshake, among them the SSID. This SSID setting should limit access to only authorized users of the wireless network. The SSID is broadcast by default as a network name, but broadcasting this beacon frame can be disabled. Many APs also use a default SSID; for example, for many versions of Cisco APs, this default is tsunami, which can indicate an AP that has not been configured for any security. Renaming the SSID and disabling SSID broadcast are both good ideas; however, because the SSID is part of every frame, these measures should not be considered securing the network. As the SSID is, hopefully, a unique identifier, only people who know the identifier will be able to complete association to the AP.

While the SSID is a good idea in theory, it is sent in plaintext in the packets, so in practice, SSID offers little security significance—any sniffer can determine the SSID, and many operating systems—Windows XP and later, for instance—will display a list of SSIDs active in the area and prompt the user to choose which one to connect to. This weakness is magnified by most APs’ default settings to transmit beacon frames. The beacon frame’s purpose is to announce the wireless network’s presence and capabilities so that WLAN cards can attempt to associate to it. This can be disabled in software for many APs, especially the more sophisticated ones. From a security perspective, the beacon frame is damaging because it contains the SSID, and this beacon frame is transmitted at a set interval (ten times per second by default). Since a default AP without any other traffic is sending out its SSID in plaintext ten times a second, you can see why the SSID does not provide true authentication. Scanning programs such as NetStumbler work by capturing the beacon frames, and thereby the SSIDs, of all APs.

![](img/922567202a944c5e8d3ba0168d2ad3a5_107_0.png)

**EXAM TIP** Although not considered the strongest security measures, renaming the SSID and disabling SSID broadcast are important concepts to know for the exam.

## WEP

The designers of the 802.11 protocol also attempted to maintain confidentiality by introducing Wired Equivalent Privacy (WEP), which uses a cipher to encrypt the data as it is transmitted through the air. WEP has been shown to have an implementation problem that can be exploited to break security. WEP encrypts the data traveling across the network with an RC4 stream cipher, attempting to ensure confidentiality. (The details of the RC4 cipher are covered in Chapter 24.) This synchronous method of encryption ensures some method of authentication. The system depends on the client and the AP having a shared secret key, ensuring that only authorized people with the proper key have access to the wireless network. WEP supports two key lengths, 40 and 104 bits, though these are more typically referred to as 64 and 128 bits. In 802.11a and 802.11g, manufacturers extended this to 152-bit WEP keys. This is because in all cases, 24 bits of the overall key length are used for the initialization vector (IV).

The IV is the primary reason for the weaknesses in WEP. The IV is sent in the plaintext part of the message, and because the total keyspace is approximately 16 million keys, the same key will be reused. Once the key has been repeated, an attacker has two ciphertexts encrypted with the same key stream. This allows the attacker to examine the ciphertext and retrieve the key. This attack can be improved by examining only packets that have weak IVs, reducing the number of packets needed to crack the key. Using only weak IV packets, the number of required captured packets is reduced to around four or five million, which can take only a few hours on a fairly busy AP. For a point of reference, this means that equipment with an advertised WEP key of 128 bits can be cracked in less than a day, whereas to crack a normal 128-bit key would take roughly 2,000,000,000,000,000 years on a computer able to attempt one trillion keys a second. AirSnort is a modified sniffing program that can take advantage of this weakness to retrieve the WEP keys.

The biggest weakness of WEP is that the IV problem exists, regardless of key length, because the IV always remains at 24 bits. Most APs also have the ability to lock in access only to known MAC addresses, providing a limited authentication capability. Given sniffers’ capacity to grab all active MAC addresses on the network, this capability is not very effective. An attacker simply configures his wireless cards to a known good MAC address.

![](img/922567202a944c5e8d3ba0168d2ad3a5_108_0.png)

> **EXAM TIP** WEP alone should not be trusted to provide confidentiality. If WEP is the only protocol supported by your AP, place it outside the corporate firewall and VPN to add more protection.

## WPA

The first standard to be used in the market to replace WEP was Wi-Fi Protected Access (WPA). This standard uses the flawed WEP algorithm with the Temporal Key Integrity Protocol (TKIP). TKIP works by using a shared secret combined with the card’s MAC address to generate a new key, which is mixed with the IV to make per-packet keys that encrypt a single packet using the same RC4 cipher used by traditional WEP. This overcomes the WEP key weakness, as a key is used on only one packet. The other advantage to this method is that it can be retrofitted to current hardware with only a software change, unlike Advanced Encryption Standard (AES) and 802.1x.

While WEP uses a 40-bit or 104-bit encryption key that must be manually entered on wireless access points and devices and does not change, TKIP employs a per-packet key, generating a new 128-bit key for each packet. This can generally be accomplished with only a firmware update, enabling a simple solution to the types of attacks that compromise WEP.
