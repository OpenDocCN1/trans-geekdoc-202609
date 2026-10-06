# FIGURE 32.3
Disconnected WSUS server deployment

![](bbox=[0.308, 0.98, 0.843, 0.335])

# FIGURE 32.4
Autonomous mode in a multisite environment

![](bbox=[0.308, 0.377, 0.843, 0.726])

# Complex Hierarchies with WSUS

Depending on the deployment type and the needs of your organization, there are a few additional advantages to using the newer version of Windows Server. Doing so can greatly minimize the server (or virtual) deployments required to manage your environment. Building on the capabilities of Windows Server 2012 R2 and WSUS, you can configure Autonomous mode, Replica mode, as well as branch-office and roaming clients.

Autonomous mode, commonly distributed mode, is the default installation option for WSUS. In this configuration (shown in Figure 31.4), you are using an upstream server to share updates with one or multiple downstream servers, and by leveraging access controls you give local administrators the ability to manage their own environments.