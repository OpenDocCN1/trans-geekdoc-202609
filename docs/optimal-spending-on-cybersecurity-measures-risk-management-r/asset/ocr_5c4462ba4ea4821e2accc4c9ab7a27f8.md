+   • Google has agreements with suppliers that include requirements to address information security risks.

# IDENTITY MANAGEMENT, AUTHENTICATION AND ACCESS CONTROL

+   • The Möbius Platform uses roles (Student, Instructor and Administrator) to grant levels of access. These roles are managed at the application tier unless LTI or LDAP is being used, in which case they are mapped from the information provided by these services.

+   • Software access to hosted instances is granted securely to the Möbius development staff to establish and maintain the software. All access is granted/revoked based on “need to know” best practices. DigitalEd’s tools handle access to machines through the enforcement of the public RSA keys that are created by the users needing access. Employees are required to use unique credentials when conducting administrative functions.

+   • Möbius is fully interactive and provides validation and error messages to help guide the user.

+   • Each Möbius instance is deployed in its own container on the GCP, and all data are stored in an isolated database.

+   • To gain access to Möbius, users must register and authenticate with a valid username and password.

+   • Users of the Möbius service can be authenticated by external LDAP or API services.

+   • All access, error and system messaging in addition to application logging is enabled. Audit logs contain login, logout, source Internet protocol (IP) addresses and a variety of actions performed.

+   • All traffic to Möbius traverses a wireless access firewall (WAF). For selected paths, DigitalEd can direct that traffic to the WAF with both standard checks and specific checks for the application. DigitalEd can change the set of paths on demand.

+   • Software access to hosted instances is granted securely to Möbius development staff to set up and maintain the software. All access is granted/revoked based on “need to know” best practices. The software handles access to machines through enforcement of public RSA keys that are created by the users needing access.

+   • GCP employs various next-generation threat protection (NGPT) techniques at the data centre level, as outlined here: https://storage. googleapis.com/gfw-touched-accounts-pdfs/google-cloud-security- and-compliance-whitepaper.pdf.

+   • Google’s management performs periodic assessments of internal identity, authentication and source code management controls.