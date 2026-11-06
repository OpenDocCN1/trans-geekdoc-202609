
# Authentication in Windows Server 2003

Any well-formed security model needs to address the following three topics: authentication, authorization, and accounting (or auditing). Authentication deals with who a person is, authorization centers around what an authenticated user is permitted to do, and accounting/auditing is concerned with tracking who did what to a file, service, or other resource. Windows Server 2003 addresses all three facets of this security model, beginning with the user authentication strategies that we discuss in this chapter.

Regardless of which protocol or technical mechanism is used, all authentication schemes need to meet the same basic requirement of verifying that a user or other network object is in fact who or what it claims to be. This can include verifying a digital signature on a file or hard drive, or verifying the identity of a user or computer that is attempting to access a resource. Windows Server 2003 offers several protocols and mechanisms to perform this verification, including (but not limited to) the following:

- `Kerberos`
- NT LAN Manager (`NTLM`)
- Secure Sockets Layer/Transport Security Layer (`SSL/TLS`)
- Digest authentication
- Smart cards

The following sections cover the details of each authentication mechanism available with Windows Server 2003, and the appropriate use for each. The most common authentication mechanism dates back to mainframe computing, password authentication. This occurs when the user supplies a password to a server or host computer and the server compares the supplied password with the information that it has stored in association with the user or resource in question. In the case of users, if the two passwords match, the system permits the user to log on. Concerns regarding password authentication have largely been connected with ensuring that user passwords are not transmitted in an easily intercepted and decipherable form over a network connection. In fact, many modern password authentication schemes, such as `NTLM` and `Kerberos`, never transmit the actual user password at all.

An issue that is more difficult to address is user education. Even after a great deal of effort has been put into teaching users the importance of strong passwords, many still use relatively weak passwords for convenience. In a world of increasingly connected computing systems, the importance of creating strong password policies as part of your network’s security plan cannot be overstated. To assist in this task, Windows Server 2003 allows you to establish password policies that mandate the use of strong, complex passwords, as discussed earlier in the chapter. You can also require that your users log on using smart cards, a topic that we cover in depth in a later section.

## Need for Authentication

User authentication is a necessary first step within any network security infrastructure because it establishes the identity of the user. Without this key piece of information, Windows Server 2003 access control and auditing capabilities would not be able to function. Once you understand how the various authentication systems operate, you’ll be able to use this information to create an effective user authentication strategy for your network. The location of your users, whether they are connected to the LAN via a high-speed network connection or a simple dial-up line, and the client and server operating systems in use throughout your organization will dictate the appropriate authentication strategy for your users.

Keep in mind as we go along that a fully functional authentication strategy will almost certainly involve a combination of the methods and protocols. A single solution will not meet the needs of an enterprise organization. Your goal as a network administrator is to create an authentication strategy that provides the optimum security for your users while allowing you to administer the network as efficiently as possible.

## Single Sign-On

A key feature of Windows Server 2003 is support for single sign-on, an authentication mechanism that allows your domain users to authenticate with any computer in the domain, while only providing their logon credentials one time. This system allows network administrators to manage a single account for each user, rather than dealing with the administrative overhead of maintaining multiple user accounts for each server. It also provides greatly enhanced convenience for network users, because needing to maintain only a single password or smart card makes the network logon process much simpler.

Whether your network authentication relies on single sign-on or not, any authentication scheme is a two-step process. At the very least, the user must perform an interactive logon in order to access the local computer. If network access is required, network authentication will allow the user to access needed network services and resources. In this section, we examine both of these processes in detail.

### Interactive Logon

A network user performs an interactive logon when presenting valid network credentials to the operating system of the physical computer the user is attempting to logon to—usually a desktop workstation. The logon name and password can either be a local user account or a domain account. When logging on using a local computer account, the user presents credentials that are stored in the `SAM` database on the local machine. Every Windows NT, 2000, and Server 2003 workstation, stand-alone server, or member server has a `SAM` database that is used for this purpose. Accounts stored in a `SAM` database can only be used for access to that specific computer.

When using a domain account, the user’s logon information is authenticated against the `Active Directory` database. This allows the user to gain access to not only the local workstation but also to all resources he or she has been granted permission to use in the domain and any trusting domains. In this case, the user’s domain account works in conjunction with the workstation’s `SAM` database. The user authenticates to the domain, but is allowed to access the local computer because his or her domain account has the appropriate permissions and rights locally. This is typically done when the workstation joins the domain, through group membership. For example, the `Domain Users` global group in `Active Directory` is added to the local `Users` group on the workstation. Because all domain user accounts are members of the `Domain Users` group by default, they also inherit access to the local computer through this group’s membership in the local `Users` group.

### Network Authentication

Once a user has gained access to a physical workstation, it’s almost inevitable that the user will require access to files, applications, or services hosted by other machines on the LAN or WAN. Network authentication is the mechanism that confirms the user’s identity to whatever network resource the user attempts to access. Windows Server 2003 provides several mechanisms to enable this type of authentication, including `Kerberos` and `NTLM`.

Using the previous description of interactive logons, users who log on using a local computer account must provide logon credentials each time they attempt to access a network resource. This occurs because the local computer account only exists within the individual computer’s `SAM` database rather than a centrally managed directory service like `Active Directory`.
