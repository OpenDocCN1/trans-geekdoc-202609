![](bbox=[0.07, 0.12, 0.85, 0.45])

Figure 4.1 Final methods cannot be overwritten.

Of course, if you are the sole developer making a class or method final does not seem to be necessary. However, you should always be ready for when the development team gets larger or you refactor your codebase into a library others will also be using.

# Using Autoloading

```
spl_autoload_register('myAutoloadFunction');
```

When you are using a class, it needs to be defined; otherwise PHP will throw an error. There is a second chance, however, should a class not be available once it is used. The spl_autoload_register() function registers a function that will be called once PHP code tries to use a class that has not been registered yet. After the call to the registration function, the code that uses the undefined class is run again. If the class is now available, great; otherwise, the usual error occurs.