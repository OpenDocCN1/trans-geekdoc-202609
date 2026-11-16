
## Search Functions

The power of LDAP comes from the versatility of search operations that can be performed on the directory. Several functions are provided by PHP not just to search but also to manipulate and process results.

### ldap_search()

```
int ldap_search(int link_identifier, string base_dn, string filter
[, array attributes [, int attrsonly [, int sizelimit
[, int timelimit [, int deref]]]]])
```

ldap_search() performs the search for a specified filter on the directory with the scope of LDAP_SCOPE_SUBTREE. This is equivalent to searching the entire subtree under the specified base DN that is specified by base_dn. The search filter can be simple or advanced, using Boolean operators in the format described in the LDAP documentation. It returns a search result identifier or false on error.

There is an optional fourth parameter attributes that can be added to restrict the attributes and values returned by the server to just those required. This is much more efficient than the default action (which is to return all attributes and their associated values). The use of the fourth parameter should therefore be considered good practice. The fourth parameter is a standard PHP string array of the required attributes, for example array (mail, sn, cn). Note that the dn is always returned irrespective of which attributes types are requested.

The fifth parameter, attrsonly, specifies if only attributes need to be returned. Setting this to 1 returns only attributes, whereas setting this to 0 returns attributes and values.

It is possible to limit the number of entries returned as a result of the search using the sizelimit attribute. Some directory servers will be configured to return no more than a preset number of entries. This parameter is therefore limited by the corresponding server-side maximum for the number of entries to be returned.

The timelimit attribute determines the amount of time in seconds to spend on a search operation. Setting this argument to 0 is equivalent to unlimited time. However, similar to the sizelimit argument, the maximum time is limited by the maximum time the server has been configured to spend on a search query.

The last argument, deref, determines the behavior in terms of dealing with aliases during the search. This argument can take the following values:

- LDAP_DEREF_NEVER: Aliases are never dereferenced in this case. This is the default case.
- LDAP_DEREF_ALWAYS: Aliases should always be dereferenced.
- LDAP_DEREF_SEARCHING: Aliases should be dereferenced during the search but not when locating the base object of the search.
- LDAP_DEREF_FINDING: Aliases should be dereferenced when locating the base object but not during the search.

### ldap_compare()

```
int ldap_compare(int link_identifier, string dn,
string attribute, string value)
```

ldap_compare() is used to compare the value of a string with an attribute of an entry in the directory specified by a DN. It takes a link identifier as the first parameter followed by the DN of the entry whose attribute is to be compared against, followed by the attribute itself and finally the string itself. It returns true if the attribute value matches the string exactly, false if not, and -1 if the comparison operation failed. However, this function cannot be used to compare binary values and is available only from PHP 4.0.2 and upwards:

```
<?php
if (!($conn=ldap_connect("ldapmachine.myorg.com"))) {
echo("Failed to connect to the server");
} else {
if (ldap_bind($conn)) {
$toCompare = "richard";
$dn = "mail=richardc@xyz.com, o=myorg, c=us";
$attr = "cn";

if((($ret = ldap_compare($conn, $dn, $attr, $toCompare)) < 0) {
echo("ldap_compare failed");
} elseif ($ret == TRUE) {
echo("Comparison succeeded");
} elseif ($ret == FALSE) {
echo("Comparison failed");
}
} else {
echo("Failed to bind to the server");
ldap_close($conn);
}
}
?>
```

### ldap_read()

```
int ldap_read(int link_identifier, string base_dn, string filter
[, array attributes [, int attrsonly [, int sizelimit
[, int timelimit [, int deref]]]]])
```

ldap_read() performs the search for a specified filter on the directory with the scope LDAP_SCOPE_BASE, which is equivalent to reading an entry from the directory. An empty filter is not allowed. If you want to retrieve absolutely all information for this entry, use a filter of objectClass=*. If you know which entry types are used on the directory server, you might use an appropriate filter such as objectClass=inetOrgPerson.

This call takes an optional fourth parameter, which is an array of the attributes required. It returns a search result identifier, or false on error. The newly introduced parameters attrsonly, sizelimit, timelimit, and deref have exactly the same functionality as they have in the ldap_search() function.

### ldap_dn2ufn()

