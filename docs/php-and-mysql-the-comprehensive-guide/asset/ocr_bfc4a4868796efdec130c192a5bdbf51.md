Apache installation or in /usr/bin (the which apxs call reveals the path). Otherwise, PHP is only generated as a CGI module:

```
./configure --with-apxs2=/Path/bin/apxs --with-mysql
```

You can see the desired result in Figure 2.22.

![](bbox=[0.144, 0.2, 0.822, 0.51])

Figure 2.22 Configure Has Run Through—a Good Sign!

> **Note**
> 
> You can use ./configure --help to display a list of all options. The necessary settings for extensions can be found at the beginning of each chapter in this book. A summary is included in the online documentation at http://s.php.co/v602265.
> 
> You may also be missing some libraries on the system. For example, PHP uses libxml2, but its presence alone is not enough; you also need the libxml2-dev package. The configure tool aborts with a (usually) meaningful error message if something is missing (see Figure 2.23, which comes from a system on which libxml2 was already present, but not libxml2-dev; the pkg-config package was also missing). The developer package for sqlite3 is also often not available by default and is typically called sqlite-devel or libsqlite3-dev, depending on the distribution. If configure complains about the missing zlib package, then libzlib-dev usually helps.

+   5. Then compile PHP (see Figure 2.24):

```
make
make install
```