
## How?

There are many methodologies for developing an IT and security architecture. This chapter will discuss some examples of frameworks, models, and standards frequently used in secure design. Although most security architectures are built on common themes, they vary depending on the needs of the organization that sponsored them. Successful integration is predicated on the acceptance and adoption of the stakeholders and customers of the architecture. This is accomplished by ensuring that the security architecture addresses the business requirements of a system. Those requirements will often be different depending on the scope of the design effort: System security architecture will focus on requirements for individual systems, while enterprise security architecture (ESA) will focus on multiple systems throughout the enterprise. The basic principles of secure design and the common methodologies and techniques used to create, implement, and verify these designs will be focused on. Finally, key concepts in system security architecture and ESA will be addressed. The security professional needs to understand how security architecture and design is performed and how different levels of architecture work together to secure information assets.

System security architecture is focused on designing security services within individual computing systems. Modern computing systems are complex creatures, comprised of a myriad of moving parts: computing platform hardware, firmware, operating system (OS), utilities, and a variety of specialized applications. Each moving part may either have a native control, the ability to implement a control, or none of the above.

In general, a well-architected solution will be able to combine security functions from each of the moving parts into a cohesive design. At the same time, it will need to strike a balance between security and the other needs of the computing system. This can be a very difficult balance to achieve. Because security components can consume considerable resources, control is frequently sacrificed in favor of improved functionality, usability, or performance. It is a security architect’s challenge to find the balance and ensure that necessary controls are implemented as designed. This is most important because the ability to be successful when designing and building an enterprise security architecture "begins at the beginning, and ends at the end". Specifically, the security architect needs to understand that the ability to envision security and incorporate it from the very beginning of the planning cycle, through the design and build phases, all the way to the end of the lifecycle when an architecture is retired, is what equates to success. If security is an afterthought or is left till late in the implementation of the architecture, as opposed to being considered from the very beginning of the process, then security will never be as thorough nor as impactful as if it was "built-in" from the beginning.

There is a wide variety of computing platforms available, and each platform will take a different approach to providing security services. The architecture of these platforms is fundamental to the ways that they approach security requirements. Most computing platforms will offer a wide variety of security controls to help protect sensitive assets that are being generated, transmitted, or stored by the system. The security architect may be responsible for determining what security controls will be implemented, or he or she may be responsible for deciding what native controls will be used for a particular system in the enterprise.

The security architect must understand the basic building blocks that make up modern computing systems as well as some characteristics that distinguish types of systems from each other. Most importantly, he or she should be aware of the different ways that security can be implemented at the system level and be able to choose which mechanisms would be most appropriate in a given scenario.

## TOPICS

- Implement and manage an engineering lifecycle using security design principles
- Fundamental concepts of security models
- Controls and countermeasures based upon information systems security standards
- Security capabilities of information systems
- Assess and mitigate the vulnerabilities of security architectures, designs, and solution elements
  - Client-based (e.g., applets, local caches)
  - Server-based (e.g., data flow control)
  - Database security
  - Large scale parallel data systems
  - Distributed systems (e.g., cloud computing, grid computing, peer to peer)
  - Cryptographic systems
- Vulnerabilities in Web-based systems
- Vulnerabilities in mobile systems
- Vulnerabilities in embedded devices and cyber-physical systems (e.g., network-enabled devices)
- Cryptography
  - Cryptographic lifecycle
  - Cryptographic types (e.g., symmetric, asymmetric, elliptic curves)
  - Public key infrastructure (PKI)
  - Key management practices
  - Digital signatures
  - Digital rights management (DRM)
  - Non-repudiation
  - Integrity (hashing and salting)
  - Methods of cryptanalytic attacks (e.g., brute force, cipher-text only, known plaintext)
- Apply secure principles to site and facility design
- Facility security
  - Wiring closets
  - Server room
  - Media and storage facilities
  - Evidence storage
  - Restricted and work area security (e.g., operations center)
- Data center security
- Utilities and HVAC considerations
- Water issues (e.g., leakage, flooding)
- Fire prevention, detection, and suppression

## OBJECTIVES

According to the (ISC)² Candidate Information Bulletin (Exam Outline), a CISSP candidate is expected to:

- Understand the engineering lifecycle and apply security design principles
- Understand the fundamental concepts of security models
- Select controls and countermeasures based upon information systems security standards
- Understand the security capabilities of information systems
- Assess and mitigate the vulnerabilities of:
  - Security architectures, designs, and solution elements
  - Web-based systems
  - Mobile systems
  - Embedded devices and cyber-physical systems
- Apply cryptography
- Apply secure principles to site and facility design
- Design and implement facility security

## The Engineering Lifecycle Using Security Design Principles

According to one definition, systems engineering is "an interdisciplinary approach to translating users’ needs into the definition of a system, its architecture and design through an iterative process that results in an effective operational system. Systems engineering applies over the entire life cycle, from concept development to final disposal." 1

Systems engineering models and processes usually organize themselves around the concept of a lifecycle. The International Council on Systems Engineering (INCOSE) systems engineering process is a widely recognized representation of classical systems engineering.2 ISO/IEC 15288:2008 is an international systems engineering standard covering processes and lifecycle stages. It defines a set of processes divided into four categories: technical, project, agreement, and enterprise. Example lifecycle stages can include concept, development, production, utilization, support, and retirement. For example, the U.S. Department of Defense uses the following phases: materiel solution analysis, technology development, engineering and manufacturing development, production and deployment, and operations and support.

While the detailed views, implementations, and terminology used to articulate the system’s engineering lifecycle differ, they all share fundamental elements, depicted in Figure 3.1 by the V-model. The left side of the V represents concept development and the decomposition of requirements into functions and physical entities that can be architected, designed, and developed. The right side of the V represents integration of these entities and their ultimate transition into the field, where they are operated and maintained.
