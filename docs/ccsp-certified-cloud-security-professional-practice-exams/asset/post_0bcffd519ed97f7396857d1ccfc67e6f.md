
represents the last hop before leaving the application for external use, and would be the appropriate place to have a DLP implementation.

-   * A is incorrect because the server originating the traffic represents a first hop of network transmission, and the data may pass through other systems and network devices before leaving for external use. It would not be the optimal place for a DLP implementation.

-   * C is incorrect because firewalls and other network-monitoring solutions are between VLANs, which by nature are internal to a network and do not represent when data leaves for external use.

-   * D is incorrect because the server receiving the data would be a client where data in use becomes the appropriate stage; it is no longer data in transit once it reaches its destination.

## 9. Which of the following types of solutions is often used for regulatory compliance reporting?

-   A. SIEM
-   B. DLP
-   C. IRM
-   D. IDS

-   * A. A security information and event management (SIEM) solution is used to collect, aggregate, and process data throughout an application or even an entire infrastructure. It is often used to produce auditing and compliance reports based on the data that is collected and aggregated, and most SIEM solutions have very robust reporting, alerting, and dashboard capabilities.

-   * B is incorrect because data loss prevention (DLP) solution is used to protect sensitive information and how it is processed, handled, and disseminated. It is not used for reporting.

-   * C is incorrect because rights management (IRM) solutions are used to control how information is accessed and used, and is not a reporting tool or solution.

-   * D is incorrect because an intrusion detection system (IDS) is used to monitor data transmissions against known signatures and patterns, and to alert application owners or developers about anomalies or suspicious circumstances. It is not used for regulatory or compliance reporting.

## 10. Encryption solutions can be embedded within database operations that will serve to protect data in a manner that is not noticeable to the user. What kind of encryption strategy is this?

-   A. Transparent
-   B. Passive
-   C. RSA
-   D. Homomorphic

-   * A. Transparent encryption is used within a database to protect data as it is stored and processed, but it's done as an integrated database function and is not something that needs input from the application. The application doesn't even need to be aware it is being done. Transparent encryption is an effective tool because applications do not need to be rewritten or modified to handle encryption activities.

-   * B is incorrect because passive encryption is not a method of embedding encryption in a database system and its operations.

-   * C is incorrect because RSA refers to a specific type of encryption algorithm, not to a specific implementation of encryption. A transparent encryption system may use RSA as its cryptographic algorithm, but RSA itself is not to the question.

-   * D is incorrect because homomorphic encryption is a cutting-edge technique that allows for accessing and processing encrypted data without the traditional step of having to unencrypt it first. It is a type of encryption rather than a specific implementation, which is what the question is asking.

## 11. Which phase of the cloud data lifecycle also typically entails the process of data classification?

-   A. Use
-   B. Store
-   C. Create
-   D. Archive

-   * C. Data classification should optimally be done immediately as part of the "create" phase. As soon as data is created, it is subjected to regulatory and other protection requirements, so classification must be applied immediately.

-   * A is incorrect because the "use" phase is where data is first consumed and processed; however.

-   * B is incorrect because data needs to have a classification attached before it enters the "store" phase, as many security controls are implemented based on the way data is stored and protected. The manner in which the data is stored may also be highly dependent on its classification.

-   * D is incorrect because the "archive" phase is a much later part of the overall process, and data will have gone through storage, usage, and sharing long before it reaches archiving, so classification would need to take place earlier.

## 12. Your application generates large volumes of data based on customer input. With the large volume of incoming data, you need to be able to determine data discovery and classification as quickly and efficiently as possible. Which of the following methods for data discovery would be your best choice?

-   A. Content analysis
-   B. Labels
-   C. Metadata
-   D. Authorization

-   * C. Metadata uses attributes about the data itself, such as creator, application, type, data, or any other type of information to determine classification. Metadata is typically known as "data about data." By using metadata, where possible, you can make very quick and efficient determinations on classification.

-   * A is incorrect because content analysis is a very intensive and slow process for analyzing data to determine classification. It is also highly subjective because the data may not be normalized and consistent enough to accurately determine classification with any type of efficiency.

-   * B is incorrect because applying labels, although quicker than content analysis, is highly subjective and often done inconsistently. Labels rely on a process or users to correctly apply them in a consistent manner, whereas metadata uses attributes about the data itself.

-   * D is incorrect because authorization is the process of granting privileges and access to data or functions within an application; it is not related to the classification process at all.

## 13. When using an e-commerce site, you see your credit card information with all but the last four digits replaced with asterisks. What kind of data masking is being employed by the application?

-   A. Dynamic
-   B. Homomorphic
-   C. Static
-   D. Replication

-   * A. Dynamic masking is implemented between the data and application layers, and is applied in real time as data is requested and processed. This allows for showing only portions of a credit card number, for example, rather than the entire number that is contained in storage.

-   * B is incorrect because homomorphic refers to a type of cutting-edge encryption where data can be accessed and utilized without the traditional need to unencrypt the data set first. Although systems use homomorphic encryption throughout any type of process, it does not specifically relate to masking.

-   * C is incorrect because static masking creates a set of data, typically used for testing non-production environments. It is done as a separate process and outputs a distinct set of new data with masked values, and it's not done on a live system such as the one presented in the question.

-   * D is incorrect because replication refers to making multiple copies of data for either redundancy, high availability, or any use where a secondary copy is needed. It is not related specifically to masking, as replication involves making identical copies of data and not outputting it with masking in place.

## 14. During which phase of the cloud data lifecycle would technologies such as DRM and DLP be most appropriately utilized?

-   A. Use
-   B. Share
-   C. Store
-   D. Archive

-   * B. During the "share" phase, data is allowed outside of the original system and consumed by external users or services. This point, where data is leaving systems and consumed by others, is ideal for inclusion of DRM and DLP technologies to control how data is disseminated and ultimately used, as well as to control how far and wide it can be distributed.

-   * A is incorrect because the "use" phase is still within a controlled application and environment, where more stringent controls can be applied without relying on services and technologies such as DRM and DLP.

-   * C is incorrect because the "store" phase relies on different technologies for security, such as server controls, network controls, and encryption. DRM and DLP are focused on where data is transmitted consumed and would be more appropriate during the "share" phase.

-   * D is incorrect because archiving involves static copies of data for preservation, where technologies such as encryption would be appropriate. The use of DRM or DLP would not be necessary or appropriate because the data is not being transmitted, shared, or consumed in this phase.

## 15. In order to move quickly from your traditional data center to a cloud environment, you want your storage to resemble the same directory structure you currently have. Which cloud storage type will be your best option?

-   A. Object
-   B. Structured
-   C. Volume
-   D. Unstructured
