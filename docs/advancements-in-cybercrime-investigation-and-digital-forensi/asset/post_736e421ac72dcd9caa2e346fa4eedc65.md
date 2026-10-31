
When communicating, identity authentication via a network is difficult. An unethical individual could use this to intercept messages or impersonate another person or entity. To maintain the essential level of confidence in the communication process, a method must be developed.

A digital certificate is a standard credential that may be used to validate an individual’s identity. A certification authority (CA) is a trustworthy institution that issues certificates and is known as the certificate’s issuer. It provides server certificates and client authentication certificates to clients and servers who request them.

This signature certificate since it contains a public key for digital signatures. If the CA is a root authority, the CA certificate might be alluded to as a root certificate. A site certificate is another name for a digital certificate. A Certificate Server is a trusted application that is frequently used. The certificate server is managed by a CA running on a secure computer. This application has access to all of its clients’ public keys. Certificate servers send out communications called certificates that contain the public key of one of its clients. Each certificate is signed with the CA’s private key, and a reputable CA will only issue a certificate after validating the identity of the certificate’s subject to an individual or entity with whom the individual has a public key. The person or entity to whom a certificate is issued is referred to as the certificate’s subject (Kaur, Sahiwal, & Kaur, 2012).

## 16.5.6 THE PASSWORD ANTI-PATTERN

OAuth is an amazing and important authorization protocol. This makes OAuth an interesting solution as we use services and platforms on a daily basis. The usage of the internet is rapidly growing.

We also provide access to some of these services and platforms so that we can securely link and move data between them. With the introduction of APIs and SDKs, application development has expanded rapidly to include not only the web but also mobile and desktop platforms. While these APIs are really useful and convenient (at times, rarely), providing this interoperable service in a way that protects the user’s security becomes tricky. HTTP Basic Auth or other login-based session-related authorization routines are used by traditional HTTP services, although they normally require submitting your credentials through a third party rather than directly to the authentication/resource server. The confidential or user-specific features, services/APIs usually require authentication and authorization. While this simple login-based authentication method is simple, it poses major security risks.

One of the most major security issues with standard username/password authentication is that a user cannot easily remove access or permissions from a third-party application. In most cases, users are left with only one option: to reset their password.

Moreover, if a vulnerability or security bug is discovered in a third-party application and made public, the developers of a platform or service like Twitter can (temporarily) suspend/revoke/disable that third-party application (OAuth Client) to protect all of their users who may be using it until a security patch is released. Another security issue with simple authentication is the ability to limit resource and information access. There’s no way to limit how much data the third-party program has access to. It’s either everything or nothing.

Users want and deserve the option to grant selective access while also having the ability to revoke any unauthorized access at any time without having to enter their password. Developers want to give their users this functionality and give them access to and from a range of popular web services and platforms, but there are so many distinct authentication and authorization protocols that it’s difficult. OAuth provides a standards-based solution to the table, which all community developers can and have accepted. It’s the first step toward a unified, standardized specification for password-free authorization in web, desktop, and mobile apps (https://medium.com/security-operations/what-is-OAuth-and-why-should-i-use-it-5aa2f27ce387).

## 16.6 SYSTEM ARCHITECTURE AND DESIGN

The system’s architecture and design phase will convert system requirements into a format suitable for implementation. Understanding the system architecture leads to the project being divided into submodules. If the project is broken into modules, designing it gets easier, as does identifying and correcting errors. We can simply assess the control flow and data flow between multiple entities by separating the project into sub-divisions. We can utilize this information to examine the sort of data structure and algorithms that will be employed in the system.

### 16.6.1 SYSTEM ARCHITECTURE

The system architecture specifies the numerous internal pieces of the proposed system as well as how these internal parts will communicate with one another to accomplish various activities.

Considering the various communication methods available, the developer can study the flow of data between different entities and analyze any form of data conversions and other structural changes that may be required during implementation. The architecture also clearly indicates which components of the system are visible to the end-user and which are run in the system’s back end. The system’s information front end can be effectively designed by displaying only the user-required feature.

Figure 16.2 represents the design of the system, when a client wishes to read a secured piece of information about a user from a secured resource server, the client contacts the resource holder, and with the resource holder’s approval, the client examines the secured piece of information. The client contacts the authorization server after acquiring an authorization grant from the resource owner that includes the client’s identity, secret, and current time. If the authorization server detects that the client is already registered with it, this generates a token and uses the client’s identity and the secret to digitally sign it with the client’s id and key. The client receives the token when it has been signed. This token will be passed to the protected data server by the client. The token will be decrypted by a secure data server. If the token is authentic, the resource can be made available to the client. The token will be digitally signed here, and the token will be large (Wu & Lee, 2013).

![](img/46a7ed74d391bf69db3c36e9484e1be4_354_0.png)

FIGURE 16.2 Architectural design of system.

### 16.6.2 SIGNING YOUR OAUTH 2.0 REQUESTS

When the API provider accepts or requires signatures, the MAC authentication specification defines how OAuth requests are signed by the client.

- **1. Getting the Keys:** The client must first get a MAC key before using MAC authentication to sign requests. This may be accomplished through the OAuth authorization server. Each time the authorization server delivers an access token, the key is returned. This MAC key must be compatible with the HMAC-SHA-1 or HMAC-SHA-256 algorithms available. The MAC key might also be generated via an out-of-band operation, such as when a developer working on a project is testing a new feature. Their application is registered with an API provider. The keys must be distributed over a secure SSL/TLS connection and kept private.

- **2. Making the API Request:** When integrating with OAuth-enabled APIs that need signatures, each API request must include a MAC signature in the Authorization header. To generate this signature, create a normalized request string (nonce, HTTP method, request URI, host, port, optional body hash, etc.), and perform a cryptographic signature. If an OAuth MAC signature is required, developers should strongly consider using a prebuilt library (Boyd, 2012).

### 16.6.3 ACCESS TOKENS, CLIENT CREDENTIALS, CLIENT PROFILES, CLIENT AUTHENTICATION, AND AUTHORIZATION FLOWS

OAuth was designed to manage API permissions for typical client-server web applications. There was no direction in the benchmark on how to handle authorization in mobile apps, desktop apps, JavaScript apps, browser extensions, or other scenarios. Regardless of the fact that each of these apps uses OAuth 1.0, the implementation approach is inconsistent and usually inadequate because the protocol was not built for these circumstances. OAuth 2.0 has been developed keeping a range of circumstances in mind.

### 16.6.3.1 ACCESS TOKENS

Access tokens are a form of credential that may be used to get access to resources that are restricted. As an access token, a string is utilized. A visual representation of a customer’s permission. The client is usually unaware of the strings. Tokens are unique access scopes and durations that are issued and implemented by the proprietor of the resource. Resource servers and authorization servers are the two sorts of servers. The token
