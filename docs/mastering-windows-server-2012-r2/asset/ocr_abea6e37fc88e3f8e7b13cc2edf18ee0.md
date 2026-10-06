# CHAPTER 24 CREATING LARGER ACTIVE DIRECTORY ENVIRONMENTS: BEYOND ONE DOMAIN

when the global catalog is needed in the login process. Errors in the other domain controllers and workstation events will probably give you a subtle hint of this condition.

The global catalog has a little of everything. It has a subset of properties or attributes for every object in the forest. Remember, an object includes users, contacts, groups, computers, and other entities registered in Active Directory. So, all domain controllers are GCs that have personal information for every user in the forest even if the global catalog isn't in the same domain as the user.

How many GCs are necessary? Typically it is dictated by how many sites you have. There are many uses for GCs: The most prominent is assisting in the login process. If all users assigned principal names (UPNs)@test.com within a multiple domain forest, domain controllers need to resolve which domain they actually belong. The global catalog provides this information. So, it would be nice if a global catalog was in a site where the users are logging onto the domain.

Since a global catalog has all of this information, Active Directory–applications like Exchange Server love global catalogs. Exchange Server uses the GC to find all recipients and distribution group members in the organization. It would be nice if the Exchange Server had a GC in the same site.

You'll have to weigh this against the potential replication traffic that the servers will receive from the other domains. All domains replicate their domain information to each global catalog. Typically, the importance of global catalogs for login and Exchange Server significantly outweighs this consideration.

Once you have decided how many GCs are needed, you need to log on as an enterprise admin and enable domain controllers within the forest. This is done in the Active Directory Sites and Services console. Drilling through Sites, to a specific site, and to the Servers object, you'll see that the properties of the NTDS settings have a Global Catalog check box with a lot of punch, as shown in Figure 24.10.

# Figure 24.10
Enabling a global catalog

![](bbox=[0.318, 0.574, 0.663, 0.898])