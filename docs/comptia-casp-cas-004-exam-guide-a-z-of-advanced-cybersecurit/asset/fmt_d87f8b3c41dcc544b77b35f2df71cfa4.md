
# Trusted OS and Hardware Security

## Secure Boot Process

**Step 2**: Windows Boot Components verifies the signature on each component to be loaded. Any non-trusted components will not be loaded and will trigger remediation.

**Step 3**: The signatures on all boot-critical drivers are checked as part of secure boot verification in Winload (Windows Boot Loader) and by the Early Launch Anti-Malware driver.

The disadvantage is that systems that ship with UEFI Secure Boot enabled do not allow the installation of any other operating system. This prevents installing any other operating systems or running any live Linux media.

## Measured Launch

A measured launch is a launch in which the software and platform components have been identified, or “measured,” using cryptographic techniques. The resulting values are used at each boot to verify trust in those components. A measured launch is designed to prevent attacks on these components (system and BIOS code) or at least to identify when these components have been compromised. It is part of the Intel Trusted Execution Technology (Intel TXT). TXT functionality is leveraged by software vendors including HyTrust, PrivateCore, Citrix, and VMware.

An application of measured launch is Measured Boot by Microsoft in Windows 10 and Windows Server 2016. It creates a detailed log of all components that loaded before the anti-malware. This log can be used to both identify malware on the computer and maintain evidence of boot component tampering. One possible disadvantage of measured launch is the potential slowing of the boot process.

## Integrity Measurement Architecture

Another approach that attempts to create and measure the runtime environment is an open-source trusted computing component called Integrity Measurement Architecture (IMA). IMA creates a list of components and anchors the list to the TPM chip. It can use the list to attest to the system’s runtime integrity. Anchoring the list to the TPM chip in hardware prevents its compromise.

## BIOS/UEFI

Unified Extensible Firmware Interface (UEFI) is an alternative to using BIOS to interface between software and firmware of a system. Most images that support UEFI also support legacy BIOS services. Some of its advantages are as follows:

- Ability to boot from large disks (over 2 TB) with a GUID partition table
- CPU-independent architecture
- CPU-independent drivers
- Flexible pre-OS environment, including network capability
- Modular design

## Attestation Services

Attestation services allow an authorized party to detect changes to an operating system. These services involve generating a certificate for the hardware that states what software is currently running. The computer can use this certificate to attest that unaltered software is currently executing. Windows operating systems have been capable of remote attestation since Windows 8.

## Vulnerabilities Associated with Hardware

While security professionals devote a lot of time to chasing software vulnerabilities, they often forget about hardware vulnerabilities. Remember that one of the most well-known hacks—the Target hack—took advantage of a hardware encryption flaw. Another example of a hardware vulnerability is the hacking of a car system and the subsequent takeover of the control system. Hackers have embraced hardware attacks because of the difficulty in detecting them, but the compromising of hardware goes beyond backdoors. Vulnerabilities also include the following:

- Backdoors that affect embedded RFID chips and memory
- Eavesdropping through protected memory without any other hardware being opened
- Faults induced to interrupt normal behavior
- Hardware modification tampering with hardware or jailbroken software
- Backdoors or hidden methods for bypassing normal computer authentication systems
- Counterfeit products made to gain malicious access to systems

The only assured way of preventing such vulnerabilities is to tightly control the manufacturing process for all products. DoD uses the Trusted Foundry Program to validate all vendors in this regard. No longer can organizations simply purchase the cheapest devices from Asia; they must now begin to grapple with the creation of their own programs that emulate the Trusted Foundry Program.

## Conclusion

This chapter defines the concepts of Trusted OS and ways of improving system security. This includes antivirus, antimalware, antispyware and spam filters, patch management, and data loss prevention along with endpoint monitoring and response. Concepts for host hardening, boot loader protection, and hardware vulnerabilities are also discussed. This chapter also includes security recommendations and measures when using terminal and application delivery services.

In the next chapter, we will discuss challenges and measures for implementing secure storage controls.

# CHAPTER 8: Secure Storage Controls

## Introduction

Many organizations face the challenge of implementing protection and data security measures to meet a wide range of requirements that lie beyond regulatory compliance. Security professionals daily face the challenge of securing the application, compute, and network environment, while audit professionals are charged with verifying their success. Too often, storage security has slipped under their radar because of limited familiarity with the technology. Storage managers and administrators may be confronting these issues and technologies for the first time. This chapter highlights the basics of identifying key business drivers for data security, describes threats and attacks, summarizes security concepts and relationships, and then describes what constitutes storage security.

Most organizations are extremely dependent on digital information, which is processed electronically, and transferred on local and public networks. Within these organizations, many tasks performed are simply not possible without information and communications technology (ICT), while others can only be partially performed without ICT (i.e., many enterprises are totally reliant on the correct functioning of their ICT assets). As society as a whole becomes more dependent on ICT and digital assets, the social impact of the failure of ICT resources ceases to be an inconvenience and begins to take on the character of a disaster. A few other elements of the ICT infrastructure have a more important relationship with data than that of storage systems and ecosystems – they are the repository. They may also be the last line of defense against an adversary, but only if storage managers and administrators invest the time and effort to implement and activate the available storage security controls. While the data are becoming increasingly precious assets for both organizations and individuals, there are no global or national practice standards that can be used to categorize the sensitivity and value of the data beyond the following:

- Personal, private information (including personally identifiable information or PII)
- Business information
- National security (both classified and unclassified) information

## Structure

In this chapter, we will cover the following topics:

- Storage controls
- Cloud storage
- Geotagging
- Wearable technologies
- Encrypted and unencrypted communication
- Resource provisioning and de-provisioning
- Data flow security
- Resilience issues
- Data security considerations
- Cloud and on-premise data security

## Objective
