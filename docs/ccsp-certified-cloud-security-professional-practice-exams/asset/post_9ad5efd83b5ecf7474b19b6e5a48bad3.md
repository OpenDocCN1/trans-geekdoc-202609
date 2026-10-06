
D is incorrect because headers are very-similar-to column names and represent information about the data and how it is organized or categorized. They are also considered metadata and descriptive in nature.

43. Different types of cloud deployment models use different types of storage from traditional data centers, along with many new types of software platforms for deploying applications and configurations. Which of the following is NOT a storage type used within a cloud environment?

- A. Docker
- B. Object
- C. Structured
- D. Volume

A. Docker is a container method for building, shipping, and running applications across different platforms and clients. It runs within its own agents and containers, not a storage type under a cloud deployment model, and can be used with virtually any type of platform.

B is incorrect because object storage, where data is stored as an opaque file handler or descriptor in a flat file system, is an official cloud storage type used with Infrastructure as a Service (IaaS).

C is incorrect because structured storage, where data is stored in a database-type application, is an official cloud storage type used with Platform as a Service (PaaS).

D is incorrect because volume storage, where data is stored on a logical partition resembling a traditional file system hierarchy, is an official cloud storage type used with Infrastructure as a Service (IaaS).

44. When data is required to be acquired and retained for extended lengths of time, which of the following becomes the most pressing concern over time?

- A. Encryption
- B. Size
- C. Restoration
- D. Availability

C. As time passes and organizations change out software and other technologies, it is imperative that the ability to restore archives is maintained. Given that regulatory requirements are several years or longer, and with the rapid development of technology and upgrades, it is possible without proper planning for an organization to end up deprecating the capability to restore archives before they have reached their minimum retention time. When this happens, an organization would likely have to contract with a third party, likely at a very high cost, for restoration services should the need arise.

A is incorrect because the concern with encryption is the protection of keys over time, but the underlying technology and capabilities will still exist down the road. This is different than with software and other technologies used to create and store archives, where the prospects of being deprecated are much higher.

B is incorrect because although the size of archives can be a concern, especially for longer retention periods, it is not the type of concern that will change over time or result in issues with deprecated technology. Archives by nature do not change, size will not increase with data that is already archived, and additional storage can always be added, as needed, to handle longer retention requirements, as opposed to concerns over time with software versions and access.

D is incorrect because archives typically are housed in less accessible areas of storage, many times on tapes kept at external facilities. When the need for restoration arises, it may take some time for archives to be retrieved and restored. There is no need for archives to be immediately available, and the contract or SLA with a service provider should document the required or expected restoration times, ensuring they also will satisfy any regulatory requirements.

45. Which of the following data protection methodologies maintains the ability to connect back to the original values?

- A. Tokenization
- B. Anonymization
- C. Obfuscation
- D. Dynamic mapping

- A. Tokenization replaces data fields with opaque handlers or descriptors. In the process, the original and sensitive information is removed from the data, and the token values can be mapped back to the original values if needed.

- B is incorrect because anonymization removes direct identifiers from data sets to protect sensitive information and prevent data from being matched up with an identity. However, the goal of anonymization is not to be able to map back to original data like possible with tokenization.

- C is incorrect because obfuscation often replaces values with garbage or random data, and as such, it's not possible to map back to the original values. Obfuscation is typically used to make data sets for development or non-production systems for testing that follow the format of production data but not the actual values.

- D is incorrect because dynamic mapping can refer to many things within a system or application, but in this instance it's provided as an erroneous choice.

46. Which of the following is not a commonly accepted strategy for data discovery?

- A. Labels
- B. Metadata
- C. Signature hashing
- D. Content analysis

- C. Data discovery is focused on the three main areas: labels, metadata, and content analysis. Signature hashing may be used for some of these methods for comparison and efficiency, but it would be used as a tool or process rather than one of the key strategies.

- A is incorrect because labels, which are applied to data for grouping or organization, are commonly used for the data discovery processes. The main shortcoming with using labels is that the process is dependent on the accurate and complete application of labels before the data is processed.

- B is incorrect because metadata, or data about data, is commonly used as a strategy for discovery and classification. Metadata uses attributes such as type, creator, and other identifying information about the data itself to make determinations for discovery.

- D is incorrect because content analysis is done against the actual data itself, even if it is the slowest and least accurate method. However, as tools become more mature and efficient, the use of content analysis is rapidly growing and becoming more accurate and useful.

47. Although the preservation and retention of data are the most important concepts that usually come to mind when you're considering archiving, what process is equally important to test regularly for the duration of the required retention period?

- A. Recoverability
- B. Portability
- C. Encryption
- D. Availability

- A. Over time, data can become inaccessible if an organization loses the technologies used to archive. Regular tests should ensure data can be recovered.

- B is incorrect because portability is the quality of being able to move between cloud providers. With static storage, portability is not a primary concern, nor should it be an impediment.

- C is incorrect because encryption methods will still be available as long as the keys are properly maintained and secured. This is independent of the cloud provider or system.

Chapter 2: Cloud Data Security Domain

D is incorrect because availability is not a primary concern with archiving. Typically, offsite storage or storage services are used with archiving, in which case immediate availability will not be possible, and some period of time, by regulation, is allowed for producing records.

48. You are reviewing the standard offerings from a prospective cloud provider, and one area of log collection promises full and complete access to operating system logs for provisioned systems. Which service service category is this likely referring to?

- A. Platform
- B. Desktop
- C. Software
- D. Infrastructure

D. With Infrastructure as a Service (IaaS), the cloud customer is responsible for the provisioning, configuration, and support of operating systems and virtual machines. As such, the customer has full access to all systems and operating system logs, whereas with the other service categories, these would not be provided.

A is incorrect because in Platform as a Service (PaaS), the operating system is maintained by the cloud provider and is its responsibility, so chances are that full access to operating system logs will not be provided or even possible. A subset may be made available through certain tool sets or a SIEM solution, but direct and full access is typically not provided.

B is incorrect because Desktop as a Service (DaaS) works like SaaS, where the cloud provider is responsible for the overall system, platform, and software, and would not make full operating system logs available to the cloud customer, nor would the cloud provider necessarily provide a high level of value.

C is incorrect because the operating system with Software as a Service (SaaS) is solely the responsibility of the cloud provider, who itself would retain full access to operating system logs. Because the cloud provider is solely responsible for the logs, there would be little need for the cloud customer to access.

49. Which of the following will always serve as the starting point for the minimum period of data retention?

- A. Contract
- B. Regulation
- C. System resources
- D. Company policy

B. Regulation will dictate, based on the type and content of data, the minimum period of data retention, as well as what events must be captured for retention. Regulation is specific to the type of data and the jurisdiction where it is located or consumed.
