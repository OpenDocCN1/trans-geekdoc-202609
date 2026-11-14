+   - api://<string>/<appId>
+   - https://<tenantInitialDomain>.onmicrosoft.com/<string>
+   - https://<verifiedCustomDomain>/<string>
+   - https://<string>.<verifiedCustomDomain>
+   - https://<string>.<verifiedCustomDomain>/<string>

A verified customer-owned domain must be used for the AppId URI to prefix scopes in the API's code. Additionally, the value must be globally unique for multi-tenant applications.

**Application ownership**: Keep the number of people who own apps within the organization to a minimum. To maintain ownership of the application registration, Microsoft recommends checking the owner's list once every few months.

**Checklist**: A checklist is available in the Azure Portal to guide app developers in ensuring their app registration meets a high-quality bar. When combined with the Microsoft identity platform, the integration assistant highlights best practices and recommendations that help bypass oversights.

# # Security Standards for Onboarding Applications

Organizations should use guidance and automation tools from external sources to secure cloud applications rather than starting from scratch.

+   - Organizations can improve their security posture by using resources and lessons learned from external organizations that have already adopted these models more quickly.
+   - Rather than writing custom versions of well-established functions like databases, encryption, identity directory, and authentication, developers should use the services provided by your cloud provider.
+   - Using native security features built into cloud services should be preferred over adding external security components (such as data encryption, network traffic filtering, threat detection, and so on).
+   - Use identity services rather than cryptographic keys to authenticate.
+   - Implement web application firewalls (WAFs) to prevent attackers from exploiting common security vulnerabilities.
+   - The following guidelines are intended to help you manage this new application architecture type:
+     - Enforce security for applications hosted in containers, general application best practices, and some specific guidelines.
+     - Two popular threat model standards are STRIDE and Open Web Application Security Project (OWASP), which enable the identification of more potential risks.