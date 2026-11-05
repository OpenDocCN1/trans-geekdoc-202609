
- **Local legal requirements, including regulation, content rights, privacy or obscenity laws.** For example, video content offered by the GSP has a set of viewing rights that must be respected. Local obscenity laws must also be respected and enforced by the LSP based on restrictions in each location.

- **Local languages for user interfaces (including for self-care and self-provisioning).** For example, a GSP will offer a suite of services to its LSP partner; the self-service interface used to explore these new services must be translated into the local language by the LSP.

- **Local pricing incentives.** For example, the GSP provides a base pricing structure for its service package to the LSP partner but with the option to offer a promotional discount in certain regions based on business aspirations and current market reality.

- **Local variations of network technology capabilities.** For example, the GSP offers ultra-high-definition video content streams to its subscribers as an option. The LSP will flag whether this can be supported for subscribers in their region, which will allow adaptation of the offered content quality to the end user.

Many such scenarios can be imagined in the future that will require a flexible, federated set of service policies to be defined and implemented using a standard schema and APIs between GSPs and LSPs.

More generally, federation among network operators will become a business necessity and technical implementation of federated services over the complex virtual and physical infrastructure will be required. This will be done based on a well-defined network and services definition schema with associated sets of APIs and policies that define the capabilities and services supported by each provider’s network. Service federation will be used as an additional tool to create seemingly infinite scalability by allowing the combination of resources between GSP and LSP networks. This new federated reality will also require a new approach to development of new services. The creation of new hybrid services will require higher levels of interaction between the development teams and the (multiple) operations teams, which can be facilitated by the approach described in the next section.

### Dev-for-Ops (not DevOps)

In the software industry, DevOps is seen as a key methodology to simplify and accelerate production and innovation within a complex and dynamic software production environment by integrating the development and operations teams. However, the service provider environment has unique characteristics that require a different solution.

- Network service providers must provide services with high reliability and therefore be extremely fault tolerant. Historically, the recognition of communications services as a “lifeline” that was vital in emergency situations was the main driving force behind regulations that require high availability (99.999 percent uptime) of the services anywhere anytime. This is very different from many web services that are “nice to have” and thus can tolerate service downtime, although as discussed in [chapter 9, **The future of communications,**](#15-9781315365756_chapter-chap9.xhtml#chap9) this is also changing for some messaging platforms due to the central role they now play in human communications.

- Network services are dependent almost entirely on equipment and supporting software provided by third party vendors, which effectively prevents the full unification of the development team and the operations team — an essential requirement of the DevOps model.

At a high level, the Dev-for-Ops concept resembles the “design for manufacturing” engineering concept, where the design facilitates the manufacturing process to improve the quality and reduce cost.

Therefore a new innovative approach will be needed. Dev-for-Ops is an alternative innovative framework being defined that delivers agility, scalability, cost and reliability to deploying and operating network services in which the service is developed by the vendor but with a deep understanding of the operational environment and its life cycle management requirements based on operator-specific knowledge. As we described above, the increasing standardization and unification of network operations systems and interfaces will allow better collaboration among the operators. However, this will not eliminate the need for differentiation among the operators, very similar to the need for personalization of the end-user services.

At a high level, the Dev-for-Ops concept resembles the “design for manufacturing” engineering concept, where the design facilitates the manufacturing process to improve the quality and reduce cost. Design for manufacturing and its predecessors, such as Six Sigma, were adopted in many engineering disciplines including software engineering and have delivered valuable outcomes (Goss 2010).

In the current DevOps methodology (shown in the left side of [figure 9](#19-9781315365756_chapter-chap13.xhtml#fig13_9)), the application software is delivered from the development team to the operations team, which then deploys and operates it. The development team uses feedback from the operations team to generate the next software release using agile methodology, implementing the prioritized changes that are requested by operations. The right side of [figure 9](#19-9781315365756_chapter-chap13.xhtml#fig13_9) shows the Dev-for-Ops framework, including the dependencies between the vendor and the operator, and how availability, visibility, adaptability and scalability are provided. Note that this is the same functionality described in the previous subsection as service fulfillment and service assurance but the focus here is on the development of the overall solution. These characteristics must be embedded in the solutions delivered by the vendor based on a synergistic, trusted relationship between vendor and operator.

![](images/fig13_9.jpg)

The essential differences between the two approaches are:

- DevOps delivers the application; Dev-for-Ops delivers a fully realized service including the core application, monitoring and analytics and deployment and adaptation capabilities. A Dev-for-Ops service is ready to meet the demands of contextualization, scale and global-local integration.

- In many cases, operators have important insights regarding their networks and their customers that influence methods and techniques of deploying, managing and operating the services and infrastructure. Dev-for-Ops maintains this by allowing the specific adaptation of the overall solution according to the operator specific insights.

- The feedback mechanism takes on a different character in Dev-for-Ops. In order to address the separation between vendor and operator, an automatic or semi-automatic mechanism (similar to Microsoft’s “report a bug” feature) is needed to provide the feedback in a timely manner, without revealing sensitive operator business information (Microsoft 2015).

- The insights and feedback contribute to automated, operation-aware testing, which is crucial to maintain high reliability with rapid, complex releases. Failure probabilities grow exponentially in this environment driving the need for very high-quality, bulletproof software releases.

![](images/fig13_10.jpg)

As in Six Sigma, the ability to maintain reliability when reusing components heavily depends on the ability to detect and fix small defects in any of the sub-components early in the development process. This effect is even more important today, as we not only deal with many subcomponents but also with the high frequency of software updates.
