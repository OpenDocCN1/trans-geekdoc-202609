
Since its creation, the Guidance has been updated multiple times (now at version 4) and continues to serve countless enterprises looking to securely adopt cloud services. The Guidance itself is the basis of the Certificate of Cloud Computing Knowledge (CCSK) designation. This book is written to help you understand the various domains of knowledge covered by the CSA Guidance as well as the companion document (ENISA) so you can pass your CCSK exam and be a professional who helps companies address appropriate security for cloud environments of all types.

### Why Get Certified?

- Companies of all sizes are adopting cloud services. These companies have realized that securely implemented and managed cloud services are not the same as traditional computing and require specialized professionals to ensure the security of this new era of computing. The CCSK is the industry's first cloud security certification. Over a decade later, it is still widely regarded as the leading industry certification, proving that holders possess the qualifications and capabilities to address cloud security across a broad range of domains. Obtaining the CCSK certification demonstrates to employers that you possess the knowledge required to properly handle security controls in any cloud environment.

### How to Get Certified

You take the CCSK exam online; it is not a proctored exam. You can take it on any device with network access, at a time of your choosing. There are no experience requirements, but general IT security experience is very helpful for your likelihood of success. As of this writing, the exam contains 60 questions, lasts 90 minutes, and requires a score of 80% or higher to pass. The exam is open-book, but—do not misunderstand—it is a very difficult exam.

To prepare for the exam, I recommend that you understand the concepts covered in this book and review the primary documents upon which the exam is based. These documents are the CSA Guidance (v4) and ENISA Cloud Computing Benefits, Risks, and Recommendations for Information Security. These documents are available for free on the Cloud Security Alliance website. I strongly recommend that you keep these documents accessible during the exam. I also recommend that you have two monitors if possible. One for the exam itself, and the other for the Guidance and ENISA documents, as well as the latest version of the Cloud Controls Matrix.

There are three caveats about this exam: First, like all technical exams, you can expect the test writers to try to "trick" you. You need to understand what the question is really asking. The second point is not to have a false sense of security because the exam is open-book, because you only have 1 minute and 30 seconds per question (60 questions in 90 minutes). Do not think you can look up every question, and please do not open Google. They are testing your knowledge of CSA best practices, not what someone on the internet says.

Finally, trust the knowledge you have learned from this book and answer the questions with your intuition. Everything in this book has been written to fully prepare you for any question you may encounter on the CCSK exam. Do not change your answers lightly unless you are proven wrong by a subsequent question. Nine times out of ten, you will overthink the answer and change it to the wrong one. Understand the question, trust your intuition, and move on to the next question.

After passing the exam, you will hold the CCSK certification for life. The exam version is updated in sync with updates to the CSA Guidance. For example, both the current Guidance and CCSK are version 4. There is no need to apply for Continuing Professional Education (CPEs), no Annual Maintenance Fees (AMFs), and CSA will not "revoke" your certification because you haven't taken another exam in a while (looking at you, all vendor certifications). As you can imagine, updating to the current version in the future is wise, but let's get certified first.

### CCSK Domains

The scope of knowledge you need to be tested on is very broad, covering multiple domains. This is why the CCSK exam is difficult to pass, and therefore valuable. This is not a "you can configure a security group" exam. It is a vendor-neutral exam covering everything from Governance, Risk, and Compliance (GRC) to understanding the proper security controls for new technologies such as big data, serverless computing, and containers. Below is an overview of the 14 domains covered in the CSA Guidance and ENISA documents.

#### Domain 1: Cloud Computing Concepts and Architectures

This domain provides the foundational knowledge for cloud security standards, including references to standard literature from organizations such as NIST and ISO. Key content covered includes essential characteristics, service models, deployment models, and the logical model. A key takeaway from this domain is the logical model. Understanding this model is critical to truly understanding the shared responsibility that a company assumes when adopting any type of cloud computing.

