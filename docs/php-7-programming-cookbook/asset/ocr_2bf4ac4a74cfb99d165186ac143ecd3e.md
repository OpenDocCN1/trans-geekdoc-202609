| Error | Fix |
| :--- | :--- |
| configure: WARNING: unrecognized options: --enable-spl, --enable-reflection, --with-libxml | Not a big deal. These options are defaults and don't need to be included. For more details, please refer to the following link:<br><br>http://jjcutrer.com/howto/linux/how-to-compile-php7-on-ubuntu-14-04 |

# ### Installing PHP 7 from pre-compiled binaries

As the title implies, **pre-compiled** binararies are a set of binary files that somebody else has kindly compiled from PHP 7 source code and has made available.

In the case of Windows, go to `http://windows.php.net/`. You will find a good set of tips in the left column that pertain to which version to choose, **thread safe** versus **non-read safe**, and so forth. You can then click on **Downloads** and look for the ZIP file that applies to your environment. Once the ZIP file has been downloaded, extract the files into the folder of your choice, add `php.exe` to your path, and configure PHP 7 using the `php.ini` file.

To install the pre-compiled binararies on a Mac OS X system, it is best to involve a package management system. The ones recommended for PHP include the following:

+   - MacPorts
- Liip
- Fink
- Homebrew

In the case of Linux, the packaging system used depends on which Linux distribution you are using. The following table, organized by Linux distribution, summarizes where to look for the PHP 7 package.

| Distribution | Where to find PHP 7 | Notes |
| :--- | :--- |
| Debian | `packages.debian.org`/stable/php<br>`repos-source.zend.com/zend-server/early-access/php7/php-7*DEB` | Use this command:<br>`sudo apt-get install php7`<br><br>Alternatively, you can use a graphical package management tool such as **Synaptic**.<br><br>Make sure you select `php7` (and not `php5`). |