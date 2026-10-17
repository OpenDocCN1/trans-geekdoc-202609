
**204.** B. A Trusted Platform Module, or TPM, is used as the foundation for a hardware root of trust for modern PCs. The TPM may provide a cryptographic key; a PUF, or physically unclonable function; or a serial number that is unique to the device. The CPU and hard drive are not used for this function, and HSMs, or hardware security modules, are used for public key infrastructure (PKI) and cryptographic purposes but not as a hardware root of trust for PCs.

**205.** C. Next-generation firewalls typically build in advanced capabilities like URL filtering, blacklisting, and other application-layer capabilities beyond simple packet filtering or stateful packet inspection.

**206.** D. Mobile application management (MAM) tools are specifically designed for this purpose, and they allow applications to be delivered to, removed from, and managed on mobile devices. MOM is the Microsoft Operations Manager, a systems management tool that Microsoft has replaced with Operations Manager in current use. MLM often means multi-level marketing, or pyramid schemes—not a security term. MIM is not a security term.

**207.** A. Cloud applications have many of the same concerns as on-premises applications, but compromise of the system running the application due to local access is a far less likely scenario. Cloud application vendors are more likely to operate in secure datacenters with limited or no access to the servers except for authorized personnel, greatly reducing the likelihood of this type of security issue.

**208.** D. The most critical part of a certificate authority (CA) is its root certificate, and ensuring that the root certificate is never exposed is critical to the ongoing operation of that CA. Thus, root CAs are often maintained as offline CAs, making it far harder for an attacker to compromise the system and gain access to the root certificate. In practice, compromised CAs may lose the trust of organizations around the world and be unable to continue to do business.

**209.** C. Split-tunnel VPNs send only traffic destined for the remote network over the VPN, with all other traffic split away to use the VPN system or a user’s primary network connection. This reduces overall traffic sent through the VPN but means that traffic cannot be monitored and secured via the VPN. Half-pipe is not a security term, and split horizon is most often used to describe DNS where an internal and external DNS view may be different.

**210.** A. Loop protection looks for exactly this type of issue. Loop protection sends packets that include a PDU, or protocol data unit. These are detected by other network devices and allow the network devices to shut down ports from which they receive those packets. The remaining options were made up for this question.

**211.** C. Over-the-air (OTA) updates are used by cellular carriers as well as phone manufacturers to provide firmware updates and updated phone configuration data. Mobile device management (MDM) tools can be used to monitor for the current firmware version and phone settings and will allow Charles to determine if the phones that his staff use are updated to ensure security. A network access control (NAC) agent might capture some of this data but only for network-connected phones, which will not cover off-site phones, those with Wi-Fi turned off, or remote devices. OTA is not specifically a way to update encryption keys, although firmware or settings might include them. OTA is not sent by the phones themselves.

**212.** C. Open source firewalls typically do not have the same level of vendor support and maintenance that commercial firewalls do. That means you don’t have a vendor to turn to if something goes wrong, and you will be reliant on a support community for patches and updates. Open source firewalls are typically less expensive, their open source nature means that the code can be validated by anybody who cares to examine it, and it can be acquired as quickly as it can be downloaded.

**213.** C. WPA3 personal replaced PSK, or preshared keys, with SAE, or simultaneous authentication of equals. SAE helps to prevent brute-force attacks against keys by making attackers interact with the network before each authentication attempt. This slows down brute-force attacks. WPA3 also includes a 192-bit encryption mode. It does not replace 64-bit encryption with 128-bit encryption, add per-channel security, or add distributed denial-of-service (DDoS) monitoring and prevention.

**214.** B. Security Enhanced Linux (SELinux) allows mandatory access control for Linux-based systems, and SEAndroid is an Android implementation of SELinux. That means that Isaac can use SEAndroid to accomplish his goals. Android does use a registry, but there is no MAC mode. MACDroid was made up for this question, and single-user mode does not make Android a MAC-based system.