#### Domain 2: Governance and Enterprise Risk Management

Governance and risk management are extremely broad topics. This domain focuses on the changes to governance, risk management (both enterprise and information), and information security functions after adopting cloud services. The importance of due diligence is emphasized here. If you store regulated data with a Cloud Service Provider (CSP), and that CSP uses a remote storage service lacking certain security controls, you are ultimately liable. Although the CSP chose to use that low-security storage solution, you still face the consequences of their actions in court and before regulators. In other words, you can never outsource accountability, so be sure to perform due diligence.

#### Domain 3: Legal Issues, Contracts, and Electronic Discovery

Building on governance, this domain covers the legal implications of adopting and providing cloud services. It deals with legal issues (such as jurisdictional requirements and e-discovery), third-party contracts, and third-party access to data stored in cloud environments. When considering the legal implications of the cloud, remember the following. First, laws are being written as we speak, and there is a lack of precedent to guide lawyers in execution, which is true globally. Second, unless you are the company's legal counsel, you have no business advising the company on the legal implications of the various jurisdictional pitfalls related to the cloud. Your goal is to understand the potential problems the cloud may bring and to advocate for legal support when necessary.

#### Domain 4: Compliance and Audit Management

Compliance is the function of ensuring policies are followed, and auditing is the key function of ensuring people follow the guidance (proving or disproving compliance). Simple, right? The good news in this domain is that most of what you do in traditional IT remains similar in the cloud. The bad news is that your cloud implementation often does not follow security policies because no one is watching. Why is no one watching? Good question. To answer it, you need to think about who is educating business owners on the risks of the cloud (hint: the vendors). This domain discusses what to look for when incorporating the cloud into existing compliance and audit procedures.

#### Domain 5: Information Governance

- Does management and information security protect the system, or the information stored in the system? What causes a company to make a mistake so severe that it makes the front page of a national newspaper? The answer is: disclosure of consumer information. Now consider this data in the cloud. What is the data classification level? Where is it stored? How is it protected? Who has access to the data? These are some of the questions you need to address when considering the governance and protection of data stored in the cloud. This domain covers these topics, and more.

#### Domain 6: Management Plane and Business Continuity

The management plane is the way everything in a cloud environment is built and managed. You can think of it as the **Human-Machine Interface** for the internal workings of a cloud implementation. Securing this **Human-Machine Interface** is the single most critical aspect of a secure cloud environment, regardless of the service model used. Want to click a box to encrypt Software as a Service (SaaS) data? Management plane. Want to build a new server instance? Infrastructure as a Service (IaaS)? Management plane. Want to establish a failover region and replicate data or images across the country or globe nightly to support disaster recovery and business continuity requirements? You guessed it, management plane. In IaaS, how do you plan and build business continuity and disaster recovery? If you have already done so? Where are the log files stored? In the event of an account compromise, are they protected? If your protection scheme is agent-based, and the cloud's vulnerability assessment is limited to running scans against IP addresses, you need to rethink your options in the new environment.

#### Domain 7: Infrastructure Security

This domain covers the security of the cloud infrastructure itself, including the physical and virtual resources that make up the cloud. It discusses network security, host security, and the security of the management plane components that are part of the infrastructure. It also covers the shared responsibility model for infrastructure security between the CSP and the customer.

#### Domain 8: Virtualization and Containers

Virtualization is the core technology of the cloud, and it is not just virtual machines. Virtualization is how pools of compute, network, and storage resources are created and managed, and it drives the multi-tenant nature of cloud services. In this domain, we focus on the division of responsibility for securing various virtualization technologies—what the provider needs to supply, and what the consumer needs to do. You will find that the virtualized network technologies we are accustomed to using as IT professionals have become outdated in this new environment. The second part of this domain covers container-related components and how to secure them.

#### Domain 9: Incident Response

