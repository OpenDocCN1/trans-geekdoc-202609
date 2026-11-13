# if ... else statements

If you're clear on the previous sections, nothing here will surprise you. The else portion of an if ... else statement enables you to specify code that will be executed if the condition specified is false. The following code prints "it is not equal":

```
$a = 2;
if ($a == 1){
    echo "it's equal";
}
else
{
    echo "it is not equal";
}
```

# if ... elseif statements

You will often have to check a variable against more than one set of conditions. For instance, you might have a single page that will insert, edit, and delete records in a database. It is fairly typical to indicate which portion of the script you wish to run by assigning different values to a submit button in an HTML form. When the form is submitted, the value of the submit button can be checked against several elseif statements, as follows:

```
if ($_POST['submit'] == "edit")
{
    // code for editing database
}
elseif ($_POST['submit'] == "update")
{
    //code for updating records
}
elseif ($_POST['submit'] == "delete")
{
    //code for deleting records
}
else
{
    echo "I have no idea what I should be doing.";
}
```