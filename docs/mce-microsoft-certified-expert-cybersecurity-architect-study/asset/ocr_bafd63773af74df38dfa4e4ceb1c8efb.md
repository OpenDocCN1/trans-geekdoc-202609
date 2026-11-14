Office cloud policy allows you to enforce policy settings for Microsoft 365 Apps for enterprise on users' devices, even if they are not domain-joined or otherwise managed. Microsoft 365 Apps for enterprise policy settings roam to a device when a user signs in. Windows, macOS, iOS, and Android devices can use policy settings, but not all are available on all operating systems.

When creating policy configurations, you can review and apply policies that Microsoft recommends as a security baseline. If the policy is tagged as a security baseline, you can also filter your view to include only the policies that are tagged as such.

The content is grouped according to the security controls defined by the Azure Security Benchmark and the related guidance for Azure Cloud Services.

Azure Control for SaaS Services (also known as cloud services) focuses on areas such as network security, logging and monitoring, identity and access control, data protection, vulnerability management, inventory and asset management, secure configuration, malware defense, data recovery, incident response, penetration tests, and red team exercises.

What is penetration testing? A penetration test is a simulated cyberattack against your system, application, and data to check for exploitable vulnerabilities. In web app security, penetration testing is typically used to expand a web application firewall (WAF).

Penetration testing can concern the attempted breaching of any number of application systems (for example, application protocol interfaces [APIs], front-end/back-end servers) to discover vulnerabilities, such as unsanitized inputs, that are tolerant to code injection attacks.

Understandings by the penetration test can be utilized to fine-tune organization WAF security policies and patch witnessed vulnerabilities.

Table 7.1 provides a complete mapping between Azure Cloud Services and Azure Security Benchmark.

For references and more information, see the following:
github.com/MicrosoftDocs/SecurityBenchmarks/raw/master/
Azure%20offer%20Security%20Baselines/1.1/
azure-cloud-services-security-baseline-v1.1.xlsx

# **TABLE 7.1** Azure Cloud Services and Azure Security Benchmark

| Azure Control | Responsibility | Benchmark Recommendation |
|---|---|---|
| Network Security | Customer | Protect Azure resources within virtual networks. |
| Network Security | Customer | Monitor and log the configuration and traffic of virtual networks, subnets, and NICs. |
| Network Security | Customer | Protect critical web applications. |
| Network Security | Customer | Deny communications with known malicious IP addresses. |
| Network Security | Customer | Record network packets. |