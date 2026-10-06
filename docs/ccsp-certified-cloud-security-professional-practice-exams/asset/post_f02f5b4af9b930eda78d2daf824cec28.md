
C is incorrect because integrity can be assured through traditional permissions by denying the ability to write or delete data. If permissions are granted to modify or delete data, through traditional permissions there is not any mechanism to limit how much of the data or what portions of it can be modified or for how long, as IRM could.

D is incorrect because the ability to copy is inherent with the ability to read data. If a user can access a file to read, he can also copy it, either directly copying the file as a whole unit or copying the data out of it and into another source. IRM is capable of preventing data from being copied even if the user can read it.

## 29. When an organization implements a SIEM system and begins aggregating event data, the configured event sources are only valid at the time it was configured. Application modifications, patching, and other upgrades will change the events generated and how they are represented over time. What process is necessary to ensure events are collected and processed with this mind?

- A. Continual review
- B. Continuous optimization
- C. Aggregation updates
- D. Event elasticity

- B. Continuous optimization is the process where event data is evaluated on an ongoing basis to catch any changes in formats or additional data sources. Applications are always changing, and without continuous optimization, event data would likely become stale or incomplete before long.

- A is incorrect because the term “continual review,” although it sounds similar to continuous optimization, is not the term used for what the question is asking.

- C is incorrect because the term “aggregation updates” does sound similar and captures the essence of what continuous optimization does, it is not a real term or commonly.

- D is incorrect because “event elasticity” is a made-up term for the purposes of the question, does it capture the concept of event data pairing with the elastic nature of cloud environments. However, it is not pertinent to the question.

## 30. Applying restrictions on certain activities requires the use of information rights management (IRM). Which of the following would NOT require an IRM solution?

- A. Copy
- B. Rename
- C. Read
- D. Print

C. The ability to restrict who can read data or files does not require the use of an IRM solution and can be accomplished with traditional security controls or permissions settings. This can be done either through direct file permissions or the use of ACLs, or by preventing a user or process from getting to the file at all.

A is incorrect because a file that can be read can also be copied. If file permissions restrict the ability to insert files onto the file system, the contents of the file can be copied through a variety of methods.

B is incorrect because files can typically be renamed if they can be read on a system. Though some file systems can prevent files from being inserted, which will also prevent them from being renamed in most instances, it is not a universal capability and will typically require the use of an IRM solution.

D is incorrect because printing is possible if a file can be read. Once the data is accessible, even if printing is not possible directly from the host system, there are a variety of ways to copy or move data that could expose it to being printed. IRM technologies can be used in a variety of ways to prevent printing.

## 31. Which cloud service category is object storage associated with?

- A. Software
- B. Infrastructure
- C. Desktop
- D. Platform

- B. Infrastructure as a Service (IaaS) uses object and volume storage. Object storage is where data is stored on a system through the use of an opaque descriptor or handler and then accessed with it, rather than through a traditional file system with naming conventions, folders, and so on.

- A is incorrect because Software as a Service (SaaS) uses its storage mechanisms that are specific to its applications and not typically accessible by a cloud customer through any other means than the application interfaces. For instances where file objects are allowed to be stored, they are done through application interfaces and are only accessible through those means.

- C is incorrect because Desktop as a Service (DaaS) uses storage in a similar way as SaaS. Storage is done by the cloud provider and is specific to how its systems are implemented. DaaS typically functions as a SaaS implementation, where applications hosted on a cloud platform are accessed and used through a client.

- D is incorrect because Platform as a Service (PaaS) uses structured and unstructured storage types. Structured storage typically resembles a database-type system, where the organization and labels are well defined and used by the application, whereas unstructured storage serves to host support files such as images, web objects, configuration files, and so on.

## 32. Which of the following is NOT a common component of a DLP implementation process?

- A. Discovery
- B. Monitoring
- C. Revision
- D. Enforcement

- C. Revision is not a core component of a loss prevention (DLP) process, though it would likely be part of an organization's larger change management or technical advisory processes. For any DLP strategy to be successful, an organization must include other processes in the workflow for revision over time as systems change and data evolves, but revision is not a core component of the actual DLP processes.

- A is incorrect because data discovery is a key component of DLP implementation. DLP systems first need to discover the data they are intended to protect and monitor, either through specific configurations of data sources and storage systems or via predefined signatures or other discovery method to find new data as it comes into the system or is accessed.

- B is incorrect because monitoring is done constantly by DLP systems as access is or moved. DLP systems, before enforcing policies and controls, need to constantly monitor data and network operations to match rulesets or signatures.

- D is incorrect because enforcement is a core component of the DLP process.

## 33. Which of the following operations can be controlled and prevented with an IRM solution but would not be possible with authorization?

- A. Read
- B. Delete
- C. Modify
- D. Distribution

- D. An IRM solution can control what can be done with data. With traditional authorization there is little that can be prevented from copying, printing, sharing, or otherwise distributing it.

- A is incorrect because read operations can be controlled by traditional authorization and do not need an IRM solution. However, an IRM solution can give far greater and granular control over it.

- B is incorrect because delete can be prevented through specific authorization rights.

- C is incorrect because modify is a core capability of all file systems, and IRM is not needed to control it, though IRM can certainly give far greater control over it.

## 34. Which of the following concepts is NOT one of the key components of a data-archiving program?

- A. Format
- B. Size
- C. Regulations
- D. Testing

- B. Many considerations are needed to develop a data-archiving program and establish the policies that govern it, but the size of archives is a technical consideration, not one to drive policy. Regulations especially focus on what needs to be preserved and for how long, the size of the archives is never a consideration under regulatory frameworks.

- A is incorrect because the format of archives is a prime consideration. It directly ties to regulatory requirements for what must be preserved, as well as to considerations for ensuring it can be restored and accessed for the duration of the required retention period.

- C is incorrect because regulations are the most central and important component of a data-archiving program. They define what needs to be preserved and what the retention period is. Company policies or other considerations may expand on the regulatory requirements, but the regulatory requirements will always form the minimum basis for retention.

- D is incorrect because testing is vital to ensure the success and compliance of an archiving program. Although identifying data that must be preserved and establishing processes to do so are vital, the testing of the restoration capabilities is equally vital. Collecting data and archiving it will not fulfill regulatory requirements if the organization is later unable to restore or access it, should the need arise.

## 35. Which of the following activities is NOT something typically performed by an SIEM solution?

- A. Deletion
- B. Alerting
- C. Correlation
- D. Aggregation

A. A SIEM solution will aggregate event data and allow for analysis and reporting on it. However, it functions as a consumer of event data; it does not maintain the data from the source. Data is copied into an SIEM solution from agents.
