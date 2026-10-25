
database of approved users or in a data authentication server [25]. With the use of these new IoT devices, authentication should be taken seriously. Never create a product with a default password that is the same across all devices.

- ii. **Backdoor debug:** An undocumented way to get access to a computer system or the data it contains [26]. Backdoors can be installed by software or hardware makers as a deliberate means of gaining access to their technology after providing them to the customers for removing errors or bugs. Manufacturers should never leave any kind of debugging access in production devices, even if you need to leave access on a non-standard port using hard-coded random passwords.

- iii. **Encryption:** Encryption is a formula used to turn data into a secret code [27]. Encryption means converting simple data into encrypted data or that can be called cipher text or coded data from simple data. All IoT devices that are communicating to cloud or other devices sharing data that all should be encrypted and available to only people that are meant to be seeing that information.

- iv. **Privacy:** Privacy means anyone's right to control access to their personal information. In IoT devices, everyone must ensure that no personal data, such as a device's location, owner information, connection information, etc., is available to any other person or device, otherwise hackers may gain access to the device, and privacy would not be available to the device owner.

- v. **Web interface:** If the web interface is there, it should be a robust one, not the open one like SQL injection and cross-site scripting.

- vi. **Firmware updates:** Bugs regarding security and privacy may arise at any point. Every IoT device must be able to be updated via over the air (OTA) updates. However, those updates need to be verified before being applied. The update must be signed, and the device should check the signature, and only then may it proceed to install the update.

## 9.8 PREVIOUS ATTACKS

- i. **Robot vacuum cleaner** - These are the IoT devices that are used to vacuum a house floor. These devices operate on the house floor vacuuming and when it detects any obstruction in its path it changes direction and stores the created map for further usage as shown in Figure 9.7. The issue found with these devices was that it has produced a map of the house, and that device has a default username and password that was not changed by the manufacturer. The remote code vulnerability is named CVE-2018-10987 [28] and if compromised will provide access hackers who get the device's MAC address system admin privileges [28]. The impacted vacuum cleaners are vulnerable to an authenticated remote code execution exploit. An authenticated offender will send a specially crafted UDP packet and execute commands on the vacuum as root. The bug is within the function REQUEST_SET_WIFIPASSWD (UDP command 153). An attacker can manipulate the %s variable by sending a specially crafted UDP packet. In some cases, authentication can be achieved with the default password of 888888 for the admin account [29]. Since the vacuum has LAN, a digital camera with night vision, and smartphone-controlled navigation, the attacker can secretly spy on the owner and even use the vacuum as a 'microphone on wheels' for maximum surveillance potential.

![](img/be689ed28322f90f68916a35ce44e55d_206_0.png)

FIGURE 9.7 Map of a house provided by robot vacuum cleaner [31].

- ii. **Electronic Locks** - Electronic locks are same as the simple mechanical locks, but they are controlled electronically. A lock code is set and whenever we want to open the lock, we use the same code to unlock the device and use the safe for accessing our items kept inside. Some locks are only accessible by your mobile device. This condition can be very good or very bad, as it provides security, but what if the phone gets stolen or lost? You, yourself, would not be able to open the lock. Some of these locks could be opened by just using high-powered magnets around them. Another issue with smart locks that use phones to unlock and lock is firmware problems. The firmware update in 2017 caused a malfunction in smart locks produced by LockState that affected more than 500 customers. The company required affected customers to send the lock for repairs [30]. According to the hacker convention DEF CON, around 75% of these locks are not safe and are vulnerable to attacks. These locks are vulnerable for the following reasons:

  - a. **Plain text passwords**: Saving the password the same as the user enters and not in any form of cryptic or hash form. The password stored in a company database should have added data, and that, too, in scrambled form, so that if anyone tries to access that password, it is irreversible and useless for others.

  - b. Device spoofing: A device is used by attackers to act as another device in a network so that that device could be used to target other devices on that network and steal their data and have access to them whenever they want.

  - c. Replay attacks: When two devices are exchanging data, the attacker tries to copy the digital signature so that it could be used as a false communication signal for the device, send malware to that device, and steal its data.

## 9.9 AVAILABLE SOLUTIONS

- i. Identity mixer: Idemix is a cryptographic protocol suite that offers robust authentication and privacy-preserving features. These features include anonymity, allowing transactors to carry out transactions without disclosing their identities, and unlinkability, enabling a single identity to send multiple transactions without revealing that they originated from the same identity [32].

This is a type of cryptic message that only reveals the required information. For example, if person 1 has to prove that he is the authentic user, he can provide a digital certificate to the other user (person 2) that will only provide the necessary information for authentication, and the other information such as physical address and control over the device is not provided.

- ii. Proper authentication: Many of the IoT devices these days do not have proper authentication, and that results in the security breaches. To ensure the security of all the devices, they must have proper authentication. Any user that tries to access the device must fulfill the authentication criteria; it should be checked every time.

- iii. Access control: Our device should have access control so that the device is secure from attacks of other users, and other devices that communicate with our device should have controlled access, otherwise those devices can be a type of weak link in our device's security.

- iv. Encryption: Each and every message that is sent to the device from any user or any other device should be encrypted so that the message is useful only to the user that has the proper decryption key and useless for the other users and attackers. An encrypted message is sent through the internet, and anyone can sense it, but anyone other than the user with the decryption key can use that encrypted message or signal.

- v. No backdoor debugging: The manufacturer must ensure not to keep any sort of backdoor for further debugging that could be a potential access door for an attacker also. Backdoors are generally used by manufacturers so that in case of system failure they can access the user's device and find the reason for system failure. This kind of backdoors are generally used by attackers to hack into any device, and since all devices are connected to internet, they are all affected.

### Identity Mixer Overview

![](img/be689ed28322f90f68916a35ce44e55d_208_0.png)

FIGURE 9.8 Functioning of Identity Mixer [32].

- vi. **Provide support:** Manufacturers should provide firmware updates regularly so that new types of attacks do not affect our devices, and our devices are safeguarded from various attacks (Figure 9.8).

## 9.10 FUTURE SCOPE

The digital transformation forced either to develop a new system or to converge the existing technology to achieve the solution for the existing problems. Initially, AI and IoT emerged as individual concepts to solve problems, but the convergence of these techniques develops an intelligent system that is able to provide better solutions than the individual one.

- 1. To develop a new intelligent vehicle that communicates with another vehicle and with drivers using wireless technology to ensure a jam-free journey with an enjoyable and safe driving experience [33].
- 2. To develop reliable, efficient, and user-friendly system.
- 3. To develop security architecture that considers the life cycle and the capability of AI and IoT systems. It includes development of new security protocols that traditional end-to-end internet protocols are not able to provide. System should have scalability potential so that it can serve both small- and large-scale needs [5].
- 4. To develop an AIoT framework that supports global needs.
- 5. Convergence of AI, IoT, and WT offers new business opportunities and new approaches for researchers to analyze the data that traditional techniques lack.
- 6. To develop 3D models of CPS systems that perform accurately in hazardous environment without human intervention.
