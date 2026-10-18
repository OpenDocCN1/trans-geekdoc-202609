
Privileges listed in this interface are already granted to the user or role. If the list is blank, nothing is currently granted. To grant a system privilege, click `Edit` button located on the far-right side of the interface near the `Search` field. Once you click the `Edit` button, new buttons labeled `Cancel`, `Add`, and `Remove` will appear. Click the `Add` button to open the `Select System Privileges` popup window. Within this window, you’ll see a search bar and a list of system privileges with checkboxes to their left. Use the search bar to filter the list based on the entered text. Then, scroll through the list and select the checkbox beside the system privilege you want to grant. With one or more system privileges selected, click the `OK` button to add the desired items to the user. Your selected system privileges should now appear under the `System Privileges` tab, as shown in [Section 7.2](#07_002.html#h7.2).

[![List of Selected System Privileges](bilderklein/klein07_002.png)](img-f7.2.html)

**Figure 7.2** List of Selected System Privileges

To assign the `Grantable to others` privilege, locate a system privilege in the list. To the right, you’ll see a slider button to move to `Yes`, thus allowing the user to grant the same privilege to another user or role. Repeat this process for each system privilege in the list. Once you’ve added all the desired system privileges to the list, click the `Save` button to grant the privileges.

To revoke a system privilege, start by clicking the `Edit` button again, then select the checkbox beside each system privilege in the list, and click the `Remove` button to revoke the privileges. Repeat the process for each system privilege you want to revoke. Once you’ve removed all the desired system privileges, click the `Save` button. The removed privileges will be revoked, and the user object will be updated.

During the process of adding or removing, you can click the `Cancel` button to discard any unsaved changes. Clicking the `Cancel` button will deactivate the `Add`, `Cancel`, and `Remove` buttons and return you to a read-only list of currently granted system privileges.

### 7.3.3 Granting System Privileges with the SAP HANA Web-Based Development Workbench

The SAP HANA Web-Based Development Workbench security manager, hosted within the SAP HANA extended application services, classic model (SAP HANA XS) engine (XS engine), provides an interface that you can use to create users, create roles, or manage security for standard roles. This interface provides a web-based alternative to the SAP HANA cockpit and also serves as an alternative to issuing `GRANT` and `REVOKE` statement with SQL.

You can access the SAP HANA Web-Based Development Workbench via a supported Internet browser. The following URLs can be customized to match the details of your environment:

*   `http://sap-hana.myhost.com:8000/sap/hana/ide/security`
*   `http://<sap_hana_host>:80<instance_number>/sap/hana/ide/security`

In the last example, replace `<sap_hana_host>` with the host name of the SAP HANA system in your environment and `<instance_number>` with the two-digit instance number corresponding to your SAP HANA system.

For secure access, the following examples should help you construct the correct URL:

*   `https://<sap_hana_host>:43<instance_number>/sap/hana/ide/security`
*   `https://sap-hana.myhost.com:4300/sap/hana/ide/security`

Once you have access to the SAP HANA Web-Based Development Workbench security manager, expand the `Security` node on the right. Expand `Roles` to reveal a list of standard roles defined in the system. Double-click a role to open the management interface for the given role. With the selected role management window open, you can begin granting and revoking privileges.

###### Note

To perform the same action for an individual user account, expand the `Users` node and double-click the desired user account.

Recall that we recommend the use of repository-based roles to support an SAP HANA security model. However, in this section, we’ll simply highlight the basic workflow if you chose to manage security with standard roles or directly on individual user accounts.

With the GUI management interface open for a given grantee, you can add a system privilege as follows. Locate the tab labeled `System Privileges`. Click the plus (`+`) button to add and search for the desired system privilege. The `Find System Privileges` window will appear where you can search for a specific system privilege. Select the desired system privileges and click `OK` to add them to the list. Choose `Grantable to Other Users and Roles` to the right of each listed system privilege as needed.

To save your changes, press `(Ctrl)+(S)` or click the disk icon at the top left to save and activate the privilege. To revoke a system privilege, select it in the list and click the red `X`. Once again, save the changes to make them active within the database system.

If any activation issues arise, warning messages will appear in the status pane at the bottom of the user management window. The status pane has a dark background. Error messages will appear in red text. Errors are only generated during an attempted activation or saving of changes.

### 7.3.4 Granting System Privileges with Repository Roles

When SAP HANA was initially released, assigning system privileges to standard roles was the best available option. Multiple GUIs and SQL statements were created to help organizations manage granting privileges to and revoking privileges from standard roles. As SAP HANA evolved, repository roles were introduced to aid in application development efforts. Because of their numerous benefits, we highly recommend that you use repository roles to generate security models. Now, let’s review the process for granting and revoking system privileges within repository-based roles.

#### Script-Based Repository Roles

In [Chapter 6](#06_001.html#h6), we introduced you to repository roles and outlined the workflows required to create and manage repository roles. In this section, we’ll again review the syntax necessary to assign system privileges to design-time repository-based role scripts. If you require more information about this process, refer to [Chapter 6](#06_001.html#h6).

When defining system privileges within design-time repository-based role scripts, you must start each line with `system privilege:`. After the colon, you can provide a comma-separated list of system privileges. At the end of the list, include a semicolon to finish the line. If you don’t want to include a comma-separated list, you can explicitly list each privilege on its own line, with each line beginning with `system privilege:`.

The following snippets of code show the definition of system privileges within a repository roles script. The first line includes three privileges, each separated by a comma; the remaining two lines only include a single system privilege each:

```
system privilege: AGENT ADMIN, AUDIT ADMIN, AUDIT OPERATOR;    
system privilege: AUDIT OPERATOR;    
system privilege: CREATE REMOTE SOURCE;
```

As you can see, you can reuse the `system privilege:` expression multiple times within the script. You can also consolidate them all into a single line in which each privilege is comma-separated. Note that the `_SYS_REPO` account has been granted all system privileges by default. The `_SYS_REPO` account also can grant all system privileges to other users or roles by default.

#### SAP HANA Web-Based Development Workbench Editor
