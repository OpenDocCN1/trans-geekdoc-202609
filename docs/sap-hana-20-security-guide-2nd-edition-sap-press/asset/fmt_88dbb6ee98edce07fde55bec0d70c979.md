
However, the developer creating the catalog view must have the `SELECT` privilege and the authority to give this privilege to other users. The developer won’t be able to activate the view unless he is the owner of all referenced objects or has the `SELECT` privilege and `Grantable to Others` privilege for each referenced object. In our experience, this concept is most often not understood and implemented poorly within most security models. If your organization plans to develop catalog database views to support access to data, make sure that your developers have the appropriate privileges to activate catalog views.

### Considerations for Catalog Stored Procedures and Functions

As discussed in [Chapter 2](#02_001.html#h2), you can choose between two security options when defining stored procedures or functions. You can establish the SQL security in definer or invoker mode.

In definer mode, the developer must have privileges to perform all SQL actions defined within the stored procedure or function. In addition, he must have the `Grantable to Others` privilege for each associated SQL privilege. In this way, the definer is effectively delegating those privileges to the user or role that’s been granted the `EXECUTE` privilege against the stored procedure or function. In most cases, this approach is the least restrictive way to manage access to the activities performed by the stored procedure or function.

In invoker mode, the user or role with `EXECUTE` privileges against the stored procedure or function must also have the appropriate privileges to support the defined actions against each referenced catalog object. For example, if the stored procedure adds data to a table, the user first would need the `EXECUTE` privilege for the stored procedure. Second, he would need the `INSERT` privilege against the referenced catalog table. In most cases, this approach is the most restrictive way to manage access to the activities performed by the stored procedure or function.

### Schemas, Tables, Procedures, and Views as Repository Objects

One of the most important concepts in SAP HANA security is the ability to understand the difference between catalog objects created using a SQL `CREATE` statement and catalog objects created using development artifacts within the SAP HANA development repository. Objects created within the SAP HANA repository are often called repository objects. The key differentiator between the two object types lies in the ownership of the objects, as we’ll discuss next.

When a user executes a `CREATE` SQL statement to define an object, he becomes the sole owner of the object. In most cases, he must then grant privileges to other users or roles for them to access the object he created. If the owner’s user account is deleted from the system, any objects he created or privileges he granted are also removed from the system. In addition, if an organization has multiple SAP HANA environments to support proper lifecycle management, these `CREATE` statements must be manually executed in each environment. These situations should be avoided when establishing a security model because the model should be able to be transported easily between SAP HANA environments.

When an object is created as a development artifact in the SAP HANA repository, the object isn’t owned by the developer. Instead, the object is owned by a special system account called `\_SYS\_REPO`. This account can’t be deleted from the system and exists in all SAP HANA systems. Therefore, if needed, you can easily transport the definition of catalog objects or a security model between two or more SAP HANA systems; it already exists in each environment and therefore can easily take ownership of these objects in each.

As discussed in [Chapter 3](#03_001.html#h3) and [Chapter 6](#06_001.html#h6), `\_SYS\_REPO` is responsible for activating repository-based roles, SAP HANA information views, and a few other security-sensitive objects. In an ideal security model, almost all catalog objects would be created as development artifacts specifically to ensure that `\_SYS\_REPO` is the owner of the object. When `\_SYS\_REPO` owns most objects, establishing, transporting, and maintaining a security model within an SAP HANA landscape is much easier.

## 8.2 Granting Object Privileges with SQL

In this section, we’ll review the different ways to grant object privileges to users or roles using SQL statements.

### 8.2.1 Securing Schemas with SQL

When you secure catalog objects, you’re essentially granting SQL privileges to users, roles, or both. In [Section 8.1](#08_001.html#h8.1), we outlined many of the privileges that you grant based on the type of catalog objects you’re working with. In this section, we’ll demonstrate the actual process of granting those privileges to users or roles using SQL statements.

In [Chapter 3](#03_001.html#h3), we outlined the process for creating catalog schemas. Once a schema is created, the owner of the schema will likely need to access the SAP HANA cockpit and grant other administrator users or security administration roles full privileges that are grantable to others on the schema. Once this process is complete, the security administrators will be able to establish a security model based on the schema and its objects. Keep in mind that the schema might also be associated with a service account and not an actual human user. For example, if you set up an SAP HANA service account to manage table replication between SAP ERP and SAP HANA using SAP Landscape Transformation Replication Server, then additional security settings in SAP HANA will need to be maintained. This approach assumes that users will interact with the replicated data. Once an SAP Landscape Transformation Replication Server mass data transfer configuration is established, you’ll need to log on to SAP HANA using the service account credentials and grant others access to the schema used by SAP Landscape Transformation Replication Server. Remember, only the owner of the schema can grant this access.

One way a user can grant or revoke privileges to its schema is by issuing SQL statements, which can be executed within the SQL console. The basic syntax of the SQL script that grants privileges is as follows:

```
GRANT <PRIVILEGE1, PRIVILEGE2,…> ON SCHEMA <SCHEMA> TO <SOME_USER or 
SOME_ROLE> WITH GRANT OPTION;
```

In this syntax, the items inside the angle brackets (`<>`) are variables that you can adjust based on the privilege, schema, user, or role. The `GRANT` command means that you’re allowing the action. A comma-separated array of privileges can also be specified after the `GRANT` statement. If only one privilege is required, you don’t need an array; simply specify a single privilege by name without commas. Include `ON SCHEMA` followed by the schema name to identify the schema catalog object. Then, include `TO` followed by a user or role to identify who is receiving the granted privileges.

For example, to grant the `ADMIN_SEC` user account the `SELECT` privilege on a user’s schema, log on as the user that owns the schema, access the SQL console, and execute the following statement (assuming that the account that owns the schema is named `TEST_USER` and that the schema name is the same):

```
GRANT SELECT on SCHEMA TEST_USER to ADMIN_SEC WITH GRANT OPTION;
```

Adding the `WITH GRANT OPTION` syntax is critical in this case because you need to grant the security administrator full access to a user’s schema. The user must include this statement to grant the security administrator the ability to grant the same privilege to other users or roles.
