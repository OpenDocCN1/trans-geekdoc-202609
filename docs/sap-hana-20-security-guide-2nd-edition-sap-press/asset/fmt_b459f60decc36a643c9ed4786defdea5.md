
The first statement provides a generic template with variables. The variables are indicated by text within angle brackets (e.g., `<USER>`). The variables will need to be replaced with items unique to your environment. The `<SYSTEM_PRIVILEGES>` variable can be replaced with a comma-separated list of system privileges, as indicated in the third example. The second SQL statement includes the `WITH ADMIN OPTION` at the end of the statement. This option allows the grantee to subsequently grant the same privilege to another user and is typically reserved for user accounts or roles that manage security models. The final statement provides a full example in which you’ll grant three different system privileges to the user `JONATHAN`. This statement includes the `WITH ADMIN OPTION`, which allows the account `JONATHAN` to grant the same privileges to other users or roles.

You can also revoke system privileges using the `REVOKE` SQL syntax. The following statements demonstrate the `REVOKE` syntax:

```
REVOKE <SYSTEM_PRIVILEGE> FROM <USER>;    
REVOKE DATA ADMIN, EXPORT, IMPORT FROM JONATHAN;
```

The first statement provides a generic template with variables. The variables are indicated by text within angle brackets (e.g., `<USER>`). The variables will need to be replaced with items unique to your environment. The `<SYSTEM_PRIVILEGES>` variable can be replaced with a comma-separated list of system privileges, as indicated in the second example. The second statement provides a full example in which the listed system privileges are removed from the user account `JONATHAN`.

## Catalog Schema Privileges

If a schema is owned by a standard database user, you can use one of the following SQL statements to grant one or more privileges to a user account:

```
GRANT <SCHEMA_PRIVILEGE> ON SCHEMA <SCHEMA_NAME> TO <USER>;    
GRANT <SCHEMA_PRIVILEGE> ON SCHEMA <SCHEMA_NAME> TO <USER> WITH GRANT OPTION;    
GRANT SELECT, EXECUTE, DROP ON SCHEMA "MySchema" TO JONATHAN;
```

The `<SCHEMA_PRIVILEGES>` variable can be replaced with a comma-separated list of schema object privileges, as indicated in the third statement. When included, the `WITH GRANT OPTION` clause at the end of the statement allows the user to subsequently grant the same privilege to another user.

To remove the privileges, use the following syntax:

```
REVOKE <SCHEMA_PRIVILEGE> ON SCHEMA <SCHEMA_NAME> FROM <USER>;
REVOKE SELECT, EXECUTE, DROP ON SCHEMA "MySchema" FROM JONATHAN;
```

The `<SCHEMA_PRIVILEGES>` variable can be replaced with a comma-separated list of schema object privileges, as indicated in the second statement.

Note that `GRANT` and `REVOKE` statements won’t work on repository-based schemas. Such schemas are owned by the system account `_SYS_REPO` and must be granted using a special stored procedure. In the next section, we’ll provide example SQL statements for such cases.

## Repository Schema Privileges

When a schema is created in the SAP HANA development repository, that schema will be owned by the system user `_SYS_REPO`. We call these types of schemas repository schemas. In such cases, you can’t use the standard `GRANT` and `REVOKE` SQL syntax to manage permissions for a given user account. Instead, you must use a specific stored procedure to grant and another to revoke repository schema privileges.

To grant repository schema privileges, you’ll need to execute a stored procedure in the `_SYS_REPO` schema named `GRANT_SCHEMA_PRIVILEGE_ON_ACTIVATED_CONTENT`. To use this procedure, the security administrator must have the object privilege `EXECUTE` on the stored procedure. This procedure has three input parameters. The first parameter can accommodate a comma-separated array of schema privileges. The second parameter can accommodate a single schema name. The third parameter can accommodate a user name or role name.

In the following example, you’ll need to replace the variable `<OBJECT_PRIVILEGES>` with one or more schema privileges; replace the variable `<SCHEMA_NAME>` with the case-sensitive name of our schema (if the name is lowercase or mixed-case, use double quotes around the name); and replace `<USER_NAME>` with the name of a user defined in the SAP HANA system:

