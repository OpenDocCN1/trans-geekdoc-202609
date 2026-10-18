
# Technical Vulnerabilities

Technical vulnerabilities are often remediated with patches, updates, or configuration changes to the system, and in some cases completely new software or hardware is necessary to mitigate vulnerabilities if they cannot otherwise be eliminated. Technical vulnerabilities are usually detected during vulnerability scanning, which involves using a host- or network-based scanner to search a system for known vulnerabilities. We will discuss vulnerability scanning later in this objective.

## Nontechnical Vulnerabilities

Nontechnical vulnerabilities can be more difficult to detect, and even harder to mitigate, than technical vulnerabilities, but they are equally serious. Nontechnical vulnerabilities include weaknesses that are inherent to administrative controls, such as policies and procedures, and physical controls. A policy addressing the mandated use of encryption is a serious weakness, for example, if no one is required to encrypt sensitive data. Physical vulnerabilities, such as lack of fencing, alarms, guards, and so on, can create serious security and safety concerns in terms of protecting facilities, people, and equipment.

Nontechnical vulnerabilities are also discovered during a vulnerability assessment, but this type of assessment looks more closely at processes and procedures, as well as administrative and physical controls. These vulnerabilities can’t, however, be addressed by simply patching; more often than not, mitigating these vulnerabilities requires more resources, additional personnel training, or additional policies.

## Managing Patches and Updates

Along with vulnerability management comes patching and update management. Technical vulnerabilities are most often addressed with patches or updates to operating systems and applications. However, patches and updates shouldn’t simply be applied sporadically or only when an administrator has time. They should be carefully considered for both positive and potentially negative security and functional issues they may introduce into the infrastructure. Managing patches and updates includes considering the criticality of both the patch and the system, a solid patch update schedule, and formal patch testing and configuration management, all discussed next.

![Images](note.jpg)

**NOTE** Although some professionals tend to use the terms “patches” and “updates” interchangeably in ordinary conversation, a patch is specifically used to mitigate a single vulnerability or fix a specific functional or performance problem. An update is a group of patches, released by a vendor on a less frequent basis (often scheduled periodically) and may add functionality to a system, or “roll up” several patches.

### Patch and System Criticality

Criticality is a key concern in patch and update management, from two different perspectives:

• **System criticality** When installing patches and updates, critical assets, such as servers and networking equipment, may be offline for an indeterminate amount of time while the patch or update is applied and tested. Often this downtime is minimal, but for critical assets, the installation should be scheduled to meet the needs of the user base and the organization.

• **Patch and update criticality** The critical nature of the patch or update itself may be a factor. The patch may, for example, mitigate a zero-day vulnerability that creates high risk in the organization. The patch must be applied as soon as possible but should be balanced with the criticality of the systems that it must be applied to.

An organization must be prepared to make decisions that require balancing system criticality with patch criticality; this is often a subject that has to be addressed quickly by the entire change management board, so an organization must plan appropriately.

![Images](exam.jpg)

**EXAM TIP** Criticality of both patches and systems must be balanced when making the determination to install patches that mitigate serious vulnerabilities, especially those that have not been tested or may take systems down for an unknown period of time. You must balance the need to maintain system uptime and availability with the risk of not implementing the patch quickly.

### Patch Update Schedule

Criticality aside, patches should be applied as soon as possible but should be prioritized according to the urgency of the patch and the criticality of the assets. An organization should have a regular schedule and routine for deploying patches, which should include the ability to test patches in a development environment before applying them to production systems. Administrators should have the opportunity to review patches based on the system criticality and the risk that leaving an unpatched system introduces, so they can appropriately schedule the patch for installation.

Routine patches may be applied only once a week or once a month but should at least be scheduled so that there is minimal disruption to the user base. This is where policy comes into play—the patch and vulnerability management policy should indicate a schedule based on criticality of patches and systems. A typical schedule may require critical patches to be applied within one business day and routine patches to be applied within seven calendar days. In any event, a regular patching schedule is absolutely necessary to make sure that new vulnerabilities are mitigated.

### Patch Testing and Configuration Management

Simply downloading a patch and applying it to a production system is not a safe practice; patches and updates sometimes have adverse effects on systems, including affecting their functionality and performance, or even opening up further security vulnerabilities. Sometimes patching one vulnerability can lead to another, so patches should be tested on development or test systems prior to being implemented in the production environment. Unfortunately, sometimes the patch schedule makes this difficult, particularly when the patch or system is critical. In the event of an urgent patch, an organization might decide to apply it directly to production systems, after thorough research and ensuring the patch or update can be rolled back quickly if needed.

As mentioned previously, patches and updates are closely related to configuration management; sometimes applying a major patch or update changes the security baseline significantly. Once the patch has been tested and approved, it is implemented on production systems. For future systems, the patch may need to be considered for the initial build and included in the system master images. This requires configuration management and documenting changes to the official standardized baseline.

Patches and updates should be documented to the greatest extent possible; sometimes this may not be practical in the event of many patches that may come all at once, but at least maintaining a list of patches or a snapshot of the system state before and after patching can help later documentation. This is important because if a patch or update changes system functionality or lowers the security level of a system, documentation can provide valuable information when researching the root cause of the issue and can support potential rollback.

**Cross-Reference**

Configuration management was discussed at length in Objective 7.3.

## REVIEW
