
- **Validation** – The change is validated by the operations staff to ensure that the intended machines received the deployment package. The security staff performs a security scan or review of the affected machines to ensure that new vulnerabilities are not introduced. Changes should be included in the problem tracking system until operations has ensured that no problems have been introduced.
- **Documentation** – The outcome of the system change, to include system modifications and lessons learned, should be recorded in the appropriate records. This is the way that change management typically interfaces with configuration management.

## Configuration Management

Organizational hardware and software require proper tracking, implementation testing, approvals, and distribution methods. Configuration management is a process of identifying and documenting hardware components, software, and the associated settings. A well-documented environment provides a foundation for sound operations management by ensuring that IT resources are properly deployed and managed. The security professional plays an important role in configuration management through the identification and remediation of control gaps in current configurations.

Detailed hardware inventories are necessary for recovery and integrity purposes. Having an inventory of each workstation, server, and networking device is necessary for replacement purposes in the event of facility destruction. All devices and systems connected to the network should be in the hardware list. At a minimum, configuration documentation should include in the hardware list the following information about each device and system:

- 1. Make
- 2. Model
- 3. MAC addresses
- 4. Serial number
- 5. Operating system or firmware version
- 6. Location
- 7. BIOS and other hardware-related passwords
- 8. Assigned IP address if applicable
- 9. Organizational property management label or bar code

Software is a similar concern, and a software inventory should minimally include:

- 1. Software name
- 2. Software vendor (and reseller if appropriate)
- 3. Keys or activation codes (note if there are hardware keys)
- 4. Type of license and for what version
- 5. Number of licenses
- 6. License expiration
- 7. License portability
- 8. Organizational software librarian or asset manager
- 9. Organizational contact for installed software
- 10. Upgrade, full or limited license

The inventory is also helpful for integrity purposes when attempting to validate systems, software, and devices on the network. Knowing the hardware versions of network components is valuable from two perspectives. First, the security professional will be able to quickly find and mitigate vulnerabilities related to the hardware type and version. Most hardware vulnerabilities are associated with a particular brand and model of hardware. Knowing the type of hardware and its location within the network can substantially reduce the effort necessary to identify the affected devices. Additionally, the list is invaluable when performing a network scan to discover unauthorized devices connected to the network. A new device appearing on a previously documented network segment may indicate an unauthorized connection to the network.

A configuration list for each device should also be maintained. Devices such as firewalls, routers, and switches can have hundreds or thousands of configuration possibilities. It is necessary to properly record and track the changes to these configurations to provide assurance for network integrity and availability. These configurations should also be periodically checked to make sure that unauthorized changes have not occurred.

Operating systems and applications also require configuration management. Organizations should have configuration guides and standards for each operating system and application implementation. System and application configuration should be standardized to the greatest extent possible to reduce the number of issues that may be encountered during integration testing. Software configurations and their changes should be documented and tracked with the assistance of the security practitioner. It is possible that server and workstation configuration guides will change frequently due to changes in the software baseline.

## Develop a Recovery Strategy

Recovery strategies are driven by the recovery time frame required by the function or application to be recovered. Some strategies the security professional may consider for organization operations are as follows:

- **Surviving Site** — A surviving site strategy is implemented so that while service levels may drop, a function never ceases to be performed because it operates in at least two geographically dispersed buildings that are fully equipped and staffed.
- **Self-Service** — An organization can transfer work to another of its own locations, which has available facilities and/or staff to manage the time sensitive workload until the interruption is over.
- **Internal Arrangement** — Training rooms, cafeterias, conference rooms, etc. may be equipped to support organization functions while staff from the impacted site travels to another site and resumes organization.
- **Reciprocal Agreements/Mutual Aid Agreements** — Other similar organizations may be able to accommodate those affected. For example, one law firm may be able to provide office space to another in the event of an outage. This could involve the temporary suspension of non-time sensitive functions at the organization operations not affected by the outage.
- **Dedicated Alternate Sites** — Built by the company to accommodate organization function or technology recovery.
- **Work from Home** — Many organizations today have the capability to have employees work from locations that are remote from a physical office environment.
- **External Suppliers** — A number of external organizations offer facilities covering a wide range of organization recovery needs from full data centers with a wide range of platforms, alternate site space in physical facilities, mobile units that can be transported to the company site, and temporary staff to provide services when the employees cannot.
- **No Arrangement** — For low-priority business functions or applications, it may not be cost justified to plan at a detailed level. The minimum requirement would be to record a description of the functions, the maximum allowable lapse time for recovery, and a list of the resources required.

Each of these strategies can be considered for the organization and technology recovery. Those that are recommended need to have a cost/benefit analysis (CBA) performed to determine if the costs of the strategy being recommended fits within the amount of risk or loss the organization is trying to avoid. The company should not spend $1,000,000 a year on a recovery strategy to protect $100,000 of income. Every organization does not need a dual data center recovery strategy. The strategy selected must fit the organizational need.

The cost of implementing the recovery strategy recommended needs to include the initial costs associated with building out the strategy as well as ongoing costs to maintain the recovery solution, and where applicable, the cost of periodic testing of the solution to ensure it remains viable, as well as the costs associated with communication, to ensure that all users in the organization are aware of the plans.

Once the strategy has been agreed to and funded, the security professional must then implement the various strategies approved. This may involve negotiating with vendors to provide recovery services for organization or technology, doing site surveys of existing sites to determine excess capacity, wiring conference rooms or cafeterias to support organization functions, buying recovery technology, installing remote replication software, installing networks for voice and data recovery, assigning alternate site seats to the various organization areas, and the like. The security professional also needs to ensure that communication systems are in place to allow the organization to be able to reach all employees during and immediately after an event and to allow for on-going information and status updates to be disseminated to the employees throughout the duration of an event.

## Implement a Backup Storage Strategy

Backup strategies for data used to restore technology are varied and are driven by the Recovery Time Objective (RTO) and the Recovery Point Objective (RPO) needed to support the organizational requirements. Some organizations have begun tiering data based on its importance to the organization and frequency of use. The more time sensitive data is replicated offsite either synchronously or asynchronously to ensure its availability and its currency. Other data is backed up to tape and sent offsite once or more a day.

If the backup tapes are stored somewhere else besides an alternate site, then the time it takes to pack and transport those tapes must be included in the RTO. Depending on how many tapes are required, this could increase the time to recovery by hours or even days. To reduce the recovery time from 3 to 5 days minimum to 24 hours or less,
