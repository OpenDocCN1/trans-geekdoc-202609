
underlying infrastructure costs. It provides a development sandbox at a lower cost than doing it all in-house.

## Infrastructure Capability Types
An infrastructure customer cannot control the underlying hardware but has control over the operating system, installed tools, solutions installed, and provisioning of infrastructure compute, storage, and network and other computing resources.

This capability provides the customer with the ability to spin up an environment quickly. The environment may be needed for only hours or days. The parent organization does not have to purchase the hardware or physical space for this infrastructure or pay for its setup and continuing maintenance for usage spikes, temporary needs, or even regular cycles of use.

## Cloud Service Categories
There are three primary cloud service categories: SaaS, PaaS, and IaaS. In addition, other service categories are sometimes suggested, such as storage as a service (STaaS), database as a service (DBaaS), and even everything as a service (XaaS). However, these can be described in terms of the three basic types and have not caught on in common usage. They are most often used in marketing.

Security of systems and data is a shared responsibility between the customer and service provider. The point at which responsibilities of the service provider end and the responsibilities of the customer begin depends on the service category.

When talking about SaaS, PaaS, or IaaS solutions, we must know which service model is being discussed. Each is discussed in some detail next. Which model you are referring to is in part determined by where in the process you are.

If you are an end user, you are likely using a SaaS solution. If you are a developer, you may be offering a SaaS solution you developed in-house or through the use of a PaaS development environment. It is possible that the cloud service you provide is a development environment, so you offer a PaaS service you built on an IaaS service. Some customers work at all three levels. They use an IaaS service to build a development environment to create a SaaS solution. In each case, the security responsibilities are shared, as described elsewhere, by the customer and the CSP. However, that shared responsibility can become rather complex if the customer uses multiple services at differing service levels.

### Software as a Service
SaaS is the most common cloud service that most people have experience with. This is where we find the end user, which at times is each of us. If you have shared a file through Google Docs, stored a file on Dropbox, signed a document using DocuSign, or created a document with Office 365, you have used a SaaS solution. They are usually subscription-based services and are easy to set up and use. Corporations often negotiate and purchase a site license. The amount of control over security will vary by the CSP and the size of the contract.

### Platform as a Service
PaaS is the domain of developers. With a PaaS solution, the service provider is responsible for infrastructure, networking, virtualization, compute, storage, and operating systems. Everything built on top of that is the responsibility of the developer and their organization. Many PaaS service providers offer tools that may be used by the developers to create their own applications. How these tools are used and configured are the responsibility of the developers and their organizations.

With a PaaS solution, a developer can work from any location with an Internet connection. The developer’s organization no longer has to provide the servers and other costly infrastructure needed. This can be especially useful when testing new solutions and developing experimental ideas. In addition, the CSP provides patching and updates for all services provided. Major CSPs offer PaaS solutions.

### Infrastructure as a Service
IaaS is where we find the system administrators (SysAdmins). In a typical IaaS offering, the IaaS service provider is responsible for the provisioning of the hardware, networking, and storage, as well as any virtualization necessary to create the IaaS environment. The SysAdmin is responsible for everything built on top of that, including the operating system, developer tools, and end-user applications as needed.

The IaaS service may be created to handle resource surge needs, to create a development environment for a distributed DevOps team, or even to develop and offer SaaS products.

## Cloud Deployment Models
There are three cloud deployment models and one hybrid model. The hybrid model is a combination of any two or more other deployment models. Each deployment model has advantages and disadvantages. A cloud deployment model tells you who owns the cloud and who can access the cloud—or at least, who controls access to the cloud. The deployment model may also tell you something about the size of the cloud.

### Public Cloud
In a public cloud, anyone with access to the Internet may access the resources provided, usually through a subscription-based service. The resources and application services are provided by third-party service providers, and the systems and data reside on third-party servers. For example, Dropbox provides a file storage product to end users. The details of how Dropbox provides this service are for the business to determine. For the customer, it is simply a publicly available cloud service.

There are concerns with privacy and security in a public cloud. And, while that may have been the case in the past, public clouds have made great strides in both privacy and security. The responsibility for both — data privacy and security — remains with the data owner (customer). Concerns about reliability can sometimes be handled contractually through the use of a service-level agreement (SLA). However, for many public cloud services, the contractual terms are fixed for both individual or corporate accounts.

Concerns also exist for vendor lock-in and access to data if the service provider goes out of business or is breached. The biggest drawback may be in customization. A public cloud provides those services and tools it determines will be profitable, and the customer often must choose from among the options provided. Each cloud service provider has a varied set of tools.

### Private Cloud
A private cloud is built in the same manner as a public cloud, architecturally. The difference is in ownership. A private cloud belongs to a single company and contains data and services for use by that company. There is not a subscription service for the general public. In this case, the infrastructure may be built internally or hosted on third-party servers.

A private cloud is usually more customizable, and the company controls access, security, and privacy. A private cloud is also generally more expensive. There are no other customers to share the infrastructure costs. With no other customers, the cost of providing excess capacity is not shared.

A private cloud may not save on infrastructure costs, but it provides cloud services to the company’s employees in a more controlled and secure fashion. The major cloud vendors provide both a public cloud and the ability for an organization to build a private cloud environment.

The primary advantage to a private cloud is security. With more control over the environment and only one customer, it is easier to avoid the security issues of multitenancy. And when the cloud is internal to the organization, a secure wipe of hardware becomes a possibility.

### Community Cloud
A community cloud falls somewhere between public and private clouds. The cloud is built for the needs of multiple organizations, all in the same industry. These common industries might be banks; governments such as a group of states; or resources shared between local, county (or parish), and state governments. Universities often set up consortiums for research, and this can be facilitated through a community cloud. Structured like public and private clouds, the infrastructure may be hosted by one of the community partners or by a third-party. Access is restricted to members of the community and may be subscription based.

While a community cloud can facilitate data sharing among similar entities, each remains independent and is responsible for what it shares with others. As in any other model, the owner of the data remains responsible for its privacy and security, sharing only what is appropriate, when it is appropriate.

### Hybrid Cloud
A hybrid cloud can be a combination of any of the other cloud deployment models but is usually a combination of the private and public cloud deployment models and can be used in ways that enhance security when necessary and allows scalability and flexibility.

When an organization has highly sensitive information, the additional cost of a private cloud is warranted. The private cloud provides the access, resource pooling, and other benefits of a cloud deployment in a more secure fashion.

However, an organization will also have less sensitive information (e.g., email, memos, and reports). In most cases, the amount of this data is much larger. A public cloud can provide the benefits of cloud computing in a cost-effective manner for this less sensitive data. As most of an organization’s data is usually of the less sensitive type, the cost savings of a public cloud realized can be substantial, while protecting the more sensitive data in the private cloud. The overall cost savings remains, and the benefits of cloud computing are realized.

In a hybrid model, the disadvantages and benefits of each type of cloud deployment remains for the portion of the cloud using that deployment model. Cloud orchestration can be used to keep this hybrid cloud manageable for the workforce to use.

## Cloud Shared Considerations
All cloud customers and CSPs share a set of concerns or considerations. It is no longer the case that all companies use a single CSP or SaaS vendor. In fact, larger companies may use multiple vendors and two or more CSPs in their delivery of services. The business choice is to use the best service for a particular use (best being defined by the customer based on features, cost, or availability). The sections that follow discuss some major considerations that allow the use of multiple CSPs and vendors, in support of the complex cloud environment that exists.
