
When we perform a search, we need to specify the base of the tree where the search should begin and also the scope of the search. The scope indicates what part of the tree is to be covered while searching. ldap_list() performs the search for a specified filter on the directory with the scope, LDAP_SCOPE_ONELEVEL. This means that the search should only return information that is at the level immediately below the base DN given in the call (equivalent to typing ls on a UNIX shell and getting a list of files and folders in the current working directory).

This call takes an optional fourth parameter that is an array of just the required attributes. The newly introduced parameters attrsonly, sizelimit, timelimit and deref have exactly the same functionality as they have in the ldap_search() and ldap_read() functions. This function returns a search result identifier or false on error.

### ldap_count_entries()

```
int ldap_count_entries(int link_identifier, int result_identifier)
```

ldap_count_entries() returns the number of entries stored as a result of previous search operations (as a result of a search call). result_identifier identifies the internal LDAP result. It returns false on error.

### ldap_next_attribute()

```
string ldap_next_attribute(int link_identifier,
int result_entry_identifier, int &ber_identifier)
```

ldap_next_attribute() is called to retrieve the attributes in an entry. The internal state of the pointer is maintained by the ber_identifier. It is passed by reference to the function. The first call to ldap_next_attribute() is made with the result_entry_identifier returned from ldap_first_attribute(). It returns the next attribute in an entry on success, and false on error.

### ldap_next_entry()

```
int ldap_next_entry(int link_identifier, int result_entry_identifier)
```

This function returns the entry identifier for the next entry in the result whose entries are being read starting with ldap_first_entry(). Successive calls to ldap_next_entry() return entries one by one till there are no more entries. The first call to ldap_next_entry() is made after the call to ldap_first_entry with the result_identifier as returned from the ldap_first_entry(). If there are no more entries in the result then it returns false.

## Modification Functions

It must be remembered that modification of directory entries should not be as frequent as search operations or the performance of the server would degrade significantly. However, modification is necessary and the functions under this category even allow us to add and delete entries and attributes.

### ldap_add()

```
int ldap_add(int link_identifier, string dn, array entry)
```

The ldap_add() function adds new entries into the directory. When adding or modifying an entry, the entry must have all of the required attributes and only allows attributes as specified by the LDAP server's schema. Objectclass attributes define what attributes are required and which ones are simply allowed (such as, optional).

The link_identifier is the connection identifier that is returned by the ldap_connect() function. The new entry to be added needs a DN that is specified as the second argument. The third argument passed is an array consisting of attributes and values of the new entry. If we take the example of the LDIF for FooWid, the entry array would be:

```
entry["cn"] = "Don Joe III";
entry["mail"] = "djoe@exist.com";
entry["description"] = "Professional bungee-jumper";
...
```

### ldap_mod_add()

```
int ldap_mod_add(int link_identifier, string dn, array entry)
```

This function adds attribute values to the existing attributes of the specified DN. It performs the modification at the attribute level as opposed to the object level. Object level additions are done by the ldap_add() function, that is, if we needed to add a telephone number to an entry, we would use this function, whereas to add a completely new entry we would rely on ldap_add(). It returns true on success and false on error.

### ldap_mod_del()

```
int ldap_mod_del(int link_identifier, string dn, array entry)
```

This function removes attribute values from the specified DN. It performs the modification at the attribute level as opposed to the object level. Object level deletions are done by the ldap_del() function, that is if we needed to delete the room number of an entry corresponding to an employee, we would use this function, whereas to completely delete an employee entry, we would rely on ldap_del(). It returns true on success and false on error.

### ldap_delete()

```
boolean ldap_delete(int link_identifier, string dn)
```

ldap_delete() deletes a particular entry in the LDAP directory specified by the DN. It returns true on success and false on error. Usually LDAP servers are configured such that this is only allowed for as few users as is specified in the LDAP server's ACL.

### ldap_modify()

```
boolean ldap_modify(int link_identifier, string dn, array entry);
```

ldap_modify() is used to modify the existing entries in the LDAP directory. The structure of the entry is same as in ldap_add(). It returns true on success and false on error. Modifications are only allowed for authenticated users. The server's ACL usually allows different users to modify different attributes. For example, all users might only be allowed to change their password, while a user's manager might be able to change a user's office number and job title, and only a select group (for example the directory administrators) can edit any attribute.

All modifications must follow the server's schema. A modification can take the form of an add, replace, or delete action. Special care must be taken with replacing multi-valued attributes because if we replace an attribute with multi-values with a single value, we will be in effect replacing all of its values.

## Error Functions

These functions are useful in identifying error conditions within our scripts. They are designed to allow us to write scripts that are independent of the locale or specifically the local language in which the error messages are represented.

### ldap_errno()

```
int ldap_errno(int link_identifier)
```

Often we need to check the error value of the last executed function. This value is available to us by calling the ldap_errno() function. The return value of this function can be passed to the ldap_err2str() function to obtain a string describing the error.

### ldap_error()

```
string ldap_error(int link_identifier)
```

This function merely combines the functionality of the ldap_errno() and the ldap_err2str() functions, that is it returns a string describing the error if any occurred while executing the last function. The link_identifier argument is available because it is possible that since the application might open connections to more than one LDAP server, we need a mechanism to examine error conditions associated with each of the connections.

### ldap_err2str()

```
string ldap_err2str(int errno)
```

ldap_err2str() returns a descriptive error string when supplied with an argument that is an error number. This is especially useful when running localized applications where the error messages may be in a local language. Programs can therefore check for error numbers rather than error strings.

## A Sample LDAP Application in PHP

So we finally get down to putting to some practical purpose what we have gleaned through the course of this chapter.

We will develop an application that will export the directory information for the employees of our favorite company Foo Widgets Inc. Let us look at what could be the possible requirements and design considerations for such an application:

- There are two categories of users - regular employees and the directory administrator.
- The application should allow a regular employee to search entries corresponding to all other employees and to modify the entry corresponding to them.
- The administrator should have exclusive privileges unavailable to regular employees – to create new entries and delete existing entries.
- The application should use an LDAP directory as the back-end.
- It should have a simple front-end, with all complexity moved to the back-end. It should ideally be browser-independent.
- A set of common utility functions first, upon which to build the application itself.

The script below is the first that gets invoked as part of launching the application:

```
<?php
// empdir_first.php
```

We include a set of utility functions here:

```
require("empdir_functions.php");
```

This script is called again as a result of the user deciding to either add a new entry or to search for an existing entry:

```
if (!isset($choice)) {
    generateHTMLHeader("Click below to access the Directory");
    generateFrontPage();
} else if (strstr($choice, "ADD")) {
    $firstCallToAdd = 1;
```

For additions to the directory the empdir_add.php script is called:

```
require("empdir_add.php");
} else {
    $firstCallToSearch = 1;
```

For searching the directory, we call the empdir_search.php script:

```
require("empdir_search.php");
}
?>
