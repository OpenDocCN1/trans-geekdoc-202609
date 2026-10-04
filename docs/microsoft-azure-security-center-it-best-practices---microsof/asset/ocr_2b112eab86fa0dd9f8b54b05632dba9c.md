# Single click remediation

Now that you know the scope of recommendations across different workloads, it is possible to visualize some remediation scenarios and realize that it can be challenging to manually remediate multiple recommendations. To simplify the remediation process, Security Center launched a new feature in summer 2019 that enables you to remediate a recommendation with just a few steps.

By the time we were writing this chapter, the single-click remediation feature was in Private Preview, and for this release, only the following recommendations were available:

+   - Disk encryption should be applied on virtual machines.
- Web Application should only be accessible over HTTPS.
- Function App should only be accessible over HTTPS.
- API App should only be accessible over HTTPS.
- Remote debugging should be turned off for Function App.
- Remote debugging should be turned off for Web Application.
- Remote debugging should be turned off for API App.
- CORS should not allow every resource to access your Function App.
- CORS should not allow every resource to access your Web Application.
- CORS should not allow every resource to access your API App.
- Secure transfer to storage accounts should be enabled.
- Transparent Data Encryption on SQL databases should be enabled.
- Monitoring agent should be installed on your virtual machines.
- Auditing on SQL server should be enabled.

After applying the remediation using this feature, the recommendation will be refreshed according to the recommendation type. If the remediation was performed using Azure Policy (control plane), the refresh will take place in 10 minutes; in other words, the recommendation disappears from the list because it was remediated already.

> TIP The Azure Security Center engineering team is constantly working to improve the dashboard freshness; therefore, it is recommended to visit the Security Center Frequent Asked Questions (http://aka.ms/ascfaq) article for the latest information regarding this latency.