In this case cn=Bob W, ou=Administration, o=FooWid, c=US is an example of a unique name to identify an employee's record. Once we locate a record using this identifier, we can easily access other interesting information contained in the record, such as the employee's e-mail id or telephone number.

So to uniquely identify an employee, would it be sufficient that we trace the employee node in the tree from the root? The answer is yes; for example, Bob could be uniquely identified as c=US, o=FooWid, ou=Administration, cn=Bob W.

# Some LDAP Terminology

Keeping in mind the organizational chart of FooWid as an example, let's take a look at some common terminology:

+   **Entry**
+   In a generic sense, an entry is to a directory what a record or row is to a database. The node holding the name Bob can also hold information about him, such as which floor he works on and what his e-mail address is. The whole node as such is called an entry. This is also called a DSE (Distinguished Service Entry).

+   **Attributes**
+   An attribute is to a directory what a field is to a database. The field in the entry Bob holding his common name is labeled as cn and is assigned the value Bob W; this is an example of an attribute.

+   **Objects**
+   Objects in a directory are analogous to tables in a database. All the records in a database table are similar in the sense that they have similar fields. Similarly all entries of a particular object type will have the same kind of attributes. Objects have the additional capability that they can be extended to add new attributes to the pre-existing list of attributes (unlike tables in relational databases).

+   **Distinguished Name (DN)**
+   The name used to uniquely (and globally) identify Bob is c=US, o=FooWid, ou=Administration, cn=Bob W. This is the distinguished name. Here an attribute, cn in this case, is chosen as the key that will represent the entry. The path leading to the entry with their values makes up the DN, thus the DN is the unique identifier of an entry.

+   **Relative Distinguished Name (RDN)**
+   Each level in the tree makes up a component of the DN to a particular node. Each of these components is called an RDN (Relative Distinguished Name).

+   **Directory Information Tree (DIT)**
+   The entire information tree of the directory itself is called the DIT (Directory Information Tree).

+   **Schema**
+   The schema of an LDAP directory gives the layout of the information it contains and also how this information is grouped. It thereby allows clients or external interfaces to determine how the data is arranged within the directory and how it can be accessed in terms of search, addition, deletion, modification, and so on. You must refer to RFC 2256 (http://www.ietf.org/rfc/rfc2256.txt) for comprehensive detail on the LDAP object classes and attributes.