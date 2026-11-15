And this is an overview of important functions that are new in PHP 8.x up to 8.4:

+   - As of version 8.1, PHP allows a new octal notation for numbers with 0 in front and an o behind.
+   - Since PHP 8.1, PHP allows enumerations with fixed data values. More on this in Chapter 6.
+   - New in PHP 8.1 is the never keyword as a return type for functions. Since PHP 8.2, null, false, and true are also possible as types, and DNF types allow mixed returns. More on these topics in Chapter 6.
+   - Since PHP 8.2, there is a new, significantly better Random\\Randomizer class for mathematical functions, which can be found in Chapter 9.
+   - PHP 8.4 brings new array_*() functions.
+   - In PHP 8.4 the DOM API was completely refactored. This includes standards-compliant support for the parsing of HTML5 documents.

There are now some new functions in object-oriented programming, which have been constantly optimized:

+   - In PHP 8.1, the option to declare properties as readonly was added. In PHP 8.2, readonly was then also possible at the class level.
+   - As of PHP 8.1, objects can also be used as static variables, as default values for parameters, and as global constants and parameters for properties.
+   - In PHP 8.1, dynamically set properties are classified as deprecated. Instead, they can be specifically allowed for a class by setting the attribute named #[AllowDynamicProperties].
+   - Since PHP 8.1, constants in classes can also be marked as final.
+   - As of PHP 8.3, constants can also be typed with data types.
+   - In PHP 8.3, the #[Override] attribute allows you to mark a method that, as the name suggests, overrides another.
+   - In PHP 8.1, fibers are added as a new concept. They allow the execution of parallel calls in PHP and are therefore an approach for multithreading. More on this can be found in Chapter 26.
+   - Since PHP 8.3, the json_validate() method allows JSON strings to be validated before decoding.
+   - PHP 8.4 supports property hooks. They provide support for properties that can natively be read by IDEs and analysis tools, without the need to write DocBlock comments that might go out of sync.
+   - PHP 8.4 supports asymmetric visibility, that means a property can have different types of visibility, for instance public for reading and private für setting.
+   - With the #[Deprecated] attribute in PHP 8.4 you can use the deprecated functionality for own methods, constants and functions.