
security architectures. To ensure that the organization gets the right level of control to address the most common risks, a good architecture must be comprehensive but also simple. It must also avoid unnecessary duplication of services or complexities that could compromise the business benefits of the security services. It must be able to address control requirements as they evolve over time.

- **It provides a unified vision for common security controls:** By providing this common services model, the architecture looks at security controls from a holistic view, identifying potential gaps in those controls and providing a long-term plan for improvement. As such, it is a fundamental part of good security management practices.
- **It leverages existing technology investments:** Any proposed security should reuse existing technologies that are already deployed in the enterprise whenever practical. By focusing on what the organization has already deployed, the architecture can take full advantage of the internal skill sets, licensing, and agreements to minimize the need for training or staff augmentation.
- **It provides a flexible approach to current and future threats and also the needs of core functions:** If done well, the implementation of the architecture should be flexible enough to provide safeguards and countermeasures for current and emerging threats. It also, however, has to be flexible enough to allow the core applications within the organization to operate and integrate as intended.

The result should be an architecture that supports and integrates with:

1. An effective security program that recognizes that all information is not equal or constant in terms of value and risk over time.
2. An efficient security program that applies the right technology to protect the most critical assets combined with quality processes that reduce the risks to acceptable business levels. This is achieved through some form of evaluation process.
3. A high quality security program that includes regular management reviews and technology assessments to ensure controls are working as intended and providing feedback so that technology and processes can adapt to changes in value and risks over time. This is measured and monitored as part of a system assurance program.

## Intended Benefits

While every design may be different, all ESAs strive to:

- Provide guidance to IT architects and senior management and enable these decision makers to make better security-related investment and design decisions;
- Establish future-state technology architecture for the security environment focused on a limited set of proposed security services;
- Support, enable, and extend security policies and standards;
- Describe general security strategies used to guide security-related decisions at technical architecture and solution levels;
- Leverage industry standards and models to ensure security best practices are being applied;
- Present and document the various elements of the security architecture in order to ensure proper linkage and alignment with other architecture domains;
- Define technology security architecture in relationship with other technology domains;
- Provide an understanding of the impact on the security posture (better, worse, no change) of development and implementation within the other domains;
- Manage IT solution risk consistently across the project, while leveraging industry best practices;
- Reduce costs and improve flexibility by implementing reusable, common security services; and
- Provide a secure mechanism for end-of-life and decommissioning solutions when necessary.

## Defining and Maintaining Enterprise Security Architecture

ESA starts with a basic understanding of the overall strategic direction of the organization, and the IT delivery strategies that are used to support them. Key business drivers and technology positions are also documented. Current policies and standards are used as input to requirement gathering (particularly with legal or regulatory compliance). As security hinges on the question of access of subjects (active parties asking for information) to objects (passive parties providing information), effort is made to capture common types of users, types of sensitive or critical assets, and how access between the two should be mitigated. To capture high-level priorities, generally accepted security and security architecture principles are discussed and documented. Other requirements are obtained through interviews with key stakeholders, documentation reviews, and current IT security management processes and procedures. All of these inputs are then used to provide a comprehensive set of requirements for security services. The success of any design can then be measured against its alignment with these standards.

Once these requirements have been documented, they are then used to derive a set of architectural models. A security architect starts with conceptual target models describing a number of sets of common security services. These services are defined according to their intended users, the systems and data they access, and how security must be applied in the contexts of use scenarios. Target models include high-level logical models for each set of common security services as well as walkthroughs using those models, combining user groups and scenarios. At the beginning, the security architect may choose to develop a limited set of target models intended to address the most critical business problems. Further models may be added in the future.

Component models and physical models are considerably more granular, addressing security components within individual systems. Component models describe security functionality in terms of generic components, component flows, and nodes. Physical models showing security services in context are also developed during implementation. These types of models are developed as part of projects focused on the deployment of new services and incorporated into the ESA during development. As decisions are made, they are captured as architectural decisions. These are separate documents describing the issue at hand, the options that were considered, and the rationale for decisions that were made. This ensures that all decisions are open to continuous review.

While models assist in framing the final shape of the ESA, it is important that they be grounded in a practical, ordered set of transition activities that will move the organization from the current environment to the future state. With the development of the models, the current security controls environment is documented. A gap analysis is then performed, and steps to address those gaps are prioritized based on business priorities and interdependencies. These are then articulated into a strategic roadmap, showing how those gaps will be addressed over an extended period, typically three to five years.

The security architect has to be prepared to address any issues, risks, and planned updates that may come up during the development of the designs. For example, a threat/risk assessment provides a method of quantifying the risks associated with IT and can be used to help validate the abilities of new security controls and countermeasures to address the identified risks. If new vulnerabilities have been discovered or introduced, it also provides a way to determine if changes are required to the overall ESA.

With a firm idea of the current threat/risk environment, security architects can set priorities for the solution-level design and implementation, and security designs can be revalidated to ensure that the high-level requirements and models can be kept up to date.

## Common Security Services

A number of security functions are suitable as foundations for common security services in the enterprise. Most ESAs distinguish between different types of services. The following is a sample taxonomy of services that may be used as building blocks in ESA.

- **Boundary Control Services** – These services are concerned with how and whether information is allowed to flow from one set of systems to another, or from one state to another. Boundary control systems are intended to enforce security zones of control by isolating entry points from one zone to another (choke points). As such, they provide a set of common points to access or transmit information across security zones. These systems will include the typical range of secure networking devices – firewalls, border routers, proxies, and other boundary services – intended to protect more trusted/sensitive assets from less trusted/sensitive assets.
- **Access Control Services** – These services focus on the identification, authentication, and authorization of subject entities (whether human or machine) as they are deployed and employed to access the organization’s assets. As a strategic set of services, they are intended to normalize identification and promote shared authentication throughout the enterprise. In general, these services will promote reduced-sign-on (RSO) or single-sign-on (SSO), but they will also include RSO or SSO services themselves as common services.¹⁵ It will also include a number of other services surrounding the creation, handling, and storage of credentials in the enterprise. On the authorization side, these services focus on what valid user entities are allowed and not allowed to do within the enterprise given a set of rules enforced through automated systems. They will offer coarse-grained (system-level) authorization services that can be leveraged by other domains in the enterprise architecture.
- **Integrity Services** – Integrity services focus on the maintenance of high-integrity systems and data through automated checking to detect and correct corruption. As a set of common services, these can be leveraged by the
