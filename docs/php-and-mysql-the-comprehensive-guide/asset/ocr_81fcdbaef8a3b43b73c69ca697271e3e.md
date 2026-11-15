The use of namespaces is therefore quite simple, but the proverbial devil can be in the details. Because identical names are now permitted within different namespaces, side effects can occur if, for example, a namespace creates a function that has been implemented simultaneously in another namespace or directly within PHP. PHP offers some help and techniques for this.

# ### 11.5.4 Determine the Current Namespace

First, the `namespace` keyword can also be used to obtain a reference to the current namespace—similar to `$this` in OOP, which generates a reference to the current instance, or `self` for the current class. This can then look like the following example.

```
```php
<?php
namespace myNS;

const NAME = 'Bravo';
function sayHello($name) { echo "Hello $name!"; }

namespace\sayHello(namespace\NAME);
?>
```
```

# Listing 11.66 The "namespace" Keyword ("namespace2.php")

In the code from <u>Listing 11.66</u>, the `namespace` prefix would not have been necessary at all as there is only one function, `sayHello()`, and only one constant, `NAME`. However, this technique can be very useful in more complex code. Instead of `namespace`, you can also specify the explicit namespace name—but you will then have to adapt this reference again if you ever need to change the namespace name.

If, on the other hand, you want to access a function, class, or constant integrated in PHP but have accidentally chosen exactly the same identifier within the current namespace, you can access the internal PHP implementation by preceding it with a backslash. Assuming that PHP—like our `myNS` namespace—has a `sayHello()` function, you can call the PHP function as follows, regardless of which namespace you are in:

```
\sayHello()
```

> > **Tip**
> > Speaking of which, if you would like to have the current namespace as a character string, the `__NAMESPACE__` constant contains exactly this information.

# ### 11.5.5 Namespaces via Alias

So far, we haven’t gained too much. Compared to classes with endless names, the typing work hasn’t been reduced too much. However, the actual usefulness of namespaces