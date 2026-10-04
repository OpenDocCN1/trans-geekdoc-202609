
```json
  "startTimeUtc": "2019-03-18T12:34:52.0616273Z",
  "endTimeUtc": "2019-03-18T12:34:52.0616273Z",
  "type": "host-logon-session",
  "host": {
    "$ref": "centralus_1"
  },
  "account": {
    "$ref": "centralus_3"
  }
}
```

As you can see, there is a lot of information that can be consumed when retrieving alert via REST API. While Security Center security alert dashboard provides important details about the alert, the REST API brings a different perspective to consume the same set of data.

# Accessing Alerts using the Security Graph API

The Microsoft Graph (graph.microsoft.com) is a unified interface to access information from Microsoft online services, such as Azure Active Directory, Office 365, and others. The Security Graph API is based on Microsoft Graph, and can be defined as a unified REST API for integrating security products.

When you make calls to the Graph Security API, they will be federated to all supported Microsoft security products, services, and partners. The results are aggregated in a common schema, which makes correlating alerts from multiple data sources easier. The idea is that when you connect and enrich the alerts, you will be able to easily understand the scope and impact of attack.

# Simplify integration with Microsoft Graph Security API

Today, most organizations rely on a collection of security tools to manage and respond to cyber threats. This can include ticketing, investigation, and automation systems, among others. By integrating Azure Security Center with these tools and workflows, you can streamline security operations and improve threat response.

The Microsoft Graph API provides a unified interface and standard schema for integrating security solutions from Microsoft and its partners. By connecting to one endpoint with one authentication key, organizations can greatly simplify alert management. A single call to the Microsoft Graph Security API returns alerts from Azure Security Center, AD Identity Protection, Azure Information Protection, Microsoft Cloud App Security, as well as Office365, Windows, and Azure Advanced Threat Protection. Organizations can also use the Microsoft Graph Security API to update the alert status. For example, when you close an Azure Security Center alert in an integrated application, it will show as dismissed in Azure Security Center.

Organizations can connect to the Microsoft Graph Security API directly via the API or using PowerShell scripts. Connectors from Azure Logic Apps, Microsoft Flow, PowerApps, and Power BI provide code-free options for automation and reporting. Samples for Azure Notebooks offer an easy way to analyze alert data in Jupyter notebooks. Also, SIEM integration via Azure Monitor is supported.

Visit aka.ms/graphsecurityapi to learn more about leveraging the Microsoft Graph Security API to integrate Azure Security Center alerts with your security tools and workflows.

Sarah Feder, Principal Group PM Manager, Graph Security API team

Figure 10-2 shows a representation of the different components that can be used with the Graph Security API.

| Apps | Web apps | Device and native apps | Bots | Background processes | Analytics dashboard and tools | Automation workflows |
|---|---|---|---|---|---|---|

| Common Libraries, Authentication, and Authorization | | | | | | |
| Microsoft Graph | Alerts | Secure Store | Indicators | Actions | Other Graph Services (Azure AD, O365, SharePoint, Intune...) | |
|---|---|---|---|---|---|---|

| Graph Security API - Federated Queries, Aggregates Results, Applies Common Schema | | | | | | | |
| Security Providers | Windows Defender ATP | Office 365 ATP | Azure ATP | Azure Identity Protection | Cloud App Security | Azure Security Center | Azure Information Protection | Azure Sentinel |
|---|---|---|---|---|---|---|---|---|

**Figure 10-2** Graph Security API architectural diagram

Looking at this diagram from the top, you see that the apps on top are basically consuming the data. You can create your own app to consume data from the Microsoft Security products, located in the third layer (Security Providers). The intermediate interface (Microsoft Graph) is where the Security Graph API is located. Notice in this layer, the Security Graph API has many capabilities other than retrieving alerts, setting actions to alerts. These options are beyond the scope of this chapter, but if you want to learn more about the use of Security Graph API, visit https://aka.ms/securitydocs.

After reviewing this diagram, you can also see that the Security Graph API is an intermediary service (broker) that provides a single programmatic interface to connect multiple security providers (Microsoft and Partners). When planning to build your own app to use the Graph Security API, make sure to cover the following points:

- Register your app with Microsoft Graph: Log in to portal.azure.com to add the app to your Azure AD tenant.
- Specify permissions and secrets: You can use Delegated if your app accesses the API as signed-in user, or you can use Application if your app has its own Role Base Access Control (RBAC).
- Write your code: You can start by leveraging the sample codes at http://aka.ms/graphsecurityapicode
- Get consent from the organization using your app: In this step, the Azure AD Admin needs to grant consent for the organization (tenant) to use the app.

# Using the Security Graph API

The Security Graph API is accessible through the Microsoft Graph; in other words, it uses the single point of connection (https://graph.microsoft.com) with the same syntax REST API and response in JSON format. Security data accessible via the Security Graph API is protected using permissions and Azure AD (AAD) roles. To retrieve alerts from Security Center using the Security Graph API, you need to use the HTTP GET request similar to the example below:

https://graph.microsoft.com/v1.0/security/alerts

One important aspect of this GET request is that it will retrieve all alerts from the service providers that you may have in your tenant, which includes Azure Security Center, Azure Active Directory Identity Protection, Microsoft Cloud App Security, Windows Defender Advanced Threat Protection, Azure Advanced Threat Protection, Office 365, Cloud App Security, Azure Information Protection (preview), Azure Sentinel, and other partner providers to which you may have access, such as Palo Alto Networks.

Depending on the amount of service providers that you have, the amount of data that returns with a simple GET request for all alerts can be substantial. It is a good idea to use filters to target the information that you really want to see. For example, if you want to see only the top 10 high severity alerts, you can use the GET request below:

https://graph.microsoft.com/v1.0/security/alerts?$filter=severity eq 'High'&$top=10

The part of the URL in bold represents the filter that was created to retrieve only the information that you needed. If you want to validate your GET request before start writing your app, you can use the Microsoft Graph Explorer (https://developer.microsoft.com/en-us/graph-explorer) to test the URL. For this example, you would get a result that lists the top 10 high-severity alerts. While this filter helps, it will still show the 10 high-severity alerts for all security providers to which you have access. If you want to see alerts generated by Security Center, you can filter by the vendor provider using the vendorInformation property, as shown in the example:

```
https://graph.microsoft.com/v1.0/security/alerts?$filter=vendorInformation/provider eq='ASC'
```

If you use Microsoft Graph Explorer to run this GET Request while logged in to a subscription that has Security Center on it, this request will retrieve only alerts where the security provider is Security Center (see Figure 10-3).

![](img/4b11e95292819ab1a383a41ef73aedb4_206_0.png)

FIGURE 10-3 Graph Explorer

You can also use logical operators to expand your query. For example, if you want to see only high-severity alerts generated by Security Center, you can use the following GET request. (Notice the addition of the bold strings).

```
https://graph.microsoft.com/v1.0/security/alerts?$filter=vendorInformation/provider eq='ASC' and Severity eq 'High'
```
