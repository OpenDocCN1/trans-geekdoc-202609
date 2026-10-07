# Google Cloud Identity Access Management

There are some main differences between a service account and a user account:

+   - Service accounts have no ability to log in to the Cloud console like a normal user.
- Public and private RSA key pairs are used to authenticate the service account and sign the API request.
- A service account can be impersonated by a human or another service account.
- Service accounts are not visible in Cloud Identity because they belong to the Cloud managed domain. While service accounts can be added to a Google group, it is not recommended since groups are meant for specific purposes that service accounts do not fit into.
- A service account is not created in your Google Workspace domain. They are not under the control of your Google Workspace and Cloud Identity administrators. They live in Google Cloud and should be managed there.

![](bbox=[0.173, 0.365, 0.856, 0.5])

Figure 6.3 – Service account and resource

As depicted in Figure 6.3, service accounts get access to perform actions on a Google Cloud resource via an IAM role, just like users. Now we will see how to manage the lifecycle of service accounts.

# Creating a service account

Service accounts can be created under the IAM | Service accounts menu in the Cloud console. Service accounts can also be created using gcloud, REST APIs, or client libraries.

To create a service account, the user should have the Service Account Admin role (roles/iam.serviceAccountAdmin) to wait.

It is recommended to wait for a minimum of 60 seconds before you use the service account post creation.

# Disabling a service account

You can disable a service account either by using the Cloud console, gcloud, or APIs. However, note that if a resource is using a service account, after disabling the resource can no longer access Google Cloud resources.