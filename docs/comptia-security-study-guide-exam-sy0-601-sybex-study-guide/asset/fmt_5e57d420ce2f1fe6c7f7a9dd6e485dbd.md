
## 12. Bart knows that there are two common connection methods between Wi-Fi devices. Which of the following best describes ad hoc mode?

1. Point-to-point
2. NFC
3. Point-to-multipoint
4. RFID

## 13. Susan wants to ensure that the threat of a lost phone creating a data breach is minimized. What two technologies should she implement to do this?

1. Wi-Fi and NFC
2. Remote wipe and FDE
3. Containerization and NFC
4. Geofencing and remote wipe

## 14. What are the two most commonly deployed biometric authentication solutions for mobile devices?

1. Voice recognition and face recognition
2. Fingerprint recognition and gait recognition
3. Face recognition and fingerprint recognition
4. Voice recognition and fingerprint recognition

## 15. Alaina has implemented WPA2 and uses enterprise authentication for access points in infrastructure mode. What encryption protocol is her network using?

1. WEP
2. TKIP
3. CCMP
4. IV

## 16. Jerome wants to allow guests to use his organization's wireless network, but he does not want to provide a preshared key. What solution can he deploy to gather information such as email addresses or other contact information before allowing users to access his open network?

1. WPS capture mode
2. Kerberos
3. WPA2
4. A captive portal

## 17. Amanda wants to create a view of her buildings that shows Wi-Fi signal strength and coverage. What is this type of view called?

1. A channel overlay
2. A PSK
3. A heatmap
4. A SSID chart

## 18. Laura wants to deploy a WPA2 secured wireless for her small business, but she doesn't have a RADIUS server set up. If she wants her Wi-Fi to be encrypted, what is her best option for wireless authentication?

1. EAP
2. PSK
3. EAP-TLS
4. Open Wi-Fi with a captive portal

## 19. Gurvinder wants to select a mobile device deployment method that provides employees with devices that they can use as though they're personally owned to maximize flexibility and ease of use. Which deployment model should he select?

1. CYOD
2. COPE
3. BYOD
4. MOTD

## 20. Octavia discovers that the contact list from her phone has been acquired via a wireless attack. Which of the following is the most likely culprit?

1. Bluejacking
2. An evil maid
3. Bluesnarfing
4. An evil twin

# Chapter 14: Incident Response

When things go wrong, organizations need a way to respond to incidents to ensure that their impact is limited and that normal operations can resume as quickly as possible. That means you need to know how to identify an incident given a series of events or data points, how to contain the incident, and then what to do about it.

In this chapter you will learn about the components of a typical incident response process, including the incident response cycle. Incident response isn't just about how to stop an attacker or remove their tools. It includes preparation and learning processes to ensure that the organizations continuously learn and improve based on the incidents they have resolved. You will also learn about incident response teams, the types of exercises you can conduct to get ready for incidents, and the incident response plans you may want to have in place. With that information in hand, you'll learn about three common models that help contextualize incidents: MITRE's ATT&CK model, the Diamond Model of Intrusion Analysis, and the Cyber Kill Chain.

With the basics of incident response under your belt, your next step will be to explore incident response data and tools, with a focus on security information and event management (`SIEM`) systems. You will explore common capabilities and uses for `SIEM` tools, as well as the logs and data that `SIEM` systems ingest and analyze to help incident responders.

The chapter continues with an exploration of mitigation and recovery processes and tools. Playbooks and runbooks are two of the most important elements for responders because they help guide responses in stressful situations and ensure that your organization has planned what to do in advance. Security orchestration, automation, and response (`SOAR`) tools are also commonly used to help guide recovery and response. `SOAR` tools and manual techniques help with the mitigation and recovery processes that often reconfigure endpoint security solutions to ensure organizations are secure as part of a response process.

## Incident Response

No matter how strong an organization's security protections are, eventually something will go wrong. Whether that involves a direct attack by a malicious actor, malicious software, an insider threat, or even just a simple mistake, a security incident is an eventuality for all organizations.

Organizations therefore need an incident response (`IR`) plan, process, and team, as well as the technology, skills, and training to respond appropriately. A strong incident response process is not just a one-time action or something that is applied only in emergencies. Instead, `IR` is an ongoing process that improves organizational security using information that is learned from each security incident.

### The Incident Response Process

The first step toward a mature incident response capability for most organizations is to understand the incident response process and what happens at each stage. Although organizations may use slightly different labels or steps and the number of steps may vary, the basic concepts remain the same. Organizations must prepare for incidents, identify incidents when they occur, and then contain and remove the artifacts of the incident. Once the incident has been contained, the organization can work to recover and return to normal, and then make sure that the lessons learned from the incident are baked into the preparation for the next time something occurs.

[Figure 14.1](#c14.xhtml#c14-fig-0001) shows the six steps that the Security+ exam outline describes for the incident response process.

![FIGURE 14.1 The incident response cycle](images/c14f001.png)

**FIGURE 14.1** The incident response cycle

The six steps you will need to know for the Security+ exam are as follows:

1. **Preparation.** In this phase, you build the tools, processes, and procedures to respond to an incident. That includes building and training an incident response team, conducting exercises, documenting what you will do and how you will respond, and acquiring, configuring, and operating security tools and incident response capabilities.

2. **Identification.** This phase involves reviewing events to identify incidents. You must pay attention to indicators of compromise, use log analysis and security monitoring capabilities, and have a comprehensive awareness and reporting program for your staff.

3. **Containment.** Once an incident has been identified, the incident response team needs to contain it to prevent further issues or damage. Containment can be challenging and may not be complete if elements of the incident are not identified in the initial identification efforts.

4. **Eradication.** The eradication stage involves removing the artifacts associated with the incident. In many cases, that will involve rebuilding or restoring systems and applications from backups rather than simply removing tools from a system since proving that a system has been fully cleaned can be very difficult. Complete eradication and verification is crucial to ensuring that an incident is over.
