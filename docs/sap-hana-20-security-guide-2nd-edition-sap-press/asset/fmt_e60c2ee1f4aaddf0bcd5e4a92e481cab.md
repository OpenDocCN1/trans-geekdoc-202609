
When defining system privileges in design-time repository-based role scripts, you must start each line with `system privilege:`. After the colon, provide a comma-separated list of system privileges. At the end of the list, include a semicolon to finish the line. If you don’t want to include a comma-separated list, you can explicitly list each privilege on its own line, ensuring that each line begins with `system privilege:`.

The following snippets of code show the definition of system privileges within a repository role script. The first line includes two privileges, and the remaining two lines include only a single system privilege each:

```
system privilege: AGENT ADMIN, AUDIT ADMIN;    
system privilege: AUDIT OPERATOR;    
system privilege: CREATE REMOTE SOURCE;
```

Notice how you can reuse the `system privilege:` expression multiple times within the script. You can also consolidate all these instances into a single line in which each privilege is separated from the next with a comma. Note that the `_SYS_REPO` account has been granted all system privileges by default and can grant also all system privileges to other users or roles by default.

## 6.3.2 Schema Privileges

Schema privileges can be granted in two ways. First, you can grant schema privileges to any runtime catalog schemas active in the system. In this instance, you can reference a schema regardless of the method used to create it. Schema privileges can also be granted to design-time schema objects. In this instance, you can only reference schemas created within the repository.

### Runtime Schemas

When defining runtime catalog schema privileges within design-time repository-based role scripts, you must start each line with `catalog schema`. Following this term, include the name of the schema followed by a colon. You can also include a comma-separated list of schemas if you want them all to share the same privileges. After the colon, include a comma-separated list of schema privileges. At the end of the list, include a semicolon to finish the line.

The following snippets of code show the definition of catalog schema privileges within a repository role script. The first line grants `EXECUTE` and `SELECT` on the `_SYS_BIC` schema. The second line grants several privileges for the `MySchema` schema. The third line shows the use of multiple schemas in the same line:

```
catalog schema "_SYS_BIC": EXECUTE, SELECT;    
catalog schema "MySchema": CREATE ANY, DROP, ALTER, UPDATE;    
catalog schema "_SYS_REPO", "_SYS_BIC": SELECT;
```

Note also that the `_SYS_REPO` system account must have full privileges for the listed schemas or must own the schemas before such privileges can be activated within the definition of a repository role.

### Design-Time Schemas

In addition to referencing runtime catalog objects, you can also reference design-time schemas. Referencing a design-time schema is only possible if the schema itself is a repository object. In most cases, we recommend that you reference the design-time version of a schema because creating a dependency chain that can be identified can be useful during lifecycle management. The privileges will be granted on the runtime version of the object once all referenced objects are activated.

When defining repository schema privileges, you must start each line with `schema`. This term is only applicable for design-time schema objects. Following this term, include the name of the repository schema file. The name of the file will need to include the package hierarchy and a colon preceding the file name. You can specify multiple schema files in the list as well. The following example includes the fully qualified name of a design-time schema object:

```
Security.Schemas:SalesMart.hdbschema
```

After the schema file name, include a colon, then a comma-separated list of schema privileges. At the end of the list, include a semicolon to finish the line. [Listing 6.3](#06_003.html#l6.3) shows two complete lines that grant the listed schema privileges. The first line references a single schema file, and the second references multiple schema files within the same line.

```
schema Security.Schemas:SalesMart.hdbschema: SELECT, EXECUTE;
schema 
  Security.Schemas:SalesMart.hdbschema,
  Security.Schemas:MySchema.hdbschema: 
  SELECT; 
```

**Listing 6.3** Repository Role Script Granting Schema Privileges

In summary, you’ll use different syntaxes to program runtime schema objects and design-time schema objects.

## 6.3.3 Object Privileges

Object privileges can be granted in two ways. First, you can grant object privileges to any runtime catalog object, which works for both standard catalog objects and activated repository objects. Object privileges can also be granted to design-time objects listed in the repository. In this instance, you can only reference objects created within the repository. The privileges assigned to the design-time object will also be granted to the runtime version of the same object.

### Runtime Objects

When defining runtime object privileges in repository role scripts, you must start each line with `catalog sql object`. Following this term, include the fully qualified name of the catalog object, followed by a colon. You can also specify a comma-separated list of catalog objects if you want them to all have the same privileges. After the colon, include a comma-separated list of object privileges. At the end of the list, include a semicolon to finish the line. Note that the `_SYS_REPO` system account must have full privileges for the object or own it before such privileges can be included within the definition of a repository role.

[Listing 6.4](#06_003.html#l6.4) shows the definition of catalog object privileges within a repository role script. The first line references a single catalog object. The second line references two different catalog objects, each granted the listed privilege.

```
catalog sql object "MySchema"."TestTableTwo": SELECT, ALTER, DROP;
catalog sql object 
  "MySchema"."DIM_CUSTOMER", "MySchema"."DIM_PRODUCT": 
  SELECT, DELETE, ALTER;
```

**Listing 6.4** Repository Role Script Granting Runtime Catalog Object Privileges

We recommend that you only reference catalog objects that exist exclusively in runtime when using this syntax—that is, objects created using the SQL `CREATE` statement. Instead, you should use the design-time syntax for any repository-based catalog objects.

### Design-Time Objects

In addition to referencing runtime catalog objects, you can also reference design-time catalog objects. Referencing design-time objects is only possible if the object itself is a repository object. In most cases, we recommend that you reference the design-time version of an object because creating a dependency chain that can be identified can be useful during lifecycle management.

To reference design-time repository objects, you’ll need to use a different syntax. The syntax must start each line with `sql object`. In effect, you’re just removing the term `catalog` from the statement used when referencing runtime objects. Following this term, include the package and object name of the design-time object. You’ll separate the package name and object name with two colons. Unlike schemas, you don’t need to include the file extension in the fully qualified name. For example, to reference repository table `STG_CUSTOMER` stored in the `e-corp.sales.table` package, you’d use the following repository table syntax:

```
e-corp.sales.tables::STG_CUSTOMERS
```
