
# 11.4 Privileges on Users

Unrelated to application privileges, an additional option named `Privileges on Users` can be used to grant the `ATTACH DEBUGGER` privilege but has a limited scope of usage within SAP HANA. `Privileges on Users` allows a user to grant a grantee debug access to the user’s own session. This privilege only offers the ability to assign the `ATTACH DEBUGGER` privilege and is limited to the grantor’s account.

For example, the user account `SYSTEM` can log on to a SQL console and grant to the user account `ADMIN_MIKE` the `ATTACH DEBUGGER` privilege but only for the user `SYSTEM`. In fact, GUI interfaces for this functionality will only allow you to specify `SYSTEM` account under the User column. This privilege grants `ADMIN_MIKE` debug SQLScript code rights within the `SYSTEM` account’s session. `SYSTEM` is also the only user that can grant this privilege to `ADMIN_MIKE`.

In the following sections, we’ll review two options for granting privileges on users using the SAP HANA cockpit and using SQL statements.

## 11.4.1 Granting Privileges on Users with the SAP HANA Cockpit

Let’s review the workflows necessary to grant and revoke privileges on users with the SAP HANA cockpit. As an alternative to using SQL statements, you can use the SAP HANA cockpit GUI action called `Assign Privileges` or `Manage Roles`. Each interface allows you to both grant and revoke privileges on users. Most users will find using the SAP HANA cockpit easier than memorizing and entering in SQL statements.

To access the `Assign Privileges` or `Manage Roles` area, start at the SAP HANA cockpit Home screen and locate an SAP HANA system in the Resource Directory. Connect to the desired tenant database or `SYSTEMDB`, which will take you to the System Overview window. Using the Filter by Area dropdown list, choose the option Security. Locate the `Assign Privileges` or `Manage Roles` in the User & Role Management tile.

[Figure 11.5](#11_004.html#f11.5) shows the `Assign Privileges` interface within the SAP HANA cockpit `Assign Privileges` for the `TEST_01` user account. In the window, you’ll see several tabs for the various privilege categories starting with the `System Privileges`, `Object Privileges`, `Analytic Privileges`, `Application Privileges`, `Package Privileges`, and `Privileges on Users` tabs. You’ll find a similar interface when working with roles. However, the `Role Details` GUI has an additional link called `Roles` where you can grant existing roles to the selected role.

The sixth tab in the `Assign Privileges` window is named `Privileges on Users`. Use this tab to configure privileges on users.

If already configured, the interface will list the `ATTACH DEBUGGER` privilege with the grantor that assigned this privilege. If the list is blank, nothing is currently configured. To grant attach debugger, click the `Edit` button located on the far-right side of the interface near the Search field. Once you click the `Edit` button, new buttons labeled `Save`, `Cancel`, `Add`, and `Remove` will appear. Click the `Add` button to add `ATTACH DEBUGGER` to the grantee. Notice that the grantor will always be the account used to authenticate with the SAP HANA system. The `Attach Debugger` assignment should now appear in the list. Note that nothing else can be configured here. Only the `ATTACH DEBUGGER` privilege can be assigned, and the grantor is automatically determined as the account used to access the system via the SAP HANA cockpit. Once you’ve configured this option, click the `Save` button to grant the privileges.

![Managing Privileges Assigned to User Accounts in the SAP HANA Cockpit](bilderklein/klein11_005.png)

**Figure 11.5** Managing Privileges Assigned to User Accounts in the SAP HANA Cockpit

To revoke the `ATTACH DEBUGGER` privilege, start by clicking the `Edit` button. Highlight the `Attach Debugger` assignment line then click the `Remove` button to revoke the privilege. Once you’ve removed the item, click the `Save` button. The removed privileges will be revoked, and the user object will be updated.

During the process of adding or removing privileges, you can click the `Cancel` button to discard any unsaved changes. Clicking the `Cancel` button will deactivate the `Add`, `Cancel`, and `Remove` buttons and return you to the prior, read-only state.

## 11.4.2 Granting Privileges on Users with SQL

In addition to using the SAP HANA cockpit, a grantor can execute the following SQL code to grant the `ATTACH DEBUGGER` privilege to another grantee:

```
GRANT ATTACH DEBUGGER TO <GRANTEE>;
```

Replace the `<GRANTEE>` variable with the name of a grantee within your environment. When executed, the grantee will be granted access to debug the grantor’s session.

# 11.5 Summary

Application privileges define custom levels of access to applications developed in the XS engine. Once activated, these privileges can be granted to users or roles within the SAP HANA system. The `Privileges on Users` tab in SAP HANA GUI interfaces is used to grant the `ATTACH DEBUGGER` privilege to another grantee. You can also use SQL to grant the `ATTACH DEBUGGER` privilege.

# 12 Authentication

Authentication is key in validating a user’s access to the SAP HANA system. In this chapter, we’ll discuss how SAP HANA supports external authentication providers in addition to its basic internal authentication mechanism.
