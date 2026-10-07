(D) Rely on public API keys shared between the company and each vendor

**Explanation 423. Correct Answer: B. Implement SSO using Security Assertions Markup Language (SAML).** SAML is an XML-based standard for exchanging authentication and authorization data between parties. It’s designed to facilitate single sign-on for web applications. By implementing SSO with SAML, GlobalTech can allow its employees to authenticate once and gain access to multiple applications without authenticating.

**Option A is incorrect.** Having independent LDAP servers for each application defeats the purpose of SSO and complicates user management.

**Option C is incorrect.** Embedding encrypted user credentials in URLs is insecure and not a recommended practice.

**Option D is incorrect.** API keys are used for system-to-system communication and not for user authentication. Moreover, public API keys shouldn’t be shared recklessly.

**Question 424.** A company wants to implement a solution that verifies the software integrity of remote servers before allowing them to connect to the primary network. Which of the following solutions BEST achieves this objective through attestation?

+   **(A)** Host-based firewall
**(B)** Whitelisting application
**(C)** Remote attestation
**(D)** VPN tunneling