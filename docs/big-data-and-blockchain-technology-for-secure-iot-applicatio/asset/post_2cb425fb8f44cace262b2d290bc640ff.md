
## Table 5.1 Previous studies

| Authors | Methods | Contribution | Limitation |
|---|---|---|---|
| Y. Dong et al. [6] | Decentralized consortium blockchain system | Prototype with redactability and access control using chameleon hash, digital signature, and multi-authority attribute-based encryption (MA-ABE). Enhances robustness and protects against central point attacks. Viability demonstrated in practical scenarios. | Limited assessment details on performance, efficiency, and real-world feasibility |
| A. Shafieinejad and Roop Ranjan et al. [7] | Blockchain and ABE for safe cloud file sharing | Innovative collaboration approach ensuring safe cloud file sharing. Uses access polynomial for quick access revocation. Incorporates smart contracts in blockchain for access control. High scalability. | Lack of detailed assessment on performance, efficiency, and real-world feasibility |
| L. Wu and J. Du [8] | Access control for implanted medical devices | Innovative access control strategy for implanted medical devices using proxy devices and ciphertext-policy attribute-based encryption (CP-ABE). Efficient execution on tangible emulator devices. Practical and efficient model demonstrated. | Limited information on scalability and real-world deployment |
| M. Mahdavi et al. [9] | Revised FIBE and KP-ABE techniques | Presents revised versions of fuzzy identity-based encryption (FIBE) and Key-Policy Attribute-Based Encryption (KP-ABE) schemes with reduced pairing processes. Lacks thorough assessment of performance in real-world IoT situations. | Lack of assessment details on performance, efficiency, and feasibility in real-world IoT situations |
| N. Arivazhagan et al. [10] | Cross-trust multiple authorization ABE | Introduces CT-MA-ABE for cross-border institutional authorization using MA-ABE and blockchain certification authority (BCA). Implements encryption-based authorization for privacy. Successful deployment in South China legal jurisdictions. | Successful deployment in specific regions, lack of broader assessment details |
| F. Meng [11] | Improved OOABKS with verifiable security | Thorough examination of current Object-Oriented Attribute-Based Key Sharing (OOABKS) systems. Presents an improved OOABKS technique with verifiable security and efficiency. Maintains flexibility and security. | Lack of information on specific constraints in current OOABKS schemes |

(Continued)

## Table 5.1 (Continued) Previous studies

| Authors | Methods | Contribution | Limitation |
|---|---|---|---|
| PR. Kumar et al. [12] | Revocable Attribute-Based Encryption (RABE) | Proposes an efficient RABE technique addressing data integrity and key escrow issues. Security demonstrated using decisional q-parallel bilinear Diffie-Hellman exponent (q-PBDHE) assumption and discrete logarithm (DL) premise. | Lacks specific information on performance and scalability |
| PR. Kumar et al. [13] | Adaptive Secure Encryption (ASE) | Introduces FEASE, an Adaptive Secure Encryption (ASE) algorithm, providing speed and expressiveness. Enhances security against keyword-guessing attacks. Superior performance compared to existing ASE constructs. | Lacks detailed information on specific limitations and potential vulnerabilities |
| J. Lee et al. [14] | Key Aggregate Searchable Encryption (KASE) | Introduces a system for Personal Health Records (PHRs) that uses key aggregate searchable encryption (KASE) for security, and blockchain with smart contracts for data integrity, audit records, and transparency. Ensures rights of individuals during delegation using attribute tokens. Formal and informal security evaluations conducted. | Lacks detailed information on specific security evaluations, and potential challenges in real-world implementation |
| PR. Kumar et al. [15] | Attribute-Based Threshold Proxy Re-Encryption (AB-TPRE) | Presents attribute-based threshold proxy re-encryption (AB-TPRE) as a solution to the single point of failure in conventional Attribute-Based Proxy Re-Encryption (AB-PRE). AB-TPRE employs multiple proxies with a threshold mechanism for secure transformations. Introduces a share updatable feature to mitigate security risks. | The effectiveness and practicality of the proposed share updatable feature need to be thoroughly tested. Additional assessment details, especially in real-world scenarios, are required. |

ciphertexts of a fixed size. Introduced a strategy for CP-ABE and KP-ABE that utilizes ciphertexts of constant size. We refer to these as schemes 1 and 2, respectively.

