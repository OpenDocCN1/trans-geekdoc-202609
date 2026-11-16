![](bbox=[0.15, 0.085, 0.85, 0.355])

Figure 3-4. Bard's direct access to internet feeds gives it an advantage

While accessing outside data sources such as websites, APIs, or third-party databases has advantages, it exposes the application to potential risks. The risks of ingesting untrusted external data sources can range from consuming false or harmful information from compromised websites to becoming a conduit for security threats like malware or unauthorized data access. The untrusted nature of these data sources makes them inherently less controllable than internal resources, thereby adding an additional layer of uncertainty and risk.

The concept of trust boundaries becomes especially pertinent when accessing public internet data. Unlike internal services, where you can uniformly apply security measures, external sources may adhere to security standards different from those of your organization. This differential in trust necessitates additional layers of validation, security checks, and monitoring to ensure that data crossing this boundary doesn't compromise the system.

# Access to Internal Services

Internal services like databases and internal APIs often serve as the backend support structure for LLM applications. They may house critical data from user profiles and logs to configuration settings and even vast data in SQL or vector databases. As a component that often interfaces with various other internal and external elements of the system, internal services represent a critical point in the application's architecture, both functionally and from a security perspective.