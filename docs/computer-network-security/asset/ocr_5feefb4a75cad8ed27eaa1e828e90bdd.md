![](bbox=[0.13, 0.1, 0.88, 0.48])

# Figure 5.1. The separation of the different types of networks into distinct zones

# 5.6.3. Rules applied to interzone traffic

The following rules are applied to a ZFW when routing traffic:

+   - a security zone must be created before it can be assigned interfaces;
+   - an interface may be assigned to a single security zone;
+   - by default, traffic is authorized between interfaces that belong to the same zone;

a security policy must be pre-configured in order to authorize traffic to pass between two zones. Three actions can be taken:

+   - **Pass**: traffic is allowed to transit from one zone to another;
+   - **Inspect**: allows traffic and inspects return traffic;
+   - **Drop**: delete the traffic;

Any traffic towards a router interface (“self-zone”) is authorized unless explicitly prohibited.