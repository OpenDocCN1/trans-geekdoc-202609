# Chapter 8: Objects

```
echo <p>The letter 'e' occurs at position: " . $MyString->strpos(" e " ) ;
</p>";
$MyString->madeUpMethod();"
```

The two method calls, $MyString->strlen() and $MyString->strstr(), don't have any arguments because their equivalent PHP functions only require one argument — the string to search with — this is automatically populated with the stored string in the __call() method. The third method call, $MyString->strpos(" e " ), requires a single argument — the string to search for — which is then passed as the second argument to PHP's strpos function.

The following table shows how the CleverString maps calls to the actual PHP functions

| Method Call | PHP String Function Call |
| --- | --- |
| $MyString->strlen() | strlen($this->string) |
| $MyString->strstr() | strcmp($this->string) |
| $MyString->strpos(" e " ) | strpos($this->string, "e") |

Finally, quickly we attempt to call a disallowed — in fact, nonexistent — string function, which displays an error message in the page:

```
$MyString->madeUpMethod();
```

This example shows how easy it is to wrap a set of existing functions, methods, or API calls in a class using a single __call() method. You could easily extend this example to allow practically all of PHP's string of functions to be called, without writing much much extra code.

# Other Overloading Methods

Although you won't use them too much, it's worth mentioning three other overloading methods provided by PHP:

```
__isset() is called whenever the calling code calls PHP's isset on an invisible property. It takes one argument — the property name — and should return true if the property is deemed to be "set," and false otherwise:
```

```
class MyClass {
    public function __isset($propertyName) {
        // All properties beginning with "test" are "set"
        return ( substr($propertyName, 0, 4 ) == "test" ) ? true : false;
    }
}
```