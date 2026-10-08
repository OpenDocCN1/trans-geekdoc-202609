# Writing Accessor Functions 167

```
function __get($name)
{
    return $this->$name;
}
function __set($name, $value)
{
    $this->$name = $value;
}
```

This code provides minimal functions to access the named $attribute. The function named __get() simply returns the value of $attribute, and the function named __set() assigns a new value to $attribute.

Note that __get() takes one parameter—the name of an attribute—and returns the value of that attribute. Similarly, the __set() function takes two parameters: the name of an attribute and the value you want to set it.

You do not directly call these functions. The double underscore in the name shows that these have a special meaning in PHP; just like the __construct() and __destruct() functions.

How do they work? If you instantiate the class
$a = new classname();

you then use the __get() and __set() functions to check and set the value of any attributes that are otherwise inaccessible. These functions will not be used, even if declared, when accessing attributes declared to public.

If you type
$a->attribute = 5;

this statement implicitly calls the __set() function with the value of $name set to "attribute", and the value of $value set to 5. You need to write the __set() function to do any error checking you require.

The __get() function works in a similar way. If, in your code, you
$a->attribute

this expression implicitly calls the __get() function with the parameter $name set to "attribute". It is up to you to write the __get() function to return the value.

At first, this code might add little or no value. In its present form, this is probably true, but the reason for providing accessor functions is simple: you then have only one section of code that accesses that particular attribute.

With only a single access point, you can implement validity checks to make sure that sensible data is being stored. If it occurs to you that the value of $attribute should only