# EXE application control policy violation audited

Learn more

# General information

| Description | |
| --- | --- |
| Description | The below user can run executables that are violating the application control policy of your organization on this machine. It can possibly expose the machine to malware or application vulnerabilities. |
| Activity time | Sunday, March 3, 2019, 9:36:35 PM |
| Severity | Medium |
| State | Active |
| Attacked Resource | <unknown> |
| Subscription | Courto IT - demo |
| Detected by | Microsoft |
| Environment | Azure |
| Resource type | Virtual Machine |
| signature | D=<$GOOGLE,INC.; L=MOUNTAIN VIEW; S=CALIFORNIA; C=<US>$GOOGLEUPDATEDATE.EXE\1.1.33.05 |
| TargetUser | NT AUTHORITY\SYSTEM |
| Hit Count | D=<$GOOGLE,INC.; L=MOUNTAIN VIEW; S=CALIFORNIA; C=<US>$0.0.0.0
%PROGRAMFILE%26$GOOGLEUPDATEDATE$GOOGLEUPDATEDATE.EXE
CN-MICROSOFT AZURE DEPENDENCY CODE SIGN%26$0.0.0.0
$SDRIVE\WINDOWS\AZURESEGMENTAGENTPOLICY.EXE |
| path | |

FIGURE 5-22 Policy violation alert

Application whitelisting is a powerful tool that you can use to protect your Windows and Linux virtual machines running in Azure—on-premises and in other cloud providers. In contrast to our on-premises experience, configuring application whitelisting is an easy-to-manage and effective solution.

> NOTE To learn more about application whitelisting (adaptive application controls), check out the article "Adaptive Application Controls in Azure Security Center" at https://docs.microsoft.com/en-us/azure/security-center/security-center-adaptive-application.