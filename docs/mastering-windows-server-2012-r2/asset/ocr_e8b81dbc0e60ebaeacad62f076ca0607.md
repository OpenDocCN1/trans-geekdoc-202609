# 13. Click Next.

# GLOBAL CATALOG OR UNIVERSAL GROUP MEMBERSHIP CACHING

When configuring an RODC in a site, you will need to consider whether to make it a global catalog server or enable universal group membership caching. Chapter 22 includes details that can help you decide what to use in a production site, but for a test lab, you can get away without either.

The RODC Options page will appear. This page will allow you to select a delegated administrator account or group for the RODC.

+   14. Select and apply the Remote Office Admins group you created earlier in the exercise.

Take note of both the accounts that are allowed to replicate passwords and the accounts that denied password replication attributes to the RODC. If you wish to make any changes to these default policies, simply click the Add button to allow or deny replicated passwords. Remember that Den always takes precedence, if you have an account or group that lives in both columns, then password replication to the RODC will not occur. Your display will look similar to Figure 23.13.

FIGURE 23.13
RODC Options page

![](bbox=[0.32, 0.487, 0.855, 0.815])

+   15. Click Next.

The Additional Options page will populate, allowing you to specify a path to install from media and choose a specific domain controller to replicate from if you want to.