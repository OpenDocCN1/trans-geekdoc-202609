After that, choose the **Load balancer name** from the dropdown as shown in the following figure. A load balancer will listen to HTTP port **80**. Choose the **Target group name** as **mlapp-tg** from the dropdown, which you created and configured in the load balancer section.

Service IAM role
Task definitions that use the awsvpc network mode use the AWSServiceRoleForECS service-linked role, which is created for you automatically. Learn more.

![](bbox=[0.2, 0.245, 0.8, 0.52])

Figure 13.41: ECS Service-target and port

# **Step 3: Set Auto Scaling (optional)**

Auto-scaling is optional. This will automatically update the service’s desired count within a specified range based on CloudWatch alarms. In the current scenario, the default is used, that is, **Do not adjust the service’s desired count**. Click on **Next step**.

# **Step 4: Review**

In this step, review the configuration for the service. Here, you can go to the previous step to update the configuration. If it looks fine, then go ahead and create a service by hitting the **Create Service** button, as shown in the following figure:

![](bbox=[0.37, 0.78, 0.64, 0.81])

Figure 13.42: ECS Service-Review

After step 4, the service will be created; however, it will take a few minutes to create the desired number of tasks for that service. The progress of task creation can be