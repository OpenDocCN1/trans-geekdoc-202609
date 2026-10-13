
# NIST Special Publication 800-61 Revision 2

When a SOC discovers that a breach has occurred, it immediately kicks off the incident response process or calls upon the team responsible for the incident response service. An incident response service covers how a team prepares for, detects, responds to, and recovers from an incident. In each one of these areas, the SOC must have a well-documented understanding of the steps that need to occur to be successful. NIST Special Publication 800-61 Revision 2, *Computer Security Incident Handling Guide*, describes incident response plans as having a lifecycle with the following phases (see [Figure 3-17](#ch03.xhtml#ch03fig17)):

*   Preparation
*   Detection and analysis
*   Containment, eradication, and recovery
*   Post-incident activity

![FIGURE 3-17 NIST SP 800-61 Rev. 2 Incident Response Process](Images/03fig17.jpg)

**FIGURE 3-17** NIST SP 800-61 Rev. 2 Incident Response Process

## Step 1: Preparation

*Preparation* is considered the most important phase of the plan. Not only does preparation cover how an organization will respond when an incident occurs, it also includes how organizations can prevent incidents from occurring by securing networks and applications. When organizations are preparing to handle events, they need basic policies that identify what actions will occur and resources that will be required such as contact and call lists; defined tracking systems; messaging protocols; access to forensic software; and physical access to war rooms and buildings. Incident response teams need access to multiple IT teams as well as procedures on how to engage legal, upper management, and public relation teams.

> **Note**
>
> A key part of preparation is preventing attacks from occurring. This is accomplished using risk assessments, user awareness training, vulnerability testing, host security, and other methods.

## Step 2: Detection & Analysis

The *detection and analysis* phase prepares an organization to be able to detect a variety of different cyberattacks from different threat surfaces. Detection occurs through data collection from network devices, host machines, security tools, and people monitoring such tools. Failing at detection means threats can operate unnoticed within the network, systems, or services.

Analysis serves a few purposes. First, the SOC must use analysis to validate whether any events that are detected are a real threat or something else. The SOC can make four different determinations regarding the analysis of an event:

*   **False positive:** When the detect tools incorrectly identify a security event the SOC needs to be concerned with
*   **True positive:** When the detect tools correctly identify a security event the SOC needs to be concerned with
*   **False negative:** When the security tools incorrectly don't alert the SOC about an event the SOC needs to be concerned with
*   **True negative:** When the security tools correctly don't alert to an event the SOC does not need to be concerned with

The mature incident response program will have a strong analysis capability allowing for the reduction of noise made up of false positives. A mature incident response program will also have a strong detection capability allowing for a reduced amount of false negatives.

## Step 3: Containment Eradication & Recovery

*Containment* focuses on stopping an attack from spreading. NIST SP 800-61 Rev. 2 often references the containment phase as "decision making." An example is how during a datacenter breach, the SOC will need to decide whether to shut down a server to prevent an attacker from gaining access to data or to leave the server running to avoid tipping off the attacker that the SOC is aware of the attacker's presence, enabling the SOC to study the attacker's methods and collect evidence. This raises a question regarding the need to preserve evidence of the attack versus minimizing the risk of attackers potentially damaging systems or stealing data. In other words, if an organization lets an attacker continue attacking a system, the organization may learn more about the attacker, their methods, and motivation. However, they do this at the risk of the attacker damaging systems, gaining a stronger foothold into the organization that may go undetected, and stealing or damaging data. The answer to this type of question will need to be addressed on a case by case situation. I will help you understand how to make the best decision regarding when to allow attacks to occur for research purposes in [Chapter 8](#ch08.xhtml#ch08), "Threat Hunting and Incident Response."

Eradication focuses on responding to all impacted parties. Eradication can work only if proper containment has been performed. If a threat isn't contained, it can't be eradicated because it's possible it will always be spreading to new systems during the eradication of the systems identified as impacted by the threat. Eradication can be performed in many ways and will depend on the type of threat being handled. In certain situations, an advanced threat will be extremely difficult to remove, in which case the best action is a complete system wipe and rebuild. Other times, eradication can just remove the threat without negatively impacting the infected system. Eradication can also include containment steps, such as shutting down services while the eradication process occurs. This is done to ensure containment of threats that can change behavior when the threat detects it is being eradicated.

Recovery can't occur until eradication has been performed, because recovery is based on the concept of returning things back to operation as they were prior to the incident. Often, containment and eradication include limiting services to prevent the spread of the threat. During the recovery phase, security measures implemented during the previous steps are removed and systems are monitored to ensure the threat has been completely eradicated. If any sign of the threat is identified, the entire process, starting with detection and analysis, is repeated until the recovery step shows no sign of the identified threat.

## Step 4: Post-Incident Activity

*Post-incident activity* includes the lessons-learned session. What happened during the incident? What controls worked, and why? What controls failed and why? What changes need to be made to enable the entire organization to be more secure and more responsive? The answers to these questions are collected for the first phase of the incident response program to improve the preparation of the organization against future threats. Post-incident activity allows the organization to learn from experience and incorporate that knowledge in better protecting the organization.

[Figure 3-18](#ch03.xhtml#ch03fig18) shows a flowchart representing how a SOC can navigate through an incident. [Figure 3-18](#ch03.xhtml#ch03fig18) is a modified version of the NIST 800-61 Rev. 2 standard that includes guidance on how to proceed within each phase and what processes will come into play. You should expect that the approach your organization takes to implementing an incident response program will likely be slightly different from published standards.

![FIGURE 3-18 Incident Response Process](Images/03fig18.jpg)

**FIGURE 3-18** Incident Response Process

# Incident Response Planning
