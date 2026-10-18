
The second category involves roles based on functional activities. For example, developers could be granted privileges to work in the SAP HANA package repository. A role named `ECORP_INFORMATION_MODELER` might be created for users that will create information views. Security administrators would be granted privileges to manage security. For example, the `ECORP_SECURITY_ADMIN` role would be created for individuals that plan to manage security. Finally, the `BACKUP_MONITOR` and `BACKUP_ADMIN` roles could be created and granted to individuals that manage backups.

These categories provide a nice delineation, but some overlap is likely between the types of privileges you grant within either type of role. However, you should still try to avoid granting the same privileges to multiple roles. One easy way to manage this separation is by granting roles to roles. SAP HANA supports granting privileges to roles and granting existing roles to other roles. Nesting roles within roles, when implemented properly, can greatly reduce maintenance on a security model. For example, you can grant the role `DM_READ_ONLY` to the `ECORP_INFORMATION_MODELER` role. In this way, you can ensure that developers also have SELECT access to the data mart schema even if you don’t explicitly grant those privileges in the `ECORP_INFORMATION_MODELER` role, ensuring that the information modeler has a basic level of access to the data mart schema.

[Figure 5.3](#05_003.html#f5.3) shows how you can nest roles to simplify the security model design.

[![Child Roles Nested within a Parent Role](bilderklein/klein05_003.png)](img-f5.3.html)

**Figure 5.3** Child Roles Nested within a Parent Role

The `ECORP_INFORMATION_MODELER` parent role has been granted the `DM_READ_ONLY`, `STG_READ_ONLY`, and `PACKAGE_ECORP_ROOT` child roles to provide access to the schemas and packages used by the information modeler. [Figure 5.3](#05_003.html#f5.3) only shows a few example privileges granted to the roles, shown to the right of each role name. In a true security model, you’d expect each role to be granted several different privileges.

### 5.3.2 Granting and Revoking Privileges with SQL

Using the SQL console and SQL statements, you can both grant privileges to and revoke privileges from roles. When granting privileges to specific objects, you’ll need to first recognize the object type. Specifically, you’ll need to use a different syntax for repository-based objects than for standard catalog objects. Repository-based objects are owned by the `_SYS_REPO` system account. With this account, you have no way to delegate grant and revoke privileges to other users in the system. For example, you can’t log on as `_SYS_REPO` and grant SELECT to another user while including the `WITH ADMIN OPTION` or `WITH GRANT OPTION` statement options. Because of this limitation, you must use a series of system-delivered stored procedures to grant privileges for repository-based objects owned by `_SYS_REPO`. These stored procedures are activated in the `_SYS_REPO` schema and can be called directly, assuming you have the `EXECUTE` privilege for the procedures. Standard catalog objects can be granted or revoked using the standard SQL `GRANT` or `REVOKE` statements. Let’s look at a series of SQL statements used to grant privileges based on the object and privilege type.

#### System Privileges

You can grant system privileges to roles using the `GRANT` SQL syntax. The following three SQL statements are separated by concluding semicolons:

```
GRANT <SYSTEM_PRIVILEGE> TO <ROLENAME>;
GRANT <SYSTEM_PRIVILEGE> TO <ROLENAME> WITH ADMIN OPTION;
GRANT DATA ADMIN, EXPORT, IMPORT TO ROLE_SEC_ADMIN WITH ADMIN OPTION;
```

The first statement provides the general syntax, with variables indicated by text within angle brackets (`<>`). The variables must be replaced with items unique to your environment. The `<SYSTEM_PRIVILEGES>` variable can be replaced with a comma-separated list of system privileges, as indicated in the third SQL example. The `<ROLENAME>` variable will be replaced with the name of an activated role within the system.

The second SQL statement includes the `WITH ADMIN OPTION` at the end of the statement. This option allows the grantee of the role to subsequently grant the same privilege to another user or role. This capability is typically reserved for user accounts or roles that manage security models. The final SQL statement provides a full example in which you’ll grant system privileges to the role `ROLE_SEC_ADMIN`. This statement includes the `WITH ADMIN OPTION`, which allows the grantee to grant the same privileges to other users or roles.

You can also revoke system privileges using the `REVOKE` SQL syntax, as follows:

```
REVOKE <SYSTEM_PRIVILEGE> FROM <ROLENAME>;
REVOKE DATA ADMIN, EXPORT, IMPORT FROM ROLE_SEC_ADMIN;
```

The first statement provides the general syntax, and the second SQL statement provides a full example in which the listed system privileges are removed from the role `ROLE_SEC_ADMIN`.

###### Note

As we continue through this section, the same rules will apply to the each of the examples: The first and/or second example is a generic template that contains variables within angle brackets that need to be replaced with items unique to your environment, and the final SQL statement will provide a full example.

#### Catalog Schema Privileges

If a schema is owned by a standard database user, you can use the syntax shown in [Listing 5.1](#05_003.html#l5.1) to grant one or more privileges to a role.

```
GRANT <SCHEMA_PRIVILEGE> ON SCHEMA <SCHEMA_NAME> TO <ROLENAME>;
GRANT <SCHEMA_PRIVILEGE> ON SCHEMA <SCHEMA_NAME> TO <ROLENAME> WITH GRANT OPTION;
GRANT SELECT, EXECUTE ON SCHEMA "MySchema" TO MYSCHEMA_READONLY_ACCESS;
```

**Listing 5.1** Three Example SQL Statements Granting Privileges to a Role

The `<SCHEMA_PRIVILEGES>` variable can be replaced with a comma-separated list of schema object privileges, as indicated in the example.

To remove the privileges, use the following syntax:

```
REVOKE <SCHEMA_PRIVILEGE> ON SCHEMA <SCHEMA_NAME> FROM <ROLENAME>;
REVOKE SELECT, EXECUTE ON SCHEMA "MySchema" FROM MYSCHEMA_READONLY_ACCESS;
```

Note that `GRANT` and `REVOKE` statements won’t work on repository-based schemas, which are owned by the system account `_SYS_REPO` and must be granted using a special stored procedure. In the next section, we’ll provide example SQL statements for repository-based schemas.

#### Repository Schema Privileges

When a schema is created in the SAP HANA development repository, that schema is owned by the system user `_SYS_REPO`; these schemas are repository schemas. In these cases, you can’t use the standard `GRANT` and `REVOKE` SQL syntax to manage permissions for a given role. Instead, you must use a specific stored procedure to grant (and another to revoke) repository schema privileges.

To grant repository schema privileges, you’ll need to execute a stored procedure in the `_SYS_REPO` schema named `GRANT_SCHEMA_PRIVILEGE_ON_ACTIVATED_CONTENT`. To use this procedure, the security administrator must have the `EXECUTE` object privilege on the stored procedure. This procedure has three input parameters: The first parameter can accommodate a comma-separated array of schema privileges, the second parameter can accommodate a single schema name, and the third parameter can accommodate a role name.

In the following example, you’ll need to replace `<OBJECT_PRIVILEGES>` with one or more schema privileges; replace `<SCHEMA_NAME>` with the case-sensitive name of the schema, enclosed in double quotes if lowercase or mixed case; and replace and `<ROLENAME>` with the name of a role defined in the SAP HANA system. To execute a stored procedure, use the SQL `CALL` function followed by the name of the stored procedure, as in the following statement:

```
CALL "_SYS_REPO"."GRANT_SCHEMA_PRIVILEGE_ON_ACTIVATED_CONTENT"
('<OBJECT_PRIVILEGES>','<SCHEMA_NAME>','<ROLENAME>');
```
