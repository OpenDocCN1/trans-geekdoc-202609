This group is a domain local security group and includes the following members by default:

+   * Cert Publishers
* Domain Admins
* Domain Controllers
* Enterprise Admins
* Group Policy Creator Owners
* krbtgt
* Read-only Domain Controllers
* Schema Admins

# KRBTGT AND KRBTGT123

Writable DCs use the krbtgt account with Kerberos. You can think of it as the Kerberos ticket-granting ticket account, and its password is known by all writable DCs. When tickets need to be created for authentication, they are encrypted with a symmetric key that is derived from the password. Since all DCs use the same password for this account, all DCs can decrypt tickets granted by other DCs.

The Kerberos ticket-granting ticket account works differently on RODCs. First, it has a different name such as krbtgt123 (or another semi-random string of numbers after krbtgt). Second, it has a different password. Writable DCs know the password of the RODC; however, the RODCs don't know the password of the krbtgt account used by writable DCs.

Users with accounts in any of these groups can still log onto the RODC. The only difference is that their credentials won't be cached, preventing the security risk if the RODC is stolen.

# ALLOWED RODC PASSWORD REPLICATION GROUP

The Allowed RODC Password Replication group is also a domain local security group located in the Users container. Figure 23.5 shows the Allowed RODC Password Replication group.
Unlike the Denied RODC Password Replication group, which includes several members by default, the Allowed RODC Password Replication group does not include any members by default. Members added to this group can have their passwords replicated or cached to any RODC in the domain.

If a user is a member of both this group and the Denied RODC Password Replication group, the Denied RODC Password Replication group will take precedence.