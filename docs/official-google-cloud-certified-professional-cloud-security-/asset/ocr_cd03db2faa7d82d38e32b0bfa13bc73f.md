# DLP architecture options

![](bbox=[0.144, 0.098, 0.856, 0.355])

Figure 10.3 – Hybrid inspection architecture

As shown in 10.3, you may feed data from practically any source—including sources outside Google Cloud—directly to Cloud DLP via hybrid jobs and job triggers, and Cloud DLP will analyze the data for sensitive information and automatically record and aggregate the scan results for further analysis.

Hybrid jobs and job triggers encompass a set of asynchronous API methods that allow you to scan payloads of data from virtually any source for sensitive information, and then store the findings in Google Cloud. Hybrid jobs enable you to write your own data crawlers that behave and serve data similarly to the Cloud DLP storage methods.

Hybrid environments are common in enterprises. Many organizations store and process sensitive data using some combination of the following:

+   - Other cloud providers
- On-premises servers or other data repositories
- Non-native storage systems, such as systems running inside a virtual machine
- Web and mobile apps
- Google Cloud-based solutions