
# Choosing the `Clean` Option

Choosing the `Clean` option for an incident related to a worm or a Trojan would do nothing to remediate the incident because the root cause is the file and therefore cannot be cleaned. This option removes the infection from the file but does not actually delete the file itself. This is helpful only where a legitimate file has been infected with nonlegitimate code.

# Choosing the `Quarantine` Option

Choosing the `Quarantine` option would move the file to a reserved area controlled by the antivirus program. The file is not removed permanently, nor is it repaired—it is simply isolated. This is often a fairly safe option since it preserves the file in cases where removing it would impact the operation of the system.

## Recovery

In the `recovery` portion of the containment, eradication, recovery phase of the IRP process, actions are taken to validate that all systems and services affected by the incident are fully restored to a normal operational condition. After the CSIRT has concluded that the incident has been completely remediated, they must restore the confidence of the stakeholders in the system.

To accomplish this, system personnel must test the operation of the system (or systems) that was affected by the incident to ensure that it is fully functional. In addition, involve the system management stakeholders in observing the restored system and have them declare that it is fully operational.

In critical OT environments, organizations may be required to have procedures in place to protect data that would be useful in the investigation of an incident that requires execution of their IRP. Always take steps to maintain positive control of any evidence and log everything in an appropriate chain of custody form to maintain its integrity.

As mentioned earlier, while remediation steps such as removing infected assets/files and returning the process to a normal operational state is the primary goal of all incident response plans, it is important to be aware that activities leading to this goal, such as deleting files, powering down a system to replace a hard drive, or restoring the system to a previous version, might destroy forensic evidence that could be used to determine root cause.

In many cases, capturing forensic information prior to restoring the system is the only way to determine what happened after the fact. The forensic collection process is also typically the basis for any legal actions that might be taken related to an attack.

At the top of the forensic collection process to-do list is actually a don't-do item—do not turn off computing devices during an attack or before information about the incident can be obtained and recorded. Before powering off affected devices, it is important to collect images of any volatile data from system RAM and the hard drive, if possible. After these images have been created, it is safe to disconnect the affected devices from the network and shut them down.

The final step is to restore the affected devices to their fully operational states. This typically involves restoring them from backup copies or baseline snapshots.

## Post-Incident Activities

The NIST guidelines identify the `lessons learned` and improvement steps of the `post-incident activities` as the most important part of the incident response lifecycle. These steps help the organization to evolve in anticipation of new threats and improved technologies. All the parties involved in a major incident should be involved in a lessons-learned meeting following the conclusion of the response effort to determine what occurred, what was done, what could have been done that wasn't, and how well the response plan worked.

### Root-Cause Analysis

After containment actions have been implemented, the CSIRT must turn its attention to locating the root cause of the incident. This is accomplished through `root-cause analysis` (`RCA`). RCA is a problem-solving method that is used to separate causal factors from root causes. A causal factor is any condition that will provide an improved condition if removed but does not prevent the recurrence of the incident. A `root cause` is the condition or item that does prevent the incident from recurring after it has been removed or neutralized.

All of the collected incident data should be brought together and analyzed thoroughly. The analysis of the incident's characteristics may show a systemic security problem that needs to be addressed, or it may point out singular vulnerabilities that must be mitigated. In either case, the analysis can be used to update the IRP and suggest any additional controls that need to be put in place to strengthen the organization's cybersecurity posture.

### Recording/Reporting

All the procedures listed in the previous sections, including actions taken during the response, must be documented. If warranted, help from federal authorities, such as CISA or NERC, may be requested for a more in-depth analysis. At the very least, lessons learned should be shared and company security policies adjusted to prevent similar follow-up attacks.

Recall that the initial incident handler is responsible for establishing a `chain of custody` for handling the incident information that may become evidence. This includes creating a chain of custody document. The chain of custody document should clearly specify the “who, what, where, when, and possibly why” in case the evidence becomes a legal requirement.

At the completion of the IRP process, an incident report should be produced and distributed to all stakeholders affected. This report should include the root-cause analysis findings, the remediation actions taken, and recovery activities implemented. The purpose of the report is to educate the management team about what is/was required to make the network more secure.

The `Cybersecurity & Infrastructure Security Agency` (`CISA`) has produced guidelines for government agencies specifying how federal, state, local, and tribal government organizations submit incident notifications to the `National Cybersecurity and Communications Integration Center` (`NCCIC`) and `United States Computer Emergency Readiness Team` (`US_CERT`).

The guidelines require that organizations report information security incidents where the CIA of information systems have been compromised within one hour of the incident being validated by a member of their CSIRT team, its Security Operations Center (SOC), or its IT department. The report must include information from three categories:

*   Impact and Severity Categories
*   Attack Vectors
*   Incident Attributes

#### Impact and Severity Categories

The NCCIS collects incident impact and severity information to analyze incident attributes for a National Cyber Incident Scoring System (NCISS). The collected information is also used to calculate a severity score developed by the NCISS. Severity score categories range from Baseline (White or Blue Levels) to Low (Green level) to Medium (Yellow level) to High (Orange level) to Severe (Red level) to Emergency (Black level). The impact and severity category data required by the NCISS includes the following:

*   `Functional impact`—This is a measure of the impact to business functionality or ability to provide services. Severity levels assigned include No Impact, Minimal Non-Critical, Minimal Critical, Significant Non-Critical, Denial of Non-Critical Services, Significant Critical Services, and Denial of Critical Services Loss of Control.
*   `Information impact`—This entry describes the type of information lost, compromised, or corrupted. Impact reporting options include No Impact, Suspected But Not Identified, Privacy Data Breach, Proprietary Information Breach to Destruction of Non-Critical Systems, Critical Systems Data Breach, Core Credential Compromise, and Destruction of Critical System.
