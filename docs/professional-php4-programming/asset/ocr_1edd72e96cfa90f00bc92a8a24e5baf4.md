This function is invoked when the user clicks the Delete link in the Edit column of the search results:

```
<?php
//empdir_delete.php
include("empdir_common.php");
include("empdir_functions.php");
```

We create a string corresponding to the DN of the entry we intend to delete:

```
$dnString = "mail=" . urldecode($mail) . ",ou=" . urldecode($ou) . "," .
    $baseDN;
```

The script prompts the user for the administrator's password since this is required for deleting entries
from the directory:

```
if (!isset($adminpassword)) {
    generateHTMLHeader("Administrator action: ");
    promptPassword($mail, $ou, "empdir_delete.php");
    return;
}
```

Here the DN of the administrator user is hard-coded. Ideally there can be a whole category of
administrative users and the roles and privileges of these users can be managed by using the HTTP
sessions in tandem with the LDAP implementation's authentication and authorization mechanism:

```
$adminRDN = "cn=Admin," . $baseDN;
```

We connect to the server and bind as the administrator user:

```
$linkIdentifier = connectBindServer($adminRDN, $adminpassword);
if ($linkIdentifier) {
```

The actual deletion is performed using the DN string we constructed earlier:

```
if (ldap_delete($linkIdentifier, $dnString) == true) {
    generateHTMLHeader("The entry was deleted succesfully");
    returnToMain();
} else {
    displayErrMsg("Deletion of entry failed !!");
    closeConnection($linkIdentifier);
    exit;
} else {
    displayErrMsg("Connection to LDAP server failed!!");
    exit;
}
?>
```