As the old saying goes, failing to plan is planning to fail. Unless you have planned and continuously tested your **incident response** capabilities in the cloud environment, your company will inevitably be caught off guard when an incident occurs, and the first question from the incident response team will be: "Who do we contact to disconnect the server from the network?" Does your incident response team have the virtual tools needed in the new virtual environment? Has the incident response process been completely re-engineered to accommodate cloud services? Many aspects can remain unchanged during cloud migration, but incident response is not one of them. New processes leveraging cloud services can reduce downtime from **hours** to **minutes**.

#### Domain 10: Application Security

Application security for applications migrating to the cloud does not change because they run in the cloud. Cloud-native applications are a completely different story. These cloud-native applications may initially authenticate using **permanent credentials** (such as access keys) or **temporary credentials** (such as role assumption). If permanent credentials are used, how are these credentials rotated per policy? If temporary credentials are used, how are they audited to ensure least privilege (after all, developers will develop)? What happens if a new cloud-native application relies on multiple Cloud Service Provider (CSP) services, some of which are prohibited by the company because they have not passed independent third-party assessment?

#### Domain 11: Data Security and Encryption

Encryption considered "sufficient" in the cloud is mostly based on data classification. When encryption is required by regulation or policy, you need to consider three factors: **data location**, **encryption engine location**, and **key location**. Your company's risk tolerance is unique. Some company policies require on-premises key management, while others only need to "check the box" (literally). This domain explores the trade-offs of different Encryption as a Service models (such as provider-managed and customer-managed keys).

#### Domain 12: Identity, Entitlement, and Access Management

Your first checkpoint when implementing or evaluating a cloud service, and forever will be, **access control**. As with traditional IT, the best practice is the **principle of least privilege**—grant users only the access they need to do their jobs, and no more. This is, of course, basic. Therefore, there should also be no cases where access permissions for millions of customers' Personally Identifiable Information (PII) are granted to the whole world, although this has happened repeatedly. But what is not basic? Permissions granted via JSON scripts, which need to be validated in any assessment or audit of IaaS. You need to understand how these authorizations are processed and what their effective permission set is.

#### Domain 13: Security as a Service

Security as a Service (SecaaS) enables you to protect cloud and traditional assets through cloud services. When capabilities. The main changes are "who" is responsible for the controls, and "how" they are implemented. For example, if you use a SaaS system to process Personally Identifiable Information (PII), and the provider you use does not encrypt the data, resulting in a data breach, you will be liable to your customers and regulators. Is telling the customer "we assumed the provider encrypted the data, but we were wrong" a valid defense? In some cases, the responsibility for implementing security controls may shift to the Cloud Service Provider (CSP), but please note that your company is always responsible for security and privacy, regardless of which party implements the controls.

Enterprise governance and policies do not change when moving to the cloud, but they must be extended to cover cloud services. When adopting public cloud services, remember that you are building a cybersecurity supply chain based on a third party (over which you have almost no control). For example, a 2017 McAfee study showed that 52% of surveyed enterprises explicitly stated they had traced malware infections back to SaaS applications. This is just one example of why you must perform due diligence on any provider you rely on to securely store or process your data. Currently, there is a disconnect across industries between what CSPs should perform for customers and what they actually perform (or provide to customers to satisfy policies). Many business owners expect SaaS providers to handle everything for them. Think about it: if no one in your company is responsible for maintaining the Identity and Access Management (IAM) provided by the provider, how do you satisfy the "revoke credentials upon termination" policy?

![Images](img/note.jpg)

