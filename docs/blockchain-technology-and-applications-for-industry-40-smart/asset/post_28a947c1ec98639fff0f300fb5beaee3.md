
## 3.3 Authentication and authorization

### 3.3.2 Authentication

When a unique blockchain address has been assigned and used to identify devices, the authenticity can be verified for every transaction created by a particular device. If a device has access to the blockchain account associated with the given blockchain-address, it can create valid transactions. A verifiable transaction origin is the basic trust feature of a blockchain system. So, if a transaction originates from a correct device address and the transaction is valid (not rejected during block creation), we can assume that it was created by the authentic device and not by some other device claiming the same identity.

If authentication is needed to access some on-chain smart contract capabilities, the authorization devices for access control. In Ethereum smart contracts, for example, there is a tx.origin variable in Solidity that returns the account's address that sent the transaction. However, the authentication based on tx origin can be exposed to a transaction origin attack, a form of phishing attack. Here, tx.origin authentication in smart contracts is usually created with the msg.sender variable. For details, see Section 2.4.4.2.

A blockchain system can also be used only as an underlying technology to authenticate and authorize devices for access control in off-chain service. In this case, the purpose of the decentralized application is to securely grant a device, a user, or a backend system, the appropriate identification and authentication information, such as a token, one-time password, IP address, or a certificate. This information is then used to authenticate a given entity and manage the service access. Apart from identification and authentication information, in this way, we can issue the entities initial authorization data or credentials too. Here, blockchain-based identification and authentication of devices are primarily not about the smart contract method, but about access to other services in the IoT architecture.

Strict access control requires the authentic identity of the communicating devices. In IoT, a dedicated gateway frequently manages the identities, which are then used when authenticating with others [51]. The forms of these identities are very diverse, for example, unique IPv6 addresses, one-time passwords, unforgeable tokens, or other credentials.

### 3.3.3 Authorization and access control

Traditional access control technologies govern the ability of users and devices to access capabilities and services made available by entities of the same kind. The OMAM reference model can help us define the organizational security and access control policy in a heterogeneous environment. This is a four-layer model, where each layer is designed separately. Horizontally, within each layer, we can compare the alternative access control aspects. Vertically, we compare and combine different access control policies. The reference model is depicted in Fig. 3.3. OM-AM stands for Objective, Model, Architecture, and Mechanism. The objective and model (OM) layers articulate what the security objectives are and what should be achieved, while the architecture and mechanism (AM) layers address how to meet those requirements [52].

| Mechanisms | Architecture |
| :--- | :--- |
| Objectives | |

Fig. 3.3: Authorization reference model for IoT.

#### 3.3.3.1 Authorization models

The possible access control models differ in many aspects, including granularity, flexibility, centralization, and interoperability. They are, therefore, not equally appropriate for implementation in IoT systems. In Sections 3.3.1 and 3.2.2, we highlight some possible approaches for identifying and authenticating IoT devices with DLT. Nevertheless, the decentralized approach is nearly one option and device identification can be managed in the traditional (centralized) way. Similarly, access control can utilize centralized or decentralized approaches.

Identity-based access control (IBAC) is a type of security that focuses on access to digital information or services based on the authenticated identity of an entity. Discretionary access control (DAC) considers the authenticated identity and the groups to which they belong. In DAC, subjects can transfer access controls among each other. Therefore, the name is discretionary. IBAC and DAC become unsuitable for IoT because it is almost impossible to manage the access control lists for every entity in the system.

On the other hand, in mandatory access control (MAC), the security policy is centrally controlled by a security policy administrator. Users cannot override or modify this policy – mandatory. A risk with MAC is high centralization and a single-point failure in the controller. IoT devices at diverse locations or with different functions may belong to various management organizations. This imposes another relevant problem for the centralized access control model, which does not fit IoT systems.

We can simultaneously implement MAC and DAC, where DAC refers to one category of access controls that can transfer among each other. MAC refers to the second category of access controls that imposes constraints upon the first.

Role-based access control (RBAC) employs pre-defined rules that carry a specific set of privileges. It can enforce MAC and DAC access control models too. Despite being used to manage access control in large organizations with hundreds of users and thousands of permissions, RBAC might not be flexible and scalable enough for IoT.

Attribute-based access control (ABAC), also known as policy-based access control, is more flexible and scalable, and can provide a more fine-grained access control that is needed in IoT. There are no access lists or roles in the system. Instead, attributes are assigned to every device, and only those with enough attributes that match the access policy are allowed. The policies can express a complex Boolean rule set and evaluate many different attributes. In several examples, DLT was applied to control the distribution of attributes in ABAC. In [51], a simplified DLT-based access control protocol was proposed for IoT.

Most traditional access control models face a common problem – credible center is needed to ensure trust. In [52], they presented an extensive review of various access control mechanisms for IoT. The conclusion is that traditional access control may not be completely appropriate for resource-constrained environments.

### 3.3.2 OAuth authorization architecture

The OAuth 2.0 [53] is a commonly applied authorization framework, which introduces an authorization layer and separates the role of the client from the resource owner. This standardized protocol provide specific authorization flows (Fig.3.4) for web or desktop applications, mobile devices, applications, or IoT, and simplifies the overall authorization architecture and client development. In OAuth, the client requests access to resources controlled by the resource owner and hosted by the resource server, and is issued a set of credentials different from those of the resource owner.

Instead of using the resource owner's credentials to access protected resources, the client obtains an access token – a string denoting a specific scope, lifetime, and other attributes. Access tokens are issued to third-party clients by an authorization server with the approval of the resource owner. OAuth does not pass authentication data between clients and resource providers, but instead acts as an authorization token. The client uses the access token to access the protected resources hosted by the resource server. However, [54] showed to run all OAuth logic in a resource-constrained device might be impossible because of its high communication and computation overheads.

### 3.3.3 Decentralized authorization examples

FairAccess [55] was the early attempt at a decentralized authorization management framework for IoT using blockchain. As one of the first, it pointed out the need for granularity, privacy, transparency, and sovereignty in identification and authentication. The implementation reflects the infant times of blockchain technologies. In FairAccess, they use the UTXO model of blockchain and BTC-like addresses to identify all interacting entities. The underlying blockchain network supported no smart
