
## 8 Case studies

### Case study #1 – Möbius solution

Möbius is an industry-leading digital learning platform that excels at creating and deploying interactive teaching and assessment content for higher-educational institutions around the world. Currently, ABC University uses Maple TA, which is a vendor-built, on-premises testing and assessment software solution. The intent of this initiative is to migrate this platform to a software-as-a-service (SaaS) version of this solution known as Möbius. The Möbius Platform offers an interactive, online approach for ABC University students interested in pursuing science, technology, engineering and math courses. This initiative will also facilitate integration with the university’s learning management system (LMS). The students’ information, grades and courses will reside within this application.

### Questions

- 1. Determine the inherent risk.
- 2. Assess the internal control environment using the NIST Cybersecurity Framework: Core Components.
- 3. Determine the risk appetite, risk tolerance and risk profile.
- 4. Assess the residual risk and provide recommendations, if appropriate.
- 5. Develop the risk-mitigation strategy.

### Solution

### Business overview

With more than 15 years in the market, the Möbius Platform is used by students, teaching assistants and professors at some of the largest institutions worldwide. Möbius is a robust online authoring and delivery environment specifically designed to meet the needs of science, technology, engineering and mathematics (STEM) classrooms. It includes a suite of tools and features for authors aiming to design and develop digital assets for their students or peers and a delivery environment that enables and promotes deep and active learning for users through the combination of instructional material and hands-on activities.

The Möbius Platform offers the following:

- A mechanism for creating and deploying online STEM courses.
- Lessons, assessments and interactive learning activities that unfold the potential for STEM students to acquire knowledge at a guided, yet self-defined, pace.
- Complex STEM disciplines with its world-class math engine.
- The ability to create and use powerful multimedia visualizations to anchor key STEM concepts.
- Immediate and meaningful feedback to students and data on student engagement and understanding for instructors.
- Advanced question types with algorithmically generated and randomized questions.
- Access to high-quality content created by curriculum experts.
- Seamless integration with ABC’s LMS.

### Technical overview

The Möbius Platform is vendor owned by DigitalEd. This cloud-based solution is hosted within the Google Cloud Platform (GCP) System and the Alibaba Cloud.

### Risk assessment

### IMPACT AND LIKELIHOOD

The impact and likelihood rating scale outlines the evaluation of the protection requirement level for each protection requirement. Table 8.1 shows the impact and likelihood rating as it applies to the risk elements.

### INHERENT RISK

The inherent risk has been assigned based on one of three scores of high, medium or low, as shown in Table 8.2.

ABC University (AU) Employees & Students
![](img/8bcb92bad95ddd74218ba966f2798d54_123_0.png)

DigitalEd Employees
![](img/8bcb92bad95ddd74218ba966f2798d54_123_1.png)

Möbius COURSEWARE
![](img/8bcb92bad95ddd74218ba966f2798d54_123_2.png)

Aliyun Location: China
![](img/8bcb92bad95ddd74218ba966f2798d54_123_3.png)

Google Cloud Platform (GCP) Location: 1) North America, 2) EU & UK, 3) Australia
![](img/8bcb92bad95ddd74218ba966f2798d54_123_4.png)

Figure 8.1 The technical overview of the Möbius Platform.

Table 8.1 The impact and likelihood rating scale as applied to the risk elements.

