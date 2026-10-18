
# Identity and Access Management

Identity and Access Management is a framework for managing digital identities. IAM manages the user database, logs when users sign in and out, manages the creation of groups or roles, and allows for the assignment and removal of access privileges. Many different groups offer IAM frameworks, the most famous of which may be Amazon Web Systems (AWS) which use it for controlling access to the infrastructure as a service (IaaS) technologies they offer.

IAM often makes use of PIM and PAM to accomplish these goals. A well-implemented, thorough IAM framework can work across operating systems and handle many different types of resources.

## 7.3.5. Unix File Permissions

From its inception, Unix was designed to be a multi-user environment, and as such, a lot of attention was paid to file permissions. Every file in a Unix system has an owner and a group. Each file also has permissions for owner, group, and all users. Permissions are set using octal numbers where each bit represents read (bit 0: 1), write (bit 1: 2), or execute (bit 2: 4) permission.

![](images/permissions.svg)

For example, if you wanted a read and execute permission the number would be 5 (1 + 4). Read and write permission would be 3 (1 + 2).

Permissions are specified with the `chmod` command, the first octal number is the permissions for the owner, the second is for the group, and the third is for all user. So to change a file to have read, write, and execute permissions for the owner, read permissions for the group, and no permissions for everyone else, the command would be `chmod 710 <filename>` where `<filename>` is the name of your file.

The owner and group of a file can be set with the `chown` command: `chown <owner>.<group> <filename>`. If `<group>` is not specified only the owner is changed.

## 7.3.6. ACLs

Access Control Lists (ACL) are used to permit or deny access based on a characteristic. They tend to be based on a simple characteristic and either deny access to anyone not on the list, `allowlist`, or deny access to anyone who `is` on the list, `denylist`.

ACLs used in networking and typically filter based on IP address. You can find examples of ACLs in most firewall products as well as in Amazon Web Services (AWS) Virtual Private Cloud (VPC).

Filesystem ACLs apply the same concept to files. Linux uses fileystem ACLs to permit or deny access in a more nuanced way than possible with [Unix File Permissions](#index.xhtml#_unix_file_permissions).

## 7.3.7. SSH Keys

Secure Shell Server (SSH) supports the use of asymmetric encryption keys for authentication. Most severs support RSA, DSA, and ECDSA keys, with RSA being the most common. An SSH server maintains a list of authorized keys, typically in `~/.ssh/authorized_keys`, that can be used to connect to the server. When a client connects, the SSH server issues a challenge asking the client to sign a random piece of data using their private key. If the private key matches the public key stored in the `authorized_keys` file, the user is logged in.

SSH keys have the advantage of being easier to use as the user doesn’t need to remember and type in a password. For this reason, keys are often used for authentication when running protocols over SSH such a [git](https://git-scm.com/). Keys also have the advantage of possibly thwarting MitM attacks. While a password can be easily stolen by a malicious actor impersonating an SSH server, authentication via key will only transmit a signed bit of random data. This bit of data is useless to the MitM.

## 7.3.8. Sessions and Cookies

HTTP sessions can also be used to control access to a resource. This is often employed in web applications. Upon successful sign-in, a user is given a cookie with a cryptographically tamper-resistant session ID. Every request the user makes to that site will include that cookie. Eventually the session will time out and the user will make a request that is denied based on their session ID no longer being valid. Typically the website will redirect them from the protected resource to a login page where they can log in again.

Website cookies may also be used to store user preferences or the current state of the application. A cookie could list the items currently in a users shopping cart or specify whether or not the user prefers dark mode. Cookies have been a target of scrutiny as they can be used in attacks. If cookies can be accessed by an outside application or by a separate malicious tab in a web browser, then can be used to gain access to a users session.

## 7.3.9. Single Sign On (SSO)

Given the ubiquitous nature of web applications, maintaining separate usernames and passwords can be difficult for users. A recent trend has been to support Single Sign On, where one identity provider is used to confirm that users are who they claim to be. There are a few protocols that make this possible, including SAML and OAuth.

SAML stands for Security Assertion Markup Language and is an XML based Single Sign On solution. The SAML workflow centers around the SAML identity provider or IDP. The following steps take place to grant access to a resource via SAML:

1. User accesses a sevice

2. User is redirected to SAML IDP with SAML request

3. User logs in

4. Credentials are verified

5. SAML IDP sends credentials to the service

OpenID is another protocol that allows users to authenticated using a third-party identity provider in a similar fashion to SAML. One of the main differences is that OpenID was designed to be decentralized, allowing for multiple IDPs for users to choose from. In February 2014 OpenID introduced OpenID Connect (OIDC), a more modern system that allows IDPs to provide information about users via a REST API. This move was largely in response to the popularity of OAuth.

OAuth is a method for allowing websites to access parts of a user’s profile with the user’s permission. OAuth is not `technically` a full-fledged authentication protocol, but it is often used as part of one. The following diagram highlights the differences between OpenID authentication and an OAuth flow:

![OpenID vs. Pseudo-Authentication using OAuth by Perhelion used under CC0 1.0](images/oauth.svg)

[OpenID vs. Pseudo-Authentication using OAuth](https://commons.wikimedia.org/wiki/File:OpenIDvs.Pseudo-AuthenticationusingOAuth.svg) by [Perhelion](https://commons.wikimedia.org/wiki/File:OpenIDvs.Pseudo-AuthenticationusingOAuth.svg) used under [CC0 1.0](https://commons.wikimedia.org/wiki/File:OpenIDvs.Pseudo-AuthenticationusingOAuth.svg)

## 7.3.10. Kerberos

Kerberos is an authentication protocol for client server connections. It was developed by MIT in the 1980s and is most largely deployed on Windows networks, but many Linux distributions support using it for authentication as well. Kerberos makes extensive use of time-based tickets and as such all client participating must have their clocks in sync. When functioning correctly, Kerberos allows for full authentication on an untrusted network.

Kerberos makes use of many different services and concepts to perform its duties. Some of these services may run on the same machine and they are almost always abbreviated:

Authentication Server (AS) 

: performs the authentication step with clients 

Ticket-Granting Service (TGS) 

: service which creates and signs tickets 

Ticket-Granting Tickets (TGT) 

: time stamped and encrypted (with the TGS secret key) ticket that grants the ability to create tickets and sessions for services 

Key Distribution Center (KDC) 

: runs the TGS and grants TGTs 

Service Principle Name (SPN) 

: name of a service that uses Kerberos authentication 
