The cleanup function which closes the connection specified by the link identifier argument:

```
function closeConnection($linkIdentifier)
{
  ldap_close($linkIdentifier);
}
?>
```

This script is invoked when the user clicks the SEARCH button. The search screen would look like below:

![](bbox=[0.11, 0.265, 0.9, 0.715])

```
<?php
// empdir_search.php
include("empdir_common.php");
```

We set the search filter to be a null string initially:

```
$searchFilter = "";
```

Since this script is also called to process the search operation apart from being called to display the screen for entering search criteria, we need to distinguish between the two cases: