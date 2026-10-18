
# HDI 容器用户、架构与权限说明

*   One user and schema named `MYPROJ_HDI_DB_1#DI`. This user and schema contain APIs as stored procedures and metadata tables. For example, you can use a stored procedure in this schema to grant standard users access to the HDI schema `MYPROJ_HDI_DB_1`.

*   The object owner user and schema named `MYPROJ_HDI_DB_1#OO`. This user is an important user from a security standpoint, which we’ll explain in more detail shortly.

*   Multiple users using the naming pattern `MYPROJ_HDI_DB_1_<GUID>_DT`. What roles these users play is unclear, but from a security standpoint, they can use `EXECUTE` on some critical API stored procedures in the `MYPROJ_HDI_DB_1#DI` schema.

*   Multiple users using the naming pattern `MYPROJ_HDI_DB_1_<GUID>_RT`. What roles these users play is unclear, but from a security standpoint, they can use `EXECUTE` on some critical API stored procedures in the `MYPROJ_HDI_DB_1#DI` schema.

From a complete list of granted privileges, users, schemas, and other database objects associated with our example HDI container named `MYPROJ`, you can run the example SQL statements shown in [Listing 18.1](#18_004.html#l18.1) to see details concerning the deployment.

```
SELECT * FROM SYS.SCHEMAS WHERE SCHEMA_NAME like '%MYPROJ%';
SELECT * FROM SYS.TABLES WHERE SCHEMA_NAME like '%MYPROJ%';
SELECT * FROM SYS.VIEWS WHERE SCHEMA_NAME like '%MYPROJ%';
SELECT * FROM SYS.PROCEDURES WHERE SCHEMA_NAME like '%MYPROJ%';
SELECT * FROM SYS.OWNERSHIP WHERE SCHEMA_NAME like '%MYPROJ%';
SELECT * FROM SYS.USERS WHERE USER_NAME like '%MYPROJ%';
SELECT * FROM SYS.ROLES WHERE ROLE_NAME like '%MYPROJ%';
SELECT * FROM SYS.GRANTED_ROLES WHERE ROLE_NAME like '%MYPROJ%';
SELECT * FROM SYS.SYNONYMS WHERE SCHEMA_NAME like '%MYPROJ%'; 
SELECT * FROM SYS.GRANTED_PRIVILEGES 
WHERE  SCHEMA_NAME like 'MYPROJ_HDI_DB_1#%';
```

**Listing 18.1** Example SQL to See What Is Created in the SAP HANA Database to Support an HDI Container

In addition to these users, two roles are also created. The first is the `MYPROJ_HDI_DB_1::access_role`, and the second is the `MYPROJ_HDI_DB_1::external_privileges_role`. `MYPROJ_HDI_DB_1::access_role` is granted limited object privileges on the schema `MYPROJ_HDI_DB_1` and is also granted privileges defined in `.hdbgrants` scripts for the application user or within the `application_user` value array. The role `MYPROJ_HDI_DB_1::external_privileges_role` has no defined privileges by default.

The user account that ends in “#OO” or `MYPROJ_HDI_DB_1#OO` using our working example is the first account we’ll examine. “OO” is short for “object owner,” and we’ll use the term `#OO` at times in this chapter when referring to this user. By default, this user has limited access to the database but has the `CREATE ANY`, `CREATE VIRTUAL PACKAGE`, and `SELECT METADATA` object privilege on the `MYPROJ_HDI_DB_1` schema. On its own schema, this user is only granted the `CREATE TEMPORY TABLE` object privilege. This user is also granted the roles `_SYS_DI_OO_DEFAULTS` and the `PUBLIC` role. The `_SYS_DI_OO_DEFAULTS` role provides “API”-like access to stored procedures and access to metadata views for manipulating the runtime objects in an HDI container. This role is also granted to all `#OO` users by default. Any privileges this role has been granted would apply to all `#OO` users in the database. However, we do not recommend leveraging this role in your security model design.

Out of the box, the `#OO` user will have access to objects in the `MYPROJ_HDI_DB_1` schema because it is the creator or “object owner” of all objects in that schema. In SAP HANA, if you create a catalog object, you have full privileges access to it. When an HDI container requires access at runtime to non-HDI container catalog objects (i.e., classic runtime objects in the database) or other runtime objects deployed by another HDI container, the `#OO` user must also have access to those catalog objects. For example, if you’ve deployed SAP S/4HANA on the SAP HANA database and SAP S/4HANA created the schema `SAPABAP1`, you would need to log on to SAP HANA as `SAPABAP1` and run the following statement for the HDI container `MyProj` to access tables in that schema at runtime:

```
GRANT SELECT ON SCHEMA SAPABAP1 TO MYPROJ_HDI_DB_1#OO WITH GRANT OPTION;
```

A second process exists that SAP Web IDE for SAP HANA developers can use to grant the `#OO` user access to external objects using standard database role, `.hdbgrants` files, user-defined services, and `.hdbsynonym` files within your projects. We’ll explain this process in more detail in [Section 18.4.3](#18_004.html#h18.4.3).

The second user of interest is the `MYPROJ_HDI_DB_1#DI` user, or `#DI` user for short. This user is the owner of a schema that contains tables, views, and stored procedures that are important to the mechanics of the HDI container at runtime. As mentioned earlier, you cannot log on as this user. Therefore, you would technically need another database user that has `EXECUTE` access to this schema, or the procedures within the schema, before you can grant external access outside of the HDI container. This process is quite complicated and requires executing a series of stored procedures in a variety of schemas and as different users to effectively give a non-HDI user the ability to grant access to the HDI user schema instead of creating SAP Web IDE for SAP HANA developer artifacts. Luckily, with SAP Web IDE for SAP HANA, the SAP HANA database explorer provides an option for a user to open the SQL console as the “admin” or as `_SYS_DI` or as other technical system-generated users with `EXECUTE` access on the procedures.

## Users with EXECUTE Access to the #DI Schema Procedures

Note that we could not determine the exact user that is impersonated when launching the SQL console as an admin within the SAP HANA database explorer. By querying the SAP HANA metadata views, we could see that the system account `_SYS_DI` is the owner of the procedures within the `#DI` schema. We can also see that other system-generated users also have the access. For example, the following SQL will list the user account with `EXECUTE` access on the procedure for the HDI container named `MYPROJ_HDI_DB_1`:

```
SELECT * FROM SYS.GRANTED_PRIVILEGES 
WHERE  SCHEMA_NAME like 'MYPROJ_HDI_DB_1#%' 
and OBJECT_NAME like 'GRANT_CONTAINER_%'
```

You can also query the ownership view to see the owner of the procedures. The following SQL will list the owners of the procedures for the HDI container named `MYPROJ_HDI_DB_1`:

```
SELECT * FROM SYS.OWNERSHIP 
WHERE SCHEMA_NAME like '%MYPROJ%'
and OBJECT_NAME like 'GRANT_CONTAINER_%';
```

Opening the SQL console as the “admin” is a shortcut explained in Sections [Section 18.3.2](#18_003.html#h18.3.2) and [Section 18.4.3](#18_004.html#h18.4.3). Another option, which we’ll discuss later in [Section 18.4.2](#18_004.html#h18.4.2), is to create HDI container roles and then grant them to users. However, you’ll still need to use the SAP HANA database explorer’s SQL console run as an admin to grant the role to other users. Therefore, technically, you have two additional options to achieve the same result. However, these “easier” options give SAP Web IDE for SAP HANA developers security access and the ability to escalate their own privileges at runtime. This access is a major security concern because you cannot selectively prevent the editing of objects at design time like you could in the SAP HANA XS `_SYS_REPO` platform.

In the next section, we’ll review HDI container roles and how they you can use them to provide access to catalog objects, schemas, calculation views, and other items within an HDI container.

## 18.4.2 HDI Container Roles
