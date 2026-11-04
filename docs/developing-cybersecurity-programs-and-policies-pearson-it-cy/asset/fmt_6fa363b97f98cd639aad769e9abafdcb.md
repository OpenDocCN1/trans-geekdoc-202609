
# Physical and Environmental Security

Security professionals are often so focused on technical controls that they overlook the importance of physical controls. The simple reality is that physical access is the most direct path to malicious activity, including unauthorized access, theft, damage, and destruction. Protection mechanisms include controlling the physical security perimeter and physical entry, creating secure offices, rooms, and facilities, and implementing barriers to access, such as monitoring, and alerting. Section 11 of ISO 27002:2013 encompasses both physical and environmental security. Environmental security refers to the workplace environment, which includes the design and construction of the facilities, how and where people move, where equipment is stored, how the equipment is secured, and protection from natural and man-made disasters.

In previous chapters, you learned that to properly protect organizational information, we must first know where it is and how critical it is to the organization. Just as we shouldn’t spend as much money or resources to protect noncritical information as we would to protect critical information, so it goes that we shouldn’t spend the same amount to protect a broom closet as we should to protect information-processing facilities such as data centers, server rooms, or even offices containing client information.

Information security professionals rarely have the expertise to address this security domain on their own. It is critical to involve facilities and physical security personnel in strategic and tactical decisions, policies, and procedures. For example, the information security expert designs a server room with a double steel door, card-reading lock, and a camera outside the door. A facilities expert may question the construction of the walls, floor, vents, and ceilings, the capability of the HVAC and fire suppression systems, as well as the potential for a natural disaster, such as an earthquake, fire, or flood. A physical security expert may question the location, the topography, and even the traffic patterns of pedestrians, automobiles, and airplanes. Creating and maintaining physical and environmental security is a team effort.

In this chapter, we focus on design, obstacles, monitoring, and response as they relate to secure areas, equipment security, and environmental controls. We examine the security issues, related best practices, and of course, physical and environmental security policies.

## FYI: ISO/IEC 27002:2013 and NIST Cybersecurity Framework

Section 11 of ISO 27002:2013 is dedicated to physical and environmental security, with the objective of maintaining a secure physical environment to prevent unauthorized access, damage, and interference to business premises. Special attention is paid to disposal and destruction.

The NIST Cybersecurity Framework addresses physical security in three areas:
* Under the Protect Identity Management, Authentication and Access Control (PR.AC) Category stating that physical access to assets must be managed and protected
* Under the Information Protection Processes and Procedures (PR.IP) Category stating that policy and regulations regarding the physical operating environment for organizational assets must be met
* Under the Security Continuous Monitoring (DE.CM) Category stating that the physical environment needs to be monitored to detect potential cybersecurity events

Corresponding NIST guidance is provided in the following documents:
* **SP 800-12:** “An Introduction to Computer Security—The NIST Handbook”
* **SP 800-14:** “Generally Accepted Principles and Practices for Securing Information Technology Systems”
* **SP 800-88:** “Guidelines for Media Sanitization”
* **SP 800-100:** “Information Security Handbook: A Guide for Managers”
* **SP 800-116 Rev. 1:** “A Recommendation for the Use of PIV Credentials in Physical Access Control Systems (PACS)”
* **SP 800-116:** “A Recommendation for the Use of PIV Credentials in Physical Access Control Systems (PACS)”
* **SP 800-183:** “Networks of ‘Things’”

## Understanding the Secure Facility Layered Defense Model

The premise of a ***layered defense model*** is that if an intruder can bypass one layer of controls, the next layer of controls should provide additional deterrence or detection capabilities. Layered defense is both physical and psychological. The mere fact that an area *appears* to be secure is in itself a deterrent. Imagine the design of a medieval castle. The castle itself was built of stone. It was sited high on a hill within a walled property. There may have been a moat and an entry drawbridge. There were certainly lookouts and guards. For intruders to launch a successful attack, they had to overcome and penetrate each of these obstacles. The same concept is used in designing secure buildings and areas.

## FYI: How Can You Ensure Physical Security of Assets When Your Data and Applications are in the Cloud?

Mature cloud providers such as Amazon Web Services (AWS) provide detailed explanations of their physical and operational security processes for the network and server infrastructure. These are the servers that will host your applications and data in the cloud that you do not have any control over. AWS details all their physical security practices at the following white paper:
`https://d1.awsstatic.com/whitepapers/Security/AWS_Security_Whitepaper.pdf`

The white paper details:
“AWS’s data centers are state of the art, utilizing innovative architectural and engineering approaches. Amazon has many years of experience in designing, constructing, and operating large-scale data centers. This experience has been applied to the AWS platform and infrastructure. AWS data centers are housed in nondescript facilities. Physical access is strictly controlled both at the perimeter and at building ingress points by professional security staff utilizing video surveillance, intrusion detection systems, and other electronic means.

Authorized staff must pass two-factor authentication a minimum of two times to access data center floors. All visitors and contractors are required to present identification and are signed in and continually escorted by authorized staff. AWS only provides data center access and information to employees and contractors who have a legitimate business need for such privileges. When an employee no longer has a business need for these privileges, his or her access is immediately revoked, even if they continue to be an employee of Amazon or Amazon Web Services. All physical access to data centers by AWS employees is logged and audited routinely.”

The paper describes their methodologies and capabilities for the following:
* Fire detection and suppression systems to reduce risk of fire.
* Data center electrical power systems are designed to be fully redundant and maintainable without impact to operations, 24 hours a day, and seven days a week. This includes the use of uninterruptible power supply (UPS) units to provide back-up power and the use of generators.
* Climate and temperature control required to maintain a constant operating temperature for servers and other hardware.
* Management and monitoring of electrical, mechanical, and life support systems and equipment so that any issues are immediately identified.
* Storage device decommissioning when a storage device has reached the end of its useful life, to prevent customer data from being exposed to unauthorized individuals. AWS states that it follows the NIST SP 800-88 (“Guidelines for Media Sanitization”) as part of their decommissioning process.

### How Do We Secure the Site?
