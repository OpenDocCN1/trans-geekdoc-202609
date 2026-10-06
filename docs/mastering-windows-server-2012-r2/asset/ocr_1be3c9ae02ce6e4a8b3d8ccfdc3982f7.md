# WHAT NEEDS AN OU, AND WHAT NEEDS A DOMAIN?

As you read earlier, you can divide up enterprises by breaking them into multiple domains. In addition, you can create a single domain and use organizational units to parcel out administrative control, or you can do any combination of these.

This is partially a political question, but you can get a head start by looking at the perceived needs of organization. Is administration centralized or decentralized? Who manages users accounts? Who manages the resources such as file servers? Do the company's divisions work together, or is there not very much collaboration?

The choice of OU, or multiple domains is to do the network to the controlling forces so they can administer it. OUs provide admins to control the computer, user, or group accounts that they are responsible for. So if admins just need this, organizational units are the way to go. The multiple-domain choice is dependent on who will manage the domain controllers. If there is a separate group of admins who will control the domain apart from the forest root domain, the additional domain would be justified!

From a technical point of view, there are really a few reasons to use more than one domain, as you really have. The biggest reason is replication traffic. If you have two large domains connected only by a slow WAN link, you may find that it makes sense to keep them as separate domains. But think carefully about it—Active Directory is very efficient at using WAN links for replication traffic.

# NAMES FOR YOUR DOMAINS/TREES

Active Directory allows a wider variety of domain names, but sometimes you can have too much of a good thing with too many options. If you're going multidomain, how will the domains fit together? Do you divide geographically, by division, or by function? Where are the lines of control in your organization?

It's important to understand that the names of domains are primarily political. With the exception of the parent-child relation, there is hardly any other technical concern concerning the name. The name will occasionally be reflected to the users through technology such as domain-based Distributed File Systems (DFS) and depend on how they log onto computers. So, because the name will be seen by users, management might care what the domain is named.

# GET THE DNS INFRASTRUCTURE READY

Once you know the names of your domains, you need to map out the DNS infrastructure. Know which servers will support it. Plan how clients will be to resolve internal names and external names. Remember the following:

+   Plan a DNS zone whose matches your AD domain name and are not afraid to use an imaginary top-level domain.

+   It's recommended that you don't use your externally registered DNS names.