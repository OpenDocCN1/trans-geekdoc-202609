
## Risk Avoidance, Transference, Acceptance, Mitigation, Deterrence

Risks are absolutes—they cannot be removed or eliminated. Actions can be taken to change the effects that a risk poses to a system, but the risk itself doesn’t really change, no matter what actions are taken to mitigate that risk. A high risk will always be a high risk. However, actions can be taken to reduce the impact of that risk if it occurs. A limited number of strategies can be used to manage risk. The risk can be avoided, transferred, mitigated, or accepted.

Avoiding the risk can be accomplished in many ways. Although threats cannot be removed from the environment, one’s exposure can be altered. Not deploying a module that increases risk is one manner of risk avoidance.

Another possible action to manage risk is to transfer that risk. A common method of transferring risk is to purchase insurance. Insurance allows risk to be transferred to a third party that manages specific types of risk for multiple parties, thus reducing the individual cost. Another common example of risk transfer is the protection against fraud that consumers have on their credit cards. The risk is transferred to another party, so people can use the card in confidence.

Risk can also be mitigated through the application of controls that reduce the impact of an attack. Controls can alert operators so that the level of exposure is reduced through process intervention. When an action occurs that is outside the accepted risk profile, a second set of rules can be applied, such as calling the customer for verification before committing a transaction. Controls such as these can act to reduce the risk associated with potential high-risk operations.

In addition to mitigating risk or transferring risk, it may be acceptable for a manager to accept risk in that despite the potential cost of a given risk and its associated probability, the manager of the organization will accept responsibility for the risk if it does happen. For example, a manager may choose to allow a programmer to make “emergency” changes to a production system (in violation of good separation of duties) because the system cannot go down during a given period of time. The manager accepts that the risk that the programmer could possibly make unauthorized changes is outweighed by the high-availability requirement of that system. However, there should always be some additional controls, such as a management review or a standardized approval process, to ensure the assumed risk is adequately managed.

Understand that risk cannot be completely eliminated. A risk that remains after implementing controls is termed a residual risk. In this step, you further evaluate residual risks to identify where additional controls are required to reduce risk even more. This leads us to the earlier statement, in the chapter introduction, that the risk management process is iterative.

## The Cloud

Cloud computing is a common term used to describe computer services provided over a network. These computing services are computing, storage, applications, and services that are offered via the Internet Protocol. One of the characteristics of cloud computing is transparency to the end user. This improves usability of this form of service provisioning. Cloud computing offers much to the user: improvements in performance, scalability, flexibility, security, and reliability, among other items. These improvements are a direct result of the specific attributes associated with how cloud services are implemented. The promise of cloud computing is improved utility and is marketed under the concepts of Platform as a Service, Software as a Service, and Infrastructure as a Service. The challenge in managing risk in the cloud is in the advance determination of who has what level of security responsibility—the cloud provider, the service provider, or the user?

## Risks Associated with Cloud Computing and Virtualization

When examining a complex system such as a cloud or virtual computing environment from a risk perspective, several basic considerations always need to be observed. First, the fact that a system is either in the cloud or virtualized does not change how risk works. Risk is everywhere, and changing a system to a new environment does not change the fact that there are risks. Second, complexity can increase risk exposure. The addition of cloud and/or virtualization adds to the risk simply by adding complexity to the system.

There are specific risks associated with both virtualization and cloud environments. Having data and computing occur in environments that are not under the direct control of the data owner adds both a layer of complexity and a degree of risk. The potential for issues with confidentiality, integrity, and availability increases with the loss of direct control over the environment. The virtualization and cloud layers also present new avenues of attack into a system.

Security is a particular challenge when data and computation are handled by a remote party, as in cloud computing. The specific challenge is how to allow data outside your enterprise and yet remain in control over the use of the data. The common answer is encryption. Through the proper use of encryption of data before it leaves the enterprise, external storage can still be performed securely by properly employing cryptographic elements. The security requirements associated with confidentiality, integrity, and availability remain the responsibility of the data owner, and measures must be taken to ensure that these requirements are met, regardless of the location or usage associated with the data. Another level of protections is through the use of service level agreements (SLAs) with the cloud vendor, although these frequently cannot offer much remedy in the event of data loss.

## Virtualization

Virtualization is the creation of virtual systems rather than actual hardware and software. The separation of the hardware and software enables increased flexibility in the enterprise. On top of actual hardware, a virtualization layer enables the creation of complete systems, including computers and networking equipment, as virtual machines. This separation of hardware and software enables security through a series of improvements. The ability to copy entire systems, back them up, or move them between hardware platforms can add to the security of a system.

Although vulnerabilities exist that can possibly allow processes in one virtual environment to breach the separation between virtual environments or the layer to the host, these are rare and exceptionally difficult to exploit. A new form of vulnerability—the ability to make copies of complete virtual systems—must be addressed, as this could lead to data and intellectual property loss. Protecting the storage of virtual systems must be on par with backups of regular systems to avoid wholesale loss. Virtualized systems should be updated/patched similar to nonvirtualized systems. Virtual systems still need security services to protect virtual machines from intrusions, malware, and the same threats that regular systems face.

## Recovery Time Objective and Recovery Point Objective

The term recovery time objective (RTO) is used to describe the target time that is set for a resumption of operations after an incident. This is a period of time that is defined by the business, based on the needs of the enterprise. A shorter RTO results in higher costs because it requires greater coordination and resources. This term is commonly used in business continuity and disaster recovery operations.

Recovery point objective (RPO), a totally different concept from RTO, is the time period representing the maximum period of acceptable data loss. The RPO defines the frequency of backup operations necessary to prevent unacceptable levels of data loss. A simple example of establishing RPO is to answer the following questions: How much data can you afford to lose? How much rework is tolerable?

RTO and RPO are seemingly related but in actuality measure different things entirely. The RTO serves the purpose of defining the requirements for business continuity, while the RPO deals with backup frequency. It is possible to have an RTO of 1 day and an RPO of 1 hour, or an RTO of 1 hour and an RPO of 1 day. The determining factors are the needs of the business.

![](img/922567202a944c5e8d3ba0168d2ad3a5_139_0.png)

EXAM TIP Although recovery time objective and recovery point objective seem to be the same or similar, they are very different. The RTO serves the purpose of defining the requirements for business continuity, while the RPO deals with backup frequency.

## Chapter Review

In this chapter, you became acquainted with the principles of risk management. The chapter began by defining key terms associated with risk management. It then presented the three categories of security controls: management, technical, and operational. Next, it discussed the concepts of false positives and false negatives and how they relate to security systems.

You learned that security policies can have a direct impact on risk, and discovered the roles of policies, including the security policy, privacy policy, acceptable use policy,
