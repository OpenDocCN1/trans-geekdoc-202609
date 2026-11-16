# LDAP Models

Let's explore the four models of LDAP which allow LDAP software to be interoperable, thus allowing for it to be tailored to fit disparate applications from different vendors:

+   - Information model
+   - Naming model
+   - Functional model
+   - Security model

# Information Model

The information model describes the informational units that go into the directory, that is, the entries and their types. As we saw earlier, the entries are the basic building blocks of the directory, which in turn are composed of attributes. The attributes of an entry are composed of an attribute type and one or more values. We design a schema for the directory which constrains the attributes and the type of attributes. Schemas are described in the LDIF (LDAP Data Interchange Format).

# LDAP Data Interchange Format (LDIF)

LDIF is a standardized text-based format that describes directory entries. Using the LDIF format, data from one directory can be exported to another regardless of the actual format the two directories use for their datastores. For example, we can move data from a directory that uses GDBM as a back-end datastore to another directory that uses Oracle's RDBMS as a datastore.

LDIF has been designed with the "lightweightness" of LDAP in mind. LDIF is a text format and even binary entries (such as images) need to be converted to base64 (a text format) before they can be stored as part of an LDIF definition. Further, the LDIF format provides a human-readable interface for data stored within the directory. However, remember that the actual storage of data within the LDAP server itself is in the format required by the particular back-end database that it uses for a datastore and should not be confused with LDIF.

Let's take a look at a sample directory that we shall be using further when we take a look at developing an LDAP application in the last section:

![](bbox=[0.16, 0.68, 0.87, 0.93])