Core PHP Programming

```
print("</PRE\n");
print("<HR\n");
}
while ($entry = ldap_next_entry($ldap, $entry));
ldap_free_result($result);
?>
```

# integer ldap_read(integer link, string dn, string filter, array
attributes)

The ldap_read function functions similarly to ldap_list and ldap_search. Arguments are used in the same manner, but ldap_read searches only in the base DN.

# integer ldap_search(integer link, string dn, string filter, array
attributes)

The ldap_search function behaves similarly to ldap_list and ldap_read. The difference is that it matches from the current directory down into every subtree. The attributes argument is optional and specifies a set of attributes that all matched entries must contain.

```
<?
/*
** Function: compareEntry
** This function compares two entries for
** the purpose of sorting.
*/
function compareEntry($left, $right)
{
	$ln = strcmp($left["last"], $right["last"]);
	if($ln == 0)
{
	return(strcmp($left["first"],
		$right["first"]));
	} else
{
	return($ln);
	}
}

//connect to LDAP server
```

IT-SC book 496