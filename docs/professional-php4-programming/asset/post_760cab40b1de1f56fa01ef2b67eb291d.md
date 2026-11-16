
So what if an employee has two telephone numbers, say one work number and a second cell phone number? In a traditional database, this is solved by representing the numbers as a separate telephone number table with the employee ids used to relate them to a particular employee. However, in an LDAP directory there can be one attribute with the name `telephonenumber` but with multiple values; there could be two fields with the same name `telephonenumber`, one representing the work number and the other representing the mobile number. In such a situation, the directory is most likely to perform better than the database in terms of processing a query for the telephone numbers of an employee. Such a fluid scheme is one of the reasons that queries are processed very fast in a LDAP directory.

- Directories such as LDAP order data in a hierarchical fashion as well as group data into various groups. As an example for this, consider the entries for employees in the FooWid Inc chart in the LDAP Applications section later in the chapter. The entry may have an attribute called `workfloor` that determines the floor on which the employee is working. All employees working on the first floor belong to the First Floor group. Thus, though the data may appear to be organized hierarchically, it is also grouped using attributes to affect the grouping. However, it must be noted that there are no standards for groups. A group is simply an objectclass with attributes that store the DN of entries in the organization. By interrogating the objectclass, applications can draw out the basic nodes that relate to any one group, and traverse them.

- Objects in a directory bear a close resemblance to tables. This is because all entries corresponding to objects of the same type have similar attributes, just as all records in a particular database table have the same set of fields. However, objects in directories go a little further in that they can be extended in an object-oriented fashion to add more attributes. This is something that we cannot possibly do with a database table (unless we create a new table and populate it with earlier data or use subsidiary tables).

## Components of LDAP

LDAP as a directory system involves the following components:

![](img/9cf7789dba9b16ef3f8576d5aea89186_506_0.png)

- LDAP server is the server that LDAP clients interact with to obtain directory information. The actual data is stored in a datastore (usually a database). The datastore is hidden from the clients since the server knows how to retrieve information from the datastore and present it to the clients in a common format.

- LDAP data organization, indicated by Back-End Database in the above diagram, defines how the data is formatted while in storage and exchange with respect to the communicating LDAP entities, that is, client-server and server-server (a special case which we shall see soon).

- LDAP protocol, indicated by X.500 Server in the above diagram, is the common language spoken by clients and servers when the clients access the directory. The protocol itself is message-oriented, that is, no states about the clients are maintained on the server. The client sends one or more LDAP messages or LDAP requests to the server that processes the requests and sends the results back to the client as LDAP messages or responses. The LDAP protocol also provides for certain server to server communication.

- LDAP clients implemented using different vendor APIs and tools on different platforms are able to connect to the LDAP server, as long as they speak the LDAP protocol and handle data in the particular format required by LDAP.

## Characteristics of LDAP

Let's take a look at some of the distinguishing features of LDAP that have made it the directory solution of choice.

### Global Directory Service

A well-designed LDAP directory allows users to access data that is uniquely identifiable on a global scale. To clarify this further, entities stored in an LDAP directory are unique in the sense that no two-directory entities anywhere in the world will have the same identifier to access it.

Taking the domain name analogy on the Internet, the owner of yourdomain.com may have a machine with the name foomachine. Now, the owner of mydomain.com can still have a machine with the name foomachine, because the machine can be uniquely identified as foomachine.mydomain.com as opposed to foomachine in the domain yourdomain.com, which can be uniquely identified as foomachine.yourdomain.com. LDAP uses a similar strategy for maintaining uniqueness of its entities, which we shall soon see.

### Open Standard Interconnectivity

LDAP is an open standard and can be adopted by any vendor or individual freely with no licensing involved. The fact that LDAP can run on top of TCP/IP gives it the unique advantage of interconnectivity with machines similarly enabled. Further, the clients and servers are vendor-independent as long as they can speak LDAP.

### Customizability and Extensibility

The query and update mechanism of LDAP is standardized between clients and servers. The users are insulated from it, since each application can have its own interface or a GUI that translates the user interaction into this query and update standard. Further, it is flexible enough to be extended to suit different application scenarios and locales; in fact LDAPv3 applications can support multiple languages using the Unicode UTF-8 character set for all attribute values and values of identifiers.

### Heterogeneous Data Store

The LDAP server uses a back-end datastore to store its data, but is not tied down to any particular database. In fact LDAP can at the same time use more than one back-end database to store and retrieve its data. So it is not uncommon for one LDAP server to use a commercial database as its datastore while another server might just as well use a flat file datastore.

### Secure and Access Controlled Protocol

LDAP is a secure protocol in that it makes use of authentication to ensure that transactions are secure. Authentication is used by the server to establish that the interacting client is who it claims to be. In LDAP version 2, this was done by sending a password along with the identifier for the interacting entity. This was, however, not a very secure mechanism since it was exposed to eavesdropping on the wire.

LDAP v3 uses the Simple Authentication and Security Layer (SASL) that, by making very few assumptions about the actual mechanisms that implement security, allow a lot of flexibility in choosing the right authentication scheme. The Secure Socket Layer (SSL) protocol, is the most popular one to be implemented for this purpose and provides protection against network eavesdropping.

Apart from just authenticating transactions, LDAP provides a very rich set of access control features, which can be used to control who accesses what and the manner in which this can be done (such as update or query). Password policy control as part of version 3 allows for fine-grained password expiration. The proxied authorization control allows users to perform certain operations assuming a different role or set of privileges.

### LDAP Applications

The key to deciding whether to choose an LDAP directory service is to understand what data can go into the LDAP directory. A few cases of what data can be represented using an LDAP directory and some examples of common directory applications are in order:

- The directory services can be white page services, yellow page services, or a query list of all the printers on the 6th floor. Queries with multiple constraints are of course possible – list of all employees in the Engineering division working out of Europe with birthdays falling on March 22nd.

- A very common LDAP application is seen in e-mail clients that auto-fill the e-mail address of the recipient when the name of the recipient is typed into the To: field. The e-mail client uses the name to query an e-mail directory and fills in the field with the result.

- Several LDAP applications are actually gateways to other established services. For example, using a DNS to X.500 gateway, it is possible for LDAP-enabled clients to query an LDAP server for information residing on a legacy X.500 directory. Other examples of LDAP gateways are e-mail to LDAP, finger to LDAP, and DNS to LDAP.

Examples of data suited to reside in LDAP directories:

- Employee phone book

- Organizational charts

- IT services information (for example, Domain names or IP addresses of servers)
