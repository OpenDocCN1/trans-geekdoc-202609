
## Interoperability

With the concern over vendor lock-in, interoperability is a primary consideration. Interoperability creates the ability to communicate with and share data across multiple platforms and between traditional and cloud services provided by different vendors. Avoiding vendor lock-in allows the customer to make decisions based on the cost, feature set, or availability of a particular service regardless of the vendor providing the service. Interoperability leads to a richer set of alternatives and more choices in pricing.

## Portability

Portability may refer to data portability or architecture portability. Data portability is focused on the ability to move data between traditional and cloud services or between different cloud services without having to port the data under challenging and lossy methods or significant changes to either service or the loss of metadata.

Data portability matters to an organization that uses a multicloud approach, as data moves between vendors. Each move cannot create a data porting exercise, or it is not seamless or useful. It is also important in a cloud bursting scenario, where peak usage expands into a cloud environment and then shrinks back to its original noncloud size. This must be seamless to make the strategy useful. Data backups are increasingly to the cloud, and a restore to in-house servers must be handled easily.

Architecture portability is concerned with the ability to access and run a cloud service from a wide variety of devices, running different operating systems. This allows users on a Windows laptop and a MacBook Pro to use the same application services, share the same data, and collaborate easily.

## Reversibility

Reversibility is a measure of the extent to which your cloud services can be moved from one cloud environment to another. This includes moving between a cloud environment and an on-premise traditional environment. The movement between environments must be simple and automatic. Companies now move to and from the cloud and between clouds in a multicloud environment and when cloud bursting.

The movement between environments needs to be secure or the movement is not simple nor low cost. Reversibility also decreases vendor lock-in as solutions need to be able to move between CSPs and to and from the cloud. It will become important as application software and data will eventually reside in different locations and the mature cloud environment will not care.

## Availability

Availability has two components. The first is one leg of the CIA triad. Within the constraints of the agreed-upon SLA, the purchased services and company or individual data must be made available to the customer by the CSP. If the SLA is not met, the contract will spell out the penalties or recourses available. In this example, if a customer has paid for Dropbox, but when they try to access the service, it is not available, the service availability fails. If this failure is not within the requirements of the SLA, the customer has a claim against the service provider.

The second component of availability is concerned with the elasticity and scalability of the cloud service. If the CSP has not properly planned for expansion, a customer may need to grow their use of the contracted service, and the resources may not be available. Consider a service like Dropbox. If the customer pays for 2TB of storage and it is not available, when they need it, the service fails in terms of availability, even if access to files already stored with the service continues to be provided.

## Security

Cloud security is a challenging endeavor. It is true that the larger CSPs spend resources and focus on creating a secure environment. It is equally true that a large CSP is a large target, and there are aspects of cloud computing, such as multitenancy, that create new complexities to security.

One issue that is part of various national laws such as the European Union’s General Data Protection Regulation is the restriction on cross-border transfers of data. In an environment where the actual hardware could be anywhere, it is an important consideration to know where your data resides. When there are law enforcement issues, location of the data may also be a jurisdictional challenge.

The owner of data remains ultimately responsible for the security of the data, regardless of what cloud or noncloud services are used. Cloud security involves more than protection of the data but includes the applications and infrastructure.

## Privacy

The involvement of third-party providers, in an off-premises situation, creates challenges to data protection and privacy. The end user cannot always determine what controls are in place to protect the privacy of their data and must rely on privacy practice documents and other reports to determine if they trust the third party to protect their data privacy.

Privacy concerns include access to data both during a contract and at the end of a contract as well as the erasure or destruction of data when requested or as required within the contract. Regulatory and contractual requirements such as HIPAA and PCI are also key concerns. Monitoring and logging of data access and modification, and the location of data storage, are additional privacy concerns.

## Resiliency

Resilience is the ability to continue operating under adverse or unexpected conditions. This involves both business continuity and disaster recovery planning and implementation. Business continuity might dictate that a customer stores their data in multiple regions so that a service interruption in one region does not prevent continued operations.

The cloud also provides resiliency when a customer suffers a severe incident such as weather, facilities damage, terrorism, civil unrest, or similar events. A cloud strategy allows the company to continue to operate during and after these incidents. The plan may require movement of personnel or contracting personnel at a new location. The cloud strategy handles the data and processes as these remain available anywhere network connectivity exists.

Major CSPs use multiple regions and redundancy to increase the ability of a recovery. Many organizations plan a resilient strategy that includes internal resources and the capabilities of the cloud.

## Performance

Performance is measured through an SLA. Performance of a cloud service is generally quite high as major CSPs build redundancy into their systems. The major performance concerns are network availability and bandwidth. A network is a hard requirement of a cloud service, and if the network is down, the service is unavailable. In addition, if you are in an area of limited bandwidth, performance will be impacted.

## Governance

Cloud governance uses the same mechanisms as governance of your on-premises IT solutions. This includes policies, procedures, and controls. Controls include encryption, access control lists (ACLs), and identity and access management. As many organizations have cloud services from multiple vendors, a cloud governance framework and application can make the maintenance and automation of cloud governance manageable. This may be another cloud solution.

A variety of governance solutions, some cloud-based, exist to support this need. Without governance, cloud solutions can easily grow beyond what can be easily managed. For example, a company may want to govern the number of CSP accounts, the number of server instances, the amount of storage utilized, the size of databases, and other storage tools. Each of these adds to the cost of cloud computing. A tool that tracks usage and associated costs will help an organization use the cloud efficiently and keep its use under budget.

## Maintenance and Versioning

Maintenance and versioning in a cloud environment have some advantages and disadvantages. Each party is responsible for the maintenance and versioning of their portion of the cloud stack. In a SaaS solution, the maintenance and versioning of all parts is the responsibility of the CSP, from the hardware to the SaaS solution. In a PaaS solution, the customer is responsible for the maintenance and versioning of the applications they acquire and develop. The platform and tools provided by the platforms, as well as the underlying infrastructure, are the responsibility of the CSP. In an IaaS solution, the CSP is responsible for maintenance and versioning of hardware, network and storage, and the virtualization software. The remainder of the maintenance and versioning is the responsibility of the customer.

What this means in practical terms is that updates and patches in a SaaS or PaaS environment may occur without the knowledge of the customer. If properly tested before being deployed, it will also be unnoticed by the customer. There remains the potential for something to break when an update or patch occurs, as it is impossible to test every possible variation that may exist in the cloud environment of the customers. This is true in a traditional on-premise environment as well. In an IaaS environment, the customer has much more control over patch and update testing and deployment.

On the positive side, there will not be the endpoints that exist in every organization that never get updated and have older, insecure versions of potentially unlicensed software. When connecting to the cloud service, the customer will always be using the newest, most secure version of the solution in a SaaS solution.

In a PaaS or IaaS, the customer is responsible for some of the maintenance and versioning. However, each customer that connects to the PaaS and IaaS environment will be accessing the most current version provided. The maintenance and versioning are simplified by restricting the maintenance and versioning to the cloud environment. It is not necessary to update each endpoint running a particular piece of software. Everyone connecting to the cloud is running the same version, even if it is old and has not been updated.
