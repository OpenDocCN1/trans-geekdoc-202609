You will be able to manage all your organization’s custom rules when you have the Role Administrator role.

![](bbox=[0.207, 0.135, 0.792, 0.493])

Figure 6.2 - IAM—custom roles

Figure 6.2 shows a few ways you can create custom roles:

+   * By combining predefined roles
* By combining permissions of predefined roles
* By combining a predefined role and adding additional permissions
* Starting with a predefined role but removing some permissions from that role

# Lifecycle of a custom role

Consider the following permissions dependencies while creating custom roles:

+   * A predefined role or many predefined roles may exist for the service before you decide to establish your own custom role.
* TESTING and NOT_SUPPORTED permissions are ineligible for inclusion within a custom role.
* Even if a service’s API is enabled, you may not be able to see or use certain permissions in a custom role. Consider checking out the Google Cloud documentation for custom role permissions.