# Understanding the Privilege System in Detail

sometimes called grant tables. These tables vary in their specific function but also serve the general function, which is to determine what users are and not allowed to do. Each of them contains several types of fields. There are scope fields, which identify the user, host, and part of a database that the privilege refers to; and privilege fields, which identify which actions can be performed by that user in that scope. There are also security fields, which contain security-related information, and resource control columns, which constrain the number of resources that may be consumed.
The user is used to decide whether a user can connect to the MySQL server at all and whether or she has administrator privileges. The host table formerly used and is now obsolete, but it is still present in the mysql database. The db determines which data-bases the user can use, the columns_priv table determines which columns within a database she has access to, the proxies_priv table determines which users can act as proxies or grant proxy privileges to others, and the proc_priv table determines which routines a user can execute.

# The User Table

The user table contains details of global user privileges. It determines whether a user is allowed to connect to the MySQL server at all and whether she has any global-level privileges—that is, privileges that apply to every database in the system.
You can see the structure of this table by issuing a DESCRIBE user; statement. The schema for the user table is shown in Table 12.1.

Table 12.1 Schema of the User Table in the mysql Database
| Field | Type |
| --- | --- |
| Host | char(60) |
| User | char(16) |
| Password | char(41) |
| Select_priv | enum('N', 'Y') |
| Insert_priv | enum('N', 'Y') |
| Update_priv | enum('N', 'Y') |
| Delete_priv | enum('N', 'Y') |
| Create_priv | enum('N', 'Y') |
| Drop_priv | enum('N', 'Y') |
| Reload_priv | enum('N', 'Y') |
| Shutdown_priv | enum('N', 'Y') |
| Process_priv | enum('N', 'Y') |