# Core PHP Programming

The ldap_connect function returns an LDAP connection identifier, or FALSE when there is an error. Both arguments are optional. ldap_connect returns the identifier of the current open connection. If the port is omitted, port 389 is assumed.

# integer ldap_count_entries(integer link, integer result)

The ldap_count_entries function returns the number of entries in the specified result set. The result argument is a result returned by ldap_read.

# boolean ldap_delete(integer link, string dn)

The ldap_delete function removes an entry from the directory.

```
<?php
// connect to LDAP server
if(!($ldap=ldap_connect("ldap.php.net")))
{
    die("Unable to connect to LDAP server!");
  }

//set login DN
$dn="cn=root, dc=php, dc=net";

//attempt to bind to DN using password
if(!ldap_bind($ldap, $dn, "secret"))
{
    die("Unable to bind to `$dn`!");
  }

//delete entry from directory
$dn="cn=John Smith, dc=clearink, dc=com"
if(ldap_delete($ldap, $dn))
{
    print("Entry Deleted!\n");
}
else
{
    print("Delete failed!\n");
}

//close connection
ldap_close($ldap);
?>
```