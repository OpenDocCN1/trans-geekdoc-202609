3 In the Grant access page, paste the email ID of the service account that you created in the New Principals field, select Service Account User in the Role field, and click Save, as shown in figure 11.11.

# Grant access to “Compute Engine default service account”

Grant principals access to this resource and add roles to specify what actions the principals can take. Additionally, add conditions to grant access to principals only when a specific criteria is met. Learn about IAM conditions

# Resource

+   - Compute Engine default service account

# Add principals

Principals are sets of users, groups, or service accounts. Learn more about principals in IAM

![](bbox=[0.18, 0.406, 0.683, 0.706])

# Assign roles

Roles are composed of sets of permissions and determine what the principal can do with this resource. Learn more

Figure 11.11 Specifying access to the Compute Engine default service account

Now we have completed the steps to set up the service account for the ML pipeline, we can continue with the setup of the pipeline.

# 11.2.4 Introduction to Cloud Shell

So far, all the actions that we have taken in Google Cloud have been in the Console UI. Google Cloud also includes the Cloud Shell, which is a self-contained instance that lets you run command line commands to interact with Google Cloud. In addition to the