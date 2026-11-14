
# VPN Technologies

## SSL/TLS

(Secure Sockets Layer) and (Transport Layer Security) SSL/TLS are the most common choice for remote access VPNs that create a secure channel by exchanging certificates and encrypting application data.

## IPsec

(IP Security) IPsec is the most widely used choice for site-to-site VPNs. It is not a real protocol as much as a flexible architecture that uses different protocols and algorithms. What it ciphers depends on the mode: transport mode ciphers only the data contained in the IP packet while in tunnel mode it ciphers the whole IP packet adding another header with different addresses. IPsec uses two main components: ESP or AH. ESP encrypts the data while AH is a protocol that creates the header added to the packet (it contains the hash of the packet and the encryption key) guaranteeing the integrity of the data.

# Physical Security

The first concern for physical security is to prevent an attacker from having physical access to computer devices. Physical barriers are the first level of security and a possible implementation is the three-layered one: perimeter entrance, building access, computer room access. The perimeter must be protected by a fence, mobile barriers and bollards, alarms, guards and video surveillance. The building must be protected by locks that can be opened with keys or even with proximity cards. Server rooms can have advanced control systems such as motion detectors, biometric recognition and mantrap. A mantrap is an intermediate room closed by two doors controlled by an authentication system or manually operated by a guard. Control systems should be commensurate with the value of resources. Physical security must stop social engineering attacks such as impersonation, tailgating and shoulder surfing. Computer rooms must meet appropriate requirements. They must therefore be kept in check:

## A) Air Quality

The hardware equipment requires special temperature and humidity values guaranteed by air conditioning systems; dusty or too humid environments can spoil systems and all circuits. In data centers, servers are often organized on long rows of shelves called racks. Considering that the servers expel hot air from behind and suck in fresh air from the front to optimize cooling, they can be arranged in hot and cold aisles. Arranging the servers so that they all expel hot air from the same side prevents some servers from sucking in hot air from others.

## B) Power Supply

In the electrical supply you need a surge absorber that absorbs current peaks, an uninterruptible power supply that supplies the devices in the event of a blackout and a generator that generates energy for the entire building through a thermal motor. Generators do not replace uninterruptible power supplies as they take a certain amount of time to become operational.

## C) Lighting

A poorly designed lighting system worsens physical security as it increases the possibility of intrusion, physical assault (robbery) and accidents. Poor lighting can also render video surveillance ineffective.

## D) Electromagnetic Emissions

Electromagnetic shielding limits the radiation emitted, which is risky for privacy and those received from outside that represent a disturbance. Usually the shielding is a braiding of metal wires that captures the emissions and discharges them to the ground (Faraday cage). The most important process of emission control concerns the limitation of the Wi-Fi signal.

## E) Fire-fighting Systems

Infrared detectors work just like motion detectors. Infrared detectors work by detecting changes in infrared radiation, traditionally thermal heat. Once the normal parameters have changed and the set threshold limit has been exceeded, changes are detected and an alarm or warning can be triggered, taking into account the established protocols that are in place. In the event of a fire, each room must be equipped with fire extinguishers appropriate to its contents.

For PCs, category C fire extinguishers are recommended. There are fire extinguishing systems that can be integrated into the building by detectors that are sensitive to a sharp rise in temperature or smoke and can operate on water or gas. Water-based systems are the cheapest but can damage the hardware. The gas ones (such as carbon dioxide) are the most expensive and are reserved for rooms with servers or important documents; the gas ones introduce gas into the environment by removing oxygen to suppress the fire. FM-200 systems are among the most widespread because they use a gas that is not harmful and takes effect in just 10 seconds.

## F) Natural Hazards

Environmental safety is primarily aimed at increasing the availability of systems. Depending on the territory, the site may be at risk of flooding or earthquakes. Vibrations should not be underestimated because in the long run they cause the disconnection of cables and components or worse, the breaking of pipes with consequent water leaks. It is also necessary to take care to protect the cables from malicious attack and wear by using corrugated cables (plastic or flexible rubber hose).

## Evacuation Plans and Legal Compliance

By law, an evacuation plan must be created which defines how to behave in the event of a disaster. The plan must indicate the evacuation procedures, emergency exits and the frequency with which drills are to be carried out. Safety in the workplace is regulated by the Consolidated Law on Safety at Work (TUSL).

# Practical Examples of Pentesting and Vulnerability Analysis

Pentesting is a very dangerous practice and must be agreed by contract with the company that requires it before being carried out. The main difference between pentesting and vulnerability analysis lies in the fact that the first analysis is a real attack that puts at risk data and security of the company while the second analysis analyzes the main vulnerabilities in a non-invasive way. Obviously there are many tools to perform analysis and attacks and in this module will be presented the main tools used for both pentesting and vulnerability analysis. For this type of examples will be used the operating systems Kali Linux (attacker) or Parrot, downloadable for free, and a Windows system (victim) installed on a virtual machine (VirtualBox). Next we will describe how to download Metasploitable which is a system designed to be attacked and therefore to better practice penetration testing and vulnerability analysis. The attacks presented in the example are for educational purposes, have been carried out in a personal testing environment and also run under the same network. It must be remembered that attacking or testing without the consent of the victim is a crime.

## Installation of Operating Systems

As for the installation of Kali Linux and Parrot, to simplify the installation just download the files directly for VirtualBox. The following figure shows how to download Parrot. Go to the manufacturer's website and click on Download in the security section. Then you will need to download the VirtualBox format directly, there will be an entry "for virtual machine" and just click on "Download". Once the download is complete, simply double-click on the file you have just downloaded and the configuration will start automatically. In case of boot problems you will need to set the network to `card with bridge`.

## Metasploitable

The Metasploitable virtual machine allows you to test attacks in a very simple way since it was designed and created specifically to be attacked. In fact, this system will have numerous weak points that can be used to perform pentesting operations. You have to download the Metasploitable file with the extension `.vmdk`. When the download is complete, open VirtualBox and click on `New`.

The following screen will open where you have to set the values as in the picture.

At the end of this phase, clicking `Next`, you will have to set the amount of memory. The default setting is fine so you can continue clicking on `Next`.
