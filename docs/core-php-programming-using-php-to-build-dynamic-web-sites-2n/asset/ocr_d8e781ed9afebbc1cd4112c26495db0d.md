# Core PHP Programming

textual data. String constants are always surrounded by double quotes ("") or single quotes ('').

In addition to these, PHP has four aggregate data types that use the other three: arrays, objects and booleans, and resources. An array is a collection of values associated with indexes. Arrays are discussed in full in Chapter 5, "Arrays." Objects are similar to arrays, but may also contain functions. They are discussed in Chapter 6, "Classes and Objects." Boolean values are either true or false. Historically, PHP did not support a separate type for booleans; instead zero and any other value was considered to be a true value. With PHP 4, this changed. Now data may be cast or set to be boolean type. Resources are integers to identify system resources, such as open files or database connections.

As you write PHP code, you will usually be unaware of the distinction between types because variables are multype. You do not declare a variable to be a particular type. You just assign it a value. PHP will remember what type of data you put into the variable. When you retrieve data from the variable, they are returned with that same type.

There are two ways to override this behavior. The first way is to use the `settype` function. This tells PHP that you want to start considering a variable to be a certain type. The data associated with the variable will be converted to the new type. The alternative is to use one of the type conversion functions or a cast. Consider Listing 2.1, which contrasts `settype`, the type conversion functions, and casts.

# Listing 2.1 Experimenting with Type Conversion