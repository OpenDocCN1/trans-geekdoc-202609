# Introducing DirectAccess

DirectAccess is a relatively new remote access functionality that was first introduced in Windows Server 2008 R2. Adoption of it was low, however, mainly because of the difficulty in getting it to work in the first place—you needed to be a wizard with IPv6 and a net genius to fight it! The fact that a DirectAccess experience could only be achieved when you ran it with Microsoft's Unified Access Gateway (UAG) product mean that it definitely wasn't a cheap solution and was typically going to be available to the larger enterprise customer.

With Windows Server 2012 R2 DirectAccess, though, all changes. Microsoft has redesigned it to be deployed and managed, and by doing so, it means that this fantastic remote connectivity is now available to a much wider audience.

"Fantastic remote connectivity?” you hear say. In this section we'll explain why we think so, and we'll walk you through deploying and managing it. Once you understand what it can do and you've tried it in your own environment, it' be hard to go back to the old VPN client of connectivity.

DirectAccess enables users to securely connect back into the corporate environment without the need to use a traditional VPN client. Sometimes it refer to this as a “hands-free VPN” solution because it has all the benefits of VPNs that without the administrative overhead for ends and the requirement on IT administrators to configure and manage multiple authentication methods that come with third-party VPN clients. When a customer has been configured to connect with DirectAccess has an Internet connection and manages the policies by the DirectAccess administrator, it will always get automatically connected to the internal network—even before the user logs in. Users don't even have to think about connecting, and from the IT administrator's perspective, they will have remote computers under control and management.

# How DirectAccess Works

When you deploy DirectAccess, you get an always-on, IPSec-based connection to your office that's easy to manage and driven through Group Policy. The person responsible for managing the remote-access solution for your company network, with employees constantly logging support calls related to not being able to log remotely, forgetting their usernames and passwords, and so.

All issues go away when you give those employees DirectAccess connectivity. The fact that all data encryption, packet encapsulation, and authentication happens as soon as the TCP/IP protocol stack initializes on the client before they even log in, meaning that you will still have the capacity to push out your updates and group policies, is a win-win situation.

# FEATURES

Here's a list of some DirectAccess features that you can take advantage of with Windows Server 2012 R2:

**No PKI Prerequisite** In the earlier version of DirectAccess, it was a prerequisite to have public-key infrastructure (PKI) deployed so you could make use of certificates for authentication. In smaller environments, configuring and managing a dedicated PKI was an administrative headache. With this, reality you still use certificates for authentication in certain scenarios, but there's an option now to use a self-signed certificate as part of the configuration wizard.