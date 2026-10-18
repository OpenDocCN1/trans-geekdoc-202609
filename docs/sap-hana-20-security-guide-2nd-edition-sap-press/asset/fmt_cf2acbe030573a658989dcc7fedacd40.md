
Unlike standard roles, repository roles require a slightly different process when assigning them to existing users or roles. Standard roles rely on specific GRANT SQL syntax. For example, `GRANT <SOME PRIVILEGE> TO <GRANTEE>` must be executed to assign a standard role. Repository roles are different. Since they’re owned by the `_SYS_REPO` system account, repository roles can only be granted by that account. Since you cannot log on as this system account, you’ll need an alternative method to impersonate `_SYS_REPO` for granting actions.

To accommodate this need, SAP HANA provides special stored procedures to either grant or revoke the assignment of repository roles to other users or roles. You can call these stored procedures directly using the SQL console. These stored procedures also can be automatically invoked using either SAP HANA Studio or the SAP HANA Web-Based Development Workbench security manager. Let’s look at how to grant and revoke repository roles using each of the three available methods.

### 6.5.1 Granting and Revoking Repository Roles with Stored Procedures

Repository roles are granted using the `GRANT_ACTIVATED_ROLE` stored procedure in the `SYS_REPO` schema. For a security administrator to use the stored procedure, he must have EXECUTE rights on the procedures.

The stored procedure requires that you specify two input parameters for proper execution. The first parameter requires the name of an active repository role, and the second requires the name of a grantee. The grantee can be either a user or a role. Use the following syntax:

```
GRANT_ACTIVATED_ROLE"('<Repository Name Name>','Grantee Name')
```

For example, to grant the Security.Roles::consumer repository role to the user account G3457543, you would execute the stored procedure in the SQL console as follows:

```
CALL "_SYS_REPO"."GRANT_ACTIVATED_ROLE"
('Security.Roles::consumer','G3457543');
```

To revoke a repository role, you’ll need to use another stored procedure found in the `_SYS_REPO` schema, named `REVOKE_ACTIVATED_ROLE`. For a security administrator to use the procedure, they must have been granted EXECUTE rights on the procedures. This stored procedure has the same two input parameters as the previous example. For example, to revoke the repository role Security.Roles::consumer from the user account G3457543, you would execute the stored procedure in the SQL console as follows:

```
CALL "_SYS_REPO"."REVOKE_ACTIVATED_ROLE"
('Security.Roles::consumer','G3457543');
```

The grant procedure is set up to execute the role granting actions as if the system account `_SYS_REPO` were executing the code. This arrangement ensures that the grantor is not the user account executing the procedure. Therefore, you don’t need to worry about protecting the grantor of the role. The revoke procedure performs a similar function. When executed, the procedure impersonates the `_SYS_REPO` user, and the role is easily revoked because `_SYS_REPO` was the grantor.

### 6.5.2 Granting and Revoking Repository Roles with SAP HANA Cockpit

At this time, the SAP HANA cockpit does not properly support the granting of repository-based roles, and therefore, we do not recommend using this interface when granting repository-based roles. As an alternative, you can use the SQL syntax in the SAP HANA cockpit SQL console to grant and revoke repository roles.

### 6.5.3 Granting and Revoking Repository Roles with the SAP HANA Web-Based Development Workbench

As mentioned in [Chapter 5](#05_001.html#h5), the SAP HANA Web-Based Development Workbench security manager, hosted within the SAP HANA XS engine, provides an interface that you can use to create users, create roles, and manage security.

You can access the SAP HANA Web-Based Development Workbench security manager by updating the following two URLs to match the details of your environment:

*   `http://<sap_hana_host>:80<instance_number>/sap/hana/ide/security`
*   `https://<sap_hana_host>:43<instance_number>/sap/hana/ide/security`

Once you have access to the SAP HANA Web-Based Development Workbench security manager, expand the Security node on the right side of the window. Expand Users to reveal a list of users. Click a user to open the management interface for the given user account. With the selected user management window open, you can begin granting and revoking repository roles using the Granted Roles tab. [Figure 6.16](#06_005.html#f6.16) shows an example of the Granted Roles tab with existing repository role granted.

[![Granting Repository-Based Roles with the SAP HANA Web-Based Workbench Security Interface](bilderklein/klein06_016.png)](img-f6.16.html)

**Figure 6.16** Granting Repository-Based Roles with the SAP HANA Web-Based Workbench Security Interface

Notice that, in the GUI under Granted Roles, the grantor for repository roles is `_SYS_REPO`. Effectively, the GUI is executing the correct stored procedures when granting or revoking repository roles.

To revoke the repository role, select the role in the Granted Roles list. Click the red X button to revoke the role. Save your changes to activate the action at runtime.

To help demonstrate the concept of repository roles further, let’s review a case study where we examine how E-Corporation used repository roles to create a security model.

## 6.6 Case Study: Creating Basic Repository Roles

E-Corporation has recently implemented an analytic solution within the SAP HANA platform. The company has provisioned tables; loaded data with an extract, transform, and load (ETL) tool; and created a series of SAP HANA information views. The user community will primarily interact with the SAP HANA information views, which will be secured with an analytic privilege that limits data access by region. Each user will have her own logon to the SAP HANA system to accommodate the data security requirements. However, users will primarily access the data via SAP BusinessObjects Business Intelligence (BI). The SAP BusinessObjects BI system has been configured to support single sign-on (SSO) for the SAP HANA platform with Security Assertion Markup Language (SAML) authentication.

In addition to the privileges needed to secure access to the information views, the security model must support power user access, developer access, and security administrator access.

E-Corporation has contacted its lead SAP HANA security consultant and requested help in defining a security model to accommodate its security requirements. The consultant has determined that a series of repository roles will need to be defined. Let’s look further at the consultant’s decision-making process and the four repository roles recommended for this project.

### 6.6.1 Consumer Repository Role

The first repository role will provide a base level of access to SAP HANA information views. The name of the repository role will be `consumer`. This role will grant SELECT and EXECUTE access to the `_SYS_BI` schema, which is required because additional metadata is published to this schema. The role will also grant SELECT access to the design-time calculation view `e-corp.sales.models::SCV_CUSTOMER_SALES`. Users will need to have SELECT access, at a minimum, to query the information views and metadata in the `_SYS_BIC` schema. When you reference the design-time calculation view in the repository role, the system will automatically grant access to its corresponding column view in the `_SYS_BIC` schema. An analytic privilege will also be granted. The analytic privileges will limit the consumer’s access to a series of information views and will dynamically filter the results of the views so that each user will be limited to one or more sales regions based on his predetermined security profile.
