# Google Cloud Identity Access Management

+   - How do I create service accounts with the least privilege?
- How do I enable services in a particular project but not others?
- How do I grant just the right access to users?
- How do I operate in multi-cloud environments?
- How do I find over-provisioned access?
- How do I troubleshoot access issues?

![](bbox=[0.148, 0.287, 0.851, 0.006647999999999999])

In Figure 6.1, you can see how IAM works on the principle of who (identity) has what access (role) to which resource. The principal entity is usually a user, group, or service account. However, there are other principals, as explained later. The role is a set of fine-grained permissions. Permissions are predefined actions that you can take on a particular resource (for example, BigQuery). Permissions for a given resource are fixed and cannot be created. We will talk about service accounts later in this chapter. At this point, the thing to remember is a service account represents a service or application identity in Google Cloud. It is one of the most important distinctions in how Google Cloud handles permissions for workloads. *