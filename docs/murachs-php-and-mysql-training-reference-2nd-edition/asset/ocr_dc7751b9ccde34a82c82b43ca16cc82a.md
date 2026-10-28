# The components of an HTTP URL

```
http://www.murach.com/books/index.htm
protocol        domain name          path       filename
```

# What happens if you omit parts of a URL

+   - If you omit the protocol, the default of `http://` will be used.
+   - If you omit the filename, one of the default filenames for the Apache web server will be used: `index.htm`, `index.html`, or `index.php`.
+   - If you omit the filename and there is no default file, Apache will display an index of the files and directories in the path.

# URLs for requesting pages from an Internet web server

# A request for a specific page

```
http://www.murach.com/books/phps/index.htm
```

# A request for the default (home) page of a website

```
http://www.murach.com/
```

# URLs for requesting applications from a local web server

# A request for the default page in an application directory

```
http://localhost/book_apps/ch01_product_discount/
```

# A request for a directory that doesn’t contain a default page

```
http://localhost/book_apps/
```

# An index of the applications in the book_apps directory

![](bbox=[0.087, 0.556, 0.676, 0.779])

# Description

+   - To request a web page or website on the Internet, enter the URL for the page or site in the address bar of your web browser.
+   - To request a web page or application on a local server, use *localhost* as the domain name.
+   - To make it easy to run the book applications and exercise starts for this book, get an index of the book_apps and ex_starts directories, and bookmark those pages.

Figure 1-13 — How to run a PHP application