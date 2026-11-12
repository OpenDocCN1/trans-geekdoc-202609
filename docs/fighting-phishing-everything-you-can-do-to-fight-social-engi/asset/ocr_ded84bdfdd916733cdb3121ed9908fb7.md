+   - All endpoints should have host-based firewalls enabled with appropriate industry-recommended rules when available.
+   - All endpoints should have intrusion detection software enabled.
+   - All endpoints should have authentication logon screens and access control enabled.
+   - All endpoints with user logon capabilities should have a locked screensaver for inactivity longer than three minutes.

# Firewall/Network Isolation

+   - The network should have one or more firewalls enabled using industry-recommended rules.
+   - Firewalls should never have ANY-ANY rules enabled, except when needed briefly for troubleshooting purposes. Anytime an ANY-ANY rule is enabled, it must be approved by IT management before being implemented and proactively deleted immediately after the test is completed.
+   - VPNs are required to connect to the network remotely. VPN should be protected by a phishing-resistant MFA.

# Secure Coding (SDL Stuff and Signed Scripts)

+   - All company programmers and contractors must be trained in secure development lifecycle (SDL) techniques.
+   - All programmers must use type-safe languages and tools.
+   - All programmers must develop on approved, programming-specific workstations.
+   - Programmers are not allowed to use code found on non-company websites unless that code has been security-reviewed.