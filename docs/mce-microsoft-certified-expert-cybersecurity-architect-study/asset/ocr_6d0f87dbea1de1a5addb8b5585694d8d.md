Team members should consider the following questions:

+   - Is there a way to detect an attack?
+   - If you are attacked or penetrated, how will you respond?
+   - Is there a way to recover from an attack, such as when data is leaked or tampered with?

# # Strategies for Mitigating Threats

Identifying every possible threat to a system is impossible because the list is so long. In some cases, security holes are caused by dependency issues, such as outdated operating systems and libraries. Maintaining these dependencies is crucial.

The majority of modern web applications make APIs available for clients to use. A well-designed web API should support the following:

+   - **Platform independence:** No matter how the API is implemented internally, any client should be able to call it. For this to work, standard protocols must be used, and an agreement must be reached on the data format to be exchanged between the client and web service.
+   - **Service evolution:** Client applications should not depend on the web API to evolve and add functionality, and the API should be able to support existing client applications without requiring any modifications. All functionality must be discoverable so that client applications can fully use it.

Focus on the web API's business entities. An e-commerce system, for instance, might have customers and orders as its primary entities. The process of creating an order involves sending an HTTP POST request that contains the order information. HTTP responses indicate whether the order has been placed successfully. Nouns (the resource) should be used as resource URIs whenever possible rather than verbs (the operations on the resource).

> From the SC-100 exam standpoint, remember that a security strategy's critical components for preventing breaches are threat models, code reviews, security testing, and SDLs.

# # Specify Priorities for Mitigating Threats to Data

Microsoft maps cybersecurity weaknesses in your organization to actionable security recommendations, prioritizing them according to their impact. Mitigating or remediating vulnerabilities is easier with prioritized recommendations.