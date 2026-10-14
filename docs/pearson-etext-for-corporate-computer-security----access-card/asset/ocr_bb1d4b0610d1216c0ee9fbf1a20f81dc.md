# PATCH MANAGEMENT SERVERS

Faced with overwhelming patching loads, many companies now use internal patch management servers. Patch management servers learn what software is running on the firm’s servers. Patch management servers then actively assess what programs on each host need to be patched and push patches out to the servers. Patch management servers can greatly reduce patching costs.

In corporate environments using Windows Server, it is possible to manage patches, hotfixes, and updates through Windows Server Update Services (WSUS). It allows systems administrators to manage the download, distribution, and application from a centrally managed server (Figure 7-14). Administrators can make sure each machine is updated and apply patches when appropriate.

# THE RISKS OF PATCH INSTALLATION

Installing patches is not without its own risks. First, added security often comes at the cost of reduced functionality, which might not be justified given the degree of added safety offered by a patch.

Second, some patches actually freeze machines or do other damage. This is particularly bad if a patch has no uninstall option. Firms typically download a patch on a test system and examine the effects of the patch thoroughly before rolling the patch out to all servers or clients. If a company has a standard security baseline for various types of hosts, chances are good that experiences on the test system will mirror those on other hosts.

# Test Your Understanding

+   8. a. Why do firms have a difficult time applying patches?
+      b. Why do many firms prioritize patches?
+      c. How do patch management servers help?
+      d. What two risks does patching raise?

# 7.4 Managing Users and Groups

7.4 Explain how to manage users and groups.

# The Importance of Groups in Security Management

The next aspect of host hardening we will discuss is creating and managing user accounts and groups. Every user must have an account. In addition, it is common to create groups and then add individual users to these groups. When security measures, such as requiring long and complex passwords, are applied to groups, all users in these groups are automatically subjected to these measures. Applying security measures to groups obviously requires much less labor than applying these measures to accounts individually.

Applying measures to groups also tends to reduce errors because most groups have well-defined roles that lead to clear security requirements. Individuals, by contrast, may have multiple roles with different security requirements, making it difficult to assign proper security settings to individual accounts.

# Test Your Understanding

+   9. Give two reasons why assigning security measures to groups is better than assigning security measures to individuals within groups.