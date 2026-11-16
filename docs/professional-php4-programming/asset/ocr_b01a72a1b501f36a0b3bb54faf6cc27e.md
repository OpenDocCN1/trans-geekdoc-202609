# ldap_add()

```
int ldap_add(int link_identifier, string dn, array entry)
```

The ldap_add() function adds new entries in to the directory. When adding or modifying an entry, the entry must have all of the required attributes and only allows attributes as specified by the LDAP server's schema. Objectclass attributes define what attributes are required and which ones are simply allowed (such as, optional).

The link_identifier is the connection identifier that is returned by the ldap_connect() function. The new entry to be added needs a DN that is specified as the second argument. The third argument passed is an array consisting of attributes and values of the new entry. If we take the example of the LDIF for FooWid, the entry array would be:

```
entry["cn"] = "Don Joe III";
entry["mail"] = "djoe@exist.com";
entry["description"] = "Professional bungee-jumper";
...
```

# ldap_mod_add()

```
int ldap_mod_add(int link_identifier, string dn, array entry)
```

This function adds attribute values to the existing attributes of the specified DN. It performs the modification at the attribute level as opposed to the object level. Object level additions are done by the ldap_add() function, that is, if we needed to add a telephone number to an entry, we would use this function, whereas to add a completely new entry we would rely on ldap_add(). It returns true on success and false on error.

# ldap_mod_del()

```
int ldap_mod_del(int link_identifier, string dn, array entry)
```

This function removes attribute values from the specified DN. It performs the modification at the attribute level as opposed to the object level. Object level deletions are done by the ldap_del() function, that is if we needed to delete the room number of an entry corresponding to an employee, we would use this function, whereas to completely delete an employee entry, we would rely on ldap_del(). It returns true on success and false on error.

# ldap_delete()

```
boolean ldap_delete(int link_identifier, string dn)
```

ldap_delete() deletes a particular entry in the LDAP directory specified by the DN. It returns true on success and false on error. Usually LDAP servers are configured such that this is only allowed for as few users as is specified in the LDAP server's ACL.

# ldap_modify()

```
boolean ldap_modify(int link_identifier, string dn, array entry);
```