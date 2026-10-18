
## Repository Privileges

### Granting and Revoking Repository Object Privileges

```
CALL "_SYS_REPO"."GRANT_PRIVILEGE_ON_ACTIVATED_CONTENT"('<OBJECT_PRIVILEGES>',
'<OBJECT_NAME>','<USER_NAME>');
CALL
"_SYS_REPO"."GRANT_PRIVILEGE_ON_ACTIVATED_CONTENT "('SELECT, EXECUTE', 
'"StagingMart"."e-corp.sales.tables::STG_CUSTOMERS"', 'JONATHAN');
```

Listing 4.4 Two Example SQL Statements Granting a Repository-Based Object’s Object Privileges to a Grantee

To revoke repository catalog object privileges, you’ll need to execute a stored procedure in the `_SYS_REPO` schema named `REVOKE_PRIVILEGE_ON_ACTIVATED_CONTENT`. This procedure has three input parameters, which are the same as those used in the previous procedure to grant the privileges. The SQL statements shown in Listing 4.5 call the stored procedure equipped to revoke catalog object privileges; the second statement provides an example specifically revoking catalog object privileges previously granted to the user account `JONATHAN`.

```
CALL 
"_SYS_REPO"."REVOKE_PRIVILEGE_ON_ACTIVATED_CONTENT "('<OBJECT_PRIVILEGES>',
'<SCHEMA_NAME>','<USER_NAME>');
CALL "_SYS_REPO"."REVOKE_PRIVILEGE_ON_ACTIVATED_CONTENT"('SELECT, EXECUTE' , 
'"StagingMart"."e-corp.sales.tables::STG_CUSTOMERS"' , 'JONATHAN');
```

Listing 4.5 Two Example SQL Statements Revoking a Repository-Based Object’s Object Privileges from a Grantee

### Structured Privileges

Structured privileges are a special type of object that forces the system to provide additional access restrictions against a column view or catalog view. In Chapter 3, we introduced analytic privileges, which are used with SAP HANA information views to provide data access to an activated information view. We’ll discuss analytic privileges in more detail in Chapter 10. Technically, analytic privileges are a type of structured privilege, but most GUIs refer to structured privileges as analytic privileges. Repository-based analytic privileges are owned and managed by the system account `_SYS_REPO`. However, structured privileges can be owned by any user with the required system privileges.

If a structured privilege is owned by a standard database user, then you can use the `GRANT STRUCTURED PRIVILEGE` SQL syntax to grant such privileges to a user account. To grant a structured privilege, you must be its owner because there is no `WITH ADMIN OPTION` to allow another user to grant this privilege. Note that this syntax will not work on repository-based analytic privileges. In the following example, replace the `<STRUCTURED_PRIVILEGE_NAME>` variable with the name of the structured privilege:

```
GRANT STRUCTURED PRIVILEGE <STRUCTURED_PRIVILEGE_NAME> TO <USER_NAME>;
```

As an example, we’ll walk through the process of creating a catalog view and a structured privilege and the process for granting the privilege to a user. Start by using the SQL statement shown in Listing 4.6 to create a standard catalog view.

```
CREATE VIEW "MySchema"."MYVIEW" ( "MYKEYCOLUMN",
     "STATE",
     "CITY",
     "POSTALCODE" ) AS select
     T0."MYKEYCOLUMN",
     T0."STATE",
     T0."CITY",
     T0."POSTALCODE" 
FROM "SYSTEM"."MYTABLENAME" T0
WITH STRUCTURED PRIVILEGE CHECK;
```

Listing 4.6 SQL Code to Create the MYTABLE View

You’ll then create a structured privilege referencing the view, which will apply a filter on the `STATE` column. The following SQL statements will create a structured privilege that will filter the `STATE` column to `TN`, then, after the privilege name, the `FOR SELECT` syntax is used to indicate that the privilege should be applied when querying the view:

```
CREATE STRUCTURED PRIVILEGE "MyStructuredPriv"     
FOR SELECT ON "MySchema"."MYVIEW" WHERE "STATE" = 'TN';
```

You’ll then grant the structured privilege to the user `JONATHAN`. Once granted, the user will only see value from the view where `"STATE" = 'TN'`:

```
GRANT STRUCTURED PRIVILEGE "MyStructuredPriv" TO JONATHAN;
```

To revoke the structured privilege, you’ll use the `REVOKE STRUCTURED PRIVILEGE` SQL syntax. The following SQL statements provide first a generic and then a specific example of the SQL syntax:

