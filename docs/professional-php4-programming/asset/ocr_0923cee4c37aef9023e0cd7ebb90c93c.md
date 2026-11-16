| Method | Description |
| --- | --- |
| create() | Creates new user in the database |
| update() | Updates the user in the database |
| delete() | Removes the user from the database |
| getUsername() | Returns the property |
| setUsername() | Sets the property |
| getFullname() | Returns the property |
| setFullname() | Sets the property |

# # Application Logic

Two scripts will handle the maintenance of the Privilege and UserPrivilege information in the system: privilege.php and userprivilege.php. We will leave it to the developers who use our system to create their own script(s) for maintaining user information such as name, contact information, and passwords.

# ### privilege.php

privilege.php is responsible for handling user activity regarding privileges, namely requests to create, delete, or modify privileges in the system. It contains the following functions:

| Function | Description |
| --- | --- |
| main() | Flow control |
| getPrivileges() | Returns an array of all privileges |
| save() | Saves the selected privilege |
| delete() | Removes the selected privilege |
| validate() | Validates form data |
| displaySelection() | Generates page for selecting a privilege |
| displayDetails() | Generates page for selected privilege |

# ### userprivilege.php

userprivilege.php is responsible for handling user activity concerning the assignment of privileges to users. It contains the following functions:

| Function | Description |
| --- | --- |
| main() | Flow control |
| getUsers() | Returns an array of all users |