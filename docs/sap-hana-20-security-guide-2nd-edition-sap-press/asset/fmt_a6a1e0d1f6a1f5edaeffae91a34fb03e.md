
The ALTER USER syntax can also be used to unlock a user account that was disabled due to multiple failed logon attempts. The syntax to reset the number of invalid connection attempts and activate a user account is as follows:

```
ALTER USER JONATHAN RESET CONNECT ATTEMPTS;
```

To enable an account that was explicitly disabled by the administrator, use the following syntax:

```
ALTER USER JONATHAN ACTIVATE;
```

To disable SAML authentication for the user, use the following syntax:

```
ALTER USER JONATHAN DISABLE SAML;
```

To enable Kerberos and add a Kerberos identity, use the following syntax:

```
ALTER USER JONATHAN ADD IDENTITY 'testkerberosName' FOR KERBEROS;
ALTER USER JONATHAN ENABLE KERBEROS;
```

It’s sometimes necessary to modify a user account to prevent the system’s default settings from expiring passwords of a specific age. To prevent a user account’s password from expiring, use the following syntax:

```
ALTER USER JONATHAN DISABLE PASSWORD LIFETIME;
```

To limit the amount of system memory in gigabytes that an individual user account can consume with a given SQL statement, use the following syntax:

```
ALTER USER JONATHAN SET PARAMETER STATEMENT MEMORY LIMIT = 5; 
```

To disable an individual user’s memory restrictions, use the following syntax:

```
ALTER USER JONATHAN CLEAR PARAMETER STATEMENT MEMORY LIMIT;
```

### 4.2.2 Creating and Managing Users in the SAP HANA Cockpit

You can also create and manage user accounts in SAP HANA cockpit. Using the SAP HANA cockpit Home screen, locate an SAP HANA system in the Resource Directory. Connect to the desired tenant database or SYSTEMDB, which will take you to the System Overview window. Using the Filter by Area dropdown list, choose the Security option. Locate the User & Role Management tile and choose Manage Users. On the left side of the User Management window, click on the large plus icon (+) to create a new user. Choose between the Create User and Create Restricted User options. A new pane will appear on the right side of the window where you’ll add details about the user account. [Figure 4.3](#04_002.html#f4.3) shows an example of the pane that will appear when selecting the Create User option.

[![SAP HANA Cockpit User Creation and Edit Window](bilderklein/klein04_003.png)](img-f4.3.html)

**Figure 4.3** SAP HANA Cockpit User Creation and Edit Window

To specify the name of the user account, enter the desired name in the mandatory User Name field. If a User Group is required, select an existing user group. Enter an email address in the Email field if required. Specify a valid date and time using the Valid From and Valid To fields when required. Select the desired options for Creation of Objects in Own Schema, PUBLIC Role, and Disable ODBC/JDBC Access by choosing the Yes or No radio buttons beside each option.

Scroll down to reveal the Authorization Mode and Authentication sections, as shown in [Figure 4.4](#04_002.html#f4.4).

[![SAP HANA Cockpit User Authorization and Authentication Options](bilderklein/klein04_004.png)](img-f4.4.html)

**Figure 4.4** SAP HANA Cockpit User Authorization and Authentication Options

In the Authorization Mode section, choose between Local and LDAP. When set to Local, users will exclusively rely on local roles defined in SAP HANA. When set to LDAP, users can only have roles that are mapped to LDAP groups assigned to their account. Note that, with existing user accounts, switching between these options will revoke any previously granted LDAP or local roles.

In the Authentication section, you can enable or disable password authentication with the Authentication Mechanism and Password checkboxes. Once a selection is made, choose between the Local or LDAP modes. If the Local option is selected, enter the desired password in the Password field. Confirm the password in the Password Confirmation field. If the LDAP option is selected, note that a password is not required because it will be managed by the LDAP provider.

To define third-party authentication information, use the Kerberos, SAML, SAP Logon Ticket, X509, SAP Assertion Ticket, and JWT checkboxes. The Kerberos option also requires that you enter the case-sensitive External ID. For example, if Kerberos is based on Microsoft Active Directory, enter the SAMAccountName attribute into this field. For the SAML option, map external identities for each identity provider. Scrolling down further, you’ll also see additional identity options for the X.509 certificate identities and JWT.

Unlike legacy GUIs for SAP HANA, the SAP HANA cockpit user management GUI doesn’t provide options for granting or revoking roles and privileges. We’ll introduce you to these options in [Section 4.3.2](#04_003.html#h4.3.2). In [Chapter 4](#04_001.html#h4) and [Chapter 5](#05_001.html#h5), we’ll also provide more details about how to grant and revoke privileges.

Once you’ve defined the required options, scroll to the bottom and click the Save button. A new account will be activated if no errors arise.

When a user account is disabled or deactivated due to multiple failed logons, the user management interface in the SAP HANA cockpit will indicate that the account has been deactivated with the User Status field found in the list of users on the left. To activate the user, click the account in the list. The user management pane will appear in read-only mode. Click the Activate button on the top right side of the pane. Click the Activate button to activate the account. Conversely, to deactivate an account, click the Deactivate button.

### 4.2.3 Creating and Managing Users with the SAP HANA Web-Based Development Workbench

The SAP HANA Web-Based Development Workbench security manager, hosted within the XS engine, provides a GUI to create users, create roles, or manage security.

You can access the SAP HANA Web-Based Development Workbench via a supported Internet browser. The following URL can be customized to match the details of your environment:

`http://<sap_hana_host>:80<instance_number>/sap/hana/ide/security`

Replace `<sap_hana_host>` with the host name of the SAP HANA system in your environment and `<instance_number>` with the two-digit instance corresponding to your SAP HANA system (e.g., `http://sap-hana.myhost.com:8000/sap/hana/ide/security`).

For secure access, use `https://<sap_hana_host>:43<instance_number>/sap/hana/ide/security` (e.g., `https://sap-hana.myhost.com:4300/sap/hana/ide/security`).

To use the SAP HANA Web-Based Development Workbench security manager, a user account will first need one of the roles listed in [Table 4.1](#04_002.html#t4.1). Users only need one of the two roles to access the security manager.

| Role Name || Summary |

| --- | --- |

| `sap.hana.ide.roles::SecurityAdmin` || Within the SAP HANA Web-Based Development Workbench, the user can only access the security manager, which provides interfaces to create and manage users and roles. |

| --- | --- |

| `sap.hana.ide.roles::Developer` || This role grants a higher level of privileges for users that need full access to the SAP HANA Web-Based Development Workbench. This role grants access to the editor, catalog, and security interfaces and is considered the parent to the `sap.hana.ide.roles::SecurityAdmin` role. |

**Table 4.1** Roles Required to Use the Security Manager

###### Additional Privileges Needed to Use the Security Manager

Note that the roles listed in [Table 4.1](#04_002.html#t4.1) simply allow the granted user access to the GUI. To manage a security model, additional privileges and roles will need to be granted. For example, the user will need the system privilege USER ADMIN to create users and the system privilege ROLE ADMIN to create roles. To grant privileges to a user or role, the account accessing the security manager will also require privileges to grant the privileges to other users or roles.
