
**High potential impact** means the loss of CIA could be expected to have a severe or catastrophic adverse effect on organizational operations, organizational assets, or individuals.

### Confidentiality Factors
Information is evaluated for confidentiality with respect to the impact of unauthorized disclosure as well as the use of the information. Federal guidelines suggest that agencies consider the following:
* How can a malicious adversary use the unauthorized disclosure of information to do limited/serious/severe harm to agency operations, agency assets, or individuals?
* How can a malicious adversary use the unauthorized disclosure of information to gain control of agency assets that might result in unauthorized modification of information, destruction of information, or denial of system services that would result in limited/serious/severe harm to agency operations, agency assets, or individuals?
* Would unauthorized disclosure/dissemination of elements of the information type violate laws, executive orders (EOs), or agency regulations?

### Integrity Factors
Information is evaluated for integrity with respect to the impact associated with unauthorized modification or destruction. Federal guidelines suggest that agencies consider the following:
* How does unauthorized or unintentional modification of information harm agency operations, agency assets, or individuals?
* What is the impact of actions taken, decisions made based on modified information, or if the modified information is disseminated to other organizations or the public?
* Does modification/destruction of elements of the information type violate laws, EOs, or agency regulations?

### Availability Factors
Information is evaluated for availability with respect to the impact of disruption of access to or use of the information. Federal guidelines suggest that agencies consider the following:
* How does the disruption of access to or use of information do harm to agency operations, agency assets, or individuals?
* What is the impact of destruction and/or permanent loss of information?
* Does disruption of access to or use of elements of the information type violate laws, EOs, or agency regulations?

### FYI: Examples of FIPS-199 Classification

#### Example 1
An organization managing *public information* on its web server determines that there is no potential impact from a loss of confidentiality (that is, confidentiality requirements are not applicable), a moderate potential impact from a loss of integrity, and a moderate potential impact from a loss of availability. The resulting SC of this information type is expressed as follows:
`SC public information = {(confidentiality, n/a), (integrity, moderate), (availability, moderate)}`.

#### Example 2
A law enforcement organization managing extremely sensitive investigative information determines that the potential impact from a loss of confidentiality is high, the potential impact from a loss of integrity is moderate, and the potential impact from a loss of availability is moderate. The resulting SC for this type of information is expressed as follows:
`SC investigative information = {(confidentiality, high), (integrity, moderate), (availability, moderate)}`.

#### Example 3
A power plant contains an SCADA (supervisory control and data acquisition) system controlling the distribution of electric power for a large military installation. The SCADA system contains both real-time sensor data and routine administrative information. The management at the power plant determines that: (i) for the sensor data being acquired by the SCADA system, there is moderate impact from a loss of confidentiality, a high potential impact from a loss of integrity, and a high potential impact from a loss of availability; and (ii) for the administrative information being processed by the system, there is a low potential impact from a loss of confidentiality, a low potential impact from a loss of integrity, and a low potential impact from a loss of availability. The resulting SCs of these information types are expressed as follows:
`SC sensor data = {(confidentiality, moderate), (integrity, high), (availability, high)}`, and
`SC administrative information = {(confidentiality, low), (integrity, low), (availability, low)}`.
The resulting SC of the information system is expressed as
`SC SCADA system = {(confidentiality, moderate), (integrity, high), (availability, high)}`,
thus representing the high-water mark or maximum potential impact values for each security objective from the information types resident on the SCADA system.

## Why Is National Security Information Classified Differently?
The Unites States government and the military process, store, and transmit information directly related to national security. It is important that everyone who interacts with these data recognize the significance. The first EO specifically defining and classifying government information was issued by President Harry S. Truman in 1952. Subsequent EOs were issued by Presidents Eisenhower, Nixon, Carter, Reagan, Clinton, and Bush. In December 2009, President Barack Obama issued Executive Order 13526 (Classified National Security Information), which revoked and replaced previous EOs:
“This order prescribes a uniform system for classifying, safeguarding, and declassifying national security information, including information relating to defense against transnational terrorism. Our democratic principles require that the American people be informed of the activities of their Government. Also, our Nation’s progress depends on the free flow of information. Nevertheless, throughout our history, the national defense has required that certain information be maintained in confidence in order to protect our citizens, our democratic institutions, our homeland security, and our interactions with foreign nations. Protecting information critical to our Nation’s security and demonstrating our commitment to open Government through accurate and accountable application of classification standards and routine, secure, and effective declassification are equally important priorities.” (President Barack Obama, December 29, 2009)

The following three special classifications defined in Executive Order 13526 denote special access and handling requirements. Information extraneous to the classification system is considered unclassified. Sensitive But Unclassified (SBU) is a Department of Defense–specific classification category. Authorization to assign classification level is restricted to specific U.S. Government officials:
* **Top Secret (TS):** Any information or material the unauthorized disclosure of which reasonably could be expected to cause exceptionally grave damage to the national security. Examples of exceptionally grave damage include armed hostilities against the United States or its allies; disruption of foreign relations vitally affecting the national security; the compromise of vital national defense plans or complex cryptology and communications intelligence systems; the revelation of sensitive intelligence operations; and the disclosure of scientific or technological developments vital to national security.
* **Secret (S):** Any information or material the unauthorized disclosure of which reasonably could be expected to cause serious damage to the national security. Examples of serious damage include disruption of foreign relations significantly affecting the national security; significant impairment of a program or policy directly related to the national security; revelation of significant military plans or intelligence operations; compromise of significant military plans or intelligence operations; and compromise of significant scientific or technological developments relating to national security.
