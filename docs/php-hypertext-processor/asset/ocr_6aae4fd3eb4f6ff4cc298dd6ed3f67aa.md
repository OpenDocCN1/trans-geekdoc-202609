# Variable Naming

Rules for naming a variable is:

+   Variable names must begin with a letter or underscore character.

+   A variable name can consist of numbers, letters, underscores but you cannot use characters like + , - , % , ( , ) . & , etc

There is no size limit for variables.

# PHP – Variables

Scope can be defined as the range of availability a variable has to the program in which it is declared. PHP variables can be one of four scope types:

+   Local variables

+   Function parameters

+   Global variables

+   Static variables

# PHP Local Variables

A variable declared in a function is considered local; that is, it can be referenced solely in that function. Any assignment outside of that function will be considered to be an entirely different variable from the one contained in the function:

```
<\?
$x = 4;
function assignx () {
$x = 0;
print "\$x inside function is $x.
";
}
assignx();
print "\$x outside of function is $x.
";
\?>
```

This will produce the following result.

```
$x inside function is 0.
$x outside of function is 4.
```