```
CALL "_SYS_REPO"."GRANT_SCHEMA_PRIVILEGE_ON_ACTIVATED_CONTENT"
('<OBJECT_PRIVILEGES>','<SCHEMA_NAME>','<USER_NAME>');
```

The following SQL statement represents a complete example based on objects in a demo environment; multiple schema privileges are granted to the user `JONATHAN` against the schema `"MySchema"`:

```
CALL "_SYS_REPO"."GRANT_SCHEMA_PRIVILEGE_ON_ACTIVATED_CONTENT"
('SELECT, EXECUTE, UPDATE, CREATE ANY' ,'"MySchema"', 'JONATHAN');
```

To revoke repository schema privileges, you’ll need to execute a stored procedure in the `_SYS_REPO` schema named `REVOKE_SCHEMA_PRIVILEGE_ON_ACTIVATED_CONTENT`. This procedure has three input parameters, which are identical to those the preceding procedure used to grant privileges. The following SQL statements can be used to call the stored procedure equipped to revoke repository schema privileges; the second statement provides an example revoking privileges previously granted to the user account `JONATHAN`:

```
CALL "_SYS_REPO"."REVOKE_SCHEMA_PRIVILEGE_ON_ACTIVATED_CONTENT"
('<OBJECT_PRIVILEGES>','<SCHEMA_NAME>','<USER_NAME>');
CALL "_SYS_REPO"."REVOKE_SCHEMA_PRIVILEGE_ON_ACTIVATED_CONTENT"
('SELECT, EXECUTE', '"MySchema"', 'JONATHAN');
```

## Catalog Object Privileges

If a catalog object is owned by a standard database user, you can use one of the following SQL statements to grant catalog object privileges to a user or role. The `<OBJECT_PRIVILEGE>` variable can be replaced with a comma-separated array of privileges. The `WITH GRANT OPTION`, when specified, allows the grantee the ability to subsequently grant the same privileges to other users in the system, as shown in [Listing 4.3](#04_003.html#l4.3).

```
GRANT <OBJECT_PRIVILEGE> ON <OBJECT_NAME> TO <USER>;    
GRANT <OBJECT_PRIVILEGE> ON <OBJECT_NAME> TO <USER> WITH GRANT OPTION;
GRANT SELECT, INSERT, UPDATE, DELETE ON “MySchema”.”MyTable” TO JONATHAN WITH GRANT OPTION;
```

**Listing 4.3** Three Example SQL Statements Granting Object Privileges to a Grantee

To revoke these privileges, you can use one of the following statements:

```
REVOKE <OBJECT_PRIVILEGE> ON <OBJECT_NAME> FROM <USER>;    
REVOKE SELECT, INSERT, UPDATE, DELETE ON “MySchema”.”MyTable” FROM JONATHAN;
```

## Repository Object Privileges

When a catalog object is created in the SAP HANA development repository, that catalog object will be owned by the system user `_SYS_REPO`. We call these types of objects repository catalog objects. In these cases, you can’t use the standard `GRANT` and `REVOKE` SQL syntax to manage permissions for a given user account. Instead, you must use a specific stored procedure to grant (and another specific stored procedure to revoke) repository catalog object privileges.

To grant repository catalog object privileges, you’ll need to execute a stored procedure in the `_SYS_REPO` schema named `GRANT_PRIVILEGE_ON_ACTIVATED_CONTENT`. To use this procedure, the security administrator must have the `EXECUTE` object privilege for the stored procedure. This procedure has three input parameters: The first parameter can accommodate a comma-separated array of schema privileges, the second parameter can accommodate a single schema name, and the third parameter can accommodate a user name or role name. As shown in [Listing 4.4](#04_003.html#l4.4), you’ll need to replace the `<OBJECT_PRIVILEGES>` variable with one or more schema privileges and replace the `<OBJECT_NAME>` variable with the case-sensitive and fully qualified name of our catalog object. Additionally, if the name is lowercase or mixed case, include double quotes around the schema and catalog object name and replace `<USER_NAME>` with the name of a user defined in the SAP HANA system.
