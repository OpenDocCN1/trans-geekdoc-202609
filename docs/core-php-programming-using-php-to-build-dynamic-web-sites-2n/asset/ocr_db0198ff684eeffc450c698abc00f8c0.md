Code within the braces forms a new scope and should be indented.

```
// tell the user if a is equal to
ten
if ($a==10)
{
    printf("a is ten.\n");
}
else
{
    printf("a is not ten.\n");
}
```

# #Naming

The names of variables, constants, and functions are to begin with a lowercase letter. In names that consist of more than one word, the words are written together and each word starts with an uppercase letter. Use short names for variables in a small scope, such as just inside a for loop. Use longer names for variables in larger scopes.

Function names should begin with a lowercase letter and use capitals for subsequent words.

```
/*
** Function getAddressFromEnvironment
** Input: $Prefix - prefix used to generate address form
** Return: array suitable for addressFields
*/
function getAddressFromEnvironment ($Prefix)
{
    global $AddressInfo;
    // get list of all address fields
    //from the AddressInfo array
    reset($AddressInfo);
    while ($field, $info) = each ($AddressInfo))
    {
        $ReturnValue[$field] = trim ($GLOBALS[$Prefix][$info[ADDR_VAR]])
    }
    return ($ReturnValue);
n
```