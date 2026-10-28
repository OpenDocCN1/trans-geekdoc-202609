# # How to code a constructor method

# ## The syntax

```
```php
public function __construct([parameterList]) {
    // Statements to execute
}
```
```

# ## The default constructor

```
```php
public function __construct() { }
```
```

# ## The constructor for the Category class

```
```php
public function __construct($id, $name) {
    $this->id = $id;
    $this->name = $name;
}
```
```

# ## The constructor for the Category class with default values

```
```php
public function __construct($id = NULL, $name = NULL) {
    $this->id = $id;
    $this->name = $name;
}
```
```

# # How to code a destructor method

# ## The syntax

```
```php
public function __destruct() {
    // Statements to execute
}
```
```

# ## A destructor for a database class

```
```php
public function __destruct() {
    $this->dbConnection->close();
}
```
```

# # Description

+   - *A constructor method*, or just *constructor*, is a special method that’s executed when a new object is created from the class. It often initializes the properties of the object.
+   - *A destructor method*, or just *destructor*, is a special method that’s executed when an object is no longer available for use. In other words, it is executed when there are no variables that refer to the object. This type of method can’t include any parameters.
+   - Within a class, the special variable named $this stores a reference to the current object. As a result, it allows you to access the properties and methods of the current object.
+   - The *object access operator* (->) provides access to an object’s properties and methods. When you code the object access operator, you can’t have a space between the two characters.

Figure 14-4 How to code constructors and destructors