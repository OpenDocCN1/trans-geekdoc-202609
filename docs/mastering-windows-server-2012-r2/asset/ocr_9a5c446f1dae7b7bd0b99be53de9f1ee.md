# FSMOS AND GCS 1211

You see, by default, AD assigns the FSMO roles to the first DC that you install. In this story, 1 GHz system quickly served a very important role. But now it can't. And AD isn't smart enough to figure out that and nominate a new computer in that. You might say that our "sparkling" forest has lost its "fizz-moe." It's your job to transfer the FSMO roles to other DCs.

It's important to know where the FSMO roles live and operate in your environment. We have a few general recommendations on where certain roles should live in the domain and forest. Try not to spread roles across multiple domain controllers as much possible. For the most part, the primary domain controller of the forest root domain should be the PDC, Schema Master, Domain Naming Master and RID Master. Having them all centrally makes them easier to manage. Technically speaking, the Infrastructure Master role can operate on any domain controller in an environment where every domain controller is a GC server. If you are in a multicast environment where not all of your DCs are GC, you must place the Infrastructure Master role on a domain controller that does not have the global catalog. We will take a look at each role in depth over the next sections.

# Global Catalogs

We've mentioned global catalog servers throughout the chapter. So, you might expect that their type would fall into this FSMO category. They don't really, they are not "single". Although you start out with one, you can enable other domain controllers to assume the role. However, like FSMO roles, it is important to know which domain controllers have the role and where they are located.

![](bbox=[0.19, 0.513, 0.47, 0.532])

# DECOMMISSIONING WITH DCPROMO AD DS

This story all about the 1 GHz domain controller is not unrealistic. We encountered situations where an uninformed admin wiped away the hard drives of a failed domain controller keeping the domain going "It was old anyway." It just happened to be the first DC of the domain.

If you run into a disaster and cannot recover the system, there are methods, discussed, to move the FSMOs from that failed domain controller.

For starters, the first one is the first domain controller you build. Since all the necessary roles are required from the get-go, the FSMOs and the Global Catalog role are slammed onto that first server. So, with the previous example, the ghost of the 1 GHz workstation will rear its ugly head