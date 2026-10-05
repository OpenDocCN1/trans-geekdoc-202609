but it may not be preventable. Active attacks may take the form of one of four types (or combination thereof): masquerading, replay, message modification, denial-of-service (DoS). These attacks are defined below.

+   - Masquerading: The attacker impersonates an authorized user and gains certain unauthorized privileges.

+   - Replay: The attacker monitors transmissions (passive attack) and retransmits messages as the legitimate user.

+   - Message modification: The attacker alters a legitimate message by deleting, adding to, changing, or reordering it.

+   - Denial-of-service: The attacker prevents or prohibits the normal use or management of communications facilities.

The risks associated with 802.11 are the result of one or more of these attacks. The consequences of these attacks are, but not limited to, loss of proprietary information, legal and recovery costs, tarnished image, and loss of network service.

# Loss of Confidentiality

Confidentiality is the property with which information is not made or disclosed to unauthorized individuals, entities, or processes. This is, in general, a fundamental security requirement for most organizations. Due to the broadcast and radio nature of wireless technology, confidentiality is a more difficult security requirement to meet in a wireless network. Adversaries do not have to tap into a network cable to access network resources. Moreover, it may not be possible to control the distance over which the transmission occurs. This makes traditional physical security countermeasures less effective.

Passive eavesdropping of native 802.11 wireless communications may cause significant risk to an organization. An adversary may be able to listen in and obtain sensitive information including proprietary information, network IDs and passwords, and configuration data. This risk is present because the 802.11 signals travel outside the building perimeter or there may be an “insider.” Because of the extended range of 802.11 broadcasts, adversaries can potentially detect transmission from a parking lot or nearby roads. Through the use of a wireless network analyzer tool or sniffer, is particularly easy for two reasons: 1) frequently authentication features of WLAN technology are not even enabled, and 2) because of the numerous vulnerabilities in the 802.11 technology security.

Wireless packet analyzers, such as AirSort and WEPrack, are tools that are readily available on the Internet today. AirSort is one of the first created to automate the process of analyzing networks. Unfortunately, it is also used for breaking into wireless networks. AirSort can take advantage of flaws in the key-scheduling algorithm that was provided for implementation of RC4, which forms part of the original WEP standard. To accomplish this, AirSort requires any computer running the Linux operating system and a wireless network card. The software passively monitors the WLAN data transmissions and computes the encryption keys

![](bbox=[0.91, 0.105, 0.99, 0.285])