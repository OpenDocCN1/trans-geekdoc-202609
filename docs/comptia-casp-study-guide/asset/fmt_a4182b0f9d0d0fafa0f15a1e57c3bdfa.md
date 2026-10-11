
## Over-the-Air Updates

In addition to managing configuration settings remotely, the team responsible for installing updates can do this remotely. This delivery, known as *over-the-air (OTA) updates*, avoids waiting for a user to come in or dock their device for the update. Software or the device's firmware can be updated in this way.

## Remote Wiping

Another process that a CASP+ might need to do without relying on the user being “in the building” is remotely wiping the device. For example, as part of the process of a termination, also known as *offboarding*, an employee's device could be remotely wiped, mitigating the risk of unauthorized device usage or abuse.

## Mobile Device Concerns

In the context of mobile devices, here are some concerns of which the CASP+ should be aware:

### SCEP

The *Simple Certificate Enrollment Protocol (SCEP)* is a popular method of certificate enrollment, which is the process of a user or device requesting and receiving a digital certificate. SCEP is highly scalable and widely implemented. However, its original designers went on hiatus for several years, and SCEP received little attention to address concerns about its cryptographic strength. According to CERT vulnerability note VU#971035, the authentication methods for SCEP to validate certificate requests are ill suited for any environment other than a closed one. So, any mobility device management (MDM) involving BYOD opens itself up to risks of unauthorized certificate requests.

### Unsigned Apps/System Apps

The concept of code signing is designed to ensure that an application developed by a third party has not been altered or corrupted since it was signed as valid. Of course, this matters when the original developer is assumed to be a trusted source. However, what about apps that are not signed? If a user is able to download and install unsigned applications and unsigned system apps, the mobile device is no longer assured to be trustworthy.

### Sideloading

Normally, when loading or installing an application, a user would use the device's application-distribution channel. For most devices, this would mean using Google Play or the Apple App Store. But if a user seeks an alternate, back-channel method to load an application that may not be accessible otherwise, that method is called sideloading. Naturally, the security concern for a CASP+ is why such an application requires sideloading and is not available through the normally vetted channel. *Sideloading*, or loading applications outside a controlled channel, means that the established process of inspecting an application for malicious code is likely being bypassed.

### Context-Aware Management

Security restrictions on mobile devices can be placed in keeping with a user's behavior or their local location. Just as straightforward as the position of a mobile device, time-based restrictions can be placed on a user's access and/or authorization. If the user is attempting to access a sensitive share directory after restricted hours, employing time-based restrictions means limiting access until the permissible time period.

## Outsourcing and Contracting

Organizations should go through a source strategy to determine what tasks should be completed by employees, contractors, or third parties. Outsourcing is one common approach. *Outsourcing* can be defined as an arrangement in which one company provides services for another company that may or may not have been provided in house. Outsourcing has become a much bigger issue in the emerging global economy, and it is something security professionals need to review closely. There will always be concerns when ensuring that third-party providers have the requisite levels of information security.

Outsourcing has become much more common in the IT field throughout the course of the last decade or so. In some cases, the entire information management function of a company is outsourced, including planning and business analysis as well as the installation, management, and servicing of the network and workstations. The following services are commonly outsourced:

*   Application/web hosting
*   Check processing
*   Computer help desk
*   Credit card processing
*   Data entry
*   Payroll and check processing

Crucial to the outsourcing decision is determining whether a task is part of the organization's core competency or proficiency that defines the organization. Security should play a large role in making the decision to outsource because some tasks take on a much greater risk if performed by someone outside the organization.

During any technical deployment, IT security professionals should have a chance to review outsourcing, insourcing, managed services, and security controls and practices of a partnered company. If irregularities are found, they should be reported to management so that expenses and concerns can be properly identified. Before combining or separating systems, a CASP+ should ask these basic questions:

*   Who has access to resources?
*   What types of access will be provided?
*   How will users request access?
*   Who will grant users access?
*   What type of access logs will be used, what will be recorded, and when will it be reviewed?
*   What procedures will be taken for inappropriate use of resources?
*   How will security incidents be reported and recorded, and who will handle them?
*   Who will be responsible for investigating suspicious activity?

The CASP+ should also be concerned with developing a course of action that is based on informed business decisions with the goal to provide for long-term security. Here are some of the technical deployment models with which a CASP+ should be familiar:

### Outsourcing

Outsourcing can be defined as obtaining a resource or item from an outside provider. As an example, consider Dell. Dell might be based in Round Rock, Texas, yet its distribution hub is in Memphis, Tennessee. Further, Dell assembles PCs in Malaysia and has customer support in India. Many parts come from the far corners of the globe.

### Insourcing

Insourcing can be defined as using a company's own personnel to build an item or resource or to perform an activity.

### Managed Services

Some organizations use managed services. One common approach is to use managed cloud services. Managed cloud hosting delivers services over long periods of time, such as months or even years. The secure use of cloud computing is contingent upon your organization reviewing the cloud provider's policies. In such situations you may be purchasing services in time slices or as a service on a virtual server. This means that data aggregation and data isolation can occur.

The security concern with data aggregation is that your data may be combined with others or may even be reused. For example, some nonprofit donor databases offer their databases for free yet combine your donor database with others and resell it. Data isolation should be used to address how your data is stored. Is your data stored on an isolated hard drive, or does it share virtual space with many other companies?

Finally, it is important to discuss the issues of data ownership and data sovereignty with the managed service provider. Make sure that your data remains solely yours while in the custody of the managed service provider. As the volume of data grows, also ensure that the managed service provider maintains the same level of assurance.

## Resource Provisioning and Deprovisioning

Resource provisioning and deprovisioning should be examined before a technical deployment in order to understand how resources are handled. For example, is the hard drive holding your data destroyed, or is it simply reused for another client? How about users? Are their records destroyed and accounts suspended after they are terminated?

In addition to users, resource provisioning and deprovisioning can also include the following:

*   Servers
*   Virtual devices
*   Applications
*   Data remnants
