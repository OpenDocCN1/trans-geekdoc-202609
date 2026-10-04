# Enable auditing on SQL server

Description
Enable auditing on your SQL Server to track database activities across all databases on the server and save them in an audit log.

General Information

| RECOMMENDATION SCORE | 8/15 |
|---|---|
| RECOMMENDATION IMPACT | +7 |
| USER IMPACT | Low |
| IMPLEMENTATION COST | Low |

Threats

+   - Data exfiltration
- Data leakage
- Malicious insider
- Threat resistance

Remediation steps

+   - To enable SQL server auditing:
- Select the SQL server.
- Under Auditing, select On.
- Select Auditing details and configure a storage account for the audit1 log.
- Click Save.

![](bbox=[0.215, 0.445, 0.765, 0.525])

> FIGURE 4-27 Details about the advantages of enabling auditing on SQL server

3. Click Unhealthy Resources tab at the bottom of this page to see the SQL servers that are affected by this recommendation.

4. Click the SQL server for which you want to remediate this recommendation, and the Auditing blade will open, as shown in Figure 4-28.

![](bbox=[0.185, 0.665, 0.765, 0.895])

> FIGURE 4-28 Remedating the recommendation by enabling auditing

Strengthen your security posture