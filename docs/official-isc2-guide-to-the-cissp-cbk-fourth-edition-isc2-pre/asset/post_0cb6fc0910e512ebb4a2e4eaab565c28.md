
Sessions and perhaps two desktop sessions if virtual desktops are used. However, organizations must be cautious with regards to how multiple sessions are implemented because each session can provide an additional point of attack for an adversary and many more sessions to monitor for the security operations team and the end-user. The security practitioner needs to keep in mind that by monitoring sessions for behavior such as logins during non-business hours, he or she will be able to spot potentially suspicious behavior across any of the systems being observed.

## Schedule Limitations

Some desktop sessions may be limited by time. For example, if a kiosk is available in the lobby of an organization for general use during normal hours, does it make sense to have it allow sessions during non-business hours? Or should cash registers allow the creation of sessions outside of normal operating hours? Typically, session management should follow the concept of "least privilege" and only allow the creation of sessions within the most restrictive schedule and resources required to meet the mission.

## Logical Sessions

As more information systems become service-based through Web browsers, understanding Web-based sessions, their weaknesses, and how to protect them is critical for information security professionals to understand. Basic sessions are created between authenticated users, services, applications, and devices on a routine and regular basis in almost all information systems. For example, a typical online banking scenario may follow this sequence:

- 1. A user starts a Web browser and navigates to his or her bank’s website.
- a. There is now a session created between the user’s browser and the bank’s Web server.
- 2. The user clicks on the "secure login" link to get to the bank login page.
- a. The user has now secured the session typically using Secure Sockets Layer (SSL).
- 3. The user enters a username and password and authenticates.
- a. This information is passed through the encrypted session where, if intercepted, it would be very difficult to decrypt.
- 4. The user conducts banking business and "logs off" of the banking website.
- a. This will close the encrypted connection and ensure no other activities could occur under the user’s credentials until another session is established.

An account is created and in most cases needs not be repeated in its entirety during subsequent access, depending on the details of the relying party policy and the sensitivity and criticality of actions performed using the account.

Electronic authentication (e-authentication) is the process of establishing confidence in user identities electronically presented to an information system. It is the process of establishing confidence that an individual/organization using a credential that is known to the system (e.g., login name, digital certificate) is indeed the person/organization to whom the credential was issued. There are three types of authentication factors: something you know (e.g., password, PIN), something you have (e.g., smartcard, hard token, mobile phone), and something you are (e.g., biometric characteristic such as a fingerprint or voice pattern).

Authentication is performed each time a user logs into an account (e.g., portal, email) or otherwise uses a credential. Multi-factor authentication, which requires more than one type of authentication to be used at the point of system login, is sometimes used to achieve a higher level of assurance.

In the United States, each federal agency is responsible for verifying or validating the identity of individuals to whom it issues credentials. FIPS 201-2 establishes a specific level of trust in an individual’s identity as part of a process that binds the ID card to an individual (e.g., employee or contractor).18 Once that level of trust is established, it is possible to establish a chain of trust among government agencies. Establishing and binding a validated identity to a Personal Identity Verification (PIV) credential at the time the credential is issued is the foundation for a trusted common identity credential accepted throughout the federal enterprise.

FIPS 201-2 is composed of two major sections, PIV I and II. Both of these sections define requirements for the identity-proofing and registration process. In order to be in compliance with PIV I, agencies should implement a certified and accredited identity-proofing, registration, and issuance process for PIV cards across their enterprise.

A secure and robust identity-proofing process is the foundation for FIPS 201-2 compliance. A successful implementation of FIPS 201-2 is not contingent on technologies and systems only. If a PIV credential is issued based on a faulty identity-proofing process, the credential is compromised, no matter what technology it implements. FIPS 201-2 specifies an identity verification chain of trust for federal agencies. An identity verification chain of trust comprises a common set of identity vetting rules that are used by multiple entities so that they can accept and trust one another’s credentials. The chain of trust assures all parties involved that each participating entity followed the vetting procedures to securely and accurately verify an individual’s identity. One of the goals is to permit agencies other than the issuing agency to accept a credential and avoid the requirement to issue a separate credential.

