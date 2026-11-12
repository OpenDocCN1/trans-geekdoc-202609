```
}
}
}

$user = new Users();

// Use the __set() magic method to modify the private property
$user->name = "Lina"; // The "name" property is now set to "Lina".
```

In this example, the User class defines a private property $name. The __set() magic method is used to intercept attempts to assign values to inaccessible object properties.

When we try to assign a value to the "name" property of the $user object, the __set() method is automatically invoked. It receives two arguments: the name of the property to be modified and the value to be assigned to it.

In the body of the __set() method, we check whether the name of the property passed corresponds to "name". If so, the value supplied is assigned to the object's $name property.

This magic method allows you to modify a private property of the User class in a controlled way, by intercepting and processing attempts to assign values to this property.

# d. __call() and __callStatic()

The magic __call() method is invoked when we attempt to call a method that doesn't exist or is inaccessible