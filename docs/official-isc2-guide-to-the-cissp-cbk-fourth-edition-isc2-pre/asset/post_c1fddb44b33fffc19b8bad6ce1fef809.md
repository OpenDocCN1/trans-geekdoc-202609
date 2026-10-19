
The SOA provides for modularity, flexibility, and reusability. Moreover, it allows for consistent and collaborative governance, security, and management, including policy enforcement, authentication, encryption, and digital signature implementations, with the caveat that the security is designed and implemented correctly. The availability of middleware interfaces, however, can make them common targets for attack as many of the SOAs were not developed with end-to-end security as a requirement.

## Embedded Systems

Embedded systems are used to provide computing services in a small form factor with limited processing power. They embed the necessary hardware, firmware, and software into a single platform that can be used to provide a limited range of computing services, usually around a single application. They typically feature a limited OS with the base minimum functionality required to meet its functional requirements. Other constrained devices such as mobile phones, media players, and networking devices such as routers and wireless devices take a similar approach.

From the security architect perspective, embedded systems have a number of potential advantages and disadvantages. Security services tend to be simple, testable, and verifiable, making the task of ensuring that security has been designed and implemented correctly much simpler. Unfortunately, security in such systems is typically limited to a few basic security features to help protect memory and privileged access to memory. While they may be able to support a wide range of security services, they have very limited processing power that must be shared by the core functions and security components. This frequently results in less-than-robust security features, particularly when richer functionality is the primary business driver. It is also frequently more difficult to patch security vulnerabilities in constrained embedded devices.44 This is why the security architect needs to consider where security needs to be placed and how it needs to be addressed BOTH inside and outside of the embedded system, as well as how much trust can be placed in the integrity of the embedded system from an architecture standpoint.

## Pervasive Computing and Mobile Devices

The number of mobile devices has grown considerably in the past four or five years. Products vary from sophisticated mobile phones, such as fourth-generation (4G) handsets, to full-featured "ultrabooks" and tablets.

These devices can now manage personal information, such as contacts, appointments, and to-do lists. Current tablets and cell phones connect to the Internet, function as global positioning system (GPS) devices, and run multimedia software. They can also support a wireless Bluetooth network and wireless wide area networks (WANs). They have memory card slots that accept flash media that can serve as additional storage for files and applications. Most all devices provide audio and video support, incorporating MP3 players, a microphone, a speaker, and headphone jacks along with a built-in digital camera. Integrated security features such as a biometric fingerprint reader can also be included.

These devices share common security concerns with other resource-constrained devices. In many cases, security services have been sacrificed to provide richer user interaction when processing power is very limited. Their mobility has made them a prime vector for data loss because they can be used to transmit and store information in ways that may be difficult to control. As a result, the security architect needs to be able to address a long list of threats and vulnerabilities across a wide array of device platforms and form factors in the enterprise. The following list sums up the key areas and actions that the security architect should focus on:

- 1. Mobile Devices Need Antimalware Software
- 2. Secure Mobile Communications
- 3. Require Strong Authentication, Use Password Controls
- 4. Control Third-party Software
- 5. Create Separate, Secured Mobile Gateways
- 6. Choose (or Require) Secure Mobile Devices, Help Users Lock Them Down
- 7. Perform Regular Mobile Security Audits, Penetration Testing

For example, how would a security architect take the items on this list and integrate them into a coherent strategy for management of mobile devices in the enterprise? The easiest answer is to create a security policy that addresses some or many of the items on the list. The harder answer involves the steps required to draft, review, implement, communicate, train, manage, optimize, enforce, audit, and update the policy over time within the enterprise. What would be involved in crafting a security policy to address the use of mobile devices in the enterprise? A policy would include some of the bullet points listed below:

## GENERAL MOBILE DEVICE BEST PRACTICES

- Use a passcode/passphrase/pattern to lock the device after inactivity; typically no more than 10 minutes of inactivity should trigger this.
- Encrypt the device if the option is available, using the highest encryption possible (minimum 128-bit). If encryption is unavailable, never store highly confidential data on the device.
- When choosing between unsecured WiFi and 3G/4G/CDMA service, always opt for the cellular data service, as it is typically significantly more secure than unsecured WiFi. If accessing sensitive/protected data, never use unsecured WiFi unless you have access to a VPN client.
- Use a VPN if the device will support it.
- Report stolen/lost devices as soon as possible. Note your device serial number, ESN (Electronic Serial Number, if applicable), and other identifying information for your own records and to facilitate law enforcement or other recovery.
- Utilize remote wipe capabilities if possible, based on platform.
- Carefully select applications to install on the device, taking into account the type of data the application will access, whether or not the application is believed to be secure, and whether or not the vendor typically collects information from users through the application (leading to possible data leakage).
- It is recommended to avoid use of Remote Desktop programs via a mobile device.
- Disable options and applications that you do not use.
- If Bluetooth is enabled, do not allow the device to be discovered automatically, and secure it with a password to prevent unauthorized access.
- Never leave the mobile device unattended.
- Utilize antivirus/antimalware software if supported.
- Regularly back up data – preferably in an encrypted fashion.
- Update the device’s software per the manufacturer’s instructions. Typically updates tend to fix security holes and improve device functionality.
- Limit use of the device by third parties to protect your personal data and facilitate accountability for potential misuse.
- Turn off GPS and data when not being used.
- Do not jailbreak the mobile device.

## IPAD/IPOD/IPHONE SPECIFIC BEST PRACTICES

Use of configuration templates to set up the device on the enterprise network and to enforce suggested policies on the device, including:

- Use of a passcode (strength dependent on the potential data the device may contain)
- Allow device wipe if 10 failed passcode attempts
- Use of Cisco AnyConnect VPN – Available in the Apple App Store
- Encryption of device configuration profile
- Forced encryption of device backups
- If multiple users will be accessing the device, the native mail program should not be used to protect the primary user’s email account.
- If the device is no longer in use, ensure that all of the data on it is wiped, and it is disposed of properly.

Another resource for the security architect to take a look at would be NIST Special Publication 800-124 Revision 1, "Guidelines for Managing the Security of Mobile Devices in the Enterprise".45 The Guidelines provide a comprehensive overview of the current state of centralized mobile device management technologies, including an overview of the components, architectures, and capabilities of these technologies and offer recommendations for selecting, implementing, and using such technologies.

Other key recommendations for organizations seeking to implement and maintain a sound mobile device security program include:

- Instituting a mobile device security policy that is documented in the system security plan and that defines:
  1. The types of enterprise resources that may be accessed via mobile devices;
  2. The types of mobile devices that are permitted to access the organization’s resources;
  3. The degree of access of the various classes of mobile devices (organization-provided mobile devices vs. personally-owned mobile devices) and how provisioning should be handled;
  4. How the organization’s centralized mobile device management servers are administered and how policies in those servers are updated; and
  5. All other requirements for mobile device management technologies.
- Developing system threat models for mobile devices and the organization resources that are accessed through mobile devices before designing and deploying mobile device solutions.
- Considering the merits of each security service provided by mobile device solutions, determine which services are needed for the organization’s environment, and then designing and acquiring one or more solutions that
