
*   [\[17\]](#Ch005_225-293_B9780443187346000039.xhtml#B-bb0090) Cisco Smart Net Total Care Service Data Sheet. [https://www.cisco.com/c/en/us/products/collateral/cloud-systems-management/smart-net-total-care/datasheet-c78-735459.xhtml](https://www.cisco.com/c/en/us/products/collateral/cloud-systems-management/smart-net-total-care/datasheet-c78-735459.xhtml).
*   [\[18\]](#Ch005_225-293_B9780443187346000039.xhtml#B-bb0095) DSL and Cable Modem Networks. [https://www.ciscopress.com/articles/article.asp?p=31289](https://www.ciscopress.com/articles/article.asp?p=31289).
*   [\[19\]](#Ch005_225-293_B9780443187346000039.xhtml#B-bb0100) I Already Use a CDN. Why Do I Need Front-End Performance Optimization? [https://blog.radware.com/applicationdelivery/applicationaccelerationoptimization/2013/08/cdn-front-end-performance-optimization/](https://blog.radware.com/applicationdelivery/applicationaccelerationoptimization/2013/08/cdn-front-end-performance-optimization/).

# Chapter 6: Domain 5: Identity and Access Management (IAM)

## Abstract

The Identity and Access Management domain focuses on appropriately controlling access to data and systems. Proper identification and authentication must precede granting any access. The domain explores various aspects of single and multifactor authentication (MFA), including deficiencies of password-only authentication, challenges with biometrics, and the use of tokens. The domain demonstrates the need for credential management and Single Sign-On (SSO) on-premises and recognizes organizations’ growing use of cloud identity providers and Federated Identity Management (FIM). The domain explores authentication and authorization protocols such as Kerberos, SAML, OAuth, and OpenID Connect (OIDC). After appropriate identification and authentication, attention turns to authorization and proper application of access control models such as Mandatory (MAC), Discretionary (DAC), Attribute-Based (ABAC), and Role-Based Access Control (RBAC). The domain concludes by exploring the entire identity and access provisioning lifecycle to ensure appropriate controls are applied, emphasizing the importance of privileged access monitoring.

### Keywords

Authentication; Multifactor authentication (MFA); Biometrics; Authorization; Access control; Single Sign-On (SSO); Federated Identity Management (FIM); Mandatory Access Control (MAC); Role-Based Access Control (RBAC); Attribute-Based Access Control (ABAC)

Exam objectives in this chapter:

*   Identity and Access Provisioning
*   Authentication Methods
*   Access Control Technologies
*   Access Control Models
*   Federated Identity Management (FIM)

## Unique Terms and Definitions

*   **Crossover Error Rate (CER)**—describes the point where the False Reject Rate (FRR) and False Accept Rate (FAR) are equal.
*   **Discretionary Access Control (DAC)**—gives subjects full control of objects they have created or been given access to, including sharing the objects with other subjects.
*   **False Accept Rate (FAR)**—occurs when an unauthorized subject is accepted by the biometric system as valid. Also called a Type II error.
*   **False Reject Rate (FRR)**—occurs when an authorized subject is rejected by the biometric system as unauthorized. Also called a Type I error.
*   **Mandatory Access Control (MAC)**—system-enforced access control based on subject’s clearances and object’s labels.
*   **Role-Based Access Control (RBAC)**—subjects are grouped into roles and each defined role has access permissions based upon the role, not the individual.
*   **Attribute-Based Access Control (ABAC)**—a newer approach to access control that can determine access permissions based upon considering various attributes of the subjects and objects at the time of the access request.

## Introduction

Identity and Access Management (also known as access control) is the basis for all security disciplines, not just IT security. The purpose of access management is to allow authorized users access to appropriate data and deny access to unauthorized users. Seems simple, right? It would be easy to completely lock a system down to allow just predefined actions with no room for leeway. In fact, many organizations, including the US military, are doing just that; restricting the access users have to systems to a very small functional capability.

However, with increasing dependence on the Internet to perform work, systems must be flexible enough to be able to run a wide variety of software that is not centrally controlled.

Another concern that impacts access control is the dependence on antiquated (also known as “legacy”) software applications. Large IT infrastructures (such as the US military) may run mission-dependent applications that are over 10 years old! The cost of replacing these legacy applications is often too high for the organization to complete in one funding cycle. IT professionals must often manage security while running insecure legacy applications that introduce access control risks.

One thing is certain: with the dependence on IT as a means of doing business, and Identity and Access Management as one of the first lines of defense, understanding how to properly implement access management has become vital in the quest for secure communications.

Access controls protect against threats such as unauthorized access, inappropriate modification of data, and loss of confidentiality. Access control is performed by implementing strong technical, physical, and administrative measures. This chapter focuses on the technical and administrative aspects of access control; we discussed physical security in [Chapter 4](#Ch004_107-223_B9780443187346000076_1.xhtml), Domain 3: Security Architecture and Engineering. Remember that physical security is implicit in most other security controls, including access control.

## Authentication Methods

A key concept for implementing any type of access control is controlling the proper authentication of subjects within the IT system. A subject first identifies himself or herself; this identification cannot be trusted by itself. The subject then authenticates by providing an assurance that the claimed identity is valid. A `credential set` is the term used for the combination of both the identification and authentication of a user.

There are three basic authentication methods: `Type 1` (something you know), `Type 2` (something you have), and `Type 3` (something you are). A fourth type of authentication is some place you are.

### Type 1 Authentication: Something You Know

Type 1 Authentication (something you know) requires testing the subject with some sort of challenge and response where the subject must respond with a knowledgeable answer. The subject is granted access on the basis of something they know, such as a password or `PIN (Personal Identification Number`—a number-based password). This is the easiest, and often weakest, form of authentication.

#### Passwords

Passwords have been the cornerstone for access control to IT systems. They are relatively easy and cheap to implement. Many online banking, stock portfolio services, private Web mail, and healthcare systems still use a user name and password as the access control method.

There are four types of passwords to consider when implementing access controls: static passwords, passphrases, one-time passwords, and dynamic passwords.

*Static passwords* are reusable passwords that may or may not expire. They are typically user-generated and work best when combined with another authentication type, such as a smart card or biometric control.

*Passphrases* are long static passwords, comprised of words in a phrase or sentence. An example of a passphrase is: “I will pass the CISSP® in 6 months!” Passphrases may be made stronger by using nonsense words (replacing CISSP® with “XYZZY” in the previous passphrase, for example), by mixing case, and by using additional numbers and symbols.
