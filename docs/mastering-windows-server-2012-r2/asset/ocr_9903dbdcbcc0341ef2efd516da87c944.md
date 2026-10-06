# PLANNING YOUR ACTIVE DIRECTORY ENVIRONMENT

If the link is not capable of supporting the replication traffic, you should consider multiple domains. The domain partition, the largest part of an Active Directory, would be limited to the location office where it resides. The configuration and schema partitions would be replicated over the WAN link, but they would not change frequently. This would greatly reduce the amount of replication traffic.

Active Directory allows you to tell it what should replicate its information, all parts of its database as to being replicated. Organizations with multiple locations need to consider whether the available bandwidth can support the replication traffic.

While we're on the subject, the global catalog (GC), which contains objects from every domain, receives from domains across the forest. The GC is essential for the user login process and Exchange Server, which should be located near the users. Then, every domain will replicate information to GCs across the WAN links to other sites as well. The available bandwidth may not support this traffic; therefore, separate forests may be the ticket.

# Multiple Domains: When They Make Sense

When, should you use one domain within OUs, and when you should have different domains or even different forests? A general rule of thumb is, "Don't use multiple domains unless must." So, the real question is, "When do multiple domains make sense?" They make sense in a few cases:

+   **Replication Problems Due to Poor Bandwidth** This is probably all domain controllers in a domain need to be online and accessible to each other all the time. Replication between domain controllers must be consistent; if the WAN link can't support the replication traffic, it's better to implement multiple domains. Think of it this way: suppose you had one office in Chicago and another in Sydney (Australia) with an expensive link between the two. Suppose also that you had 20,000 people in the Chicago office and 150 in the Sydney office. Every time the Chicago people changed their passwords, you'd have to replicate all traffic over the costly WAN link to build domains. That's not a great way to

+   **Legal Requirements** There may be legal considerations that would require separate domains and possibly separate forests. Although you don't initially think multiple forests are part of Active Directory, there are situations where they are necessary.

Since you can't prune a tree from a forest, you have to consider the organization is thinking on the topic of restructuring. A spin-off would be a separate forest to ensure a separation from the main Active Directory.

Some national laws may prevent sharing of information across national boundaries. The Global Catalog role lists private information for everyone in the forest. It also includes contacts with their information. Some countries may have a problem with that. Thus, separate forests may be required.

Organizations may have similar regulations for users. Perhaps control of secret user accounts must be contained within four walls of a certain building, or resources must be segregated with tighter security control. Given the legal mandates, a separate domain or forest may be needed. With the potential security concerns within a forest, separate forests may be required here as