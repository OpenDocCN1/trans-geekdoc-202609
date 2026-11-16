As long as at least one `httpd` process is found, the Apache web server is successfully started.

You should be able to see the default Apache installation page at http://localhost/, or whatever your web server had been previously configured to display as the home page from the `DocumentRoot` setting in `httpd.conf`.

# # Installing PHP

There are a number of third party groups that have begun to offer pre-compiled versions of Apache/PHP for use with OS X. Although such packages are not necessary, the existence of such packages should be noted. For more information on downloading binary versions of PHP for OS X, please consult the PHP manual. We'll be compiling from source in this book, but if you run into serious difficulties, you may find it easier to install the pre-compiled binaries.

Download and unpack the PHP source to a temporary directory, just as you did MySQL and Apache. If any PHP extensions other then MySQL are required, you should have downloaded, installed, and tested them before installing PHP.

With the Apache server configuration options, we must explicitly specify certain directories for PHP to use for it to function smoothly with OS X as shown below:

```
./configure \
--with-mysql=/Users/root/Desktop/mysql-3.xx.xx \
--with-apache=/Users/root/Desktop/apache_1.x.xx \
--prefix=/usr \
--sysconfdir=/etc \
--localstatedir=/var \
--mandir=/usr/share/man
```

You'll need to include `--with-XXX` for any other PHP extensions you've added to this process.

# # Compiling PHP

Once PHP has been properly configured it is ready to be compiled. As with Apache and MySQL, PHP is compiled through the use of a pair of `make` commands as follows:

```
make
make install
```

Under some circumstances, the above commands may end in error. Due to the differences between newline characters on UNIX/DOS/Mac, the previous configure statement fails to properly modify the `internal_functions.c` file located in `./main` of the PHP source tree. Several `#include` statements are inserted by `configure` script, but instead of a newline, only an `n` is inserted, and multiple separate `#include` lines are all on a single line. To correct this error, if it should occur, open the `internal_functions.c` file and correct the following:

```
#include "ext/xml/php_xml.h"n#include "ext/standard/php_standard.h"ninclu...
```

which should be: