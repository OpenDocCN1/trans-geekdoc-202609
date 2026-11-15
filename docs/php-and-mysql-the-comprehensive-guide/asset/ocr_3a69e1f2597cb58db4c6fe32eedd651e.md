```
ZEND_FE_END
};
```

When using the PEAR package, this information can be found directly in the book.c
file.

+   php_book.h
+   The header file for the extension.

There is also a template for a unit test for the extension in the tests directory and (when
using the PECL packages) a starting point for the associated DocBook documentation in
the manual folder. As you can see, getting started is not difficult at all: quite the opposite.

Now you just need to compile the extension. To do this, go to the base directory of the
PHP source code (php-src) and execute the phpize script, which is installed with PHP
(Windows users, use buildconf as described in Chapter 2):

```
phpize
```

Then reconfigure PHP (Windows users, use nmake instead of make):

```
./configure --enable-book
make
```

Figure 39.6 and Figure 39.7 illustrate this process. Finally, except under Windows, make
sure (with root rights) that the extension (Book.so) is also located in the correct directory:

```
make install
```

![](bbox=[0.145, 0.53, 0.63, 0.88])

Figure 39.6 Use the "--enable-book" Configuration Switch