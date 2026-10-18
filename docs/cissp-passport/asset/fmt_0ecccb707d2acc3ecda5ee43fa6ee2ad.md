
# Authentication

Authentication means that an individual’s system credentials are validated as being tied to that individual, so the system can verify that they are who they say they are. However, an individual cannot be authenticated by a system unless that system already has the individual’s verified credentials. But how is the individual validated before they even get an account? It requires a process whereby the individual establishes their identity with another entity and validates that identity. Registration and identity proofing are interrelated processes organizations use to prove the identity of an individual, as well as to register that identity for future validation. Once that identity is validated, a chain of trust between it and other identities, such as system credentials, can be established.

Take, for instance, the process of getting a U.S. passport. A passport itself is a valid proof of identity, but how do you establish your identity in order to get a passport? You have to provide other trusted forms of identification, such as a driver’s license and birth certificate. You also have to appear in person before a passport agent and provide an approved picture and likely have your fingerprints made. This establishes a chain of trust so that the passport can be issued, which itself is trusted afterwards. This process is called establishment of identity.

For new employees in a company, establishment of identity involves providing physical documentation, such as a driver’s license, birth certificate, passport, and so on, to the employer. Employers require this information for various reasons, including to initiate security clearances, withhold taxes, and perform background checks. This process must be trustworthy; if an organization mistakenly accepts proof of identity that is not actually valid (such as a library card or an expired driver’s license) or identification that could be easily forged, that sets up a chain of weak trust and proofing throughout the onboarding process as well as other processes.

This proofing and establishment of identity process is used not only by employers, but also by any organization that owns a resource a user might wish to access online. Think of online banking, for example, or access to another financial website. The individual must prove their identity, often by completing online forms that verify who they are through a series of questions with answers that only they would know, or by providing, again, written documentation in person before being allowed access to the site. In any event, the registration, identity proofing, and establishment of identity process is used to validate the individual so that the organization can subsequently issue the individual a trusted set of credentials.

## Federated Identity Management

Federated identity management (FIM) means that multiple organizations may use a single IdM provider. The IdM provider stores individual identities and credentials belonging to an entity which are validated upon request to any other entity wishing to authenticate an individual, across multiple organizations participating and systems. For example, Facebook performs FIM services when users wish to use their Facebook credentials to authenticate to a third-party application or website. More often than not, a third party is responsible for federated identity management, but the key here is that the same identity, once established, can be used for various resources, regardless of the organization, as long as the organization trusts the federated identity provider’s credentials.

### Cross-Reference

Objective 5.3 continues the discussion of federated identity management with third-party services.

## Credential Management Systems

A credential management system is one that securely stores credentials and can be used to issue, update, suspend, and revoke credentials. Consider an Active Directory account that can be created, added to groups, granted permissions, locked, and deleted. The Active Directory database, along with the utilities used to manage the user accounts in the database, is a form of a credential management system. However, credential management systems are much more comprehensive, as they can also include the administrative policies used to manage credentials, the physical systems that control and use smart cards, and other technical controls.

In addition to creating, updating, and deleting accounts, credential management systems facilitate the management processes used in long-term account management. Some of these management processes are embedded in enterprise credential management systems, but others may be add-ons or even standalone applications. Other activities performed by credential management systems include

- Password management Credential management systems assist in the creation and secure storage of user passwords
- Password synchronization Credential management systems assist in synchronizing passwords across multiple systems, applications, and identities.
- Self-service password reset Credential management systems assist users in resetting their own passwords by allowing them to use cognitive passwords (e.g., a series of predetermined questions and answers that only the user would know), or other secure methods.
- Assisted password reset Credential management utilities can be used by helpdesk personnel to assist in resetting user passwords securely, allowing the user to validate their identity and create a password that only they know.

## Single Sign-On

Single sign-on (SSO) is a method of authentication that requires a user to only authenticate once and still have access to multiple resources within an organization and possibly even within other organizations. Before single sign-on, users had to authenticate several times if each resource had its own security policies and credential requirements. Single sign-on is implemented by various technologies, including Kerberos and Windows Active Directory. Other technologies can assist in integrating single sign-on with federated identity management so that third-party identity providers can be used to authenticate a user to resources spanning multiple organizations, websites, and so on.

### Cross-Reference

Objective 5.6 discusses technologies that can assist with single sign-on authentication across multiple organizations, including OpenID Connect (OIDC) and Open Authorization (OAuth), as well as provides an in-depth discussion on Kerberos.

## Just-in-Time

Just-in-time access control refers to only allowing a user to have the access they need at the time they need it. Usually JIT access applies only to a specific set of actions and is temporary. For example, running a privileged command as a nonprivileged user may require an employee to escalate their privilege level by authenticating as a different account with higher privileges. In Windows this is often accomplished by using the runas command, and in Linux by using the sudo command. Just-in-time access is usually provisioned ahead of time but does not become effective until the user actually needs it. Access may also be contingent on circumstances; a user may not have access to a particular resource or a specific privilege level unless they need it based upon circumstances, such as time of day, login host, and so on.

### Cross-Reference

Objective 5.5 provides details about the runas and sudo commands.
