First, let's understand a few aspects of Cloud Identity. Cloud Identity is accessed via a separate console (admin.google.com). Cloud Identity is also the first product that you will interact with when you configure your Google Cloud environment, as the super administrator account exists in Cloud Identity. There will be more on the super administrator account later in this chapter. Cloud Identity only provides an authentication service and not authorization. The authorization aspect is covered by Google Cloud Identity and Access Management (IAM), which is accessed via the Google Cloud console (console.google.com).

Before we get into the configuration and setup of Cloud Identity, let's look at some of the key features to better understand Cloud Identity. Cloud Identity is the same IDaaS that powers Google Workspace, and it's available both as a free version and a premium version. The premium version has no cap on the number of users, although you can ask Google in the free version to increase the number of users from the default 50-user limit. The other differences include the premium version's support for Secure LDAP, access to the Google security center, mobile device management, auto-exporting audit logs to BigQuery, and session length management, which you control the duration of the authentication tokens. Finally, the free version comes with no service-level agreements (SLA's).

Now that we know about the differences between free and premium Cloud Identity, let's take a quick look at some of the features of Cloud Identity that we will cover in this chapter.

# Single pane of glass

![](bbox=[0.193, 0.488, 0.806, 0.823])

Figure 5.1 - Google Cloud Identity features