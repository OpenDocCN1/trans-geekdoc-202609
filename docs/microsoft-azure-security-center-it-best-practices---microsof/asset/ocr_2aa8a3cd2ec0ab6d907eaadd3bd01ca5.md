![](bbox=[0.158, 0.031, 0.918, 0.403])

# # Integration with Microsoft Defender ATP

Security Center extends its Cloud Workload Protection Platforms (CWPP) offering integration with Windows Defender Advanced Threat Protection (ATP) and bringing comprehensive Endpoint Detection and Response (EDR) capabilities. The Microsoft Defender ATP sensor is automatically enabled for supported Windows Servers that are onboarded to Security Center. With this integration, Security customers can access the Microsoft Defender ATP console to perform a detailed investigation to uncover the scope of a breach.

> **IMPORTANT** This feature supports detection on Windows Server 2012 R2, Windows Server 2016, and only servers with Standard Tier subscriptions. By the time we were writing this chapter, the support for Windows Server Defender ATP in Windows Server 2019 was not available yet.

The onboarding process is seamless from the user's perspective. If the machine is in Azure and Auto Provision is configured to On, the Microsoft Monitoring Agent (MMA) will be deployed. After the MMA is deployed, it will check whether the operating system is supported to receive Windows Server Defender ATP. If it is enabled, the Microsoft Defender ATP sensor is deployed to the VM. This whole onboarding process can take up to 24 hours.