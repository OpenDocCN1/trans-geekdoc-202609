# Settings - Data Collection

Azure Pass - Tenership

Security Center collects security data and events from your resources and services to help you prevent, detect, and respond to threats. Learn more

# Settings

+   Data Collection

+   Threat detection

# Auto Provisioning

This enables the automatic installation of the Microsoft Monitoring Agent on all the VMs in your subscription. If enabled, any new or existing VM without an installed agent will be provisioned. Learn more

+   Email notifications

+   Pricing tier

![](bbox=[0.235, 0.065, 0.935, 0.245])

FIGURE 2-12 Auto provisioning allows the automatic installation of the agent.

6. If you want to disable Auto Provisioning, click Off and Save. Disabling Data Collection doesn't mean the agent is removed. To remove the agent, you must manually uninstall Microsoft Monitoring Agent from the VM.

> NOTE The steps used in this book are assuming that auto provisioning is enabled. If you are simulating the steps of this book, make sure to leave auto provisioning selected.

Under the Data Collection option, you can also configure the workspace that will be used by Security Center to store the data collected by the agent, as shown in Figure 2-13.

# Workspace configuration

Data collected by Security Center is stored in Log Analytics workspaces. You can select to have data collection from Azure VMs stored in workspaces created by Security Center or an existing workspace you created. Learn more

+   Use workspace(s) created by Security Center (default)
Connect Azure VMs to report to workspaces created by Security Center
Use another workspace
Connect Azure VMs to report to selected workspace

![](bbox=[0.175, 0.675, 0.915, 0.695])

FIGURE 2-13 Options to control the workspace.

In the same tab, you can also configure the level of data collection granularity for Windows systems, as shown in Figure 2-14.