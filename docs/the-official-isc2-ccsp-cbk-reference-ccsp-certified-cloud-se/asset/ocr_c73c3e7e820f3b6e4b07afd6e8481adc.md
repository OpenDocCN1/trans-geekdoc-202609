# Interoperability

With customers using a variety of cloud services, often from different vendors, interoperability is an important consideration. In addition, some situations may require a private cloud sharing data with an on-premises solution. The ability to share data between tools and cloud environments and between clouds and corporate infrastructure is important. One issue is that the security tools and control sets differ between CSPs. A gap in security may result. Careful planning is essential, and the services of a cloud broker may also be warranted.

One way to improve the situation is through application programming interfaces (APIs). If properly designed, the API can bridge the security gap between services and allow the sharing of data and processes across multiple platforms. For example, if a SaaS tool is used to build a data inventory and supports the corporate data/system classification scheme, an API could be built to securely share that information with the governance, risk management, and compliance (GRC) or system inventory tool. This creates a single source for data, sharing it with relevant systems, and removes the potential of multiple data classification in different systems.

# Vendor Lock-in

Solving the interoperability and portability challenges will go a long way toward ending vendor lock-in. This occurs when a customer is tied to a specific CSP and moving would incur significant costs including financial, technical, and legal. Vendor lock-in remains a significant concern with cloud computing. Continued advances in virtualization, improvements in portability and interoperability, and a careful design within a reference architecture have decreased this issue.

An additional concern is the use of CSP-specific services. If these are used to build capabilities, moving to a new CSP also impacts this additional capability. This is similar to using nonstandard features of a compiler in the development process. It locks you into that development environment.

One example is the use of AWS CloudTrail. CloudTrail allows auditing of your AWS account in support of governance, risk management, and compliance. If the decision is made to move away from AWS, the GRC functionality will have to be rebuilt with new services, either with the new CSP or with another vendor.

With additional improvements and careful architecture, vendor lock-in should become an issue in the past. Until then, the security challenges of cloud computing in general, and portability and interoperability in particular, remain.

# Security Considerations for Different Cloud Categories

In a cloud environment, security responsibilities are shared between the service provider and the customer. In the SaaS model, the customer has the least responsibility, and in