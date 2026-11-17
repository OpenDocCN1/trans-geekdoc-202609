
- In a context-based system, access is based on user privileges as defined in the user’s own data records. This is usually granted to persons acting in a certain job role or function.

- In a content-dependent system, access is based on the value or sensitivity of data items in a table. This system checks the content of the data being accessed and allows, for example, a manager of Department A to see employee records for personnel that contain an A in the Department field but not records containing any other value in that field.

## Permission Levels

Permission levels indicate a subject’s rights to a system, application, network, or other resources. In a DAC environment, the authorization system uses permission levels to determine what objects any subject can access. Permission levels can be any of the following:

- **User-based**—The permissions granted to a user are often specific to that user. In this case, the rules are set according to a user ID or other unique identifier.
- **Job-based, group-based, or role-based access control (RBAC)**—Permissions are based on a common set of permissions for all people in the same or similar job roles.
- **Project-based**—When a group of people (for example, a project team) are working on a project, they are often granted access to documents and data related just to that project.
- **Task-based**—Task-based access control limits a person to executing certain functions and often enforces mutual exclusivity. In other words, if a person executes one part of a task, he or she might not be allowed to execute another related part of the task. This is based on the concepts of separation of duties and need to know.

## Mandatory Access Control

**Mandatory access control (MAC)** is another method of restricting access to resources. You determine the level of restriction by how sensitive the resource is. This is represented by a classification label. Individuals must then be formally authorized (i.e., obtain clearance) to access sensitive information. Security policies defined for systems that are used to process classified information (or any other sensitive information) must include provisions for enforcing MAC rules. That is, they must include a set of rules that controls who can access what information.

> **NOTE**
> 
> Remember: Sensitivity labels, or classifications, are applied to all objects (resources). Privilege- or clearance-level labels are assigned to all subjects (users or programs).

Under mandatory access control, the system and the owner jointly make the decision to allow access. The owner gives the need-to-know element. Not all users with a privilege or clearance level for sensitive material need access to all sensitive information. The system compares the subject and object labels that go with the terms of the Bell-La Padula confidentiality model, which is covered later in the chapter. Based on that comparison, the system either grants or denies access.

**Temporal isolation** restricts access to specific times. It first classifies the sensitivity level of objects. Then it allows access to those objects only at certain times. Temporal isolation is often used in combination with role-based access control. You may see temporal isolation more commonly described as **time-of-day restrictions**. Regardless of the term used, they both simply mean restricting access to specific time windows.

## Nondiscretionary Access Control

In nondiscretionary access control, access rules are closely managed by the security administrator. They are not managed by the system owner or by ordinary users for their own files.

Nondiscretionary access control can be used on many operating systems. This strategy is more secure than discretionary access control. The system doesn’t rely only on users’ compliance with organizational policies. For example, even if users obey well-defined file protection policies, a Trojan horse program could change the protection to allow uncontrolled access. This kind of exposure isn’t possible under nondiscretionary access control.

Security administrators have enough control in nondiscretionary access control to make sure sensitive files are write-protected for integrity and readable only by authorized users, to preserve confidentiality. The chances that a corrupted program will be used are reduced because users can run only those programs they are expressly allowed to run.

Nondiscretionary access control helps ensure that system security is enforced and tamperproof. If your organization needs to manage highly sensitive information, you should seriously consider using nondiscretionary access control. It does a better job of protecting confidentiality and integrity than DAC. The data owner, who is often the user, does not make access decisions. This allows you to enjoy some of the benefits of MAC without the added administrative overhead.

## Rule-Based Access Control

In a rule-based system, access is based on a list of rules that determine who should be granted access. Data owners make or allow the rules. They specify the privileges granted to users, such as read, write, execute.

The success of rule-based access control depends on the level of trust you have with the data owners. This type of access control pushes much of the administration down to the data owner. For technical and security-conscious users, this type of access control tends to work well. It doesn’t work as well in environments with many users or where users lack the necessary technical skills and training. FIGURE 5-3 shows how individual rules control each user’s permissions.

## Access Control Lists

Most operating systems provide several options to associate lists or permissions with objects. These lists are called **access control lists (ACLs)**. Different operating systems provide different ACL-enabling options. For example, Linux and OS X have read, write, and execute permissions. These can be applied to file owners, groups, or global users. Windows has both share permissions and security permissions, both of which enable ACLs to define access rules.

### Explicit Rules Grant Access

![](img/b2a7c1cdb4938c3b37d6925de0425ae9_183_0.png)

FIGURE 5-3 Rule-based access control.

Share permissions are used to get to resources by a network share. Security permissions are used to get to resources when the user is logged on locally. Some Windows permissions include the following:

- Share permissions—Full, change, read, and deny.
- Security permissions—Full, modify, list folder contents, read-execute, read, write, special, and deny.

In both share and security permissions, deny overrides every other permission. But what happens if no ACL exists for a resource? Most authorization systems use implicit deny, which means that if no rule to grant access exists, access is automatically denied. This approach is more restrictive but more secure.

Because of the greater number of choices, Windows ACLs are said to be more fine-grained, because they allow a greater level of control. FIGURE 5-4 shows an ACL.

## Role-Based Access Control

Another type of access control is role-based access control (RBAC). An RBAC policy bases access control approvals on the jobs the user is assigned. The security administrator assigns each user to one or more roles. Some operating systems use groups instead of roles. The resource owner decides what roles have access to which resources. Microsoft Windows uses global groups to manage RBAC. FIGURE 5-5 shows RBAC.

Before you can assign access rules to a role, you must define and describe the roles in your organization. The process of defining roles, approvals, role hierarchies, and constraints is called role engineering. Starting with a clear list of role definitions that fit your organization is key to RBAC. The real benefit of RBAC over other access control methods is

**FIGURE 5-4**
An access control list.

| User | Resource | Permission |
| :--- | :--- | :--- |
| Hal | User Hal Directory | Full Control |
| | User Kevin Directory | Write |
| | User Kara Directory | No Access |
| | Printer 001 | Execute |
| Kevin | User Hal Directory | Write |
| | User Kevin Directory | Full Control |
| | User Kara Directory | No Access |
| | Printer 001 | No Access |
| Kara | User Hal Directory | Write |
| | User Kevin Directory | Full Control |
| | User Kara Directory | No Access |
| | Printer 001 | Execute |
| | Printer 002 | Execute |

its ability to represent the structure of the organization and force compliance with control policies throughout it.

Suppose that Jane and Fred in Figure 5-5 should have access to the Inventory application, but Albert should not. As shown in the figure, however, Albert *does* have access to this application—a need-to-know violation. This error is due to the overgeneralizing of roles. Overgeneralizing roles can result in providing more access to individuals

**FIGURE 5-5**
Role-based access control.

![](img/b2a7c1cdb4938c3b37d6925de0425ae9_184_0.png)
