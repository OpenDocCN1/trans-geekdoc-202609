
KC continues to look for ways to improve the due diligence and security of the cloud deployments that their vendors use. One well‐explored idea came from the Security Architecture world: patterns. A security architecture pattern is a defined, reusable solution. These patterns are used by internal cybersecurity teams to provide conditions and requirements to those deploying into production operations. Experts use their experience with best practices and document them into easy‐to‐understand formats or patterns. For example, KC uses `SAML 2.0` for federated identity management. A security pattern has been developed for how it is implemented securely and repeatedly as new vendor software is added to the enterprise.

Due to the number of vendors and types of implementations, KC decided to review and propose a number of ways a pattern or its equivalent could be leveraged for vendors deploying to cloud. Security Configuration reports are produced by the provider's `CSPs`, as are existing published cloud security patterns, baselines, and benchmarks. Lastly, the industry has a number of certifications that can be leveraged as a pattern or model that can be used to provide guidance on required controls. We discuss each of those instances next, and some of the ways they can be reused as security standards for a vendor's cloud.

Note, KC's Cyber Third‐Party Risk team was tasked with developing a repeatable, easy‐to‐use guide using several of the most well‐known Cloud Service Providers to ensure that their vendors knew the requirements and could easily implement them.

## The Shared Responsibility Model

In order to understand and assess the risk with cloud deployments, it is necessary to understand the Shared Responsibility Model. In a traditional data center, all the responsibility for security falls to the company. However, when a company's services or products are located in a `CSP`, the responsibilities start to become the duty of the Cloud Service Provider.

Defining cloud computing is the first step in understanding the Shared Responsibility model. `NIST` defines it as follows:

> Cloud computing is a model for enabling ubiquitous, convenient, on‐demand network access to a shared pool of configurable computing resources (e.g., networks, servers, storage, applications, and services) that can be rapidly provisioned and released with minimal management effort or service provider interaction.

The `ISO` definition is similar to `NIST`'s definition: Cloud computing is a “Paradigm for enabling network access to a scalable and elastic pool of shareable physical or virtual resources with self‐service provisioning and administration on‐demand.” While the simple way it is described for this book, “any data or process that is not in your own data center or location,” is still accurate, the more technical definition would be resources, data, and/or processes that are pooled and made available for use by the customer. When the use is complete, the resources, data, and/or processes are then released for use by another customer.

As discussed earlier in the chapter, there are three service models described by `NIST`: `SaaS`, `PaaS`, and `IaaS`.

`ISO` includes other definitions like Compute‐as‐a‐Service (`CaaS`) and Data Storage‐as‐a‐Service (`DSaaS`), and the lists of types can get muddled. For the vast majority of services required for business, however, `NIST` breaks them down into the three categories listed. An easy way to illustrate this model is by showing the stack where `SaaS` is on top of the `PaaS`, which lies on top of the `IaaS`. [Figure 10.1](#c10.xhtml#c10-fig-0001) shows how the different service models compare.

![FIGURE 10.1 SaaS, PaaS, and IaaS Stacks](images/c10f001.png)

[FIGURE 10.1](#c10.xhtml#R_c10-fig-0001) `SaaS`, `PaaS`, and `IaaS` Stacks

Cloud computing is a shared technology model that allows different organizations to manage and be responsible for different parts of the stack. The result is that the responsibilities typically owned by the customer are shared across all the organizations involved in the cloud deployment, whether it is `SaaS`, `PaaS`, or `IaaS`. This Shared Responsibility Model drives how the service model is managed by the different deployment types.

The `SaaS` model dictates that the `CSP` is responsible for nearly the whole stack, including security. The user generally can only manage the application and is not allowed to alter its functionality on the back end. `SaaS` solutions can enable the customer to manage user‐level access, but the cloud provider is the owner for perimeter security, logging, monitoring, auditing, and the security of the application itself. The customer often manages the authorization and entitlements of their users and is responsible for the data located in the cloud.

`PaaS` dictates that the `CSP` owns the security of the platform (e.g., operating system) while the consumer is responsible for all services and products that are deployed on the platform. This is where the responsibilities are evenly split between the consumer and cloud provider. For example, if the customer has deployed a `Database-as-a-Service`, where the platform is the database running on an OS, then they are responsible for the security of the accounts and authentication methods. The cloud provider is then responsible for the security of the platform itself. [Figure 10.2](#c10.xhtml#c10-fig-0002) illustrates the differences in the Shared Responsibility Model.

In the `IaaS` model, the cloud provider is responsible for the security of the underlying substructure, while the customer owns all the security controls placed on top of the infrastructure. This is the far end from the `SaaS` responsibilities, where most of the ownership lies with the cloud provider; in the `IaaS` model, nearly all of the responsibilities lie with the customer. The cloud provider monitors the perimeter for security, but the customer owns the virtual network security and all that is included with the network security.

![FIGURE 10.2 The Shared Responsibility Model](images/c10f002.png)

[FIGURE 10.2](#c10.xhtml#R_c10-fig-0002) The Shared Responsibility Model

The most important part of the security in any deployment is having a clear understanding of who is responsible for what actions at all phases of the cloud's deployment. What is provided by the `CSP` and when in comparison to what the consumer is responsible for and at what point in the deployment are crucial questions that can get muddy when a consumer is your third party providing this service to you as an end customer.

In the Shared Responsibility model, whether you select `SaaS`, `PaaS`, or `IaaS`, the customer is responsible for some key areas:

*   `Data Security`: The `CSP` has no insight or visibility into your data on their platform. Ensure that both you and the vendor retain control of the data, its maintenance, and use. The data's security should be the primary concern regardless of model chosen.
*   `Application Security`: Any applications the vendor or you operate on the cloud environment are not the responsibility of the cloud provider. Any malicious code, intrusion, misuse, or maintenance of the application is the responsibility of the customer.
*   `Identity and Access Management`: Any Single‐Sign‐On (`SSO`), multi‐factor authentication (`MFA`), keys, certificates, password management, and the identity and access management (`IAM`) process are the responsibility of the customer. The vendor providing the service to you, as the customer, may pass some of this responsibility on to your organization; however, this is not the `CSP`'s responsibility.
