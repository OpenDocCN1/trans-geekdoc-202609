
The add_get_* functions exist for every type of indexing and every type of data except zval, where it wouldn't make any sense. Extended versions also exist that allow string lengths to be specified for associative array keys.

The downloadable code for this book has some additional examples for using arrays.

## Accessing and Modifying Hash Tables

As mentioned earlier, all arrays are hash tables, so by definition all the functions that work on hash tables will also work on arrays. In fact, all of the functions from the previous section were just easy-to-use wrappers around hash tables. However, it is often useful to access the hash table directly.

Hash tables have additional benefits such as the ability to check if a key exists, and apply functions to the entire hash at one time. However, perhaps the most useful feature is simulating a foreach loop. After reviewing iterators in Chapter 2 this should be fairly familiar code:

```
HashTable *hash = ...
zval **data;

for ( zend_hash_internal_pointer_reset_ex(hash, &pointer);
    zend_hash_get_current_data_ex(hash, (void **) &data, &pointer ) == SUCCESS;
    zend_hash_move_forward_ex(hash, &pointer) ) {
    /* the zval data is filled with the current hash value */
}
```

Note the double pointer for the data variable. Be sure when accessing it to use the _PP macros and not the ones ending in simply _P. You can also get the number of elements in the hash by using zend_hash_num_elements( hash ).

It is not necessary to loop through the hash table to perform common operations such as looking up the value associated with a key and checking if a key exists. Finding elements in a hash table if you know the key is fairly simple:

```
zend_hash_find( hash, key, strlen(key), (void **)&data );
```

data is a double pointer to a zval just like before. Finding it if you know the index is similar:

```
zend_hash_index_find( hash, 3 /* index of 3 */, (void **)&data );
```

Finally, the code that checks if a key exists looks like this:

```
int exists;
exists = zend_hash_exists( hash, key, strlen(key) );
exists = zend_hash_index_exists( hash, 3 /* index of 3 */ );
```

Hash tables are used all over PHP. They are the core concepts used for everything from global values to the return values from many API functions, so it is very important to understand everything about them.

## OBJECTS AND INTERFACES

The first part of the chapter explained how to define classes using the CodeGen_PECL utility. This section explains how to create classes and interfaces from scratch.

Perhaps as important, this section reviews how to inspect a class, modify it at run time, and access its properties and methods. By the end of this section you should be able to create an extension that can access data directly from an object passed into a function.

## Creating a Class

Classes are created in much the same way as basic extensions and functions. They contain their own methods table and have their own set of macros; however, most of them should seem familiar.

## Class Definition, Inheritance, and Namespaces

At a minimum there needs to be a class entry pointer, a methods table, and initialization code. It is best practice to put all the initialization in a function to call from the MINIT function but it is also possible to put all the code in MINIT directly, as illustrated in the following steps:

- 1. Define the class entry pointer in the C file:
- 2. The next step is to define the methods table, which bears a not-coincidental resemblance to the extension function table. The methods table must be there even if it is empty. An empty methods table looks like this:
- 3. The class entry pointer was defined but it is empty right now. A simple initialization function can be created and then called from MINIT. This is a very simple class but classes will only get larger from here so it is always a good idea to separate out the functionality.

```
static zend_class_entry *helloworld_ce_ptr = NULL;
```

The class entry is a structure that stores information about the class in order to be used by the engine when initializing instances and accessing the object. It includes several hash tables for methods and properties as well as special pointers especially for magic methods.

```
static zend_function_entry helloworld_methods[] = {
  { NULL, NULL, NULL }
}
```

```
zend_class_entry ce;
INIT_CLASS_ENTRY(ce, "helloworld", helloworld_methods);
helloworld_ce_ptr = zend_register_internal_class( &ce );
```

The code is straightforward and simply registers the class so that Zend knows it exists and can instantiate it. In the process it stores the pointer to the new class entry. Note that the returned class entry is not the same in memory as the original passed into it.

There is also an extended version of the macro for binary strings that takes the length of the class name as an argument after the class name. Ultimately all the macros end up expanding to the same one:

```
INIT_OVERLOADED_CLASS_ENTRY_EX(class_container, class_name,
  class_name_len, functions, handle_fcall, handle_propget, handle_propset,
  handle_propunset, handle_propisset)
```

