An initiative definition is a collection of policy definitions that is tailored toward achieving a singular overarching goal. Initiative definitions simplify the management and assignment of policy definitions. They simplify policy assignments by grouping a set of policies into a single item—an initiative definition. Figure 3-1 shows components.

# Initiative

# Policy Definition

# Policy parameters in JSON format

![](bbox=[0.435, 0.275, 0.735, 0.355])

FIGURE 3-1 Azure Policy components

While having this understanding of Azure Policy is important, you don't need to create any initiative or policy when using Security center center policy integration with Azure Policy because Security Center will automatically create it for you. The default initiative is ASC Default (subscription:your_subscription_id), and it contains all security policies. The number of policies will keep changing as the Security Center Engineering team continues adding new services to monitor and creating new recommendations, which will be reflected as new policies. To access Azure Policy and see the Security Center initiative and policies, follow these steps:

+   1. Open the Azure Portal and sign in with a user who has Security Admin privileges.

+   2. In the left navigation pane, click All Services and type Policy; the Policy blade appears, as shown in Figure 3-2.

![](bbox=[0.235, 0.675, 0.93, 0.805])

FIGURE 3-2 Azure policy dashboard