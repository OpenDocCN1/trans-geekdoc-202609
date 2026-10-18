
Now that the schemas are in place, developers can create tables to store the data. The security consultant recommends that developers use repository-based tables for two reasons: First, developers won’t need the `CREATE ANY object` privilege for the two schemas, which simplifies the security model. Second, repository tables can be promoted easily with the security model to other SAP HANA environments to support sound lifecycle management.

[![Development Repository Schema Artifacts and Corresponding Script Syntax](bilderklein/klein03_013.png)](img-f3.13.html)

**Figure 3.13** Development Repository Schema Artifacts and Corresponding Script Syntax

Because the tables created by the developers must be secured in such a way that developers can frequently make changes, the security consultant recommends that E-Corporation create a new package hierarchy to store development artifacts that the development team can use for the sales analytics project. Setting up a separate package hierarchy in these instances is recommended because this hierarchy can be secured independently from the top-level security package. The consultant thus recommends that a top-level package named `e-corp` be created and, within it, a subpackage named `sales`. Within the `sales` package, he also recommends that a package named `tables` be created. [Figure 3.14](#03_005.html#f3.14) shows how the resulting package hierarchy should appear within the SAP HANA Web-Based Development Workbench editor.

[![E-Corporation’s Package Hierarchy](bilderklein/klein03_014.png)](img-f3.14.html)

**Figure 3.14** E-Corporation’s Package Hierarchy

E-Corporation creates the Customers table and the Products table in the `StagingMart` schema (following the steps in [Section 3.3.2](#03_003.html#h3.3.2)). The repository CDS tables are created within the `e-corp.sales.tables` package. The repository object type will be a CDS document or an `.hdbdd` file. We’ll use the context `stg` so that each table is prefixed with “`e-corp.sales.tables::stg`.” [Listing 3.2](#03_005.html#l3.2) shows the syntax of the `stg.hdbdd` script that will be activated to generate runtime tables in the SAP HANA schema “`StagingMart`”.

```
namespace "e-corp".sales.tables;
@Schema: 'StagingMart'
context stg {ENTITY Customers {
    key CustomerID : Integer;
    CustomerName : String(256);
    CustomerAddressLine1 : String(256);
    CustomerCity : String(256);
    CustomerLatt : Decimal(26,6);
    CustomerLong : Decimal(26,6);

    }
ENTITY Products {
    key ProductID : Integer;
    ProductName : String(256);
    ProductDescription : String(256);
    ProductTypeID : Integer;
    ParentProductID : Integer;
    }

}
```

**Listing 3.2** Syntax of the `stg.hdbdd` Script

Once the CDS document table script is activated, two new tables will be visible within the `StagingMart` schema. The names of the tables are shown in [Figure 3.15](#03_005.html#f3.15), which shows the SAP HANA Web-Based Development Workbench catalog. Notice how the name of the runtime version of each table includes the repository package hierarchy name, two colons, the context name, and finally the table or CDS entity name.

[![CDS Repository-Based Tables Created in the StagingMart Schema](bilderklein/klein03_015.png)](img-f3.15.html)

**Figure 3.15** CDS Repository-Based Tables Created in the StagingMart Schema

SAP HANA requires unique object names for all runtime versions of objects created within the repository. To achieve this requirement, the package hierarchy name is automatically included as a prefix for every catalog object created within the CDS document.

E-Corporation now has two design-time schema scripts, one CDS document script resulting in two runtime schemas, and two runtime catalog tables. The foundation for a sound security model has been implemented. Developers that have been granted privileges for these objects can now begin loading data into these SAP HANA tables. Security administrators can relax, knowing that their security model can be transported and backed up.

## 3.6 Summary

In this chapter, you learned about catalog objects. How you choose to create catalog objects is one of the most important factors on the type of security model and security processes that will be implemented. If you create standard catalog objects, then developers and security administrators will constantly need to follow tedious processes for the model to be maintained. However, if you choose to create repository-based catalog objects, then developers can be mostly decoupled from the security model maintenance process. In addition, the security model and its dependent catalog objects can be transported easily to another system or into a backup file.

In the next chapter, we’ll dive more deeply into the security model by exploring the processes necessary for provisioning users. We’ll also discuss the processes necessary for assigning privileges and roles to user accounts.

# 4 User Accounts

In this chapter, we’ll provide a complete overview of user accounts, including the processes for provisioning, maintaining, and granting privileges and roles to user accounts.

Before a person, application, or service can interact with the SAP HANA system, it must be authenticated. To authenticate with SAP HANA, the person, application, or service must issue credentials. These credentials are typically validated in the form of a user account and a password. The authentication process is designed to uniquely identify the person, application, or service because SAP HANA supports authorizations for each individual user account. Authorization is the process whereby SAP HANA determines the types of actions that the user account can perform, and these authorizations come in the form of granted privileges.

In [Chapter 2](#02_001.html#h2), we introduced you to the concept behind privileges and explored the different types of privileges available within SAP HANA. Privileges can be granted to user accounts or to roles, and roles can then be granted to one or more user accounts. Inevitably, privileges authorize a user account to perform specific actions within SAP HANA, and so an important relationship exists between privileges and the user accounts that they are assigned to.

In this chapter, we’ll introduce you to the process of creating user accounts, managing user accounts, assigning privileges to user accounts, and assigning roles to user accounts. As you’ll discover, these actions can be performed in multiple ways, such as via SQL statements or using graphical user interfaces (GUIs).

## 4.1 What Are User Accounts?

A user account is essentially an object in the SAP HANA system that stores a user name, password, and other attributes pertaining to the user account. User names can be defined with any alphanumeric character from A–Z or numbers 0–9. The underscore (`_`) is also supported. Most special characters, such as periods, colons, equal signs, spaces, commas, and many others are not supported within a user name. By default, passwords must be defined according to system-configured standards for complexity. User accounts also contain other attributes, such as an email address, a Security Assertion Markup Language (SAML) identity, a Kerberos identity, a locale, a statement memory limit, and a time zone. Four different types of user accounts can be created, as we’ll explore in the following sections.

### 4.1.1 Standard User Accounts
