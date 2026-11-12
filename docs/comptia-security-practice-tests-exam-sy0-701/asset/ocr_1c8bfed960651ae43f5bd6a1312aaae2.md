105. D. While auditors may request application version information during audits, they are not typically notified during normal application updates and patching cycles. Application administrators, service owners, and system administrators are all commonly notified about functional validation test results so that they can take further action or know that the service update is complete.

106. B. Each individual has their own keypair in asymmetric encryption systems; thus, for four individuals to communicate securely using asymmetric encryption four keypairs are needed.

107. D. A dedicated, hardware-based, cloud-hosted hardware security module (HSM) is an appropriate solution for Michelle's needs. Cloud providers often provide shared HSMs as a service, which can increase perceived risk due to the shared underlying hardware. Dedicated hardware is typically available at a higher cost. Trusted platform modules (TPMs) are used to provide secure boot and related services, not to store secrets for an organization.

108. B. To sign a file, Murali needs to use his own private key. The recipient can then use their public key to validate the signature.

109. C. OCSP requests must include the certificate's serial number to allow the OCSP responder to check the CA database for the certificate and its status. It does not require the domain name or requestor's name. Open public ledgers are part of blockchains, not OCSP.

110. C. Wildcard certificates have a * in them, denoting that they can be used for any subdomain. For example, in this question, the wildcard would match any *.example.com subdomain like test.example.com and sales.example.com. Self-signed certificates will not link to a root or intermediate CA, and thus cannot be verified with CAs.

111. A. Policies and procedures are examples of directive controls. Deterrent controls attempt to dissuade attackers from taking action. Preventive controls attempt to stop security issues from occurring. Proactive controls are not a control category used on the Security+ exam.

112. A. Allow lists can be difficult to manage over time, particularly as manufacturers and vendors add additional download and update sites and subdomains. This creates additional work for administrators and can cause errors or issues with updates and patching if not carefully monitored. Allow lists do prevent sites from being visited if they are not on the list, they can be configured with wildcards to allow entire domains or subdomains if desired, and they only allow sites that are added, meaning any problems with unwanted sites are the responsibility of the allow list administrator.

113. A. EAP is commonly used for authentication to wireless networks. MS-CHAP is used with PPTP-based VPNs, Kerberos is used for organizationwide authentication, and LDAP is used as part of authentication in Microsoft Active Directory domains, among other uses.

114. A. Validation testing should follow application restarts to ensure the application is working as expected after the restart. Documentation and updating version information can be done after the validation because if validation fails the change may need to be reversed. Vulnerability scanning should have been done prior to implementation in a test environment if needed, and then should be done as part of ongoing security operations.