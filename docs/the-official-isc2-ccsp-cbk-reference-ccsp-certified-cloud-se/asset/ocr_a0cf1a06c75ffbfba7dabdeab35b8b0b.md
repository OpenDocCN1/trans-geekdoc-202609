+   - **Differing classification schemes:** Different apps and platforms will categorize events with different metadata. For example, one OS may identify user logins as “Informational” events, while apps running on that OS log the same activity as “User Events.” Constructing queries on such varied data will be difficult.

+   - **Identity attribution:** Ultimately logs should be able to answer the basic question “Who did what and when?” Sufficient user ID attribution needs to be easily identifiable; otherwise, it may prove impossible to definitely state that a particular user took a given action. The organization’s identity and access management system may offer the ability to utilize a single identity across multiple services, but many cloud services enforce their own user management, complicating the attribution of events to a specific user.

+   - **Application-specific logs:** Apps may offer the ability to generate logs, but unlike widely standardized tools like operating systems or web server software, they may log information in a unique format. SaaS platforms may offer even fewer configuration options as internal functionality such as event logging configuration is not exposed to the end users. Making sense of this data in relation to other sources, such as an app that uses a numeric ID value for users while others use an email address, can be challenging.

+   - **Integrity of log files:** App and OS log files typically reside on the same hosts as the software generating the logs and so are susceptible to tampering by anyone with privileged access to the host. If a user has administrative permissions, they may be able to not only perform unauthorized actions but then cover up evidence by modifying or deleting log files.

The full Logging Cheat Sheet is available here: cheatsheetseries.owasp.org/cheatsheets/Logging_Cheat_Sheet.html.

# Logging, Storage, and Analysis of Data Events

Logs are made valuable only by review; in other words, they are valuable only if the organization makes use of them to identify activity that is unauthorized or compromising. Due to the sheer volume of log data generated, it is unlikely a human being would be capable of performing log reviews for any computing environment more complex than a single application.

SIEM tools, which are covered in detail in Domain 5: Cloud Security Operations, can help to solve some of these problems by offering these key features:

+   - **Log centralization and aggregation:** Rather than leaving log data scattered around the environment on various hosts, the SIEM platform can gather log data from operating systems, applications, network appliances, user workstations, etc., providing a single location to support investigations. This is often referred to as