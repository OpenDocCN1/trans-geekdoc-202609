# Chapter 5: Cloud Application Security
159

may be appropriate and feasible in some cases, but one can never assume that it is or that all configurations and security controls are possible in a cloud environment.

# Cloud Appropriateness

With any application security model, the underlying hosting environment is a significant portion of securing the application and plays a crucial role in the auditing and compliance of an application. Many regulatory requirements involve the underlying infrastructure and hosting environment having to be certified to an appropriate security level before the application resides therein can be certified. With a cloud environment, such a certification may not be practical or even possible. Especially within a public cloud, the cloud provider is unlikely to be able to meet strict security requirements of any regulatory schemes, or may be unwilling to allow auditors the type and level of access that would be needed in order to properly certify the environment. One approach that many cloud providers may opt to take is to use a SOC 2 audit and make the report available to cloud customers and potential cloud customers as a way of providing confidence without having to open their systems or sensitive information to the masses. Cloud environments are also typically configured on web-based applications that are built on modern web service frameworks and cutting-edge programming languages and platforms, and are unlikely to adequately support many legacy systems or programming languages.

# Integration Challenges

In a traditional data center, the developers and administrators will have full access to all components, servers, and networking equipment to make integration of services and systems seamless and feasible. With a cloud environment (and even with IaaS), access to these types of systems and services will be severely limited, if even available at all. When attempting to do system integrations, without having full access to both systems and logs, it can be very difficult to troubleshoot or properly engineer the system designs and communications channels. The cloud customer would have to rely heavily on the cloud provider for assistance, and depending on the cloud service model and the demands of other tenants, it might not be something the cloud provider is willing or able to do. In likelihood, the cloud customer would have to adopt the APIs and other particular offerings and services from the cloud provider to get the most access and visibility possible, which could also lead to vendor lock-in and a decrease in portability.

# Cloud Environment Challenges

With cloud environments involving new and rapidly evolving technologies, the focus tends to be on newer application environments and the more modern programming languages and development methodologies. When undertaking cloud development, it is imperative for an organization to ensure that developers and project managers who are familiar with cloud, its particular issues and challenges, as well as the technologies and systems present in a cloud environment versus traditional data centers.

# Cloud Development Challenges

Typical software development lifecycle (SDLC) processes and methodologies revolve around well-documented and well-established practices and procedures. A typical organization will have its own practices that it follows and will have its internal policies