```
REVOKE STRUCTURED PRIVILEGE <STRUCTURED_PRIVILEGE_NAME> FROM <USER>;
REVOKE STRUCTURED PRIVILEGE "MyStructuredPriv" FROM JONATHAN;
```

### Remote Sources

To grant access to a remote source or a smart data access federated database connection, issue a SQL statement based on the following example:

```
GRANT <SOURCE_PRIVILEGE> ON REMOTE SOURCE <SOURCE_NAME> TO <USER>;
```

The variable `<SOURCE_PRIVILEGE>` can be replaced by a comma-separated array of privileges specific to remote-source objects. The `<SOURCE_NAME>` variable can be replaced by the name of the remote source.

To remove remote-source privileges, use the `REVOKE` SQL statement. The following SQL statement will remove the privileges specified in the `<SOURCE_PRIVILEGE>` variable array:

```
REVOKE <SOURCE_PRIVILEGE> ON REMOTE SOURCE <SOURCE_NAME> FROM <USER>;
```

### Repository Analytic Privileges

When you create a standard analytic privilege, that privilege is owned by the system user `_SYS_REPO`. Analytic privileges are a type of structured privilege, but you can’t use the standard `GRANT` and `REVOKE` SQL syntax to assign analytic privileges to a user. Instead, you must use a specific stored procedure to grant (and another specific stored procedure to revoke) analytic privileges for users.

To grant an analytic privilege to a user, you must execute the stored procedure `GRANT_ACTIVATED_ANALYTIC_PRIVILEGE` stored in the `_SYS_REPO` schema. To use this procedure, the security administrator must have the `EXECUTE` object privilege for the stored procedure. The procedure provides two input parameters: The first parameter contains the name of the analytic privilege, and the second input parameter contains the name of the user. The following SQL statements provide the syntax used to execute the stored procedure, and then a specific example:

```
CALL "_SYS_REPO"."GRANT_ACTIVATED_ANALYTICAL_PRIVILEGE"
('<ANALLYTIC_PRIVILEGE_NAME>','<USER_NAME>');
CALL "_SYS_REPO"."GRANT_ACTIVATED_ANALYTICAL_PRIVILEGE"
('"e-corp.sales.security/ap_sales_reporting_region"','JONATHAN');
```

To revoke an analytic privilege from a user, you must execute the stored procedure `REVOKE_ACTIVATED_ANALYTIC_PRIVILEGE` stored in the `_SYS_REPO` schema. This stored procedure uses the same two input parameters. The following SQL statements provide the syntax used to execute the stored procedure and a specific example:

```
CALL "_SYS_REPO"."REVOKE_ACTIVATED_ANALYTICAL_PRIVILEGE"
('<ANALLYTIC_PRIVILEGE_NAME>','<USER_NAME>');
CALL "_SYS_REPO"."REVOKE_ACTIVATED_ANALYTICAL_PRIVILEGE"
('"e-corp.sales.security/ap_sales_reporting_region"','JONATHAN');
```

### Application Privileges

When you create an application privilege, that application privilege is owned by the system user `_SYS_REPO`. To grant or revoke application privileges, you must use a specific stored procedure. The following SQL statements demonstrate the syntax used to grant an application privilege and a specific example:

```
CALL "_SYS_REPO"."GRANT_APPLICATION_PRIVILEGE"
('<APPLICATION_PRIVILEGE_NAME>','<USER_NAME>');
CALL "_SYS_REPO"."GRANT_APPLICATION_PRIVILEGE"('"sap.hana.admin::Administrator"','JONATHAN');
```

The next statements provide the syntax used to revoke an application privilege and a specific example:

```
CALL "_SYS_REPO"."REVOKE_APPLICATION_PRIVILEGE"
('<APPLICATION_PRIVILEGE_NAME>','<USER_NAME>');
CALL "_SYS_REPO"."REVOKE_APPLICATION_PRIVILEGE"('"sap.hana.admin::Administrator"','DFT');
```

### Package Privileges

To grant access to a package in the SAP HANA repository, issue a SQL statement based on the following syntax; the second statement provides a specific example:

```
GRANT <PACKAGE_PRIVILEGE> ON <"package.subpackage"> TO <USER> WITH GRANT OPTION;
GRANT REPO.READ, REPO.EDIT_NATIVE_OBJECTS ON "e-corp" TO JONATHAN WITH GRANT OPTION;
```
