
# Remaining Agile with API Design-First

An API design-first approach is focused on frequent feedback and opportunities to make adjustments throughout the design and delivery process. An API design-first approach does not specify that all design work must be complete before proceeding into code. To understand how, it is time to revisit the Agile Manifesto and see how it can be applied to an API design-first approach.

# The Agile Manifesto Revisited

A quick review of the Agile Manifesto principles helps us better understand how API design-first fits with agile development. Following are a few principles relevant to the concerns of API design-first:

- Our highest priority should be to satisfy the customer.
- We should welcome changing requirements, even late in development.
- We must strive to deliver working software frequently.
- Business people and developers must work together daily.
- Working software is the primary measure of progress.
- Be attentive to technical excellence and good design, as this enhances agility.
- Seek the simple by maximizing the amount of work not done.

Keeping these principles in mind, teams have the opportunity to remain agile while communicating early and often with stakeholders on the API design. These stakeholders may include internal development teams, channel partners, and the developers tasked with integrating the API.

Delivering an API design progressively, rather than all at once, allows teams to meet the principle of welcoming changing requirements and delivering working software. It also helps teams avoid last-minute scrambles that can negatively impact API design.

"seek the simple" encourages teams to design in a simple way. Teams should design an API that avoids clever designs that require a higher cognitive load to understand. Instead, designs should be intuitive based on the use cases it addresses and should use vocabulary that is appropriate for the solution domain. They should offer only the necessary information to support the case.

> 1. Kent Beck, et al., “Principles behind the Agile Manifesto,” https://agilemanifesto.org/principles.html.

# The Agility of API Design-First

The goal of API design-first should be to gather sufficient details to limit the risk of a breaking change in the future. It doesn't mandate that an entire design process must be completed before development begins. Agile development and API design-first make terrific companions.

# Remember

Teams can always add to an API design, but it is impossible to take things away without breaking integrations that depend on them. Take advantage of agile software development to incrementally design APIs with the needs of customers, partners, and the workforce in mind.

An API design-first process enables teams to move quickly, thoughtfully, and with the agility to make changes early in the process. It is the complete opposite of the waterfall approach to API design.

# The Align-Define-Design-Refine Process

One of the biggest challenges most API design teams encounter is how to deliver an API design from business requirements in any variety of forms: use cases, spreadsheets, wireframes, and so on. Those with a background in software analysis may find this to be an easier task. However, there are still challenges when it comes to mapping a domain model and capabilities into a Web-based API design. One of the challenges is the need to ensure alignment of scope and deliverables among all technical and nontechnical team members.

As the name suggests, the Align-Define-Design-Refine (ADDR) process² guides teams through an API design-first approach. The process groups the step-by-step process into four distinct phases:

- **Align:** Ensures alignment of understanding and scope across business, product, and technology around a set of desired outcomes
- **Define:** Maps business and customer requirements into digital capabilities that will form the basis of one or more APIs to deliver the desired outcomes

² The ADDR process is based on the many lessons learned during my years of experience in API design coaching.

# CHAPTER 2 COLLABORATIVE API DESIGN

- 3. **Design:** Applies specific design steps for each API to meet the desired outcomes using one or more API styles
- 4. **Refine:** Refines the API design through feedback from developers, in addition to documentation, prototyping, and testing efforts

There are seven steps across the phases, which are explored in-depth for the remainder of this book:

- 1. **Identify digital capabilities:** Identify the customer needs and desired outcomes, including the corresponding digital capabilities that are required.
- 2. **Capture activity steps:** Expand the digital capabilities to include a unified understanding and clarity through collaborative API design sessions.
- 3. **Identify API boundaries:** Group the digital capabilities into API boundaries and determine whether the APIs already exist or new APIs are required.
- 4. **Model API profiles:** Use a collaborative API modeling session to define the high-level API design, including resources and operations into an API profile.
- 5. **High-level API designs:** Select one or more API styles that each API profile will offer and document the high-level design elements.
- 6. **Refine the design:** Incorporate design feedback from API consumers using techniques that encourage improvement in the developer experience.
- 7. **Document the API:** Complete the API documentation, including reference documentation and getting started guides, to accelerate integration.

Figure 2.4 summarizes the ADDR process that supports an API design first approach.

The process achieves the following goals:

- Deliver an API design that emphasizes and solves the customer problems using a vocabulary they understand.
- Reduce the constant design churn common with informal design processes.
- Optimize the entire organization, not just developers, for API design and delivery.
- Avoid unnecessary steps whenever possible to expedite delivery.
- Create a repeatable process that delivers an API design with a mixture of technical and nontechnical roles, some of don't fully understand the nuances of API design but are able to contribute their insights.

# THE ALIGN-DEFINE-DESIGN-REFINE PROCESS

Figure 2.4 The ADDR process overview ![](img/6a42b4fe2691ad7de274bb9859.png)

The ADDR process is built loosely on concepts and practices found in DDD. However, organizations do not be practicing DDD, or even familiar with it, to be effective at applying the process. Those familiar with DDD may recognize some of the concepts and techniques used. However, it is important to recognize that the ADDR process may deviate from DDD practices when necessary to ensure that it remains approachable and repeatable in a variety of situations. As such, those familiar with DDD may wish to make adjustments to the process to fit their needs and preferences.

# The Role of DDD in API Design

As mentioned, an API design process should emphasize and solve the customers' problems using a vocabulary they understand. This requires a deep understanding of how the API will address market needs, combined with business strategy. The design and development of an API occurs without factoring in these concerns, it will often miss the mark for being a great API that is a joy to use.

Domain-driven design (DDD) is an approach to software development that encourages collaboration between domain experts and software developers to address complex solutions. DDD's core principles include discussion, listening, understanding, discovery, and delivering business value. Every member of the team across nonlocal and technical roles contributes to the insightful depth of business innovations in the software solutions. Those new to DDD may wish to refer to the seminal book on DDD by Eric Evans and Vaughn Vernon's Implementing Domain-Driven Design, which provides insights on implementing DDD in an organization.

The remainder of this book examines the ADDR process in detail:

- Aligning and defining the APIs required to deliver desired outcomes (Chapters 3–6)
- Designing APIs that meet the desired outcomes using common patterns and practices (Chapters 7–9)
- Decomposing APIs into smaller services (Chapter 10)
- Improving the developer experience through a combination of robust documentation, helper libraries, and testing strategy to ensure consumers get up running with confidence (Chapters 11–13)
- Evolving the API design, which is critical for sustainable, long-lived APIs (Chapter 14)
- Protecting APIs to ensure that data is not leaked to unauthorized parties (Chapter 15)
- Scaling the API design effort, which is important for larger initiatives (Chapter 16)
