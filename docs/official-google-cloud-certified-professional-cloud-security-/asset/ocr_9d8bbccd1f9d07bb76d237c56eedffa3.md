Under VPC network permissions, select the role as compute.networkUser. Depending on the VPC network sharing mode, IAM principals are granted the Network User role for the entire project or selected subnets. These principals are Project Admins.

In VPC network sharing mode, you have two options; first, there is Share subnets (project-level permissions). Selecting this option will share current and future subnets of the host project with all service projects and Project Admins. Alternatively, if you select Individual subnets (subnet-level permissions), this will selectively share subnets from the VPC networks of the host project with service projects and Project Admins. If you have made your selection, you can move on to the next step.

5. You can save and complete the process of attaching projects.

The Shared VPC Admin can designate service accounts as Project Admins. Service Project Admin has two types of service accounts:

+   - The user-managed service account, with the following format: USER_ID@SERVICE_PROJECT_ID.iam.serviceaccount.com

+   - The Google API service account, with the following format: SERVICE_PROJECT_NUMBER@cloudservices.serviceaccount.com

For both types of service accounts, you have the option to either give access to all subnets or only to limited subnets. In the following example, we will look at giving service account access to all subnets.

The steps to create a user-managed service account or a Google API service account as a Project Admin are the same. They are shown in the following steps, where you need to specify a service account principal based on whether you need a user-managed service account or Google API service account:

+   1. First, we will log in to the Google Cloud console as a Shared VPC Admin and navigate to the Settings page. Here we will change the project to the service project that contains the service account that needs to be defined as a Service Project Admin:

+   2. Next, copy the project ID of the service project. For clarity, we will refer to the service project ID as SERVICE_PROJECT_ID.

+   3. Next, ensure that you change the project to the Shared VPC host project. Then, navigate to the IAM page in the Google Cloud console.

+   4. Next, we will add a new service account by clicking Add.