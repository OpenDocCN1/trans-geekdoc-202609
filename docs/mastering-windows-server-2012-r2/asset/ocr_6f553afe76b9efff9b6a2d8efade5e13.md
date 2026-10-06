Consider the impact of the solitary empty root domain controller:

+   - All Kerberos authentication traffic goes through the forest root domain. Remember, it is "friends with everyone", specifically, the root of each tree.

+   - Time synchronization is centralized by the PDC emulator of the forest root, which happens to be the first domain controller by default.

+   - Two FSMO roles, Naming Master and Schema Master, reside in this domain and on that sole DC.

So, if solitary empty domain controller goes down, the rest of the forest will see the effect. You can't make a replica domain controller without one from which to replicate, so you will be stuck performing a cold-iron restore. You may have to rebuild the Active Directory environment from scratch and migrate users and computers to it if a restore is not available.

# Active Directory Design Pointers

The purpose of this chapter is to give you an overall idea of how AD's pieces work. Earlier we discussed the primary decision areas for an Active Directory design. We strongly suggest that you peruse the rest of this book before starting to build your AD structure, because the AD permeates Windows-based networks. But the following sections provide a few hints on how to get started designing your AD structure.

# Examine Your WAN Topology

Domain controllers in a domain must replicate themselves to keep domain information consistent across the domain. DCs need be connected exactly 24/7—you could just dial connections between branch offices and the home office every day or so and then force replication to occur, although that's not simple and may lead to problems down the road—but on the whole you'll find that domains work best if they have a constant end-to-end connection. If you have an area that's poorly or sporadically served by your WAN connections, perhaps it's best to make it a separate domain or a separate forest.

# Lay Out Your Sites

Once you know what the WAN connections are, list the sites you'll have, name them, and figure out which machines go in which sites. Also, consider the nature of connections—speed and cost—to assist Active Directory in the instersite bandwidth wisely.

# Figure Out Which Existing Domains to Merge and Merge Them

You'll probably want to merge the number of domains in your enterprise. One way to do that would be to merge resource domains into a master domain. The idea here would be that you upgrade the master domain to Server 2012 and then merge other domains into that master domain as organizational units using the Active Directory Migration Tool (ADMT) or whatever migration tool you might buy. Merging domains and using the ADMT are topics discussed in detail in Chapter 25.