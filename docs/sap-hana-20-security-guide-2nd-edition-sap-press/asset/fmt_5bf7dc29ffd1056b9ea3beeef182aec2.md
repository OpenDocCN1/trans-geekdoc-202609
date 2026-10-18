
Although a stored procedure is not required, the use of a catalog table to store the mappings between user accounts and filter values is required. The structure of this table is different from that of the dynamic SQL-based analytic privileges, which requires the mapping of filter conditions to users. In fact, the structure is similar to the structure required to support dynamic XML-based analytic privileges. [Table 10.3](#10_006.html#t10.3) provides an example of the structure and data found in such a table.

| `USER_NAME` || `FILTER_VALUE` |

| --- | --- |

| `JHARRIS01` || `1000` |

| --- | --- |

| `TTIM03` || `2000` |

| --- | --- |

| `WTRAN05` || `2000` |

| --- | --- |

| `WTRAN05` || `3000` |

**Table 10.3**    Example Mapping Used to Facilitate Dynamic Expression-Based SQL Analytic Privileges

The `USER_NAME` column must contain values that match user accounts defined in the SAP HANA system. The `FILTER_VALUE` column must contain individual values. This table will become the source of your subqueries defined in the SQL editor.

Based on our testing, the SQL editor supports a variety of different SQL expressions. The supported syntax seems to match anything that can be used in a SQL statement WHERE clause. However, some limitations may exist that we were unable to identify during testing and validation.

In the following statement, you can define a static filter condition. Assume that the information view has an attribute column named `CUSTOMERKEY`. You’ll use the `IN` clause and a static string array of values, as in the following example:

```
("CUSTOMERKEY" in (1000,2000,3000,4000,5000))
```

In the following statement, you can reference two different columns in the expression. Assume that all referenced information views have attribute columns with names `CUSTOMERKEY` and `PLANT`. You’ll use two different operators in the expression—an `IN` operator for `CUSTOMERKEY` and an `=` operator for `PLANT`:

```
("CUSTOMERKEY" in (1000,2000,3000,4000,5000)) and ("PLANT" = 1000)
```

As shown in [Listing 10.3](#10_006.html#l10.3), you can reference two different columns in the expressions. Assume that all referenced information views have attribute columns with names `CUSTOMERKEY` and `PLANT`. However, as opposed to the static list of filter values, you’ll use a subquery to look up filter values from two different catalog tables. You’ll also use the `SESSION_USER` system variable to dynamically reference the user account column `USER_NAME` within the table.

```
 ("CUSTOMERKEY" in (SELECT DISTINCT "FILTER_VALUE" FROM "SECURITY".
"RLS_CUSTOMER_ACCESS" WHERE USER_NAME = SESSION_USER))
AND 
("PLANT" in (SELECT DISTINCT "FILTER_VALUE" FROM "SECURITY".
"RLS_PLANT_ACCESS" WHERE USER_NAME = SESSION_USER) )
```

**Listing 10.3**    SQL Expression for Dynamically Filtering Data

In these examples, notice that you can use a variety of attribute columns, operators, and even subqueries to define filter expressions. To better illustrate dynamic expression-based SQL-based analytic privileges, let’s walk through the process of defining them.

To create a SQL-based dynamic analytic privilege, you can use the SAP HANA Web-Based Development Workbench editor. Within the editor, locate a secure package location to host the analytic privileges. Within the repository, locate a package in a secure location. Right-click the package and choose New • Analytic Privilege…. A popup window will appear labeled New Analytic Privilege.

In this window, specify the technical name of the analytic privilege in the Name field. The name can only contain the characters A–Z, a–z, and the underscore special character. In the Label field, specify a description for the analytic privilege. The Type dropdown list must contain have the SQL option selected because these information views are configured to use SQL analytic privileges. Click Create to continue.

A new SQL-based dynamic analytic privileges management tab will appear titled with the name of the analytic privilege. Just above the Privilege Validity section, you’ll see three radio buttons: Attributes, SQL Editor, and Dynamic. Choose the SQL Editor option to continue. The tab layout will again update, and a new section titled SQL Editor will appear. As shown in [Figure 10.15](#10_006.html#f10.15), the new layout window is divided into three main sections: General, Secured Models, and Sql Editor.

The first section, General, located in the top left corner, contains fields for the Name, Label, and Type of the analytic privileges. The Label field can be updated at any time. The Name and Type fields are read-only at this point in the process.

[![Dynamic Expression-Based SQL Analytic Privileges Management Window](bilderklein/klein10_015.png)](img-f10.15.html) 

**Figure 10.15**    Dynamic Expression-Based SQL Analytic Privileges Management Window

The Secured Models section, located on the bottom left corner, provides an interface to add or remove additional referenced information views. To add additional information views, click the Add button and search for the desired information view. To remove an information view, highlight it in the list and click the Remove button. The large section on the right named SQL Editor, is where you can type the desired SQL filter expression.

Let’s assume that the SQL expression must support a subquery lookup based on the security table values shown in [Table 10.3](#10_006.html#t10.3). To accommodate this, we’ll use a subquery to look up an array of filter value from the `FILTER_VALUES` column. Based on this requirement, we’ll use the expression shown in [Listing 10.4](#10_006.html#l10.4).

```
 "CUSTOMERKEY" IN 
    (SELECT "CUSTOMERKEY"
    FROM "security_tables"."Security.Tables::RLS_CUSTOMER_ACC"
    WHERE "USER_NAME" = SESSION_USER)
```

**Listing 10.4**    Example Complex SQL Filter Expression

In effect, you can look up filter values and apply these values to the filter expression using the `SESSION_USER` variable at runtime. You can do this even without the use of a stored procedure, which simplifies the solution by reducing the number of design-time objects required.

Click the save icon when you’re ready to deploy the analytic privileges, which will both save an analytic privilege within the repository and deploy it to the system for use within a role. Once an analytic privilege is activated, its restrictions won’t apply until the analytic privilege is granted to an existing role or user. If no competing analytic privileges have also been applied to the grantee, queries to the referenced information views will be limited based on the defined filter conditions or restrictions.

## 10.7 Troubleshooting Effective Analytic Privileges and Filter Conditions

The easiest method of troubleshooting the net effect of analytic privileges for a given user and information view is to query the `SYS.EFFECTIVE_STRUCTURED_PRIVILEGES` system view.

When querying this system view, three filter conditions within the WHERE clause must be satisfied before the query will execute. The `USER_NAME`, `ROOT_SCHEMA_NAME`, and `ROOT_OBJECT_NAME` columns must all be specified in the WHERE clause as filter conditions. The SQL code shown in [Listing 10.5](#10_007.html#l10.5) will check for the effective analytic privileges applied to the `WTRAN05` user for the `e-corp.sales.models/SCV_CUSTOMER_SALES` information view.

```
SELECT *
FROM "SYS"."EFFECTIVE_STRUCTURED_PRIVILEGES" 
WHERE
"USER_NAME" = 'WTRAN05' AND 
"ROOT_SCHEMA_NAME" = '_SYS_BIC' AND
"ROOT_OBJECT_NAME" = 'e-corp.sales.models/SCV_CUSTOMER_SALES'
```

**Listing 10.5**    SQL Statement for Querying EFFECTIVE\_STRUCTURED\_PRIVILEGES System View

The output of the query provides some important information. The `EFFECTIVE_FILTER` output column will indicate the total filters applied from all restrictions. If multiple restrictions are applied, this column will have the same output value for all rows.
