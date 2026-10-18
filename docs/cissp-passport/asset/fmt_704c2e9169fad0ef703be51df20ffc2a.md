
Just-in-time access prevents users from carrying higher privileges or access than they normally need on a continual basis; they only get the access when they need it and only under specific circumstances. Such access can also be temporary and apply to only a specific action or resource. Just-in-time access is an effective way to adhere to the principle of least privilege while still allowing users to have the functionality they may need based upon their job duties. JIT access also helps to relieve the IT administrative burden by enabling users to perform necessary tasks without IT intervention.

### REVIEW

**Objective 5.2: Manage identification and authentication of people, devices, and services** In this objective we addressed identification and authentication of people, devices, and services. We discussed several key elements of identification and authentication, including identity management (`IdM`), authentication factors (knowledge, possession, and inherence), and the distinction between single-factor authentication and multifactor authentication.

We also discussed the accountability aspect, which means that details about the identification and authentication process must be recorded in order to hold individuals accountable for their actions. Session management is ensured through strong identification and authentication mechanisms, as well as strong encryption.

In order to initially prove an individual’s identity, they must go through a registration, proofing, and establishment process. Once this process is complete, the individual is able to obtain other identities, such as system credentials, that can be further trusted.

Federated identity management uses a single entity that is responsible for credentials that multiple organizations can trust and use to authenticate an individual for multiple resources. Credential management systems are used to create, update, and revoke credentials, as well as perform functions such as self-password reset, password synchronization, and password management. Single sign-on is an implementation of authentication technologies that allows the user to authenticate only once but subsequently be able to access many different resources.

Just-in-time access control refers to only allowing a user to have the access they need at the time they need it. Usually JIT access applies only to a specific set of actions and is temporary. The use of the `runas` command in Windows and `sudo` in Linux can facilitate JIT access control.

#### 5.2 QUESTIONS

**[1](#ch05.xhtml#ch5ques2-1).** You are tasked with implementing multifactor authentication for a sensitive system in your organization. Your supervisor would like you to explain which combination of factors would be considered multifactor. Which of the following would you tell your supervisor is a good example of multifactor authentication?

**A.** Smart card and PIN

**B.** PIN and password

**C.** Username and password combination

**D.** Smart card and token

**[2](#ch05.xhtml#ch5ques2-2).** In order to issue you credentials for a sensitive system, your organization must go through a formal process to verify your identity. Which of the following examples best describes registration, identity proofing, and establishment processes?

**A.** Providing your public key to your employer

**B.** Proving your identity using a driver’s license, passport, and birth certificate

**C.** Providing a letter of recommendation from a supervisor

**D.** Comparing the picture on your identification card to a picture in a company database

#### 5.2 ANSWERS

**[1](#ch05.xhtml#r_ch5ques2-1).** A Multifactor authentication consists of at least two separate types of factors. In this case, a smart card, which is something you possess, and a PIN, which is something you know, would be two factors. All other choices would be considered single-factor authentication, since each one of them only uses one of the authentication factors.

**[2](#ch05.xhtml#r_ch5ques2-2).** B Registration, identity proofing, and identity establishment processes require that you conclusively prove who you are, using trusted identification credentials. In this case, a driver’s license, passport, and birth certificate would conclusively prove your identity. Providing your public key to your employer would not prove anything, since anyone can have your public key. Providing a letter of recommendation from a supervisor would not prove who you are. Comparing the picture on your identification card to a picture in a company database would not conclusively prove who you are, since both the identification and the information in the database could be forged.

### ![Images](obj5-3.jpg)Federated identity with a third-party service

In this objective we will examine federated identity management (`FIM`) processes that use third-party services. Third-party services are most often used in online identification and authentication, and examples include Microsoft and Google authentication services and apps that people have on their smartphone or tablet. This objective explains third-party identity management services in on-premise, cloud, and hybrid implementations.

#### Third-Party Identity Services

Not every organization can afford the cost of the personnel, infrastructure, and policy involved with identifying and authenticating external individuals who access the organization’s web services and managing their credentials. Fortunately, such organizations can turn to a third-party identity service provider to meet their needs, which often is more affordable and more efficient and ensures that identification and authentication are securely handled.

Almost everyone has used third-party identity services, whether they actually realized it or not. If you’ve ever used Duo, Microsoft, or Google authentication services, for example, you have used third-party identity services. For this objective, we will discuss three approaches to providing third-party identify services: on the premises of the organization, through cloud-based services, or as a hybrid of both methods. In Objective 5.6 we will discuss additional components of identity and authentication services, including mechanisms and protocols associated with third-party services such as the Security Assertion Markup Language (`SAML`), Open Authentication (`OAuth`), and OpenID Connect (`OIDC`).

As briefly discussed in Objective 5.2, `FIM` expands beyond a single organization and is used when organizations join a group or a “federation” of other organizations who share identity and credentials for the purposes of single sign-on (`SSO`) into multiple resources across organizations. Examples of a federation might include a company with numerous geographically separated divisions or campuses, universities with multiple campuses, or government organizations across a country. Note that while the federation manages identities and credentials, each member of the federation controls its own access to resources.

##### On-Premise

Having an on-premise (aka on-premises) solution for identity management (`IdM`) typically means that the organization has implemented and retains both management control over the solution and the responsibility for its daily maintenance and security. However, some third-party solutions also can reside on-premise; these are solutions that require identity management servers or services to be installed within the organization’s internal infrastructure. The organization still has some level of control, as well as lower-level maintenance and security responsibilities with the solutions. These are typically integrated solutions that use standardized identification and authentication mechanisms and protocols, such as Kerberos authentication and Microsoft Active Directory.

##### Cloud
