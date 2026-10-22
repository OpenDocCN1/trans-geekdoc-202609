
- What level of additional administrative overhead will the features create?
- Consolidating management of multiple security functions does not necessarily make them easier to manage. This also adds complexity depending how each subsystem integrates.

## 26.8.6 Management.

GSDs typically require substantial planning, configuration, monitoring, and maintenance. Having a robust management platform in distributed GSD environments is essential to the success of the implementation.

- Does the current environment have the management features needed or required?
- Self-evaluation of the current management environment is fairly easy, as there are already established likes, dislikes, nice-to-haves, must-haves, and must-nots.
- Is there the need/want for distributed or centralized management?
- The size and type of GSD deployment is important to consider. It probably does not make sense to use an extensive management platform for a few devices. With larger geographically distributed environments, having centralized control of all devices is necessary for efficient and effective command and control.
- Are redundant management systems needed?
- Redundant management systems ensure administrative control and logging of GSD devices in the case of a failure. Be sure to review management systems redundancy options to ensure the secondary system has functional parity.
- Is the ability to manage the system from both a centralized management console and/or directly from the device a necessity?
- Certain types of GSDs allow system and policy changes to be made directly from the device. This feature can be useful during testing or troubleshooting but may cause confusion or misconfiguration if not properly understood and managed.
- Is encryption a requirement to protect management, policy, and logging functions?
- The need to encrypt sensitive information is an important consideration for transmission of GSD management and logging functions. If sent clear-text, it is possible for someone to monitor these communications and gain significant intelligence about the network security architecture.
- Is detailed reporting mechanism a necessity?
- Most logging systems provide the ability to filter data, but it may be useful to do more in-depth reporting. Some example reports include rule base hit percentages (e.g., which rules receive the highest percentage of hits) or traffic usage statistics (e.g., percent usage by protocol, network segment, host, and/or user).
- What level of granularity is necessary for management permissions?
- With only a few administrators, this may not be as significant, but larger deployments may have distributed administrators. The GSD management system must provide role-based security with the ability to restrict access to certain tasks, areas, and/or logs. It may be useful to compartmentalize the systems and allow other support teams view-only access for troubleshooting and auditing purposes.

- Do you need out-of-band access?
- Having an out-of-band access solution such as a direct serial connection and/or dial-in solution may provide the ability to monitor and/or change the system during the network outage.

## 26.8.10 Usability.

Having a management environment that has every feature imaginable is worthless if it is too complex and convoluted to operate and maintain.

- Is the management console intuitive?
- The management console should have a consistent and simple interface to manage the devices and policies. The more intuitive the interface, the less time the administrators will need to spend figuring out how to complete otherwise easy tasks or troubleshooting issues.
- Are the primary functions easy to accomplish?
- The interface should make it easy to follow and edit policies as well as view and filter logs.

## 26.8.11 Learning Curve.

By choosing a GSD vendor with an intuitive interface and functionality, it should be much easier to learn the environment.

- Is training required to learn the new device(s) and management platform?
- Even with the best interface and features, it may be necessary for the administrator(s) to get training to use the system effectively. Check with the vendor to see what training (basic through advanced) is available and at what cost. If possible, determine the effectiveness of the instructor(s) through referrals.
- If some of the security features are new to the organization, expect a steeper initial and increased ongoing learning curve due to the breadth and depth for each additional protection measure.
- How does the vendor approach security architecture?
- Every GSD vendor has a little different view and implementation of security features. Some focus primarily on allowing or denying traffic, although others treat network traffic as flows between zones. Moving from one vendor type to another can be confusing and could slow or confuse the conversion.

## 26.8.12 Features.

Although the GSD platform may be able to provide a single source for network-security protections, it is important to remember that it may not be cost or resource effective to meet the organization’s security needs and posture.

- Are you looking for a device to be an all-in-one solution?
- The ability to provide a single solution security platform has merits, but each additional feature has an impact on performance and availability, and when implemented improperly, increases the potential to cause issues.
- What features do you want the GSD to have?
- Common UTM features may include firewall, IPS, VPN, anti-malware, anti-spam, DLP, and Quality of Service (QoS).
- Common NGFW features include port-independent application identification and enforcement for sub-features of a particular protocol.
- Does the platform support full IPv6 enforcement across all security functions?

## 26.8.13 Price.

Be sure to understand the cost implications of the entire GSD infrastructure over its lifetime.

- What will be the total cost of ownership (TCO) of the upgrade or replacement?
- Areas for considerations include: hardware purchase price; price for requested security features (additional features, if added later, will increase the overall costs and may require new hardware); management infrastructure (hardware and software); hardware and software maintenance fees; training costs; direct or third-party support contract; potential conversion downtime; and learning curve.

### Initial Cost

- How much will the new GSD equipment cost?
- This includes the price of the GSD, expansion cards, and management devices.
- An appliance may be a more cost-effective alternative long term if there are multiple deployment options as the vendor is solely responsible for issues.
- How much extra will shipping cost?
- If this is a distributed deployment, there may be extra shipping costs and tariffs associated with getting the equipment to international locations.
- How much will it cost to purchase the features I need?
- This is highly dependent on the GSD. Certain GSDs come with everything out of the box, while others provide some basic functionality including the firewall, VPN, and basic protocol inspection but charge extra to use the full functionality of the existing items and/or to add new functionality.
- How much is it necessary to invest in training to learn the new solution?
- Training often includes attending offsite courses (which may require additional travel expenses). In some cases, it may be more cost effective to bring a trainer in-house to provide a more tailored training program. A train-the-trainer methodology can be a money-saving option, depending on team size and funding.

### Ongoing Costs

- How much is the yearly hardware and/or software maintenance?
- The maintenance contract may be negotiable based on length of term and costs (potentially based on a percentage of the purchase).
- What level of service do you require?
- GSD vendors provide different service levels to correspond with response times, escalation ability, and access to additional information. In accordance, the higher level of service, the more this will cost.
- Can the provider support you at each of your locations?
- If necessary, major issues may require a vendor or vendor partner to come onsite to complete a repair. If available, determine the cost (time and travel) before using this type of service.
- If you have international deployments, be sure to understand the vendor's ability to provide general warranty repair and/or onsite service for those locations.
