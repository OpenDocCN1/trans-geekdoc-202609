
The second role will similar to the first but will require the `"privileges_with_grant_option"` in the script for each privilege. This option will allow the grantee to also grant the same privilege to others. Recall that this ability is a requirement when granting privileges to the container’s `#OO` user. In addition, you must end the runtime name of the role with a `#`, which signifies that the roles contain the `"privileges_with_grant_option"` and the HDI infrastructure will only allow this privilege to be granted to the `#OO` user of a target container via an `.hdbgrants` file.

The design-time name of the second role will be `MYPROJ_EXT_HDI_OO_ACCESS.hdbrole`. Its runtime name will be `MyProj.db.roles::MYPROJ_EXT_HDI_OO_ACCESS#`, and the role will be configured with JSON syntax shown in [Listing 18.11](#18_004.html#l18.11).

```
{ 
  "role":{ 
    "name":"MyProj.db.roles::MYPROJ_EXT_HDI_OO_ACCESS#", 
      "object_privileges":[ 
      { 
       "name":"MyProj.db::CUSTOMERS", 
       "type":"TABLE", 
       "privileges_with_grant_option":[ "SELECT" ]
      } ,
      { 
       "name":"MyProj.db::CS_CUSTOMERS", 
       "type":"TABLE", 
       "privileges_with_grant_option":[ "SELECT" ]
      }
    ],
      
      "schema_privileges":[  
{  
    "reference":"REF_SYSTEM_2",
    "privileges_with_grant_option":[ "SELECT" ]
},
{  
    "privileges_with_grant_option":[ "SELECT" ]
}
  ]
    }
   }
```

**Listing 18.11** `MYPROJ_EXT_HDI_OO_ACCESS.hdbrole` Script

The script shown in [Listing 18.11](#18_004.html#l18.11) will grant the following access:

*   SELECT to the HDI table `"MyProj.db::CUSTOMERS"` including the WITH GRANT OPTION

*   SELECT to the HDI synonym `"MyProj.db::CS_CUSTOMERS"`, which actually points to the SYSTEM.CUSTOMER table including the WITH GRANT OPTION.

*   SELECT to the schema reference `REF_SYSTEM` including the WITH GRANT OPTION which points to the SYSTEM schema.

*   SELECT to the HDI container schema `MYPRJ_HDI_DB_1` including the WITH GRANT OPTION

Before you can build roles within your project, you’ll create the `MYPROJ_EXT_HDI_ROLREF.hdbroleconfig` file to provide link to the SYSTEM schema referenced in the [Listing 18.10](#18_004.html#l18.10) and [Listing 18.11](#18_004.html#l18.11) files. The file must contain the JSON statement shown in [Listing 18.12](#18_004.html#l18.12).

```
{ 
 "MyProj.db.roles::MYPROJ_EXT_HDI_APP_ACCESS":{ 
    "REF_SYSTEM":{ 
      "schema":"SYSTEM" 
        }
  },
   "MyProj.db.roles::MYPROJ_EXT_HDI_OO_ACCESS#":{ 
    "REF_SYSTEM_2":{ 
      "schema":"SYSTEM" 
        }
  }
 }
```

**Listing 18.12** `MYPROJ_EXT_HDI_ROLREF.hdbroleconfig` File

Within your project, you can now build the three files that will deploy these roles at runtime. These roles will need to be active at runtime so that the EXAMPLE container can access them.

To complete the process, you’ll now need to access the target EXAMPLE project in SAP Web IDE for SAP HANA. In this project, we’ll create two items. First, you’ll need to create an SAP HANA service connection to the primary HDI container MyProj. Second, you’ll need to create the `MYPROJ.hdbgrants` file that will reference the two HDI roles you created in the prior steps.

Let’s start by creating the service connection to the primary HDI container MyProj. Access SAP Web IDE for SAP HANA and expand the EXAMPLE project node to reveal the `db` folder. Right-click the `db` folder and choose the option New • SAP HANA Service Connection. Choose the HDI container option and then select the service in the list that references the MyProj container. The name of the service will start with the name of the user that activated it, followed by a serialized number and letter string and then end with `-MyProj-hdb_db`, as shown in [Figure 18.25](#18_004.html#f18.25).

[![Choosing the MyProj Service When Creating an SAP HANA Service Connection](bilderklein/klein18_025.png)](img-f18.25.html)

**Figure 18.25** Choosing the MyProj Service When Creating an SAP HANA Service Connection

Click OK to add this service to your `mta.yaml` file. Note the name of the service because you’ll need to reference this name when defining your `.hdbgrants` file.

Next, you’ll need to define the `MYPROJ.hdbgrants` file. This file will grant the primary container MyProj roles to various HDI container systems users. This step is required to so that runtime content within the target EXAMPLE container can access runtime content within the MyProj container. Within the `db • src` folder, create the file `MYPROJ.hdbgrants`. The file should contain the JSON text shown in [Listing 18.13](#18_004.html#l18.13).

```
{
  "XSA_ADMIN-x6o70e6hj4yiatlu-MyProj-hdi_db" : {
   "object_owner" : { 
      "schema_roles" : [
       "MyProj.db.roles::MYPROJ_EXT_HDI_OO_ACCESS#"
      ]
    },
    "application_user" : {
      "schema_roles" : [
        "MyProj.db.roles::MYPROJ_EXT_HDI_APP_ACCESS"
      ]
    }
  }
}
```

**Listing 18.13** The `MYPROJ.hdbgrants` File in the EXAMPLE Project

Within the script, you’ll start by referencing the service name `"XSA_ADMIN-x6o70e6hj4yiatlu-MyProj-hdi_db"` : { . This name is specific to the name you set up in the `mta.yaml` project or when creating the SAP HANA service connection. You’ll then assign the two roles to the different service account users. The role `"MyProj.db.roles::MYPROJ_EXT_HDI_OO_ACCESS#"` is the role with the highest level of access and must be granted to the `#OO` user within the `"object_owner"` JSON value array. The `"application_user"` JSON value array will be mapped to the `"MyProj.db.roles::MYPROJ_EXT_HDI_APP_ACCESS"` role.

Once the `MYPROJ.hdbgrants` is built and deployed to runtime, you can now reference MyProj runtime objects within the EXAMPLE project. Keep in mind that you’ll first also need to create synonyms in the EXAMPLE project that reference objects in the MyProj container. However, the GUI will walk you thought this process any time you browse for objects from the HDI container service connection. Again, the service connection allows developers to search for objects native to the primary HDI container MyProj at design time. In addition, the service connection allows the `MYPROJ.hdbgrants` file to grant its roles to the `EXAMPLE_HDI_DB_1#OO` user at runtime.

## 18.5 Summary

You should now have a basic understanding of the difference scenarios and options that security teams need to understand when supporting security in the SAP HANA XSA environment. The SAP HANA XSA cockpit is used to configure SAP HANA XSA users, access to organizations, and access to spaces. Many other options are available, including the management of the service connections key to providing security within SAP Web IDE for SAP HANA and with HDI containers. SAP Web IDE for SAP HANA is primarily a developer’s tool, but the security team will need to understand how to create HDI container roles and manage the `.hdbgrants` file. In addition, we discussed the complex options for granting database users access to objects within an HDI container using `.hdbrole` files, granting access between containers and classic database objects in the `.hdbgrants` file, granting access to the `#OO` user directly, and finally granting access between containers.

# The Author

[![](bilderklein/klein1896_haun.png)](img-f_none_A_00.html)

Jonathan Haun currently serves as a senior director at Enowa LLC where he is responsible for managing the company’s business intelligence and technology practices. Over the past few years, Jonathan has helped several clients implement solutions using SAP HANA. In addition to being certified in multiple SAP BusinessObjects Business Intelligence (BI) tools, he also holds the SAP Certified Application Associate—SAP HANA 1.0, SAP Certified Technology Associate—SAP HANA 1.0, and SAP Certified Technology Specialist—SAP HANA Installations certifications.