```
string ldap_dn2ufn(string dn)
```

ldap_dn2ufn() function is used to turn a DN into a more user-friendly form, stripping off type names of the attributes. For example the DN 'cn=Resident Geek, o=caffeinated, c=uk' would be turned into 'Resident Geek, caffeinated, uk'.

### ldap_explode_dn()

```
array ldap_explode_dn(string dn, int with_attrib)
```

ldap_explode_dn() splits a DN returned by ldap_get_dn() into its component parts, that is the RDNs. ldap_explode_dn() returns an array of all those components. with_attrib is used to request that the RDNs are returned with only values or their attributes as well. To get RDNs with attributes (attribute=value format), set with_attrib to 0, and to get only values set it to 1.

### ldap_first_attribute()

```
string ldap_first_attribute(int link_identifier, int result_entry_identifier, int &ber_identifier);
```

ldap_first_attribute() returns the first attribute in the entry pointed by the entry identifier. Remaining attributes are retrieved by calling ldap_next_attribute() successively.

ber_identifier is an identifier to internal memory location pointer where all the results of this query are stored. It is passed by reference - the & indicates this. The same ber_identifier is passed to the ldap_next_attribute() function, which reads the next entry and then updates the pointer to the next entry.

### ldap_first_entry()

```
int ldap_first_entry(int link_identifier, int result_identifier)
```

Entries in the LDAP result are read sequentially using the ldap_first_entry() and ldap_next_entry() functions. ldap_first_entry() returns the entry identifier for first entry in the result. This entry identifier is then supplied to ldap_next_entry() to get successive entries from the result. It returns the result entry identifier for the first entry on success or false on error.

### ldap_free_result()

```
boolean ldap_free_result(int result_identifier)
```

ldap_free_result() frees up the memory allocated internally to store the result of a previous search operation and pointed to by the result_identifier. Typically, all the memory allocated for the search result gets freed at the end of the script. In case the script is making successive searches that return large resultsets, ldap_free_result() could be called to keep the runtime memory usage by the script low. It returns true on success and false on error.

### ldap_get_attributes()

```
array ldap_get_attributes(int link_identifier, int result_entry_identifier)
```

ldap_get_attributes() is used to simplify reading the attributes and values from an entry in the search result. The return value is a multi-dimensional array of attributes and values. Having located a specific entry in the directory, we can find out what information is held for that entry by using this call. We would use this call for an application that browses directory entries and/or where you do not know the structure of the directory entries. In many applications you will be searching for a specific attribute such as an e-mail address or a surname, and won't care what other data is held. It returns a complete entry information in a multi-dimensional array on success, and false on error.

### ldap_get_dn()

```
string ldap_get_dn(int link_identifier, int result_entry_identifier)
```

ldap_get_dn() is used to find out the DN of an entry in the result. It returns false on error.

### ldap_get_entries()

```
array ldap_get_entries(int link_identifier, int result_identifier)
```

ldap_get_entries() is used to simplify reading multiple entries from the result and then reading the attributes and multiple values. The entire information is returned by one function call in a multi-dimensional array. The attribute index is converted to lowercase (attributes are case-insensitive for directory servers, but not when used as array indices). It returns the complete result information in a multi-dimensional array on success, and false on error.

### ldap_get_values()

```
array ldap_get_values(int link_identifier, int result_entry_identifier, string attribute)
```

ldap_get_values() is used to read all the values of the attribute in the entry from the result. The entry is specified by the result_entry_identifier. The number of values in the entry is stored in an index called count in the resultant array. Individual values are accessed by an integer index in the array. The first index is 0.

This call needs a result_entry_identifier, so needs to be preceded by one of the LDAP search calls and one of the calls to get an individual entry. Your application will either be hard coded to look for certain attributes (such as surname or mail) or you will have to use the ldap_get_attributes function to work out what attributes exist for a given entry. LDAP allows more than one entry for an attribute, so it can, for example, store a number of e-mail addresses for one person's directory entry all labeled with the attribute mail.

### ldap_list()

```
int ldap_list(int link_identifier, string base_dn, string filter [, array attributes [, int attrsonly [, int sizelimit [, int timelimit [, int deref]]]]])
```
