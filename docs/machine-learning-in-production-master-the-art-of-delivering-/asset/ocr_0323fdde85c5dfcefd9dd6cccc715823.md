# # Configure Jenkins

Now, mainly two sections are to be configured for the current scenario: GitHub webhook integration and extended email integration.

+   1. Go to Jenkins dashboard.
+   2. Go to **Manage-Jenkins | Manage Plugin**.
+   3. Install Git, GitHub, and email plugins without restart.

If the preceding plugins are already selected, you can continue to the next step.

Now, let’s configure the GitHub webhook in Jenkins.

Go to **Manage Jenkins | Configure System**.

Scroll down and update the **API URL** in the **GitHub** section, as follows:

```
https://api.github.com
```

In the **Credentials** section, add GitHub’s PAT generated in the previous step. You can leave the **Name** field blank.

Finally, click on the **Save** button.

The following figure shows GitHub webhook integration in Jenkins:

![](bbox=[0.14, 0.54, 0.85, 0.87])

Figure 9.5: GitHub configuration in Jenkins