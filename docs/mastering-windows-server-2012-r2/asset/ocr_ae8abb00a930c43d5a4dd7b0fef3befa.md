# 746 CHAPTER 14 CREATING AND MANAGING SHARED FOLDERS

+   3. You will use the default.

+   4. Next, you will need to give the replication group a name. We'll name it CorpRep, shown in Figure 14.36.

# FIGURE 14-36nNew Replication Group Wizard's Name and Domain screen

![](bbox=[0.318, 0.205, 0.893, 0.574])

+   5. Next, you will need to add the servers that will be part of the replication group.

You should choose these with some thought, because you will add to the amount of data that will flow into and out of the servers selected.

# WAITING FOR Replication

Configuration changes are not applied immediately to all members. The new configuration must be replicated to all domain controllers, and each member in the replication group must poll its closest domain controller to obtain the changes. The amount of time this depends on AD replication latency and the long polling interval (60 minutes) on each member. To poll immediately for configuration changes, open a command-prompt window, and then follow the following command for each member of the replication group: `dfsdiag.exe pollad`