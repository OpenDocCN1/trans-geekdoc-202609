
as a central naming repository, which generates universally unique identifiers (UUIDs). When a user requests a resource, a search is done within a potentially large network to find a particular resource, thus requiring a precise specification of the resource.

However, authorization may be the biggest challenge, as there is no central authority to trust. It is also significantly more difficult to control security vulnerabilities in a distributed environment, although such vulnerabilities may be less pervasive. Each system has some responsibility for enforcing security and protecting themselves from compromise.

## Grid Computing

Grid computing is the sharing of CPU and other resources across a network in such a manner that all machines function as one large computer. Grid computers are often used for processor intensive tasks, which are suitable to be processed by parallel tasks. Grid computing is often confused with "cluster computing." Both involve using two or more computers to solve problems, but grid computing is heterogeneous while cluster computing is homogeneous. Grid computers can have different operating systems, hardware, and software. Grid systems are also associated with multi-tasking (a desktop computer may be part of a grid with spare CPU resources and also serve normal desktop functions), whereas a cluster is devoted to a single task. Finally, clusters are most often physically close together with a fast bus or network connecting the nodes, while a grid is geographically dispersed.

Given the dispersed and shared nature of grid computing, the security architect involved in the design of a grid system should keep in mind some of the vulnerabilities this leads to:

- Unless dedicated private communication lines are funded between nodes, much of the traffic for the grid will flow over public Internet conduits. Encryption of information between nodes or the use of VPN technology may provide mitigation for this vulnerability.
- Given the geographic distance a grid has between nodes, user authentication may be completely logical. Therefore, strong logical authentication controls must be implemented to ensure only authorized users access the grid. Consider specifying Kerberos, PKI, or multifactor authentication methods as part of the grid’s security architecture.
- Grid node software must be examined if joining a grid and security designed if hosting a grid. Special attention should be directed towards how the grid application isolates grid computing activity from other system activities.

## Cloud Computing

Cloud computing is a vague and ambiguous term. Many vendors market their product as cloud although it may not match what another vendor considers cloud. For the sake of discussion, cloud computing has been formally defined by U.S. NIST as:

> “... a model for enabling ubiquitous, convenient, on-demand network access to a shared pool of configurable computing resources (e.g., networks, servers, storage, applications, and services) that can be rapidly provisioned and released with minimal management effort or service provider interaction. This cloud model is composed of five essential characteristics, three service models, and four deployment models.” [70](70)

NIST defines the five essential characteristics of cloud computing as:

- **On-Demand Self-Service** – A consumer can unilaterally provision computing capabilities, such as server time and network storage, as needed automatically without requiring human interaction with each service provider.
- **Broad Network Access** – Capabilities are available over the network and accessed through standard mechanisms that promote use by heterogeneous thin or thick client platforms (e.g., mobile phones, tablets, laptops, and workstations).
- **Resource Pooling** – The provider’s computing resources are pooled to serve multiple consumers using a multi-tenant model, with different physical and virtual resources dynamically assigned and reassigned according to consumer demand. There is a sense of location independence in that the customer generally has no control or knowledge over the exact location of the provided resources but may be able to specify location at a higher level of abstraction (e.g., country, state, or datacenter). Examples of resources include storage, processing, memory, and network bandwidth.
- **Rapid Elasticity** – Capabilities can be elastically provisioned and released, in some cases automatically, to scale rapidly outward and inward commensurate with demand. To the consumer, the capabilities available for provisioning often appear to be unlimited and can be appropriated in any quantity at any time.
- **Measured Service** – Cloud systems automatically control and optimize resource use by leveraging a metering capability at some level of abstraction appropriate to the type of service (e.g., storage, processing, bandwidth, and active user accounts). Resource usage can be monitored, controlled, and

## Key Concepts and Definitions

- **Key Clustering** – When different encryption keys generate the same ciphertext from the same plaintext message.
- **Synchronous** – Each encryption or decryption request is performed immediately.
- **Asynchronous** – Encrypt/Decrypt requests are processed in queues. A key benefit of asynchronous cryptography is utilization of hardware devices and multiprocessor systems for cryptographic acceleration.
- **Hash Function** – A hash function is a one-way mathematical operation that reduces a message or data file into a smaller fixed length output, or hash value. If one compares the hash value computed by the sender with the hash value computed by the receiver over the original file, unauthorized changes to the file can be detected, assuming they both used the same hash function. Ideally there should never be more than one unique hash for a given input and one hash exclusively for a given input.
- **Digital Signatures** – Provide authentication of a sender and integrity of a sender’s message. A message is input into a hash function. Then the hash value is encrypted using the private key of the sender. The result of these two steps yields a digital signature. The receiver can verify the digital signature by decrypting the hash value using the signer’s public key, then perform the same hash computation over the message, and then compare the hash values for an exact match. If the hash values are the same, then the signature is valid.
- **Asymmetric** is a term used in cryptography in which two different but mathematically related keys are used, where one key is used to encrypt and another is used to decrypt. This term is most commonly used in reference to Public Key Infrastructure (PKI).
- A **Digital Certificate** is an electronic document that contains the name of an organization or individual, the business address, the digital signature of the certificate authority issuing the certificate, the certificate holder’s public key, a serial number, and the expiration date. The certificate is used to identify the certificate holder when conducting electronic transactions.
- **Certificate Authority (CA)** is an entity trusted by one or more users as an authority in a network that issues, revokes, and manages digital certificates.
- **Registration Authority (RA)** performs certificate registration services on behalf of a CA. The RA, a single purpose server, is responsible for the accuracy of the information contained in a certificate request. The RA is also expected to perform user validation before issuing a certificate request.
- **Plaintext** or **Cleartext** is the message in its natural format. Plaintext is human readable and is extremely vulnerable from a confidentiality perspective.
- **Ciphertext** or **Cryptogram** is the altered form of a plaintext message, so as to be unreadable for anyone except the intended recipients. An attacker seeing ciphertext would be unable to easily read the message or to determine its content.
- The **Cryptosystem** represents the entire cryptographic operation. This includes the algorithm, the key, and key management functions.
- **Encryption** is the process of converting the message from its plaintext to ciphertext. It is also referred to as enciphering. The two terms are used interchangeably in the literature and have similar meanings.
- **Decryption** is the reverse process from encryption. It is the process of converting a ciphertext message into plaintext through the use of the cryptographic algorithm and key that was used to do the original encryption. This term is also used interchangeably with the term decipher.
- The **Key** or **Cryptovariable** is the input that controls the operation of the cryptographic algorithm. It determines the behavior of the algorithm and permits the reliable encryption and decryption of the message. There are both secret and public keys used in cryptographic algorithms.
- **Nonrepudiation** is a security service by which evidence is maintained so that the sender and the recipient of data cannot deny having participated in the communication. Individually, it is referred to as the "nonrepudiation of origin" and "nonrepudiation of receipt."
- An **Algorithm** is a mathematical function that is used in the encryption and decryption processes. It may be quite simple or extremely complex.
- **Cryptanalysis** is the study of techniques for attempting to defeat cryptographic techniques and, more generally, information security services.
- **Cryptology** is the science that deals with hidden, disguised, or encrypted communications. It embraces communications security and communications intelligence.
- **Collision** occurs when a hash function generates the same output for different inputs.
- **Key Space** represents the total number of possible values of keys in a cryptographic algorithm or other security measure, such as a password. For example, a 20-bit key would have a key space of 1,048,576.
