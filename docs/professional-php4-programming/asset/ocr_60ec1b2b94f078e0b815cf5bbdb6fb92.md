```
if (isset($firstCallToSearch)) {
    generateHTMLHeader("Search using the following criteria:");
    generateHTMLForm(0, "empdir_search.php", "SEARCH");
} else {
    require("empdir_functions.php");
}
```

If all of the fields are empty, we print an error and re-display the screen:

```
if (!$cn && !$sn && !$mail && !$employeeenumber && !$ou &&
    !$telephonenumber) {
    generateHTMLHeader("Search using the following criteria:");
    displayErrMsg("Atleast one of the fields must be filled !!");
    generateHTMLForm(0, "empdir_search.php", "SEARCH");
} else {
```

We create an associative array with the search criteria that we shall later use as an argument to the search function:

```
$searchCriteria["cn"]        = $cn;
$searchCriteria["sn"]        = $sn;
$searchCriteria["mail"]      = $mail;
$searchCriteria["employeenumber"] = $employeeenumber;
$searchCriteria["ou"]        = $ou;
$searchCriteria["telephonenumber"] = $telephonenumber;
$searchFilter = createSearchFilter($searchCriteria);
```

We connect to the server and do an anonymous bind:

```
$linkIdentifier = connectBindServer();
if ($linkIdentifier) {
```

This function call fetches the search results if the search succeeded. We display the results using the printResults() function:

```
$resultEntries = searchDirectory($linkIdentifier,
                                    $searchFilter);
if ($resultEntries) {
    generateHTMLHeader("Search Results:");
    printResults($resultEntries);
    returnToMain();
} else {
    returnToMain();
}
} else {
    displayErrMsg("Connection to LDAP server failed !!");
    closeConnection($linkIdentifier);
    exit;
}
}
?>
```