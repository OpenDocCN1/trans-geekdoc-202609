Finally, complete the process by selecting the configuration file type and location. In this case, the Cloud Build configuration file (YAML or JSON) option is selected for Configuration Type and the cloudbuild.yaml file location from the repository is provided, as shown in the following figure:

![](bbox=[0.2, 0.18, 0.8, 0.55])

# Figure 12.15: Creating trigger in Cloud Build – selecting configuration file type and its location

Now, any update pushed to the Cloud Source Repository will trigger the pipeline. To see the build history, go to the **History** section from the side panel or view it through the link from the dashboard.

The following figure shows the build history with **Status**, **Build ID**, the **Source - loan_pred**, that is, the Cloud Source Repository in this case, and **Ref - the master branch** of that repository in this case. It also shows the **Trigger type**, **Trigger name**, and **Duration**, that is, the time taken to complete the build.

![](bbox=[0.13, 0.75, 0.87, 0.92])

# Figure 12.16: Build history