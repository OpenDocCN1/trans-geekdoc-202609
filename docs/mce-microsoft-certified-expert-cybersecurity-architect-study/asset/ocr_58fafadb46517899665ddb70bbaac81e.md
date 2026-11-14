# Define the Security Requirements for Web Workloads

The security requirements for your web workloads must be considered when evaluating Azure App Service. Azure App Service is a web application, REST API, and mobile back-end service based on HTTP. Both Windows and Linux-based environments are compatible with these applications.

As part of the Azure App Service platform, you will have access to Azure VMs, storage, network connections, web frameworks, management, and integration functionality. Azure App Service has the following security requirements:

+   * **Ensure that you secure your apps with HTTPS:** It is already possible to access your app through HTTPS once it has been created (app_name.azurewebsites.net). For clients to make secure HTTPS connections to your custom domain, you should configure the custom domain with a TLS/SSL certificate.
+   * **Disable insecure protocols:** The App Service provides a one-click configuration to enforce HTTPS, which means unencrypted (HTTP) traffic is turned away before it ever reaches your application code.
+   * **Create static IP restrictions:** Default settings allow your App Service application to accept requests from any IP address on the Internet, but you can restrict this access to a subset of IP addresses. For example, App Service on Windows allows you to define a list of IP addresses permitted to access your application.
+   * **Enable client authentication and authorization:** The Azure App Service provides a turn-key authentication and authorization service for clients and users. The user and client app can sign in with little or no application code. You may use App Service to handle the authentication and authorization process or implement your own solution.
+   * **Don't store application secrets:** There is a commonly accepted method for accessing application secrets, such as database credentials, API tokens, and private keys, by referencing them as environment variables.
+   * **Implement network isolation:** Isolated tiers provide complete network isolation by deploying your applications within a dedicated App Service environment hosted in your Azure Virtual Network instance.

# Security Posture Management for App Service

The overall security posture of web workloads needs to be continually assessed, just as it does for any cloud workload. Defender for App Service utilizes the cloud scale to identify attacks targeting applications running over App Service. Attackers probe web application weaknesses to find and exploit them—requests to applications running in Azure pass