
Given the access and privileges with which the management plane operates, concerns over security are of the highest level. A compromise of the management plane would give an attacker complete control of the entire environment and make the entire cloud vulnerable, which is well above the risk and threat a compromised hypervisor would provide because the management plane controls multiple hypervisors. The most highly vetted limited set of administrative staff should have access to the management plane, and all access and functions should be tightly audited and reviewed on a regular basis.

## Risks Associated with Cloud Infrastructure

Cloud-based systems have the same level of risk as other hosting models, but with the addition of risks specific to cloud hosting. A cloud-based system should be approached and managed by any other outsourced platform, with the same types of concerns, risks, and governance requirements as an external hosting environment.

## Risk Assessment and Analysis

Cloud hosting has the same areas of risk as all systems and applications, with cloud-specific risks on top of these risks or as key aspects expanding upon them. From an organizational and regulatory perspective, there are risks related to lock-in, governance, data security and privacy, and any legal and regulatory controls and reports for a system or application. One of the biggest benefits of the cloud hosting model is portability and the ability to move between providers at will. If an organization locked into that provider and incur a lot of property requirements, they may get locked in substantial costs if they decide to switch.

With any external hosting arrangement, a company loses substantial control over their systems and their governance. Even with strong contractual requirements and SLAs in place, the level of control and access will be much less than what would be in their proprietary data centers. Depending on the regulatory requirements for the type of application and data to be hosted, the choice of cloud provider may be limited, or even extincted. Cloud providers have to serve a large number of customers with their business model, which makes them complying with various types of certifications and requirements difficult. A primary concern for any company is where their data is stored and whether sufficient protections are in place to ensure their confidentiality and integrity. A cloud environment presents many challenges for appropriate governance, made even more complicated by eDiscovery requirements, depending on the nature and type of the data, that need to be carefully evaluated and weighed before making a cloud hosting decision.

> NOTE: eDiscovery is the process through which electronic data is requested by a legal entity for use in a criminal or civil legal proceeding. It is the responsibility of the application or system owner to thoroughly analyze for all data that is within scope and pertinent to the official request, and then provide it to the legal entity with a certification that it is complete and secured.

![](img/44bc0d6508f04646c7c3b07267095e71_150_0.png)

## Chapter 4: Cloud Platform and Infrastructure Security

131

Apart from the risk factors that play into any hosting environment, a cloud environment has additional data factors that are unique in nature. A major risk in a cloud environment is ensuring that data can be completely removed from the system when necessary or required. As covered in Chapter 2, in a traditional data center, physical media can be destroyed to ensure data destruction, which is not possible in a cloud environment, so concepts such as cryptographic erasure and overwriting are prominently used. Along the same lines of data protection is the security of system images within a cloud environment. Because the images themselves are just files on a file system without any physical separation of servers, combined with the possibility of malware injecting into an image even when it is not running, their security becomes important in a cloud environment, where the cloud provider bears sole responsibility for assurance.

With the self-service aspect of cloud computing, an enormous amount of software is involved in running a cloud environment—from image creation and deployment, to auditing and reporting tools, to user management and key management. Every piece of software throughout the environment—from full application suites to small utility scripts—carries with an inherent risk of compromise and vulnerabilities. This software is also removed from the customer's visibility and inspection, and it's the sole responsibility of the cloud provider to ensure its security. Because this is outside the run-time environment of the cloud system, in many instances this software will be overlooked in audits and monitoring, and the Cloud Security Professional should apply due diligence when selecting a cloud provider to ensure that they are aware of the risks associated with these tools and have strong auditing and monitoring policies and systems in place. The underlying software running the actual virtual hosts is also susceptible to risk of compromise and vulnerabilities, which we will cover in the following section on virtualization risks. However, the key points include the hypervisor being compromised as well as the potential for guests to break out and access other systems and data if cloud security controls are not properly implemented and monitored.

## Virtualization Risks

With the added layers and complexities of virtualization also come additional risks not found in a traditional server model.

If a hypervisor were to be compromised in any way, the underlying virtual machines that are hosted by it are also vulnerable. Because the hypervisor has control over and their access to computing resources, the possibility of malware injections and open attack vectors become pronounced for any virtual machines hosted under or controlled by the hypervisor.

Beyond just the virtual machines connected to the hypervisor, because it plays a central role within the cloud infrastructure, a compromised hypervisor can also be used to attack other hypervisors or components within the same cloud environment. A compromised hypervisor can also be used as a launching pad to compromise virtual machines hosted by other hypervisors that are accessible within the cloud.

Another big risk with virtualization involves how network traffic is handled, monitored, and logged. With a traditional network in a data center with physical servers, it is possible to log and analyze network traffic, use intrusion detection systems (IDS) as desired. However, in a virtualized environment, this is not necessarily through a physical switch.

152

# CCSP Certified Cloud Security Professional All-in-One Exam Guide
132

As cloud and virtualized environments have gained popularity, most major offer offer virtualized versions of traditional physical gear, such as switches, firewalls, and IDSs.

A significant difference and potential drawback with virtualized environment versus a traditional server model is the reality of images are stored and operate. With a traditional server model, the operating system is deployed on top of the underlying hardware and interacts directly with it. However, in a virtualized environment, a "server" is nothing more than a disk image that resides on an actual file system. While a virtual host is up and running, it is susceptible to all the types of attacks and vulnerabilities that a physical host would, based on its operating system. Due to the nature of a disk image existing in the environment, there is an extra vulnerability the disk image itself attacked from the hypervisor and file system. From this attack vector, no compensating security controls or monitoring be effective at mitigating the attack, especially because this method is not dependent on the image being live or running at the time.

![](img/44bc0d6508f04646c7c3b07267095e71_152_0.png)

> TIP: As a Cloud Security Professional, much of your attention should be paid to the actual run-time environment and the protection of data. However, do not overlook diligence ensuring that the cloud provider takes steps toward securing the virtualized environment and protecting the hypervisor layer as has in place strong security controls and monitoring to ensure that virtual images cannot be modified while live or inactive state.

## Countermeasure Strategies

While the unique challenges and additional risks of cloud computing are well known, so too are the many mitigation strategies that have become commonplace and best practices. The same degree of automation that a cloud platform provides between provisioning and reporting can be applied to the implementation of security controls. As systems auto-scale and expand, using base images for virtual hosts that have already been hardened and scanned, you can ensure that new hosts, as they are brought online, are already secured in the exact same manner as the baseline. The same methodology can be applied within a cloud framework for patching and updating. After performing upgrades and large-scale automated patching, which then requires scanning and auditing