There is also a macro `INIT_OVERLOADED_CLASS_ENTRY` (without the _EX) that takes all the parameters of its extended version except `handle_propunset` and `handle_propisset`. It also doesn’t expect a length for the class name.

> *If you wanted to have your class inside of a namespace there are three macros for that. Each macro is identical to its default namespace counterpart except that it takes the namespace as the second argument:*

`INIT_NS_CLASS_ENTRY`
`INIT_OVERLOADED_NS_CLASS_ENTRY`
`INIT_OVERLOADED_NS_CLASS_ENTRY_EX`

The handlers at the end of the overloaded macros are expecting to be defined with `PHP_FUNCTION`. However, you can always define a `PHP_FUNCTION` and not put it in the function table. If you don’t put it in the function table for your extension (remember: `PHP_FE`) it won’t be callable from within PHP.

As you may have guessed, they correspond to the `__call`, `__get`, `__set`, `__unset`, and `__isset` methods. All magic methods have dedicated pointers in the `zend_class_entry` structure; however they can still be easily defined by creating a method of that name just as you would in PHP.

Inheriting from another class is as simple as using `register_internal_class_ex` instead of its non-extended counterpart:

```
zend_register_internal_class_ex( &ce, NULL, "parent_class_name" );
```

The second parameter is the parent class entry and the third is the name of the parent class. You should only use one or the other. The class does not need to be in the same extension as the child class; however, if the parent class is specified as a string and it is not found, you will end up with a null class entry.

It is also possible to define a class as abstract:

```
helloworld_ce_ptr->ce_flags |= ZEND_ADD_EXPLICIT_ABSTRACT;
```

Remember to make changes to the class entry pointer after the class is registered. Changing the local structure before registering it won’t have an effect.

## Using Methods

Defining a method works much the same way as defining a function except the macro `PHP_METHOD` should be used instead of `PHP_FUNCTION` (don’t forget to also put it in the header). The `PHP_METHOD` macro also takes two arguments instead of one. The first is the class name and the second is the method name.

Also, `PHP_FE` becomes `PHP_ME` and must be put in the class function table instead of the global function table. The `PHP_ME` macro takes `visibility` as its final argument. The possible values for `visibility` are:

- `ZEND_ACC_PUBLIC`
- `ZEND_ACC_PROTECTED`
- `ZEND_ACC_PRIVATE`

You can also use a binary or operation to combine either of the three with ZEND_ACC_STATIC to make the method statically accessible. As with many things when writing extensions, it doesn’t make much sense to have a statically callable private method but public and protected are more useful. Just like in PHP, a static method can be called either truly static or as if it were a real method. Even so, it should only access other static properties and methods (never use “this”).

The method implementation is just like a function implementation except you will probably want to get the value of $this at the top every time it is called, especially because the value should be passed in for argument parsing:

```
PHP_METHOD(helloworld, method_name)
{
    zend_class_entry * _this_ce;
    zval * _this_zval = NULL;

    if (zend_parse_method_parameters(ZEND_NUM_ARGS() TSRMLS_CC, getThis(),
        "O", &_this_zval, helloworld_ce_ptr) == FAILURE) {
        RETURN_NULL;
    }

    _this_ce = Z_OBJCE_P(_this_zval);

    ...
}
```

The value of the current object is always passed as a zval to the first parameter. After parsing the parameters it is often desirable to get the class entry structure from the object as well. At first glance it looks redundant. Although it doesn’t happen during typical use for most extensions, when you deal with inheritance and polymorphism it is possible for the values of _this_zval to be different than getThis() and _this_ce to be different than helloworld_ce_ptr.

At this point it may be natural to assume that this method always takes the object as the first argument it can then also be called procedurally like with MySQLi:

```
mysqli_query( $mysqli_obj, "SELECT * FROM example" );
```

Close, but not quite there. It must be added to the extension method table as an alias in addition to the entry in the methods table of the class:

```
PHP_MALIAS(parent, true, foo, NULL, ZEND_ACC_PUBLIC)
```

The main difference between the previous macro and the PHP_ME macro is that it accepts an alias name that is different than the method name as the third argument. It is important to define the function and its implementation using the alias and not the method name. Also, in PHP the class name is automatically prepended to the alias.

It is possible to make a method abstract. Because abstract methods don’t have an implementation it is necessary to define them in the function table a little differently. To do that it is necessary to dive a little bit deeper into the macros. Both PHP_FE and PHP_ME eventually expand out to reveal that
