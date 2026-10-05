
# Chapter 2 Authentication Basics

## In-Band vs. Out-of-Band Authentication

Authentication factors can be considered in-band or out-of-band. In-band means the authentication factor method being used is conducted over the same communications channel as the primary login method. Out-of-band is when the authentication is sent over a channel different from the primary login channel.

For example, if you're trying to log in an Internet service application and you are required to type in a password and a password recovery within the same browser, this is considered two instances of the same type of factor, both in-band. If, however, you are required to type in a password on your computer and a second PIN code that was sent to your external cell phone, the factor is considered out-of-band.

Even better, if you are required to respond to separate authentication factors only in those channels and they aren't “cross-channel” (i.e., an authentication factor sent to out-of-band can be responded to in the same band as the other factor), then it provides more security assurance. Authentication factors on the same device, even in different channels, are not considered as authentication methods using different channels over different devices. Of course, this increases the complexity of the authentication process. In general, out-of-band authentication is usually considered more secure than in-band authentication.

As the number of separate authentication factors and communication bands increases, so does security assurance. In many scenarios, an MFA solution can only improve security, and MFA should be used where and when it makes sense to do. Unfortunately, not all authentication scenarios allow MFA, or not the same MFA solution. At least for (2020 and the next few years), users will still be required to use a single-factor authentication method in many scenarios.

No matter how it is done, successful authentication is the process of providing a valid identity label and one or more required authentication factor proofs. If done successfully, the subject and their identity is authenticated.

## Access Control Token

After a successful authentication, in most cases, the access control processes then associate an access control object (e.g., token, ticket) with the now verified, authenticated identity label. This access control token varies by system and protocol. In nearly all systems, it will contain an unique identifier, as a series of numbers or characters, specifically identifies the identity label, either permanently or for a particular session log. In other systems, such as Windows, it may also contain a list of group memberships, permissions, privileges, and other needed information. Figure 2.5 shows some of the information found in a Windows access control token.

The token may or not have a predetermined maximum lifetime, which upon expiration forces the subject to reauthenticate to remain in an “active” session. In Windows, an access control token may arrive in the form of a Kerberos ticket or an New Technology LAN Manager (NTLM) or LAN Manager (LM) token. On websites and services, most access control tokens are represented by an HTML code, which is a simple text file. Web cookies contain a unique identifier for the authenticated user and/or their session, followed by an expiration date (as shown in Figure 2.6).

![](img/c78b0f79db62998ee317a35df5629d85_79_0.png)

Figure 2.5: Example of the type of information found inside a Windows access control token

```
TOKEN CODE: document.cookie = 
"11_at=AQEDASYwnMSMEG70AAAABYB50K6AAAAXoE4agXGoHz4v6KVonJ5QHBkTy65SSI8ijjBPVgtk3Fu7680BatADYCAen5N94xxk1P864BUY17coGFYM66KM@KoTaGudaGYXIphdcxhhhM;expires=2020-05-04 03:18:11;"
```

Figure 2.6: Example HTML cookie access token

The expiration date indicates for how the cookie will be considered valid and that date may or not indicate how the user can reconnect to the website without needing to reauthenticate. Process of this token is often all that is needed to be successfully reauthenticated as a particular identity. In many cases, the token is seen as equivalent to the verified identity.

Get ready, important point ahead!

If you're reading along, blah, blah, blah, and not really comprehending, stop here to refocus your attention. I'm getting ready to say unknown to most people—even unknown to some security experts. Most computer security experts don't know this fact. And reading this one fact makes you a better computer security person. If you already know the fact in the next sentence, consider yourself one of the lucky ones.

Regardless of how you used to authenticate, the resulting access control token is usually the same. It formatted the same. It looks the same. It is treated the same. There are some edge cases where you authenticated could impact the token, and some of the contained claims are different because of how you authenticated, but most of the system there is little or no difference.

Let me explain by an example. Suppose you log on to your Windows laptop using a name and password. When you log in using a biometric fingerprint, you get an access control token. And both are identical or close to identical. In most systems, the process of authenticating and the process of getting the authentication token are essentially unrelated events. The system component giving you the access control token doesn't really care how you authenticated, only that you successfully authenticated. Regardless of how you did, here's your resulting access control token.

## Hacking Multifactor Authentication

### Least Privilege Principle

One of the bedrock security principles is that subjects should have the least amount of permissions and privileges necessary to delimit their task. You never want someone with the highest permissions and privileges all the time, especially if they are doing regular tasks (e.g., checking email, writing a document).

### On-Demand

Some authentication mechanisms allow a single person to use multiple logons, one privileged and nonprivileged, and the user picks which one they need at a single time. Other systems will allow you to perform step-up authentication, say, moving from a regular user to admin user (using sudo in Linux) when the higher or different account is needed. Other systems require specific credentials at the time of need. All highly privileged accounts may be stored in a centralized database, and any potential administrator has to successfully authenticate the privilege account and “check out”. The checkout is tracked in an event log. The highly privileged account may be further limited by duration, security domain, or allowed actions. These systems are generally known as privileged account managers (PAMs). Other types of access control systems act as SSO systems and will automatically regulate regular users to privilege status when needed.

### Authorization

You have successfully authenticated your identity and obtained an access control token. Now you want to use it as a license to access protected objects (i.e., file, folders, websites, services). The process of an access control manager submitting access control token and comparing it to a list of permissions associated with a protected resource is called authorization. Determining “can this person or device access that” is the key function of an access control manager. How well it enforces the comparison between the identity and its access control token and what is allowed the permissions and privileges attached to the protected object (often known as access control lists) tells us how the system is overall.

### Accounting/Auditing

All the critical steps of the three previous steps (IDM, authentication, and authorization) should be noted and saved to an event log. In general, accounting refers to tracking how of something (e.g., how many times they have logged on, in the system) and auditing refers to a detailed analysis of the involved action. However, in today’s world we usually lump them into auditing or event log management. Any good authentication system will log all critical steps from provisioning to deprovisioning and everything in between.