**215.** B. The system described is a privileged access management (PAM) system. PAM systems are used to manage and control privileged accounts securely. MAC is an access control scheme that enforces access at the OS level. FDE is full-disk encryption, and TLS is Transport Layer Security.

**216.** A. Using a mobile device management (MDM) tool that allows control of the devices would allow Amina to lock out the cameras, preventing staff members from using the Android tablets to take pictures. She would still need to ensure that her staff did not bring their own camera equipped devices into the facility. DLP is data loss prevention, OPAL is an encryption standard for drives, and MMC has a number of meanings, including multimedia cards and Microsoft Management Console snap-ins for Windows systems, none of which would provide the control she needs.

**217.** C. A universal endpoint management (UEM) tool can manage desktops, laptops, mobile devices, printers, and other devices. UEM tools often use applications deployed to mobile devices to configure and manage them, and Olivia’s best option from this list is a UEM tool. A CASB is a cloud access security broker and is not used to manage mobile devices, and the other options require massive amounts of manual work and are unlikely to succeed—or users will simply change settings when it is convenient to them.

**218.** C. Next-generation (NG) secure web gateways (SWG) add additional features beyond those found in cloud access security brokers and next generation firewalls. While features can vary, they may include web filtering, TLS decryption to allow traffic analysis and advanced threat protection, cloud access security broker (CASB) features, data loss prevention (DLP), and other advanced capabilities. This type of solution is a relatively new one, and the market is changing quickly.

**219.** C. Access policies are built using information and attributes about access requests. If the policy requirements are met, the actions like allowing or denying access, or requiring additional authentication steps can be performed. Geolocation and time-based logins focus on a single information component, and account auditing is used to review permissions for accounts, not to perform this type of validation or policy-based control.

220. B. Numeric representations of file permissions are commonly used instead of using rwx notation with chmod. A 7 sets full permissions, and the first number sets the user’s rights, meaning that here the user will be granted full access to the file.

221. B. Certificate pinning associates a known certificate with a host and then compares that known certificate with the certificate that is presented. This can help prevent man-in-the-middle attacks but can fail if the certificate is updated and the pinned certificate isn’t. A CRL, or certificate revocation list, would show whether the certificate has been revoked, but it would not show if it was changed. Patrick will not have access to the remote server’s private key unless he happens to be the administrator.

222. C. Privacy Enhanced Mail (PEM) is the most common format issued by certificate authorities. Distinguished Encoding Rules (DER) format is a binary form of the ASCII text PEM format. PKCS#7 or P7B format is Base64 ASCII, and PKCS#12, or PFX, format is binary format used to store server certificates, intermediate certificates, and private keys in a single file.

223. C. Michelle’s only option is to remove the certificate from the list of trusted certificates on every machine that trusted it. This can be time-consuming and error prone, and it’s one reason self-signed certificates are avoided in production at many organizations.

224. D. Changing the IP addresses associated with a domain to an arbitrary value could cause routing or other problems. That means that changing the IP address would not be a chosen method of validating a domain. The remaining options are legitimate and normal means of validation for certificates.

225. A. SNMPv3 adds the ability to authenticate users and groups and then encrypt messages, providing message integrity and confidentiality. It does not have SQL injection prevention built in, but it also isn’t a protocol where SQL injection will typically be a concern.

226. A. This diagram shows a reverse proxy. A reverse proxy takes connections from the outside world and sends them to an internal server. A forward proxy takes internal connections and sends them to external servers. Round-robin and next-generation proxies are not types of proxies, although round-robin is a form of load balancing.

## Chapter 4: Operations and Incident Response

1. A. Mila should select a hash because a hash is designed to be unique to each possible input. That means that multiple files could have the same checksum value, whereas a hashing algorithm will be unique for each file that it is run against.

2. A. Allow lists are lists of approved software. Software can only be installed if it is on an allow list. Deny lists block specific applications, but they cannot account for every possible
