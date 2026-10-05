# Chapter 12 • Wireless Standards

Three operational modes for wireless networks are defined in the 802.11 standards.

**Basic Service Set (BSS)** Also known as infrastructure mode, a group of wireless devices using the same type of modulation, frequency band, and security protocol, connected to a single access point. All wireless communication goes through the WAP, whether to connect to other wireless devices or to a bridged Ethernet network.

**Extended Service Set (ESS)** A collection of two or more BSSs that function together as a single network serving a common pool of wireless devices. All of the WAPs use the same SSID, and devices can roam from one WAP to another without having to reconnect. While not required, ESS use a wireless LAN controller (WLC) to authenticate, coordinate roaming among WAPs, and prevent channel interference.

**Independent Basic Service Set (IBSS)** Also known as ad hoc mode, a point-to-point link between two wireless devices connected directly to each other without an intervening access point.

# Encryption Standards

To prevent unauthorized users from using a wireless LAN, the devices use a security protocol that protects the traffic between the clients and the WAP. As is typical with security protocols, they evolve over time as attackers develop exploits for the existing security.

# WPA

The first protocol developed for Wi-Fi, called Wired Equivalent Privacy (WEP), was found to be vulnerable and inadequate. To replace WEP, the Wi-Fi Alliance developed Wi-Fi Protected Access (WPA) in 2003. WPA uses 256-bit encryption keys, rather than the smaller keys that contributed to the vulnerability of WEP. WPA also introduced the Temporal Key Integrity Protocol (TKIP), which uses the same underlying cipher as WEP (called RC4) but adds a message integrity check (MIC) and other security features, in addition to the larger keys.

# WPA2

The similarities between WEP and WPA are deliberate so that existing devices with WEP could be upgraded to WPA with just a firmware update. However, the initial version of WPA was also found to be exploitable and was deprecated in 2006 in favor of Wi-Fi Protected Access 2 (WPA2), also known as 802.11i, which is the wireless encryption protocol used in common today.

WPA2 continues to support TKIP for backward compatibility purposes, but the WPA standards require that implementations include more advanced algorithms, including Counter Mode with Cipher Block Chaining Message Authentication Code Protocol (CCMP) for integrity checking, which is part of the Advanced Encryption Standard (AES) that WPA2 uses for data encryption. This combination is sometimes noted as CCMP-AES.