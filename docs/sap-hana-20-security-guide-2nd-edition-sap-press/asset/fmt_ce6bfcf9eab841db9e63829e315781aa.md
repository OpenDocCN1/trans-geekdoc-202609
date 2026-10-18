
To simplify this mechanism within SAP HANA, you would need to logically devise a system in which a single user owns all objects and that same user grants all privileges. This user should also be set up in such a way that the user can never be deleted from the system. Ideally, this special user would delegate the actions of the developers to prevent their accounts from owing objects. This user would also delegate the actions of security administrators to prevent their accounts from being listed as the grantors of privileges.

Creating this logical system seems an unlikely solution in a multiple user environment. Luckily, SAP HANA has already incorporated this solution into the SAP HANA development repository. The `_SYS_REPO` system user, in this case, becomes both the owner of all repository objects and the grantor of all privileges defined within a repository role. With SAP HANA, you have a single system user account managing security processes while avoiding most of the pitfalls of security management in a multiple-user RDBMS environment.

If you follow the repository-based model when creating objects, developers only need the ability to create repository objects, and security administrators only need the ability to create repository roles and grant them to others. You’ll thus also be able to segregate these actions within the system because the repository-based model offers a way to delineate between users that can define roles and users that can grant roles to others.

In contrast, when you use standard roles and catalog objects, the definer and grantor of roles must have the `ROLE ADMIN` system privilege. This privilege should only be granted sparingly and only to security administrators. Not having a clear delineation also forces security administrators to define all roles and work closely with the developers while doing so. This dependency often proves to be inefficient and prone to error.

The `_SYS_REPO` account therefore is important to the structure of your security model. You should strive for a security model that ensures that this account owns all catalog objects and grants privileges to repository roles.

## 6.1.2 Grantors and Privileges

When you issue a `GRANT <PRIVILEGE>` SQL statement using a standard user account, that user account becomes the grantor of the privilege. The grantor is an important function within a security model. When a privilege is granted to a role or user, only the grantor can revoke the privilege. If you have multiple security administrators operating within an SAP HANA environment, this limitation on who can revoke privileges can be difficult to manage.

For example, if one security administrator grants a privilege to a role, only that administrator can revoke the privilege. If that security administrator is not available one day and the privilege must be revoked, no other user account in the system can revoke that privilege. This situation can be problematic and also introduces risk because key individuals must be always present to manage changes to the security model.

Some organizations will try to solve this problem by creating a dedicated account that’s shared by multiple administrators. However, doing so isn’t recommended because sharing an account reduces your ability to properly audit an individual’s activities when shared accounts are used. In other words, someone can make an important change that affects the security of the system without any record being made of the actual person that performed the change.

When you use repository roles, you don’t need to be concerned with these issues. With repository roles, privileges are always granted using the `_SYS_REPO` system account. You also don’t need to worry about multiple users managing security. A repository role can be updated by anyone with access to the package where the role resides in the SAP HANA repository. Each time a repository role is activated, the privileges within that role are granted with `_SYS_REPO` as the grantor. If a privilege is removed from the repository role definition, the privilege will be revoked from the runtime version of the repository role. Because `_SYS_REPO` is the original grantor, full access to revoke the privilege is always available.

Another important requirement for grantors entails the privileges the grantor needs before it can grant privileges. An account can serve as the grantor if two prerequisites are met. First, the grantor must have been granted the privilege with `WITH GRANT OPTION`. Second, the grantor must own the object. If the grantor doesn’t own the object, the owner must first grant the security administrator the necessary privileges. As mentioned earlier, this arrangement makes the management of a security model based on standard catalog objects and standard roles difficult.

If you use repository objects, again, you won’t encounter this issue. All repository objects will be owned by `_SYS_REPO`. If you reference repository objects in a repository role, `_SYS_REPO` will already be the owner and the natural grantor of the privileges. Now, let’s look at how repository roles can help with the grantor of roles.

## 6.1.3 Grantors and Roles

Just as the security manager account can grant individual privileges, it can also grant existing standard roles to other users or roles. However, before a security account can grant a standard role, the account must meet one of two prerequisites:

*   The user must be directly or indirectly granted the role, and the `WITH ADMIN OPTION` must be set for the granted role.
*   The user must have the system privilege `ROLE ADMIN`. This system privilege allows the assignee to grant or revoke any existing standard role to another user or role.

The `ROLE ADMIN` privilege allows the security administrator to both create and grant roles, which might not be an issue for some organizations. However, if your organization requires the segregation of duties, preventing the creator from also being the grantor of the role will be difficult. Some organizations will insist that the model allow one group to create the roles and another group to be responsible for assigning those roles.

Repository roles are granted using the `"_SYS_REPO"."GRANT_ACTIVATED_ROLE"` stored procedure and are revoked using the `"_SYS_REPO"."REVOKE_ACTIVATED_ROLE"` stored procedure. Repository roles themselves are created within the SAP HANA package hierarchy, and design-time objects can be secured independently from these stored procedures. Therefore, organizations that require a segregation of duties have a solution: The creation of repository roles can be isolated from the privileges required to grant repository roles. Now, let’s summarize the benefits of using repository roles.

## 6.1.4 Why Use Repository Roles?

SAP has announced that the SAP HANA extended application services, classic model engine (XS engine) and `_SYS_REPO`-owned objects will be removed from the platform in the future. However, as of SAP HANA 2.0 SPS 04, in our opinion, no viable alternative exists for managing a comprehensive security model, and repository-based roles work perfectly fine if you continue to develop content in the SAP HANA XS `_SYS_REPO` repository. However, if you’re developing content in the new SAP HANA extended application services, advanced model (SAP HANA XSA) platform, you’ll have no choice but to adopt some of the new security principles of SAP HANA XSA, even if numerous gaps in securing such objects based on best practices still exist.

Overall, repository roles can help your organization achieve a security model in the following ways:

*   As mentioned earlier, the definition of the repository role is stored in the SAP HANA development repository in the form of a text-based script. Therefore, the repository role definition can be managed independently of the runtime version of the repository role.
