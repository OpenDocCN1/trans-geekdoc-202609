
Because of potential security implications, several capabilities should be prioritized first.

- **Identity:** Security assurances can be achieved only by developing user directories and other authentication functions. Instead of using homegrown authentication solutions, choose mature capabilities such as Using Azure Active Directory (Azure AD), AAD B2B for Azure, and a B2C version of Azure AD. Users, partners, customers, applications, services, and other entities can be authenticated and granted permission through third-party solutions.

- **Data protection:** To encrypt and protect data, developers should use cloud services that include native encryption. There are many examples in the security world of failed attempts to protect data or passwords that cannot withstand attacks. Developers should only attempt to create their own cryptographic algorithms if they can directly use cryptography.

- **Key management:** Instead of directly handling keys, prefer identity authentication. A key management service such as Azure Key Vault or AWS Key Management Service, can access services requiring keys. As opposed to attempting to handle keys in application code safely, this will help you manage and secure these keys.

- **Application configurations:** Inconsistent configurations can create security risks for applications. The Azure App Configuration service helps mitigate this risk by centrally managing application settings and feature flags.

![](img/5ab9852bf401dd309bf0f81797a91445_387_0.png)

From the SC-100 exam standpoint, remember that two popular standards, STRIDE and OWASP, can identify more potential risks. When designing an app or system, developers can spot threats using the STRIDE threat model. OWASP is a nonprofit organization dedicated to improving software security.

## Specify a Security Strategy for Applications and APIs

Continuous integration/continuous delivery (CI/CD) for applications and API development should be incorporated into the DevOps life cycle as rapidly as possible to avoid a waterfall development cycle.

What is a waterfall model? The *waterfall model* was the first process model to be introduced. It is also referred to as a *linear-sequential life-cycle model* and is very simple to understand and use. In a waterfall model, each phase must be completed before the next step can begin, and there is no overlapping of the stages.

Continuous delivery of value to end users is enabled by the union of people, processes, and tools in DevOps. As a result of the merging of Dev and Ops, multidisciplinary teams from development and operations collaborate using tools and practices that are shared and efficient.

In a DevOps environment, security concerns can be addressed quickly without waiting for a waterfall model's longer planning and testing schedule. Application and API life cycles are influenced by DevOps throughout the planning, development, delivery, and operation phases. Phases do not have specific roles, but they all depend on each other. To some extent, all roles are involved in each phase in a true DevOps culture. Table 8.4 describes the phases of a DevOps culture.

## TABLE 8.4 DevOps Phases and Tasks

| Phase | Task |
| :--- | :--- |
| Plan | A DevOps team imagines, defines, and describes the features and capabilities of applications and systems they are building. A single-product task can be tracked at a low level of granularity, and a multiproduct portfolio task can be tracked at a high level of granularity. DevOps teams plan with agility and visibility by creating backlogs, tracking bugs, managing agile software development with Scrum, using Kanban boards, and visualizing progress. |
| Develop | This includes all aspects of coding, such as writing, testing, reviewing, integrating, and packaging code for deployment into various environments by team members. Teams use version control software to collaborate on code and work in parallel, usually Git. Furthermore, they aim to innovate rapidly without compromising quality, stability, or productivity. Through automated testing and continuous integration, they iterate in small increments using highly productive tools, automate mundane and manual steps, and use highly effective tools. |
| Deliver | Deploying applications consistently and reliably into production environments, ideally via continuous delivery. In addition to the delivery phase, the infrastructure that underpins those environments must also be deployed and configured. Containers, microservices, and infrastructure as code (IaC) are commonly used in these environments. |
| Operate | In this phase you maintain, monitor, and troubleshoot production applications in public and hybrid clouds. DevOps practices ensure that systems are reliable and highly available and aim for zero downtime while reinforcing security and governance. |

## Enforcing Security for DevOps

Teams that don't have a standard DevSecOps strategy are urged to begin the preparations as soon as possible. Initially, team members may be reluctant to accept the existing threats because they don't fully appreciate them. Some may consider a unique investment wasteful, as they believe that the team needs to be equipped to take on the challenge. As a first step, the team needs to build consensus on the nature of the risks, how to mitigate them, and whether they need additional resources they do not have right now.

There are a few common arguments skeptics will raise, including the following:

- What is the level of threat? Data and services that teams are charged with protecting are often undervalued.
- Is our team good? Security discussions may be perceived as doubt about the team’s ability to build a secure system.
- This is not possible. Junior engineers often make this argument, and experienced individuals usually know better.
- We have never been breached. How do you know? Can you tell us how?
- Value debates are endless. It may be perceived that DevSecOps is a distraction from core feature development. Although security investments must be balanced with other priorities, they cannot be ignored.

### Security Strategy Components

Many techniques can be applied in the quest for more secure systems. Table 8.5 demonstrates the security strategy components.

## **TABLE 8.5** Security Strategy Components

| Preventing Breaches | Assuming Breaches |
|---|---|
| Threat models | War game exercises |
| Code reviews | Central security monitors |
| Security testing | Live site penetration tests |

There should already be some practices in place in every team to prevent breaches. Static analysis tools and other security testing features are increasingly available free of charge, and most developers have become accustomed to writing secure code.

In a world where breaches are a given, many teams need a strategy for dealing with them. The admission of this can be challenging, especially when dealing with complex management situations. Practice techniques that assume breaches will help the team answer questions about their security on their own time, so they don’t have to figure it all out during an actual security emergency.

Team members should consider the following questions:

- Is there a way to detect an attack?
- If you are attacked or penetrated, how will you respond?
- Is there a way to recover from an attack, such as when data is leaked or tampered with?

### Strategies for Mitigating Threats

Identifying every possible threat to a system is impossible because the list is so long. In some cases, security holes are caused by dependency issues, such as outdated operating systems and libraries. Maintaining these dependencies is crucial.

The majority of modern web applications make APIs available for clients to use. A well-designed web API should support the following:

- **Platform independence:** No matter how the API is implemented internally, any client should be able to call it. For this to work, standard protocols must be used, and an agreement must be reached on the data format to be exchanged between the client and web service.
- **Service evolution:** Client applications should not depend on the web API to evolve and add functionality, and the API should be able to support existing client applications without requiring any modifications. All functionality must be discoverable so that client applications can fully use it.

Focus on the web API's business entities. An e-commerce system, for instance, might have customers and orders as its primary entities. The process of creating an order involves sending an HTTP POST request that contains the order information. HTTP responses indicate whether the order has been placed successfully. Nouns (the resource) should be used as resource URIs whenever possible rather than verbs (the operations on the resource).

> From the SC-100 exam standpoint, remember that a security strategy's critical components for preventing breaches are threat models, code reviews, security testing, and SDLs.

### Specify Priorities for Mitigating Threats to Data

Microsoft maps cybersecurity weaknesses in your organization to actionable security recommendations, prioritizing them according to their impact. Mitigating or remediating vulnerabilities is easier with prioritized recommendations.
