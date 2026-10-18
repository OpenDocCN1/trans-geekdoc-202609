
# Package Privileges

The seventh tab in Assign Privileges window is named Package Privileges. The process for granting or revoking package privileges like the process used for object privileges. Packages and privileges listed in this interface are those that are already granted to the role. If the list is blank, nothing is currently granted. To grant a package privilege, click the Edit button located on the far-right side of the interface just to the right of the search field. Once you click the Edit button to enable edit mode, new buttons labeled Cancel, Add Package, Change Privileges, and Remove Package will appear. Click the Add Package button to open the Select Objects popup window. Within this window, you’ll see a search bar and a list of packages. Use the search bar to filter the list based on the entered text. Scroll through the list and highlight the package you want to assign privileges to.

Once you click the desired package, a new window titled Add Package with Privileges will appear. In this window, you’ll see a list of possible package privileges that can be assigned. Select the checkbox beside each privilege you want to grant. In addition, for each privilege, you can use the Yes/No slider under Grantable to Others to allow the privilege to be granted to other users. Click the OK button located at the bottom right of the interface to continue.

You should now see the selected packages and the privileges you assigned listed in the Package Privileges tab.

To revoke a package privilege, click an assigned package and its assigned privilege from the list and then click the Remove Package button to revoke the privilege. To make the changes active, click the Save button or continue making other changes if necessary. Note that, once the Save button is clicked, you’ll be returned to the list of privileges and be required to click the Edit button again to make further changes.

To change assigned object privileges, while in edit mode, click an assigned object and its assigned privilege from the list and then click the Change Privileges button to open a new popup window titled Change Privileges of concatenated with the name of the package. A list of assigned and unassigned privileges for the package will appear. Select the relevant checkbox to grant the privilege or deselect the checkbox to revoke the privilege. Use the Yes/No slider to manage the grantable to others privilege. Click the OK button at the bottom right of the window to apply your changes. Again, to make the changes active, click the Save button or continue making other changes if necessary until you’re ready to activate all changes.

# 5.3.4 Granting and Revoking Privileges with the SAP HANA Web-Based Development Workbench

The SAP HANA Web-Based Development Workbench security manager, hosted within the XS engine, provides an interface to create users, create roles, or manage security. You can access SAP HANA Web-Based Development Workbench via a supported Internet browser. The following two URLs can be customized to match the details of your environment:

*   `http://sap-hana.myhost.com:8000/sap/hana/ide/security`
*   `http://<sap_hana_host>:80<instance_number>/sap/hana/ide/security`

In the second example, replace `<sap_hana_host>` with the host name of the SAP HANA system in your environment. Replace `<instance_number>` with the two-digit instance corresponding to your SAP HANA system.

For secure access, the following examples should help you construct the correct URL:

*   `https://<sap_hana_host>:43<instance_number>/sap/hana/ide/security`
*   `https://sap-hana.myhost.com:4300/sap/hana/ide/security`

Once you have access to the SAP HANA Web-Based Development Workbench, expand the Security node on the right side of the window. Expand Roles to reveal a list of roles. Click a role to open the management interface for the given role. With the selected Role window open, you can begin granting and revoking privileges. Just below the role name, you’ll see the Granted Roles, Part of Roles, System Privileges, Object Privileges, Analytic Privileges, Package Privileges, and Application Privileges (not visible in screenshot) tabs. [Figure 5.8](#05_003.html#f5.8) shows an example of this role interface where you can assign privileges to a role.

[![Layout of the Role Management Interface Where You Can Assign Privileges to a Role](bilderklein/klein05_008.png)](img-f5.8.html)

**Figure 5.8** Layout of the Role Management Interface Where You Can Assign Privileges to a Role

In the absence of the SAP HANA cockpit, you can use this GUI to manage security for standard catalog objects and `_SYS_REPO`-owned catalog objects that were created at design time.

While working in this interface, if any activation issues arise, warning messages will appear in the status pane at the bottom of the Role Editor window. The status pane has a dark background, and error messages will appear in red text. Errors are generated only during an attempt to activate or save changes.

## System Privileges

To grant or revoke system privileges within a role, locate the System Privileges tab. To add a system privilege, click the plus sign (`+`) to open the Find System Privileges tab. You can use the search box to filter the list based on the entered text. Select one or more privileges from the list and click OK to continue. Your selected system privileges will now be listed in the tab. To assign the Grantable to Other Users and Roles, select the privilege and locate the checkbox to the right in the Details for area to the right of each selected system privilege as needed. [Figure 5.8](#05_003.html#f5.8) also shows an example where system privileges have been granted to the role `TEST_ROLE`.

To revoke a system privilege, select the privilege from the list and click the red X. To save your changes, press `(Ctrl)+(S)`. Alternatively, click the save icon (floppy disk) at the top left to save and activate the privilege. Look for activation errors just below the privileges tab in the section with a dark background. Errors will be listed in red text. White text will indicate that the change was successful.

## Object Privileges

The fourth tab in the user role editor interface is called Object Privileges. You’ll use this tab to grant or revoke object privileges. To add an object privilege, click the plus sign (`+`) and search for the desired catalog objects. A search dialog will appear, allowing you to search for an object. Unlike in the SAP HANA cockpit, the SAP HANA Web-Based Development Workbench also provides additional search checkbox options based on the object type, which may help you pinpoint specific objects by type. Select the desired objects and click OK. A list of selected objects will appear in the tab, as shown in [Figure 5.9](#05_003.html#f5.9). To the right of each object is a list of applicable privileges that can be granted using checkboxes. Checked items will be granted and unchecked boxes will be revoked when you save the changes. The Grantable to Others option is also available using the Yes and No radio buttons.

To revoke individual privileges previously granted, select the object in the left pane and then deselect any existing privileges in the pane to the right. To revoke all privileges for an object privilege, select the object from the list and click the red X. This action will remove the object and revoke all currently granted privileges. To save your changes, press `(Ctrl)+(S)` or click the disk icon to save and activate the privilege. Look for activation errors just below the privileges tab in the section with a dark background. Errors will be listed in red text. White text will indicate that the change was successful.

[![Working with a Role’s Object Privileges in the SAP HANA Web-Based Development Workbench Security Manager](bilderklein/klein05_009.png)](img-f5.9.html)

**Figure 5.9** Working with a Role’s Object Privileges in the SAP HANA Web-Based Development Workbench Security Manager
