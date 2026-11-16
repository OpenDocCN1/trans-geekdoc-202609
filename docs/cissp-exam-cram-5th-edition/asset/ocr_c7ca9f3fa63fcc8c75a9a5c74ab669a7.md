# Sensor Placement

Your organization’s security policy should detail the placement of your IDS and its sensors. The placement of IDS sensors requires some consideration. IDS sensors can be placed externally, in the DMZ, or inside the network. Your decision to place a sensor in any one or more of these locations will require specific tuning. Without proper tuning, the sensor will generate alerts for all traffic that matches given criteria, regardless of whether the traffic is indeed something that should generate an alert. The placement of sensors is dynamic and must constantly change as your environment changes. A sensor should be stealth, and may even be deployed via a one-way networking cable so that it is harder for a hacker to scanner and find it.

> **ExamAlert**
> 
> An anomaly-based IDS can detect zero-day attacks, but signature-based and rule-based IDSs cannot.

# Intrusion Prevention Systems (IPSs)

IPSs take IDS technology a step further. IPSs can react automatically and actually prevent security occurrences from happening—without user intervention. IPSs are considered the next generation of IDSs and can block attacks in real time. NIST uses the term IDP (intrusion detection and prevention) to define modern devices that provide the functionality of both IDS and IPS devices. These devices typically perform deep inspection and can be applied to devices that support OSI Layer 3 to OSI Layer 7 inspection.

# Two Great Tools Combined as One

SIEM is a combination of the two separate services security information management (SIM) and security event management (SEM). SIM is used to process and handle the long-term storage of audit and event data, whereas SEM is used for real-time reporting of events. Combining these two technologies provides users with the ability to alert, capture,