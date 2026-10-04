The Microsoft Graph API provides a unified interface and standard schema for integrating security solutions from Microsoft and its partners. By connecting to one endpoint with one authentication key, organizations can greatly simplify alert management. A single call to the Microsoft Graph Security API returns alerts from Azure Security Center, AD Identity Protection, Azure Information Protection, Microsoft Cloud App Security, as well as Office365, Windows, and Azure Advanced Threat Protection. Organizations can also use the Microsoft Graph Security API to update the alert status. For example, when you close an Azure Security Center alert in an integrated application, it will show as dismissed in Azure Security Center.

Organizations can connect to the Microsoft Graph Security API directly via the API or using PowerShell scripts. Connectors from Azure Logic Apps, Microsoft Flow, PowerApps, and Power BI provide code-free options for automation and reporting. Samples for Azure Notebooks offer an easy way to analyze alert data in Jupyter notebooks. Also, SIEM integration via Azure Monitor is supported.

Visit aka.ms/graphsecurityapi to learn more about leveraging the Microsoft Graph Security API to integrate Azure Security Center alerts with your security tools and workflows.

Sarah Feder, Principal Group PM Manager, Graph Security API team

Figure 10-2 shows a representation of the different components that can be used with the Graph Security API.

| Apps | Web apps | Device and native apps | Bots | Background processes | Analytics dashboard and tools | Automation workflows |
|---|---|---|---|---|---|---|

| Common Libraries, Authentication, and Authorization |
| Microsoft Graph | Alerts | Secure Store | Indicators | Actions | Other Graph Services (Azure AD, O365, SharePoint, Intune...) |
|---|---|---|---|---|---|

| Graph Security API - Federated Queries, Aggregates Results, Applies Common Schema |
| Security Providers | Windows Defender ATP | Office 365 ATP | Azure ATP | Azure Identity Protection | Cloud App Security | Azure Security Center | Azure Information Protection | Azure Sentinel |
|---|---|---|---|---|---|---|---|---|

**Figure 10-2** Graph Security API architectural diagram