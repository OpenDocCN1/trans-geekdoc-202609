+   - E-mail addresses
+   - Public certificates and cryptographic public keys
+   - URLs
+   - Binary data such as pictures

In short, LDAP can be used in applications where the data is seldom changed and the query volumes are high.

To better understand a typical application of LDAP let us take a look at the organizational chart of a small company, FooWid Inc. A directory service can be implemented to store information about the organization and its employees:

![](bbox=[0.146, 0.31, 0.885, 0.523])

FooWid, based in the USA and working out of a two-storied building has just two departments – manufacturing and administration and 5 employees. A thing to note here is that employees are hierarchically classified under departments, just as they are also grouped under the criteria of the floor on which they work. This is precisely the kind of scenario we can attempt to represent in an LDAP directory:

![](bbox=[0.146, 0.622, 0.89, 0.838])

First we break up the hierarchical tree into various levels and assign names to each of the levels; the first level is the country level and is labeled c, the next level is the name of the organization and the label is o; the label for departments is ou (organizational unit). Let us label the employee names as cn, (common name). Each of these labels has a value assigned to them.