The requirements for PIV I Identity Proofing and Registration are as follows:

- 1. Agencies must use an approved identity proofing and registration process.
- 2. The process must begin with the initiation of a National Agency Check with Written Inquiries (NACI) or an equivalent Office of Personnel Management (OPM) or National Security investigation required for federal employment. For current employees, this requirement is satisfied if the employee has a completed and successfully adjudicated NACI on file.
- 3. Before PIV credential issuance occurs, the FBI National Criminal history fingerprint check portion of the National Agency Check with Written Inquiries (NACI) must be completed and properly adjudicated.
- 4. The applicant must appear at least once in person in front of a PIV official before credential issuance can take place.
- 5. During identity proofing, the applicant must provide two identity source documents in original form. The documents must be on the list of acceptable documents included in I-9, OMB No.1115-0136, Employment Eligibility. One of the documents must be a valid (not expired) picture ID issued by a state government or the federal government.
- 6. The PIV identity-proofing, registration, and issuance process must adhere to the principle of separation of roles. No single individual may have the power to request issuance of a PIV credential without the approval of a second authorized person.

The identity proofing and registration process must be officially certified and accredited in accordance with NIST Special Publication 800-79-1: Guidelines for the Certification and Accreditation of PIV Card Issuing Organizations.

The role-based model assigns PIV identity-proofing responsibilities to individuals, based on the roles and functions they perform. In this model, one person cannot perform multiple roles, with one exception: The PIV Issuer and PIV Digital Signatory functions may be performed by the same entity. This requirement safeguards against the possibility of collusion between an applicant and the issuing authority.

The PIV role-based identity proofing process defines the following roles:

A cornerstone of all security strategies is the organization’s ability to control access to business systems and networks. Virtually all access controls rely on the use of credentials to validate the identities of users, applications, and devices. Organizations employ a variety of systems and technologies to convey identity and to attest to the claims and trust models that are associated with those identities. Some credentials are used to access the most valuable data in the organization, whereas others are used for more mundane tasks. Some are used thousands of times a second and others once a year. But as the number of credentials within an organization increases and the diversity of the security models and policies that they represent expands, the issue of credential management has emerged as a serious business challenge that goes way beyond traditional password management.

In the current online environment, individuals are asked to maintain dozens of different usernames and passwords, one for each website with which they interact. The complexity of this approach is a burden to individuals, and it encourages behavior—like the reuse of passwords—that makes online fraud and identity theft easier. At the same time, online businesses are faced with ever-increasing costs for managing customer accounts, the consequences of online fraud, and the loss of business that results from individuals’ unwillingness to create yet another account. Moreover, both businesses and governments are unable to offer many services online because they cannot effectively identify the individuals with whom they interact. Spoofed websites, stolen passwords, and compromised accounts are all symptoms of inadequate authentication mechanisms.

Just as there is a need for methods to reliably authenticate individuals, there are many Internet transactions for which identification and authentication is not needed, or the information needed is limited. It is vital to maintain the capacity for anonymity in Internet transactions in order to enhance individuals’ privacy and otherwise support civil liberties. Nonetheless, individuals and businesses need to be able to check each other’s identity for certain types of sensitive transactions, such as online banking or accessing electronic health records.

As Information Technology (IT) continues to increase in complexity, many organizations struggle with the management headaches associated with an overabundance of application-specific user accounts and access controls. This problem is further complicated by today’s mobile workforce and the need to access critical information anywhere and anytime. External threats such as malware, phishing, and vishing create an environment where proper selection of Identity and Access Management solutions is critical. Organizations are now working to establish unified, robust, and enterprise-wide user authorization and authentication frameworks to enable
