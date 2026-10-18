
You can also use SQL statements to define SAP HANA audit policies. Using SQL isn’t as easy, but this scripting option can help you apply a consistent audit policy throughout your SAP HANA landscape. SQL script can be executed with the SQL console found in most management tools in SAP HANA. We’ve found that the GUI-based tools are at inconsistent times and don’t always support all audit policy options, but the SQL options support all possible audit configurations.

When creating an audit policy, use the generic SQL syntax shown in [Listing 15.2](#15_003.html#l15.2).

```
CREATE AUDIT POLICY <POLICY NAME> 
AUDITING <STATUS> <ACTIONS>
ON <CATALOG OBJECTS>
FOR | EXCEP FOR <USER LIST>
LEVEL <LEVEL> 
TRAIL TYPE <TRAIL>;
```

**Listing 15.2**    SQL Template for Defining an Audit Policy

The `<POLICY NAME>` variable will be replaced with the name of the policy. The `<STATUS>` variable should be replaced with `SUCCESSFUL`, `UNSUCCESSFUL`, or `ALL`. The `<ACTIONS>` variable should be replaced with the syntax specific to the action being audited; for example, you can specify one or more actions, such as `CREATE USER`, `ALTER USER`, or `ALTER ROLE`.

###### Note

The syntax of all possible actions is quite extensive and can be found in the SAP HANA SQL and System View Reference Guide, in the “CREATE AUDIT POLICY Statement reference” section.

You can download the guide from [http://s-prs.co/v498219](http://s-prs.co/v498219).

The `ON` clause and the `<CATALOG OBJECTS>` variable are required for data manipulation actions. The `<CATALOG OBJECTS>` variable should be replaced with the fully qualified name of the catalog object.

The `<USER LIST>` variable can contain a comma-separated list of user accounts in the system. The `FOR` and `EXCEPT FOR` syntax is optional for most audit actions. The `<LEVEL>` variable can be replaced with `EMERGENCY`, `ALERT`, `CRITICAL`, `WARNING`, or `INFO`. The `<TRAIL>` variable can be replaced with `TABLE`, `SYSLOG`, or `CSV`.

To better understand the SQL syntax, let’s review a few complete SQL examples. To audit the management of standard roles, you can create an audit policy titled `MANAGE ROLE` with the following code:

```
CREATE AUDIT POLICY "MANAGE ROLE" 
AUDITING ALL CREATE ROLE, ALTER ROLE, DROP ROLE
LEVEL INFO;
```

To audit the management of user accounts, you can create an audit policy titled `MANAGE USER` with the following code:

```
CREATE AUDIT POLICY "MANAGE USER" 
AUDITING ALL CREATE USER, ALTER USER, DROP USER
LEVEL INFO;
```

To monitor instances in which the stored procedures in the `_SYS_REPO` schema are executed, you can create an audit policy using the SQL code shown in [Listing 15.3](#15_003.html#l15.3).

```
CREATE AUDIT POLICY "GRANT OR REVOKE REPOSITORY OBJECTS" 
AUDITING ALL 
EXECUTE ON 
"_SYS_REPO"."*"
LEVEL INFO;
```

**Listing 15.3**    Creating a Policy Named GRANT OR REVOKE REPOSITORY OBJECTS

To monitor all unsuccessful actions for all users except system account users, you can create a policy using the SQL code shown in [Listing 15.4](#15_003.html#l15.4).

```
CREATE AUDIT POLICY "ALL ACTIONS" 
AUDITING UNSUCCESSFUL ACTIONS 
EXCEPT FOR 
_SYS_DI, _SYS_AFL, _SYS_XB, _SYS_WORKLOAD_REPLAY, 
_SYS_TASK, _SYS_STATISTICS, _SYS_SQL_ANALYZER, 
_SYS_REPO, _SYS_ES, _SYS_EPM, _SYS_DI_TO, _SYS_DI_SU, 
_SYS_DI_SEARCH_CATALOG, _SYS_DI_CDS_CATALOG, _SYS_DI_CATALOG, 
_SYS_DI_BI_CATALOG 
LEVEL INFO;
```

**Listing 15.4**    Creating a Policy Named ALL ACTIONS

When an audit policy is created using SQL, the audit policy disabled by default. To activate the policy, you’ll need to issue an `ALTER AUDIT POLICY` SQL statement. For example, you can issue the following SQL statement to enable an audit policy named `ALL ACTIONS`:

```
ALTER AUDIT POLICY "ALL ACTIONS" ENABLE;
```

To disable an audit policy, you can issue the following SQL statement:

```
ALTER AUDIT POLICY "ALL ACTIONS" DISABLE;
```

To delete an audit policy, you must use a `DROP AUDIT POLICY` SQL statement. For example, you can delete the `ALL ACTIONS` policy as follows:

```
DROP AUDIT POLICY "ALL ACTIONS";
```

###### SAP HANA SQL and System View Reference Guide

The complete syntax used to drop and alter audit policies can be found online in the SAP HANA SQL and System View Reference Guide. Look for the “ALTER AUDIT POLICY Statement (Access Control)” and “DROP AUDIT POLICY Statement (Access Control) sections.

The complete syntax used to create audit policies can be also be found in this guide. Look for the “CREATE AUDIT POLICY Statement (Access Control)” section.

Using SQL to define and manage audit policies is helpful for applying a consistent audit policy through the SAP HANA landscape. In the next section, we’ll briefly review how audit policies can be created in the SAP HANA cockpit.

### 15.3.4 Creating Policies with the SAP HANA Cockpit

The SAP HANA cockpit provides a GUI interface where you can manage auditing in an SAP HANA database. To access the security manager, log on to your SAP HANA cockpit and connect to the desired database. Click the Auditing tile. Within this tile, click the Auditing header to access the Auditing interface.

In the Auditing interface, look for the Audit Policies tab, as shown in [Figure 15.6](#15_003.html#f15.6).

To define a new audit policy, click the Create Audit Policy link located above the list of defined audit policies. A new interface will appear with a two-step option that will eventually morph into a four-step process. In the first step, `1. Name`, enter the name of the audit policy in the provided file, and a new button labeled `Step 2` will appear. Click the `Step 2` button to proceed to the next step.

[![Audit Policy Area in the SAP HANA Cockpit](bilderklein/klein15_006.png)](img-f15.6.html) 

**Figure 15.6**    Audit Policy Area in the SAP HANA Cockpit

The next step, `2. Audited Actions and Action Status`, will appear, as shown in [Figure 15.7](#15_003.html#f15.7). On this page, you can configure the Audited Action Status and the specific audit action by category for the policy. Notice that you can search for a category or action using the Search box located over the listed audit events. Once an action is selected, the `Step 3` button will appear. Click this button to proceed to the next step.

[![Configuring the Audit Action Status and Audit Policy Action within the SAP HANA Cockpit](bilderklein/klein15_007.png)](img-f15.7.html) 

**Figure 15.7**    Configuring the Audit Action Status and Audit Policy Action within the SAP HANA Cockpit

The next step, `3. Audited Users`, will appear, as shown in [Figure 15.8](#15_003.html#f15.8). Select an option for the under Select the users to be audited by the policy section. If you need to audit a specific user or several users, search for the user in the provided list and select the checkbox for each user to be audited. Click the `Step 4` button below the list to proceed.

[![Configuring Audit Policy Target Users within the SAP HANA Cockpit](bilderklein/klein15_008.png)](img-f15.8.html) 

**Figure 15.8**    Configuring Audit Policy Target Users within the SAP HANA Cockpit

The next step, `4. Audit Trail`, will appear, as shown in [Figure 15.9](#15_003.html#f15.9). In this step, you’ll configure the Audit Level setting for the policy.

[![Configuring the Audit Policy Audit Trail in the SAP HANA Cockpit](bilderklein/klein15_009.png)](img-f15.9.html) 

**Figure 15.9**    Configuring the Audit Policy Audit Trail in the SAP HANA Cockpit

For a system database, you can configure one or more audit trail targets. For a tenant database, you can only choose the default trail target configured for the database. Click the `Step 5` button to continue.

The final step, `5. Policy Status`, allows you to choose to Enable or Disable the policy when saving, as shown in [Figure 15.10](#15_003.html#f15.10). Click the `Review` button to go to a summary screen and review each individual setting and then click the `Save` button at the bottom once you’re ready to activate the policy.
