# HANDLING PERMISSIONS WITH THE NEW DOMAIN

Suppose you decide to go the C&P route. Since there will be an intermediate phase, you can expect that the users of the organization will be members of old domains or the new one. This will require users in the new domain to be able to access files and other resources in an old one. Straddling the two domains, the organization will be heavily dependent on the trusts between the domain controllers until all servers that hold the resources are on the same side as the others.

How will the users maintain access to resources in the new domain as they did in the old domain? Business continuity is a big-ticket item for management; they need to ensure their people will be able to get to data. A seamless migration will minimize any access outages.

There are two approaches to maintain access: re-ACL and SID histories. ACL stands for access control list, a techie for the security tab of a shared folder. The SID is the security identifier, which is the unique number assigned to accounts to identify it within the permission structure. If you don't blink after opening the security tab of a file, you may see the SID listed on the ACL before the computer resolves the SID to a friendly name.

![](bbox=[0.181, 0.417, 0.218, 0.443])

# Real World Scenario

# THE RANDOM HORDE AND THEIR JUNK

A group of venture capitalists acquired two IT firms. The management of the newly formed corporation wanted to merge the two firms' Active Directory forests into one to provide a unified message system from Exchange and reduce the administrative overhead.

The network environment of one firm seemed to be held together with duct tape and Super Glue. Unexpected downtime was common, and performance slowed down after a few days of operations between restarts.

You might think that an IT firm would be able to apply its expertise to its own environment. They had the know-how to deliver a top-of-the-line example of their services. However, they did not have the time and money to do so No.

As employee employee, the environment was the result of a random horde. To address issues in an aging and piecemeal environment, part-time administrators and IT professionals faced stop-gap measurements. These in turn became the long-term solutions. Similar solutions existed in Active Directory. The number of user accounts tripled the number of actual computers as well. The undocumented VPN solution that relied on the original domain controller could not be reconfigured. (They lost the admin password.) Thus, an upgrade or swing migration would potentially collapse the remote users' tunnel into the network. A C&P approach was must.

# Re-ACLing the Server

One approach is the obvious (somewhat laborious) way: just walk over all those old servers and add Joe's new account to the permissions lists on those servers. This is called reACL because the other name for a list of permissions on a network service is the access control list. It can be a real pain, but some migration tools will do that for you automatically.