**NOTE**    To read the study "Building Trust in a Cloudy Sky", visit [`https://www.mcafee.com/enterprise/en-us/assets/executive-summaries/es-building-trust-cloudy-sky.pdf`](https://www.mcafee.com/enterprise/en-us/assets/executive-summaries/es-building-trust-cloudy-sky.pdf).

Once the basics are covered, cloud security seems pretty straightforward, doesn't it? Perform due diligence, assign people to manage the security settings provided by the provider, and everything will be perfect. This applies to SaaS. The IaaS story is completely different.

As repetitive as it sounds, IaaS is exactly what you make of it. If you migrate a "traditional" application from a data center to an IaaS provider, then security at the application (applistructure) and data (infostructure) layers does not change. Operating system security remains the same, and the application's own security controls are unchanged. Your team already knows how to configure and secure these, right? What is completely different is the virtual environment (metastructure) on which the application runs, and the physical (infrastructure) environment belonging to a third party in a public cloud deployment—which you likely cannot access. Most of this book deals with security controls for prevention, detection, and response capabilities at the metastructure layer.

On the other hand, building cloud-native applications puts your company in a whole new world, where security controls may be provided by the vendor, may be limited, or may not exist at all. Stateless serverless applications call unknown services and have unknown dependencies, which may bring security and licensing issues. Even if the application uses approved services, you still need to consider the privilege level used to access these services. Are developers using permanent credentials or temporary credentials?

Then there are free cloud services. You might expect CSPs to provide full transparency to customers, but do you really expect a "pay-as-you-go" provider to claim that use of its "free" products grants it ownership of all data stored in its environment? Otherwise, how would they grow their customer base?

Looking at the big picture, the 80/20 rule of cloud security applies once again—that is, 80% of what you have always done as an IT security professional remains the same, while the 20% that changes completely changes the game.

I hope I have successfully captured your attention and made you excited to begin your cloud security certification journey. Let's start securing your potential! You can do it!

## Chapter 1

## Cloud Computing Concepts and Architectures

This chapter covers the following topics from Domain 1 of the CSA Guidance:

- Cloud Logical Model
- Cloud Computing Definitions
- Cloud Service Models
- Cloud Deployment Models
- Reference and Architectural Models
- Cloud Security, Compliance Scope, and Shared Responsibility Model
- Key Areas of Concern for Cloud Security

*The beginning is the most important part of the work.*

*—* Plato

As Plato said, the beginning is the most important part of the work, so we should start by establishing a solid foundation. This chapter serves as the cornerstone for subsequent chapters and contains the concepts you need to understand to become a CSA Certificate of Cloud Security Knowledge (CCSK) candidate. This chapter describes and defines cloud computing, establishes baseline terminology, and details the overall logical and architectural frameworks, such as the International Organization for Standardization/International Electrotechnical Commission (ISO/IEC) 17789 standard and the National Institute of Standards and Technology (NIST) 800-145 and 500-292 standards, which are discussed throughout this book.

![Images](img/exam_tip.jpg)

**EXAM TIP**    In this book, you will see numerous references to NIST and other organizational standards. Do not leave this book to study those documents. The CCSK exam is based on CSA Cloud Security, not NIST standards. The exam is open-book; if you encounter a question referencing a specific publication number (the number, not the content), you can quickly look it up in the CSA Guidance. Regarding the content of the CSA Guidance itself, this book covers all the knowledge you need for the exam (and more).

Although cloud services are presented to consumers in a user-friendly form, the implementation required behind the scenes to support up to 1 million customers is completely different from what even the most experienced IT professionals are used to. Cloud Service Providers (CSPs) create and manage a service consisting of resource pools (compute, network, storage) accessed by controllers using Application Programming Interfaces (APIs). It is through these resource pools and API access that many of the cloud's key characteristics (such as self-service, elastic scaling, and resource pooling) are realized. The high-level schematic in `Figure 1-1` below illustrates the critical role of the controller in providing abstraction (you do not need to access hardware directly) and orchestration (coordinating processes) to serve resources. In short, you request resources (compute, network, storage) from the controller, and the controller handles the rest.

```
Figure 1-1
```

* * *

**`Figure 1-1`**    Cloud Controller and Resource Pools. (Used with permission from Cloud Security Alliance.)

![Images](img/note.jpg)
