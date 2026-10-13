
# Chapter 11: Disaster Recovery and Business Continuity

## Introduction

A disaster can be defined as an event that creates disruptions in the operation of the organization's processes that adversely affect its productivity and profitability and require recovery efforts to correct. Organizations must be able to continue operations despite all types of small emergencies and large disasters to ensure the health and continuation of the organization.

Modern enterprises are so dependent on their communications infrastructure that “the network” is one of the most important components of any organization's continuity plan. Lost data translates into system downtime, wasted production, customer dissatisfaction, and a reduction in company earnings.

Although preventive measures are always the preferred tool to use against possible disasters, they cannot guarantee that system recovery will never be necessary. Therefore, a disaster recovery process should be designed to restore all or part of the organization's network in the event of a critical failure caused by accident, theft, intentional sabotage, or a naturally occurring disaster.

As mentioned in [Chapter 8](#c08.xhtml), “ICS Security Governance and Risk Management,” organizations rely on three interrelated types of plans to contend with these possibilities: the *incident response plan* (*IRP*), the *business continuity plan* (*BCP*), and the *disaster recovery plan* (*DRP*). These plans typically share overlapping functions, but they are different. The *BCP* is designed to anticipate and offer guidance for key components, objectives, and processes for continued operations during an interruption of the organization's business flow. As such, it is not triggered into action so much as it is referenced when an interruption or disaster occurs. The *DRP* is typically activated when a loss of operations or data has occurred. The *IRP* is triggered when an incident or potential incident has been detected or reported. Knowing what each plan is designed to do, how it is related to the other two plans, and when to trigger each one are key to effectively securing the operations and functions of the organization.

The *IRP* was introduced in [Chapter 8](#c08.xhtml) and covered in detail in [Chapter 10](#c10.xhtml), “ICS Security Monitoring and Incident Response.” In this chapter, the focus will shift to address the purposes and functions of the business continuity plan and the disaster recovery plan.

## Business Continuity Plans

A business continuity plan is a document designed to describe the organization's preparation, growth plans, and future planning in case either type of damaging event occurs.

The *BCP* is designed to be the overriding plan that guides the design and implementation of the other plans. As such, it will have linkage to both the incident response and disaster recovery plans.

The top of the *BCP* attempts to identify the critical business functions and must provide processes and procedures for responding to and recovering from business interruptions due to occurrences pointed out by the organization's risk analysis and business impact assessment and analysis to provide for the most cost-effective continuance of their operations. The *BCP* is applied to every internal business unit throughout the organization, as well as its outside vendors. As you may be able to imagine, plans created at this level of the organization are developed by executive teams.

Another function of the *BCP* is to attempt to identify all the possible disaster scenarios that could hamper or stop the organization’s various business functions. This typically includes items such as potential natural disasters, loss of utilities (such as electrical power or network resources), or manmade interruptions (such as hacker or terrorist activities).

Along with the *DRP*, a solid *BCP* includes a risk analysis, a business impact analysis, plan maintenance, training, and integration processes, as well as validation of the plan. These items are usually created by the organization's enterprise resource planning (*ERP*) or information security (*infosec*) teams. For a *BCP* to be successful, it is critical that it has the endorsement of upper management.

### System Redundancy

*Redundancy* is the practice of devoting additional hardware to maintain system and network resources. By adding additional devices, components that represent single points of failure can be removed from operation. A *point of failure* is any element in the network that if it fails, a critical process shuts down. An example of a *point of failure* would be if the only data historian in the *OT* network were to fail. In this case, the organization would be unable to record production data until the data historian function was restored.

*System redundancy* is the process of creating parallel systems in the operation to provide alternative pathways for continuing the organization's operation. Creating this type of redundancy typically involves providing secure recovery through alternate sites, installing high-availability fault-tolerant network resources, and implementing data backup systems and methods to provide a redundant source of data.

#### Alternate Sites

Creating and maintaining alternative sites for redundancy purposes runs at the top end of the *BCP* redundancy options. Establishing an alternate site enables the organization to temporarily continue operations during a major disaster and throughout the recovery period. After the disaster is over, the organization may be able to return operations to their main site. As operations are being reestablished at the primary site, start with the least critical process. It may be necessary to temporarily work out of two sites until the primary site is completely restored.

Alternate sites are facilities that can be used in cases of disaster:

*   Hot sites
*   Warm sites
*   Cold sites
*   Cloud sites