### 5.3.2 Security of BLS and Boneh-Gentry-Lynn-Shacham (BGLS) signature

An aggregate signature system is a cryptographic method that allows for the combination of several signatures on multiple messages from multiple users into a single concise signature.

Regrettably, there are currently no aggregate signature methods that are completely non-interactive, even when relying on the random oracle heuristic. This means that signers need to exchange messages with each other, either in a sequential or alternative manner, in order to create the signature. Interacting with some intriguing apps might be too expensive.

Aggregate signatures, as defined by S. Ilakiya et al. [17], are a kind of digital signature that allows any party to consolidate many signatures on multiple messages from multiple users into a single concise signature. This basic element is valuable in several scenarios when there is limited storage or bandwidth capacity, and thus, there is a need to minimize the overall cryptographic burden.

Basic BGLS aggregate signature scheme [17]:

|  |  |
|---|---|
| Set up | $G_1 = \langle g_1 \rangle, G_2 = \langle g_2 \rangle, G_T$, prime order $p$  
$\mathbf{H}: \{0,1\}^* \to G_1$, full domain  
$e : G_1 \times G_2 \to G_T$, bilinear |
| KeyGen | $x \leftarrow_s \mathbb{Z}_p$  
$sk = x \in \mathbb{Z}_p$  
$pk = (y_1, y_2) = (g_1^x, g_2^x) \in G_1 \times G_2$ |
| Sign $(sk, m)$ | $\sigma = \mathbf{H}(m)^{sk} \in G_1$ |
| Agg $(\sigma_1, ..., \sigma_k)$ | $\sigma_A = \prod_{i=1}^k \sigma_i \in G_1$ |
| AggVer $(\sigma_A, (pk_1, m_1), ..., (pk_k, m_k))$ | $\prod_{i=1}^k e(\mathbf{H}(m_i), y_{2,i}) = e(\sigma_A, g_2)$ |

## 5.4 ENCRYPTION AND HEALTHCARE

The first factor that guarantees the unity and strength of a healthcare system is the protection of personal health information (PHI). The introduction of digital technology in healthcare allows for convenient access to this data, which facilitates the provision of more efficient and impactful health services and therapy. Presently, healthcare professionals widely use EHR technology. Most medical offices have shifted their EHR systems [18] to use outsourcing options, wherein EHR data is kept in centralized data warehouses on a third-party cloud that may lack total reliability and security.

Healthcare organizations must possess the capability to monitor and record user entry into their network. In order to do this, it is important to provide each user a distinct user ID for the purpose of accessing your organization's network. Ensuring the security of healthcare networks is a very successful strategy for preventing breaches. Malicious actors that successfully breach an organization's internal network have the capability to disseminate malware over the whole of the organization's system, therefore infecting every device that establishes a connection to the network. Failure to adopt efficient network management may have a negative impact on a firm.

Data backup and disaster recovery refer to the systematic practice of creating duplicate copies of crucial information and establishing a well-defined strategy for retrieving and restoring these files in the event of a catastrophe. HIPAA mandates the replication and storage of ePHI at an external facility. Healthcare organizations must also establish a disaster recovery strategy and provide a means of accessing data during emergency scenarios. In order to adhere to HIPAA regulations, it is essential to regularly create backups of data to mitigate the risk of patient data loss.

## 5.5 RESULTS AND DISCUSSION

The CP-ABE encryption technique, which is seen in Figure 5.4, is required to choose one random element from Z_p (during the building of polynomial p) and run two exponentiations in G (an elliptic curve group) for each attribute in order to encrypt the data. The KP-ABE encryption technique [19], however, only has to do two exponentiations in G (an elliptic curve group) for each attribute, and it only needs to choose one random element from Z_p across all of the attributes. Consequently, the time required for encryption by KP-ABE [20] is about three times quicker than the time required by CP-ABE [21].

In terms of decryption, the costliest calculation is the bilinear mapping, which is performed twice in CP-ABE and just once in KP-ABE for each leaf node. Consequently, the decryption time of KP-ABE is about two times quicker than the decryption time of CP-ABE [22]. However, while being more computationally efficient than CP-ABE in all three dimensions, KP-ABE has two notable drawbacks. Initially, it is important to note that the dimensions of the public key and master key increase proportionally with the quantity of characteristics in the overall set. This might result in an increase in communication overhead for the system, particularly when the system often necessitates users to update their public key. The relationship
