
The `STRUCTURED_PRIVILEGE_NAME` output column will indicate the source of the restriction. A unique row will exist for each unique analytic privilege.

The `STRUCTURED_PRIVILEGE_FILTER` output column will indicate the syntax of the restriction in relation to the analytic privileges that produced the restriction. A unique row will exist for each unique analytic privilege.

The `STRUCTURED_PRIVILEGE_STATUS` output column will contain the value `APPLIED` when a restriction is found and applied. If the value `NOT AUTHORIZED` is returned, then the user doesn’t have any analytic privileges assigned. Other values, such as `NOT GRANTED`, `NO MATCHING ATTRIBUTE`, and `NO FILTER VALUES FOUND`, are also possible depending on the type of structured privilege referenced.

## 10.8 Granting Analytic Privileges

In this section, we’ll review the options available for granting analytic privileges to and revoking analytic privileges from grantees: SQL commands, the SAP HANA cockpit, the SAP HANA Web-Based Development Workbench security manager, and repository-based role scripts or repository-based role editor options.

### 10.8.1 Granting Analytic Privileges with SQL

When you create an analytic privilege, that privilege is owned by the system user `_SYS_REPO`. Analytic privileges are a type of structured privilege, but you can’t use the standard `GRANT` and `REVOKE` SQL syntax to assign analytic privileges to a grantee. Instead, you must use a specific stored procedure to grant and another to revoke analytic privileges for a grantee.

To grant an analytic privilege to a grantee, you must execute the `GRANT_ACTIVATED_ANALYTIC_PRIVILEGE` stored procedure in the `_SYS_REPO` schema. To use this procedure, the security administrator must have the `EXECUTE` object privilege on the stored procedure. The procedure provides two input parameters. The first parameter should contain the name of the analytic privilege, and the second input parameter should contain the name of the grantee. Use the following SQL syntax to execute the stored procedure and assign the analytic privilege:

```
CALL "_SYS_REPO"."GRANT_ACTIVATED_ANALYTICAL_PRIVILEGE"
('<ANALLYTIC_PRIVILEGE_NAME>','<GRANTEE>');
```

Following is another example, using an actual analytic privilege and role:

```
CALL "_SYS_REPO"."GRANT_ACTIVATED_ANALYTICAL_PRIVILEGE"
('"e-corp.sales.security/ap_sales_reporting_region"','ROLE_REGION');
```

To revoke an analytic privilege from a grantee, you must execute the `REVOKE_ACTIVATED_ANALYTIC_PRIVILEGE` stored procedure in the `_SYS_REPO` schema. This stored procedure uses the same two input parameters. Use the following syntax to execute the stored procedure:

```
CALL "_SYS_REPO"."REVOKE_ACTIVATED_ANALYTICAL_PRIVILEGE"
('<ANALLYTIC_PRIVILEGE_NAME>','<GRANTEE>');
```

The following example uses an actual analytic privilege and role:

```
CALL "_SYS_REPO"."REVOKE_ACTIVATED_ANALYTICAL_PRIVILEGE"
('"e-corp.sales.security/ap_sales_reporting_region"','ROLE_REGION' );
```

### 10.8.2 Granting Analytic Privileges with the SAP HANA Cockpit

Let’s review the workflows necessary to grant and revoke analytic privileges with the SAP HANA cockpit. As an alternative to using SQL statements, you can use the SAP HANA cockpit options called `Assign Privileges` or `Manage Roles`. Each interface allows you to both grant and revoke analytic privileges for a given user account or for a given role. Most users will find using the SAP HANA cockpit easier than memorizing and entering in SQL statements.

To access the `Assign Privileges` or `Manage Roles` interfaces, start at the SAP HANA cockpit Home screen, locate an SAP HANA system in the Resource Directory. Connect to the desired tenant database or `SYSTEMDB`, which will take you to the System Overview window. Using the `Filter by Area` dropdown list, choose the option `Security`. Locate the `Assign Privileges` or `Manage Roles` in the `User & Role Management` tile.

[Figure 10.16](#10_008.html#f10.16) shows the `Assign Privileges` interface within the SAP HANA cockpit for the `TEST_01` user account. In the windows, you’ll see several tabs for various privilege categories starting with the `System Privileges`, `Object Privileges`, `Analytic Privileges`, `Application Privileges`, `Package Privileges`, and `Privileges on Users` tabs. You’ll find a similar interface when working with roles. However, the `Role Details` GUI has an additional link called `Roles` where you can grant existing roles to the selected role.

The third tab in the `Assign Privileges` window is named `Analytic Privileges`. Click this tab to list, grant, or revoke analytic privileges for a given grantee.

The privileges listed in this interface have already been granted to the user or role. If the list is blank, nothing is currently granted. To grant an analytic privilege, click the `Edit` button located on the far-right side of the interface near the `Search` field. Once you click the `Edit` button, new buttons labeled `Save`, `Cancel`, `Add`, and `Remove` will appear. Click the `Add` button to open the `Select Analytic Privileges` popup window. Within this window, you’ll see a search bar and a list of analytic privileges with checkboxes. Use the search bar to filter the list based on the entered text. Then, scroll through the list and select the checkbox beside the analytic privilege you want to grant. With one or more analytic privileges checked, click the `OK` button to add the desired items to the user. Your selected analytic privileges should now appear in the `Analytic Privileges` section.

[![Managing Privileges Assigned to User Accounts in the SAP HANA Cockpit](bilderklein/klein10_016.png)](img-f10.16.html)

**Figure 10.16** Managing Privileges Assigned to User Accounts in the SAP HANA Cockpit

To assign the `Grantable to Others` privilege, locate an analytic privilege in the list. To the right, you’ll see a slider button to move to `Yes`, thus allowing the user to grant the same privilege to another user or role. Repeat this process for each analytic privilege in the list. Once you’ve added all the desired analytic privileges to the list, click the `Save` button to grant the privileges. Note that most analytic privileges are owned by the system user `_SYS_REPO` and cannot be configured as grantable to others. However, generic structured privileges, like the runtime catalog object type, can be configured with this option.

To revoke an analytic privilege, start by clicking the `Edit` button again, then select the checkbox beside each analytic privilege in the list, and click the `Remove` button to revoke the privileges. Repeat the process for each analytic privilege you want to revoke. Once you’ve removed all the desired analytic privileges, click the `Save` button. The removed privileges will be revoked, and the user object will be updated.

During the process of adding or removing privileges, you can click the `Cancel` button to discard any unsaved changes. Clicking the `Cancel` button will deactivate the `Add`, `Cancel`, and `Remove` buttons and return you to a read-only list of currently granted analytic privileges.

### 10.8.3 Granting Analytic Privileges with the SAP HANA Web-Based Development Workbench

The SAP HANA Web-Based Development Workbench security manager, hosted within the XS engine, provides an interface that you can use to create users, create roles, or manage security for standard roles. This interface provides a web-based alternative to SAP HANA Studio and also serves as an alternative to issues `GRANT` and `REVOKE` statement with SQL.

You can access the SAP HANA Web-Based Development Workbench via a supported Internet browser. The following URLs can be customized to match the details of your environment:

*   `http://sap-hana.myhost.com:8000/sap/hana/ide/security`
*   `http://<sap_hana_host>:80<instance_number>/sap/hana/ide/security`

In the last example, replace `<sap_hana_host>` with the host name of the SAP HANA system in your environment and `<instance_number>` with the two-digit instance number corresponding to your SAP HANA system.
