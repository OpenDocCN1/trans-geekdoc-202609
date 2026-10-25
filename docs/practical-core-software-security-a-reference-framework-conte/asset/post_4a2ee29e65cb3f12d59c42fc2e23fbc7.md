
Software executives, leaders, and managers must support the robust coding practices and necessary security enhancements as required by a business-relevant SDL as well as supporting the staffing requirements, scheduling, budgeting, and resource allocations required for this type of work. We have described the process, requirements, and management of metrics for people in these roles so that they can accurately assess the impact and resources required for an SDL that is relevant to and will work best in their organization and environment. Our approach has been designed from real-life, on-the-ground challenges and experiences, and we have described how to think about issues in order to develop effective approaches and manage them as a business process.

One style of SDL isn't relevant to all environments. What we have done in this book is provide you with a detailed framework in a Waterfall-type format that provides lists from which you can pick and choose to meet the needs of your environment or for full or partial (upgrade) software development needs. We will start this chapter with an overview of the top four environments you are likely to deploy your SDL in; then, we will summarize the key elements of our SDL reference framework as well as the top maturity models you are likely to build your SDL around, some final thoughts on enhancing your threat modeling practice as part of the SDL, and, finally, guidance on pulling it all together.

## 9.1 Overview of the Top Four Environments in Which You Are Likely to Deploy Your SDL

You can “build your own” SDL to build security into a process that is appropriate for your specific needs and environment, whether it be Agile, DevOps, Cloud, Digital Enterprise, or a combination of two or more of these. Each environment is described below.

### 9.1.1 Agile

Agile software development refers to software development life cycle (SDLC) methodologies based on the idea of iterative development, in which requirements and solutions evolve through collaboration between self-organizing, cross-functional teams. Agile development is designed to enable teams to deliver value faster, with greater quality and predictability and greater abilities to respond to change.¹

Scrum and Kanban are the dominant implementations of Agile, and Scrum is the one most often found in software development organizations. There’s Agile/Scrum as a formal, strict, tightly controlled process, and then there’s Agile/Scrum as it’s implemented in the real world. Implementation of Agile will vary from the fundamentalist and purist views to various elements that appear as Agile-like processes, and everything in between. It’s less important HOW it’s implemented in your environment than it is to understand WHAT your specific implementation means to your SDL.

### 9.1.2 DevOps

With the successful rise and proof of the viability of Scrum to speed up software development, further changes made to speed up HOW software is deployed came on the scene with the marriage of development and operations.

![](img/a54ed04827050a271316d34985425127_221_0.png)

Figure 9.1 Agile/Scrum framework (Source: Neon Rain Interactive, licensed under CC BY-ND 3.0 NZ).

Now, development teams and operations teams work together as partners for ongoing operations, enhancements, defect removal, and optimization of resources as they learn how their product operates in the real world.

As AppSec professionals engage in the planning for continuous integration/continuous deployment (CI/CD), DevOps, and new models for data center operations, DevOps began to transform into what we'll call DevSecOps.

Figure 9.1 is a simple depiction of how Agile and DevOps work in unison.²

Figure 9.2 shows what the marriage of Dev and Ops teams looks like when comprehensive security controls transform DevOps into DevSecOps.³

### 9.1.3 Cloud

As organizations migrated to new uses of cloud technology, such as Platform as a Service (PaaS), Infrastructure as a Service (IaaS), and containerization, it became obvious that a lift and shift strategy was not going to fly. Rather, these new ways of operating data centers required rethinking how applications are built, deployed, and used. Large, monolithic applications started undergoing a refactoring process to break up the applications. This activity involves isolating functions (services) around a central concept or entity—for example, one microservice might deal with all the functions needed to create a client entity, another microservice might represent the sales entity, yet another might represent order processing, and so on. These microservices are activated using an application programming interface (API) that describes what functions are available to access and what attributes are involved. These APIs are most often developed using the representational state transfer,⁴ or REST, architectural style.

### Security practices on DevOps continuum -> Dev[Sec]Ops

- Analysis -> Learning
- Defect/Incident 3-step
- New attack surface?
- Plan to update threat model

- Restore/maintain service for non-attack usage

- RASP auto respond
- Roll-back or toggle off
- Block attacker
- Shut down services

- Intrusion detection
- App attack detection

- Log information for after-incident analysis

- Configuration validation
- Feature toggles / Traffic shaping configuration
- Secrets management

- Pen testing (Vulns found -> Test scripts)
- Compliance validation (PCI, etc.)
- Fuzzing

- If we do X will it mitigate?
- Capacity forecasting
- Learning -> Update playbooks and Training

- Test security features
- Common abuse cases

- Break the build
- code analysis

- Static/IAST analysis
- Abuse case tests
- Code review

- Threat modeling -> backlog items
- Analyze/Predict -> backlog items
- Design complies with policy?

Figure 9.2 DevSecOps cycle (Source: Retrieved from https://twitter.com/lmaccherone/status/84334674967097888512. Used with permission of L. Maccherone, Jr.).

Application development using these microservices entails developing a series of API invocation processes that perform useful work without concern for how these services are implemented, while permitting enhancement and changes to occur without interface changes to isolate the need for rebuilding every application that needs those services.

Traditional SDL mapping needs to be adapted to make it feasible to build and deploy code where the velocity of deployments can be 100s or 1000s of changes a day. It increases the need to make accurate threat models with a granular understanding of trust boundaries (e.g., between microservices).

One should ask if every API update needs all SDL activities. For feasible SDL activities, triggers should be defined to kick off high-impact ones (e.g., dynamic security testing).

### 9.1.4 Digital Enterprise

A digital enterprise uses technology to enable and improve business activities to achieve a competitive advantage. This is why many start-ups have an advantage over established competitors. They are able to start out small with agile business practices that are fast, agile, innovative, and disruptive. Larger institutionalized companies must now move quickly to digitize all of their operations to compete. This typically involves rapid and dramatic change. The ability to respond to a changing marketplace is critical for their success. The principles used for Agile, DevOps, and the cloud described in Sections 9.1.1 to 9.1.3 are used to build and enhance the successful operations for a digital enterprise.

The traditional Waterfall method for software development is not feasible or practical for the iterative product release cycle required for the digital enterprise. The elements of the Agile development process and CI/CD should use early user testing, customer analytics, and prioritization based on user feedback, thus providing a smoother path toward enhancing the business value chain. Agility is achieved by eliminating wasted effort, thereby speeding up the product release lifecycle. Automation, orchestration technology, and APIs are used to reduce or eliminate manual security processes and interactions to shorten development times and deliver new features, fixes, and updates aligned with the business. This will reduce the release times, raise quality levels, and increase the productivity of the team members, as well as facilitate security operating at speeds required in a cloud environment. Enterprise environments typically include employee productivity tools (Slack®, Office 365®, messaging, emails) and business systems such as CRM and HR (e.g., Workday®). Similar to the cloud, enterprise development needs can be quite different from traditional products. The technology stack is likely to be Microsoft®-based. Increasingly, on-prem business applications are being replaced by Software-as-a-Service (SaaS) applications.

As more companies have moved to public cloud services due to the end-to-end digital transformation, from the customer interface through the back-office processes, security challenges have significantly increased with the ever-changing and increasing footprint and attack surfaces. Building security into the software development process as described in this book has never been more important, and it is core to the successful operation of a digital enterprise. Integrating third-party SaaS applications through APIs increases the attack surface and changes trust boundaries in many cases. This supply-chain integration risk is enhanced today; in all likelihood, the application stack is changing every day. SDL managers should pay special attention to location-specific regulatory and privacy requirements.
