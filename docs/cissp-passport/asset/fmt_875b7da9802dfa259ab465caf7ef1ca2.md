
# Most systems in the infrastructure are complex and have a myriad of configuration settings that must be carefully set in order to maintain their security and functionality. It would be impractical for administrators to manually set all of these configuration settings and expect to have time for any other of their daily tasks. Additionally, misconfigurations occur due to human error, and many of these configuration settings may render a system nonfunctional or not secure if not set correctly. This is where automation is fundamental in maintaining configuration baselines.

Hundreds of automated tools are available to assist with configuration management. Some of them are built into the operating system itself, and many others are free or third-party utilities that come with management software. For example, Windows Server includes Active Directory (AD), which has group policy settings that enable change management administrators to manage configuration baselines in an AD domain. Linux has its own built-in configuration management utilities as well. Additionally, organizations can use powerful customized scripts, such as those written in PowerShell or Python, as well as enterprise-level management systems. We will discuss many of the tools used to configure and maintain security settings in Objective 8.2. Using automated tools to perform configuration management can help reduce issues caused by human error, ensure standardization of configuration settings across the enterprise, and make configuration changes much more efficient.

## Cross-Reference

Tool sets, software configuration management, and security orchestration, automation, and response (SOAR) are related to automating the configuration management process and are discussed in depth in Objective 8.2.

## REVIEW

### Objective 7.3: Perform Configuration Management (CM) (e.g., provisioning, baselining, automation)

This objective reviewed configuration management processes. Configuration management is a subset of change management and is closely related to both vulnerability management and patch management. The provisioning process is where the initial installation and configuration of systems and applications occur. It’s important to establish a standardized baseline to use for devices across the organization, and there may be multiple baselines to address different types of devices. Baselines also change occasionally, as the environment changes or systems and applications change. Configuration management is made much more efficient and easier by using automated tools that can help reduce human error and ensure configuration baselines are maintained.

### 7.3 QUESTIONS

**[1](#ch07.xhtml#ch7ques3-1).** Your company is creating a secure baseline for its end-user workstations. The workstations should only be able to communicate with specific applications and hosts on the network. Which of the following should be included in the secure baseline for the workstations to ensure enforcement of these restrictive communications requirements?

**A.** Operating system version

**B.** Application version

**C.** Limited open ports, protocols, and services

**D.** Default passwords

**[2](#ch07.xhtml#ch7ques3-2).** Riley has been manually provisioning several hosts for a secure subnet that will process sensitive data in the company. These systems are scanned before being taken out of the test environment and connected to the production network. The scans indicate a wide variety of differences in configuration settings for the hosts that have been manually provisioned. Which of the following should Riley do so that the configuration settings will be consistent and follow the secure baseline?

**A.** Provision the systems using automated means, such as baseline images

**B.** Manually configure the systems using vendor-supplied recommendations

**C.** Back up a generic system on a network and restore the backup to the new systems so they will be configured identically

**D.** Manually configure the systems using a secure baseline checklist

### 7.3 ANSWERS

**[1](#ch07.xhtml#r_ch7ques3-1).** C Any open ports, protocols, and services affect how the workstation communicates with other applications on the network or other hosts. These should be carefully considered and controlled for the secure baseline. The other choices are also considerations for the secure baseline, but do not necessarily affect communicating with only specific applications or hosts on the network.

**[2](#ch07.xhtml#r_ch7ques3-2).** A Riley should use an automated means to provision the secure hosts; an OS image with a secure baseline could be deployed to make the job much easier and more efficient and ensure that the configuration settings are standardized.

## ![Images](obj7-4.jpg)Apply foundational security operations concepts

In this objective we reexamine some foundational security concepts that we covered in previous domains, albeit in this objective from an operations context. These concepts include need-to-know, least privilege, separation of duties, privileged account management, job rotation, and service level agreements.

### Security Operations

Security operations describes the day-to-day running of the security functions and programs. When you first learned about security theories, models, definitions, and terms, it may not have been clear as to how these things apply in the course of a security professional’s normal day. Now you are going to apply the fundamental knowledge and concepts you learned earlier in the book to the operational world.

#### Need-to-Know/Least Privilege

Two of the important fundamental concepts introduced in Domain 1, and emphasized throughout the book, are need-to-know and the principle of least privilege. These concepts ensure that entities do not have unnecessary access to information or systems.

##### Need-to-Know

Recall from previous discussions that need-to-know means that an individual should have access only to information or systems required to perform their job functions. In other words, if their job does not require access, then they don’t have the need-to-know for information, and by extension, the systems that process it. This limitation helps support and enforce the security goal of confidentiality. The need-to-know concept is applied operationally throughout security activities. Examples include restrictive permissions, rights, and privileges; the requirement for need-to-know in mandatory access control models; and the need to keep privacy information confidential.

A new employee’s need-to-know should be assumed to be the minimum required to fulfill the functions of their job. As time progresses, an individual may require more access, depending on changing job requirements and the operating environment. Only then should additional access be granted. Need-to-know should be carefully considered and approved by someone with the authority to do so; normally that might mean the individual’s supervisor, a data or system owner, or a senior manager. Need-to-know should also be periodically reviewed to see if the individual still has validated requirements to access systems and information. If the job requirements change or the operating environment no longer requires the individual to have the need-to-know, then access should be revoked or reduced.

##### Principle of Least Privilege