| Risk Element | Impact | Likelihood |
| :--- | :--- | :--- |
| **1 Data Classification**<br>PII: The protection of PII is subject to routine risk-assessment processes. A privacy impact assessment (PIA) is managed by ABC’s FOIP office. PII elements are captured and stored through this cloud-hosted web application platform—specifically, any personal information that is used regarding an ABC student to include but not limited to the following:<br>• Student information.<br>• Grades.<br>• Course information.<br>• Connectivity to the Learning Tool Interoperability.<br><br>Sensitive Authentication Data (SAD): This is the information on a payment card used for authentication at the time of a purchase. This includes data from the full magnetic strip, card security code (CSC, CVV2, CID, CAV2), and personal identification number (PIN). The Möbius Platform facilitates payment card transactions from ABC individuals, so the protection of SAD is required by DigitalEd. | Major | Frequent |
| **2 Business Requirements**<br>The Möbius Platform is used within the ABC student environment to provide a comprehensive online courseware platform focusing on the unique needs of STEM students. | Moderate | Likely |
| **3 Application Development**<br>Application development is minimal to include integration with the Möbius Platform. Development includes a standard interface within the university’s LMS and connectivity to learning tool interoperability (LTI). | Minor | Possible |
| **4 Vendor Relationship**<br>DigitalEd is a privately held Canadian company, with approximately 65 employees worldwide. DigitalEd is an online learning company with a simple and resonant purpose to shape the world through digital learning. DigitalEd introduced the Möbius Platform in spring 2017 with the intent of improving the online learning experiences of authors, instructors and students in STEM-based classrooms. | Moderate | Likely |
| **5 Technology Landscape**<br>Suppliers and third-party partners include the GCP System and Aliyun. | Major | Frequent |
| 6 Legal/Regulatory<br>Disclosure of data subject to specific regulatory requirements.<br>Lawsuits by aggrieved owners of lost or compromised data—that is, PII.<br>Fines and penalties assessed by regulators. | Major | Possible |
| 7 Brand/Reputational<br>Unflattering or negative publicity due to press coverage that damages ABC's brand.<br>Loss of customer confidence due to the release or compromise of data. | Minor | Possible |
| 8 Operational<br>Loss of operations and use of the system by authorized users. | Moderate | Likely |
| 9 Financial<br>Significant costs to restore/repair any damages caused by intentional/unintentional users. | Minor | Possible |
| 10 Security and Fraud Issues<br>Loss and/or manipulation of sensitive data—that is, PII—through disclosure of authentication credentials, DDoS attacks or malware attacks. | Major | Frequent |

Table 8.2 The inherent risk rating scale as applied to the risk elements.

| Risk Element | Impact | Likelihood | Rating | Qualitative Inherent Risk Rating |
| :--- | :--- | :--- | :--- | :--- |
| 1 Data classification | 4 | 5 | 20 | High |
| 2 Business requirements | 3 | 4 | 12 | High |
| 3 Application development | 2 | 3 | 6 | Medium |
| 4 Vendor relationship | 3 | 4 | 12 | High |
| 5 Technology landscape | 4 | 5 | 20 | High |
| 6 Legal/regulatory | 4 | 3 | 12 | High |
| 7 Brand/reputational | 2 | 3 | 6 | Medium |
| 8 Operational | 3 | 4 | 12 | High |
| 9 Financial | 2 | 3 | 6 | Medium |
| 10 Security and fraud issues | 4 | 5 | 20 | High |
| Average | | | 12.6 | High |

### Internal control environment: Effective

The core components of the NIST Cybersecurity Framework were utilized to adequately assess the DigitalEd environment supporting the Möbius Platform. Specifically, the following suppliers and third-party partners provided internal control documentation: (1) Higher Education Community Vendor Assessment Tool (HECVAT)—Lite: DigitalEd, (2) System and Organization Controls (SOC) 2 Type II Report: GCP System for May 1, 2019, to April 30, 2020, period and (3) the Payment Card Industry (PCI) Data Security Standard (DSS) self-assessment questionnaire (SAQ) as of March 21, 2019.

### ASSET MANAGEMENT

- Physical devices and systems within suppliers and third-party partners—that is, DigitalEd and Google—are inventoried.
- Software platforms and applications within suppliers and third-party partners—that is, DigitalEd and Google—are inventoried.
- Organizational communication and data flows are mapped.
- External information systems are catalogued.
- Resources—that is, hardware, devices, data, time, personnel and software—are prioritized based on their classification, criticality and business value.
- Cybersecurity roles and responsibilities for the entire workforce and third-party stakeholders—that is, suppliers, customers and partners—are established.
- Google has policies and procedures in place to establish acceptable use of information assets.
- Google has established policies and guidelines to govern data classification, labelling and security.

### BUSINESS ENVIRONMENT

- The university's role in the supply chain, critical infrastructure and its industry sector is identified and communicated.
- The priorities for DigitalEd's mission, objectives and activities are established and communicated.
- The dependencies and critical functions for the delivery of critical services are established.
- The resilience requirements to support the delivery of critical services are established for all operating states—that is, under duress/attack—during recovery or under normal operations.
