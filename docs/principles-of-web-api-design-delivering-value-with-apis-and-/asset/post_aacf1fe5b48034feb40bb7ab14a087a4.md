
managers, to name just a few. These roles represent the needs of the customers. An effective API design includes input from many roles across the organization, not just the technical details of how to push data in and out of a data store or legacy system.

It is also necessary to create alignment between stakeholders and the development teams responsible for implementing the API. If the API lacks business context, it may meet the needs of customers but lack sufficient factors to meet business goals. If the API lacks a customer context, it may meet the needs of business but fail to deliver the desired outcomes of customers. If it lacks both, the API will serve no real purpose and efforts will have been wasted. In the ADDR process, digital capabilities are used to create alignment between business, customers, and technology to avoid these negative consequences.

## What Are Digital Capabilities?

Business capabilities describe the enablers an organization brings to market. Examples of business capabilities include consumer product design, manufacturing, and customer support.

Digital capabilities are assets that turn desired outcomes into reality through automation. They offer the workforce, partners, and customers the ability to interact with the organization digitally. Digital capabilities may take the form of one or more technology solutions. Examples include REST APIs, Webhook-based asynchronous APIs for integration, SOAP services, message streams, and bulk data exchange through a nightly, weekly, or monthly file-based export process.

Reviewing the digital capabilities offered by an in-house or competitor’s product or service provides greater insights into what the organization values, including the market segments addressed.

Digital capabilities portfolio is the collection of digital capabilities offered by a product or organization. For organizations building a platform to connect two or more parties within a marketplace, the terms digital platform and platform capabilities may be more familiar.

While digital capabilities may be mapped to business capabilities, they operate at different levels of concern. Business architects define business capabilities, such as customer service, and may associate key performance indicators (KPIs) or objectives (OKRs) to track growth. Digital capabilities focus on producing outcomes and include the activities required to deliver the business capabilities of the organization. Business capabilities describe the “what” of the organization; digital capabilities describe the “how.”

## CHAPTER 3 IDENTIFY DIGITAL CAPABILITIES

Table 3.1 Digital Capabilities Realized by a REST-Based Project Management API

| Digital Capability | Example REST-Based API Design |
|---|---|
| Manage project from start to finish | POST /projects |
| Add collaborators to a project | POST /projects/{projectid}/collaborators |
| Subdivide project into issues | POST /issues |
| Mark issue complete | POST /issues?status=issueId/completed |
| View incomplete issues | GET /issues?status=incomplete |
| View active projects | GET /projects?status=active |

Table 3.1 provides an example for a typical project management application to demonstrate the differences between digital capabilities for a project management application and how they may be realized through a REST-based API. Notice how the digital capabilities are written with a focus on customers and their desired outcomes. The choice of API design style, such as REST, GraphQL, or gRPC (detailed in Chapters 7 and 8), is not explicitly part of a digital capability but rather a part of how the digital capability is manifested. In some cases, multiple API design styles may be offered for a single digital capability. There are a few ways that business and product requirements may be captured and used to drive the design of digital capabilities as APIs. The ADDR recommends using job stories, which are rooted in the jobs to be done approach to design.

## Focus on the Jobs to Be Done

Jobs to be done (JTBD) are the identified needs fulfilled by a product or service offering. JTBD involves capturing how a customer problem, the task to be performed, and the desired outcome that should result.

> JTBD was formulated by Clayton Christensen, author of The Innovator's Dilemma, as a method of taking the viewpoint of the customer when designing a product or service. JTBD ensures that the product addresses a specific need and therefore has a better chance of gaining market adoption. It starts by identifying the needs of customers, the job, and then defining how product or service will fill that.

- 1. Christensen Institute, “Jobs to Be Done,” accessed August 12, 2021, https://www.christenseninstitute.org/jobs-to-be-done.
2. Clayton M. Christensen, The Innovator's Dilemma: When New Technologies Cause Great Firms to Fail (Boston: Harvard Business Review Press, 2016).

## WHAT ARE JOB STORIES?

In JTBD, jobs are more than just functions that need to be performed. Jobs are really about the desired outcome or accomplishment. Jobs may be new and unresolved or may be solved in some way that doesn't quite meet the customers' needs. A product that produces the desired outcome is one that considers all of these factors about the jobs to be done. JTBD applies to APIs as well as all other aspects of product and software design with the organization.

The idea behind JTBD is rooted in the voice of the customer (VOC)³ from the mid-1980s, product managers attempted to improve product performance by getting into the mindset of the customer. VOC combines market research data with specific waits and needs that have been identified through surveys and customer interviews.

Christensen also reminds us that there is an emotional and social side to the jobs that a product attempts to solve. The job extends beyond the immediate problem to include a reduction or removal of the anxiety involved. The product should provide a positive experience while producing progress toward the desired outcome. May even go so far as to enjoyment while completing the job.

## Principle 2: API design starts with an outcome-based focus

A focus on the outcome ensures the API deliver value to everyone. This requires a product-thinking approach to API design rather than one is driven purely by data and systems integration. The ADDR process is focused on identifying and realizing these outcomes.

## What Are Job Stories?

Customers and users don't care about APIs, microservices, serverless, or the flavor of frontend framework used. They want a solution to a problem. They care about outcomes.

Job stories capture the jobs to be done for any product, including the customer motivations, events, and expectations for a new product, service, or API. They frame every design problem from the perspective of the customer. Job stories seek to identify the problems that customers have and the eventual outcome they wish to achieve. Jobs are identified that will solve these problems. APIs will offer digital capabilities that will power these JTBD to produce the desired outcome.

> 3. Wikipedia, s.v. "Voice of the Customer," last modified July 15, 2021, 12:112, https://en.wikipedia.org/wiki/Voice_of_the_customer.

## CHAPTER 3 IDENTIFY DIGITAL CAPABILITIES

Job stories were created by Alan Klement⁴ and are based on JTBD formulated by Christensen. They offer a simple framework to capture all the aspects of the job to be done.

Teams producing job stories will find their API designs focus more on the desired outcomes of the audience. They will also have the details necessary to create acceptance criteria for automated tests. It is important to note that job stories aren't contain implementation specifications. Instead, they should elaborate on what happens to make the necessary progress to deliver the outcome.

The ADDR process leans heavily on job stories to capture business requirements in a customer-centric way. Job stories express customer requirements in a simple format and provide a natural way to identify digital capabilities that will drive API design.

## The Components of a Job Story

Job stories are composed of three components using the “When, I want to, so I can" format:

- 1. **When:** The triggering event to establish causality is the situation or reason why the customer chooses the outcome. Triggering events are key indicators for when an API will be used.
- 2. **I want to:** The capability is what the customer has identified as the action that needs to be taken. The capability identifies the important role that the API will play to deliver the desired outcome. It is also used to deconstruct the operations that the API will deliver.
- 3. **So I can:** The outcome is the desired end state. It is the result of applying the capability when the triggering event occurs. The outcome delivers the acceptance for the API design.

Figure 3.2 shows an example Forgot Password job story, highlighting its three components.

The job story in Figure 3.2 demonstrates how a job story may be used to in the design of a digital capability. In this case, it captures a digital capability Reset My Password. This is one of many digital capabilities the API must offer to meet the needs of the target customers.

> ⁴. Alan Klement, “Replacing the User Story with the Job Story,” JTBD.info, November 12, 2013, https://njtbd.info/replacing-the-user-story-with-the-job-story-af7cdee10c27.
