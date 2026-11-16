```
return 0;
}
return $linkIdentifier;
}
```

Given a search criteria string, this function creates a search filter expression:

```
function createSearchFilter($searchCriteria)
{
    $noOfFieldsSet = 0;
    if ($searchCriteria["cn"]) {
        $searchFilter = "(cn=*" . $searchCriteria["cn"] . "*)";
        ++$noOfFieldsSet;
    }

    if ($searchCriteria["sn"]) {
        $searchFilter .= "(sn=*" . $searchCriteria["sn"] . "*)";
        ++$noOfFieldsSet;
    }

    if ($searchCriteria["mail"]) {
        $searchFilter .= "(mail=*" . $searchCriteria["mail"] . "*)";
        ++$noOfFieldsSet;
    }

    if ($searchCriteria["employeenumber"]) {
        $searchFilter .= "(employeenumber=*" .
        $searchCriteria["employeenumber"] . "*)";
        ++$noOfFieldsSet;
    }

    if ($searchCriteria["ou"]) {
        $searchFilter .= "(ou=*" . $searchCriteria["ou"] . "*)";
        ++$noOfFieldsSet;
    }

    if ($searchCriteria["telephonenumber"]) {
        $searchFilter .= "(telephonenumber=*" .
        $searchCriteria["telephonenumber"] . "*)";
        ++$noOfFieldsSet;
    }
}
```

We perform a logical AND on all specified search criteria to create the final search filter:

```
if ($noOfFieldsSet >= 2) {
    $searchFilter = "(&" .$searchFilter . ")";
}
return $searchFilter;
}
```

This function; given a link identifier obtained from the connectBindServer() function and the search filter created by createSearchFilter(), performs a search on the directory:

```
function searchDirectory($linkIdentifier, $searchFilter)
{
    global $baseDN;
    $searchResult = ldap_search($linkIdentifier, $baseDN, $searchFilter);
```