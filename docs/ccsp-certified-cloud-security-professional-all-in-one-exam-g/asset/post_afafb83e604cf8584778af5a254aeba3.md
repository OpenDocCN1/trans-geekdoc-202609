
# CCSP Certified Cloud Security Professional All-in-one Exam Guide

requirements for its protection and use. Encryption is important for many aspects of a cloud implementation. This includes the storage of data on a system, both when it is being accessed and while it is at rest, as well as the actual transmission of data between systems or between the system and a consumer. The Cloud Security Professional must ensure that appropriate encryption is selected will be strong enough to meet regulatory and system requirements, but also efficient and accessible enough for operations to seamlessly work within the application.

## Data in Transit

Data in transit is the state of data when it is actually being used by an application and is traversing systems internally or going between the client and the actual application. Whether the data is transmitted between systems within the cloud or going out to a user's client, data in transit is when data most vulnerable to exposure of unauthorized capture capture. Within a cloud hosting model, the transmission between systems is even more important than with a traditional data center due to multitenancy; the other systems within the same cloud are potential security risks and vulnerability points where data capture could happen.

In order to maintain portability and interoperability, the Cloud Security Professional should make the processes for encryption of data in transit vendor-neutral in regard to the capabilities or limitations of a specific cloud provider. The Cloud Security Professional should be involved in the planning and design of the system or application from the earliest stages to ensure that everything is built properly from the ground up, and not retrofitted after design or implementation has been completed. Whereas the use of encryption with the operations of the system is crucial during the design phase, the proper management of keys, protocols, and testing/auditing are crucial once a system has been implemented and deployed.

The common method for data-in-transit encryption is to use the well-known SSL and TLS technologies over HTTPS. With many applications utilizing web services as the framework for communications, this has become the prevailing method, which is the same method used by clients and browsers to communicate with servers over the Internet. This method is now being used within server-to-server internal communication within cloud environments for methods for data in transit are VPNs (virtual private networks) and IPsec. These methods can be used by themselves but are most commonly used in parallel to provide the highest level of protection possible.

> NOTE: Over time, many versions of SSL and TLS have been declared unsafe or compromised. This also applies to specific encryption ciphers used by SSL and TLS. As a Cloud Security Professional, it is very important to stay on top of this matter, especially if SSL and TLS are provided on behalf of the cloud provider. Regulatory bodies as well as industry certification groups will often dictate the disabling of ciphers that are no longer considered safe or sufficient, so this one area to always stay abreast of developments and news.

![](img/44bc0d6508f04646c7c3b07267095e71_58_0.png)

## Chapter 2: Architectural Concepts and Design Requirements

## Data at Rest

Data at rest refers to information stored on a system or device (versus data that is actively being transmitted across a network or between systems). The data can be stored in many different forms to fit within this category. Some examples include databases, file sets, spreadsheets, documents, archives, and even mobile devices.

Data residing on a system is potentially exposed and vulnerable for longer than short transmission and transaction operations would be, so special care is needed to ensure its protection from unauthorized access. With transactions and data in transit, a small subset of records or even a single record is transmitted at any time, the comprehensive record sets maintained in databases and other file systems.

While encrypting data is central to the confidentiality of any system, the availability and performance of data are equally important. The Cloud Security Professional must ensure that encryption provides high levels of security and protection and do so in a manner that facilitates high performance and system speed. Any use of encryption will cause higher load and processing times, so proper scaling and evaluation of systems are critical when testing deployments and design criteria.

With portability and vendor lock-in considerations, it is important for a Cloud Security Professional to ensure that encryption systems do not effectively cause a system to be bound to a proprietary offering. If a system or application using a proprietary encryption system from a cloud provider, portability will likely be more difficult and tie to that particular provider. With many implementations spanning multiple cloud providers and infrastructures for disaster recovery and continuity planning, having encryption systems that can maintain consistency and performance is important.

## Key Management

With any encryption system, a method is needed to properly issue, maintain, and organize. If a customer has their own key management systems and procedures, they can ensure their own data security, as well as preventing "locked in" with a cloud provider and the systems they provide, which may be proprietary in nature. Beyond the vendor lock-in that can occur with using a key management system from the cloud provider, your keys are also being managed within a system that contains similar keys for other systems. A customer that controls of their own key management systems ensures a higher degree of portability and segregation of systems for security.

Two key management services (KMS) are commonly used: remote and client-side.

### Remote Key Management

Remote key service is maintained by the cloud provider. This allows for seamless integration with the cloud environment, but also allows for all generation and maintenance. The main drawback to a remote KMS is that connectivity will have to be open for downtime, either accidental or by design, this introduces the potential for

![](img/44bc0d6508f04646c7c3b07267095e71_59_0.png)

### Client-Side Key Management

Most common with SaaS implementations, client-side KMS is hosted and controlled by the customer. This allows for seamless integration with the cloud environment, but the customer is fully responsible for all generation and maintenance.

## Access Control

Access control combines the two main concepts of authentication and authorization, but adds a third concept of accounting as well. With authentication, a person or system verifies who they are, and with authorization they acquire the appropriate system rights they should have based on their role. Access involves maintaining the logs and records of authentication and authorization, for both operational and regulatory needs.

Access control systems have a variety of different types of authentication mechanisms that provide increasing levels of security based on the type of data sensitivity. On the low end, this could involve the use of a user ID and password, which everyone is familiar with in regard to typical access. For higher levels of security, systems should use multiple factors of authentication in combination. This will typically be a combination of the classic user ID and password with an additional requirement such as physical presence. Types of secondary factors typically include biometric tests (fingerprints and retina scans), a physical token device that is plugged into a computer and read by the system, and the use of a mobile device or callback feature, where the user is provided with a code to input in addition to their password. There are many other types of secondary authentication methods, but the ones mentioned above are the most common. Physical secondary types of authentication can also be layered in combination; for example, the user could have to provide a retina scan as well as a physical token device.

The main areas of access management concerns are described in the following sections.

## Account Provisioning

Before any access can be granted and roles determined, accounts must be created on the system that will form the basis of access. At this stage, the most crucial aspect for an organization is the validation of users and verification of their credentials to allow accounts for the system. It is incumbent on an organization and their security policies and practices to determine the appropriate level of proof required to verify a new user and identity credentials. This can be based solely on the policies of the organization, or it can include extensive additional processes based on contractual, legal, or regulatory requirements. A prime example would be government contracts, where specific documentation for verification must be submitted to authorities outside of
