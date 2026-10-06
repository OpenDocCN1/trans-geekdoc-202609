# FIGURE 22.15
Three sites connected with three sites links

![](bbox=[0.483, 0.111, 0.804, 0.329])

Since the CrossHQ link is connected with the fastest link (a 10 Mbps line), I have assigned it a cost of 10—the lowest cost of each of the links. The CrossRemote link is the slowest at 1 Mbps, and I have assigned it the highest cost of 100. CrossHQ has a 2 Mbps WAN link, and I have assigned a cost of 25.

When HQ replicates with the crosstown office, it sees that the direct path through CrossHQ has the lowest cost of 10 as a cost of 125 (10 + 25) if it went through the remote office.

However, when the remote office needs to replicate with the crosstown office, the least-cost path is HQ with a cost of 35 (10 + 25). The direct path using the CrossRemote link has a cost of 100, so it would be used only if one of the paths failed.

# ## Configuring Intersite Replication

Now you've seen how to create subunits, sites, and site links, you'll learn how to configure them to match your network infrastructure.

You already know that within a site AD replicates by building a replication topology between domain controllers. The same topology across WAN links would be inefficient, so AD instead creates a minimal spanning tree, meaning it creates a set of site-to-site replication paths that minimize the load on your WAN bandwidth.

Take a look at the AD Sites and Services snap-in in Figure 22.16. It shows three sites with IP site links.

Notice that the cost of each of the sites has been modified within Active Directory Sites and Services. You'll see how to do this in a moment.

This is a simple enterprise, and it'll serve fine to manage the issues in a multiple environment. You, once you set up your sites, DCs figure out how to replicate all by themselves within the *site*. But across sites, they need a little help.

You tell AD about connections between sites by creating site links. You help AD identify which path to use for replication, when to perform replication, and how often to perform replication by configuring the site link properties.

If you double-click any site link object, you'll see a dialog box similar to Figure 22.17.