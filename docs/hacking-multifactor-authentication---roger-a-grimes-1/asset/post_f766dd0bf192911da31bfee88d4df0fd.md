
[content]

## Chapter 3 Types of Authentication

faces. In extreme and less popular cases, I've seen, DNA, ears, and even smell used as bio-metric attributes. The user scans in or records the requested biometric attribute, and when they go to log in, resubmit the same biometric attribute for comparison. If the originally recorded attribute matches the newly submitted one, the user is authenticated. In theory, it works as long as the most popular attributes used is globally unique. And so far, there is no conclusive evidence that the most popular attributes used (fingers, hands, eyes, and even the face of twins) are not globally unique.

Biometrics are easy to use. We always have our fingers, face, eyes, and the rest of our body parts with us even more often than our cell phones. On the downside, biometric authentication is not nearly as accurate as the underlying body attribute. Biometric authentication is full of false negatives and positives. For every biometric measurement you make, there are people in our population whose metric varies by day and cannot be relied on. For example, if your organization uses fingerprints for biometric authentication, in any large group (several thousands of thousands), there would be at least one person, if not, for whatever reason, their biometric measurement does not match by.

I'm not a fan of biometrics—I'm the opposite of that. They are far too easy to hack. I only support biometrics with specific preconditions and reliable reliance. Biometric hacks will be covered in Chapter 16, "Attacks Against Biometrics."

## FIDO

The Fast Identity Online (FIDO) Alliance (fidoalliance.org) is a set of popular MFA standards that relies on public-private key cryptography. Formed in late 2012–2013 and supported by world's largest digital companies, the FIDO Alliance made it its mission to create "password-less" authentication standards that could be used by a wide range of websites, services, software, and devices. And they appear to be achieving that goal better than any previous attempts by other standards bodies. FIDO supports a wide range of 1FA and MFA devices (computers, USB tokens, mobile phones, wired and wireless, etc.).

Currently, FIDO (now named FIDO2) has two main authentication parts and four (version 1.2) specifications. Any FIDO2-compliant software (OS, browsers, services, etc.) use the World Wide Web Consortium's (W3C) Web Authentication standard (WebAuthn) and APIs. Most of the major browsers support WebAuthn, not all. The Client to Authenticator (CTAP) specification covers how wireless, including mobile devices, interact with FIDO2. The Universal Authentication Framework (UAF) specification is a password-less method, which can be 1FA or MFA, but does not necessarily have to involve a separate device. The Universal 2nd Factor (U2F) specification, as the name implies, covers MFA and requires a second factor and device of some type.

With U2F, the user registers their device with the participating site or service and chooses to implement an authentication factor, such as a PIN or biometric ID. When connecting to the site or service, conducting a transaction that requires strong authentication, the device performs local authentication (verifying the PIN or biometric identity) and passes the along success or failure to the remote site. With U2F, an additional security device (such as a cell phone or USB dongle) is used as the second factor after the password or PIN has been provided.

The public-private cryptography used behind the scenes is reminiscent of other of TLS negotiations. Both the server and the client have a private-public key pair, and they share the key with each other to facilitate authentication over a protected transmission method. The relying party's public key is used to send randomly created "challenge" information back and forth between the server and client. The client's private key never leaves the device and can be used only when the user physically interacts with the device.

Traditional TLS guarantees authentication only to the client. FIDO authentication goes much further by linking "registered" devices to their users and those of the eventual websites or services. One authentication device can be linked to many (or all) websites and services. The prereistration prevents many, not all, types of authentication attacks. For more information on the FIDO2 standard and specifications, look here: fidoalliance.org/specifications/download.

## Federated Identities and APIs

Many authentication open standards not only define the protocols for each participating subject, client, and server, but also allow a single authenticated login and the resulting access control token to be shared that additional logins are not needed for additional participating sites and services. It's SSO, instead of being focused on a single corporate environment, it is intended to connect completely different sites and services.

One popular federated option many people are familiar with is the Facebook logon. As you may know, if you log in to a new website or service, the site may let you create a brand-new login or use Facebook, Twitter, or some other account type you may already have. That website or service has been coded to participate in a federated identity service. There have been many federated identity services over the years, including Microsoft Passport, for corporate customers, Microsoft Active Directory Federated Services (ADFS).

## OAuth

In the consumer space, the most recent and most popular federated authentication service is Open Authorization (OAuth). I'm going to cover it here in more detail because OAuth is the most popular open standard of its type, and understanding how it works will explain how the others work and can be possibly hacked.

OAuth is an open standard authorization protocol or framework that describes how unrelated servers and services can safely allow authenticated access to their assets without sharing initial login credential. In official authentication parlance, this is known as secure third-party delegated authorization.

Created and strongly supported from the start by Twitter, Google, and other companies, OAuth was released as an open standard in 2010 and became widely adopted. Over the next two years, it underwent substantial revision, and version 2.0 was released in 2012. You can join Amazon, Facebook, Instagram, Netflix, PayPal, and a list of other providers.

An early opponent describes OAuth as similar to a car's valet key. Some luxury cars have special, limited keys, which can be used to allow a valet to drive but don't allow full access. Instead, the car can be driven for a few miles, the key can't access the trunk or locked box. OAuth essentially allows the user, via an authentication provider they have previously successfully authenticated, to give another website or service a limited-access authorization token for additional resources.

Additionally, OAuth 2.0 is a framework, not a protocol (like version 1.0). It would be like the car manufacturers agreeing how valets would automatically request, receive, and use the keys and how those keys would generally look like, more than anything else. The valet keys could do compared full care about how it works. Just as in real life, valets and car owners don't need to care about how it works. They just want it to work seamlessly as possible. Here is how OAuth works behind the scenes, step-by-step. Let's assume a user has signed into one website or service using HTTP/S. The then initiates a feature or transaction that has access to another unrelated site or service. The following happens (greatly simplified):

- The first website connects to the second site on behalf of the user, using OAuth, providing the user's verified identity.
- The second site generates a one-time token and a one-time secret to the transaction and parties involved.
- The first site gives this token and secret to the initiating's client software.
- The client's software presents the request token and secret to their authorization provider (which or may not be the second site).
- If not already authenticated to the authorization provider, the client may be authenticated. Once authenticated (or if already authenticated), the client is asked to approve the authorization transaction to the second website.
- The user approves (or their software silently approves) a particular transaction type at the first website.
