

cleared for top secret, which means he can also view secret and confidential information because those are less sensitive. If Dwayne were authorized to access only confidential data, however, he would not be able to read up to higher levels like secret. Compartmentalized objects require clearance from a specific domain or group, such as the Department of Homeland Security.

In a *compartmentalized system*, it is possible to separate data into separate categories. For example, Dwayne, who works for the Department of Defense, would not be able to read documents cleared for the State Department; Dwayne would have a top secret—sensitive compartmentalized information (TS-SCI) clearance. The military would be exercising a MAC system with least privileges to ensure that because Dwayne has TS, he has only the necessary access required to complete his job.

A *hybrid design* combines elements of both hierarchical and compartmentalized designs.

Important items to know about MAC include the following:

- It’s considered a need-to-know system.
- It involves more overhead than DAC.
- All users and resources are assigned security labels.

> **Caution**
>
> Although MAC uses a security label system, DAC systems allow users to set and control access to files and resources.

## Role-Based Access Control (RBAC)

RBAC, also known as nondiscretionary access control, enables a user to have certain preestablished rights to objects. These rights are assigned to users based on their roles in the organization. The roles almost always map to the organization’s structure. Many organizations are moving to this RBAC because it eases access management. For example, if you are the IT administrator of a bank, there are some clearly defined roles, such as bank manager, loan officer, and teller. RBAC allows you to define specific rights and privileges to each group. The users are then placed into the groups and inherit the privileges assigned to their groups. If Joan is a teller and gets promoted to loan officer, all the administrator must do is move her from the teller group to the loan officer group. Many modern OS designs use RBAC.

RBAC is well suited to organizations that have a high turnover rate. Assigning access rights and privileges to a group rather than to an individual reduces the burden on administration. How RBAC is implemented is up to the individuals designing the operating system. For RBAC to work, roles within the organization must be clearly defined in policy.

Your organization might decide to use _static separation of duties_ (SSD). SSD dictates that a member of one group cannot be a member of another group. Let’s say Mike is a member of the network administrators group. In this case, Mike cannot also be a member of the security administrators group or the audit group. For SSD to work, roles must clearly be defined to make it clear where conflicts exist within the organization.

Another design is _dynamic separation of duties_ (DSD). DSD dictates that a user cannot combine duties during any active session. Let’s say Mike is a member of the audit group and the audit management group. If Mike logs on to perform an audit test, he does not have management rights. If Mike logs on under the audit management group, he cannot perform an audit test.

Table 6.8 provides an example of separation of duties.

## TABLE 6.8 Separation of Duties

| Role | Example of Allowed Access |
|---|---|
| User | Web browsing, approved applications, and changes to desktop appearance |
| Auditor | Review of firewall logs, server logs, and application logs |
| Security administrator | Firewall administration, ACL updates, and server patching |

Task-based access control (TBAC) is similar to RBAC but instead of being based on roles, it uses tasks. TBAC is based on tasks so that the allowed duties are based on the types of tasks a specific individual would perform. A good example of this can be seen when you access Windows Server 2019. In the user administration group, you can see some predefined profiles, such as print manager, backup manager, and power user. The access assigned to each of these is based on the types of tasks the individual would perform.

## Attribute-Based Access Control

Attribute-based access control (ABAC) is a more dynamic, flexible, context-aware and adaptive type of access control. ABAC has a much greater number of possible control variables than RBAC. ABAC has a set of characteristics called *attributes*, which can be any of the following:

- **User attributes**: These attributes include items such as a user’s name, role, organization, and security clearance.
- **Environmental attributes**: These attributes include items such as the time of access, location of the data, and current organizational threat levels.
- **Resource attributes**: These attributes include items such as creation date, resource owner, filename, and data sensitivity.

ABAC can control security and access on a more fine-grained basis, and it is implemented to reduce risks due to unauthorized access. For example, ABAC can place granular limits on user access, such as only allowing user access during certain times, in certain regions, or for certain branch offices relevant to the employee in question. Keep in mind that ABAC is complex, and in some cases it may provide more control than is really needed; in such cases, RBAC might be a better option. As a security professional, you must always balance risk and cost. There’s no reason to use the more granular option if it is not needed as using it would simply mean incurring additional resource costs.

ABAC is supported by Extensible Access Control Markup Language (XACML), which defines the policies, requests, and architecture. It is based on XML and includes policy decision points (PDPs), which evaluate policies against access requests provided by policy enforcement points (PEPs). A PDP may also need to query a policy information point (PIP) to gather descriptive attributes about the user or any other missing attribute in a request. A policy administration point (PAP) is used to manage the PDP and PIP functionality (see Figure 6.13).

![](img/cd307d33c10f35ada49ea76811ef60ad_488_0.png)

## FIGURE 6.13 XACML ABAC Architecture

## Rule-Based Access Control

Rule-based access control is based on a specific set of rules, much like a router ACL. Rule-based access control is considered a variation of DAC. Rule-based access control involves the following steps:

- 1. Intercept each request.
- 2. Compare it to the level of authorization.
- 3. Make a decision.

For instance, say that a router uses a rule-based ACL that has permissions set to allow web traffic on port 80 and deny Telnet traffic on port 23. These two basic rules define the ACL. ACLs are tied to objects. Permissions can be assigned in three different ways: They can be assigned explicitly or implicitly, or they can be inherited. ACLs have an implicit deny all statement that is the last item processed. A sample Cisco-formatted ACL with both allow (permit) and deny statements is shown here:

```
no access-list 111
access-list 111 permit tcp 192.168.13.0 0.0.0.255 any eq www
access-list 111 deny tcp any any eq telnet
access-list 111 deny icmp any any
interface ethernet0
ip access-group 111 in
```

> **ExamAlert**
>
> Although some people use the terms *access control list* and *capability table* interchangeably, they are not the same. Capability tables are bound to subjects; ACLs are bound to objects.

## Other Types of Access Control

Content-dependent access control (CDAC) is based on the content of a resource. CDAC is primarily used to protect databases that contain potentially sensitive data. CDAC is also used to filter out unauthorized traffic and is typically used by proxies or firewalls. For example, you may be able to log in to your organization’s SharePoint page and see the number of days you will be expected to travel next month but unable to see when or where the CEO will be traveling during the same period.

Lattice-based access control (LBAC) is a MAC-based type of access control that defines the least upper and greatest lower bounds. An upper bound is called a *join*, and a lower bound is called a *meet*. LBAC deals with access in complex situations. It allows access only if the subject’s capability is greater than or equal to that of the object being accessed. For example, Figure 6.14 demonstrates the boundaries in LBAC. If you were cleared for top secret, you could read the level below, which is secret.

