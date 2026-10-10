
Some of the techniques mentioned above are applied simultaneously. For example, we can apply image processing and anomaly detection algorithm to find out the anomaly behaviors of humans in surveillance videos. [Table 3.1](#chap3.xhtml#tab3-1) further lists some typical AI applications used in multiple domains.

**Table 3.1.** Explanation of some applications

| **Applications** | **Explanation and benefits** |
| --- | --- |
| Chatbot | * Automatic solution suggestion and recommendation, e.g., Q&A, knowledge base, etc.<br>* Omni-channel integrated with others, e.g., CRM. |
| Credit Scoring | * Profile customer risk more accurately, taking into account the person, not a stereotype. |
| Anti-fraud and Security | * Analyze documents for account registration (RegTech), detect anomalies in patterns within accounts, and more. |
| Robotic Process Automation (RPA) | * Replacement of routine repeatable works, e.g., invoice processing, payroll, sales order, customer/HR information processing (onboarding/offboarding), etc.<br>* Semi-automation in documentation, workflow, etc. |
| Asset Management | * Fast and accurate prediction to reduce the number of intermediaries, helping reduce operational costs. |
| Supply chain and inventory optimization | * Prediction for the best solution of inventory/route/supplier/etc. with lower cost. |
| IT system analytics | * Automated deployment, modularity, use of microservices, avoid excessive fine-grained optimization early on.<br>* Big Data analytics and predictive maintenance to prevent failure. |
| Collaborative Robot | * Completion of IT hardware/software installation/maintenance/monitoring/etc. |

### 3.3.1 General Applications

Compared to other traditional industries, such as manufacturing and food, FIs take the lead in AI adoptions, although sometimes they are a bit conservative in applying the latest ML development. AI techniques have been applied across all front, middle, and back offices at FIs, and cover various financial service areas, such as retail banking, wholesale banking, private banking, IT, audit, etc. [Table 3.2](#chap3.xhtml#tab3-2) summarizes some popular AI applications in the industry, such as price prediction, resource allocation, risk analysis, and loan or credit approval applications.

With these AI applications, FIs expect to achieve:

*   Better quality of services and customer experience;
*   Meliorated production lifecycle and improved production continuity and rhythm;
*   Increased automation, enhanced workforce efficiency, collaboration, and productivity;
*   Increased availability, accuracy, and consistency for operational and maintenance work.

In the following section, we will use general banking as an example to describe some typical applications. Large banks usually divide their organization into two parts, the group business (GB) and group functions (GF) as discussed in [Chapter 1](#chap1.xhtml). The GB normally contains the retail banking (it may also include private banking and wealth management), wholesale banking (it may also include corporate, commercial and institutional banking) and investment banking. The GF generally refers to support functions, e.g., legal, audit, compliance/risk, HR, finance, IT, and logistics departments. GB and GF may be integrated to an extent.

### 3.3.2 Retail and Private Banking

As more and more banks provide similar services and products, user experience becomes the key point to attract and retain customers.

Some customer-facing applications, e.g., chatbots and document RPA (it is defined in [Table 3.1](#chap3.xhtml#tab3-1)), adopt AI quickly to improve service efficiency and quality. For example, HBSC’s virtual assistant, Wells Fargo’s Facebook Messenger chatbot, United Overseas Bank (UOB)’s processing bot, and Bank of America’s mobile voice assistant “Erica” are replacing the work previously done by client service officers. Due to the strict requirement on accuracy, most of these robots have predefined question and answer pairs, which limits the usage of the latest generative NLP models. This is relieved for the internal staff facing chatbot, which may require a higher recall than a precision value. Thus, some latest reading comprehension (i.e., text understanding by AI engine) models can be directly applied to internal documents so that the chatbot can answer users’ questions.

**Table 3.2.** AI applications in FI

![](images/p89.jpg)

The basic objective of the RPA is to automate some routine repeatable works with a certain level of aid from software and hardware. Such routine work can relate to invoice processing, payroll, sales order, customer complaints, etc. The early stage of RPA is mostly rule-based, but now it becomes more powerful with the aid of ML techniques.

AI is also widely used in service centers, ranging from the service quality monitoring to automatic calling. For example, based on certain regulations in China, sales staff must clearly inform the clients about the risks of the financial products before they can sell it. These conversations shall be taped. Instead of conducting manual checks on the sample data, AI engines can be used to understand the whole population of conversations so that it can detect whether key information has been stated by the staff and consented by the client. Using sentimental analysis, we can further identify the mood of the client and staff, and assess his/her level of satisfaction with the service delivered.

AI-aid credit scoring systems are also widely used in banks to promote personalized and prompt decision-making. In some Chinese digital banks, e.g., WeBank (Tencent) and MyBank (Alibaba), the almost instant loans have been carried out for years.

Through various AI techniques with IoT (see [Chapter 10](#chap10.xhtml)) and automation, personality can be embedded into the products and services, such as personal financial assistant (robo-advisors) to manage your income, consumption, investment, loan, etc. Portfolio managers can also gain benefits for the portfolio optimization, selection, and allocation.

Thus, AI actually can accompany the customers for their full banking journey. For example, when a potential customer starts to apply for an account, she or he can use the chatbot for the questions encountered during the application. During the online application through web or mobile, the bank may use an AI robot to detect if the applicant is a human or a bot agent. After the required forms are filled and documents are submitted, the onboarding system will process some image documents using OCR, e.g., the scanned ID card, salary, and address proof. All the client information extracted will be further verified by due diligence steps, such as KYC. Together with the traditional credit bureau query, KG-based engine may provide a much wider knowledge about the applicant. An AI algorithm will suggest an approval or rejection decision to a bank staff. Once the application is accepted, the bank may use a profiling system to understand the customer better, which is further refined with the customer’s financial activities associated with the bank. The bank may use the third-party data, e.g., social network and e-commerce, to have a further enhanced “label” for the customer. A recommendation engine may help relation managers to provide some potential financial services or products to the customers by wisely using all the data. A transaction monitoring system is always running in the background to identify if a transaction is illegal.

### 3.3.3 Wholesale Banking

Wholesale banks are stepping up efforts to streamline receivable and payable processes of client accounts using AI technology. For example, AI-backed robots are used in front-end activities, e.g., secure customer identities, provide frictionless onboarding and streamline processes, and enhance user experiences.
