scrambled form, so that if anyone tries to access that password, it is irreversible and useless for others.

+   b. Device spoofing: A device is used by attackers to act as another device in a network so that that device could be used to target other devices on that network and steal their data and have access to them whenever they want.

+   c. Replay attacks: When two devices are exchanging data, the attacker tries to copy the digital signature so that it could be used as a false communication signal for the device, send malware to that device, and steal its data.

# 9.9 AVAILABLE SOLUTIONS

+   i. Identity mixer: Idemix is a cryptographic protocol suite that offers robust authentication and privacy-preserving features. These features include anonymity, allowing transactors to carry out transactions without disclosing their identities, and unlinkability, enabling a single identity to send multiple transactions without revealing that they originated from the same identity [32].

This is a type of cryptic message that only reveals the required information. For example, if person 1 has to prove that he is the authentic user, he can provide a digital certificate to the other user (person 2) that will only provide the necessary information for authentication, and the other information such as physical address and control over the device is not provided.

+   ii. Proper authentication: Many of the IoT devices these days do not have proper authentication, and that results in the security breaches. To ensure the security of all the devices, they must have proper authentication. Any user that tries to access the device must fulfill the authentication criteria; it should be checked every time.

+   iii. Access control: Our device should have access control so that the device is secure from attacks of other users, and other devices that communicate with our device should have controlled access, otherwise those devices can be a type of weak string in our device's security.

+   iv. Encryption: Each and every message that is sent to the device from any user or any other device should be encrypted so that the message is useful only to the user that has the proper decryption key and useless for the other users and attackers. An encrypted message is sent through the internet, and anyone can sense it, but anyone other than the user with the decryption key can use that encrypted message or signal.

+   v. No backdoor debugging: The manufacturer must ensure not to keep any sort of backdoor for further debugging that could be a potential access door for an attacker also. Backdoors are generally used by manufacturers so that in case of system failure they can access the user's device and find the reason for system failure. This kind of backdoors are generally used by attackers to hack into any device, and since all devices are connected to internet, they are all affected.